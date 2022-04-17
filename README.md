# Lamp-Stack-Implementation
This is a project which implement the use of Web Stack (LAMP STACK) In AWS

### Create a EC2 Instance 
- Select region (the cl and launch a new EC2 instance of t2.micro family with Ubuntu Server 20.04 LTS (HVM)
- Create a pair Key as the EC2 is created 
- Move into the folder where the pair key is downloaded and run the following command to connect to the instance
          `sudo chmod 0400 <private-key-name>.pem`
          `ssh -i <private-key-name>.pem ubuntu@<Public-IP-address>`

###  Install APACHE and Update the Firewall
- Firat is to update a list of packages in package manager, the following command is used
                `sudo apt update`

- Then we run apache2 package installation using the following command
                `sudo apt install apache2
                
- The image below will be display with the ip address
<img width="801" alt="Screenshot 2022-04-17 at 09 28 47" src="https://user-images.githubusercontent.com/80678596/163705182-cd4d5d38-6943-41dc-bfb1-2184847c3a54.png">
