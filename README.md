<p align="center"> 
<img src="https://i.imgur.com/Clzj7Xs.png"/> 
</p> 

<h1>OS Ticket - Prerequisites and Installation</h1 > 
This tutorial outlines the prerequisites and installation of OS Ticketing System .<br /> 




<h2>Environments and Technologies Used</h2> 

- Microsoft Azure (Virtual Machines/Computer) 


<h2>Operating Systems Used </h2> 

- Windows 10 </b> (21H2) 

<h2>OS Ticket Installation Files</h2> 

- https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6


<h2>Installation Steps</h2> 
- Create an Azure Virtual Machine Windows 10, 4 vCPUs
Name: Vm-osticket
Username: labuser (for example/whatever you chose)
Password: osTicketPassword1! (for example/whatever you chose)

![image](https://github.com/techwithterrence/osticket-prereqs/assets/174138674/4fe1e250-e47a-40aa-84c4-c38b62b5e073)
![image](https://github.com/techwithterrence/osticket-prereqs/assets/174138674/68af1d14-b06a-495c-8bdf-a14947f75853)




Open this: Installation Files
We will use these files to install osTicket and some of the dependencies. I’m using this offline version to make sure everyone is using the same version of all the files :)

- Install / Enable IIS in Windows WITH
CGI and Common HTTP Features
World Wide Web Services -> Application Development Features ->
[X] CGI
[X] Common HTTP Features
AND IIS Management Console
Internet Information Services -> Web Management Tools -> IIS Management Console
	[X] IIS Management Console

![image](https://github.com/techwithterrence/osticket-prereqs/assets/174138674/11ab993b-3c9c-45e4-9ed7-8844004c5928)

![image](https://github.com/techwithterrence/osticket-prereqs/assets/174138674/c1b51550-e4db-4c57-ab77-2ddc7edddf57)


- From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

- From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)

- Create the directory C:\PHP

- From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP
!! ATTENTION !!
If this appears, choose to “Keep” the file:




If you are still having trouble downloading PHP 7.3.8, please try downloading and installing Google Chrome and doing it from within there. 

![image](https://github.com/techwithterrence/osticket-prereqs/assets/174138674/32e63438-d1ef-4fae-b6c1-1baf87a801cf)


From the Installation Files, download and install VC_redist.x86.exe.

- From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
- Launch Configuration Wizard (after install) ->
- Standard Configuration ->
- Password1

- Open IIS as an Admin

- Register PHP from within IIS

Reload IIS (Open IIS, Stop and Start the server)

- Install osTicket v1.15.8
- Download osTicket from the Installation Files Folder
Extract and copy “upload” folder to c:\inetpub\wwwroot
Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

Reload IIS (Open IIS, Stop and Start the server)

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browse, observe the changes

Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)

From the Installation Files, download and install HeidiSQL.
Open Heidi SQL
Create a new session, root/Password1
Connect to the session
Create a database called “osTicket”

- Continue Setting up osticket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: Password1
Click “Install Now!”

Congratulations, hopefully it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

End Users osTicket URL:
http://localhost/osTicket/ 

Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Notes:
Browse to your help desk login page: http://localhost/osTicket/scp/login.php  
End Users osTicket URL: http://localhost/osTicket/ 
