Link: https://tryhackme.com/room/gobusterthebasics (Premium Room)

<img width="1200" height="1200" alt="image" src="https://github.com/user-attachments/assets/293491a6-2c98-418f-b1ce-27daee00ac3d" />

This room focuses on an introduction to Gobuster, an offensive security tool used for enumeration.

**Module 1: Introduction**

<img width="1140" height="800" alt="image" src="https://github.com/user-attachments/assets/4790a9cd-91eb-4a46-a060-d3584e043170" />

This room focuses on the offensive security tool Gobuster, often used for reconnaissance. We will explore how this tool can enumerate web directories, subdomains, and virtual hosts. This room will follow a hands-on approach where you can follow along with the commands explained and execute them yourself to see the results.

Learning Objectives

- Understanding the basics of enumeration

- How to use Gobuster to enumerate web directories and files

- How to use Gobuster to enumerate subdomains

- How to use Gobuster to enumerate virtual hosts

- How to use a wordlist

**Answer the questions below**

1. _I'm ready to learn about Gobuster!_

Answer: No answer needed

------------------------------------------------------------------------------------------------------------------------------------------------

**Module 2: Environment and Setup**

For this room, we will use an Ubuntu 20.04 VM acting as a web server. This web server hosts multiple subdomains and vhosts. The web server also has two content management systems (CMS) installed. These are Wordpress and Joomla.

Throughout this room, we will be using the AttackBox, where Gobuster is already installed, to enumerate the web server directories and subdomains. However, if you prefer to use your own machine instead of the AttackBox, you must be connected to the TryHackMe VPN and have Gobuster installed. You can find installation instructions for Gobuster on your own machine in the official [Gobuster GitHub repository](https://github.com/OJ/gobuster).

Important: We work in a local network with a DNS server on the web server. To ensure we can resolve the domains used throughout this room, you need to change the /etc/resolv-dnsmasq file:

- Open up a terminal on the the AttackBox and enter the command: sudo nano /etc/resolv-dnsmasq.

- Insert nameserver MACHINE_IP as the first line.

- Save the file by pressing CTRL+O, followed by pressing ENTER, and then exit the editor by pressing CTRL+X.

- Enter the command /etc/init.d/dnsmasq restart to restart the Dnsmasq service.

The file should look something like this:

```
root@tryhackme:~# cat /etc/resolv-dnsmasq 
nameserver MACHINE_IP
nameserver 169.254.169.253
```

**Answer the questions below**

1. _I assigned the MACHINE_IP as the first nameserver in the /etc/resolv-dnsmasq file and restarted the Dnsmasq service._

Answer: No answer needed

------------------------------------------------------------------------------------------------------------------------------------------------

**Module 3: Gobuster: Introduction**

Gobuster is an open-source offensive tool written in Golang. It enumerates web directories, DNS subdomains, vhosts, Amazon S3 buckets, and Google Cloud Storage by brute force, using specific wordlists and handling the incoming responses. Many security professionals use this tool for penetration testing, bug bounty hunting, and cyber security assessments. Looking at the phases of ethical hacking, we can place Gobuster between the reconnaissance and scanning phases.

Before exploring Gobuster, let’s briefly discuss the concepts of enumeration and Brute Force.

**Enumeration**

Enumeration is the act of listing all the available resources, whether they are accessible or not. For example, Gobuster enumerates web directories.

**Brute Force**

Brute force is the act of trying every possibility until a match is found. It is like having ten keys and trying them all on a lock until one fits. Gobuster uses wordlists for this purpose.

**Gobuster: Overview**

Gobuster is included by default in distributions like Kali Linux. Let’s start by looking at Gobuster’s help page. This help page gives us a good overview of its functionalities and options.

Enter the following command: gobuster --help. You should get the help page for the Gobuster tool as shown below:

```
           
root@tryhackme:~# gobuster --help
Usage:
  gobuster [command]

Available Commands:
  completion  Generate the autocompletion script for the specified shell
  dir         Uses directory/file enumeration mode
  dns         Uses DNS subdomain enumeration mode
  fuzz        Uses fuzzing mode. Replaces the keyword FUZZ in the URL, Headers and the request body
  gcs         Uses gcs bucket enumeration mode
  help        Help about any command
  s3          Uses aws bucket enumeration mode
  tftp        Uses TFTP enumeration mode
  version     shows the current version
  vhost       Uses VHOST enumeration mode (you most probably want to use the IP address as the URL parameter)

Flags:
      --debug                 Enable debug output
      --delay duration        Time each thread waits between requests (e.g. 1500ms)
  -h, --help                  help for gobuster
      --no-color              Disable color output
      --no-error              Don't display errors
  -z, --no-progress           Don't display progress
  -o, --output string         Output file to write results to (defaults to stdout)
  -p, --pattern string        File containing replacement patterns
  -q, --quiet                 Don't print the banner and other noise
  -t, --threads int           Number of concurrent threads (default 10)
  -v, --verbose               Verbose output (errors)
  -w, --wordlist string       Path to the wordlist. Set to - to use STDIN.
      --wordlist-offset int   Resume from a given position in the wordlist (defaults to 0)

Use "gobuster [command] --help" for more information about a command.
```

The help page contains multiple sections:

- **_Usage_**: Shows the syntax on how to use the command.
    
- **_Available Commands_**: Multiple commands are available to aid us in enumerating directories, files, DNS subdomains, Google Cloud Storage buckets, and Amazon AWS S3 buckets. Throughout this room, we will focus on the dir, dns, and vhost commands. We will cover each of them in the following tasks.

- **_Flags_**: These are specific options we can configure to customize our commands. Let’s look at the flags we will often use throughout this room: 

| Short Flag | Long Flag   | Description |
|------------|-------------|-------------|
| `-t`       | `--threads` | Configures the number of threads to use for the scan. Each thread sends out requests with a slight delay. Default is 10. Increase for large wordlists if system resources allow. |
| `-w`       | `--wordlist`| Specifies the wordlist to use for iterating. Each word is appended to the target URL. |
|            | `--delay`   | Sets the time to wait between requests. Useful to avoid detection by rate-limiting mechanisms on the server. |
|            | `--debug`   | Enables debug output to help troubleshoot errors or unexpected behavior. |
| `-o`       | `--output`  | Writes scan results to the specified output file. |


Example

Let us look at an example of how we would use these commands and flags together to enumerate a web directory:

`gobuster dir -u "http://www.example.thm/" -w /usr/share/wordlists/dirb/small.txt -t 64`


- `gobuster dir` indicates that we will use the directory and file enumeration mode.

- `-u "http://www.example.thm/"` tells Gobuster that the target URL is http://example.thm/.

- `-w /usr/share/wordlists/dirb/small.txt` directs Gobuster to use the small.txt wordlist to brute force the web directories. Gobuster will use each entry in the wordlist to form a new URL and send a GET request to that URL. If the first entry of the wordlist were images, Gobuster would send a GET request to http://example.thm/images/.

- `-t 64` sets the number of threads Gobuster will use to 64. This improves the performance drastically.

Now that we have a quick overview of Gobuster, let’s explore the different modes and their use cases in the following tasks.

**Answer the questions below**

1. _What flag do we use to specify the target URL?_

Answer: `-u`

2. _What command do we use for the subdomain enumeration mode?_

Answer: `dns`

------------------------------------------------------------------------------------------------------------------------------------------------


**Module 4: Use Case: Directory and File Enumeration**

Gobuster has a dir mode, allowing users to enumerate website directories and their files. This mode is useful when you are performing a penetration test and would like to see what the directory structure of a website is and what files it contains. Often, directory structures of websites and web apps follow a particular convention, making them susceptible to Brute Force using wordlists. For example, the  directory structure on the web server hosting WordPress looks something  like this:

```
           
root@tryhackme:~# tree -L 3 -d
.
└── html
    └── wordpress
        ├── wp-admin
        ├── wp-content
        └── wp-includes
```

Gobuster is powerful because it allows you to scan the website and return the status codes. These status codes immediately tell you if you, as an outside user, can request that directory or not.

**Help**

If you want a complete overview of what the `Gobuster dir` command can offer, you can look at the help page. Seeing the extensive help page for the dir command can somewhat be intimidating. So, we will focus on the most essential flags in this room. Type the following command to display the help: gobuster dir --help.

Many flags are used to fine-tune the gobuster dir command. It is out of scope to go over each one of them, but in the table below, we have listed the flags that cover most of the scenarios:

| Flag  | Long Flag                | Description                                                                                                                    |
|-------|--------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| `-c`  | `--cookies`              | Configures a cookie to pass along with each request, such as a session ID.                                                    |
| `-x`  | `--extensions`           | Specifies which file extensions to scan for, e.g., `.php`, `.js`.                                                             |
| `-H`  | `--headers`              | Configures an entire header to include with each request.                                                                      |
| `-k`  | `--no-tls-validation`    | Skips TLS certificate validation, useful for self-signed certificates often found in CTFs or test environments.                |
| `-n`  | `--no-status`            | Hides status codes of each response to keep output cleaner.                                                                    |
| `-P`  | `--password`             | Used with `--username` to provide a password for authenticated requests.                                                       |
| `-s`  | `--status-codes`         | Specifies which HTTP status codes to display (e.g., `200`, or a range like `300-400`).                                         |
| `-b`  | `--status-codes-blacklist` | Specifies status codes to exclude from output, overriding the `-s` flag.                                                     |
| `-U`  | `--username`             | Used with `--password` to provide a username for authenticated requests.                                                       |
| `-r`  | `--followredirect`       | Configures Gobuster to follow HTTP redirects (e.g., 301 or 302 responses).                                                     |


How To Use dir Mode

To run Gobuster in dir mode, use the following command format:

`gobuster dir -u "http://www.example.thm" -w /path/to/wordlist`

Notice that the command also includes the flags -u and -w, in addition to the dir keyword. These two flags are required for the Gobuster directory enumeration to work. Let us look at a practical example of how to enumerate directories and files with Gobuster dir mode:

`gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -r`

This command scans all the directories located at www.example.thm using the wordlist directory-list-2.3-medium.txt. Let’s look a bit closer at each part of the command:

- `gobuster dir`: Configures Gobuster to use the directory and file enumeration mode.

- `-u http://www.example.thm`: The URL will be the base path where Gobuster starts looking. So, the URL  above is using the root web directory. For example, in a typical Apache installation on Linux, this is /var/www/html. So if you have a “resources” directory and you want to enumerate that directory, you’d set the URL as http://www.example.thm/resources. You can also think of this like http://www.example.thm/path/to/folder.

- The URL must contain the protocol used, in this case, HTTP. This is important and required. If you pass the wrong protocol, the scan will fail.

- In the host part of the URL, you can either fill in the IP or the HOSTNAME. However, it is important to mention that when using the IP, you may target a different website than intended. A web server can host multiple websites using one IP (this technique is also called virtual hosting). Use the HOSTNAME if you want to be sure.

- Gobuster does not enumerate recursively. So, if the results show a directory path you are interested in, you will have to enumerate that specific directory.

- `-w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt` configures Gobuster to use the directory-list-2.3-medium.txt wordlist to enumerate. Each entry of the wordlist is appended to the configured URL.

- `-r` configures Gobuster to follow the redirect responses received from the sent requests. If a status code 301 was received, Gobuster will navigate to the redirect URL that is included in the response.

Let’s look at a second example where we use the -x flag to specify what type of files we want to enumerate:

`gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x .php,.js`

This command will look for directories located at http://example.thm using the wordlist directory-list-2.3-medium.txt. In addition to directory listing, this command also lists all the files that have a .php or .js extension.

**Answer the questions below**

1. _Which flag do we have to add to our command to skip the TLS verification? Enter the long flag notation._

Answer: `--no-tls-validation`

2. _Enumerate the directories of www.offensivetools.thm. Which directory catches your attention?_

Answer: `secret`

**_Explanation:_**

We use this command `gobuster dir -u "www.offensivetools.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt`

And we see a directory called `secret`

<img width="595" height="145" alt="image" src="https://github.com/user-attachments/assets/ff04a0b7-6538-4ac6-945f-b01b800b0855" />

3. _Continue enumerating the directory found in question 2. You will find an interesting file there with a .js extension. What is the flag found in this file?_

Answer: `THM{ReconWasASuccess}`

We use the command `gobuster dir -u "www.offensivetools.thm/secret" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x .js` and see a file named "flag.js"

<img width="976" height="556" alt="image" src="https://github.com/user-attachments/assets/586d12f0-40d0-4b2c-82f7-937c96a3eb6a" />

Now we use curl to get our flag

`curl http://www.offensivetools.thm/secret/flag.js`

<img width="887" height="72" alt="image" src="https://github.com/user-attachments/assets/026b917b-66ed-4896-86c2-f6714ad91c26" />


------------------------------------------------------------------------------------------------------------------------------------------------

