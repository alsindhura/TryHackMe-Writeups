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


--------------------------------------------------------------------------------------------------------------------------------------------

**Module 4: Diffie-Hellman Key Exchange**

One of the challenges of using symmetric encryption is sharing the secret key. Let’s say you want to send a password-protected document to your business partner to discuss confidential business strategies. How would you share the password with them? It would be best if you had a secure channel to send the password, knowing that adversaries cannot read or alter it.

**Diffie-Hellman Key Exchange**

**Key exchange** aims to establish a shared secret between two parties. It is a method that allows two parties to establish a shared secret over an insecure communication channel without requiring a pre-existing shared secret and without an observer being able to get this key. Consequently, this shared key can be used for symmetric encryption in subsequent communications.


Consider the following scenario. Alice and Bob want to talk securely. They want to establish a shared key for symmetric cryptography but don’t want to use asymmetric cryptography for the key exchange. This is where the Diffie-Hellman Key Exchange comes in.

Alice and Bob generate secrets independently; let’s call these secrets A and B. They also have some public common material; let’s call this C.

We need to make some assumptions. Firstly, whenever we combine secrets, they’re practically impossible to separate. Secondly, the order in which they’re combined doesn’t matter. Alice and Bob will combine their secrets with the common material to form AC and BC. They will then send these to each other and combine the received part with their secret to create two identical keys, both ABC. Now, they can use this key to communicate.

If you found the previous paragraphs too abstract, let’s investigate the exact process.

- Alice and Bob agree on the public variables: a large prime number p and a generator g, where 0 < g < p. These values will be disclosed publicly over the communication channel. Although insecurely small, we will choose p = 29 and g = 3 to simplify our calculations.

- Each party chooses a private integer. As a numerical example, Alice chooses a = 13, and Bob chooses b = 15. Each of these values represents a private key and must not be disclosed.

- It is time for each party to calculate their public key using their private key from step 2 and the agreed-upon public variables from step 1. Alice calculates A = ga mod p = 313 mod 29 = 19 and Bob calculates B = gb mod p = 315 mod 29 = 26. These are the public keys.

- Alice and Bob send the keys to each other. Bob receives A = ga mod p = 19, i.e., Alice’s public key. And Alice receives B = gb mod p = 26, i.e., Bob’s public key. This step is called the key exchange.

- Alice and Bob can finally calculate the shared secret using the received public key and their own private key. Alice calculates Ba mod p = 2613 mod 29 = 10 and Bob calculates Ab mod p = 1915 mod 29 = 10. Both calculations yield the same result, gab mod p = 10, the shared secret key.

- Now each computes the shared secret key:

    Alice:   shared = B^a mod p

    Bob:   shared = A^b mod p

- Both sides get the same result because:
  (g^b)^a ≡ (g^a)^b mod p

<img width="1560" height="1180" alt="image" src="https://github.com/user-attachments/assets/0126b3eb-7040-4df7-9086-aaccbecb49f0" />

The chosen numbers are too small to provide any security, and in real-life applications, we would consider much bigger numbers.

Diffie-Hellman Key Exchange is often used alongside RSA public key cryptography. Diffie-Hellman is used for key agreement, while RSA is used for digital signatures, key transport, and authentication, among many others. For instance, RSA helps prove the identity of the person you’re talking to via digital signing, as you can confirm based on their public key. This would prevent someone from attacking the connection with a man-in-the-middle attack against Alice by pretending to be Bob. In brief, Diffie-Hellman and RSA are incorporated into many security protocols and standards to provide a comprehensive security solution.

| Feature                  | RSA                                     | Diffie-Hellman (DH)                      |
|--------------------------|-----------------------------------------|-----------------------------------------|
| Purpose                  | Encryption and digital signatures       | Key exchange (shared secret agreement)  |
| Key Type                 | Public/private key pair                  | Public/private key pair                   |
| Mathematical Basis       | Integer factorization (product of primes)| Discrete logarithm problem               |
| Operation                | Encrypt/decrypt messages                 | Agree on a shared secret key              |
| Use in Practice          | Encrypt data or sign messages            | Establish a symmetric key for encryption |
| Security Depends On      | Difficulty factoring large numbers       | Difficulty computing discrete logs       |
| Output                  | Ciphertext or signature                   | Shared secret key                         |
| Key Size                | Usually 2048 bits or more                 | Prime modulus size, often 2048 bits or more |
| Computational Cost      | Slower than DH                            | Generally faster than RSA for key exchange |
| Typical Usage           | SSL/TLS certificates, digital signatures | Key agreement in TLS, SSH, VPN            |
| Can be used for Key Exchange? | Yes, but less common                    | Yes, designed specifically for this      |


**Extra Info**

```
Session Key Generation and Encryption: DH vs RSA

    In modern secure connections (like HTTPS/TLS):

        Session key is generated via Diffie-Hellman (DH) key exchange.
        Both client (your browser) and server (Facebook) perform DH to agree on a shared secret without sending it over the network.
        This shared secret is used to derive the symmetric session key.

        RSA is used mainly for authentication, to prove the server’s identity and establish trust (via certificates).

    In some older or simpler protocols:

        The client generates a random session key and encrypts it using the server’s RSA public key, then sends it to the server.

        The server decrypts the session key with its private RSA key.

        After that, both use that symmetric session key to encrypt data
```

**What if we use VPN:**

- Your device and the VPN server do their own separate RSA/DH (or other) handshake to set up a secure tunnel.

- The VPN server and Facebook do their own, independent RSA/DH handshake as part of HTTPS/TLS.

- Your device never directly performs RSA/DH handshakes with Facebook’s server.

**Answer the questions below**

1. _Consider p = 29, g = 5, a = 12. What is A?_

Answer: `7`


**_Explanation_**

Use the [link](https://www.dcode.fr/diffie-hellman-key-exchange) and enter the paramters and then we can see the answer

<img width="334" height="140" alt="image" src="https://github.com/user-attachments/assets/3e322910-df6c-4280-a550-223ca738e184" />


2. _Consider p = 29, g = 5, b = 17. What is B?_

Answer: `9`

_**Explanation**_

<img width="335" height="136" alt="image" src="https://github.com/user-attachments/assets/6900de83-2202-4f77-9663-5b0ea0cd41d4" />

3. _Knowing that p = 29, a = 12, and you have B from the second question, what is the key calculated by Bob? (key = Ba mod p)_

Answer: `24`

4. _Knowing that p = 29, b = 17, and you have A from the first question, what is the key calculated by Alice? (key = Ab mod p)_

Answer: `24`

**_Explanation:_**

Same explanation for 3 and 4

<img width="429" height="214" alt="image" src="https://github.com/user-attachments/assets/fbd28014-34fa-499c-8ecf-8f6cd7c91831" />
<img width="339" height="163" alt="image" src="https://github.com/user-attachments/assets/5ccfb2ac-07d1-4a06-846c-ccac504c5b40" />

--------------------------------------------------------------------------------------------------------------------------------------------

**Module 5: SSH**

**Authenticating the Server**

If you have used an SSH client before, you would know the confirmation prompt in the terminal output below.

```        
root@TryHackMe# ssh 10.10.244.173
The authenticity of host '10.10.244.173 (10.10.244.173)' can't be established.
ED25519 key fingerprint is SHA256:lLzhZc7YzRBDchm02qTX0qsLqeeiTCJg5ipOT0E/YM8.
This key is not known by any other name.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.10.244.173' (ED25519) to the list of known hosts.
```
In the above interaction, the SSH client confirms whether we recognise the server’s public key fingerprint. ED25519 is the public-key algorithm used for digital signature generation and verification in this example. Our SSH client didn’t recognise this key and is asking us to confirm whether we want to continue with the connection. This warning is because a man-in-the-middle attack is probable; a malicious server might have intercepted the connection and replied, pretending to be the target server.

In this case, the user must authenticate the server, i.e., confirm the server’s identity by checking the public key signature. Once you answer with “yes”, the SSH client will record this public key signature for this host. In the future, it will connect you silently unless this host replies with a different public key.

**Authenticating the Client**

Now that we have confirmed that we are talking with the correct server, we need to identify ourselves and get authenticated. In many cases, SSH users are authenticated using usernames and passwords like you would log in to a physical machine. However, considering the inherent issues with passwords, this does not fall within the best security practices.

At some point, one will surely hit a machine with SSH configured with key authentication instead. This authentication uses public and private keys to prove the client is a valid and authorised user on the server. By default, SSH keys are RSA keys. You can choose which algorithm to generate and add a passphrase to encrypt the SSH key.

ssh-keygen is the program usually used to generate key pairs. It supports various algorithms, as shown on its manual page below.

```          
root@TryHackMe# man ssh-keygen
[...]
-t dsa | ecdsa | ecdsa-sk | ed25519 | ed25519-sk | rsa
Specifies the type of key to create. The possible values are “dsa”, “ecdsa”, “ecdsa-sk”, “ed25519”, “ed25519-sk”, or “rsa”.
[...]
```

The following is just for your information. At this stage, we recommend that you recognise their names only.

- **_DSA_** (Digital Signature Algorithm) is a public-key cryptography algorithm specifically designed for digital signatures.

- **_ECDSA_** (Elliptic Curve Digital Signature Algorithm) is a variant of DSA that uses elliptic curve cryptography to provide smaller key sizes for equivalent security.

- **_ECDSA-SK_** (ECDSA with Security Key) is an extension of ECDSA. It incorporates hardware-based security keys for enhanced private key protection.

- **_Ed25519_** is a public-key signature system using EdDSA (Edwards-curve Digital Signature Algorithm) with Curve25519.

- **_Ed25519-SK_** (Ed25519 with Security Key) is a variant of Ed25519. Similar to ECDSA-SK, it uses a hardware-based security key for improved private key protection.

Let’s generate a key pair with the default options.

```
root@TryHackMe# ssh-keygen -t ed25519
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/strategos/.ssh/id_ed25519): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/strategos/.ssh/id_ed25519
Your public key has been saved in /home/strategos/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:4S4DQvRfp52UuNwg++nTcWlnITEJTbMcCU0N8UYC1do strategos@g5000
The key's random art image is:
+--[ED25519 256]--+
|  .       +XXB.  |
| . .     . oBBo  |
|  . . . = + o=o  |
| .   . * X .o.E  |
|  . . o S +  o . |
|   . . o .. + o  |
|      o +. + o   |
|       +. .      |
|        ..       |
+----[SHA256]-----+

```

In the above example, we didn’t use a passphrase to show you the content of the private key. Let’s look at the generated public key, `id_ed25519.pub`, and the generated private key, `id_ed25519`.

```       
strategos@g5000:~/.ssh$ cat id_ed25519.pub 
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAINqNMqNhpXZGt6T8Q8bOplyTeldfWq3T3RyNJTmTMJq9 strategos@g5000
strategos@g5000:~/.ssh$ cat id_ed25519
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAAAMwAAAAtzc2gtZW
QyNTUxOQAAACDajTKjYaV2Rrek/EPGzqZck3pXX1qt090cjSU5kzCavQAAAJA+E+ajPhPm
owAAAAtzc2gtZWQyNTUxOQAAACDajTKjYaV2Rrek/EPGzqZck3pXX1qt090cjSU5kzCavQ
AAAEB981T2ngdoNm8gEzRU35bGHofqRMjfo5egxl0/9fap/NqNMqNhpXZGt6T8Q8bOplyT
eldfWq3T3RyNJTmTMJq9AAAACm9xYWJAZzUwMDABAgM=
-----END OPENSSH PRIVATE KEY-----
```
Note that the private key is shared above for demonstration purposes and was purged afterwards. Sharing a private key would be the most insecure act anyone can commit against their security. On another note, had we used -t rsa, the resulting keys would have been much longer.

**SSH Private Keys**

As just mentioned, you should treat your private SSH keys like passwords. Never share them under any circumstances; they’re called private keys for a reason. Someone with your private key can log in to servers that accept it, i.e., include it among the authorised keys, unless the key is encrypted with a passphrase.

It’s very important to mention that the passphrase used to decrypt the private key doesn’t identify you to the server at all; it only decrypts the SSH private key. The passphrase is never transmitted and never leaves your system.

Using tools like John the Ripper, you can attack an encrypted SSH key to attempt to find the passphrase, highlighting the importance of using a complex passphrase and keeping your private key private.

When generating an SSH key to log in to a remote machine, you should generate the keys on your machine and then copy the public key over, as this means the private key never exists on the target machine using ssh-copy-id. However, this doesn’t matter as much for temporary keys generated to access CTF boxes.

The permissions must be set up correctly to use a private SSH key; otherwise, your SSH client will ignore the file with a warning. Only the owner should be able to read or write to the private key (600 or stricter). ssh -i privateKeyFileName user@host is how you specify a key for the standard Linux OpenSSH client.

**Keys Trusted by the Remote Host**

The `~/.ssh` folder is the default place to store these keys for OpenSSH. The `authorized_keys` (note the US English spelling) file in this directory holds public keys that are allowed access to the server if key authentication is enabled. By default on many Linux distributions, key authentication is enabled as it is more secure than using a password to authenticate. Only key authentication should be accepted if you want to allow SSH access for the root user.

**Using SSH Keys to Get a “Better Shell”**

During CTFs, penetration testing, and red teaming exercises, SSH keys are an excellent way to “upgrade” a reverse shell, assuming the user has login enabled. Note that www-data usually does not allow this, but regular users and root will work. Leaving an SSH key in the `authorized_keys` file on a machine can be a useful backdoor, and you don’t need to deal with any of the issues of unstabilised reverse shells like Control-C or lack of tab completion.

**Answer the questions below**

1. _Check the SSH Private Key in `~/Public-Crypto-Basics/Task-5`. What algorithm does the key use?_

Answer: `RSA`

**Summary of these protocols**

```
🔐 TLS Handshake begins

    Your browser connects to the server and receives its digital certificate (with RSA or ECDSA public key).

    It verifies the server is legit.

🔄 DH Key Exchange

    Both sides run a Diffie-Hellman exchange (using public values) to securely agree on a shared session key, without sending it directly.

🔑 Session Key is established

    This is a symmetric key used to encrypt data fast (with AES).

📡 Encrypted Communication

    All HTTP traffic (requests, responses) is now encrypted with AES using that session key.
```
