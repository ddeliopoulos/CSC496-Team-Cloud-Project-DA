# CSC496-Team Cloud Project-DA

Webserver/mySQL Form Fill Out

CSC 496-80 Course Project - Installation and Deployment of a webserver with backend mySQL server
 

Dimitra Deliopoulos
Desislava Atanasova


# Project Achieved
Accessible SQL form that can be filled out and submitted. The data is held in the backend SQL server that is already implemented. 
The form is accessible through the browser. The IP address is: http://128.105.146.179/ (the IP address may change due to floating IP issues involving CloudLab).


# Environment

To provide working environment for the project, on Ubuntu 18.04 VM, Apache server and MySQL (server version 5.7.29) were installed. 
On CloudLab, Openstack profile was created with a controller and two compute nodes. The network includes two routers, one is connected to the tun0-net , the other to to the flat-lan-l-net. The topology if the network connections is presented in Deliverable 3 - CSC 496-80 Course Project file.
"bionic-server-cloudimg-amd64" is used to create an image, the disk format is QCOW2. A few snapshots of the same image after installing the essential components to the server were created. One of this snapshots became our final project.
