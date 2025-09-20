Link: https://tryhackme.com/room/fileinc

<img width="2250" height="2250" alt="image" src="https://github.com/user-attachments/assets/87a0fbd9-2528-4b09-a2d5-8772b2f88ed6" />

This room introduces file inclusion vulnerabilities, including Local File Inclusion (LFI), Remote File Inclusion (RFI), and directory traversal.

**Task 1: Introduction**

What is File inclusion?

This room aims to equip you with the essential knowledge to exploit file inclusion vulnerabilities, including Local File Inclusion (LFI), Remote File Inclusion (RFI), and directory traversal. Also, we will discuss the risk of these vulnerabilities if they're found and the required remediation. We provide some practical examples of each vulnerability as well as hands-on challenges.

In some scenarios, web applications are written to request access to files on a given system, including images, static text, and so on via parameters. Parameters are query parameter strings attached to the URL that could be used to retrieve data or perform actions based on user input. The following diagram breaks down the essential parts of a URL.

<img width="716" height="340" alt="image" src="https://github.com/user-attachments/assets/77033638-9753-4d31-96fc-b980566aa652" />

For example, parameters are used with Google searching, where GET requests pass user input into the search engine. https://www.google.com/search?q=TryHackMe. If you are not familiar with the topic, you can view the How The Web Works module to understand the concept.  

Let's discuss a scenario where a user requests to access files from a webserver. First, the user sends an HTTP request to the webserver that includes a file to display. For example, if a user wants to access and display their CV within the web application, the request may look as follows, http://webapp.thm/get.php?file=userCV.pdf, where the file is the parameter and the userCV.pdf, is the required file to access.

<img width="1792" height="828" alt="image" src="https://github.com/user-attachments/assets/cb63421a-8416-43fd-9a67-cdd27b891a52" />

**Why do File inclusion vulnerabilities happen?**

File inclusion vulnerabilities are commonly found and exploited in various programming languages for web applications, such as PHP that are poorly written and implemented. The main issue of these vulnerabilities is the input validation, in which the user inputs are not sanitized or validated, and the user controls them. When the input is not validated, the user can pass any input to the function, causing the vulnerability.
 
**What is the risk of File inclusion?**

By default, an attacker can leverage file inclusion vulnerabilities to leak data, such as code, credentials or other important files related to the web application or operating system. Moreover, if the attacker can write files to the server by any other means, file inclusion might be used in tandem to gain remote command execution (RCE).



**Answer the questions below**

1. _Let's continue to the next section to deploy the attached VM._

Answer: No answer needed

---

**Task 2: Deploy the VM**

Deploy the attached VM to follow and apply the technique as well as do the challenges. In order to access this VM, please make sure to connect to the TryHackMe network via OpenVPN or access it directly from the AttackBox, which can be launched by clicking the blue button on the top-right.

Please visit the link http://MACHINE_IP/, which will show you the following page:

<img width="1152" height="579" alt="image" src="https://github.com/user-attachments/assets/c903a71c-134a-4baf-b174-e9fd1fffcd83" />

**Answer the questions below**

1. _Once you've deployed the VM, please wait a few minutes for the webserver to start, then progress to the next section!_

Answer:  No answer needed

---

**Task 3: Path Traversal**

**Path Traversal**

Also known as Directory traversal, a web security vulnerability allows an attacker to read operating system resources, such as local files on the server running an application. The attacker exploits this vulnerability by manipulating and abusing the web application's URL to locate and access files or directories stored outside the application's root directory.>

Path traversal vulnerabilities occur when the user's input is passed to a function such as file_get_contents in PHP. It's important to note that the function is not the main contributor to the vulnerability. Often poor input validation or filtering is the cause of the vulnerability. In PHP, you can use the file_get_contents to read the content of a file. You can find more information about the function [here](https://www.php.net/manual/en/function.file-get-contents.php).

The following graph shows how a web application stores files in /var/www/app. The happy path would be the user requesting the contents of userCV.pdf from a defined path /var/www/app/CVs.

<img width="1596" height="684" alt="image" src="https://github.com/user-attachments/assets/c52cf744-8d2d-4021-ba3d-1394b8d57d4b" />

We can test out the URL parameter by adding payloads to see how the web application behaves. Path traversal attacks, also known as the dot-dot-slash attack, take advantage of moving the directory one step up using the double dots ../. If the attacker finds the entry point, which in this case `get.php?file=`, then the attacker may send something as follows, `http://webapp.thm/get.php?file=../../../../etc/passwd`

<img width="714" height="610" alt="image" src="https://github.com/user-attachments/assets/d01d4560-91f7-4db5-a74d-7709379066ba" />

As a result, the web application sends back the file's content to the user.

<img width="1850" height="918" alt="image" src="https://github.com/user-attachments/assets/3cac0a83-56ff-400b-a7b8-8edd34495191" />

Similarly, if the web application runs on a Windows server, the attacker needs to provide Windows paths. For example, if the attacker wants to read the boot.ini file located in c:\boot.ini, then the attacker can try the following depending on the target OS version:

`http://webapp.thm/get.php?file=../../../../boot.ini` or

`http://webapp.thm/get.php?file=../../../../windows/win.ini`

The same concept applies here as with Linux operating systems, where we climb up directories until it reaches the root directory, which is usually .

Sometimes, developers will add filters to limit access to only certain files or directories. Below are some common OS files you could use when testing.

| Location                          | Description                                                                 |
|-----------------------------------|-----------------------------------------------------------------------------|
| `/etc/issue`                      | Contains a message or system identification to be printed before the login prompt. |
| `/etc/profile`                    | Controls system-wide default variables, such as export variables, file creation mask (umask), terminal types, and mail notifications. |
| `/proc/version`                   | Specifies the version of the Linux kernel.                                  |
| `/etc/passwd`                     | Has all registered users that have access to a system.                      |
| `/etc/shadow`                     | Contains information about the system's users' passwords.                   |
| `/root/.bash_history`            | Contains the history of commands for the root user.                         |
| `/var/log/dmessage`              | Contains global system messages, including messages logged during system startup. |
| `/var/mail/root`                 | Stores all emails for the root user.                                        |
| `/root/.ssh/id_rsa`              | Private SSH keys for the root or any known valid user on the server.        |
| `/var/log/apache2/access.log`    | Contains the accessed requests for the Apache web server.                   |
| `C:\boot.ini`                    | Contains the boot options for computers with BIOS firmware.                 |

**Answer the questions below**

1. _What function causes path traversal vulnerabilities in PHP?_

Answer: `file_get_contents`

---

**Task 4: Local File Inclusion - LFI**

Local File Inclusion (LFI)

LFI attacks against web applications are often due to a developers' lack of security awareness. With PHP, using functions such as include, require, include_once, and require_once often contribute to vulnerable web applications. In this room, we'll be picking on PHP, but it's worth noting LFI vulnerabilities also occur when using other languages such as ASP, JSP, or even in Node.js apps. LFI exploits follow the same concepts as path traversal.

In this section, we will walk you through various LFI scenarios and how to exploit them.

#1. Suppose the web application provides two languages, and the user can select between the EN and AR

```
<?PHP 
	include($_GET["lang"]);
?>
```

The PHP code above uses a GET request via the URL parameter lang to include the file of the page. The call can be done by sending the following HTTP request as follows: http://webapp.thm/index.php?lang=EN.php to load the English page or http://webapp.thm/index.php?lang=AR.php to load the Arabic page, where EN.php and AR.php files exist in the same directory.

Theoretically, we can access and display any readable file on the server from the code above if there isn't any input validation. Let's say we want to read the /etc/passwd file, which contains sensitive information about the users of the Linux operating system, we can try the following: http://webapp.thm/get.php?file=/etc/passwd

In this case, it works because there isn't a directory specified in the include function and no input validation.

Now apply what we discussed and try to read /etc/passwd file. Also, answer question #1 below.

#2. Next, In the following code, the developer decided to specify the directory inside the function.

```
<?PHP 
	include("languages/". $_GET['lang']); 
?>
```

In the above code, the developer decided to use the include function to call PHP pages in the languages directory only via lang parameters.

If there is no input validation, the attacker can manipulate the URL by replacing the lang input with other OS-sensitive files such as /etc/passwd.

Again the payload looks similar to the path traversal, but the include function allows us to include any called files into the current page. The following will be the exploit:

`http://webapp.thm/index.php?lang=../../../../etc/passwd`

Now apply what we discussed, try to read files within the server, and figure out the directory specified in the include function and answer question #2 below.

**Answer the questions below**

1. _Give Lab #1 a try to read /etc/passwd. What would the request URI be?_

Answer: `/lab1.php?file=/etc/passwd`

**_Explanation:_**

We visit MACHINE_IP and see something like this

<img width="1383" height="689" alt="image" src="https://github.com/user-attachments/assets/f4720699-96c1-45bc-9cac-0aa820c0b808" />

Now we click on Lab #1 and see something like below

<img width="1464" height="423" alt="image" src="https://github.com/user-attachments/assets/63fc5ce8-680b-4ad8-905c-a9d3206cdcc5" />

We type /etc/passwd in the input field and we get the URL

<img width="1734" height="714" alt="image" src="https://github.com/user-attachments/assets/cc062215-9f8f-49e2-a88c-10e75e4ccfc9" />

2. _In Lab #2, what is the directory specified in the include function?_

Answer: `includes`

**_Explanation:_**

We visit Lab #2 and press enter without typing the file name

<img width="1370" height="621" alt="image" src="https://github.com/user-attachments/assets/e42333b5-d0ad-4319-afbc-17b152046b93" />

---


**Task 5: Local File Inclusion - LFI Continued**

In this task, we go a little bit deeper into LFI. We discussed a couple of techniques to bypass the filter within the include function.

#3. In the first two cases, we checked the code for the web app, and then we knew how to exploit it. However, in this case, we are performing black box testing, in which we don't have the source code. In this case, errors are significant in understanding how the data is passed and processed into the web app.

In this scenario, we have the following entry point: http://webapp.thm/index.php?lang=EN. If we enter an invalid input, such as THM, we get the following error

```
Warning: include(languages/THM.php): failed to open stream: No such file or directory in /var/www/html/THM-4/index.php on line 12
```

The error message discloses significant information. By entering THM as input, an error message shows what the include function looks like: include(languages/THM.php);.

If you look at the directory closely, we can tell the function includes files in the languages directory is adding .php at the end of the entry. Thus the valid input will be something as follows: index.php?lang=EN, where the file EN is located inside the given languages directory and named EN.php.

Also, the error message disclosed another important piece of information about the full web application directory path which is /var/www/html/THM-4/.

To exploit this, we need to use the ../ trick, as described in the directory traversal section, to get out the current folder. Let's try the following:

http://webapp.thm/index.php?lang=../../../../etc/passwd

Note that we used 4 ../ because we know the path has four levels /var/www/html/THM-4. But we still receive the following error:

```
Warning: include(languages/../../../../../etc/passwd.php): failed to open stream: No such file or directory in /var/www/html/THM-4/index.php on line 12
```

It seems we could move out of the PHP directory but still, the include function reads the input with .php at the end! This tells us that the developer specifies the file type to pass to the include function. To bypass this scenario, we can use the NULL BYTE, which is %00.

Using null bytes is an injection technique where URL-encoded representation such as %00 or 0x00 in hex with user-supplied data to terminate strings. You could think of it as trying to trick the web app into disregarding whatever comes after the Null Byte.

By adding the Null Byte at the end of the payload, we tell the include function to ignore anything after the null byte which may look like:

`include("languages/../../../../../etc/passwd%00").".php");` which is equivalent to `include("languages/../../../../../etc/passwd");`






