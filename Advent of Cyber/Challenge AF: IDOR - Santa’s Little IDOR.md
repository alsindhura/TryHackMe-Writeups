Link: https://tryhackme.com/room/idor-aoc2025-zl6MywQid9


**Task 1: Introduction**

Read the content and start the machines

**Task 2: IDOR on the Shelf**

**Answer the questions below**

1. _**What does IDOR stand for?**_

Answer: **`Insecure Direct Object Reference`**

2. _**What type of privilege escalation are most IDOR cases?**_

Answer: **`Horizontal`**

3. _**Exploiting the IDOR found in the view_accounts parameter, what is the user_id of the parent that has 10 children?**_

Answer: **`15`**

**Explanation:**

On the attack box, we visit the MACHINE_IP and login with the credentials given in the task

<img width="955" height="687" alt="Screenshot 2025-12-06 171609" src="https://github.com/user-attachments/assets/f264eb5d-01df-45e0-a232-d1ed091eaabf" />

After successful login, we see something like this

<img width="958" height="692" alt="Screenshot 2025-12-06 171700" src="https://github.com/user-attachments/assets/255a6799-3d8d-417a-9cd6-65b3500c733a" />

Now we will open dev tools

<img width="1919" height="693" alt="Screenshot 2025-12-06 171936" src="https://github.com/user-attachments/assets/4f807921-cba1-481d-82c3-b85d109e2119" />

And navigate to Network and refresh the page

<img width="685" height="592" alt="Screenshot 2025-12-06 172036" src="https://github.com/user-attachments/assets/5cc5c90c-8780-4b06-a22b-958e8a2edb23" />

We can see a request 

**`http://10.80.169.8/api/parents/view_accountinfo?user_id=10`**

which has **`user_id=10`** 

<img width="683" height="416" alt="Screenshot 2025-12-06 172533" src="https://github.com/user-attachments/assets/cebfdbc0-0b6d-4b18-8c25-f75822f2cdb7" />

We navigate to the Storage tab and select Local Storage

<img width="578" height="274" alt="Screenshot 2025-12-06 172750" src="https://github.com/user-attachments/assets/c26a6f05-1191-4a1b-a793-f4e235dd14e2" />

<img width="683" height="239" alt="Screenshot 2025-12-06 173036" src="https://github.com/user-attachments/assets/484d0c1e-55c4-452c-838b-c79b1dd7f41b" />

We can see the user_id and we will change the user_id to 11 from 10 and refresh the page

<img width="684" height="280" alt="Screenshot 2025-12-06 173112" src="https://github.com/user-attachments/assets/93e182a8-ace1-4620-8646-2c273a2a4666" />

We can see the page now has a different email address than the one we used for authentication

<img width="1228" height="588" alt="Screenshot 2025-12-06 173223" src="https://github.com/user-attachments/assets/4db1b7b2-e1ef-4da7-aaa0-94f8619afabb" />

This confirms the presence of IDOR vulnerability.

Since user_id:11 doesn't have any children listed, we will keep incrementing the values of user_id to find a user who has 10 children

User_id: 12

<img width="1918" height="587" alt="Screenshot 2025-12-06 173447" src="https://github.com/user-attachments/assets/1c6129ad-315e-42c2-a358-fda85d677aa6" />

User_id: 13

<img width="1919" height="585" alt="Screenshot 2025-12-06 173525" src="https://github.com/user-attachments/assets/aced3486-fbbc-497a-b1ef-2da66fdbff8f" />

User_id: 14 (Only 2 children)

<img width="1919" height="595" alt="Screenshot 2025-12-06 173618" src="https://github.com/user-attachments/assets/de701359-986e-4e76-9858-e2fda1180953" />

Atlast user_id: 15 has 10 children

<img width="1919" height="581" alt="Screenshot 2025-12-06 173803" src="https://github.com/user-attachments/assets/e65e5a04-80ca-4de8-81b6-26d20b66b3cb" />

____________________________________________________

4. **_Bonus Task: If you want to dive even deeper, use either the base64 or md5 child endpoint and try to find the id_number of the child born on 2019-04-17? To make the iteration faster, consider using something like Burp's Intruder. If you want to check your answer, click the hint on the question._**

Answer: No answer needed 

But the answer is **`19`**

**Explanation:**

We will open BurpSuite and navigate this website in proxy and open the user_id: 15 and click on one of the child and send this request to Intruder

<img width="1591" height="679" alt="Screenshot 2025-12-06 180154" src="https://github.com/user-attachments/assets/ded9b88b-aef8-4632-af84-af7027e71053" />

We see something like this in the Intruder 

<img width="1524" height="723" alt="Screenshot 2025-12-06 180221" src="https://github.com/user-attachments/assets/8a6409b5-cc1d-4bcd-bb25-365875dc9520" />

The above image shows a request being made to **`/api/child/b64/MTE=`** and **`MTE=`** is base64 value for 11

<img width="851" height="537" alt="Screenshot 2025-12-06 180405" src="https://github.com/user-attachments/assets/c78e5a02-f796-4b6f-9745-2307f1aba6af" />

Now in the Intruder, we select **`MTE=`** and click on **Add §** 

<img width="1919" height="695" alt="Screenshot 2025-12-06 180724" src="https://github.com/user-attachments/assets/4becb5d5-bc86-4462-9e82-577e5b9bfc6c" />

Now on the right side menu, we enter the values of 10-20 (since user_id:15 has 10 children) in base64 as our payload and click Start Attack


<img width="678" height="460" alt="Screenshot 2025-12-06 180841" src="https://github.com/user-attachments/assets/1268dcf4-2a0a-4ff5-8725-13db4e880897" />

We see something like this in the Intruder Attack screen

<img width="1916" height="750" alt="Screenshot 2025-12-06 181033" src="https://github.com/user-attachments/assets/38700000-8c45-474b-ae7d-04880b12fb53" />

Now we navigate through each row and atlast we find the child with the DOB:2019-04-17 at 19

<img width="1876" height="755" alt="Screenshot 2025-12-06 181300" src="https://github.com/user-attachments/assets/9faccdb3-d59d-4f1b-bb38-57ab07bcfd62" />

____________________________________________________________________________

5. **_Bonus Task: Want to go even further? Using the /parents/vouchers/claim endpoint, find the voucher that is valid on 20 November 2025. Insider information tells you that the voucher was generated exactly on the minute somewhere between 20:00 - 24:00 UTC that day. What is the voucher code? If you want to check your answer, click the hint on the question._**

Answer: No answer needed

But the answer is **`22643e00-c655-11f0-ac99-026ccdf7d769`**

**Explanation:**

We click on Claim Voucher in the proxy browser and enter some data and send it to the Intruder

<img width="1683" height="552" alt="Screenshot 2025-12-06 184035" src="https://github.com/user-attachments/assets/914d06a6-1e83-4539-be26-708b0bcc5b8e" />

Now in the BurpSuite, we will send this request to the Intruder

<img width="1919" height="694" alt="Screenshot 2025-12-06 184128" src="https://github.com/user-attachments/assets/e01a570b-c03d-453f-967e-3083179efd54" />

<img width="1919" height="727" alt="Screenshot 2025-12-06 184144" src="https://github.com/user-attachments/assets/8e069d5c-fd39-4f5c-bb92-fa07e0222bed" />

We can see the "test" as code which we entered ealier. We will select this text and click on  **Add §** 

<img width="1917" height="751" alt="Screenshot 2025-12-06 184314" src="https://github.com/user-attachments/assets/d63630ab-1771-47da-8b96-8e1d83053e16" />

We will then Generate possible the UUIDs using any AI tool and load the payload file and click on Start Attack

The payloads can also be found in https://pastebin.com/4dBCpfYk

<img width="630" height="404" alt="image" src="https://github.com/user-attachments/assets/e7008e46-3840-4f10-a169-53b006e5fc66" />

We can see the Intruder Attack screen

<img width="1919" height="708" alt="Screenshot 2025-12-06 192249" src="https://github.com/user-attachments/assets/18feaff6-a58a-4679-908f-a363b70c8922" />

All other attacks are 404 or 401 except 42 which shows 200

<img width="1844" height="655" alt="Screenshot 2025-12-06 192337" src="https://github.com/user-attachments/assets/45b9c4f4-3d0f-4b70-96a9-2be0a5b95f06" />

We will open this and see the response

<img width="1873" height="670" alt="Screenshot 2025-12-06 192420" src="https://github.com/user-attachments/assets/0a051d9c-9c2a-42af-8914-f8d70dc41ab3" />

The voucher code is **`22643e00-c655-11f0-ac99-026ccdf7d769`** and from the hint we will see the same

<img width="489" height="169" alt="Screenshot 2025-12-06 192532" src="https://github.com/user-attachments/assets/76a1824c-37b0-4fe2-a368-322c580ac4cd" />

__________________________________________________________________________


6. _**If you enjoyed today's room, check out our complete IDOR room!**_

Answer: No answer needed

____________________________________________________
