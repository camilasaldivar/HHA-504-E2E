HHA 504-E2E

# Steps 

##Set up and deploy EC2 using a PEM key


##Open ports 22 (SSH) and 3306 (MySQL)


##Connect to the EC2 instance using the terminal -ssh


#Change directory to downloads (This is where the PEM key is stored)

    Cd Downloads 
   
    ssh -i "Cam_AHI.pem" ubuntu@ec2-44-198-59-25.compute-1.amazonaws.com


#Run the following command after connecting to the machine: 
  
    Sudo apt-get update


#Create user (UBUNTU)
   
    sudo adduser 'USERNAME'
   
    sudo addpasswd 'PASSWORD'


#Edit the configuration 
    
    /etc/ssh/sshd_config	  
   
    Set Password Authentication and permit root login to yes 


#Re-start ssh 
    
    sudo service ssh restart

#Install MySQL 
   
    sudo apt install mysql-client mysql-server


#Update listings 
   
    sudo apt-get update 


#To check Status 
   
    sudo service mysql status
   
    If successful, running this command will display 'actively running'
 
#Change bin address to 0.0.0.0

    sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf

#Restart MySQL to make sure changes take place

    sudo service mysql restart
 
 
#Start MySQL
   
    Sudo MySQL


#Create a MySQL user 
    
    Create user 'DBA'@'%' IDENTIFIED BY 'PASSWORD';


#Grant all privileges to SQL user 
	
    	GRANT ALL PRIVILEGES ON *.* TO 'DBA'@% WITH GRANT OPTION;
	
    	Show grants;
	
	The 'show grants' command will show granted priviledges


#Create a database
   
    CREATE DATABASE e2e


#Write Python script to insert csv data 
    
    See Python Script Notebook attachment 


#Create a dump (.sql) file
   
    mysqldump -u DBA -p e2e > e2e_dump.sql
    
    sudo mysqldump-apt e2e>e2e_dump.sql
    
    ls
   
    if the dump file has been created the command ls will show it

#Launch a second ec2 instance using AWS or Azure
  
    Open Ports 22 and 3306
    
    Connect machine in the teminal 


#SCP to local Machine or another remote machine
   
    scp e2e_dump.sql client@52.170.46.178:/home/client
    
   On second instance, input the following command:
   
    sudo mysql e2e < e2e_dump.sql


#Create Trigger
    
    See sql file attachment 






