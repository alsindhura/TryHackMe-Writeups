Link : https://tryhackme.com/room/offensivesecurityintro 

Module 1: What is Offensive Security?

"To outsmart a hacker, you need to think like one."

This is the core of "Offensive Security." It involves breaking into computer systems, exploiting software bugs, and finding loopholes in applications to gain unauthorized access. The goal is to understand hacker tactics and enhance our system defences.

Beginning Your Learning Journey

In this TryHackMe room, you will be guided through hacking your first website in a legal and safe environment. The goal is to show you how an ethical hacker operates.

But before we do that, let's review by answering the questions below. Type your answer in the text box after the question and click the "Submit" button. When you're done, proceed to Task 2.

Answer the questions below

Which of the following options better represents the process where you simulate a hacker's actions to find vulnerabilities in a system?

Offensive Security
Defensive Security

`Answer: Offensive Security`


Module 2: Hacking your first machine

Your First Hack
We will use a command-line application called "Gobuster" to brute-force FakeBank's website to find hidden directories and pages. Gobuster will take a list of potential page or directory names and try accessing a website with each of them; if the page exists, it tells you.

Step 1. Open A Terminal

A terminal, also known as the command line, allows us to interact with a computer without using a graphical user interface. On the machine, open the terminal by clicking on the Terminal icon on the right of the screen.

Screenshot showing terminal button

Step 2. Use Gobuster To Find Hidden Website Pages

Most companies have an admin portal page, giving their staff access to basic admin controls for day-to-day operations. For a bank, an employee might need to transfer money to and from client accounts. Due to human error or negligence, there may be instances when these pages are not made private, allowing attackers to find hidden pages that show or give access to admin controls or sensitive data.

To begin, type the following command into the terminal to find potentially hidden pages on FakeBank's website using Gobuster (a command-line security application).

`gobuster -u http://fakebank.thm -w wordlist.txt dir`

The command will run and show you an output similar to this:

```
ubuntu@tryhackme:~/Desktop$ gobuster -u http://fakebank.thm -w wordlist.txt dir

=====================================================
Gobuster v2.0.1              OJ Reeves (@TheColonial)
=====================================================
[+] Mode         : dir
[+] Url/Domain   : http://fakebank.thm/
[+] Threads      : 10
[+] Wordlist     : wordlist.txt
[+] Status codes : 200,204,301,302,307,403
[+] Timeout      : 10s
=====================================================
2024/05/21 10:04:38 Starting gobuster
=====================================================
/images (Status: 301)
/bank-transfer (Status: 200)
=====================================================
2024/05/21 10:04:44 Finished
=====================================================
```
In the command above, -u is used to state the website we're scanning, -w takes a list of words to iterate through to find hidden pages.

You will see that Gobuster scans the website with each word in the list, finding pages that exist on the site. Gobuster will have told you the pages in the list of page/directory names (indicated by Status: 200).

![image](https://github.com/user-attachments/assets/d7292df7-16b7-436f-986f-00cdc8ceaf57)

Step 3. Hack The Bank

You should have found a secret bank transfer page that allows you to transfer money between bank accounts (/bank-transfer). Type the hidden page into the FakeBank website using the browser's address bar.

![image](https://github.com/user-attachments/assets/8adfb0bd-007c-4685-894d-a156f667999f)

From this page, an attacker has authorized access and can steal money from any bank account. As an ethical hacker, you would (with permission) find vulnerabilities in their application and report them to the bank to fix them before a hacker exploits them.

Your mission is to transfer $2000 from bank account 2276 to your account (account number 8881). If your transfer was successful, you should now be able to see your new balance reflected on your account page.

Go there now and confirm you got the money! (You may need to hit Refresh for the changes to appear)

Answer the questions below
Above your account balance, you should now see a message indicating the answer to this question. Can you find the answer you need?

Answer: 
Type `bank-transfer` in the URL space

![Screenshot from 2025-06-23 12-00-16](https://github.com/user-attachments/assets/6765d662-3fdb-4014-a43d-a8b66da3fa1b)

And we will be redirected to the bank-transfer page and enter the following

Send From : `2276`
Send To : `8881`
Amount to send in USD : `2000`

and click on `Send Money` button

![Screenshot from 2025-06-23 12-03-18](https://github.com/user-attachments/assets/2fa136e1-0f52-4e63-b83b-5270347a4115)

It should show Successful transfer. Refer the screenshot below:

![Screenshot from 2025-06-23 12-07-36](https://github.com/user-attachments/assets/3621f218-c907-4fb8-85ff-ba06dad79692)

Now Click on `Return to Your Account`

We can see the flag now: `BANK-HACKED`

![Screenshot from 2025-06-23 12-09-28](https://github.com/user-attachments/assets/6c3d1fb2-c266-43c5-afcc-16f4c1e96a5b)

Module 3: Careers in cyber security

How can I start learning?

People often wonder how others become hackers (security consultants) or defenders (security analysts fighting cybercrime), and the answer is simple. Break it down, learn an area of cyber security you're interested in, and regularly practice using hands-on exercises. Build a habit of learning a little bit each day on TryHackMe, and you'll acquire the knowledge to get your first job in the industry.

The cyber careers room goes into more depth about the different careers in cyber. However, here is a short description of a few offensive security roles:


Penetration Tester - Responsible for testing technology products for finding exploitable security vulnerabilities.

Red Teamer - Plays the role of an adversary, attacking an organization and providing feedback from an enemy's perspective.

Security Engineer - Design, monitor, and maintain security controls, networks, and systems to help prevent cyberattacks.

Answer the questions below

Read the above, and continue with the next room!


