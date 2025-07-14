Link: https://tryhackme.com/room/publickeycrypto (Premium Room)

<img width="1201" height="1200" alt="image" src="https://github.com/user-attachments/assets/3624217c-cae8-41a3-8807-e656c051e892" />

Discover how public key ciphers such as RSA work and explore their role in applications such as SSH.

**Module 1: Introduction**

Consider the following scenario from everyday life. Let’s say you are meeting a business partner over coffee and discussing somewhat confidential business plans. Let’s break down the meeting from the security perspective.

- You can see and hear the other person. Consequently, it is easy to be sure of their identity. That’s authentication, i.e., you are confirming the identity of who you are talking with.

- You can also confirm that what you are “hearing” is coming from your business partner. You can tell what words and sentences are coming from your business partner and what is coming from others. That’s authenticity, i.e., you verify that the message genuinely comes from a specific sender. Moreover, you know that what they are saying is reaching you, and there is no chance of anything changing the other party’s words across the table. That’s integrity, i.e., ensuring that the data has not been altered or tampered with.

- Finally, you can pick a seat away from the other customers and keep your voice low so that only your business partner can hear you. That’s confidentiality, i.e., only the authorised parties can access the data.

Let’s quickly compare this with correspondence in the cyber realm. When someone sends you a text message, how can you be sure they are who they claim to be? How can you be sure that nothing changed the text as it travelled across various network links? When you are communicating with your business partner over an online messaging platform, you need to be sure of the following:

- **_Authentication_**: You want to be sure you communicate with the right person, not someone else pretending.

- **_Authenticity_**: You can verify that the information comes from the claimed source.

- **_Integrity_**: You must ensure that no one changes the data you exchange.

- **_Confidentiality_**: You want to prevent an unauthorised party from eavesdropping on your conversations.

Cryptography can provide solutions to satisfy the above requirements, among many others. Private key cryptography, i.e., symmetric encryption, mainly protects confidentiality. However, public key cryptography, i.e., asymmetric cryptography, plays a significant role in authentication, authenticity, and integrity. This room will show various examples of how public key cryptography achieves that.

**Learning Prerequisites**

This room is the second of three introductory rooms about cryptography. Before starting this room, ensure you have finished the first one on the list.

- [Cryptography Basics](https://tryhackme.com/r/room/cryptographybasics)

- Public Key Cryptography Basics (this room)

- [Hashing Basics](https://tryhackme.com/r/room/hashingbasics)

**Learning Objectives**

In this room, we will cover various asymmetric cryptosystems and applications that use them, such as:

- RSA

- Diffie-Hellman

- SSH

- SSL/TLS Certificates

- PGP and GPG

First, let’s start the Virtual Machine by pressing the Start Machine button below.

You can also access the virtual machine using SSH at the IP address MACHINE_IP using the following credentials:

- Username: user

- Password: Tryhackme123!

**Answer the questions below**

1. _Let’s begin!_

Answer: No answer needed

----------------------------------------------------------------------------------------------------------------------------------------------

**Module 2: Common Use of Asymmetric Encryption**

Exchanging keys for symmetric encryption is a widespread use of asymmetric cryptography. Asymmetric encryption is relatively slow compared to symmetric encryption; therefore, we rely on asymmetric encryption to negotiate and agree on symmetric encryption ciphers and keys.

But the question is, how do you agree on a key with the server without transmitting the key for people snooping to see?

<img width="1140" height="800" alt="image" src="https://github.com/user-attachments/assets/5aeda50c-0144-41db-95a5-345a417256e3" />

**Analogy**

Imagine you have a secret code for communicating and instructions for using the secret code. The question is how you can send these instructions to your friend without anyone else being able to read them. The answer is more straightforward than it seems; you could ask your friend for a lock. Only your friend has the key for this lock, and we’ll assume you have an indestructible box you can lock with it.

If you send the instructions in a locked box to your friend, they can unlock it once it reaches them and read the instructions. After that, you can communicate using the secret code without the risk of people snooping.

In this metaphor, the secret code represents a symmetric encryption cipher and key, the lock represents the server’s public key, and the key represents the server’s private key.

| Analogy          | Cryptographic System                |
|------------------|-------------------------------------|
| Secret Code      | Symmetric Encryption Cipher and Key |
| Lock             | Public Key                          |
| Lock’s Key       | Private Key                         |

Consequently, you would only need to use asymmetric cryptography once so that it won’t affect the speed, and then you can communicate privately using symmetric encryption.

**The Real World**

In reality, you need more cryptography to verify that the person you’re talking to is who they say they are. This is achieved using digital signatures and certificates, which we will visit later in this room.

**Extra Info**

```
SSH and Cryptography – Summary Notes
🔐 1. Asymmetric and Symmetric Cryptography in Secure Connections

    Asymmetric Cryptography is used at the beginning of a secure connection (e.g. HTTPS, SSH) to:

        Authenticate the server (and optionally the client).

        Securely exchange a symmetric session key.

    Symmetric Cryptography is used after the handshake for the rest of the communication:

        Faster and more efficient for ongoing data exchange.

💻 2. What Happens During an SSH Connection
🧾 First-Time SSH Connection:

    You connect: ssh user@server.com

    Server sends its public host key (used to identify itself).

    SSH checks ~/.ssh/known_hosts:

        If the key is not found, you see:

            "The authenticity of host 'server.com' can't be established..."

    If you type yes:

        The server’s public key is saved in known_hosts for future verification.

🔁 Future SSH Connections:

    SSH compares the server’s current key to the one saved in known_hosts.

    If it matches: connection proceeds.

    If it doesn't match: SSH shows a warning (potential man-in-the-middle attack).
```

| Phase                   | Method                          |
|-------------------------|----------------------------------|
| Server identity check   | Asymmetric (host public key)     |
| Session key exchange    | Diffie-Hellman or similar        |
| Encrypted communication | Symmetric encryption (e.g. AES)  |


**Answer the questions below**

_In the analogy presented, what real object is analogous to the public key?_

Answer: `Lock`

----------------------------------------------------------------------------------------------------------------------------------------------

**Module 3:RSA**

RSA is a public-key encryption algorithm that enables secure data transmission over insecure channels. With an insecure channel, we expect adversaries to eavesdrop on it.

**The Math That Makes RSA Secure**

RSA is based on the mathematically difficult problem of factoring a large number. Multiplying two large prime numbers is a straightforward operation; however, finding the factors of a huge number takes much more computing power.

It’s simple to multiply two prime numbers together even on paper, say 113 × 127 = 14351. Even for larger prime numbers, it would still be a feasible job, even by hand. Consider the following numeric example:

- Prime number 1: 982451653031

- Prime number 2: 169743212279

- Their product: 982451653031 × 169743212279 = 166764499494295486767649

On the other hand, it’s pretty tricky to determine what two prime numbers multiply together to make 14351 and even more challenging to find the factors of 166764499494295486767649.

In real-world examples, the prime numbers would be much bigger than the ones in this example. A computer can easily factorise 166764499494295486767649; however, it cannot factorise a number with more than 600 digits. And you would agree that the multiplication of the two huge prime numbers, each around 300 digits, would be easier than the factorisation of their product.


**Numerical Example**

Let’s revisit encryption, decryption, and key usage in asymmetric encryption. The public key is known to all correspondents and is used for encryption, while the private key is protected and used for decryption, as shown in the figure below.

<img width="1840" height="1040" alt="image" src="https://github.com/user-attachments/assets/a7242523-c69c-4432-82e4-2ac59b916058" />

In the [Cryptography Basics](https://tryhackme.com/r/room/cryptographybasics) room, we explained the modulo operation and said it plays a significant role in cryptography. In the following simplified numerical example, we see the RSA algorithm in action:


- Bob chooses two prime numbers: p = 157 and q = 199. He calculates n = p × q = 31243.

- With ϕ(n) = n − p − q + 1 = 31243 − 157 − 199 + 1 = 30888, Bob selects e = 163 such that e is relatively prime to ϕ(n); moreover, he selects d = 379, where e × d = 1 mod ϕ(n), i.e., e × d = 163 × 379 = 61777 and 61777 mod 30888 = 1. The public key is (n,e), i.e., (31243,163) and the private key is $(n,d), i.e., (31243,379).

- Let’s say that the value they want to encrypt is x = 13, then Alice would calculate and send y = xe mod n = 13163 mod 31243 = 16341.

- Bob will decrypt the received value by calculating x = yd mod n = 16341379 mod 31243 = 13. This way, Bob recovers the value that Alice sent.

The proof that the above algorithm works can be found in [modular arithmetic](https://www.britannica.com/science/modular-arithmetic) and is beyond the scope of this module. It is worth repeating that in this example, we picked a three-digit prime number, while in an actual application, p and q would be at least a 300-digit prime number each.

**Extra Info**

```
🔐 Real-Life Analogy: Sending a Secret Gift Box
Characters:

    Bob (receiver, has private key)

    Alice (sender, uses Bob’s public key)

Step 1: Bob prepares his lock system

    Bob picks two secret prime numbers p and q — like two special secrets only he knows.

    He multiplies them to get a big number n — think of it as a unique lock shape.

    Bob calculates ϕ(n) (a special number used to design the keys).

    Bob chooses a number e (the public key part) — this is like a lock you can give to anyone.

    Bob calculates d (the private key part) — the only key that can open the lock.

Step 2: Bob shares his public key (n, e) with Alice

    Bob tells Alice: "Hey, here’s my public lock (n, e) — you can use this to lock a box so only I can open it."

Step 3: Alice wants to send a secret message

    Alice has a secret number x (like a small gift) she wants to send to Bob.

    Alice uses Bob’s public key (n, e) to lock her gift by calculating:

y = x^e mod n

- This means Alice puts the gift in a box and locks it with Bob’s public lock.

- Alice sends the locked box (the encrypted message y) to Bob.
Step 4: Bob receives the locked box and opens it

   - Bob uses his private key (n, d) (the special key only he has) to unlock the box by calculating:

x = y^d mod n

Bob recovers the original gift (x) — the secret message Alice sent.
```

| Symbol | Real-Life Meaning                                |
|--------|-------------------------------------------------|
| p, q   | Bob’s secret special prime secrets              |
| n      | The unique lock shape                            |
| ϕ(n)   | The secret math formula Bob uses to create his keys |
| e      | The public lock Bob shares with Alice           |
| d      | Bob’s private key to open the lock               |
| x      | The secret gift Alice wants to send              |
| y      | The locked box Alice sends to Bob                 |
| mod    | The lock mechanism wrapping around                |

**Numerical Example**

```
Step 1: Choose primes

Let’s pick small primes:

p = 3
q = 11

Step 2: Calculate n and ϕ(n)

n = p × q = 3 × 11 = 33
ϕ(n) = (p - 1) × (q - 1) = 2 × 10 = 20

Step 3: Choose e

Pick e such that:

    1 < e < ϕ(n)

    gcd(e, ϕ(n)) = 1 (no common factors)

Let’s pick:

e = 3

    gcd(3, 20) = 1 → good choice

Step 4: Calculate d

Find d such that:

(e × d) mod ϕ(n) = 1

i.e.,

(3 × d) mod 20 = 1

Try multiples of 20 plus 1 and divide by 3:

    1 mod 20 = 1 → d = 1/3 no

    21 mod 20 = 1 → d = 21/3 = 7 → integer! So:

d = 7

Step 5: Keys

    Public key: (n, e) = (33, 3)

    Private key: (n, d) = (33, 7)

Step 6: Encrypt a message

Suppose Alice wants to send:

x = 4

Encrypt:

y = x^e mod n = 4^3 mod 33
4^3 = 64
64 mod 33 = 64 - 33 × 1 = 31

So ciphertext:

y = 31

Step 7: Decrypt the message

Bob receives y = 31, decrypts:

x = y^d mod n = 31^7 mod 33

Calculate stepwise (to keep it manageable):

    31 mod 33 = 31

    31^2 = 31 × 31 = 961
    961 mod 33 = 961 - 33 × 29 = 961 - 957 = 4

    31^4 = (31^2)^2 = 4^2 = 16 mod 33

    31^7 = 31^(4 + 2 + 1) = 31^4 × 31^2 × 31^1
    = 16 × 4 × 31

Calculate:

    16 × 4 = 64 mod 33 = 64 - 33 × 1 = 31

    31 × 31 = 961 mod 33 = 4 (from above)

So:

x = 4

Recovered original message!

```

**RSA in CTFs**

The math behind RSA comes up relatively often in CTFs, requiring you to calculate variables or break some encryption based on them. Many good articles online explain RSA, and they will give you almost all of the information you need to complete the challenges. One good example of an RSA CTF challenge is the [Breaking RSA](https://tryhackme.com/r/room/breakrsa) room.


There are some excellent tools for defeating RSA challenges in CTFs. My favourite is [RsaCtfTool](https://github.com/Ganapati/RsaCtfTool), which has worked well for me. I’ve also had some success with [rsatool](https://github.com/ius/rsatool).

You need to know the main variables for RSA in CTFs: p, q, m, n, e, d, and c. As per our numerical example:

- p and q are large prime numbers

- n is the product of p and q

- The public key is n and e

- The private key is n and d

- m is used to represent the original message, i.e., plaintext

- c represents the encrypted text, i.e., ciphertext

Crypto CTF challenges often present you with a set of these values, and you need to break the encryption and decrypt a message to retrieve the flag.


**Answer the questions below**

1. _Knowing that p = 4391 and q = 6659. What is n?_

Answer: `29239669`

**_Explanation:_**

Since n= p×q => 4391 × 6659= 29239669

2. _Knowing that p = 4391 and q = 6659. What is ϕ(n)?_

Answer: `29228620`

**_Explanation:_**

Since ϕ(n) = n − p − q + 1 

We got n from previous question, we caluclate

`29239669- 4391 - 6659 + 1= 29228620`


-----------------------------------------------------------------------------------------------------------------------------------------------
