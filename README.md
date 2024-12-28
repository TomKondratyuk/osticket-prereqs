<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> 

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- osTicket Installation files
- Heidi SQL

<h2>Installation Steps</h2>

<p> Hello, this is my tutorial on how to install osTicket on your Windows system. First you will be using a virutal machine(VM) through microsoft Azure. This will give you good practice using Azure, the 2nd most popular cloud provider, which is can be as valuable as formal job experience. As well as giving you experience connecting through Remote Desktop, which many Help Desk jobs use everyday to assist employees. And the cool thing is many Azure services offer free tiers or sandbox environments, so you can practice without significant costs.
  
1.) Create Azure Virutal Machine (VM) 
First Go to the Azure Portal and create and start up a Windows 10 Virtual Machine(VM) with at least 2-4 CPUs. 

![Capture1](https://github.com/user-attachments/assets/b35b9298-c613-4c88-a8bf-78286b253d09)

2.) Connect to your Virtual Machine (VM) via remote desktop
Next, connect to your Azure VM through Remote Desktop Connection, using your Azure VM's public IP address 
Copy and Paste your Azure VM public IP
![image](https://github.com/user-attachments/assets/01670286-454f-43ff-95fd-91265de6ec24)

![image](https://github.com/user-attachments/assets/1b8984e5-7c55-4d59-982b-b1241aeec99e)


3.) Install/ Enable IIS in WIndows **WITH CGI**

Through control panel open "Programs and Features" 
Click on "Turn Windows features on or off
Fill the Internet Information Services box

![Captu3re](https://github.com/user-attachments/assets/f53ee020-f30d-4262-b8db-0f082a1011d7)

![Capt4ure](https://github.com/user-attachments/assets/f0ec513a-da0f-45d7-915f-e4e57ce71964)

And extend the ----> Internet Information Services folder, ----> World Wide Web Servies, ----> Application Development Features ----> Check CGI 

![Capt5ure](https://github.com/user-attachments/assets/7cd4bfcd-1d64-479f-88fc-adceaf9a3b81)

Hit OK, and it should install the web server

3.) In your VM download the entire folder at this link ---> https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6


4.) Extract folder to your desktop and then open the "osTicket-Installion-Files" folder, install PHP Manager for IIS -> (PHPManagerForIIS_V1.5.0.msi)

![image](https://github.com/user-attachments/assets/1d5fc895-e8e5-4929-85c0-31e8b1b4884b)

![image](https://github.com/user-attachments/assets/858fda84-1f04-40f9-999b-98b9527c74c5)


5.) Also in the "osTicket-Installion-Files" folder, Install Rewrite Module. -> rewrite_amd64_en-US.msi

6.) Create A new folder on your Windows: (C) Drive. Named PHP

unzip and extract PHP 7.3.8 (php-7.3.8-nts-win32-VC15-x86.zip) into the "C \PHP" folder

7.) In "osTicket-Installion-Files" folder" -> Install VC_redist.x86

8.) In "osTicket-Installion-Files" folder" -> Install mysql-5.5.62-win32

In the setup wizard choose "typical" setup type 

At the end of the setup wizard -> Checkmark ✓ the box to "Launch the MySQL Instance Configuration Wizard".

Choose "Standard Configuration" 

![image](https://github.com/user-attachments/assets/9eb185e0-1e13-4ea2-b0ed-4bd7ee4729eb)

Hit next until you get to this screen

![image](https://github.com/user-attachments/assets/935264e8-86a5-4272-967f-dee226f1a5f7)

Make root password: "root" 
This is bad practice in an acutal real life senario. However this is just for practice so let's keep it simple to not forget.

Keep going through and hit "Exute" --> then "Finish" when configuration is completed. 

9.) Open ISS as Admin 

Hit start and search ISS, it should pop up. Hit run as Administrator 

Open PHP manager  

![image](https://github.com/user-attachments/assets/90531959-0992-4325-b398-7be2b38a1e1a)

Hit Register new PHP verison and hit the 3 dots 

![image](https://github.com/user-attachments/assets/ac1f958a-1bc4-4eb7-b74b-28199ffb9958)

Choose the executable file in the C:\PHP folder you created

![image](https://github.com/user-attachments/assets/14c7b589-a059-4a6f-a409-c7ff38c23c85)

Restart the ISS. In ISS manager -> open and start the server

![image](https://github.com/user-attachments/assets/6529981b-c3f7-48ef-9791-97b5cf9bc10a)

10.) Intstall osTicket v1.15.8

In the "osTicket-Installion-Files" folder. Extract "osTick v1.15.8.zip" 

Copy the "upload" folder from your extracted osTicket folder into your "c:\inetpub\wwwroot" folder

![image](https://github.com/user-attachments/assets/1856d6f3-bd9c-4009-8ccb-2729ba195733)

rename "upload" to -> "osTicket" Exactly like this. *case sensitive*

Once again stop and start ISS Server in ISS Manager 

11.) Go to sites -> Default -> osTicket
 Then On the right, click "Browse *:80*

![image](https://github.com/user-attachments/assets/1c1abb28-74f7-44cc-be03-875c78a76cfd)

If you did everything correctly you should see this page pop up. (This part of the lab must be working in order to continue with the rest)

![image](https://github.com/user-attachments/assets/f6a6ce50-b411-4813-a6d5-40fe7887bd32)


But, If you get this error, it probably means you didn't rename the "upload" to "osTicket" correctly. Check for spaces or improper capitalization 

![image](https://github.com/user-attachments/assets/8651d588-8ee8-4aef-89a6-f573060fc232)

Some of the extensions are not enabled so go back to PHP manager --> Sites --> default Web sites --> osticket 
Click PHP manager and at the bottom click enable or disable an extension 
enable the following--> php.imap, php.intl, php_opcache

![image](https://github.com/user-attachments/assets/7404727c-89f1-4df2-ac69-651f151b0898)


11.) Rename: ost-config.php
Go to C:\inetpub\wwwroot\osTicket\include
 ost-sampleconfig.php to the name --> ost-config.php  *important to name it exactly that*

12.) Assign Permissions: ost-config.php 
Right click --> properties --> security --> advanced 
Disable inheritance -> Remove All

![image](https://github.com/user-attachments/assets/4d6d7f0b-0c9b-4d88-b145-a1b8afef383a)

New Permissions -> Everyone -> All
(not good practice in real life to give everyone permission, just doing this for the lab practice)

![image](https://github.com/user-attachments/assets/37c980eb-6f44-4b98-abd2-ce072554cff0)

Checkmark the Full control box to give it -> Modify, read and excute, read, and write permissions. 
Make sure you hit apply. 

![image](https://github.com/user-attachments/assets/63ef6cf1-2ff0-48b1-811a-5d30028bdffc)

Now osTicket has full control to the configuration file. 

13.) Go back to your osTicket webiste. 

Hit continue and Fill out everything, except the SQL things. 

![image](https://github.com/user-attachments/assets/a2e7764f-d433-4587-b350-8b39da9e8205)

BEFORE we continue with Intall Now we must create a database for osTicket in order to plug in the Database settings. 

14.) Install HeidiSQL in your Installation folder- 

![image](https://github.com/user-attachments/assets/47791963-6e83-4422-9a99-035b81c539f9)

Checkmark the box to launch it after installation 
Hit New. 

![image](https://github.com/user-attachments/assets/91c7e82c-ea6f-4fe1-a7d3-7bc25ff6bb96)

set-
Username: root
Password: root

hit open- and this opens a connection to our database

right click unnamed and hit create new database 

![image](https://github.com/user-attachments/assets/13055b69-f2b6-4ec9-909f-03a50a25b1ed)



























"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
