# WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad
## Introduction
LEMP stack is a popular choice for building web solutions, consisting of Linux, Nginx, MySQL, and PHP.
The LEMP software stack is a group of software that can be used to serve dynamic web pages and web applications written in PHP. This is an acronym that describes a Linux operating system, with an Nginx (pronounced like “Engine-X”) web server. The backend data is stored in the MySQL database and the dynamic processing is handled by PHP.

**This guide demonstrates how to install a LEMP stack on an Ubuntu 24.04 server using EC2**

## Step 0

1. EC2 Instance of t2.micro type and Ubuntu 24.04 LTS (HVM) was lunched in the US East (N. Virginia) region using the AWS console

![1](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/3446ebbf-8b49-4f24-b1f4-35a0ffa26889)
![5](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/98fc1e41-9c56-4cea-8210-0bbb63c4457a)

2. The security group was configured with the following inbound rules:

- Allow traffic on port 80 (HTTP) with source from anywhere on the internet.
- Allow traffic on port 443 (HTTPS) with source from anywhere on the internet.
- Allow traffic on port 22 (SSH) with source from any IP address. This is opened by default
  ![6](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/618a4aad-475d-4eee-a2e3-d836c2edb658)

3. Let's Connect our instance using SSH, then `cd` into the folder where the `private-key` was downloaded then ssh into it
   
![7](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/b8b59194-bc19-4f46-bee5-867fb99da5d0)
![8](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/9a494f67-d121-45c1-8822-e20e38a7d3fe)


## Step 1 - Install Nginx Web Server
1. Update and upgrade list of packages in package manager

![9](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/fef528e8-c489-409c-987f-b8c58ecc84b8)

2. Run Nginx
3. sudo apt install nginx
   
![10](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/d7dbd60d-04a7-4555-afd8-b88d1128e520)

sudo systemctl enable nginx

![11](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/b148c09e-56cf-4289-8b8d-68a184da831d)

4. The server is running and can be accessed locally in the ubuntu shell by running the command below:

curl http://localhost:80
OR
curl http://127.0.0.1:80

![12](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/5540d485-430e-492f-9b6d-923a14b0dbba)


5. Test with the public IP address if the Apache HTTP server can respond to request from the internet using the url on a browser.
   
http://3.91.243.130:80  
![13](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/a6af5278-c89f-40c9-92a7-1335f7b6ff80)


Another way to retrieve your Public IP address, other than to check it in AWS-Web
Console, with the help of following command

curl -s http://3.91.243.130/latest/meta-data/public-ipv4
![14](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/10511538-a84a-4942-84aa-d6976f0ff6a4)


## Step 2 - Install MySQL
1. Install a relational database (RDB)
    MySQL was installed in this project. It is a popular relational database management system used within PHP environments.

sudo apt install mysql-server
![15](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/b1b90d95-e21c-4541-a05e-12d42615f6cf)

2. Verify that mysql is running with the commands below.
   sudo systemctl status mysql
   &
   Log in to mysql console
 
 This connects to the MySQL server as the administrative database user root infered by the use of sudo when running the command.
   sudo mysql
![16](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/e5d1feb5-d86d-4644-87fe-4f37f37d2f9b)

 3 Set a password for root user using mysql_native_password as default authentication method.
    Here, the user's password was defined as "Pakistan@2"

![SQL-NEW-Passwords1](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/391ddc9b-fa72-485c-b71b-2c23c9286fae)
![SQL-NEW-Password2](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/ac3a66c8-d905-4a7a-bcb5-a161474d8d0d)

![18](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/334eff20-98bc-4802-bb40-b71253e289e5)

![19](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/199dddb2-dd86-4674-b397-12e091c247a6)

   Exit the MySQL shell

## Step 3 - Install PHP

Nginix installed to serve your content and MySQL installed to store and manage your data.Now on instaling PHP it will process code and will genrate dynamics content for the webserver.
While Apache embeds the PHP interpreterin each request Nginx requires an external program to handle PHP processing and act as a bridge between th PHP interpreter itself and the web server.
This allow for a better overall performance in most PHP-based websites, but it requires additional configuration.you will need to install php-fpm which stands for PHP fastCGI Program manager and tell Nginx to pass PHP reqests to this software for processing . Additionally you will neeed PHP -mysql,a PHP modeule that allows PHP to communicate with MySQL-based databases.Core PHP Packages will automatically be installed as dependencies.

sudo apt install php-fpm php-mysql

![20](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/ef751d93-f07a-4952-b314-d926d87f5e08)

Confirm the PHP version
php -v

![21](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/8edfe249-8e72-4c61-ba77-d644b446345f)

**At this ponit, the LEMP stack is completely installed and fully operational.**

To tset the set up with a PHP script, it's best to set up a proper Apache Virtual Host to hold the website files and folders. Virtual host allows to have multiple websites located on a single machine and it won't be noticed by the website users.

## Step 4 - Create a virtual host for the website using Apache

1. The default directory serving the apache default page is /var/www/html. Create your document directory next to the default one.
   Created the directory for projectlamp using `mkdir` command
   sudo mkdir /var/www/projectLEMP
   
   Assign the directory ownership with $USER environment variable which references the current system user.
   sudo chown -R $USER:$USER /var/www/projectLEMP
   
3. Create and open a new configuration file in nginx’s “sites-available” directory using nano.
   sudo nano /etc/nginx/sites-available/projectLEMP

   ![23](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/0c6098da-4c51-4908-815d-41b55618cc53)

   ![22](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/d1f983cf-79b0-463a-9422-328814eecdec)
  

  

4. You can test your configuration for syntax errors by typing:

sudo nginx -t

5. When you are ready, reload Nginx to apply the changes:
   sudo systemctl reload nginx


![24](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/e29a70c7-6384-4e04-9a40-664e475a55a3)
![26](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/03da9ddd-cf5a-4544-ab84-b8ba5846eb23)


Your new website is now active, but the web root /var/www/projectLEMP is still empty. Create an index.html file in that location so that we can test that your new server block works as expected:

sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html

![27](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/18c2cb6a-f28b-4950-a724-dc1ff1c31755)

6. Now go to your browser and access your server’s domain name or IP address, as listed within the server_name directive in your server block configuration file:

http://3.91.243.130

![28](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/e4f97655-1bf0-4d07-9dce-d6e732d62eaa)


After checking the relevant information about your PHP server through that page, it’s best to remove the file you created as it contains sensitive information about your PHP environment and your Ubuntu server. You can use rm to remove that file:

sudo rm /var/www/projectLEMP/info.php

![29](https://github.com/Zah00rAhmad/WEBSTACK-IMPLEMENTATION-LEMPSTACK-ZahoorAhmad/assets/111878350/3f45bed2-8228-46fc-a322-3e436f047875)






   

