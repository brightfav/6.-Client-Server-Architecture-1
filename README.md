<<<<<<< HEAD
# 6.-Client-Server-Architecture
=======
# UNDERSTANDNG CLIENT SERVER ARCHITECTURE WITH MYSQL AS RDBMS
![image intro](intro.png)

open **propitixhomes.com** on the linux console usng the code 

`$ curl -Iv www.propitixhomes.com
`
![propitix curl](<1 curl propitix.png>)

in this instance i will run two EC2 servers

![two server instance](<2 client and server on aws.png>)

named 

Server A name - `mysql server 1`

Server B name - `mysql client 1`

I installed MySQL Server software On mysql server 1. using the code below to both update and install the mysql server.

`sudo apt install mysql-server -y`

![install mysql server](<3 mysql-server install.png>)

i activated my mysql server using the code below 

`sudo systemctl enable mysql`

![activated the server](<4 enable mysql service on server.png>)

next i installed mysql client software on my client server using the code below

`sudo apt install mysql-client -y`

![install my sqlclient software](<5 install mysql client.png>)

to know my private ipadress of mysql client server i used the code below

`ip addr show`

![discover ip address](<6 ipadress of client gotten.png>)

afterward i added the ip address of the client server on my inbound allowed source of traffic on the EC2 instance

![add ip address of the client](<7 ip address of client added.png>)

afterward i created a database on the server

![database created on the server side ](<8 database created on server and all access granted.png>)

i changed the bind address on mysql-server to allow connection from any IP address, and i set the bind-address to `0.0.0.0` using the commnd below

`sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf 
`

![change bind address](<9 change to 0 0 0 0.png>)

afterwhich i restarted mysql database

![mysql restart](<10 restart mysql.png>)

thereafter i connected to the server database through the client side using the code below

`sudo mysql -u remote_user -h 172.31.41.164 -p` 

![connect to server database using client server](<11 successfully conected to mysql database server from client.png>)

**172.31.41.164**  - is the database server private IP address 

