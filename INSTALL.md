# **Installation guide**

  *This guide is meant to be done in Windows instead of Linux, therefore before completing
  any steps install gitbash so that Linux commands will be recognized in Windows*
  
## VPS Installation guide with OVHCloud
  1. Create an account on OVHCloud
  2. Login to your account
  3. Go to the Bare Metal Cloud tab and then navigate to virtual-private server
  4. You will see the different specs about your vps like the IP address
  5. The status should be running, and the distribution will be Debian 11

## Connecting to the server
  - Windows Putty
       1. Search on a browser Putty
       2. Follows instructions for instllation and then open application
       3. Type in the IP address from OVHCloud in the HostName __(or IP Address text box)__ and click open
       4. Once it opens there will be a screen saying type in Usename and password 
          __(this will be the default password and usename given by OVHCloud)__
       5. Change the root password by running the command __(sudo passwd root)__ and enter the new password
  
## Creation of Users
  1. Once your in the server you will want to create a user for yourself
  2. To create a user you will run the command __(sudo adduser "whichever user name you want")__, it will ask
     you to create password for the user.
  3. Once the user is created you will add that user to the sudo group by
     running the command in root __(usermod -aG sudo "name for user")__
  4. Check if the user is in the sudo group by running the command __(groups "name for user")__
  5. If you want to create more users repeat steps 1-5, and to switch from user to user run
     the command __(su "name of user")__
           
## Update and Upgrade
  1. Login ass root
  2. Run the command __(apt-get update)__ to update the system
  3. Run the command __(apt-get upgrade)__ to upgrade the system
  
## Creation of SSH Keys on Windows
  1. Search on a browser for PuttyGen and download the application
  2. Once your in the application click generate and move mouse around to create the key
  3. Copy the public key text
  4. Now log into your OVHCLoud account and on the dashboard tab go to service managment, it i will
     bring you to the My Services page
  5. Go on the SSH tab and then click the add an ssh key button and select dedicated
  6. For ID enter the username that you created and for the key paste the text from step 3
  7. Click confirm
  
## Disable root Access
  1. While your logged in as root run the command __(nano /etc/ssh/sshd_config)__
  2. Then find the line PermitRootLogin yes, and change it to no
  3. Save your changes by clicking ^X and typing in yes when asked to save
  4. Then run the command __(systemctl restart sshd)__
  
## Installing a intrusion prvention software (IPS)
   1. Run the command __(apt-get install fail2ban)__ this will install the software
  
## Creating a firewall
  1. In your OVHCloud account go to bare metal cloud and navigate to the IP button
  2. In the All services section, find your ip address and click the three dots
  3. Click the create a firewall button, then the enable firewall button
  4. Once its create click the three buttons again and click the configure firewall button
  5. Select add a rule and add the following rules
       ![image](https://user-images.githubusercontent.com/82057989/166299099-8244071c-4072-4485-91b2-258915c066eb.png)

## Adding a Web Server
  *We chose to use Nginx as our Web Server*
  1. Run the command __(apt install nginx)__
  2. To check if it worked go on a browser and type in http:// your IP address
  
  
