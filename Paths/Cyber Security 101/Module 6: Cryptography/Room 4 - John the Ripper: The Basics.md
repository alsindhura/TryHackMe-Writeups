Link: https://tryhackme.com/room/johntheripperbasics (Premium Room)

<img width="1201" height="1200" alt="image" src="https://github.com/user-attachments/assets/c43cf534-bcac-40a2-861a-148ca1f1253f" />

Learn how to use John the Ripper, a powerful and adaptable hash-cracking tool.

**Module 1: Introduction**

John the Ripper is a well-known, well-loved, and versatile hash-cracking tool. It combines a fast cracking speed with an extraordinary range of compatible hash types.
Learning Prerequisites

For maximum benefit, we recommend you attempt this room after the first three introductory rooms about cryptography.


- [Cryptography Basics](https://tryhackme.com/r/room/cryptographybasics)

- [ Public Key Cryptography Basics](https://tryhackme.com/r/room/publickeycrypto)
    
- [Hashing Basics](https://tryhackme.com/r/room/hashingbasics)

There are no other learning prerequisites except basic command line abilities.

**Learning Objectives**

Upon the completion of this room, you learn about using John for:

- Cracking Windows authentication hashes

- Crack `/etc/shadow` hashes

- Cracking password-protected Zip files

- Cracking password-protected RAR files

- Cracking SSH keys

Starting with Task 4, you need to apply either on the attached VM, the AttackBox, or your own system. For your convenience, you can download the required task files as a single Zip file from this task by pressing the Download Task Files button below.

**Answer the questions below**

1. _Let’s begin!_

Answer: No answer needed

-----------------------------------------------------------------------------------------------------------------------------------------------

**Module 2: Basic Terms**

This room requires basic knowledge of various cryptography terms. For your convenience, we review the most relevant terms and concepts before we move into practical hash cracking.

**What are Hashes?**

A hash is a way of taking a piece of data of any length and representing it in another fixed-length form. This process masks the original value of the data. The hash value is obtained by running the original data through a hashing algorithm. Many popular hashing algorithms exist, such as MD4, MD5, SHA1 and NTLM. Let’s try and show this with an example:

If we take “polo”, a string of four characters, and run it through an MD5 hashing algorithm, we end up with an output of `b53759f3ce692de7aff1b5779d3964da`, a standard 32-character MD5 hash.

Likewise, if we take “polomints”, a string of 9 characters, and run it through the same MD5 hashing algorithm, we end up with an output of `584b6e4f4586e136bc280f27f9c64f3b`, another standard 32-character MD5 hash.

**What Makes Hashes Secure?**

Hashing functions are designed as one-way functions. In other words, it is easy to calculate the hash value of a given input; however, it is a hard problem to find the original input given the hash value. In simple terms, a hard problem quickly becomes computationally infeasible in computer science. This computational problem has its roots in mathematics as P vs NP.

In computer science, P and NP are two classes of problems that help us understand the efficiency of algorithms:

- P (Polynomial Time): Class P covers the problems whose solution can be found in polynomial time. Consider sorting a list in increasing order. The longer the list, the longer it would take to sort; however, the increase in time is not exponential.

- NP (Non-deterministic Polynomial Time): Problems in the class NP are those for which a given solution can be checked quickly, even though finding the solution itself might be hard. In fact, we don’t know if there is a fast algorithm to find the solution in the first place.

While this is a fascinating mathematical concept that proves fundamental to computing and cryptography, it is entirely outside the scope of this room. But abstractly, the algorithm to hash the value will be “P” and can, therefore, be calculated reasonably. However, an “un-hashing” algorithm would be “NP” and intractable to solve, meaning that it cannot be computed in a reasonable time using standard computers.


**Where John Comes in**

Even though the algorithm is not feasibly reversible, that doesn’t mean cracking the hashes is impossible. If you have the hashed version of a password, for example, and you know the hashing algorithm, you can use that hashing algorithm to hash a large number of words, called a dictionary. You can then compare these hashes to the one you’re trying to crack to see if they match. If they do, you know what word corresponds to that hash- you’ve cracked it!

This process is called a dictionary attack, and John the Ripper, or John as it’s commonly shortened, is a tool for conducting fast brute force attacks on various hash types.

**Learning More**

For some more in-depth material on encryption and decryption, we recommend the [Cryptography Basics](https://tryhackme.com/r/room/cryptographybasics) and the [Public Key Cryptography Basics](https://tryhackme.com/r/room/publickeycrypto) rooms; moreover, for hashing, we recommend the [Hashing Basics](https://tryhackme.com/r/room/hashingbasics) room.

This room will focus on the most popular extended version of John the Ripper, **Jumbo John**.

**Answer the questions below**

1. _What is the most popular extended version of John the Ripper?_

Answer: `Jumbo John`

-----------------------------------------------------------------------------------------------------------------------------------------------

**Module 3: Setting Up Your System**

Throughout the tasks of this room, we will be using the following :

- The “Jumbo John” version of John the Ripper

- The RockYou password list

If you use the attached virtual machine or the AttackBox, you don’t need to install John the Ripper on your system. Consequently, feel free to skip through the installation section. If you prefer to use your system to follow along, please read along to learn how to proceed with the installation. We should note that if you use a version of John the Ripper other than Jumbo John, you might not have some of the required tools, such as `zip2john` and `rar2john`.

**Installation**

John the Ripper is supported on many Operating Systems, not just Linux Distributions. Before we go through this, there are multiple versions of John, the standard “core” distribution, and multiple community editions, which extend the feature set of the original John distribution. The most popular of these distributions is the “Jumbo John,” which we will use specific features of later.

**AttackBox and Kali**

Jumbo John is already installed on the attached virtual machine and on the AttackBox, so if you plan to use either one, you need not take any further action. Furthermore, offensive Linux distributions like Kali are shipped with Jumbo John installed.

You can double-check this by typing `john` into the terminal. You should be met with a usage guide for John, with the first line reading “John the Ripper 1.9.0-jumbo-1” or something similar with a different version number.

**Other Linux Distributions**

Many Linux distributions have John the Ripper available for installation from their official repositories. For instance, on Fedora Linux, you can install John the Ripper with `sudo dnf install john`, while on Ubuntu, you can install it with `sudo apt install john`. Unfortunately, at the time of writing, these versions provided core functionality and missed some of the tools available through Jumbo John.

Consequently, you need to consider building from the source to access all the tools available via Jumbo John. The [official installation guide](https://github.com/openwall/john/blob/bleeding-jumbo/doc/INSTALL) provides detailed installation and build configuration instructions.

**Installing on Windows**

To install Jumbo John the Ripper on Windows, you need to download and install the zipped binary for either 64-bit systems [here](https://www.openwall.com/john/k/john-1.9.0-jumbo-1-win64.zip) or for 32-bit systems [here](https://www.openwall.com/john/k/john-1.9.0-jumbo-1-win32.zip).

**Wordlists**

Now that we have `john` ready, we must consider another indispensable component: wordlists.

As we mentioned earlier, to use a dictionary attack against hashes, you need a list of words to hash and compare; unsurprisingly, this is called a wordlist. There are many different wordlists out there, and a good collection can be found in the SecLists repository. There are a few places you can look for wordlists for attacking the system of choice; we will quickly run through where you can find them.

On the AttackBox and Kali Linux distributions, the `/usr/share/wordlists` directory contains a series of great wordlists.

**RockYou**

For all of the tasks in this room, we will use the infamous `rockyou.txt` wordlist, a very large common password wordlist obtained from a data breach on a website called `rockyou.com` in 2009. If you are not using any of the above distributions, you can get the rockyou.txt wordlist from the [SecLists](https://github.com/danielmiessler/SecLists) repository under the `/Passwords/Leaked-Databases` subsection. You may need to extract it from the `.tar.gz` format using `tar xvzf rockyou.txt.tar.gz`.

Now that we have our hash cracker and wordlists all set up, let’s move on to some hash cracking!

To follow along, first, let’s start the Virtual Machine by pressing the Start Machine button below.

You can also access the virtual machine using SSH at the IP address MACHINE_IP using the following credentials:

- Username: user

- Password: Tryhackme123!

**Answer the questions below**

1. _Which website’s breach was the `rockyou.txt` wordlist created from?_

Answer: `rockyou.com`

----------------------------------------------------------------------------------------------------------------------------------------------

**Module 4: Cracking Basic Hashes**

There are multiple ways to use John the Ripper to crack simple hashes. We’ll walk through a few before moving on to cracking some ourselves.

**John Basic Syntax**

The basic syntax of John the Ripper commands is as follows. We will cover the specific options and modifiers used as we use them.

`john [options] [file path]`

- `john`: Invokes the John the Ripper program

- `[options]`: Specifies the options you want to use

- `[file path]`: The file containing the hash you’re trying to crack; if it’s in the same directory, you won’t need to name a path, just the file.

**Automatic Cracking**

John has built-in features to detect what type of hash it’s being given and to select appropriate rules and formats to crack it for you; this isn’t always the best idea as it can be unreliable, but if you can’t identify what hash type you’re working with and want to try cracking it, it can be a good option! To do this, we use the following syntax:

`john --wordlist=[path to wordlist] [path to file]`

    
- `--wordlist=`: Specifies using wordlist mode, reading from the file that you supply in the provided path

- `[path to wordlist]`: The path to the wordlist you’re using, as described in the previous task

**Example Usage:**

`john --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt`

**Identifying Hashes**

Sometimes, John won’t play nicely with automatically recognising and loading hashes, but that’s okay! We can use other tools to identify the hash and then set John to a specific format. There are multiple ways to do this, such as using an online hash identifier like [this site](https://hashes.com/en/tools/hash_identifier). I like to use a tool called [hash-identifier](https://gitlab.com/kalilinux/packages/hash-identifier/-/tree/kali/master), a Python tool that is super easy to use and will tell you what different types of hashes the one you enter is likely to be, giving you more options if the first one fails.

To use hash-identifier, you can use `wget` or `curl` to download the Python file `hash-id.py` from its GitLab page. Then, launch it with `python3 hash-id.py` and enter the hash you’re trying to identify. It will give you a list of the most probable formats. These two steps are shown in the terminal below.

```     
user@TryHackMe$ wget https://gitlab.com/kalilinux/packages/hash-identifier/-/raw/kali/master/hash-id.py
$ python3 hash-id.py
   #########################################################################
   #     __  __                     __           ______    _____           #
   #    /\ \/\ \                   /\ \         /\__  _\  /\  _ `\         #
   #    \ \ \_\ \     __      ____ \ \ \___     \/_/\ \/  \ \ \/\ \        #
   #     \ \  _  \  /'__`\   / ,__\ \ \  _ `\      \ \ \   \ \ \ \ \       #
   #      \ \ \ \ \/\ \_\ \_/\__, `\ \ \ \ \ \      \_\ \__ \ \ \_\ \      #
   #       \ \_\ \_\ \___ \_\/\____/  \ \_\ \_\     /\_____\ \ \____/      #
   #        \/_/\/_/\/__/\/_/\/___/    \/_/\/_/     \/_____/  \/___/  v1.2 #
   #                                                             By Zion3R #
   #                                                    www.Blackploit.com #
   #                                                   Root@Blackploit.com #
   #########################################################################
--------------------------------------------------
 HASH: 2e728dd31fb5949bc39cac5a9f066498

Possible Hashs:
[+] MD5
[+] Domain Cached Credentials - MD4(MD4(($pass)).(strtolower($username)))
```

**Format-Specific Cracking**

Once you have identified the hash that you’re dealing with, you can tell John to use it while cracking the provided hash using the following syntax:

`john --format=[format] --wordlist=[path to wordlist] [path to file]`

- `--format=`: This is the flag to tell John that you’re giving it a hash of a specific format and to use the following format to crack it

- `[format]`: The format that the hash is in

**Example Usage:**

`john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt`

**A Note on Formats:**

When you tell John to use formats, if you’re dealing with a standard hash type, e.g. md5 as in the example above, you have to prefix it with `raw-` to tell John you’re just dealing with a standard hash type, though this doesn’t always apply. To check if you need to add the prefix or not, you can list all of John’s formats using `john --list=formats` and either check manually or grep for your hash type using something like `john --list=formats | grep -iF "md5"`.

**Practical**

Now that you know the syntax, modifiers, and methods for cracking basic hashes, try it yourself! The files are located in `~/John-the-Ripper-The-Basics/Task04/` on the attached virtual machine.

**Answer the questions below**

1. _What type of hash is hash1.txt?_

Answer: `md5`

**_Explanation:_**

We go the path `~/John-the-Ripper-The-Basics/Task04/` and we use `cat` to get the hash from the fie hash1.txt


<img width="911" height="121" alt="image" src="https://github.com/user-attachments/assets/8201f48c-efce-46c9-afc8-48cbe69a6fac" />

Now we noticed from the above image there's a file called `hash-id.py` and we use it to get the type of hash present in the hash1.txt file

`python3 hash-id.py`

and now we enter the hash from the hash1.txt 

<img width="913" height="894" alt="image" src="https://github.com/user-attachments/assets/d73505b5-f539-46a2-a0f6-1e5a6bbcc608" />

we can see that md5 is the hash type

2. _What is the cracked value of hash1.txt?_

Answer: `biscuit`

**_Explanation:_**

We use the following command

`john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash1.txt`

<img width="912" height="413" alt="image" src="https://github.com/user-attachments/assets/b47740da-302e-4ac1-9f80-b756c6de9b51" />

3. _What type of hash is hash2.txt?_

Answer: `sha1` (without dash)

**_Explanation:_**

We use `hash-id.py` on hash2.txt

<img width="916" height="928" alt="image" src="https://github.com/user-attachments/assets/6a9160f7-8dbc-4b55-b4c2-f07311043993" />

4. _What is the cracked value of hash2.txt?_

Answer: `kangeroo`

**_Explanation:_**

We use the following command

`john --format=raw-sha1 --wordlist=/usr/share/wordlists/rockyou.txt hash2.txt`

<img width="910" height="406" alt="image" src="https://github.com/user-attachments/assets/c91e896c-abaa-4382-b03e-8a7717970fd1" />


5. _What type of hash is hash3.txt?_

Answer: `sha256` (without dash)

**_Explanation:_**

We use `hash-id.py` on hash3.txt

<img width="916" height="925" alt="image" src="https://github.com/user-attachments/assets/623dc48a-cebb-49a9-97ea-3f0fd5df4787" />

6. _What is the cracked value of hash3.txt?_

Answer: `microphone`

**_Explanation:_**

We use the following command

`john --format=raw-sha256 --wordlist=/usr/share/wordlists/rockyou.txt hash3.txt`

<img width="916" height="419" alt="image" src="https://github.com/user-attachments/assets/9ba164b2-dd39-4837-952c-6204cba098c9" />

7. _What type of hash is hash4.txt?_

Answer: `whirlpool`

**_Explanation:_**

We use `hash-id.py` on hash4.txt

<img width="915" height="995" alt="image" src="https://github.com/user-attachments/assets/63e851ab-47e9-4068-a1f1-ad0e016c0303" />


8. _What is the cracked value of hash4.txt?_

Answer: `colossal`

**_Explanation:_**

We use the following command

`john --format=whirlpool --wordlist=/usr/share/wordlists/rockyou.txt hash4.txt`

<img width="908" height="393" alt="image" src="https://github.com/user-attachments/assets/0a7848eb-ba56-4116-ba4a-6f155fdad69e" />

----------------------------------------------------------------------------------------------------------------------------------------------

**Module 5: Cracking Windows Authentication Hashes**

Now that we understand the basic syntax and usage of John the Ripper, let’s move on to cracking something a little bit more complicated, something that you may even want to attempt if you’re on an actual Penetration Test or Red Team engagement. Authentication hashes are the hashed versions of passwords stored by operating systems; it is sometimes possible to crack them using our brute-force methods. To get your hands on these hashes, you must often already be a privileged user, so we will explain some of the hashes we plan on cracking as we attempt them.

**NTHash / NTLM**

NThash is the hash format modern Windows operating system machines use to store user and service passwords. It’s also commonly referred to as NTLM, which references the previous version of Windows format for hashing passwords known as LM, thus NT/LM.

A bit of history: the NT designation for Windows products originally meant New Technology. It was used starting with Windows NT to denote products not built from the MS-DOS Operating System. Eventually, the “NT” line became the standard Operating System type to be released by Microsoft, and the name was dropped, but it still lives on in the names of some Microsoft technologies.

In Windows, SAM (Security Account Manager) is used to store user account information, including usernames and hashed passwords. You can acquire NTHash/NTLM hashes by dumping the SAM database on a Windows machine, using a tool like Mimikatz, or using the Active Directory database: `NTDS.dit`. You may not have to crack the hash to continue privilege escalation, as you can often conduct a “pass the hash” attack instead, but sometimes, hash cracking is a viable option if there is a weak password policy.
Practical

Now that you know the theory behind it, see if you can use the techniques we practised in the last task and the knowledge of what type of hash this is to crack the `ntlm.txt` file! The file is located in `~/John-the-Ripper-The-Basics/Task05/`.

**Answer the questions below**

1. _What do we need to set the `--format` flag to in order to crack this hash?_

Answer: `nt`

**_Explanation:_**

We visit the site and we find the format of the hash

<img width="916" height="126" alt="image" src="https://github.com/user-attachments/assets/af927247-9e5e-45a0-8491-f0ca4d6a5b8c" />

<img width="707" height="116" alt="image" src="https://github.com/user-attachments/assets/78749e46-ac49-4e4f-ad77-4adb21845345" />


2. _What is the cracked value of this password?_

Answer: `mushroom`

**_Explanation:_**

we use the following command to crack the hash

`john --format=nt --wordlist=/usr/share/wordlists/rockyou.txt ntlm.txt`

<img width="920" height="388" alt="image" src="https://github.com/user-attachments/assets/0b399d08-9221-40ab-96be-942cc22628cc" />

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 6: Cracking /etc/shadow Hashes**

**Cracking Hashes from /etc/shadow**

The `/etc/shadow` file is the file on Linux machines where password hashes are stored. It also stores other information, such as the date of last password change and password expiration information. It contains one entry per line for each user or user account of the system. This file is usually only accessible by the root user, so you must have sufficient privileges to access the hashes. However, if you do, there is a chance that you will be able to crack some of the hashes.


**Unshadowing**

John can be very particular about the formats it needs data in to be able to work with it; for this reason, to crack `/etc/shadow` passwords, you must combine it with the `/etc/passwd` file for John to understand the data it’s being given. To do this, we use a tool built into the John suite of tools called `unshadow`. The basic syntax of `unshadow` is as follows:

`unshadow [path to passwd] [path to shadow]`

- `unshadow`: Invokes the unshadow tool

- `[path to passwd]`: The file that contains the copy of the /etc/passwd file you’ve taken from the target machine

- `[path to shadow]`: The file that contains the copy of the /etc/shadow file you’ve taken from the target machine

**Example Usage:**

`unshadow local_passwd local_shadow > unshadowed.txt`

**Note on the files**

When using `unshadow`, you can either use the entire `/etc/passwd` and `/etc/shadow` files, assuming you have them available, or you can use the relevant line from each, for example:

**FILE 1 - local_passwd**

Contains the `/etc/passwd` line for the root user:

`root:x:0:0::/root:/bin/bash`

**FILE 2 - local_shadow**

Contains the `/etc/shadow` line for the root user: `root:$6$2nwjN454g.dv4HN/$m9Z/r2xVfweYVkrr.v5Ft8Ws3/YYksfNwq96UL1FX0OJjY1L6l.DS3KEVsZ9rOVLB/ldTeEL/OIhJZ4GMFMGA0:18576::::::`

**Cracking**

We can then feed the output from `unshadow`, in our example use case called `unshadowed.txt`, directly into John. We should not need to specify a mode here as we have made the input specifically for John; however, in some cases, you will need to specify the format as we have done previously using: `--format=sha512crypt`

`john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt`

**Practical**

Now, see if you can follow the process to crack the password hash of the root user provided in the `etchashes.txt` file. Good luck! The files are located in `~/John-the-Ripper-The-Basics/Task06/`.

**Answer the questions below**

1. _What is the root password?_

Answer: `1234`

**_Explanation:_**

We will use unshadow command and create a text.txt file with the command below:

`unshadow local_passwd local_shadow > text.txt`

Now we will use john on text.txt file and get the password

`john --wordlist=/usr/share/wordlists/rockyou.txt text.txt`

<img width="913" height="517" alt="image" src="https://github.com/user-attachments/assets/13a35c79-c5c2-4a36-8522-c950a7edf93f" />

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


**Module 7: Single Crack Mode**

So far, we’ve been using John’s wordlist mode to brute-force simple and not-so-simple hashes. But John also has another mode, called the Single Crack mode. In this mode, John uses only the information provided in the username to try and work out possible passwords heuristically by slightly changing the letters and numbers contained within the username.

**Word Mangling**

The best way to explain Single Crack mode and word mangling is to go through an example:

Consider the username “Markus”.

Some possible passwords could be:

- Markus1, Markus2, Markus3 (etc.)

- MArkus, MARkus, MARKus (etc.)

- Markus!, Markus$, Markus* (etc.)

This technique is called word mangling. John is building its dictionary based on the information it has been fed and uses a set of rules called “mangling rules,” which define how it can mutate the word it started with to generate a wordlist based on relevant factors for the target you’re trying to crack. This exploits how poor passwords can be based on information about the username or the service they’re logging into.

**GECOS**

John’s implementation of word mangling also features compatibility with the GECOS field of the UNIX operating system, as well as other UNIX-like operating systems such as Linux. GECOS stands for General Electric Comprehensive Operating System. In the last task, we looked at the entries for both `/etc/shadow` and `/etc/passwd`. Looking closely, you will notice that the fields are separated by a colon `:`. The fifth field in the user account record is the GECOS field. It stores general information about the user, such as the user’s full name, office number, and telephone number, among other things. John can take information stored in those records, such as full name and home directory name, to add to the wordlist it generates when cracking `/etc/shadow` hashes with single crack mode.

**Using Single Crack Mode**

To use single crack mode, we use roughly the same syntax that we’ve used so far; for example, if we wanted to crack the password of the user named “Mike”, using the single mode, we’d use:

`john --single --format=[format] [path to file]`

- `--single`: This flag lets John know you want to use the single hash-cracking mode
  
- `--format=[format]`: As always, it is vital to identify the proper format.

**Example Usage:**

`john --single --format=raw-sha256 hashes.txt`

**A Note on File Formats in Single Crack Mode:**

If you’re cracking hashes in single crack mode, you need to change the file format that you’re feeding John for it to understand what data to create a wordlist from. You do this by prepending the hash with the username that the hash belongs to, so according to the above example, we would change the file `hashes.txt`

From `1efee03cdcb96d90ad48ccc7b8666033`

To `mike:1efee03cdcb96d90ad48ccc7b8666033`

**Practical**

Now that you’re familiar with the Syntax for John’s single crack mode, access the hash and crack it, assuming that the user it belongs to is called “Joker”. The file is located in `~/John-the-Ripper-The-Basics/Task07/`.

**Answer the questions below**

1. _What is Joker’s password?_

Answer: `Jok3r`

**_Explanation:_**

First we find the hash format 

<img width="918" height="988" alt="image" src="https://github.com/user-attachments/assets/98d1d394-a1b5-4c4b-a15c-c025cebb8b1d" />

we see the username is `joker` from the question

and now we create a file called `text.txt` and add the username:hash 

<img width="891" height="173" alt="image" src="https://github.com/user-attachments/assets/1596f287-296e-48e4-9d2f-6bdf36bba020" />

Now we use the following command to crack the file text.txt

`john --single --format=raw-md5 text.txt`

<img width="881" height="430" alt="image" src="https://github.com/user-attachments/assets/b69c06ab-06b9-4677-bb10-d7ed6173e8dc" />

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 8: Custom Rules**

**What are Custom Rules?**

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


**Module 9: Cracking Password Protected Zip Files**

Yes! You read that right. We can use John to crack the password on password-protected Zip files. Again, we’ll use a separate part of the John suite of tools to convert the Zip file into a format that John will understand, but we’ll use the syntax you’re already familiar with for all intents and purposes.

**Zip2John**

Similarly to the `unshadow` tool we used previously, we will use the `zip2john` tool to convert the Zip file into a hash format that John can understand and hopefully crack. The primary usage is like this:

`zip2john [options] [zip file] > [output file]`

- `[options]`: Allows you to pass specific checksum options to zip2john; this shouldn’t often be necessary

- `[zip file]`: The path to the Zip file you wish to get the hash of

- `>`: This redirects the output from this command to another file

- `[output file]`: This is the file that will store the output

**Example Usage**

`zip2john zipfile.zip > zip_hash.txt`

**Cracking**

We’re then able to take the file we output from zip2john in our example use case, zip_hash.txt, and, as we did with unshadow, feed it directly into John as we have made the input specifically for it.

`john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt`

**Practical**

Now, have a go at cracking a “secure” Zip file! The file is located in `~/John-the-Ripper-The-Basics/Task09/`.

**Answer the questions below**

1. _What is the password for the secure.zip file?_

Answer: `pass123`

**_Explanation:_**

We first we use the following command to extract the password for the zip folder

`zip2john secure.zip > zip_hash.txt`

<img width="908" height="174" alt="image" src="https://github.com/user-attachments/assets/06e71096-f0b5-4349-9328-706fd538ea1d" />

and now we use normal john on `zip_hash.txt` to crack the hash for the zip file

`john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt`

<img width="914" height="369" alt="image" src="https://github.com/user-attachments/assets/7fb7ca0b-b758-45c2-bbbd-031659c08277" />

2. _What is the contents of the flag inside the zip file?_

Answer: `THM{w3ll_d0n3_h4sh_r0y4l}`

**_Explanation:_**

We will unzip the `secure.zip` folder and now we are a password and we enter the password and a new folder called `zippy` gets created

`unzip secure.zip`

<img width="915" height="170" alt="image" src="https://github.com/user-attachments/assets/17bed543-3c60-4b23-8a1d-26b6f06e091c" />

Now we go to this `zippy` folder and find the flag

<img width="915" height="249" alt="image" src="https://github.com/user-attachments/assets/8acd32fa-bc48-47df-a75a-ffde4887b429" />

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
