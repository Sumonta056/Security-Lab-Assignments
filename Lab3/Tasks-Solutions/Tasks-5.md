## Task – 5: Generating Message Digest

- `Plaint.txt` file is used to generate the hash value using the `SHA-256`, `MD-5`, and `SHA-1` one-way hash algorithm.

```
Hlw ! I am Sumonta Saha Mridul. This is a sceret Message !
```

1. ✅ Generating the hash value for a file using the **`SHA-256` one-way hash algorithm.**

```bash
 openssl dgst -sha256 plain.txt
```

- Output Value:`-sha256` one-way hash algorithm

```bash
SHA2-256(plain.txt)= a1dad895a6659ce91ddc1dbecced50a4c449a43d0d1d7c6f50066e05c1d86bea
```

2. ✅ Generating the hash value for a file using the **`MD-5` one-way hash algorithm.**

```bash
openssl dgst -md5 plain.txt
```

- Output Value: `-md5` one-way hash algorithm

```bash
MD5(plain.txt)= 9698daa45366b06e49732be280a7c675
```

3. ✅ Generating the hash value for a file using the **`SHA-1` one-way hash algorithm.**

```bash
openssl dgst -sha1 plain.txt
```

- Output Value: `-sha1` one-way hash algorithm

```bash
SHA1(plain.txt)= 049e23ff79275222a395988ca14efac47690829e
```

![alt text](../assets/image-19.png)

<hr>
