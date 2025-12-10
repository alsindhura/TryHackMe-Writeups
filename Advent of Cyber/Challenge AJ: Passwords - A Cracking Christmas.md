Link: https://tryhackme.com/room/attacks-on-ecrypted-files-aoc2025-asdfghj123

**Task 1: Introduction**

Read the content and start the machine

**Task 2: Attacks Against Encrypted Files**

**Answer the questions below**

1. _**What is the flag inside the encrypted PDF?**_

Answer: **`THM{Cr4ck1ng_PDFs_1s_34$y}`**

**Explanation:**

We open terminal and type cd Desktop/ and then list the files in the Desktop

<img width="665" height="95" alt="Screenshot 2025-12-10 110011" src="https://github.com/user-attachments/assets/6373eca7-8f2b-457e-8a7a-878e96e98ecb" />

And now we see a pdf file and we try to open it and find that it is locked using a password

<img width="876" height="770" alt="Screenshot 2025-12-10 110119" src="https://github.com/user-attachments/assets/a1220730-b2fa-420b-bf71-4517b4d7ca99" />

We need the password of the pdf file, we try pdfcrack to crack the password

**`pdfcrack -f flag.pdf -w /usr/share/wordlists/rockyou.txt `**

<img width="1107" height="465" alt="Screenshot 2025-12-10 110250" src="https://github.com/user-attachments/assets/d4792232-c9c7-420a-a103-0ebabf44f0ac" />

We got the password and now we try to open the file

<img width="873" height="761" alt="Screenshot 2025-12-10 110336" src="https://github.com/user-attachments/assets/ae20e1f4-3711-485b-8bf0-8f4494f8e653" />

And see the flag

<img width="814" height="501" alt="Screenshot 2025-12-10 110354" src="https://github.com/user-attachments/assets/61a5d026-8b15-421c-9121-f97eb4b15b6c" />

______________________________________________________________________________

2. _**What is the flag inside the encrypted zip file?**_

Answer: **`THM{Cr4ck1n6_z1p$_1s_34$yyyy}`**

**Explanation:**

In Desktop we find another file named flag.zip and this file is locked 

<img width="658" height="60" alt="Screenshot 2025-12-10 110539" src="https://github.com/user-attachments/assets/62671b07-6632-4f71-8363-9a93511accdb" />

We extracts the password hash from a ZIP file and saves it into a text file using zip2john

**`zip2john flag.zip > ziphash.txt`**

<img width="841" height="87" alt="Screenshot 2025-12-10 111132" src="https://github.com/user-attachments/assets/7f47db02-0948-449f-893b-bad0b07afbe8" />

Now we used this hash file to crack the password

**`john --wordlist=/usr/share/wordlists/rockyou.txt ziphash.txt`**

<img width="1103" height="344" alt="Screenshot 2025-12-10 111257" src="https://github.com/user-attachments/assets/4e4d392a-136f-4285-a78c-e98a0046078b" />

Now we will use the password above to unzip the file

**`7z x flag.zip -y`**

<img width="951" height="581" alt="Screenshot 2025-12-10 111837" src="https://github.com/user-attachments/assets/fec04aa0-dae2-4610-af46-129a1228d8ff" />

And the output is saved in flag.txt

<img width="970" height="126" alt="Screenshot 2025-12-10 111946" src="https://github.com/user-attachments/assets/e7d01a5a-2f6c-4f1d-9640-99c76a5b8ee9" />

_______________________________________________________________

3. **_For those who want another challenge, have a look around the VM to get access to the key for Side Quest 2! Accessible through our Side Quest Hub!_**

Answer: No answer needed

_______________________________________________________________

4. **_If you enjoyed this task, feel free to check out the Password Attacks room._**

Answer: No answer needed

_______________________________________________________________
