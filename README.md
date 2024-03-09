# Linux-assignment

LAMP and LEMP are two popular stacks used for web development. Here's the full meaning of each:

LAMP Stack:

L - Linux: The operating system.
A - Apache: The web server software.
M - MySQL or MariaDB: The database management system.
P - PHP, Perl, or Python: The programming language used for web development.
The LAMP stack is a traditional and widely used open-source web development stack.

LEMP Stack:

L - Linux: The operating system.
E - Nginx: The web server software, pronounced "engine-x".
M - MySQL or MariaDB: The database management system.
P - PHP, Perl, or Python: The programming language used for web development.
The LEMP stack is similar to the LAMP stack but replaces Apache with Nginx as the web server, known for its performance and scalability advantages in high-traffic environments.

Both stacks provide a platform for hosting dynamic websites and web applications, with slight differences in the web server software used.

Part 1: Setting Up LAMP Stack

1. Launch EC2 Instance:
   Go to the AWS Management Console and navigate to the EC2 dashboard.
   Click on "Launch Instance" and select an Ubuntu Server AMI.
   Choose an instance type, configure instance details, add storage, configure security group (allow SSH and HTTP), review and launch the instance.

2. Connect to Instance:
   Use SSH to connect to your EC2 instance. Replace your-instance-ip with your actual instance IP:
   chmod 400 "Linux pair.pem"
   ssh -i "Linux pair.pem" ubuntu@ec2-3-93-153-111.compute-1.amazonaws.com

3. Install Components: (Apache, MySQL, and PHP)
   sudo apt update
   sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql

4. Start Services: (Start Apache and MySQL services:)

sudo systemctl start apache2
sudo systemctl start mysql
sudo systemctl status apache2

5.  Test LAMP Stack:
    echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php

Part 2: Setting Up LEMP Stack on macOS

1. Use Homebrew to install Nginx, MySQL, and PHP:
   brew install nginx mysql php
2. Start Nginx and MySQL:
   sudo brew services start nginx
   mysql.server start
3. Configure Nginx for PHP: Edit the Nginx configuration file
   sudo nano /usr/local/etc/nginx/nginx.conf
4. Add the following line inside the http block to include PHP processing:
   include /usr/local/etc/nginx/fastcgi.conf;
5. Create a PHP info file in Nginx's document root directory:
   echo "<?php phpinfo(); ?>" | sudo tee /usr/local/var/www/info.php
6. Restart Nginx for the changes to take effect:
   sudo brew services restart nginx
