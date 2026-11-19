## Password

### Example of how username and password store in server:
if you think it is like this:
alice: apple
bog: banana

Email -> alice: apple <- password
Email -> bob: banana <- Password

## Rather than storing the password a clear text we go ahead this techniques:

### Hashing 
**password -> hash**
- is a process of taking a password as input and conveting it into a hash or hash value.
- This hash value they don't look like English, they typically a strings of text that have letters and numbers, but generally of some fixed length typically.

**Note:** 
- **Fixed length** refers to data, output, or structures that have a **set and unchanging size**, regardless of the size of the input or any other conditions. In the context of computing, cryptography, and data storage, it ensures consistency and predictability in processing and storage.
- **Arbitrary length** refers to the idea that an input can be of **any size or length**, from very short (a few bytes) to extremely long (millions of bytes), and the system, algorithm, or function can still process it.


![[Pasted image 20241203195236.png]]

When the password is inputted it will go to -> Hash function that contains formula and method of converting, then it will -> Output the answer.

Password -> Hash function -> Hash

Example: apple ->  Hash function  -> 1 (because A of the apple is 1 in the alpabet. This is an 
example but don't know how to convert it) 

Example 2: banana -> Hash function -> 2

**Explain Hash by chat gpt:**
Hashing is a process used to convert data of any size into a fixed-size string of characters, typically through a mathematical function called a _hash function_. The output, called a _hash value_, _hash code_, or _digest_, uniquely represents the input data.

For example:

- Input: "Hello"
- Hash using SHA-256: `185f8db32271fe25f561a6fc938b2e264306ec304eda518007d1764826381969`

So this means that data store in the database store like this:

Alice: ....13wEYFwfoiwh
Bob: ...wuJuw13KIy

So this is the good thing to enchance the security of user's account. Imagine if the database contains password in a clear text, it easy to steal the accounts and hacker may do credential stuffing on other user's account.

### Attacks that some hacker do when your password is Hash:

#### Dictionary Attack
- Assuming they break the database that contains the user's credentials. They can open a file that contains lots of english word or predefine password that they can try, first they type in a certain password and convert it into hash. Then they compare those two Hash in the password column of database if they are same. 
- But this is a lots of work and it can cost more time and effort. 

#### Brute Force Attack
- If they have the record on the database and password is encrypted, they can also do a brute force attack, they generate a lots of text and convert it into hash then compare it into the database. But i cost a lots of time and effort specially if you have a strong password and unique.


#### Rainbow Tables
- is a table that contain and generate a lots of words, texts and etc that may use as a password, and also that is all converted into hash value, it reduce the time amount that hacker spend when comparing those sample of Hash value into those hashes password in the database to get the clear text password.
- But this need a lots of storage and data, so it also cost you not only time, but also a lots of money.


### So what if the credentials are this:

Carol: cherry
Mike: cherry

#### Hash version of record:

Carol: ...2hIOhu24g
Mike: ...2hIOhu24g

When the hacker see this record. This is common sense that those hash password are the same. They don't know carol or mike password, but this gives a hint that carol and mike are have the same password.


### So can we Fix this the same Hash record?

Salting
- It refers to adding random data (called a "salt") to input data, typically passwords, before processing or hashing them. This is a security measure commonly used in cryptography and data security to protect against attacks, especially those involving precomputed tables like rainbow tables.
- This is used to avoid two people with the same password are going to have same hash value.

![[Pasted image 20241204190847.png]]

**How it Works**:

- A **salt** is a random string of characters generated for each password.
- The salt is appended or prepended to the password before it’s hashed.
- The resulting salted hash is stored in the database, along with the salt itself.

**Prepended**: The salt is added **before** the password.
    
    - Example:
        - Password: `mypassword`
        - Salt: `x8$@d12`
        - Salted Input: `x8$@d12mypassword`
**Appended**: The salt is added **after** the password.
    
    - Example:
        - Password: `mypassword`
        - Salt: `x8$@d12`
        - Salted Input: `mypasswordx8$@d12`

**Example:**

**Password input:** Cherry
**Salt:** 50aZaB
**Salted input:** 50aZabCherry  (Salted input is Password + Salt)
**Hash Value:** 50aZaBa20oh..


![[Pasted image 20241204191201.png]]

It used different salt per different user just incase their have the same password.

Carol: Cherry  -> Carol: 50aZaBa20oh...
MIke: Cherry  -> Mike: 14AfwWacbZ...

### This is example of hash nowadays:

John: &Aa91dfd9ddb4198affc5c194cd8ce6d338fde470e2a1a2e17fb64db108ea5a5c4e
Luke: &Aa8d969eef6ecad3c29a3a629280e686cff8c4d4eae3c9bdfabdf34b1afdc365e0
Peter: &Aae038dc76a702b7f70d38c416458c0c7b8b13e1e615c01191323fef8247b92e15

 So if you try to cracks or brute force a hash value it gives you a quadrillion or quatillion of possible passwords.


### One of the Weaknesses of Website

If you try to forgot your password on Gmail or other website it needs a phone or other email, and it sends a code. But if you encounter a website that if you forgot a password and prove that you are. And it send not code but your forgotten password, Do not use that website they are not secure. Because that website is not practicing best practices. They can see or know your password and they are vulnerable for hackers. 

##### One of the National Institute of Standards and Technology (NIST) says:
Verifiers SHALL store memorized secrets in a form that is resistant to offline attacks. Memorized secrets SHALL be salted and hashed using a suitable one-way key derivation function... Their purpose is to make each password guessing trial by an attacker who has obtained a password hash file expensive and therefore the cost of a guessing attack high or prohibitive.

##### HASH Categories Nowadays:
- SHA-224
- SHA-256
- SHA-384
- SHA-512
- SHA-512/224
- SHA-512/256
- SHA3-224
- SHA3-256
- SHA3-384
- SHA3-512
- Etc

##### Types of Algorithm to be used to verify the authenticity and Integrity of messages:
- CMAC
- HMAC
- KMAC
- Etc

### One-Way Hash Functions 
**arbitrary length -> fixed length**
- is a cryptographic function that takes an input (or message) and produces a fixed-length output, known as a **hash value** or **digest**, which is unique to that input. The key characteristic of a one-way hash function is that it is computationally extremely difficult to reverse the process and retrieve the original input from the hash value.

- Mathematical functions or in the programming, it is a functions written in the language like python or otherwise, that take as input a string of arbitrary length.

**One-Way Hash Functions is a Cryptographic Functions**

## Cryptography 
is a all about the practice and study of securing data, while transit from one point to another. 

### Cryptanalysis
- It is a study or practice of analyzing or breaking cryptographic systems to uncover hidden information, such as plaintext messages or secret words,  without prior access to the secret key.
### Cryptographic Functions
- are algorithms used in the field of cryptography to secure data by performing various operations on plaintext to transform it into ciphertext or provide other security-related functions, such as ensuring data integrity, authentication, or non-repudiation. 

- These functions are fundamental to modern security protocols like SSL/TLS, digital signatures, and data encryption.

#### Types of Cryptographic Functions by Chatgpt:

1. **Hash Functions**:
    
    - A cryptographic hash function takes an input (or message) and produces a fixed-length output (hash). The output is unique to the input, and it is computationally infeasible to retrieve the original input from the hash.
    - **Properties**:
        - One-way (irreversible).
        - Deterministic.
        - Collision-resistant (hard to find two different inputs with the same hash).
    - **Examples**:
        - **MD5** (outdated for security purposes).
        - **SHA-256**, **SHA-3**.
        - **RIPEMD-160**.
    - **Use Cases**:
        - Data integrity (e.g., checking file authenticity).
        - Password storage (storing password hashes rather than plaintext).
        - Digital signatures and certificates.
2. **Symmetric Key Encryption**:
    
    - In symmetric key encryption, the same key is used for both encryption and decryption. The key must remain secret between the sender and the recipient.
    - **Examples**:
        - **AES** (Advanced Encryption Standard).
        - **DES** (Data Encryption Standard) – outdated.
        - **RC4**.
    - **Use Cases**:
        - Encrypting files and messages.
        - Secure communications between two parties who share the same key.
3. **Asymmetric Key Encryption (Public Key Cryptography)**:
    
    - In asymmetric encryption, two different keys are used: one for encryption (the **public key**) and one for decryption (the **private key**). The public key can be shared openly, but only the holder of the private key can decrypt the data.
    - **Examples**:
        - **RSA** (Rivest–Shamir–Adleman).
        - **ECC** (Elliptic Curve Cryptography).
        - **ElGamal**.
    - **Use Cases**:
        - Secure data transmission (e.g., in protocols like SSL/TLS).
        - Digital signatures.
        - Key exchange protocols (e.g., Diffie-Hellman).
4. **Digital Signatures**:
    
    - A digital signature is a cryptographic function that provides a way to verify the authenticity of a message or document. It uses asymmetric key encryption.
    - **How It Works**:
        - A user signs a message using their private key. Anyone with access to the public key can verify the signature and ensure that the message came from the legitimate sender and was not altered.
    - **Examples**:
        - **RSA** digital signatures.
        - **ECDSA** (Elliptic Curve Digital Signature Algorithm).
    - **Use Cases**:
        - Verifying the authenticity of emails, documents, and software.
        - Non-repudiation in legal or financial transactions.
5. **Key Derivation Functions (KDFs)**:
    
    - Key derivation functions are cryptographic functions used to derive one or more cryptographic keys from a secret value (such as a password). They ensure that the derived keys are random and not easily guessable.
    - **Examples**:
        - **PBKDF2** (Password-Based Key Derivation Function 2).
        - **bcrypt**.
        - **Argon2**.
    - **Use Cases**:
        - Password hashing and storage.
        - Generating keys for encryption from a shared secret.
6. **Message Authentication Codes (MACs)**:
    
    - A MAC is used to verify the integrity and authenticity of a message. It is similar to a hash, but it also requires a secret key.
    - **Examples**:
        - **HMAC** (Hash-Based Message Authentication Code).
        - **CMAC** (Cipher-Based Message Authentication Code).
    - **Use Cases**:
        - Verifying the authenticity of messages in protocols like TLS and IPSec.
        - Protecting data integrity in communication channels.
7. **Random Number Generators (RNGs) and Pseudorandom Number Generators (PRNGs)**:
    
    - These cryptographic functions generate random values used in various cryptographic algorithms, such as key generation, nonce creation, and session tokens.
    - **Examples**:
        - **SHA-256**-based PRNG.
        - **Fortuna**.
        - **AES-CTR** mode for generating random numbers.
    - **Use Cases**:
        - Generating keys for encryption.
        - Session identifiers.
        - Nonces in authentication processes.











### Cryptography can broken down different categories:

#### Code
- It is not type of code that written in python or other language, It has nothing todo in software.
- But it is a mapping between what we'll call code of words and the actual message.
- It is a book of words that contains a example words and the converted code on those words.

#### Encode
plaintext -> codetext
- It means a taking a plaintext as an input and converting it and output as a codetext.

#### Decode
codetext -> plaintext
- This is the opposite of encode it takes the codetext and converting it and output as a plaintext.

#### Ciphers
- It is a method or algorithm used to encrypt and decrypt data, transforming plaintext into cipher text (unreadable, scrambled text) and vice versa. 

#### Encipher (or Encrypt)
plaintext -> ciphertext
- It is a method of converting a plain text into cipher text. the equivalent term of this and commonly used nowadays is **Encrypt**.

#### Decipher (or Decrypt)
cipher text -> plaintext
- It is a method of converting a ciphertext into plaintext. the equivalent term of this and commonly used nowadays is **decrypt**.












### How do we configure this ciphers and use the same algorithm but customize them:

#### Keys
- It an locks the capabilities of cipher, it is used not only you but other recipient.
- It also encrypt and decrypt those messages.
- It is not a physical object, but a big numbers.







### TYPES OF CRYPTOGRAPHY

#### A. Secret-Key Cryptography
- Also known as **symmetric cryptography**, it is a type of encryption where the same key is used both encrypting and decrypting data.
- It is called symmetric because the sender and receiver must used the same key to encode and decode the data to communicate securely.

![[Pasted image 20241206193732.png]]

There is the different algorithm for different cipher text but we used this simple algorithm (caesar cipher, a rotational cipher) Algorithm: if the value of A in the ABC is 1 then the key is 1, add the value of 1 into value of A, so the total is 2 value, so what is the 2 in ABC?. it is B.
![[Pasted image 20241206194810.png]]
If they get the cipher text, they not understand the meaning of that so they need the key also. But the real key in real world is not only 1,2,3 or any simple digits Commonly used is ROT 13 (Or Rotate in 13 places)

But there's not recommended using 26 as the rotating value, because if you use 26 as a key, 26 is the total numbers of letters so your are going in the exact value of the world that you encrypt.
Example: 
- Key 26
- Word: A
- Ciphertext output: A

But this algorithm to encrypt data is not secure at all, because you don't need a computer to decrypt it, you just need a pen and paper.

##### How to decrypt it?
- After you receive the cipher text and the key, write down the value of all ABC letters then get the letter of each word in cipher text then rotate the places (its either add position or by reverse)by the key value in. 


##### Some of Actual Algorithms used nowadays for Secret-Key Cryptography or Symmetric Key Cryptography
- AES 
- Triple DES
- ....

#### B. Public-Key Cryptography
Also known as **asymmetric key cryptography,** is a cryptographic system the uses a pair or two keys:
	**Public Key**: This key shared openly and is used to encrypt messages or verify digital signatures.
	**Private Key:** This key is kept secret and is used to decrypt messages or create digital signatures.

**When you send a message:**
![[Pasted image 20241206213448.png]]

**When you recieve a message:**
![[Pasted image 20241206213236.png]]
##### Example scenario: Alice wants to send a secret message to Bob.

###### Step 1: Key Generation

- Bob generates a **key pair**:
    - **Public key (PBK_Bob)**: Shared openly with everyone, including Alice.
    - **Private key (PRK_Bob)**: Kept secret by Bob.

###### Step 2: Alice Encrypts the Message

1. Alice writes a message: `Hello, Bob!`
    
2. Alice encrypts this message using Bob's **public key (PBK_Bob)**:
    
    - The encryption process ensures only the private key (PRK_Bob) can decrypt the message.
    
    **Encrypted message:** `Encrypted_Message = Encrypt(Hello, Bob!, PBK_Bob)`
    
3. Alice sends the encrypted message to Bob.
    
###### Step 3: Bob Decrypts the Message

1. Bob receives the encrypted message from Alice.
2. Bob uses his **private key (PRK_Bob)** to decrypt it:
    - **Decrypted_Message = Decrypt(Encrypted_Message, PRK_Bob)**
3. Bob now sees the original message: `Hello, Bob!`













### Some of Actual Algorithms used nowadays for Public-Key Cryptography Encryption or Asymmetric Key Cryptography
- Diffie-Hellman
- MQV
- RSA
- ....
##### RSA
**n=p * q**
...
- Is the one of the most popular algorithm that widely used public-key cryptography system that enables secure data transmission.
- Mathematical foundation: RSA is based on the computational difficult of factoring (or reversing the process) large composite numbers, which make it secure. 
-  Formula: n=p x q 
	p - is big prime number.
	q - is also a big prime number.
    n - is a total of p multiplied by q or vise versa.

- The n will used in this formula:
	**Formula:**
	**c=m^e mod n**  <-- Formula for enryption
	
	**m = c^d mod n** <-- Formula for decryption

	**c** - cipher text/enrypted message
	**m** -  (single letter, word, larger piece of data or file)
	**^e** - Public exponent for enryption
	**^d** - Private exponet for decryption
	**mod** - modulus or taking the remainder
	**n** - the total value of two big prime numbers that multiplied

###### How the enryption and decryption works.
**A. When creating a message.**
- The computer generate the a random number for e and d
- Then solving n by multiplying the generated 2 big prime numbers.

**B. When you sending a message.**
- the m (which are a character or words) is raising by the power (e) and divide by (d) and getting the modulo value.
- and convert the m by the character value of the modulo.

**C. When you receive that message**
- the c (ciphertext/encrypted message) is raising that value to the power of d then divide by the n then getting the modulo value of it.
- then, converting the c into the character value of the modulo value. 

###### If you want to dig deep this is how it works from chat gpt:
![[Pasted image 20241210201525.png]]
![[Pasted image 20241210201552.png]]
![[Pasted image 20241210201609.png]]
![[Pasted image 20241210201637.png]]
Note: that the e and d are also randomly generated by the computer.
###### It is used in the:
1. **Secure Communication Protocols**

- **TLS/SSL (Transport Layer Security / Secure Sockets Layer)**:
    - RSA is used during the handshake phase of HTTPS connections to securely exchange encryption keys.
    - The server provides its RSA public key in a certificate, and the client uses it to encrypt a session key.
- **Email Encryption**:
    - RSA is used in protocols like **OpenPGP** and **S/MIME** for encrypting emails and securely sharing keys.
- **SSH (Secure Shell)**:
    - RSA keys are commonly used for client authentication.


2. **Digital Signatures**

- RSA enables digital signatures, ensuring the authenticity and integrity of data or messages.
- Common use cases:
    - **Code Signing**: Ensures that software or firmware updates are from a trusted source (e.g., Windows updates, app downloads).
    - **Document Signing**: Used in e-signatures for contracts and legal documents (e.g., DocuSign).
    - **Certificates**: RSA is used by **Certificate Authorities (CAs)** to sign digital certificates in the **X.509** standard for HTTPS websites.


3. **Key Exchange**

- RSA can be used to exchange symmetric encryption keys in protocols like **TLS/SSL**.
- For example, a client encrypts a randomly generated session key with the server's RSA public key, and the server decrypts it with its private key.


4. **Authentication**

- **Multi-Factor Authentication (MFA)**:
    - RSA is used in systems like RSA SecurID tokens, which generate one-time passcodes based on cryptographic algorithms.
- **Identity Verification**:
    - RSA is used to verify the identity of a user, device, or service by validating RSA-signed certificates.


5. **Data Encryption**

- RSA is occasionally used to encrypt small pieces of data directly, such as:
    - Short messages or sensitive configuration files.
    - Encrypting symmetric keys for storage or transport.


6. **Blockchain and Cryptocurrencies**

- RSA is not commonly used in most blockchains (e.g., Bitcoin uses elliptic curve cryptography), but it is sometimes employed in hybrid systems or blockchain-related secure communication.


7. **File Encryption**

- **Tools like GPG/PGP** use RSA to encrypt files or their symmetric encryption keys.


8. **IoT and Embedded Systems**

- RSA is used in constrained environments for secure firmware updates, ensuring they are authentic and tamper-proof.














### Technique use in the public key cryptography:

#### A. Key Exchange
- is a process used to securely share secret key between two parties over a insecure channel.

**The two most commonly used in key exchange are:**
-  Diffie-Hellman <-- it is not encryption algorithm it is a key exchange protocol
- RSA <-- It is a encryption algorithm

##### Diffie-Hellman
- is a cryptographic protocol that allows two parties to securely exchange a secret message over a unsecured communication channel.
- Each party generates a private key (kept secret) and computes a public key (shared with the other party).
- is not an encryption algorithm; it is a **key exchange protocol**. Its purpose is to allow two parties to securely agree on a **shared secret key** over an insecure channel.

**Formula:**
A = g^a mod p
B = g^b mod p 
...

**g** - is a generator (it generate a random number)
**A, B** - These are the **public keys** derived from the private keys, Each party computes their public key by raising g to the power of their private key (modulo p), and then they share these values with each other.
**a, b** - These are the private keys chosen by the both parties.
mod - Modulus

**How it works:**
- Both party generate private key (a,b) and prime numbers (p)
- Each party computes their public key using the formula (Public Key=g ^ private key mod p)
- Each party computes the shared secret using the other party's public key and their own private key (shared secret = Other's Public key ^  Own private key mod p)
- They receive the same value although the information didn't not across the internet.

**We will do this mathematical computation to ensure that the both parties receive the same shared secrets. So when they receive that secret messages they can use the symmetric cryptography to decrypt it.**
###### It is used in the
1. **Secure Communication Protocols**

- **TLS/SSL (Transport Layer Security / Secure Sockets Layer)**:
    - Used to establish a shared secret during the handshake phase of encrypted connections (e.g., HTTPS for websites).
    - Modern versions use **Elliptic Curve Diffie-Hellman (ECDH)** for efficiency and security.
- **SSH (Secure Shell)**:
    - DH is used to negotiate a session key for encrypting communication between clients and servers.
- **IPSec (Internet Protocol Security)**:
    - Used in VPNs for secure key exchange in establishing encrypted tunnels.


2. **End-to-End Encryption**

- **Secure Messaging Apps**:
    - Apps like **WhatsApp, Signal, and Telegram** use Diffie-Hellman (or its elliptic curve variant) to securely exchange encryption keys for end-to-end encryption.
- **Email Encryption**:
    - Protocols like OpenPGP can use Diffie-Hellman for key exchange.


3. **Virtual Private Networks (VPNs)**

- DH is used in VPN protocols like **IKE (Internet Key Exchange)** to securely exchange keys for encrypting VPN traffic.


4. **Wireless and IoT Security**

- **WPA3 (Wi-Fi Protected Access 3)**:
    - Uses **Simultaneous Authentication of Equals (SAE)**, a Diffie-Hellman-based protocol for secure key exchange in Wi-Fi networks.
    

5. **Digital Signatures and Authentication**

- **Hybrid Cryptography**:
    - DH is combined with public-key cryptography (like RSA) for mutual authentication and secure key exchange in systems like SSL/TLS.
- **Zero-Knowledge Proofs**:
    - Variants of Diffie-Hellman are used in zero-knowledge proof systems for identity verification without exposing credentials.


6. **Blockchain and Cryptocurrency**

- Some blockchain platforms and cryptocurrencies use DH or similar algorithms for secure peer-to-peer key exchange and signing transactions.







#### B. Digital Signatures
is a cryptographic technique used to ensure the authenticity, integrity, and non-repudiation of digital data or messages. It serves as a digital equivalent of a handwritten signature or a stamped seal but offers far more security.

##### Algorithms are used in Digital Signatures:
This algorithms are giving you the ability to sign signatures on the documents or other information digitally. 
- DSA
- ECDSA
- RSA
- ....

##### What does mean to SIGN digitally?
- It is not like physically signing, It's all mathematics are involved

**So how its works?**

The input(message) is the document or contract that you want to sign, it will convert it into hash value.
   ![[Pasted image 20241212205000.png]]

Then, you use your private key, and pass the document or message(which is already computed as hash value using the digital algorithm), and the output of that process is your digital signature(It is not a human signatures, its look like a string of characters also).  

![[Pasted image 20241212201648.png]]

It is opposite of public key encryption, which is they using your public key to encrypt the data and you decrypt it using the private key. But in the case of digital signature is upside-down.

You used your private key and the hash of your message to digitally sign a document and the output of that is the signature (which is a number or strings of characters) and send it to recipient and verify it.

##### How they VERIFY your digital signature?
- When that recipient gets your document with your digital signatures, they verify it to confirm that your signed it.

**So how it works?**

They receive two things the document and the digital signatures(it is not a human signature, but it is a string of characters).

The recipient will convert the document into a same hash function you used, because the document might be long so you will collapse it into short hash representation thereof, just like our use of password. 
![[Pasted image 20241212203836.png]]

Remember the public key is receive accessible for anyone. So you receive their public key also.

You take the public key of the person who claimed that signed that document, you take their signature, and you decrypt it using their public key. That will output the same hash value you calculated.

![[Pasted image 20241212204636.png]]

The hash value of the person who sign the document that should match the hash value you've just calculate when you decrypt it using the public key of the person who claimed that signed the document, to confirm he/she was the person who sign that document or contract.

In summary when they verify the digital signatures they receive not only the message, but your claimed digital signature also. So they try to decrypt the signature using your public key, So the public key reverse the encryption done by a private key. 

When the recipient get the exact same hash value after decrypting what you send them, it says that i was you who signed them. 

So any signature you can decrypt with my public key, must have been encrypt with my private key. 

##### Extra info from chatgpt
###### Key Features:

1. **Authentication**: Verifies the identity of the sender. Only someone with the sender's private key could have created the signature.
2. **Integrity**: Ensures the data has not been altered during transmission. Any change in the data will invalidate the signature.
3. **Non-repudiation**: Prevents the sender from denying their involvement, as the digital signature is unique and traceable to their private key.

**How It Works:**

1. **Key Pair Generation**: A pair of cryptographic keys—one public and one private—is generated.
    
    - **Private Key**: Kept secret by the signer and used to create the digital signature.
    - **Public Key**: Shared with others to verify the digital signature.
2. **Signing Process**:
    
    - The sender creates a hash (a fixed-size, unique output) of the message using a hashing algorithm (e.g., SHA-256).
    - The hash is encrypted using the sender’s private key, producing the digital signature.
3. **Verification Process**:
    
    - The recipient decrypts the digital signature using the sender’s public key to retrieve the original hash.
    - The recipient computes the hash of the received message and compares it with the decrypted hash. If they match, the signature is valid.

**Use Cases:**

- **Electronic Documents**: Signing contracts, agreements, or forms digitally.
- **Secure Email Communication**: Ensuring the authenticity of email senders.
- **Blockchain**: Verifying transactions.
- **Software Distribution**: Confirming the integrity and origin of software.

**Benefits:**

- High security due to cryptographic methods.
- Faster and more efficient than manual signatures.
- Environmentally friendly by reducing paper usage.



#### C. PASSKEYS
- It is implementation of a standard called WebAuthn (Web Authentication).
- Passkeys are modern, passwordless authentication method design to improve the security and simply the login process. They rely on cryptographic keys(private and public keys), eliminating the need for users to remember or manually enter passwords. 

**How it works?**

When we go to the website or an app, rather then being prompted to create a username and password, you will prompted to create a passkeys. That means your device(laptop, phone and etc) will ask your fingerprint, scan you face or maybe a pin code or a short number.

Then after that your device will generate a private and public key just for that one website or app.

Your device will send the public key to that website or app, along with your user credentials(such as ID, usernames or some identifying information) to probaly to know you.
Note: This public and private key are used only for this website or app.


**When you want to lOGIN the website or app** 

the website will send you a challenge when you visit. The challenge is a like a number or word or phrase, its a piece of randomly-generated piece of data that the website that wants you to digitally sign.

So the you pass your private key with the challenge and convert it into signature with digital signature algorithm, It send that digital signature to the website.
![[Pasted image 20241213150611.png]]

**How does the website VERIFY that?**

The website or app use your public key to decrypt your signature that will output a challenge, once that challenges matches the website send you second before, it must be you.
![[Pasted image 20241213153319.png]]

By the used of this method we don't need to remember dozens of different passwords for all our accounts, but it requires that, we can not lose the device or the devices that registered for these website.  

But the the technology of the word increasingly, as the word providing a cloud services, whether it's with apple or microsoft or google that can synchronize your passkeys across devices.  

##### Extra info from chatgpt

###### Key Features:

1. **Passwordless Authentication**: Replaces traditional passwords with more secure alternatives.
2. **Based on Public-Key Cryptography**: Uses a pair of cryptographic keys:
    - **Private Key**: Stored securely on the user's device and never shared.
    - **Public Key**: Stored with the service (e.g., a website) and used for verification.
3. **Biometric or Device Authentication**: Users typically authenticate using built-in device features such as:
    - **Biometrics**: Fingerprint or facial recognition.
    - **PINs**: Device PINs (used as an additional factor on some devices).

###### How Passkeys Work:

1. **Account Creation**: When setting up an account with a passkey, a pair of cryptographic keys is generated:
    - The **private key** stays on the user’s device.
    - The **public key** is sent to the service and stored.
2. **Login Process**:
    - The user initiates login by providing their username or selecting their account.
    - The service sends a challenge (a random piece of data) to the user's device.
    - The user's device uses the private key to sign the challenge and returns it to the service.
    - The service verifies the signed challenge using the public key. If valid, access is granted.

###### Benefits:

1. **Increased Security**:
    - Eliminates password-related vulnerabilities (e.g., phishing, brute-force attacks, password reuse).
    - Private keys never leave the device or get stored on servers.
2. **Convenience**:
    - No need to remember or type passwords.
    - Faster and more seamless login experience.
3. **Resistance to Phishing**:
    - Passkeys are tied to specific domains, making it impossible to use them on fraudulent sites.
4. **Multi-Device Support**: Passkeys can be synced securely across devices using mechanisms like iCloud Keychain or other cloud storage solutions.

###### Real-World Implementations:

- **Apple, Google, and Microsoft**: Leading tech companies have integrated passkeys into their platforms, allowing users to log in to apps and websites securely.
- **FIDO Alliance**: Passkeys are built on the FIDO (Fast Identity Online) standards, ensuring broad compatibility and security.

###### Use Cases:

- Logging into websites, apps, and devices.
- Authenticating for online banking or secure enterprise applications.
- Simplifying access to personal accounts across multiple devices.








### Securing data as it's moving back and forth and sitting on our systems.

#### Encryption Transit
- refers to protecting data while it is being transmitted from one place to another(such as over the internet or within a private network). 
- The goal of encryption in transit is to ensure that the data is secure and cannot intercepted or tampered with during the transmission.

##### How Encryption in Transit Works from chat gpt

1. **Data is Encrypted**:
    
    - Before data leaves the sender's system, it is encrypted using cryptographic algorithms.
    - This ensures that even if someone intercepts the data during transmission, they cannot read it without the decryption key.
2. **Data is Transmitted**:
    
    - The encrypted data travels over the network to the recipient (e.g., via HTTPS, VPN, or other secure protocols).
3. **Data is Decrypted**:
    
    - Once the data reaches its intended recipient, it is decrypted using the appropriate key, making it readable again.





##### Example Problem
You probably know that the data be encrypted whenever traveling from point A to B or vice versa. Whether that point B is gmail, whatapp and etc. 

We ideally want no one in between us or some machine in the middle that was able to get our data. You worried the scenario like this.

Where Alice try to communicate with Bob but there was a person in the middle named Eve. Maybe this is via wires or wireless nowadays on the internet. But maybe Eve is a company like gmail, amazon or etc.

**Alice <--> Eve <--> Bob**

Alice have secure connection from gmail and Bob has secure connection from gmail, but does not mean Alice have secure connection to Bob or their entirely communication are be encrypted.

Security does not really work through transitivity. The data will encrypted from A to E or from B to E, but it does not mean that E or Gmail can't read does data(like emails and etc). This is technically possible because there's nothing technically stopping them from reading them and everything. Hopefully there have policies.

So what is alternative for that thing?
answer: End-to-End Encryption

#### End-to-End Encryption (E2EE)
Alice <--> Bob
- is a method of secure communication where only the communicating parties (the sender and receiver) can read the messages.
- The data is encrypted on the sender's device and decrypted only on receiver's device, ensuring that no third party (not even the service provider) can access the content

###### How It Works (From chat gpt)

1. **Encryption at the Sender’s End:**
    - The sender’s device encrypts the message using a unique key (often derived from the recipient's public key in public-key cryptography).
    - The data becomes unreadable to anyone without the matching private key.
    
2. **Data Transmission**:
    - The encrypted message travels over the network (internet, cellular, etc.) to the recipient.
    
3. **Decryption at the Receiver’s End**:
    - The recipient’s device uses their private key to decrypt the message and restore it to its original form.







### Deletion
- refers to the process of removing the data or files form a system, database, or device.
- The depth of deletion (level to which data is removed) and what happens to the data afterward can depending on the method used.

#### Types of Deletion

1. **Soft Deletion**:
    
    - The data is marked as "deleted" but is not physically removed from storage.
    - Examples:
        - Moving a file to the "Recycle Bin" or "Trash."
        - Marking a record in a database as "inactive" without removing it.
    - **Can be recovered** easily since the data still exists.
2. **Hard Deletion**:
    
    - The data is permanently removed from the system or storage.
    - Examples:
        - Emptying the "Recycle Bin."
        - Overwriting the data or securely deleting files.
    - **Difficult to recover**, especially if secure deletion techniques are used.


#### Problem

When i deleting a file it goes to recycle bin or trash can, so you will consider emptying the trash can, But emptying the bin does not generally delete the data that we might expect. Windows or mac not actually get rid of your file, they just forget where it is. When you see the inside of memory, you see the 0's and 1's that is your specific files. 

When you empty the trash basically they still in a specific slot of your hardrive and the computer label that slot as its no longer you use, so when they have a new file that slot will overwritten. But when that files is overwritten, some of pieces of that files is still in there. So you need a better practices like **Secure Deletion** to delete a files.


#### Secure Deletion
- it refers to the process of completely and irreversibly removing the data from a system or storage device so that it cannot be recovered, even with specialized tools.
- This is essential when dealing with sensitive and confidential information that must be permanently erased, ensuring that no one can retrieve it.


##### How can we used this?

###### Full-Disk Encryption (FDE)
- Is a security feature that encrypts the entirely hard drive or storage device, ensuring that the all data stored is protected. 
- The data, including the operating systems, files, programs and even the free space on the disk are encrypted Only authorized users woth the correct decryption key(often password or hardware token) can access the data.


When you activate that feature it is actually incarnation of an idea known as **Encryption at Rest**.

Unlike Encryption transit, which is encrypt the data and travel any where. The Encryption at Rest is, encrypt the data and just sitting their in your devices.

**What is the advantage of it?**
- if the device is stolen as long as the device are lock or close, they cannot open your data. 

So when i used my device and i login with my password or decryption key, the encrypted data will be decrypt by itself.


##### The downside or an evil side of full-disk encryption

###### Ransomware
- It is a type of malware that locks or encrypts your data or devices and ask for ransom (money or other things).

When the hackers have an access in your devices or the devices of a corporation or a company. it is not common to used the full-disk encryption technique to not only your lock device but encrypt your data also. Then they ask for some ransom. 





### Quantum Computing
refers to a type of computing uses of quantum mechanics to process information in a fundamentally different way unlike classical computers, which uses bits to represent data as either 0 or 1, quantum computers uses quantum bits, or qubits, which can represent data in more complex ways(example represent not only 0 but 1 also). So it can be not just one state but two state.