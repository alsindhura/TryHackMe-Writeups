Link: https://tryhackme.com/room/idor (Premium Room) 

<img width="512" height="512" alt="image" src="https://github.com/user-attachments/assets/e9c853a7-d99d-4546-b815-be16e05b8c11" />

**Task 1: What is an IDOR?**

In this room, you're going to learn what an IDOR vulnerability is, what they look like, how to find them and a practical task exploiting a real case scenario.

**What is an IDOR?**

IDOR stands for Insecure Direct Object Reference and is a type of access control vulnerability.

This type of vulnerability can occur when a web server receives user-supplied input to retrieve objects (files, data, documents), too much trust has been placed on the input data, and it is not validated on the server-side to confirm the requested object belongs to the user requesting it.

**Answer the questions below**

1. _What does IDOR stand for?_

Answer: `Insecure Direct Object Reference`

---

**Task 2: An IDOR Example**

Imagine you've just signed up for an online service, and you want to change your profile information. The link you click on goes to http://online-service.thm/profile?user_id=1305, and you can see your information.

Curiosity gets the better of you, and you try changing the user_id value to 1000 instead (http://online-service.thm/profile?user_id=1000), and to your surprise, you can now see another user's information. You've now discovered an IDOR vulnerability! Ideally, there should be a check on the website to confirm that the user information belongs to the user logged requesting it.

Using what you've learnt above, click on the View Site button and try and receive a flag by discovering and exploiting an IDOR vulnerability. 

**Answer the questions below**

1. _What is the Flag from the IDOR example website?_

Answer: `THM{IDOR-VULN-FOUND}`

**_Explanation:_**

We click on View Site and then we see some emails

<img width="1027" height="492" alt="image" src="https://github.com/user-attachments/assets/41bf6aae-d4d3-4d01-a859-3e6de55a292e" />

And now we open each email and find that second email takes us to a online store page when we click on it

<img width="1022" height="591" alt="image" src="https://github.com/user-attachments/assets/cad5d332-806d-483e-95b6-3dffb8bd60f7" />

<img width="1018" height="588" alt="image" src="https://github.com/user-attachments/assets/958d2fdc-66b1-46c5-8821-ef9e86bc77c8" />

In the URL we try to change the order-id from `1234` to `1000`

<img width="1022" height="613" alt="image" src="https://github.com/user-attachments/assets/f6af7609-5143-4661-904a-6ee3dbf8a2bc" />

We can see the flag

<img width="1015" height="629" alt="image" src="https://github.com/user-attachments/assets/13ecfb93-bb3b-47f5-9fe4-473786f74953" />

---

**Task 3: Finding IDORs in Encoded IDs**

**Encoded IDs**

When passing data from page to page either by post data, query strings, or cookies, web developers will often first take the raw data and encode it. Encoding ensures that the receiving web server will be able to understand the contents. Encoding changes binary data into an ASCII string commonly using the a-z, A-Z, 0-9 and = character for padding. The most common encoding technique on the web is base64 encoding and can usually be pretty easy to spot. You can use websites like [https://www.base64decode.org/](https://www.base64decode.org/) to decode the string, then edit the data and re-encode it again using [https://www.base64encode.org/](https://www.base64encode.org/) and then resubmit the web request to see if there is a change in the response.

See the image below as a graphical example of this process:

<img width="1575" height="121" alt="image" src="https://github.com/user-attachments/assets/01d7a4ec-5b5e-42d8-839e-75523f4385f7" />

**Answer the questions below**

1. _What is a common type of encoding used by websites?_

Answer: `base64`

---

**Task 4: Finding IDORs in Hashed IDs**

**Hashed IDs**

Hashed IDs are a little bit more complicated to deal with than encoded ones, but they may follow a predictable pattern, such as being the hashed version of the integer value. For example, the Id number 123 would become 202cb962ac59075b964b07152d234b70 if md5 hashing were in use.


It's worthwhile putting any discovered hashes through a web service such as [https://crackstation.net/](https://crackstation.net/) (which has a database of billions of hash to value results) to see if we can find any matches. 

**Answer the questions below**

1. _What is a common algorithm used for hashing IDs?_

Answer: `MD5`

---

**Task 5: Finding IDORs in Unpredictable IDs**

Unpredictable IDs

If the Id cannot be detected using the above methods, an excellent method of IDOR detection is to create two accounts and swap the Id numbers between them. If you can view the other users' content using their Id number while still being logged in with a different account (or not logged in at all), you've found a valid IDOR

vulnerability.

**Answer the questions below**

1. _What is the minimum number of accounts you need to create to check for IDORs between accounts?_

Answer: `2`

---

**Task 6: Where are IDORs located**

**Where are they located?**

The vulnerable endpoint you're targeting may not always be something you see in the address bar. It could be content your browser loads in via an AJAX request or something that you find referenced in a JavaScript file. 

Sometimes endpoints could have an unreferenced parameter that may have been of some use during development and got pushed to production. For example, you may notice a call to /user/details displaying your user information (authenticated through your session). But through an attack known as parameter mining, you discover a parameter called user_id that you can use to display other users' information, for example, /user/details?user_id=123.


**Answer the questions below**

1. _Read the above._

Answer: No answer needed

---

**Tasl 7: A Practical IDOR Example**

Begin by pressing the Start Machine button; once started, click the below link and open it in a new browser tab:


https://LAB_WEB_URL.p.thmlabs.com


Firstly you'll need to log in. To do this, click on the customer's section and create an account. Once logged in, click on the Your Account tab. 


The Your Account section gives you the ability to change your information such as username, email address and password. You'll notice the username and email fields pre-filled in with your information.  


We'll start by investigating how this information gets pre-filled. If you open your browser developer tools, select the network tab and then refresh the page, you'll see a call to an endpoint with the path /api/v1/customer?id={user_id}.


This page returns in JSON format your user id, username and email address. We can see from the path that the user information shown is taken from the query string's id parameter (see below image).

<img width="1844" height="299" alt="image" src="https://github.com/user-attachments/assets/ea748009-2003-4c23-a249-5410f7cb5ba7" />

You can try testing this id parameter for an IDOR vulnerability by changing the id to another user's id. Try selecting users with IDs 1 and 3 and then answer the questions below.

**Answer the questions below**

1. _What is the username for user id 1?_

Answer: `adam84`

**_Explanation:_**

We visit https://10-201-108-163.reverse-proxy-us-east-1.tryhackme.com/customers/signup and create a new account

<img width="1175" height="691" alt="image" src="https://github.com/user-attachments/assets/79eb8916-9494-41c5-9b93-cd18aa7451c8" />

Now we open dev tools go to network tab and we can see an entry with `id`

<img width="1134" height="963" alt="image" src="https://github.com/user-attachments/assets/88192247-7a17-47a4-bc22-a179f2a32d9b" />

We try to change this paramter to 1 and resend the request

<img width="1071" height="311" alt="image" src="https://github.com/user-attachments/assets/afa25ac3-06c9-436d-adac-c4abef741289" />

Now we select the entry with the id as 1 and in the response we can see the username and email

<img width="1138" height="963" alt="image" src="https://github.com/user-attachments/assets/8fbd886a-1b95-4c09-8ef6-0c584a44bac7" />


2. _What is the email address for user id 3?_

Answer: `j@fakemail.thm`

**_Explanation:_**

We change the id to 3 and in the response we can see the username and email


<img width="1130" height="925" alt="image" src="https://github.com/user-attachments/assets/5781bf48-f949-4394-bc1e-7cba4a6d8aac" />

<img width="1136" height="851" alt="image" src="https://github.com/user-attachments/assets/dee21199-4e05-464e-a9a9-41e4b4154c06" />

---
