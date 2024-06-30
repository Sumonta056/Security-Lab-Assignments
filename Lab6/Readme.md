## 📝 Lab Assignment 6: Securing Apache Web Server – 2

### 🔖 Tasks - 1 :

1. **Enable the mod_rewrite module using a2enmod command.**

![alt text](./assets/image.png)

2. **Look at the /etc/apache2/sites-enabled directory to find the configuration file for port 80 for example.com**

![alt text](./assets/image-1.png)

3. **Testing Apache configuration and restart the Apache server**

![alt text](./assets/image-2.png)

4. **Testing example.com on your browser. It’ll show “Hello, World!”**

![alt text](./assets/image-3.png)

<hr>

### 🔖 Tasks - 2 :

1. Adding users to Apache web server using the following command

![alt text](./assets/image-4.png)
![alt text](./assets/image-5.png)

2. Use the following command to cat the contents of .htpasswd file.

![alt text](./assets/image-6.png)

3. Adding a few lines into https configuration file for example.com.

![alt text](./assets/image-7.png)

4. Restarting the apache server

5. When accessing to example.com, it’ll show a prompt to give username and password.

![alt text](./assets/image-8.png)

6. Now providing the username and password from before created.

![alt text](./assets/image-9.png)

7. Now, I can access the site.

![alt text](./assets/image-10.png)
![alt text](./assets/image-11.png)

<hr>

### 🔖 Tasks - 3 :

1. Installing and configuring Mariadb server on kali linux.

![alt text](./assets/image-12.png)
![alt text](./assets/image-13.png)

2. Creating a database called ‘apache’ and use the following command to use the apache database.

![alt text](./assets/image-14.png)
![alt text](./assets/image-15.png)

3. Creating a table called users

![alt text](./assets/image-16.png)

4. Instead of storing plain passwords in database, use the following command to create a hashed password for users named Sammy and Alice in a separate console.

![alt text](./assets/image-17.png)

5. Now store the hashed password

![alt text](./assets/image-18.png)

6. Enable the mod_authn_dbd module of Apache and modifying configuration file’s contents.

![alt text](./assets/image-19.png)

7. Restart the Apache server.
8. When accessing the example.com page, it’ll show a prompt for username/password. Providing the one that have in your MySQL database. Now you can access the page.

![alt text](./assets/image-20.png)