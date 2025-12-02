Link: https://tryhackme.com/room/adventofcyberpreptrack

**Task 1-4**

Read the content

**Task 5: Challenge 1 — Password Pandemonium**

Click on "View Site"

<img width="951" height="609" alt="Screenshot 2025-12-02 115100" src="https://github.com/user-attachments/assets/19a04841-7547-4adc-9b28-2b497ad24b20" />

Click on "Update Password"

Enter a password which contains atleast

- 1 upper and lower case letter

- 1 symbol and number

- 12 characters minimum

So I choose the password **_F@3ernDp93n@jfk_**

<img width="940" height="520" alt="Screenshot 2025-12-02 115303" src="https://github.com/user-attachments/assets/2c5b08da-6b57-4712-bf45-4f4f7a46000c" />

And now I will click on Submit and see the flag **`THM{StrongStart}`**

<img width="745" height="737" alt="image" src="https://github.com/user-attachments/assets/54363c78-f3ac-4ae3-bce9-cfc40308a934" />

______________________

**Task 6: Challenge 2 — The Suspicious Chocolate.exe**

Click on "View Site"

<img width="898" height="784" alt="Screenshot 2025-12-02 115640" src="https://github.com/user-attachments/assets/cd445d61-ba04-449e-9d65-38ce813e60a6" />

Click on "Scan" and we will see the results

<img width="880" height="874" alt="Screenshot 2025-12-02 115711" src="https://github.com/user-attachments/assets/f28d5501-4b6d-4e66-8efc-5bfa71d2a264" />

Now I will select "**Malhare Labs**" because the Result says it is a trojan "**MalhareTrojan**" and select the radio button "**Malicious**" and click on Submit

<img width="875" height="834" alt="Screenshot 2025-12-02 115849" src="https://github.com/user-attachments/assets/89985294-2c62-49f1-b99a-61b90d91a503" />

And now we can see the flag **`THM{NotSoSweet}`**

<img width="877" height="595" alt="Screenshot 2025-12-02 115919" src="https://github.com/user-attachments/assets/66272d4e-32ee-4302-ab76-78c434b62d04" />

____________________________________________

**Task 7: Challenge 3 — Welcome to the AttackBox!**

Click on "View Site"

<img width="926" height="599" alt="Screenshot 2025-12-02 120157" src="https://github.com/user-attachments/assets/66293c09-6adf-47b9-ad0f-46b04fd2ff37" />

Now enter the command **_ls_** and see _**challenges/**_ 

We can navigate to this folder by using **_cd challenges/_** and here we see a text file named **Welcome.txt** and with _**cat Welcome.txt**_ we can see the flag **`THM{Ready2Hack}`**

<img width="894" height="584" alt="Screenshot 2025-12-02 120322" src="https://github.com/user-attachments/assets/cefc6345-ea02-4271-bf69-ff41b34f5145" />

___________________________________

**Task 8: Challenge 4 — The CMD Conundrum**

Click on "View Site"

<img width="926" height="663" alt="Screenshot 2025-12-02 120636" src="https://github.com/user-attachments/assets/2e7e4e5c-0b16-4d60-bd38-572be817b598" />

Here, we enter _**dir**_ to see the directories/files and we find a file name **_readme.txt_** and a folder _**mystery_data**_

<img width="880" height="654" alt="Screenshot 2025-12-02 120809" src="https://github.com/user-attachments/assets/a35d233f-7a91-47c7-9fc8-6ad2fdce7a14" />

Now we will navigate to the folder _**mystery_data**_ by using **_cd mystery_data_** and we use _**dir**_ again to see the files/folders inside mystery_data

<img width="417" height="179" alt="Screenshot 2025-12-02 121047" src="https://github.com/user-attachments/assets/abf47c53-47dd-4040-abcc-93dc78b6c13c" />

We only see on file named **_notes.txt_** and we read this file using **_type notes.txt_**

<img width="526" height="174" alt="Screenshot 2025-12-02 121219" src="https://github.com/user-attachments/assets/3499d0c0-a96d-4aee-be34-5033af62821d" />

To print the hidden artifacts on to the terminal, we type **_dir /a_** and see a hiddent file called **_hidden_flag.txt_**

<img width="444" height="172" alt="Screenshot 2025-12-02 121333" src="https://github.com/user-attachments/assets/2217f79c-d93e-4996-be4d-09391f873205" />

We use the command **_type hidden_flag.txt_** to get the flag **`THM{WhereIsMcSkidy}`**

<img width="871" height="567" alt="Screenshot 2025-12-02 121451" src="https://github.com/user-attachments/assets/3611f70c-1c67-44f9-b7e2-42edafb44793" />

_______________________________________

**Task 9: Challenge 5 — Linux Lore**

Click on "View Site"

<img width="913" height="619" alt="Screenshot 2025-12-02 121815" src="https://github.com/user-attachments/assets/c8440ef9-70fd-4684-99a0-6b1c3d2acb3f" />

We go to the folder **_cd /home/mcskidy/_** and then **_ls -la_**

<img width="894" height="614" alt="Screenshot 2025-12-02 122055" src="https://github.com/user-attachments/assets/5b2418cd-c62b-4c03-ab25-9ce72dd762d7" />

Here, we see a secret file called **".secret_message"**. In order to view the contents of this file, we use the command **"cat .secret_message"**

<img width="921" height="819" alt="Screenshot 2025-12-02 122455" src="https://github.com/user-attachments/assets/e11cb01f-ef52-4639-9e5a-08a351a73b43" />

Flag: **`THM{TrustNoBunny}`**

_________________________________

**Task 10: Challenge 6 — The Leak in the List**

Click on "View Site"

<img width="954" height="686" alt="Screenshot 2025-12-02 122716" src="https://github.com/user-attachments/assets/c3371fef-e650-46fa-afd5-4af493480f81" />

We enter **"mcskidy@tbfc.com"** in the E-mail field and click on "Check"

<img width="952" height="675" alt="Screenshot 2025-12-02 122812" src="https://github.com/user-attachments/assets/9e35f8af-392a-40b7-9b6c-3359a71a2d23" />

We see that **_"hopsec.io"_** has been compromised 

<img width="900" height="651" alt="Screenshot 2025-12-02 122912" src="https://github.com/user-attachments/assets/d17fbaa2-31cf-4b28-9ada-8948a8e40e71" />

We select this row and see the flag: **`THM{LeakedAndFound}`**

<img width="904" height="628" alt="Screenshot 2025-12-02 122945" src="https://github.com/user-attachments/assets/6dc59908-70c9-43b2-8f34-3a5dbe3bdfec" />

_____________________________________

**Task 11: Challenge 7 — WiFi Woes in Wareville**

Click on "View Site"

<img width="929" height="651" alt="Screenshot 2025-12-02 123100" src="https://github.com/user-attachments/assets/2ad6e7a1-3e2a-4f96-b625-2995540b259c" />

And in the Username and Password fields we enter: admin and log in

<img width="934" height="665" alt="Screenshot 2025-12-02 123144" src="https://github.com/user-attachments/assets/a69dc6bc-f879-40b8-9e80-4116698b8569" />

Now we will see a Password Reset page 

<img width="938" height="819" alt="Screenshot 2025-12-02 123347" src="https://github.com/user-attachments/assets/98944625-9947-494e-bb06-f3182aef2c45" />

In the fields, we enter a strong password such as **_"2Wvjm[99l6s9"_**

<img width="932" height="822" alt="Screenshot 2025-12-02 123413" src="https://github.com/user-attachments/assets/944f936e-caeb-44b5-92c1-71a2ff7436c4" />

And when we click on "Save", we can see the flag: **`THM{NoMoreDefault}`**

<img width="876" height="354" alt="Screenshot 2025-12-02 123424" src="https://github.com/user-attachments/assets/da0bbe9c-4d7d-424c-9bff-85ebf51481ec" />

__________________________________________

**Task 12: Challenge 8 — The App Trap**

Click on "View Site"

<img width="932" height="579" alt="Screenshot 2025-12-02 123642" src="https://github.com/user-attachments/assets/0babae17-c025-4cf0-ae7a-3442b6665ee3" />

We select the app **"Eastmas Scheduler"** and see that it has access to **"Password Vault"**

<img width="497" height="505" alt="Screenshot 2025-12-02 123755" src="https://github.com/user-attachments/assets/a6d74415-8f40-4b15-b71e-db0cd1d2c5c8" />

We click on "Revoke" and see the flag: **`THM{AppTrapped}`**

<img width="928" height="533" alt="Screenshot 2025-12-02 123813" src="https://github.com/user-attachments/assets/ecec445d-ef2c-4623-a88d-d08a2082f812" />

__________________________________________


**Task 13: Challenge 9 — The Chatbot Confession**

Click on "View Site"

<img width="938" height="814" alt="Screenshot 2025-12-02 123959" src="https://github.com/user-attachments/assets/7e00595f-f711-452f-bbd6-fcafd838dafa" />

Now we read each line of the conversation and find the following messages reveal the sensitive/private information

<img width="880" height="133" alt="Screenshot 2025-12-02 124239" src="https://github.com/user-attachments/assets/fc052f01-8f70-4cca-bd79-61489e4523ad" />

<img width="880" height="381" alt="Screenshot 2025-12-02 124215" src="https://github.com/user-attachments/assets/3e1f5288-6bc0-4ad1-bbb0-9be88be300ca" />

Why?

1. `https://internal.tbfc.local/admin` can reveal internal infrastructure detail
   
2. One of them reveal E-mail credentials

3. And last message shows the service token

When we click on Submit, we can see the flag: **`THM{DontFeedTheBot}`**

<img width="934" height="545" alt="Screenshot 2025-12-02 124456" src="https://github.com/user-attachments/assets/0e7449b3-ba6d-4d83-b41d-9a2498feaa6d" />

___________________________________________

**Task 14: Challenge 10 — The Bunny’s Browser Trail**

Click on "View Site"

<img width="932" height="824" alt="Screenshot 2025-12-02 124812" src="https://github.com/user-attachments/assets/42e923ac-e88c-476b-8052-f61aaa7dfa93" />

We see that the log: **_"200 GET /admin/panel • BunnyOS (HopSecBot)"_** has accessed the admin panel which is suspicious 

<img width="878" height="93" alt="Screenshot 2025-12-02 124958" src="https://github.com/user-attachments/assets/c02831b9-915e-4a0a-99d6-31a7a4f925b3" />

And click on Submit to see the flag: **`THM{EastmasIsComing}`**

<img width="912" height="548" alt="Screenshot 2025-12-02 125039" src="https://github.com/user-attachments/assets/0ce3180d-461e-4cf4-b769-be8d81bebe28" />

______________________________________________

**Task 15: The Finish Line**

Read the content

_____________________________________________
