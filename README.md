# Lamp-Stack-Implementation
This is a project which implement the use of Web Stack (LAMP STACK) In AWS

### Create a EC2 Instance 
- Select region (the cl and launch a new EC2 instance of t2.micro family with Ubuntu Server 20.04 LTS (HVM)
- Create a pair Key as the EC2 is created 
- Move into the folder where the pair key is downloaded and run the following command to connect to the instance
        - `sudo chmod 0400 <private-key-name>.pem`
          
       - `ssh -i <private-key-name>.pem ubuntu@<Public-IP-address>`

###  Install APACHE and Update the Firewall
- Firat is to update a list of packages in package manager, the following command is used
                `sudo apt update`

- Then we run apache2 package installation using the following command
                `sudo apt install apache2
                
- To verify that apache2 is running as a Service in our OS, use following command
          - `sudo systemctl status apache2`
- we can try to check how we can access it locally in our Ubuntu shell, using the following command
-         ` curl http://localhost:80`
                    or
             `curl http://127.0.0.1:80`
- The image below will be display with the ip address
<img width="801" alt="Screenshot 2022-04-17 at 09 28 47" src="https://user-images.githubusercontent.com/80678596/163705182-cd4d5d38-6943-41dc-bfb1-2184847c3a54.png">

## Installing MYSQL
- USe the the comman line to install the server 
          `sudo apt install mysql-server`
- We can the server using the following command line
          - `sudo mysql_secure_installation`
- You can sudo in the the server using the command
          - `sudo mysql`
          - This will be display which shows that it is successful
          - <img width="559" alt="Screenshot 2022-04-17 at 09 52 35" src="https://user-images.githubusercontent.com/80678596/163705771-3ce79a3d-275d-440d-83f8-676a7bf58109.png">
- We can exit the server using the following command
          `mysql> exit`
## Installing PHP
- We use the following command to install 3 packages at once
          - `sudo apt install php libapache2-mod-php php-mysql`
- After the installation, we can run the check the php version with the following command
          - `php -v`
