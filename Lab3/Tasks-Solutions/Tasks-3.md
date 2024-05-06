## Task – 3: Encryption mode – Corrupted Cipher Text

#### ❓ Question : How much information can you recover by decrypting the corrupted file, if the encryption mode is ECB, CBC, CFB, or OFB, respectively?

- **ECB Mode Recovery**: In ECB mode, each block of plaintext is encrypted independently of other blocks. This means that if a single block is corrupted, only that specific block can be decrypted without affecting the others. Therefore, you can recover the entire file except for the corrupted block.

- **CBC Mode Recovery**: CBC mode uses an IV (Initialization Vector) and chains the encryption of each block to the previous one. If a block is corrupted, it cannot be decrypted without the corresponding ciphertext block. However, if you have the corrupted ciphertext block and the IV, you can decrypt the entire file except for the corrupted block.

- **CFB Mode Recovery**: Similar to CBC, CFB also chains the encryption of each block to the previous one. The difference lies in how the chaining is done. If a block is corrupted, it cannot be decrypted without the corresponding ciphertext block. Recovery depends on having the corrupted ciphertext block and the IV.

- **OFB Mode Recovery**: OFB mode generates a keystream block by block and XORs it with the plaintext block to produce the ciphertext. If a block is corrupted, it cannot be decrypted without the corresponding ciphertext block. Recovery depends on having the corrupted ciphertext block and the IV.

#### ❓ Question : Why These Differences?

The differences in recovery capabilities stem from how each mode processes and encrypts data:

1. ECB treats each block as independent, making it easier to recover data but less secure against patterns in the plaintext.
2. CBC, CFB, and OFB all introduce some form of chaining or feedback mechanism, which makes them more secure against patterns but also complicates recovery from corrupted blocks because they depend on the integrity of the entire chain.

#### ❓ Question : What are the implications of these differences?

1. ECB (Electronic Codebook): This method has a weakness in that it is susceptible to plaintext patterns and does not effectively diffuse information.
2. CBC (Cipher Block Chaining): This technique offers improved diffusion and is more resistant to attacks that utilize known plaintext, compared to ECB.
3. CFB (Cipher Feedback) and OFB (Output Feedback): These modes have the benefit of error propagation, which means that a corruption in one block does not affect the following blocks. This feature can be beneficial in certain situations.

<hr>

### Test Encryption mode – Corrupted Cipher Text

- Create a 64 bytes long Plain.txt

```
Hlw ! I am Sumonta Saha Mridul. This is a sceret Message !
I am doing encryption mode in corrupted cipher text..
Checking what happens i modify some code in decription

Welcome to my document! This is a sample text file created for demonstration purposes. In this document, we'll explore various topics related to technology, science, and creativity. Feel free to edit and customize this text as needed. Remember to save your changes before closing the file. Enjoy exploring!
```

1. **✅ Encrypt the file using AES encryption in ECB mode && Cipher Type `-aes-128-ecb`**

```bash
    openssl enc -aes-128-ecb -e -in plain.txt -out cipher1.bin -K 00112233445566778889aabbccddeeff
```

- Lets See Inside the Encrypted File

```bash
    cat cipher1.bin
```

- Now Open the encrpted File in Ghex

```bash
    ghex cipher1.bin
```

![alt text](../assets/image-15.png)

- **Modifying the `30th byte` from `C` to `2`**

- Now Decrypt the file using AES encryption in ECB mode && Cipher Type `-aes-128-ecb`

```bash
    openssl enc -aes-128-ecb -d -in cipher1.bin -out decipher1.txt -K 00112233445566778889aabbccddeeff
```

```bash
    cat decipher1.txt
```

- Lets Look the Decrypted File

```bash
    cat decipher1.txt
```

```
Hlw ! I am Sumonta Saha Mridul. :��ϕQ���vo��z Message !
I am doing encryption mode in corrupted cipher text..
Checking what happens i modify some code in decription

Welcome to my document! This is a sample text file created for demonstration purposes. In this document, we'll explore various topics related to technology, science, and creativity. Feel free to edit and customize this text as needed. Remember to save your changes before closing the file. Enjoy exploring!
```

- **🔖 Here we can see that the `30th byte` is corrupted and the message is not decrypted properly.**

![alt text](../assets/image-14.png)

2. **✅ Encrypt the file using AES encryption in CBC mode && Cipher Type `-aes-128-cbc`**

```bash
    openssl enc -aes-128-cbc -e -in plain.txt -out cipher2.bin -K 00112233445566778889aabbccddeeff -iv 01020304050607080550101410114501
```

- Lets See Inside the Encrypted File

```bash
    cat cipher2.bin
```

- Now Open the encrpted File in Ghex

```bash
    ghex cipher2.bin
```

![alt text](../assets/image-16.png)

- **Now modify the `30th byte` from `1` to `3`**

- Now Decrypt the file using AES encryption in ECB mode && Cipher Type `-aes-128-cbc`

```bash
    openssl enc -aes-128-cbc -d -in cipher2.bin -out decipher2.txt -K 00112233445566778889aabbccddeeff -iv 01020304050607080550101410114501
```

- Lets Look the Decrypted File

```bash
    cat decipher2.txt
```

```
Hlw ! I am Sumonta Saha Mridul. nq�*!p�ny1�L~.� Message !
I am�doing encryption mode in corrupted cipher text..
Checking what happens i modify some code in decription

Welcome to my document! This is a sample text file created for demonstration purposes. In this document, we'll explore various topics related to technology, science, and creativity. Feel free to edit and customize this text as needed. Remember to save your changes before closing the file. Enjoy exploring!

```

- **🔖 Here we can see that the `30th byte` is corrupted and the message is not decrypted properly.**

![alt text](../assets/image-17.png)

Observation: Different encryption modes like ECB, CBC, CFB, and OFB offer varying levels of resilience to data corruption, with ECB being the least resilient and CFB/OFB providing better error propagation, affecting the recovery of information.

<hr>


