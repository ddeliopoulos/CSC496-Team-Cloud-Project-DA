# Installation and Deployment of Webserver/MySQL Form Fill Out Using OpenStack/CloudLab

Group-8_Members: Dimitra Deliopoulos, Desislava Atanasova

## Project Description
Accessible SQL form that can be filled out and submitted. The data is held in the backend SQL server that is already implemented. 
The form was accessible through the browser. The IP address was: http://128.105.146.179/ (The experiment expired on CloudLab, we weren't gotten back to for an extension, we had it for over a month working properly). On the technical report, there will be clear directions on establishing the proper OpenStack environment and below are the details on installing Apache2 and MySQL.

## Establishing Openstack Environment
To acheive the same OpenStack environment as the project, a Technical Report has been added to the CSC496-Team-Cloud-Project-DA directory that shows in great detail the process done through OpenStaack and CloudLab, including all the network aspects of this project so it could successfully deploy through a working non-local ip. Please reference

Link to Technical Report: [Technical Report](https://github.com/dimitra216/CSC496-Team-Cloud-Project-DA/blob/master/Deliverable%203%20-%20CSC%20496-80%20Technical%20Report%20%E2%80%93%20Installation%20and%20Deployment.pdf)

## Installing Apache2
This is installed under an instance created off of OpenStack hosted by Cloudlab using an ubuntu 18.04 server(information in Technical Report).

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
This is installed under an instance created off of OpenStack hosted by Cloudlab using an ubuntu 18.04 server(information in Technical Report).

##### Update the package index, install the mysql-server package, and then run the included security script:
 ```
 $ sudo apt update
 $ sudo apt install mysql-server
 $ sudo mysql_secure_installation
 ```
##### Adjusting user authentication/privileges and testing the server:
 ```
 $ sudo mysql
 mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;
 mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
 mysql> FLUSH PRIVILEGES;
 mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;
 mysql> exit
 $ systemctl status mysql.service
 ```
##### Create a database and test to see if it works:
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
 );
 mysql> describe test; 
 ```
# Downloadable Files
Add the HTML and PHP files into the html directory

 /var/www/html/"form.html"
 
 /var/www/html/"form_submit.php"
