## 📝 Lab Assignment 5: : Securing Apache Web Server

- [✅ Tasks - 1 : Becoming a certificate authority](#-tasks---1--becoming-a-certificate-authority)

- [✅ Tasks - 2 : Creating a certificate for example.com](#-tasks---2--creating-a-certificate-for-examplecom)

- [✅ Tasks - 3 : Launching a simple web server with the certificate generated](#-tasks---3--launching-a-simple-web-server-with-the-certificate-generated)

- [✅ Tasks - 4 : Deploy HTTPS into Apache](#-tasks---4--deploy-https-into-apache)

<hr>

### 🔖 Tasks - 1 : Becoming a certificate authority

1. **Configure openssl.cnf:**
   - Copying the openssl.cnf file from /usr/lib/ssl/openssl.cnf to current directory.
   - Modifying openssl.cnf to suit the requirements, focusing on adjustments within the [CA_default] section to define directories and settings appropriately.

<div align = "center">

![alt text](./assets/image.png)

![alt text](./assets/image-1.png)

</div>

2. **Generating a self-signed certificate for our CA, filling in necessary information such as Country Name, Common Name, etc.**

<div align = "center">

![alt text](./assets/image-2.png)

</div>

The output of the command is stored in two files: ca.key and ca.crt. The file ca.key contains the CA’s private key, while ca.crt contains the public-key certificate.

<div align = "center">

![alt text](./assets/image-3.png)

![alt text](./assets/image-4.png)

</div>

<hr>

### 🔖 Tasks - 2 : Creating a certificate for example.com

1. **Generating public/private key pair :**

![alt text](./assets/image-5.png)

2. **Generating a Certificate Signing Request (CSR):**

![alt text](./assets/image-6.png)

3. **Generating Certificates:**
   - The names in your requests do not match with those of CA. So, OpenSSL refuses to generate certificates
   - Fix this and re-issue the above command

![alt text](./assets/image-7.png)
![alt text](./assets/image-8.png)
![alt text](./assets/image-9.png)

<hr>

### 🔖 Tasks - 3 : Launching a simple web server with the certificate generated

1. **Combining the secret key and certificate into one file:**

![alt text](./assets/image-10.png)

2. **Launch the web server using server.pem:**
   
![alt text](./assets/image-11.png)

![alt text](./assets/image-12.png)

3. **Error message from the browser:**

![alt text](./assets/image-13.png)

4. **Manually adding our CA’s certificate to the Firefox browser:**

![alt text](./assets/image-14.png)
![alt text](./assets/image-15.png)
![alt text](./assets/image-16.png)
![alt text](./assets/image-17.png)
![alt text](./assets/image-18.png)
![alt text](./assets/image-19.png)

5. **In webpage, showing certificaticates’ details:**

![alt text](./assets/image-20.png)

<hr>

### 🔖 Tasks - 4 : Deploy HTTPS into Apache

1. **Writing contents in /etc/apache2/sites-available/example.com.conf file:**

![alt text](./assets/image-21.png)
![alt text](./assets/image-22.png)
![alt text](./assets/image-23.png)

2. **Restarting the apache server:**

3. **Now, try to access the http://example.com. It’ll view the webpage in HTTPS:**

![alt text](./assets/image-24.png)

<hr>
