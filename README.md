# UNDERSTANDNG CLIENT-SERVER ARCHITECTURE WITH MYSQL AS RDBMS
![image intro](img/intro.png)

open **propitixhomes.com** on the Linux console using the code 

`$ curl -Iv www.propitixhomes.com
`
![propitix curl](<img/1 curl propitix.png>)

in this instance, I will run two EC2 servers

![two server instance](<img/2 client and server on aws.png>)

named 

Server A name - `mysql server 1`

Server B name - `mysql client 1`

I installed MySQL Server software On MySQL server 1. using the code below to both update and install the MySQL server.

`sudo apt install mysql-server -y`

![install mysql server](<img/3 mysql-server install.png>)

I activated my MySQL server using the code below 

`sudo systemctl enable mysql`

![activated the server](<img/4 enable mysql service on server.png>)

next, I installed MySQL client software on my client server using the code below

`sudo apt install mysql-client -y`

![install my sqlclient software](<img/5 install mysql client.png>)

to know my private IP address of MySQL client server I used the code below

`ip addr show`

![discover ip address](<img/6 ipadress of client gotten.png>)

afterward, I added the IP address of the client on my inbound allowed source of traffic on the EC2 instance

![add ip address of the client](<img/7 ip address of client added.png>)

afterward, I created a database on the server

![database created on the server side ](<img/8 database created on server and all access granted.png>)

I changed the bind address on the MySQL-server to allow connection from any IP address, and I set the bind address to `0.0.0.0` using the commnd below

`sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf 
`

![change bind address](<img/9 change to 0 0 0 0.png>)

after which I restarted MySQL database

![mysql restart](<img/10 restart mysql.png>)

thereafter I connected to the server database through the client side using the code below

`sudo mysql -u remote_user -h 172.31.41.164 -p` 

![connect to server database using client server](<img/11 successfully conected to mysql database server from client.png>)

**172.31.41.164**  - is the database server's private IP address 

