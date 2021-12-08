HHA 504-E2E

#Steps 

#Set up and deploy EC2 using a PEM key


#Open ports 22 (SSH) and 3306 (MySQL)


#Connect to the EC2 instance using the terminal -ssh


#Change directory to downloads (This is where the PEM key is stored)

    ###Cd Downloads 
   
    ###ssh -i "Cam_AHI.pem" ubuntu@ec2-44-198-59-25.compute-1.amazonaws.com


#Run the following command after connecting to the machine: 
  
    ###Sudo apt-get update


#Create user (UBUNTU)
   
    ###sudo adduser 'USERNAME'
   
    ###sudo addpasswd 'PASSWORD'


#Edit the configuration 
    
    ###/etc/ssh/sshd_config	  
   
    ### Set Password Authentication and permit root login to yes 


#Re-start ssh 
    
    ###sudo service ssh restart

#Install MySQL 
   
    ###sudo apt install mysql-client mysql-server


#Update listings 
   
    ###sudo apt-get update 


#To check Status 
   
    ###sudo service mysql status
   
    ###will display 'actively running)
 

 #Start MySQL
   
    ###Sudo MySQL


#Create a MySQL user 
    
    ###Create user 'DBA'@'%' IDENTIFIED BY 'PASSWORD';


#Grant all privileges to SQL user 
	
    	GRANT ALL PRIVILEGES ON *.* TO 'DBA'@% WITH GRANT OPTION;
	
    	Show grants 


#Create a database
   
    ###CREATE DATABASE e2e


#Write Python script to insert csv data 
    
    ###See Python Script Notebook attachment 


#Create a dump (.sql) file
   
    ###mysqldump -u DBA -p e2e > e2e_dump.sql


#SCP to local Machine 


#Create Trigger
    
    ###See sql file attachment 


#Create a hot replica 



