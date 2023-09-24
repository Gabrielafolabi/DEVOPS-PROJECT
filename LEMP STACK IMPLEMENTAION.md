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


Installed PHP with the command:
* `sudo apt install php-fpm php-mysql`

Then i checked the version installed with the command:
* `php -v`

  ### Configuring Nginx to use PHP processor
I Create the root web directory for the domain ProjectLemp
* `sudo mkdir var/www/ProjectLEMP`

Then i changed the ownership of the directory from root user to  current system user, using the $USER environment variable.

* `sudo chown -R $USER: $USER /var/www/ProjectLEMP`

Then i created a configuration file in the nginix site-available directory. using the command below:

* `sudo mkdir etc/nginix/site-available/ProjectLEMP`
  
Then i create the server block with the configuration below:

`sudo vi /etc/nginx/sites-available/projectLEMP`

`server {
    listen 80;
    server_name projectLEMP www.projectLEMP;
    root /var/www/projectLEMP;`

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
     }

    location ~ /\.ht {
        deny all;
    }

`}`



Then after creating this, I link the PrjectLEMP directory i created inside the site-available with the site enabled.
Note that, linking it implies that the correction i make on my code in site available will automatically reflect on site-enabled...
I linked it with the command below:


* `$ sudo ln -s etc/nginx/site-available/ProjectLEMP etc/nginx/site-enabled`

Then I checked if my configuration is okay with the command below:
* `$ sudo nginx -t`

Then I disbaled the default nginix host that is already configure.:

* `$ sudo unlink /etc/nginx/sites-enabled/default`

Then reload the server for changes to take effect:

* `$ sudo systemctl reload nginx`
* 
  
