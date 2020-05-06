# CSC496-Team Cloud Project-DA

Webserver/mySQL Form Fill Out

CSC 496-80 Course Project - Installation and Deployment of a webserver with backend mySQL server
 

Dimitra Deliopoulos
Desislava Atanasova


# Project Achieved
Accessible SQL form that can be filled out and submitted. The data is held in the backend SQL server that is already implemented. 
The form was accessible through the browser. The IP address was: http://128.105.146.179/ (The experiment expired on CloudLab, we weren't gotten back to for an extension, we had it for over a month working properly). On the technical report, there will be clear directions on establishing the proper OpenStack environment and below are the details on installing Apache2 and MySQL.

# Description
To provide working environment for the project, on Ubuntu 18.04 VM, Apache server and MySQL (server version 5.7.29) were installed. 
On CloudLab, Openstack profile was created with a controller and two compute nodes. The network includes two routers, one is connected to the tun0-net , the other to to the flat-lan-l-net. The topology if the network connections is presented in Deliverable 3 - CSC 496-80 Course Project file "bionic-server-cloudimg-amd64" is used to create an image, the disk format is QCOW2. A few snapshots of the same image after installing the essential components to the server were created. One of this snapshots became our final project.

# Installing Apache2
This is installed under an instance created off of OpenStack hosted by Cloudlab using an ubuntu 18.04 server.

Update your local package index: 
 $ sudo apt update
 
Install the apache2 package: 
 $ sudo apt install apache2
 
Check the available ufw application profiles:
 $ sudo ufw app list
  
Permit traffic on port 80 (normal, unencrypted web traffic):
 $ sudo ufw allow 'Apache'
 
Verify the change:
 $ sudo ufw status
 
Check server status:
 $ sudo systemctl status apache2
 

# Installing MySQL
This is installed under an instance created off of OpenStack hosted by Cloudlab using an ubuntu 18.04 server.

Update your package index, install the mysql-server package, and then run the included security script:
 $ sudo apt update
 $ sudo apt install mysql-server
 $ sudo mysql_secure_installation
 
Adjusting User Authentication and Privileges:
 $ sudo mysql
 mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;
 mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
 mysql> FLUSH PRIVILEGES;
 mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;
 mysql> exit
  
Testing the server:
 $ systemctl status mysql.service
 
Create a database:
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
Test to see if works:
 mysql> describe test; 
 
# Deployment
Start by adding the HTML file in the html directory
 /var/www/html/"form.html"
 
Add the php file
 /var/www/html/"form_submit.php"
 
 
 
