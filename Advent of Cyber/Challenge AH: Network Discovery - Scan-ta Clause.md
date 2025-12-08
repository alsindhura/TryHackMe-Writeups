Link: https://tryhackme.com/room/networkservices-aoc2025-jnsoqbxgky

**Task 1: Introduction**

Read the content and start the machines

**Task 2: Discover Network Services**

**Answer the questions below**

1. _**What evil message do you see on top of the website?**_

Answer: **`Pwned by HopSec`**

**Explanation:**

We open MACHINE_IP and see the message 

<img width="1437" height="687" alt="Screenshot 2025-12-08 153552" src="https://github.com/user-attachments/assets/855e081f-fcae-4f45-a7c7-3e707d718bf2" />

____________________________________________________

2. **_What is the first key part found on the FTP server?_**

Answer: **`3aster_`**

**Explanation:**

First we will use nmap to see all the ports and what is behind each port using the command

**`nmap -p- --script=banner 10.80.128.201`**

<img width="983" height="406" alt="Screenshot 2025-12-08 151543" src="https://github.com/user-attachments/assets/8d0f1a63-6a93-4c3d-ac26-efd3ace1cb70" />

We found a running FTP server in some custom TBFC application. Even though FTP runs on port 21 by default, it's possible to change the port to any other one, such as 21212. Let's try accessing the FTP in anonymous mode with the ftp command and see if we can get in

**`ftp 10.80.128.201 21212`**

<img width="854" height="337" alt="Screenshot 2025-12-08 151847" src="https://github.com/user-attachments/assets/22bd7e82-daaf-4dd6-aa94-944c84719177" />

We can see a file named "tbfc_qa_key1" and we will get this file

<img width="840" height="190" alt="Screenshot 2025-12-08 152011" src="https://github.com/user-attachments/assets/ae6f4f7f-58f3-4d9f-8542-38bc62d9a432" />

And then we exit the ftp and open the file we got earlier

<img width="521" height="57" alt="Screenshot 2025-12-08 152025" src="https://github.com/user-attachments/assets/c9d0da69-d89d-4f8c-ab8b-9fd1dc0c58d6" />

First key is **`3aster_`**

____________________________________________________

3. **_What is the second key part found in the TBFC app?_**

Answer: **`15_th3_`**

**Explanation:**

Now we get the second key using netcat

**`nc -v 10.80.128.201 25251`**

<img width="707" height="100" alt="Screenshot 2025-12-08 152218" src="https://github.com/user-attachments/assets/e0cece75-f01e-464c-aa72-2e45b7b1f900" />

Then we type "GET KEY"

<img width="710" height="155" alt="Screenshot 2025-12-08 152332" src="https://github.com/user-attachments/assets/db47a3fc-2151-41e7-bcc1-49f69fdb5629" />

Second Key: **`15_th3_`**

____________________________________________________

4. **_What is the third key part found in the DNS records?_**

Answer: **`n3w_xm45`**

**Explanation:**

Now we get the third key

There are also 65535 ports for UDP, we can scan it by using -sU

**`nmap -sU 10.80.128.201`**

<img width="976" height="292" alt="Screenshot 2025-12-08 152533" src="https://github.com/user-attachments/assets/f33ad6d9-6609-40ee-89d6-fe67e49c678c" />

We try to use dig to get the third key

**`dig @10.80.128.201 TXT key3.tbfc.local +short`**

<img width="887" height="54" alt="Screenshot 2025-12-08 152636" src="https://github.com/user-attachments/assets/7233178f-8288-4c36-a033-e9e66c28a18e" />

Third key is **`n3w_xm45`**

____________________________________________________

5. **_Which port was the MySQL database running on?_**

Answer: **`3306`**

**Explanation:**

So the combined key is **`3aster_15_th3_n3w_xm45`**

<img width="1434" height="585" alt="Screenshot 2025-12-08 152824" src="https://github.com/user-attachments/assets/02caa69a-1744-4ed0-8c7d-52b3746d0b92" />

Now we see something like this and here we click GO To Terminal

<img width="640" height="459" alt="Screenshot 2025-12-08 152903" src="https://github.com/user-attachments/assets/8d9e232b-33ee-402b-b294-d6b1ceb9bee3" />

Now in the terminal we can directly execute the commands

<img width="1434" height="596" alt="Screenshot 2025-12-08 153813" src="https://github.com/user-attachments/assets/84a2b4d1-7674-40c7-b5e1-90c1fc5b0a99" />

Now, in the newly acquired termial we enter the following command

**`ss -tunlp`**

<img width="1163" height="516" alt="Screenshot 2025-12-08 154239" src="https://github.com/user-attachments/assets/cf4ac7c4-5c7b-4b48-bc0c-1055a34d8728" />

And see the port 3306

_______________________________________________________

6. **_Finally, what's the flag you found in the database?_**

Answer: **`THM{4ll_s3rvice5_d1sc0vered}`**

**Explanation:**

We use the command **` mysql -D tbfcqa01 -e "show tables;"`** to see all the tables 

<img width="722" height="146" alt="Screenshot 2025-12-08 154444" src="https://github.com/user-attachments/assets/3c994ded-b836-49d8-bcc3-bfb7d8f20664" />

Finally we run **`mysql -D tbfcqa01 -e "select * from flags;"`** to get the flag

<img width="802" height="172" alt="Screenshot 2025-12-08 154528" src="https://github.com/user-attachments/assets/137470f6-46bd-4961-b073-31d17f381056" />

_______________________________________________________

7. **_If you enjoyed today's room, feel free to check out the Nmap: The Basics room._**

Answer: No answer needed

_______________________________________________________



