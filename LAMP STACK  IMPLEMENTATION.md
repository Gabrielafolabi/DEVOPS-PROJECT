# LAMP STACK IMPLEMENTATION
A LAMP stack is a bundle of four different software technologies that developers use to build websites and web applications. LAMP is an acronym for the operating system, Linux; the web server, Apache; the database server, MySQL; and the programming language, PHP. All four of these technologies are open source, which means they are community maintained and freely available for anyone to use. Developers use LAMP stacks to create, host, and maintain web content. It is a popular solution that powers many of the websites you commonly use today. (Definition excerpt from AWS)

There are different stacks that makes it possible to build websits and web applications. These stacks of technologies are called WEB Stacks. Other WEB stacks are:
### 1. LAMP ( **Linux** **Apache** **MySQL** **PHP** )
### 2. LEMP ( **Linux** **Nginix** **MySQL** **PHP** )
### 3. MERN ( **MongoDB** **ExpressJS** **ReactJS** **NodeJS** )
### 4. MEAN ( **MongoDB** **ExpressJS** **AngularJS** **NodeJS** )

#### Note: On this article , I will be showing how to implement LAMP Stack using the following steps below.

### *Step 1* : 
Get account registered on AWS. Select your prefered region and launch a new EC2 instance of t2.micro family with ubuntu server (The latest server version)

check this link to set up your AWS account [How to set up AWS account](https://www.youtube.com/watch?v=xxKuB9kJoYM&list=PLtPuNR8I4TvkwU7Zu0l0G_uwtSUXLckvh&index=6)

Also che#k here on [how to launch EC2 instance](https://www.youtube.com/watch?v=xxKuB9kJoYM&list=PLtPuNR8I4TvkwU7Zu0l0G_uwtSUXLckvh&index=7)
In the process of launching your EC2, please save your PEM file securely and do not share with anyone. You will not be able to connect to your server again, if you lose it.

PEM file , is a private key you downloaded from while provisioning the server. It is a PEM file format. 
We are going to use this key to connect to the EC2 instance via ssh.
You use a terminal tool, it can be WSL for windows, on macbook terminal is already installed by default... I will be using gitBash on windows, which i installed already.

Then on your terminal change directory to the directory where the PEM file is downloaded. usually in the download folder for me.

* `*cd /Downloads*`

then,

* `ssh -i private-key-name.pem ubuntu@Public-IP-address`

Note: that the name you saved or given your private key, should replace "private-key-name" ...also the public address of your launched EC2 should replace "Public-IP-address"

There's a likelyhood of getting an error tagged "Bad permission"...then change permission for the private  key  file (.PEM)

* `sudo chmod 0400 <private-key-name>.pem`
  then, run the command again

* `ssh -i private-key-name.pem ubuntu@Public-IP-address`

Kudos, we have now successfully created linux server on cloud.


### *Step 3*: 
Installing Apache and Updating the Firewall. 
Apache is an open-source web server that forms the second layer of the LAMP stack. The Apache module stores website files and exchanges information with a browser using HTTP, an internet protocol for transferring website information in plain text. For example, when a browser requests a webpage, the Apache HTTP server does the following:
- Receives the request
- Processes the request and finds the required page file 
- Sends the relevant information back to the browser

Install Apache using ubuntu package manager "apt":

#update a list of packages in package manager

* `$ sudo apt update`

#run apache2 package installation

* `$ sudo apt install apache2`

So, to verify that apache2 is running as a service on the OS, run the command:

* `$ sudo systemctl status apache2`

  So, therefore, note that before we can receive any traffic on our server, we have to enable TCP port 80. This is done by adding another inbound rule.
  The TCP port 22 already existing is to enable SSH, this help us to connect to the Virtual server...

  Note that web browser by default listen to TCP port 80

  So, the commands below checks if you can access your web server

   
* `$ curl http://localhost:80`
or
* `$ curl http://127.0.0.1:80`

  The commands above do the same thing. Curl command is used to request the HTTP Apache server on pot 80, using the DNS name . The scond command does the same thing but uses the IP address. Also note that, if you dont specify the port number 80, you will still get the same result. This is because, web browser listen to port 80 by default.
  This is subject to change , depending on your configuration.


  ### Step 2: Installinng MySQL
  Alright, now that web server apache has been  installed, then we install a Database Management System (DBMS). This is to be able to store and manage data for your site in a relational database. The MySQL  is the relational DBMS used mostly  in PHP environment.

  To install mysql, use the command below:
  * `sudo apt install mysql-server`
 when prompted, confirm installation by typing y and then enter.

After installation, log in to mysql environment using the command below:

* `sudo mysql`
This will connect to the MySQL Server, as the administrative root user, which is inferred to as sudo.
you should see the output below:

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 8.0.22-0ubuntu0.20.04.3 (Ubuntu)

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective`
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.`

mysql>


You can start the interactive script by running:
* `$ sudo mysql_secure_installation`
This will ask you to configure the `VALIDATE PASSWORD PLUGIN`
you should always strong , unique password for database security.

When you are done, you can test your log in with the command below:

`$ sudo mysql -p`


### Step 4: Installing  PHP
Right now, we have Apache installed to serve your content and MySQL installed to store and manage your data. 
PHP is the component of our setup that will process code to display dynamic content to the end user.
The following commands below is used to install PHP package:

* `php-mysql`
  This is a php module that allows PHP to communicate with mysql based databases.

* `libapache2-mod-php`
  This command ebable apache to handle PHP files.

note that core PHP will automatically be installed as dependencies.

Alternatively, to install the three (3) packages at once, use the command below:

* `sudo apt install php libapache2-mod-php php-mysql`

To confirm the version of the PHP installed use the command:

* `php-v`

You will see the output below:

PHP 7.4.3 (cli) (built: Oct  6 2020 15:47:56) ( NTS )
Copyright (c) The PHP Group
Zend Engine v3.4.0, Copyright (c) Zend Technologies


### *At this point , your lamp stack is completely installled and in operation.*

## Enable PHP on the Website
Note that a file named index.html will usually take precedence over index.php in the directoryindex setting on apache. This can be change by edit the file 
etc/apache2/mods-eanbled/dir.conf , and then change the order in which the index.php file is listed.

command:
* `sudo vim /etc/apache2/mods-eanbled/dir.conf`

<IfModule mod_dir.c>
        #Change this:
        #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
        #To this:
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>

you need to save , close the file and then reload apache for the change to take effect.
command:
* `sudo systemctl reload apache2`

  * Createing a PHP script: This is to test that PHP is correctly installed and configured on my server.
  * Create a file index.php and then in the file , write a simple php program.
    command:
  * `sudo vim /var/www/projectlamp/index.php`
  * valid php code e.g
    `<? php
    phpinfo();`

### Creating a virtual Host for your Websits Using Apache.
* Set up a domain called projectlamp
* Create a dir
  `mkdir /var/www/projectlamp`
* Assign ownership to the directory
  `$ sudo chown -R $USER:$USER /var/www/projectlamp`
*Creat and open a new configuration file in apache's site-available directory.
`$ sudo vi /etc/apache2/sites-available/projectlamp.conf`

paste the below:

<VirtualHost *:80>
    ServerName projectlamp
    
    ServerAlias www.projectlamp 
    
    ServerAdmin webmaster@localhost
    
    DocumentRoot /var/www/projectlamp
    
    ErrorLog ${APACHE_LOG_DIR}/error.log
    
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

* to show the new files in the site-available directory, use the command:
  `$ sudo ls /etc/apache2/sites-available`
000-default.conf  default-ssl.conf  projectlamp.conf
* To enabel the new virtual host:
  `$ sudo a2ensite projectlamp`
* To dissable apche default website:
  `$ sudo a2dissite 000-default`
*To make sure configuration file doesnt have syntax error:
`$ sudo systemctl reload apache2`
* Then reload Apache for changes to take effect:
  `$ sudo systemctl reload apache2`

Congratulationss!!!...
Our new website is now active, but the web root /var/www/projectlamp is empty. Therfore, create an index.htmly file , with some content.
* `sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`

* Open the website URl on your browser using the ip Address or DNS name:
  `http://<Public-IP-Address>:80`
  OR
  `http://<Public-DNS-Name>:80`
  Note: You can leave this index.html page as a landing page for your application, until you create an index.php page.
  But remember to remove the index.html from the web root, after creating the index.php, because it will take prcedence over the index.php file by default. 











  





















