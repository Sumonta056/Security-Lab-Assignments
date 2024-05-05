## Task – 7: Keyed hash and HMAC (with Bonus Tasks)

- Plain Text File: `plain.txt`

```
Hlw ! I am Sumonta Saha Mridul. This is a sceret Message !
```

1. **Generate Hash Value H1 : For `HMAC-MD5`, use a key of 128 bits.**

```bash
openssl dgst -md5 -hmac "mykey" plain.txt
```

- **Output** the hash value for H1 for the modified file

```bash
HMAC-MD5(plain.txt)= e6b87de7fed721b49a0b08aef1305024ghhex
```

- Flipping Bit with `ghex` Tool

```bash
ghex plain.txt
```

![alt text](./assets/image-21.png)

- **Modify the File by Flipping One Bit (Change `61` to `20`)**

- Generate the hash value H2 for the modified file

```bash
openssl dgst -md5 -hmac "mykey" plain.txt
```

- Output the hash value for H2 for the modified file

```bash
HMAC-MD5(plain.txt)= 281db338ab6e5927c2dcd6b238ab9112
```

![alt text](./assets/image-22.png)

- **Counting how many bits are the same between H1 and H2. (Bonus Task)**

![alt text](./assets/image-23.png)

- **Number of matching bits: 184**

<hr>

2. **Generate Hash Value H1 : For `SHA256`, use a key of 256 bits.**

```bash
openssl dgst -sha256 -hmac "mylongerkey" plain.txt
```

- **Output** the hash value for H1 for the modified file

```bash
HMAC-SHA2-256(plain.txt)= 69bf09739792ead4a1f90a9e96235b19ef74bb659f371f9ead59b02fe6f69499
```

- Flipping Bit with `ghex` Tool

```bash
ghex plain.txt
```

![alt text](./assets/image-21.png)

- **Modify the File by Flipping One Bit (Change `61` to `20`)**

- Generate the hash value H2 for the modified file

```bash
openssl dgst -sha256 -hmac "mylongerkey" plain.txt
```

- Output the hash value for H2 for the modified file

```bash
HMAC-SHA2-256(plain.txt)= b2e47fcb6f288b15a5a4a010808a0ee1b1247df4826b90427a4e3f470e3af0b7
```

![alt text](./assets/image40.png)

- **Counting how many bits are the same between H1 and H2. (Bonus Task)**

![alt text](./assets/image41.png)

- **Number of matching bits: 125**

<hr>
