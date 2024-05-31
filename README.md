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




   

