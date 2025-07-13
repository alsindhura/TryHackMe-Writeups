Link: https://tryhackme.com/room/cryptographybasics

<img width="1200" height="1200" alt="image" src="https://github.com/user-attachments/assets/8b26d46b-2ee7-4ab3-88e4-ce79cc4bfc19" />

Learn the basics of cryptography and symmetric encryption.

**Module 1: Introduction**

Have you ever wondered how to prevent third parties from reading your messages? How can your app or web browser build a secure channel with a remote server? By secure, we mean that no one can read or alter the exchanged data; furthermore, we can be confident that we are connecting with the real server. Thanks to cryptography, these requirements are satisfied.

Cryptography lays the foundation for our digital world. While networking protocols have made it possible for devices spread across the globe to communicate, cryptography has made it possible to trust this communication.

This room is the first of three introductory rooms about cryptography. There are no learning prerequisites except basic abilities to use the Linux command line. If you are not sure, please consider joining the [Pre Security](https://tryhackme.com/r/path/outline/presecurity) path.

- Cryptography Basics (this room)

- [Public Key Cryptography Basics](https://tryhackme.com/r/room/publickeycrypto)

- [Hashing Basics](https://tryhackme.com/r/room/hashingbasics)

**Learning Objectives**

Upon completing this room, you will learn the following:

- Cryptography key terms

- Importance of cryptography

- Caesar Cipher

- Standard symmetric ciphers

- Common asymmetric ciphers

- Basic mathematics commonly used in cryptography


**Answer the questions below**

_I’m ready to start learning about cryptography!_

Answer: No Answer needed

----------------------------------------------------------------------------------------------------------------------------------------------

**Module 2: Importance of Cryptography**

Cryptography’s ultimate purpose is to ensure _secure communication in the presence of adversaries_. The term secure includes confidentiality and integrity of the communicated data. Cryptography can be defined as the practice and study of techniques for secure communication and data protection where we expect the presence of adversaries and third parties. In other words, these adversaries should not be able to disclose or alter the contents of the messages.

Cryptography is used to protect confidentiality, integrity, and authenticity. In this age, you use cryptography daily, and you’re almost certainly reading this over an encrypted connection. Consider the following scenarios where you would use cryptography:

- When you log in to TryHackMe, your credentials are encrypted and sent to the server so that no one can retrieve them by snooping on your connection.

- When you connect over SSH, your SSH client and the server establish an encrypted tunnel so no one can eavesdrop on your session.

- When you conduct online banking, your browser checks the remote server’s certificate to confirm that you are communicating with your bank’s server and not an attacker’s.

- When you download a file, how do you check if it was downloaded correctly? Cryptography provides a solution through hash functions to confirm that your file is identical to the original one.

As you can see, you rarely have to interact directly with cryptography, but its solutions and implications are everywhere in the digital world. Consider the case where a company wants to handle credit card information and process related transactions. When handling credit cards, the company must follow and enforce the Payment Card Industry Data Security Standard (PCI DSS). In this case, the PCI DSS ensures a minimum level of security to store, process, and transmit data related to card credits. If you check the PCI DSS for Large Organizations, you will learn that the data should be encrypted both while being stored (at rest) and while being transmitted (in motion).

In the same way that handling payment card details requires complying with PCI DSS, handling medical records requires complying with their respective standards. Unlike credit cards, the standards for handling medical records vary from one country to another. Example laws and regulations that should be considered when handling medical records include HIPAA (Health Insurance Portability and Accountability Act) and HITECH (Health Information Technology for Economic and Clinical Health) in the USA, GDPR (General Data Protection Regulation) in the EU, DPA (Data Protection Act) in the UK. Although the list is not exhaustive, it gives an idea about the legal requirements that healthcare providers should consider depending on their country. These laws and regulations show that cryptography is a necessity that should be present yet usually hidden from direct user access.

**Answer the questions below**

_What is the standard required for handling credit card information?_

Answer: `PCI DSS`

-------------------------------------------------------------------------------------------------------------------------------------------------

**Module 3: Plaintext to Ciphertext**

Let’s start with an illustration before introducing the key terms. We begin with the plaintext that we want to encrypt. The plaintext is the readable data; it can be anything from a simple “hello”, a cat photo, credit card information, or medical health records. From a cryptography perspective, these are all “plaintext” messages waiting to be encrypted. The plaintext is passed through the encryption function along with a proper key; the encryption function returns a ciphertext. The encryption function is part of the cipher; a cipher is an algorithm to convert a plaintext into a ciphertext and vice versa.

<img width="1160" height="640" alt="image" src="https://github.com/user-attachments/assets/0be73745-248f-4949-9ed6-82cec6f34bd1" />

To recover the plaintext, we must pass the ciphertext along with the proper key via the decryption function, which would give us the original plaintext. This is shown in the illustration below.

<img width="1160" height="640" alt="image" src="https://github.com/user-attachments/assets/a83dc656-c34b-4084-ac59-e5ec798d6b1f" />

We have just introduced several new terms, and we need to learn them to understand any text about cryptography. The terms are listed below:


- **_Plaintext_** is the original, readable message or data before it’s encrypted. It can be a document, an image, a multimedia file, or any other binary data.

- **_Ciphertext_** is the scrambled, unreadable version of the message after encryption. Ideally, we cannot get any information about the original plaintext except its approximate size.

- **_Cipher_** is an algorithm or method to convert plaintext into ciphertext and back again. A cipher is usually developed by a mathematician.

- **_Key_** is a string of bits the cipher uses to encrypt or decrypt data. In general, the used cipher is public knowledge; however, the key must remain secret unless it is the public key in asymmetric encryption. We will visit asymmetric encryption in a later task.

- **_Encryption_** is the process of converting plaintext into ciphertext using a cipher and a key. Unlike the key, the choice of the cipher is disclosed.

- **_Decryption_** is the reverse process of encryption, converting ciphertext back into plaintext using a cipher and a key. Although the cipher would be public knowledge, recovering the plaintext without knowledge of the key should be impossible (infeasible).

**Answer the questions below**

1. _What do you call the encrypted plaintext?_

Answer: `ciphertext`

2. _What do you call the process that returns the plaintext?_

Answer: `decryption`

-----------------------------------------------------------------------------------------------------------------------------------------------

**Module 4: Historical Ciphers**

Cryptography’s history is long and dates back to ancient Egypt in 1900 BCE. However, one of the simplest historical ciphers is the Caesar Cipher from the first century BCE. The idea is simple: shift each letter by a certain number to encrypt the message.

Consider the following example:

- Plaintext: `TRYHACKME`

- Key: 3 (Assume it is a right shift of 3.)

- Cipher: Caesar Cipher


We can easily figure out that T becomes W, R becomes U, Y becomes B, and so on. As you noticed, once we reach Z, we start all over, as shown in the figure below. Consequently, we get the ciphertext of `WUBKDFNPH`.

<img width="1120" height="480" alt="image" src="https://github.com/user-attachments/assets/ac3fa8f6-f8aa-46c7-a755-b03bce9669ca" />

To decrypt, we need the following information:

- Ciphertext: `WUBKDFNPH`

- Key: 3

- Cipher: Caesar Cipher

<img width="1120" height="480" alt="image" src="https://github.com/user-attachments/assets/8d582e49-c996-425a-aaff-fe35d08c675c" />

For encryption, we shift to the right by three; for decryption, we shift to the left by three and recover the original plaintext, as illustrated in the image above. However, if someone gives you a ciphertext and tells you that it was encrypted using Caesar Cipher, recovering the original text would be a trivial task as there are only 25 possible keys. The English alphabet is 26 letters, and shifting by 26 will keep the letter unchanged; hence, 25 valid keys for encryption with Caesar Cipher. The figure below shows how decryption will succeed by attempting all the possible keys; in this case, we recovered the original message with Key = 5. Consequently, by today’s standards, where the cipher is publicly known, Caesar Cipher is considered insecure.

<img width="1800" height="660" alt="image" src="https://github.com/user-attachments/assets/e18f19a2-8698-45f6-9103-5d471acf0bc7" />

You would come across many more historical ciphers in movies and cryptography books. Examples include:

- The Vigenère cipher from the 16th century

- The Enigma machine from World War II

- The one-time pad from the Cold War

**Answer the questions below**

_Knowing that `XRPCTCRGNEI` was encrypted using Caesar Cipher, what is the original plaintext?_

Answer: `ICANENCRYPT`

**_Explanation:_**

We visit the site https://cryptii.com/pipes/caesar-cipher

And we select "Decode" and enter the above cipher text and keep clicking "+" and "-" and we can see some sentence which makes sense at 15th key

<img width="1810" height="431" alt="image" src="https://github.com/user-attachments/assets/70781928-2960-447a-8a8b-5b521eb38338" />

------------------------------------------------------------------------------------------------------------------------------------------------

**Module 5: Types of Encryption**

The two main categories of encryption are symmetric and asymmetric.

**Symmetric Encryption**

**Symmetric encryption**, also known as **symmetric cryptography**, uses the same key to encrypt and decrypt the data, as shown in the figure below. Keeping the key secret is a must; it is also called **private key cryptography**. Furthermore, communicating the key to the intended parties can be challenging as it requires a secure communication channel. Maintaining the secrecy of the key can be a significant challenge, especially if there are many recipients. The problem becomes more severe in the presence of a powerful adversary; consider the threat of industrial espionage, for instance.

<img width="1840" height="1040" alt="image" src="https://github.com/user-attachments/assets/b02d5728-b053-4776-9b5f-d4ad3bb425c6" />

Consider the simple case where you created a password-protected document to share it with your colleague. You can easily email the encrypted document to your colleague, but most likely, you cannot email them the password. The reason is that anyone with access to their mailbox would access both the password-protected document and its password. Therefore, you need to think of a different way, i.e., channel, to share the password. Unless you think of a secure, accessible channel, one solution would be to meet in person and communicate the password to them.

Examples of symmetric encryption are DES (Data Encryption Standard), 3DES (Triple DES) and AES (Advanced Encryption Standard).

- **DES** was adopted as a standard in 1977 and uses a 56-bit key. With the advancement in computing power, in 1999, a DES key was successfully broken in less than 24 hours, motivating the shift to 3DES.

- **3DES** is DES applied three times; consequently, the key size is 168 bits, though the effective security is 112 bits. 3DES was more of an ad-hoc solution when DES was no longer considered secure. 3DES was deprecated in 2019 and should be replaced by AES; however, it may still be found in some legacy systems.

- **AES** was adopted as a standard in 2001. Its key size can be 128, 192, or 256 bits.

There are many more symmetric encryption ciphers used in various applications; however, they have not been adopted as standards.

**Asymmetric Encryption**

Unlike symmetric encryption, which uses the same key for encryption and decryption, asymmetric encryption uses a pair of keys, one to encrypt and the other to decrypt, as shown in the illustration below. To protect confidentiality, **asymmetric encryption** or **asymmetric cryptography** encrypts the data using the public key; hence, it is also called **public key cryptography**.

<img width="1840" height="1040" alt="image" src="https://github.com/user-attachments/assets/59dd4899-d495-410d-9b38-ff2958dc0ba1" />

Examples are RSA, Diffie-Hellman, and Elliptic Curve cryptography (ECC). The two keys involved in the process are referred to as a public key and a private key. Data encrypted with the public key can be decrypted with the private key. Your private key needs to be kept private, hence the name.

Asymmetric encryption tends to be slower, and many asymmetric encryption ciphers use larger keys than symmetric encryption. For example, RSA uses 2048-bit, 3072-bit, and 4096-bit keys; 2048-bit is the recommended minimum key size. Diffie-Hellman also has a recommended minimum key size of 2048 bits but uses 3072-bit and 4096-bit keys for enhanced security. On the other hand, ECC can achieve equivalent security with shorter keys. For example, with a 256-bit key, ECC provides a level of security comparable to a 3072-bit RSA key.

Asymmetric encryption is based on a particular group of mathematical problems that are easy to compute in one direction but extremely difficult to reverse. In this context, extremely difficult means practically infeasible. For example, we can rely on a mathematical problem that would take a very long time, for example, millions of years, to solve using today’s technology.

We will visit various asymmetric encryption ciphers in the next room. For now, the important thing to note is that asymmetric encryption provides you with a public key that you share with everyone and a private key that you keep guarded and secret.

**Summary of New Terms**

- **Alice** and **Bob** are fictional characters commonly used in cryptography examples to represent two parties trying to communicate securely. **Symmetric encryption** is a method in which the same key is used for both encryption and decryption. Consequently, this key must remain secure and never be disclosed to anyone except the intended party. **Asymmetric encryption** is a method that uses two different keys: a public key for encryption and a private key for decryption.

**Answer the questions below**

1. _Should you trust DES? (Yea/Nay)_

Answer: `Nay`

**_Why?_**

With the advancement in computing power, in 1999, a DES key was successfully broken in less than 24 hours, motivating the shift to 3DES.

2. _When was AES adopted as an encryption standard?_

Answer: `2001`

----------------------------------------------------------------------------------------------------------------------------------------------

**Module 6: Basic Math**

The building blocks of modern cryptography lie in mathematics. To demonstrate some basic algorithms, we will cover two mathematical operations that are used in various algorithms:

- XOR Operation

- Modulo Operation

**XOR Operation**

XOR, short for “exclusive OR”, is a logical operation in binary arithmetic that plays a crucial role in various computing and cryptographic applications. In binary, XOR compares two bits and returns 1 if the bits are different and 0 if they are the same, as shown in the truth table below. This operation is often represented by the symbol `⊕` or `^`.

| A | B | A ⊕ B |
|---|---|-------|
| 0 | 0 |   0   |
| 0 | 1 |   1   |
| 1 | 0 |   1   |
| 1 | 1 |   0   |

If this is the first time you work with a truth table, it is a table that shows all possible outcomes. The XOR truth table above states all four cases: 0 ⊕ 0 = 0, 0 ⊕ 1 = 1, 1 ⊕ 0 = 1, and 1 ⊕ 1 = 0.

**Extra Info:**

| A | B | A + B | (A + B) mod 2 | A ⊕ B |
|---|---|-------|----------------|-------|
| 0 | 0 |   0   |       0        |   0   |
| 0 | 1 |   1   |       1        |   1   |
| 1 | 0 |   1   |       1        |   1   |
| 1 | 1 |   2   |       0        |   0   |

```
When you XOR two bits, it’s like adding them and then taking the remainder when divided by 2.

If the sum is even (0 or 2), XOR output is 0.

If the sum is odd (1), XOR output is 1.
```

Let’s consider an example where we want to apply XOR to the binary numbers 1010 and 1100. In this case, we perform the operation bit by bit: 1 ⊕ 1 = 0, 0 ⊕ 1 = 1, 1 ⊕ 0 = 1, and 0 ⊕ 0 = 0, resulting in 0110.

You may be wondering how XOR can play any role in cryptography. XOR has several interesting properties that make it useful in cryptography and error detection. One key property is that applying XOR to a value with itself results in 0, and applying XOR to any value with 0 leaves it unchanged. This means A ⊕ A = 0, and A ⊕ 0 = A for any binary value A. Additionally, XOR is commutative, i.e., A ⊕ B = B ⊕ A. And it is associative, i.e., (A ⊕ B) ⊕ C = A ⊕ (B ⊕ C).

Let’s see how we can make use of the above in cryptography. We will demonstrate how XOR can be used as a basic symmetric encryption algorithm. Consider the binary values P and K, where P is the plaintext, and K is the secret key. The ciphertext is C = P ⊕ K.

Now, if we know C and K, we can recover P. We start with C ⊕ K = (P ⊕ K) ⊕ K. But we know that (P ⊕ K) ⊕ K = P ⊕ (K ⊕ K) because XOR is associative. Furthermore, we know that K ⊕ K = 0; consequently, (P ⊕ K) ⊕ K = P ⊕ (K ⊕ K) = P ⊕ 0 = P. In other words, XOR served as a simple symmetric encryption algorithm. In practice, it is more complicated as we need a secret key as long as the plaintext.

Modulo Operation

Another mathematical operation we often encounter in cryptography is the modulo operator, commonly written as % or as mod. The modulo operator, X%Y, is the remainder when X is divided by Y. In our daily life calculations, we focus more on the result of division than on the remainder. The remainder plays a significant role in cryptography.

You need to work with large numbers when solving some cryptography exercises. If your calculator fails, we suggest using a programming language such as Python. Python has a built-in int type that can handle integers of arbitrary size and would automatically switch to larger types as needed. Many other programming languages have dedicated libraries for big integers. If you prefer to do your math online, consider [WolframAlpha](https://www.wolframalpha.com/).

Let’s consider a few examples.

- 25%5 = 0 because 25 divided by 5 is 5, with a remainder of 0, i.e., 25 = 5 × 5 + 0

- 23%6 = 5 because 23 divided by 6 is 3, with a remainder of 5, i.e., 23 = 3 × 6 + 5

- 23%7 = 2 because 23 divided by 7 is 3 with a remainder of 2, i.e., 23 = 3 × 7 + 2

An important thing to remember about modulo is that it’s not reversible. If we are given the equation x%5 = 4, infinite values of x would satisfy this equation.

The modulo operation always returns a non-negative result less than the divisor. This means that for any integer a and positive integer n, the result of a%n will always be in the range 0 to n − 1.

**Answer the questions below**

_What’s 1001 ⊕ 1010?_

Answer: `0011`

**_Explanation:_**

Truth table of 1001 ⊕ 1010

| A | B | A ⊕ B |
|---|---|--------|
| 1 | 1 |   0    |
| 0 | 0 |   0    |
| 0 | 1 |   1    |
| 1 | 0 |   1    |

where 1 ⊕ 1 makes 0 and 0 ⊕ 0 makes 0 and finally 0 ⊕ 1 or 1 ⊕ 0 makes 1

2. _What’s 118613842%9091?_

Answer: `3565`

**_Explanation:_**

When we divide 118613842 with 9091, we get 3565 as reminder 

<img width="416" height="404" alt="image" src="https://github.com/user-attachments/assets/4e625c7d-8485-45ee-9f15-0d3f86f33d01" />

3. _What’s 60%12?_

Answer: `0`

**_Explanation:_**

Since 60 is divisle by 12 (12*5=60), our remainder will be 0

---------------------------------------------------------------------------------------------------------------------------------------------

**Module 7: Summary**

In this room, we learned about the importance of cryptography and some of the problems that it solves. We also introduced symmetric and asymmetric encryption ciphers. Finally, we explained the XOR and the modulo operations. In the next room, [Public Key Cryptography Basics](https://tryhackme.com/r/room/publickeycrypto), we will visit various asymmetric cryptosystems and see how they solve the problems we face in the digital world.

**Answer the questions below**

_Before proceeding to the next room, make sure you have taken note of all the key terms and concepts introduced in this room._

Answer: No answer needed

----------------------------------------------------------------------------------------------------------------------------------------------
