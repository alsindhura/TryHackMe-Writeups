Link: https://tryhackme.com/room/cyberchefbasics

<img width="1200" height="1200" alt="image" src="https://github.com/user-attachments/assets/54fc9d62-a597-4ca6-be1a-fdbdbaf2f5a7" />

This room is an introduction to CyberChef, the Swiss Army knife for cyber security professionals.

**Module 1: Introduction**

CyberChef is a simple, intuitive web-based application designed to help with various “cyber” operation tasks within your web browser. Think of it as a Swiss Army knife for data - like having a toolbox of different tools designed to do a specific task. These tasks range from simple encodings like XOR or Base64 to complex operations like AES encryption or RSA decryption. CyberChef operates on recipes, a series of operations executed in order.

<img width="1110" height="681" alt="image" src="https://github.com/user-attachments/assets/7e2fde08-a1e8-4a52-a426-2d294a2dffa7" />
<img width="1110" height="681" alt="image" src="https://github.com/user-attachments/assets/365b64e2-b144-46b2-ad7e-51d484bac9ba" />

**Learning Objectives**

- Learn what CyberChef is

- Learn how to navigate the interface

- Understand common operations

- Learn how to create recipes and process the data

**Room Prerequisites**

Familiarity with the following rooms is recommended but is not mandatory before starting this room.

- [Hashing Basics](https://tryhackme.com/r/room/hashingbasics)

- [Cryptography Basics](https://tryhackme.com/r/room/cryptographybasics)

**Answer the questions below**

1. _Proceed with the next tasks to learn more!_

Answer: No answer needed

---

**Module 2: Accessing the Tool**

There are different ways to access and run CyberChef. Let's check the two most convenient methods!

**Online Access**

All you need is a web browser and an internet connection. Then, you can click [this](https://gchq.github.io/CyberChef) link to open CyberChef directly within your web browser.

**Offline or Local Copy**

You can run this offline or locally on your machine by downloading the latest release file from this [link](https://github.com/gchq/CyberChef/releases). This will work on both Windows and Linux platforms. As best practice, you should download the most stable version.

**Answer the questions below**

1. _I have access to CyberChef and I’m ready to dive into it._

Answer: No answer needed

---

**Module 3: Navigating the Interface**

CyberChef consists of four areas. Each consists of different components or features.

These are the following areas:

1. Operations

2. Recipe

3. Input

4. Output

<img width="2984" height="1660" alt="image" src="https://github.com/user-attachments/assets/3077d835-e81f-4d6b-a0b0-bc46bd63e228" />

Let's discuss each of these areas below.

**The Operations Area**

This is a practical and comprehensive repository of all the diverse operations that CyberChef is equipped to perform. These operations are meticulously categorized, offering users convenient access to various capabilities. Users can utilize the search feature to locate specific operations quickly, enhancing their efficiency and productivity.

Below are some operations you might use throughout your cyber security journey.

| Operation          | Description                                                                 | Example                                                                                                                                   |
|--------------------|-----------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| From Morse Code     | Translates Morse Code into (upper case) alphanumeric characters.            | `- .... .-. . .- - ...` becomes `THREATS` when used with default parameters                                                               |
| URL Encode          | Encodes problematic characters into percent-encoding, a format supported by URIs/URLs. | `https://tryhackme.com/r/room/cyberchefbasics` becomes `https%3A%2F%2Ftryhackme%2Ecom%2Fr%2Froom%2Fcyberchefbasics` with “Encode all special chars” |
| To Base64           | This operation encodes raw data into an ASCII Base64 string.                | `This is fun!` becomes `VGhpcyBpcyBmdW4h`                                                                                                  |
| To Hex              | Converts the input string to hexadecimal bytes separated by the specified delimiter. | `This Hex conversion is awesome!` becomes `54 68 69 73 20 48 65 78 20 63 6f 6e 76 65 72 73 69 6f 6e 20 69 73 20 61 77 65 73 6f 6d 65 21`     |
| To Decimal          | Converts the input data to an ordinal integer array.                        | `This Decimal conversion is awesome!` becomes `84 104 105 115 32 68 101 99 105 109 97 108 32 99 111 110 118 101 114 115 105 111 110 32 105 115 32 97 119 101 115 111 109 101 33` |
| ROT13               | A simple Caesar substitution cipher which rotates alphabet characters by the specified amount (default 13). | `Digital Forensics and Incident Response` becomes `Qvtvgny Sberafvpf naq Vapvqrag Erfcbafr`         |

Alternatively, you can directly check how the operations work by hovering on the specific operation. This should give you a sample or a description and a link to Wikipedia.

<img width="1684" height="1128" alt="image" src="https://github.com/user-attachments/assets/a4260777-f237-4a89-8553-945c9ef3c6b3" />

**The Recipe Area**

This is considered as the heart of the tool. In this area, you can seamlessly select, arrange, and fine-tune operations to suit your needs. This is where you take control, defining each operation's arguments and options precisely and purposefully. The recipe area is a designated space to select and arrange specific operations and then define their respective arguments and options to customize their behaviour further. In the recipe area, you can drag the operations you want to use and specify arguments and options.

Features include the following:

- `Save recipe`: This feature allows the user to save selected operations.

- `Load recipe`: Allows the user to load previously saved recipes.

- `Clear Recipe`: This feature will enable users to clear the chosen recipe during usage.

These can be found in the highlighted icons below:

<img width="890" height="1560" alt="image" src="https://github.com/user-attachments/assets/8195f7fb-9c41-41e8-aecd-520450172721" />

The bottom part of the image above is the BAKE! button. This processes the data with the given recipe.

Additionally, you can tick the Auto Bake checkbox. This feature allows users to automatically cook using the selected recipe without manually clicking BAKE! every time.

**Input Area**

The input area provides a user-friendly space where you can easily input text or files by pasting, typing, or dragging them to perform operations.

<img width="1698" height="944" alt="image" src="https://github.com/user-attachments/assets/ff0da5fa-688d-46bb-a29b-eb50bf7097e5" />

Additionally, it has the following features:

- `Add a new input tab`: This is where an additional tab is created for the user to use different values from the previous tab.

<img width="1700" height="182" alt="image" src="https://github.com/user-attachments/assets/a097b556-a656-41ca-a978-a0b83b250dbd" />

- `Open folder as input`: This feature allows users to upload a whole folder as input value.

<img width="1696" height="104" alt="image" src="https://github.com/user-attachments/assets/ba429427-7126-479e-aeee-4fe536b7f71b" />

- `Open file as input`: This feature allows the user to upload a file as its input value.

<img width="1686" height="86" alt="image" src="https://github.com/user-attachments/assets/38d3c4cb-9e9c-408b-bd50-3d92e07e0ba2" />

- `Clear input and output`: This feature allows the user to clear any input values inserted and the corresponding output value.

- `Reset pane layout`: This feature brings the tool's interface to its default window sizes.

**Output Area**

The output area is a visual space that showcases the data processing results. It neatly presents the outcomes of any manipulations or transformations you have applied to the input data, allowing for a clear and intuitive display of the processed information.

<img width="1530" height="766" alt="image" src="https://github.com/user-attachments/assets/6d39ca2a-d857-47cd-8975-dca49d4b60dd" />

**Features include:**

- `Save output to file`: This feature allows the users to save the result into a .dat file.

- `Copy raw output to the clipboard`: This feature allows users to copy raw output directly to their clipboard, allowing them to quickly copy the results for use in other applications or documents.

- `Replace input with output`: This feature allows users to quickly overwrite the input data based on the operations' results.

- `Maximise output pane`: This feature brings the tool's interface to its default window sizes.

**Answer the questions below**

1. _In which area can you find "From Base64"?_

Answer: `operations`

2. _Which area is considered the heart of the tool?_

Answer: `Recipe`

---

**Module 4: Before Anything Else**

**Hold your horses!**

Before even going to the actual thing, let's have a quick overview of the thought process when using CyberChef! This process consists of four different steps:

<img width="1140" height="180" alt="image" src="https://github.com/user-attachments/assets/49e744eb-e7a0-45f8-9495-7d7827cab8e9" />

Let's discuss each step further.

Setting a clear objective is essential. This step involves defining specific and achievable goals. It helps answer the question, "What do I want to accomplish?". Objectives are vital in providing direction, purpose, and focus to your goals. One example would be, "During a security investigation, I found a gibberish string; I want to know what hidden message it contains if it has one."

Next, put your data into the input area. In this step, you use your data. This is where you paste or upload the gibberish string that you found.

The third step is to select the Operations you want to use. This can be tricky if you are not familiar yet with what you are dealing with. Following our example, we are still determining what to use to understand this gibberish string. During our research, we found relevant information that this gibberish string might be using anything related to encryption. Therefore, we decided to use any operations under the Encryption/Encoding category, including but not limited to ROT13, Base64, Base85, or ROT47. Note that we can use a lot of operations under this category. 

Lastly, check the output to see if it is the intended result. This begs the question, "Have we achieved our objective?". In our example, it would mean, were we able to decode the gibberish string we found? If yes, then that's it! If not, we may need to repeat the steps that we have taken.

To provide visual clarity to our example, see the figure below:

<img width="1140" height="180" alt="image" src="https://github.com/user-attachments/assets/8a008f78-2e0f-4724-9d07-e7dfa77e757f" />

**Answer the questions below**

1. _At which step would you determine, "What do I want to accomplish?_

Answer: `1`

---

**Module 5: Practice, Practice, Practice**

We want you to be as prepared as possible. Therefore, we will explore some of this task's most commonly used operation categories. Recognizing which category to utilize can enhance your ability to use the tool more efficiently and effectively.

**Extractors**

The specific operations mentioned in the table below fall under the Extractors category.

| Specific                | Description                                                                                                          |
|-------------------------|----------------------------------------------------------------------------------------------------------------------|
| Extract IP addresses    | Extracts all IPv4 and IPv6 addresses.                                                                                |
| Extract URLs            | Extracts Uniform Resource Locators (URLs) from the input. The protocol (HTTP, FTP, etc.) is required to avoid false positives. |
| Extract email addresses | Extracts all email addresses from the input.                                                                         |

The Extract IP addresses will extract any valid IPv4/6 address from any given input. We recommend checking our existing room for a quick recap of networking: [Networking Concepts](https://tryhackme.com/r/room/networkingconcepts)

The Extract email addresses extracts any strings and characters with this format, anything@domain[.]com. Examples of domains include hotmail.com, google.com, tryhackme.com, and yahoo.com

Extract URLs extracts Uniform Resource Locator, commonly known as URL. , a URL is the address used to access resources on the internet. You can check the [Web Applications Basics](https://tryhackme.com/r/room/webapplicationbasics) room if you would like to dig deeper into URLs and web applications.

**Date and Time**

The specific operations in the table below fall under the Date / Time category.

| Specific              | Description                                                                                   |
|-----------------------|-----------------------------------------------------------------------------------------------|
| From UNIX Timestamp   | Converts a UNIX timestamp to a datetime string.                                               |
| To UNIX Timestamp     | Parses a datetime string in UTC and returns the corresponding UNIX timestamp.                |

A UNIX timestamp is a 32-bit value representing the number of seconds since January 1, 1970 UTC (the UNIX epoch). To convert "Fri Sep 6 20:30:22 +04 2024" into a UNIX Timestamp, use the operations To UNIX Timestamp, where the result would be 1725654622. If you wish to convert it back to a more readable format, you can use From UNIX Timestamp.

**Data Format**

The specific operations in the table below fall under the Data format category.

| Operation       | Description                                                                                                                                         | Example                                                                                           |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| From Base64     | This operation decodes data from an ASCII Base64 string back into its raw format.                                                                  | `V2VsY29tZSB0byB0cnloYWNrbWUh` becomes `Welcome to tryhackme!`                                     |
| URL Decode      | Converts URI/URL percent-encoded characters back to their raw values.                                                                               | `https%3A%2F%2Fgchq%2Egithub%2Eio%2FCyberChef%2F` becomes `https://gchq.github.io/CyberChef/`      |
| From Base85     | A notation for encoding arbitrary byte data. It is usually more efficient than Base64. This operation decodes from an ASCII string (custom alphabets supported). | `BOu!rD]j7BEbo7` becomes `hello world`                                                             |
| From Base58     | A notation for encoding arbitrary byte data, optimized for human readability by removing confusing characters (like l, I, 0, and O).                | `AXLU7qR` becomes `Thm58`                                                                         |
| To Base62       | A notation for encoding byte data using a limited, human-friendly character set. Produces shorter strings than decimal or hexadecimal.              | `Thm62` becomes `6NiRkOY`                                                                         |

Operations such as Base(64, 85, 58, 62) are known as base encodings. Base encoding takes binary data (strings of 0s and 1s) and transforms it into a text-based representation using a specific set of ASCII (American Standard Code for Information Interchange) characters.

Although we have a dedicated room for [Hashing Basics](https://tryhackme.com/r/room/hashingbasics), let's have a quick overview and discuss the most commonly used operation, Base64.

Our example would be to encode the letters "THM". We have a short ASCII Table here that we can use for reference. If you want to view the complete ASCII Table, please refer to this page [here](https://en.wikipedia.org/wiki/ASCII).

| Decimal | Binary     | Symbol |   | Decimal | Binary     | Symbol |
|---------|------------|--------|---|---------|------------|--------|
| 65      | 01000001   | A      |   | 78      | 01001110   | N      |
| 66      | 01000010   | B      |   | 79      | 01001111   | O      |
| 67      | 01000011   | C      |   | 80      | 01010000   | P      |
| 68      | 01000100   | D      |   | 81      | 01010001   | Q      |
| 69      | 01000101   | E      |   | 82      | 01010010   | R      |
| 70      | 01000110   | F      |   | 83      | 01010011   | S      |
| 71      | 01000111   | G      |   | 84      | 01010100   | T      |
| 72      | 01001000   | H      |   | 85      | 01010101   | U      |
| 73      | 01001001   | I      |   | 86      | 01010110   | V      |
| 74      | 01001010   | J      |   | 87      | 01010111   | W      |
| 75      | 01001011   | K      |   | 88      | 01011000   | X      |
| 76      | 01001100   | L      |   | 89      | 01011001   | Y      |
| 77      | 01001101   | M      |   | 90      | 01011010   | Z      |


**Step 1: Convert To Binary and Merge(Manually)**

Based on our table above, T =`01010100`, H=`01001000`, M = `01001101`. Next, concatenate these binaries and make sure they have 24 characters. You should have `010101000100100001001101`

**Step 2: Divide and Convert to Decimal(Manually)**

Separate `010101000100100001001101` into 6 characters each. You should have `010101` `000100` `100001` `001101`. These are 6-bit characters; we should have four instances of this now. We need to convert each instance to Decimal. Let's convert, then!

| Binary  | Decimal (Base10) |
|---------|------------------|
| 010101  | 21               |
| 000100  | 4                |
| 100001  | 33               |
| 001101  | 13               |

Step 3: Convert to Base64 (Manually)

Now that we have the Numbers from the previous step, which are 21, 4, 33, and 13, let's look for the equivalent characters from our table below. This table represents a base64 index table.

| Index | Character |   | Index | Character |   | Index | Character |
|-------|-----------|---|-------|-----------|---|-------|-----------|
| 0     | A         |   | 26    | a         |   | 52    | 0         |
| 1     | B         |   | 27    | b         |   | 53    | 1         |
| 2     | C         |   | 28    | c         |   | 54    | 2         |
| 3     | D         |   | 29    | d         |   | 55    | 3         |
| 4     | E         |   | 30    | e         |   | 56    | 4         |
| 5     | F         |   | 31    | f         |   | 57    | 5         |
| 6     | G         |   | 32    | g         |   | 58    | 6         |
| 7     | H         |   | 33    | h         |   | 59    | 7         |
| 8     | I         |   | 34    | i         |   | 60    | 8         |
| 9     | J         |   | 35    | j         |   | 61    | 9         |
| 10    | K         |   | 36    | k         |   | 62    | +         |
| 11    | L         |   | 37    | l         |   | 63    | /         |
| 12    | M         |   | 38    | m         |   |       |           |
| 13    | N         |   | 39    | n         |   |       |           |
| 14    | O         |   | 40    | o         |   |       |           |
| 15    | P         |   | 41    | p         |   |       |           |
| 16    | Q         |   | 42    | q         |   |       |           |
| 17    | R         |   | 43    | r         |   |       |           |
| 18    | S         |   | 44    | s         |   |       |           |
| 19    | T         |   | 45    | t         |   |       |           |
| 20    | U         |   | 46    | u         |   |       |           |
| 21    | V         |   | 47    | v         |   |       |           |
| 22    | W         |   | 48    | w         |   |       |           |
| 23    | X         |   | 49    | x         |   |       |           |
| 24    | Y         |   | 50    | y         |   |       |           |
| 25    | Z         |   | 51    | z         |   |       |           |

Upon checking from the table, we should have found its corresponding character by now. 

| Index | Character |
|-------|-----------|
| 21    | V         |
| 4     | E         |
| 33    | h         |
| 13    | N         |

Combine these characters, and you should have the equivalent of "THM" in base64 format. The answer would be VEhN.

Woah! Isn't that amazing? You just converted a set of characters into base64 manually.

Now, let’s discuss the URL Decode. This works by converting the percent-encoded characters back to their raw values. For a reference of these values, you can check the page [here](https://en.wikipedia.org/wiki/Percent-encoding). Note that the default character set in HTML5 is UTF-8. Check the table below for a quick overview of what we can typically see in a URL.

| Character | From UTF-8 |
|-----------|------------|
| :         | %3A        |
| /         | %2F        |
| .         | %2E        |
| =         | %3D        |
| #         | %23        |

**Practical Exercise**

Click on the Download Task Files button at the top of this task to download the file that we will use to answer the questions below.

Once downloaded, you can open the file, copy and paste the content into the input field, or use the Open file as input feature to upload the file.

Note: Use the specific operations under the Extractors category for the first two questions. It's best to try to answer the questions first without using the hints.

**Answer the questions below**

1. _What is the hidden email address?_

Answer: `hidden@hotmail.com`

**_Explanation:_**

We visit https://gchq.github.io/CyberChef/ and from the Operations pane, we choose `Extractors` and inside that we choose `Extract Email Addresses`

<img width="1920" height="929" alt="image" src="https://github.com/user-attachments/assets/532cdf49-37a5-4e70-a022-b89d2fbd3e3c" />

Now we upload the file which we downloaded from the task and now we can see the hidden email

<img width="2000" height="1200" alt="email(1)" src="https://github.com/user-attachments/assets/85ec7dee-ec91-43a5-bb50-bbdcd6a81f0b" />

2. _What is the hidden IP address that ends in .232?_

Answer: `102.20.11.232`

**_Explanation:_**

Now from the Operations pane, we choose `Extractors` and inside that we choose `Extract IP Addresses`

<img width="961" height="929" alt="image" src="https://github.com/user-attachments/assets/6406b25f-69e9-4fc2-bbec-83b1e9e3029d" />

And we see the output as 

<img width="1920" height="927" alt="image" src="https://github.com/user-attachments/assets/39297732-ef3a-4e16-8b69-9184ab8a9425" />


3. _Which domain address starts with the letter "T"?_

Answer: `TryHackMe.com`

**_Explanation:_**

Now from the Operations pane, we choose `Extractors` and inside that we choose `Extract Domains`

<img width="962" height="930" alt="image" src="https://github.com/user-attachments/assets/fcf30c9b-a714-43ce-b80a-cd9decd6fc6d" />

And we see the output as 

<img width="1920" height="926" alt="image" src="https://github.com/user-attachments/assets/62c6ca78-ec0e-47a5-ab7e-3ebf7886a15f" />

4. _What is the binary value of the decimal number 78?_

Answer: `01001110`

**_Explanation:_**

Now from the Operations pane, we choose `Data Format` and inside that we choose `From Decimal` and `To Binary`

<img width="966" height="932" alt="image" src="https://github.com/user-attachments/assets/46c05f1f-6087-4748-99f4-dfea6503057d" />

Now in the Input Area we enter, 78 and get the output

<img width="1920" height="927" alt="image" src="https://github.com/user-attachments/assets/64a7b5f2-19c5-4526-ab7b-2417bac37344" />

5. _What is the URL encoded value of `https://tryhackme.com/r/careers?`_

Answer: `https%3A%2F%2Ftryhackme%2Ecom%2Fr%2Fcareers`

**_Explanation:_**

We search for `URL Encode` in the search bar and then we select URL Encoding from the options listed and we also tick the "Encode all special chars" box

<img width="956" height="935" alt="image" src="https://github.com/user-attachments/assets/043dad0f-6c01-4cea-a625-8fbafb2a77c7" />

Now we enter out input as `https://tryhackme.com/r/careers` and now we can see the output

<img width="1920" height="927" alt="image" src="https://github.com/user-attachments/assets/d8ea219a-4b94-41bd-aad2-de45e3841aae" />

---

**Module 6: Your First Official Cook**

This task allows us to apply what we've learned from the previous tasks. We'll utilize CyberChef's areas and its features to answer the questions being asked. 

Now, this is the time that you truly shine! You are going for your first cook ever!

<img width="1140" height="800" alt="image" src="https://github.com/user-attachments/assets/2f92c527-95a0-4162-98a0-570f6c42ca15" />

Ready? Let's get our hands dirty, then!

Note: It's best to try to answer the questions first without using the hints.

**Answer the questions below**

1. _Using the file you downloaded in Task 5, which IP starts and ends with "10"?_

Answer: `10.10.2.10`

**_Explanation:_**

Now from the Operations pane, we choose `Extractors` and inside that we choose `Extract IP Addresses`

<img width="961" height="929" alt="image" src="https://github.com/user-attachments/assets/6406b25f-69e9-4fc2-bbec-83b1e9e3029d" />

And we see the output as 

<img width="1920" height="925" alt="image" src="https://github.com/user-attachments/assets/7ecb7f2e-b1b9-4d6d-8110-afd5da5e352c" />

2. _What is the base64 encoded value of the string "Nice Room!"?_

Answer: `TmljZSBSb29tIQ==`

**_Explanation:_**

Now from the Operations pane, we choose `Data Format` and inside that we choose `To Base64` 

<img width="958" height="925" alt="image" src="https://github.com/user-attachments/assets/939c60a6-517b-4759-968e-6bef60ad68fb" />

Now in the Input we enter `Nice Room!` and see the output as 

<img width="1920" height="930" alt="image" src="https://github.com/user-attachments/assets/c5f4bca1-3504-4a86-b457-148146f203f0" />


3. _What is the URL decoded value for `https%3A%2F%2Ftryhackme%2Ecom%2Fr%2Froom%2Fcyberchefbasics?`_

Answer: `https://tryhackme.com/r/room/cyberchefbasics?`

**_Explanation:_**

Now from the Operations pane, we choose `Data Format` and inside that we choose `URL Decode` 

<img width="960" height="928" alt="image" src="https://github.com/user-attachments/assets/a720fef6-8d62-4059-b5b2-eee08b00a9e8" />

Now in the Input we enter `https%3A%2F%2Ftryhackme%2Ecom%2Fr%2Froom%2Fcyberchefbasics?` and see the output as 

<img width="1920" height="927" alt="image" src="https://github.com/user-attachments/assets/18635562-e76a-46a6-8e60-0f80edd2bb3d" />

4. _What is the datetime string for the Unix timestamp 1725151258?_

Answer: `Sun 1 September 2024 00:40:58 UTC`

**_Explanation:_**

Now from the Operations pane, we choose `Data/Time` and inside that we choose `From UNIX Timestamp`

<img width="945" height="925" alt="image" src="https://github.com/user-attachments/assets/5c50d7b6-7cf4-49c6-8ef2-d4aad64f7adc" />

Now in the Input we enter `1725151258` and see the output as 

<img width="1920" height="929" alt="image" src="https://github.com/user-attachments/assets/5122d326-979b-4d52-954e-4844a0f616a9" />

5. _What is the Base85 decoded string of the value <+oue+DGm>Ap%u7?_

Answer: `This is fun!`

**_Explanation:_**

Now from the Operations pane, we choose `Data Format` and inside that we choose `From Base85`

<img width="954" height="934" alt="image" src="https://github.com/user-attachments/assets/2794814a-cec1-48b2-b2df-1004180ec1c3" />

Now in the Input we enter `<+oue+DGm>Ap%u7` and see the output as 

<img width="1920" height="931" alt="image" src="https://github.com/user-attachments/assets/d93c875b-991a-4b1b-89f0-abc16d9d4d68" />

---

**Module 7: Conclusion**

In this room, we discussed how CyberChef is a powerful tool for handling various data transformations and decoding tasks. Whether you need to work with Base64, Binary, or URLs, this digital wizard's kitchen provides a visual interface that makes data manipulation intuitive and straightforward. With a diverse recipe library, you can confidently tackle tasks ranging from extracting email addresses, IP addresses, and domains. We were able to navigate its interface and have a high-level discussion of the different areas, features, and parameters. However, note that for particularly large-scale processing, it's vital to benefit from support from other tools.

**Answer the questions below**

1. _I will have CyberChef, the Swiss Army knife of cyber security, ready for my upcoming journeys!_

Answer: No answer needed

---
