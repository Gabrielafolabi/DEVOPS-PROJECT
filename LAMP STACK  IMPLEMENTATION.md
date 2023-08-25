# LAMP STACK IMPLEMENTATION
A LAMP stack is a bundle of four different software technologies that developers use to build websites and web applications. LAMP is an acronym for the operating system, Linux; the web server, Apache; the database server, MySQL; and the programming language, PHP. All four of these technologies are open source, which means they are community maintained and freely available for anyone to use. Developers use LAMP stacks to create, host, and maintain web content. It is a popular solution that powers many of the websites you commonly use today. (Definition excerpt from AWS)

There are different stacks that makes it possible to build websits and web applications. These stacks of technologies are called WEB Stacks. Other WEB stacks are:
### 1. LAMP ( **Linux** **Apache** **MySQL** **PHP** )
### 2. LEMP ( **Linux** **Nginix** **MySQL** **PHP** )
### 3. MERN ( **MongoDB** **ExpressJS** **ReactJS** **NodeJS** )
### 4. MEAN ( **MongoDB** **ExpressJS** **AngularJS** **NodeJS** )

#### Note: On this article , I will be showing how to implement LAMP Stack using the following steps below.

Step 1: Get account registered on AWS. Select your prefered region and launch a new EC2 instance of t2.micro family with ubuntu server (The latest server version)

check this link to set up your AWS account [How to set up AWS account](https://www.youtube.com/watch?v=xxKuB9kJoYM&list=PLtPuNR8I4TvkwU7Zu0l0G_uwtSUXLckvh&index=6)

Also check here on [how to launch EC2 instance](https://www.youtube.com/watch?v=xxKuB9kJoYM&list=PLtPuNR8I4TvkwU7Zu0l0G_uwtSUXLckvh&index=7)
In the process of launching your EC2, please save your PEM file securely and do not share with anyone. You will not be able to connect to your server again, if you lose it.

PEM file , is a private key you downloaded from while provisioning the server. It is a PEM file format. 
We are going to use this key to connect to the EC2 instance via ssh.
You use a terminal tool, it can be WSL for windows, on macbook terminal is already installed by default... I will be using gitBash on windows, which i installed already.

Then on your terminal change directory to the directory where the PEM file is downloaded. usually in the download folder for me.

cd /Downloads

then,
ssh -i <private-key-name>.pem ubuntu@<Public-IP-address>





