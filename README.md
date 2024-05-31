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

