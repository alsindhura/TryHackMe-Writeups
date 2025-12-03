Link: https://tryhackme.com/room/phishing-aoc2025-h2tkye9fzU

**Task 1: Introduction**

Read the content and start the machines

**Task 2: Phishing Exercise for TBFC**

**Answer the followig**

1. _**What is the password used to access the TBFC portal?**_

Answer: **`unranked-wisdom-anthem`**

**Explanation**

We navigate to **"cd ~/Rooms/AoC2025/Day02"** in attack box and then type **"./server.py"** to run the script. 

<img width="658" height="81" alt="Screenshot 2025-12-03 112438" src="https://github.com/user-attachments/assets/822e3d88-d753-497e-8cd1-ebea52616821" />

This will start the server on port 8000. Let us leave this terminal open to capture the credentials.

<img width="710" height="556" alt="Screenshot 2025-12-03 114443" src="https://github.com/user-attachments/assets/ede663f2-cfb6-46dc-a3d7-652bd8e2c99c" />

Now on another terminal, we will open **`setoolkit`** 

And I will select the following options as show below

```
1 (Social-Engineering Attacks)
5 (Mass Mailer Attack)
1 (E-Mail Attack Single Email Address)
- Send email to: factory@wareville.thm
- How to deliver: 2 (Use your own server)
- From address: updates@flyingdeer.thm
- From name: Flying Deer
- Username: [Enter]
- Password: [Enter]
- SMTP server: 10.82.142.143
- Port: 25 [Enter]
- High priority: no
- Attach file: n
- Inline file: n
- Subject: Shipping Schedule Changes
- Format: p (plain)
Email body
Dear elves,
Kindly note that there have been significant changes to the shipping schedules due to increased shipping orders.
Please confirm the new schedule by visiting http://[IP]:8000
Best regards,
Flying Deer
END
```

<img width="469" height="381" alt="Screenshot 2025-12-03 113748" src="https://github.com/user-attachments/assets/58c1a829-8d65-4ed9-8b8e-98ef2e4cd59d" />

<img width="761" height="353" alt="Screenshot 2025-12-03 113905" src="https://github.com/user-attachments/assets/4aa45265-e9f4-4b87-98f4-5a955992b739" />

<img width="563" height="139" alt="Screenshot 2025-12-03 113943" src="https://github.com/user-attachments/assets/d5ecaed5-8197-408f-b705-af58ed610595" />

<img width="904" height="139" alt="Screenshot 2025-12-03 114026" src="https://github.com/user-attachments/assets/2d529863-6faa-4931-99f7-e0e488d2a9b5" />

<img width="900" height="181" alt="image" src="https://github.com/user-attachments/assets/7f7c522a-c03b-42c5-ac09-f54442d0f7eb" />

<img width="946" height="245" alt="Screenshot 2025-12-03 114214" src="https://github.com/user-attachments/assets/96b52a9a-4bff-4cd6-aef6-05907d717704" />

In the earlier terminal we can see the following credentials captured

<img width="942" height="260" alt="Screenshot 2025-12-03 114258" src="https://github.com/user-attachments/assets/bf90de23-744b-4c6e-947d-983ae4c1b8c1" />

__________________________________________________

2. **_Browse to http://MACHINE_IP from within the AttackBox and try to access the mailbox of the factory user to see if the previously harvested admin password has been reused on the email portal. What is the total number of toys expected for delivery?_**

Answer: **`1984000`**

**Explanation:**

We navigate to MACHINE_IP and enter the password we got earlier and use the username **"factory"**

<img width="712" height="597" alt="Screenshot 2025-12-03 115055" src="https://github.com/user-attachments/assets/e19ee205-8efb-4f40-a3df-b48dc40a3cef" />

We open the last e-mail and see the number of toys

<img width="717" height="618" alt="Screenshot 2025-12-03 115135" src="https://github.com/user-attachments/assets/1068eac5-48df-497a-89dc-e6da23fc08b8" />

<img width="593" height="64" alt="Screenshot 2025-12-03 115209" src="https://github.com/user-attachments/assets/c1482eab-0730-472d-9d20-29bebe47acd1" />

______________________________________________________

3. _**If you enjoyed today's room, feel free to check out the Phishing Prevention room.**_

Answer: No answer needed

______________________________________________________
