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


### *Step 2*: 
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

  





















