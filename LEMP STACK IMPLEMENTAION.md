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

$ `sudo vi /etc/nginx/sites-available/projectLEMP`
The command above opened an empty file, then paste the below config.

  server {
    listen 80;
    server_name projectLEMP www.projectLEMP;
    root /var/www/projectLEMP;

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

}



Then after creating this, I linked the PrjectLEMP directory i created inside the site-available with the site enabled.
Note that, linking it implies that the correction i make on my code in site available will automatically reflect on site-enabled, going forward...
I linked it with the command below:


* `$ sudo ln -s etc/nginx/site-available/ProjectLEMP etc/nginx/site-enabled`

Then I checked if my configuration is okay with the command below:
* `$ sudo nginx -t`

Then I disbaled the default nginix host that is already configure.:

* `$ sudo unlink /etc/nginx/sites-enabled/default`

Then reload the server for changes to take effect:

* `$ sudo systemctl reload nginx`


Now , My ProjectLEMP directory is empty in my web root directory var/www/ProjectLEMP.

Then, i created an index.html in this directory and writing using echo.


* `$ sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html`

  Then, checked if the index.html can be access via my browser...:
*  `http://54.80.255.231:80`

 Note: remember to remove or rename the file, if you have index.php. Meanwhile Index.html will take precedence. 


#### Testing PHP with Nginx

From the web root directory, i added a php file.

* `$ sudo var/www/PrejectLEMP/index.php`

  Then i opened it to paste the php code:
* `vi var/www/ProjectLEMP/index.php`

  see the php code:
  <?php
phpinfo();


Then you can access the page on your browser with the command below:

* `[http://54.80.255.231:80/info.php`

  Then you will see the page below:

  ![image](https://github.com/Gabrielafolabi/DEVOPS-PROJECT/assets/35296784/71d75bc8-f717-45a4-bc41-959b261a53e2)



  to remove the file, you can use:

*  `$ sudo rm /var/www/your_domain/info.php`


### Retrieving Data From Mysql Database with PHP

I will first of all create a database , and a user to access the database, and then create some datas stored in the database created. After which the datas will br retrieved with PHP from the database.

step 1: creating database with name example_database

* `mysql> sudo CREATE DATABASE example_datase;`

step 2: I created a user with a password:
* `mysql>  CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`

step 3: Give the user permission to the database created

* `mysql> GRANT ALL ON example_database.* TO 'example_user'@'%';`

then exit; `mysql> exit`

Then try to login to with the new user login:
* `mysql> sudo -u example_database -p`

then show the database:
* `mysql> SHOW DATABASES;`


  Output
+--------------------+
| Database           |
+--------------------+
| example_database   |
| information_schema |
+--------------------+
2 rows in set (0.000 sec)



Then i created a todo list sitting on the example_database:

* `CREATE TABLE example_database.todo_list (item_id INT AUTO_INCREMENT,content VARCHAR(255),PRIMARY KEY(item_id));`

Then insert a few rows into the table created.

* `mysql> INSERT INTO example_database.todo_list (content) VALUES ("My first important item");`
* `mysql> INSERT INTO example_database.todo_list (content) VALUES ("My second important item");`
* `mysql> INSERT INTO example_database.todo_list (content) VALUES ("My third important item");`
* `mysql> INSERT INTO example_database.todo_list (content) VALUES ("and this one more thing");`

Then check the datas if stored.
* `mysql>  SELECT * FROM example_database.todo_list;`

You will see below:
Output
+---------+--------------------------+
| item_id | content                  |
+---------+--------------------------+
|       1 | My first important item  |
|       2 | My second important item |
|       3 | My third important item  |
|       4 | and this one more thing  |
+---------+--------------------------+
4 rows in set (0.000 sec)

Then exit from mysql console
* `mysql> exit`

step 4: Create a PHP script to fetch the data from Mysql database and displayed.

first create the php file from the web root directory.
* `$ nano /var/www/projectLEMP/todo_list.php`

  then use the code below:

  <?php
$user = "example_user";
$password = "PassWord.1";
$database = "example_database";
$table = "todo_list";

try {
  $db = new PDO("mysql:host=localhost;dbname=$database", $user, $password);
  echo "<h2>TODO</h2><ol>";
  foreach($db->query("SELECT content FROM $table") as $row) {
    echo "<li>" . $row['content'] . "</li>";
  }
  echo "</ol>";
} catch (PDOException $e) {
    print "Error!: " . $e->getMessage() . "<br/>";
    die();
}



Thereafter, save and close the file...and then access this from your browser with the URL
* `http://54.80.255.231/todo_list.php`

  You will see this below:


![image](https://github.com/Gabrielafolabi/DEVOPS-PROJECT/assets/35296784/0ddd9fd8-1b8d-4885-950b-082e3db9aaaf)

  











