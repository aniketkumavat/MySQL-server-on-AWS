# MySQL-server-on-AWS
How to run Mysql Server on AWS EC2 Instance

STEPS:

Step 1: Launch an EC2 Instance

1.Log into the AWS Management Console:
					Go to AWS Management Console.Navigate to the EC2 Dashboard:

2.In the console, Go to EC2 Instance then launch new instance.

3.COnfigure all instance details for more information instance 

4. Configure Security Group:
	    Add the following rules:
  		SSH(Port 22)
  		http/https(Port 80/443)
  		mysql/aurora (Port 3306 - allow MYSQL traffic)
		
		
6. Launch Instance wait for running state.

Step 2: Connect to your EC2 instance
	1.Connect Using SSH:
		Connect to your instance using its Public DNS:
			
   	- ssh -i "key-pair.pem" ubuntu@ec2-public-ip.availability-zone.compute.amazonaws.com
		
		
Step 3: Install MySQL Server
    1] Update the Packages
    
    	- sudo apt update -y
2] Install MySql  	
 	
    	- sudo apt install mysql-server -y

3] Secure MySQL Installation 
 		
   	- sudo mysql_secure_installation		  
- Follow the prompts to perform tasks like setting the root password, removing anonymous users, and disabling remote root login.

Step 4: Check the Status of MySql (Active or Inactive)

	 - sudo systemctl status mysql

Step 5: Login to MySql as a root

		- sudo mysql
		
Step 5: Update the password for the MySql Server

		- ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'place-your-password-here';
		
	        - FLUSH PRIVILEGES;

Step 6: Test the MySql server if it is working by running sample sql queries

	- CREATE DATABASE mysql_test;

	- USE mysql_test;

	- CREATE TABLE table1 (id INT, name VARCHAR(45));

	- INSERT INTO table1 VALUES(1, 'Virat'), (2, 'Sachin'), (3, 'Dhoni'), (4, 'ABD');

	- SELECT * FROM table1;
