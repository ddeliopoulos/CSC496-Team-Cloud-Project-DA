- Documentation describing the selected computing service, including network diagram and
specific details on what services being installed on which VM.

The selected computing service for our project is PaaS. Platform as a service (PaaS) is a cloud computing model 
allowing developers to build and deliver applications over the internet without bothering about the complexity 
of maintaining the infrastructure usually associated with developing and operating them. 

As a application server we chose Tomcat. Apache Tomcat is an open-source implementation of the Java Servlet, 
JavaServer Pages, Java Expression Language and WebSocket technologies. Tomcat provides a "pure Java" HTTP web server 
environment in which Java code can run.

As a Database we chose MySQL. MySQL is an open-source relational database management system (RDBMS). 
MySQL is free and open-source software under the terms of the GNU General Public License, and is also 
available under a variety of proprietary licenses.

The PaaS that we offer, provides standard library with application server Tomcat, and gives full control to 
a private database instance MySQL.

In our environment we do have application server Tomcat (version 9.0.31) and database server MySQL (server version 5.7.29).
Tomcat and MySQL are installed on Ubuntu 18.04.4 VM. Also setting up port forwarding will allow remote 
computers to connect to a specific computer or service, from one address and port number combination to another.

We will use ClodLab OpenStack to make instance of VM and specific Security groups.

All related documentation will be added in our GitHub repository.

![Diagramn](https://i.imgur.com/I2lcsvK.png)


