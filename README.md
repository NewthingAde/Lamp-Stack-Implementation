# Lamp-Stack-Implementation
This is a project which implement the use of Web Stack (LAMP STACK) In AWS

### Create a EC2 Instance 
- Select region (the cl and launch a new EC2 instance of t2.micro family with Ubuntu Server 20.04 LTS (HVM)
- Create a pair Key as the EC2 is created 
- Move into the folder where the pair key is downloaded and run the following command to connect to the instance
       
              sudo chmod 0400 <private-key-name>.pem
          
              ssh -i <private-key-name>.pem ubuntu@<Public-IP-address>

###  Install APACHE and Update the Firewall

- Firat is to update a list of packages in package manager, the following command is used

                     sudo apt update

- Then we run apache2 package installation using the following command
                
                     sudo apt install apache2
                
- To verify that apache2 is running as a Service in our OS, use following command
         
                    sudo systemctl status apache2
         
- we can try to check how we can access it locally in our Ubuntu shell, using the following command
        
                     curl http://localhost:80
        
                                   or
                    
                      curl http://127.0.0.1:80
             
- The image below will be display with the ip address

<img width="801" alt="Screenshot 2022-04-17 at 09 28 47" src="https://user-images.githubusercontent.com/80678596/163705182-cd4d5d38-6943-41dc-bfb1-2184847c3a54.png">

## Installing MYSQL

- USe the the comman line to install the server 

                     sudo apt install mysql-server
          
- We can the server using the following command line

                     sudo mysql_secure_installation
          
- You can sudo in the the server using the command

                            sudo mysql
          
- This will be display which shows that it is successful
          
- We can exit the server using the following command

                                   exit
          
## Installing PHP

- We use the following command to install 3 packages at once

                            sudo apt install php libapache2-mod-php php-mysql
          
- After the installation, we can run the check the php version with the following command

                                                 php -v

## Creating Virtual Host Using APACHE

- Create the directory for projectlamp using ‘mkdir’ using the command
        
                                   sudo mkdir /var/www/projectlamp

- Assign ownership of the directory with current system user using the command
       
                                  sudo chown -R $USER:$USER /var/www/projectlamp

- Create and open a new configuration file in Apache’s usinng the command line 
        
                                  sudo vi /etc/apache2/sites-available/projectlamp.conf

- paste the command below in the vim file and save 
        
                                        <VirtualHost *:80>
                                        ServerName projectlamp
                                        ServerAlias www.projectlamp 
                                        ServerAdmin webmaster@localhost
                                        DocumentRoot /var/www/projectlamp
                                        ErrorLog ${APACHE_LOG_DIR}/error.log
                                        CustomLog ${APACHE_LOG_DIR}/access.log combined
                                        </VirtualHost>

- You can list us the command line below tp list what is in the file
       
                                   sudo ls /etc/apache2/sites-available

- Enable new virtual host using the command 
      
                                          sudo a2ensite projectlamp

- You can disable Apache default website using the command
       
                                          sudo a2dissite 000-default

- Check for syntax error in the configuration file with the command
       
                                          sudo apache2ctl configtest

- Reload Apache for the changes to take effect 
      
                                          sudo systemctl reload apache2

- Create an index.html file in that location to test that the virtual host works as expected using the command
       
       sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s                           http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html

- The website URL can be access using thr IP address 
      
                                          http://<Public-IP-Address>:80

## Enable PHP on the website

- Edit the conf file with the command
        
                                   sudo vim /etc/apache2/mods-enabled/dir.conf

- Paste in the command
       
                             <IfModule mod_dir.c>
                             #Change this:
                             #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
                             #To this:
                             DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
                             </IfModule>

- Reload Apache 
       
                                   sudo systemctl reload apache2

- Create index.php file
       
                                   vim /var/www/projectlamp/index.php

- Add the following text, which is valid PHP code, inside the file:
      
                                               <?php
                                              phpinfo();

- Save and close the file, refresh the page and you will see a page similar to this:
       
<img width="774" alt="Screenshot 2022-04-18 at 23 55 58" src="https://user-images.githubusercontent.com/80678596/163884029-d2d9a787-8446-45c0-895a-b6ab658a6739.png">

- Its best to remove the file create, you can do that using the following command
      
                                   sudo rm /var/www/projectlamp/index.php
