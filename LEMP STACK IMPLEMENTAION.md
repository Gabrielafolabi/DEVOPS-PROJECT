### LEMP STACK IMPLEMENTATION
LEMP STACK is another webstack just like LAMP.
L - Linux
E - Nginx
M - Mysql
P - PHP/Python

This is to show or explained how i implemented a lamp stack.
SO, to implement this stack we need the elements mentioned above. Note that an EC2 instance running on Ubuntu has been created already. 
You can refer to previous project (LAMP Implementation) on how i created EC2 instance.

Step 1:  I installed Nginx with the command below:
but before insstalling nginx, i updated my ubuntu 
* `sudo apt upgrade`,
then,
* `sudo apt install nginx -y`

after installing nginx,
Then, i checked if nginx is active and runnning by using the command below:
* `sudo sytemctl status nginx`

You would see it active, refer to screenshot below:

![image](https://github.com/Gabrielafolabi/DEVOPS-PROJECT/assets/35296784/dfac8e44-a458-4c3e-897b-641a2ee92497)


You can verify by using the curl command below on my ubuntu shell:

* `curl http://localhost:80`

or

* `curl http://52.203.53.164 `

Also, i very on my browser to check if i can access the server, by:
* `http://52.203.53.164:80`



![image](https://github.com/Gabrielafolabi/DEVOPS-PROJECT/assets/35296784/84225164-ac5f-4cde-bd3e-0e56dedcac66)


note that, by default web browser listens to port 80, if i didnt specify the port number, my server would still be accessed.

To check for the Server public Ip address, without going through aws console, I use the command below:

* `curl -s http://169.254.169.254/latest/meta-data/public-ipv4`

Step 2: Install Mysql

After installation of nginx, then i installed mysql with the command below:

* `sudo apt install mysql-server -y`

Then I can connect to the mysql database server as the admnistrative root. using the command below:
* `sudo mysql`
Note that, it is not advisable to connect to the database without security meaures.
So, I set security measure by using the command below in the database environment:

*`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`

I exited the database environment and then set a password depending on the level I want using the command below and then follow prompted instructions:

* `sudo mysql-secure-installation`

After setting the password, I can now login to the mysql database environment with password set.

* `sudo msql -p`

Walllaahh!... MYSQL Database is now properly installed. Then I moved to install PHP.


### Step 4: Installing PHP.
