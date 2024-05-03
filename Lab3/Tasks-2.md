

## Encryption mode - ECB vs CBC (3 Marks)

![alt text](image-7.png)
![alt text](image-8.png)

1. Encrypt the image using AES encryption in EBC mode && Cipher Type `-aes-128-ecb`
```bash
   openssl enc -aes-128-ecb -in panda.bmp -out image_ecb.bmp -K 0123456789abcdef0123456789abcdef
```
- Lets See Inside the Encrypted File
```bash
    ghex image_ecb.bmp
```
![alt text](image-9.png)

- Reconstruct the header file of the encrypt with ghex from the original file.
- Replacing the first 54 bytes of image_ecb.bmp with the first 54 bytes of panda.bmp

![alt text](image-10.png)

- We Can See ECB encryption exposes patterns in the encrypted image of the original image.


2. Encrypt the image using AES encryption in CBC mode && Cipher Type `-aes-128-cbc`
```bash
   openssl enc -aes-128-cbc -in panda.bmp -out image_cbc.bmp -K 0123456789abcdef0123456789abcdef -iv 0123456789abcdef0123456789abcdef
```
- Lets See Inside the Encrypted File
```bash
    ghex image_cbc.bmp
```
![alt text](image-11.png)

- Reconstruct the header file of the encrypt with ghex from the original file.
- Replacing the first 54 bytes of image_cbc.bmp with the first 54 bytes of panda.bmp

![alt text](image-13.png)

- We Can See CBC encryption doesn't exposes patterns in the encrypted image of the original image.

<hr>



