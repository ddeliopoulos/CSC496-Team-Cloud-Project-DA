# Group 8 - Installation and Deployment of Webserver/mySQL Form Fill Out

Group members: Dimitra Deliopoulos, Desislava Atanasova

## Project Achieved
Accessible SQL form that can be filled out and submitted. The data is held in the backend SQL server that is already implemented. 
The form was accessible through the browser. The IP address was: http://128.105.146.179/ (The experiment expired on CloudLab, we weren't gotten back to for an extension, we had it for over a month working properly). On the technical report, there will be clear directions on establishing the proper OpenStack environment and below are the details on installing Apache2 and MySQL.

## Installing Apache2
This is installed under an instance created off of OpenStack hosted by Cloudlab using an ubuntu 18.04 server.

##### Update your local package index and install the apache2 package: 
 ```
 $ sudo apt update
 $ sudo apt install apache2
 ```
##### Check the available ufw application profiles and permit traffic on port 80:
 ```
 $ sudo ufw app list
 $ sudo ufw allow 'Apache'
 ```
##### Verify the change and check server status::
 ```
 $ sudo ufw status
 $ sudo systemctl status apache2
 ```
## Installing MySQL
This is installed under an instance created off of OpenStack hosted by Cloudlab using an ubuntu 18.04 server.

##### Update your package index, install the mysql-server package, and then run the included security script:
 $ sudo apt update
 $ sudo apt install mysql-server
 $ sudo mysql_secure_installation
 
#####  Adjusting User Authentication and Privileges:
 ```
 $ sudo mysql
 mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;
 mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
 mysql> FLUSH PRIVILEGES;
 mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;
 mysql> exit
 ```
  
##### Testing the server:
 ```
 $ systemctl status mysql.service
 ```
##### Create a database:
 ```
 $ sudo mysql
 mysql> create database formdb;
 mysql> use formdb;
 mysql> create table test(
    id int NOT NULL AUTO_INCREMENT,
    name varchar(255),
    email varchar(255),
    message text,
    PRIMARY KEY (id)
 ); ]
 ```
Test to see if works:
 ```
 mysql> describe test; 
 ```
# Download Files
Start by adding the HTML file in the html directory
 /var/www/html/"form.html"
 
Add the php file
 /var/www/html/"form_submit.php"
