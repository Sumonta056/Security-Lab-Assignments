## Task – 4: Padding

- **✅ ECB Encryption & Decryption**

```bash
openssl enc -aes-128-ecb -e -in plain.txt -out cipher1.bin -K 00112233445566778889aabbccddeeff
```

```bash
openssl enc -aes-128-ecb -d -in cipher1.bin -out decipher1.txt -K 00112233445566778889aabbccddeeff
```

- **✅ CBC Encryption & Decryption**

```bash
openssl enc -aes-128-cbc -e -in plain.txt -out cipher2.bin -K 00112233445566778889aabbccddeeff -iv 01020304050607080550101410114501
```

```bash
openssl enc -aes-128-cbc -d -in cipher2.bin -out decipher2.txt -K 00112233445566778889aabbccddeeff -iv 01020304050607080550101410114501
```

- **✅ CFB Encryption & Decryption**

```bash
openssl enc -aes-128-cfb -e -in plain.txt -out cipher3.bin -K 00112233445566778889aabbccddeeff -iv 01020304050607080550101410114501
```

```bash
openssl enc -aes-128-cfb -d -in cipher3.bin -out decipher3.txt -K 00112233445566778889aabbccddeeff -iv 01020304050607080550101410114501
```

- **✅ OFB Encryption & Decryption**

```bash
openssl enc -aes-128-ofb -e -in plain.txt -out cipher4.bin -K 00112233445566778889aabbccddeeff -iv 01020304050607080550101410114501
```

```bash
openssl enc -aes-128-ofb -d -in cipher4.bin -out decipher4.txt -K 00112233445566778889aabbccddeeff -iv 01020304050607080550101410114501
```

![alt text](./assets/image-18.png)


### Analyze the Results

After running the commands, have encrypted and decrypted files for each mode. Compare the sizes of the original plaintext file and the decrypted files. Observe that the decrypted files are the same size as the original plaintext file, indicating that padding was correctly applied and removed in CBC and CFB modes. In ECB and OFB modes, the sizes may differ due to the nature of these modes, but ECB does not require padding, and OFB does not require padding either.

### Report Findings

- ECB: No padding is required because it operates on blocks directly.
- CBC: Requires padding because it operates on blocks, and the plaintext length might not match the block size.
- CFB: Requires padding because it operates on blocks of data.
- OFB: Does not require padding because it treats the encryption process as a - stream cipher.
