## Task – 1: AES encryption using 3 different modes

- Create a New File `plain.txt` and adding several lines of texts

```bash
    nano plain.txt
```

```plaintext
    Hlw ! I am Sumonta Saha Mridul. This is a sceret Message !
```

```bash
    ghex plain.txt
```

![alt text](./assets/image-4.png)

1. **✅ Encrypt the file using AES encryption in ECB mode && Cipher Type `-aes-128-ecb`**

```bash
    openssl enc -aes-128-ecb -e -in plain.txt -out cipher1.bin -K 00112233445566778889aabbccddeeff
```

- Lets See Inside the Encrypted File

```bash
    cat cipher1.bin
```

- Decrypt the file using AES encryption in ECB mode && Cipher Type `-aes-128-ecb`

```bash
    openssl enc -aes-128-ecb -d -in cipher1.bin -out decipher1.txt -K 00112233445566778889aabbccddeeff
```

```bash
    cat decipher1.txt
```

```bash
    ghex decipher1.txt
```

![alt text](./assets/image.png)
![alt text](./assets/image-5.png)

<hr>

2. **✅ Encrypt the file using AES encryption in CBC mode && Cipher Type `-aes-128-cbc`**

```bash
    openssl enc -aes-128-cbc -e -in plain.txt -out cipher2.bin -K 00112233445566778889aabbccddeeff -iv 01020304050607080550101410114501
```

- Lets See Inside the Encrypted File

```bash
    cat cipher2.bin
```

- Decrypt the file using AES encryption in ECB mode && Cipher Type `-aes-128-cbc`

```bash
    openssl enc -aes-128-cbc -d -in cipher2.bin -out decipher2.txt -K 00112233445566778889aabbccddeeff -iv 01020304050607080550101410114501
```

```bash
    cat decipher2.txt
```

```bash
    ghex decipher2.txt
```

![alt text](./assets/image-1.png)
![alt text](./assets/image-6.png)

<hr>

3. **✅ Encrypt the file using AES encryption in CFB mode && Cipher Type `-aes-128-cfb`**

```bash
    openssl enc -aes-128-cfb -e -in plain.txt -out cipher3.bin -K 00112233445566778889aabbccddeeff -iv 01020304050607080550101410114501
```

- Lets See Inside the Encrypted File

```bash
    cat cipher3.bin
```

- Decrypt the file using AES encryption in ECB mode && Cipher Type `-aes-128-cfb`

```bash
    openssl enc -aes-128-cfb -d -in cipher3.bin -out decipher3.txt -K 00112233445566778889aabbccddeeff -iv 01020304050607080550101410114501
```

```bash
    cat decipher3.txt
```

```bash
    ghex decipher3.txt
```

![alt text](./assets/image-2.png)
![alt text](./assets/image-3.png)

<hr>
