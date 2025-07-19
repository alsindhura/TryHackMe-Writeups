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
