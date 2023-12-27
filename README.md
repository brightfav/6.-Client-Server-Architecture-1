# UNDERSTANDNG CLIENT-SERVER ARCHITECTURE WITH MYSQL AS RDBMS

Client-server architecture is a mode of connection between two or more machines or computers over a network to send and recieve request between each other.

The machine that sends the request is called the **Client** and the machine responding is called the **Server**

The image below gives a an illustration of a Client-Server Architecture

![image intro](img/intro.png)

to see a client-server operation i opened a website on my terminal using the command below

`$ curl -Iv www.propitixhomes.com
`
i can see the request is served by a webserver whose IP address is seen in the image below 

![propitix curl](<img/1 curl propitix.png>)

### Implementing a Client-Server Architecture using MySQL Database Management System

To do so i will create two EC2 instance and name them as follows 

Server A name - `mysql server 1`

Server B name - `mysql client 1`

![two server instance](<img/2 client and server on aws.png>)


Next I installed MySQL Server software On MySQL server 1 EC2 instance. using the code below.

`sudo apt install mysql-server -y`

![install mysql server](<img/3 mysql-server install.png>)

next I activated my MySQL server using the code below 

`sudo systemctl enable mysql`

![activated the server](<img/4 enable mysql service on server.png>)

next, on the second EC2 instance named **"mysql client 1"**  I installed MySQL client software using the code below

`sudo apt install mysql-client -y`

![install my sqlclient software](<img/5 install mysql client.png>)

next i will have to use the IP address of my EC2 client instance to grant it to my EC2 server.

To do so I used the code below

`ip addr show`

![discover ip address](<img/6 ipadress of client gotten.png>)

afterward, I added the IP address of the client EC2 nstance on my inbound allowed source of traffic on the EC2 server instance as shown in the image below

![add ip address of the client](<img/7 ip address of client added.png>)

Next, I created a database on the EC2 server instance as shown in the image below

![database created on the server side ](<img/8 database created on server and all access granted.png>)

next I changed the bind address on the EC2 server to allow connection from any IP address, and I set the bind address to `0.0.0.0` using the commnd below

`sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf 
`

![change bind address](<img/9 change to 0 0 0 0.png>)

after which I restarted MySQL database using the comand below

`sudo systemctl restart mysql`

![mysql restart](<img/10 restart mysql.png>)

thereafter I connected to the server database through the client side using the code below

`sudo mysql -u remote_user -h 172.31.41.164 -p` 

![connect to server database using client server](<img/11 successfully conected to mysql database server from client.png>)

**172.31.41.164**  - is the EC2 server instance private IP address 

