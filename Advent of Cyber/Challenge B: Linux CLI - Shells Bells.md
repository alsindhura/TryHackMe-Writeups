Link: https://tryhackme.com/room/linuxcli-aoc2025-o1fpqkvxti

**Task 1: Introduction**

Start the machine and read the content

**Task 2: Linux CLI**

**Answer the questions below**

1. _**Which CLI command would you use to list a directory?**_

Answer: **`ls`**

2. _**What flag did you see inside of the McSkidy's guide?**_

Answer: **`THM{learning-linux-cli}`**

**Explanation:**

We type **"ls"** and see a folder called **"Guides"**

<img width="769" height="92" alt="Screenshot 2025-12-02 130443" src="https://github.com/user-attachments/assets/5fba3c25-1075-4349-aa5d-9a2b5890445b" />

And we navigate to **"Guides/"** and type **"ls -la"** and see a file named **"guide.txt"**

<img width="757" height="165" alt="Screenshot 2025-12-02 130654" src="https://github.com/user-attachments/assets/21588ce9-ea5f-4ef1-b6f3-6ab8f5291211" />

We use the command **"cat .guide.txt"** to see the flag: **`THM{learning-linux-cli}`**

<img width="879" height="337" alt="Screenshot 2025-12-02 130802" src="https://github.com/user-attachments/assets/36980877-7925-4284-b82c-8f4dcf071145" />

3. _**Which command helped you filter the logs for failed logins?**_

Answer: **`grep`**

4. _**What flag did you see inside the Eggstrike script?**_

Answer: **`THM{sir-carrotbane-attacks}`**

**Explanation:**

From the message in the **".guide.txt"** we navigate to  **"/var/log"** and we use the following command to get the logs from auth.log **"grep "Failed password" auth.log"**

<img width="805" height="88" alt="Screenshot 2025-12-02 131820" src="https://github.com/user-attachments/assets/d4c54af5-0abb-47fa-b06a-9becaee1b18a" />

And we see

<img width="946" height="82" alt="Screenshot 2025-12-02 131920" src="https://github.com/user-attachments/assets/20564e7b-8b39-441c-973b-a417c4495c4f" />

And we use the command **"find /home/socmas -name *egg*"** to search for "eggs" in the socmas home directory.

<img width="686" height="100" alt="Screenshot 2025-12-02 132032" src="https://github.com/user-attachments/assets/a0f1cc7e-5325-49fe-ae81-87f1d48d6944" />

To print the flag, we use the command **"cat /home/socmas/2025/eggstrike.sh"**

<img width="734" height="283" alt="Screenshot 2025-12-02 132215" src="https://github.com/user-attachments/assets/d196158e-c3ce-4d63-a86f-1acee14450ad" />

5. _**Which command would you run to switch to the root user?**_

Answer: **`sudo su`**

6. **_Finally, what flag did Sir Carrotbane leave in the root bash history?_**

Answer: **`THM{until-we-meet-again}`**

**Explanation:**

We switch to the root user by running the **"sudo su"** command 

<img width="750" height="132" alt="Screenshot 2025-12-02 144833" src="https://github.com/user-attachments/assets/01e5ec9f-5b70-4d2f-ad1a-b8bdebb70fc8" />

We use the command **"history"** and see the flag

<img width="890" height="373" alt="Screenshot 2025-12-02 144953" src="https://github.com/user-attachments/assets/c1a04a5b-9f07-47de-820a-0df1cc367ba5" />

7. **_For those who consider themself intermediate and want another challenge, check McSkidy's hidden note in /home/mcskidy/Documents/ to get access to the key for Side Quest 1!_**

Answer: No answer needed

8. **_Enjoyed investigating in a Linux environment? Check out our Linux Logs Investigations room for more like this!_**

Answer: No answer needed

________________________________
