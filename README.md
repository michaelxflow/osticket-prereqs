<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create an Virtual Machine with Microsoft Azure
- Downloading prerequisites for osTicket
- Navigating Internet Information Service Manager "IIS"
- Setting up HeidiSQL
- Installing an configuring set up for osTicket
- osTicket download and login

<h2>Installation Steps</h2>

<p>
Login to Microsoft Azure, then go to the home page and create a recourse group
<p>
<img src="https://github.com/user-attachments/assets/ddb61ea3-4e2c-4d96-8022-d19fbaba18d8" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Name your recource group "osticket-lab", select your "region" then precede to "create".
<img src="https://github.com/user-attachments/assets/c60484e6-eb1e-4544-8e72-fee7707e6288" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Next we can then create our virtual machine for this lab!
<p>
<p>
Under recource group for this VM, select "osticket-lab". Name the virtual Machine "osticket-vm" and make sure the region is the same as your recource group zone!
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/9f9f6046-7e88-4435-afe4-652725673edd" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
For your image select "Window 10 Pro, version 22H2-x64 Gen2" this is going to be your OS for the VM.
<p>
For the size i picked "Standard_E2_v3-2 vcpus,16GB memory" you can pick any that has at least 2 vcpus for this vm and 8GB or more for memory, this will make your VM run smoothly!
</p>
<br />
<p>
<img src="https://github.com/user-attachments/assets/d823d6e0-8bcc-48d2-b583-fa02de1b921d" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
As seen obove, make your username and password for the login to this vm. I used "labuser" and "osticketPassword1" as my password. You can make up your own, just make sure you dont forget it!
<p>
Make sure you check the box below for your licensing before you continue to create this vm!
</p>
<br />
Copy the Public IP Address of your vm! You will use this to connect to your vm in "Windows Remote Desktop Connection" in your search bar.
<p>
</p>
<img src="https://github.com/user-attachments/assets/5d5ed9bb-6852-4f5d-9a8b-5d8e6d6bdb14" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Paste the Public IP Address, yours will be different than mine! Then login using your username and password!
<p>
</p>
<br />
Within the VM (osticket-vm) ,download the osTicket-Installation-Files.zip from the osTicket website and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”
<p>
We will use the files in this folder to install osTicket and some of the dependencies.
<p>
</p>
<img src="https://github.com/user-attachments/assets/955eeb28-9b3e-45c0-82a7-7d7b62d3fc12" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<br />
Go into your contol panel of windows and Install / Enable IIS in Windows with CGI

World Wide Web Services -> Application Development Features -> [X] CGI
</p>
<img src="https://github.com/user-attachments/assets/39c47c93-e149-42d5-bd6b-c5f0e0ded3f1" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<br />
From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
<p>
</p>
<img src="https://github.com/user-attachments/assets/f0abdb9a-9135-477c-8c2a-b750b85e77cb" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi) Then we will create the directoy in the "C:\PHP" folder.
<p>
</p>
<img src="https://github.com/user-attachments/assets/aab203fe-75c2-4b2c-8529-253d1f99fdf5" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
<p>
</p>
<img src="https://github.com/user-attachments/assets/63eb6786-95ad-4496-bc63-d1006cd37d45" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.
<p>
</p>
From the “osTicket-Installation-Files” folder
<p>
Install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
<p>
Typical Setup -> Launch Configuration Wizard (after install)
<p>
Standard Configuration ->
<p>
Username: root

Password: root
<p>
Then hit next and execute, then Finish! This is now your Database.
<p>
</p>
<img src="https://github.com/user-attachments/assets/5887cda6-ab24-48c5-8f12-7eaa644763e2" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<br />
Open Internet Information Service Manager "IIS" as an Admin in the search bar
<p>
</p>
<img src="https://github.com/user-attachments/assets/34d4ec78-f36e-4854-96ae-94ca4f9e1eef" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)
<p>
</p>
<img src="https://github.com/user-attachments/assets/da9de326-fec9-4f49-adb4-199b6b4ff09b" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
Reload IIS (Open IIS, Stop and Start the server)
<p>
</p>
<br />
Install osTicket v1.15.8
<p>
From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
<p>
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”
<p>
</p>
<img src="https://github.com/user-attachments/assets/a1eb2b78-fce8-40ad-94dd-53c717db2322" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<br />
Reload IIS (Open IIS, Stop and Start the server)
<p>
Go to sites -> Default -> osTicket
<p>
On the right, click “Browse *:80”
<P>
</P>
<img src="https://github.com/user-attachments/assets/3119bdd4-08e0-4dc4-a1f7-9b42e6a6abe7" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<br />
Then browse to "osTicket" on the vm windows
<p>
</p>
<img src="https://github.com/user-attachments/assets/e10d8a93-0c2e-4dbe-8b94-5c2c1f29bf69" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
Note that some extensions are not enabled as you see above!
<p>
</p>
Go back to IIS

sites -> Default -> osTicket

Double-click PHP Manager
<p>
</p>
<img src="https://github.com/user-attachments/assets/c6900891-c68c-4c65-8be6-5483c7f37dbe" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
Click “Enable or disable an extension”

Enable: php_imap.dll

Enable: php_intl.dll

Enable: php_opcache.dll
<p>
</p>
<img src="https://github.com/user-attachments/assets/63808a45-e281-4c71-b198-b38765648155" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<br />
Refresh the osTicket site in your browser and observe the changes
<p>
</p>
Rename: ost-config.php
<p>
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php   To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
<p>
</p>
<img src="https://github.com/user-attachments/assets/dd5a23ab-76ed-4916-b9ae-4e8acf8b0ce5" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<br />
Assign Permissions: ost-config.php 
<p>
Disable inheritance -> Remove All, then New Permissions -> Everyone -> All
<p>
</p>
<img src="https://github.com/user-attachments/assets/a93340bd-4888-4dc6-b59a-90a2d7e4555e" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<br />
Continue Setting up osTicket in the browser click "Continue" Name Helpdesk. Default email "receives email from customers"
<p>
</p>
<img src="https://github.com/user-attachments/assets/3b0fd7d1-17f3-4eeb-80b2-a0a8a3d23df9" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
From the “osTicket-Installation-Files” folder, install HeidiSQL.
<p>
</p>
<img src="https://github.com/user-attachments/assets/4edb6693-e44b-430b-b621-970cac817ca0" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
Open Heidi SQL, Create a new session, root/root then Connect to the session
<p>
<img src="https://github.com/user-attachments/assets/789b0c35-b42c-4f9a-830d-4df336c73588" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Create a database called “osTicket”
<p>
Right click the unamed folder, click "create new" then Datatbase, Make the Database "osticket"
<p>
</p>
<img src="https://github.com/user-attachments/assets/633f0d93-9eec-40f1-9bbe-237971f47c0c" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
Go back to browser of OsTicket
<p>
</p>
Input Database settings , MySQL Table Prefix: ost_ 
<p>
Hostname: Localhost
MySQL Database: osTicket
MySQL Username: root
MySQL Password: root
Click “Install Now!”

<p>
<img src="https://github.com/user-attachments/assets/dabbd7e6-53b5-4ae7-a19c-79c20221be44" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
Browse to your help desk login page: http://localhost/osTicket/scp/login.php
<p>
</p>
<br />
Congradulations! You have installed OsTicket on Your Virtual Machine! Now lets create some tickets and solve them!








