<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- HeidiSQL
- osTicket

<h2>Operating Systems Used </h2>

- Windows 10</b> Standard D2als v6 (2 vcpus, 4 GiB memory)

<h2>Objectives</h2>

- Create Virtual Machine Using Asure
- Launch Virtual Machine using Remote Desktop (Mac/Windows)
- Download required files on Virtual Machine for osTicket
- Set up osTicket

<h2>Installation Steps</h2>


<p>
  <h3>Create a Virtual Machine (VM) Using Azure</h3><br/>
    
  In the Azure Portal, search for "Virtual Machines" in the search bar.
  ![image](https://github.com/user-attachments/assets/c43ca67e-46d1-4d7d-95fb-a77a2e5b444e)
  
  
  Click "Create" > "Azure Virtual Machine".
  
  ![image](https://github.com/user-attachments/assets/85c36039-bb99-49ad-baa7-c42397a032af)
  
  <h3>Configure Basic Settings for VM:</h3>
  
  <p>Subscription: Select your Azure subscription.</p>
  <p>Resource Group: Create or use an existing resource group.</p>
  <p>VM Name: Enter a name for the VM (e.g., osTicket-VM).</p>
  <p>Region: Choose a preferred region.</p>
  <p>Image: Select Windows 10 pro, version 22H2 - x64 Gen2 (this is the image used as of 03/2025).</p>
  <p>Size: Choose a VM size (at least 2 vCPUs, 4GB RAM for osTicket).</p>
  <p>Administrator Account: Select your own username and password (for this lab that will be <br />
    <br />
    User:  labuser <br />
    <br />
    Pass:  osTicketPassword1!)<br />
</p>
<p>Licensing: Make sure to check this box!</p>

![image](https://github.com/user-attachments/assets/68801898-4cab-4ff4-8a84-c4573492adec) , ![image](https://github.com/user-attachments/assets/d3495904-36f8-43a7-89b4-54e2f64da57b)


<p>Hit Review and Create, Allow Azure to complete VM creation. You will get a notification.</p>
</p>
<br />
_________



<p>
<h3>Launch Virtual Machine using Remote Desktop (Mac/Windows)</h3>
</p>
<p>
<h4>To set up Remote Desktop Protocol (RDP) on a Mac, follow these steps:</h4>

Download Microsoft Remote Desktop – Get it from the App Store.

Set Up the Connection on Mac – Open Microsoft Remote Desktop, click Add PC, enter the VM’s public IP address, and save.

Connect – Select the VM in the app, enter login credentials, and start the session.
<p><h6>image found on google</h6></p>

![image](https://github.com/user-attachments/assets/36eb4b88-dce7-4eff-a4dc-1177228b9a66)


<h4>For Windows:</h4>

Simply press your windows key and type in "Remote Desktop Connection".

Find your VM public IP Address and enter it into the RDC program to find your VM.

Use your windows Log in credentials to log in.

![image](https://github.com/user-attachments/assets/496b3397-3db3-43cf-be75-787c10d0ee61)


|

![image](https://github.com/user-attachments/assets/3bb3a6f8-535e-4c39-ac77-02b8d987576d)

|

![image](https://github.com/user-attachments/assets/2aecf5ad-958c-4e7a-afc3-8a37ee55ee3e)



</p>
<br />
_________
<p>
<h3>Download required files on Virtual Machine</p><h3>
</p>
<p><h5>for convenience I provide a folder where all required applications are kept together: https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD</h5></p>

![image](https://github.com/user-attachments/assets/c7dd686a-4036-4c8d-952f-d46cf00da2dd)

  
<p><h4>Install / Enable IIS in Windows WITH CGI
  World Wide Web Services -> Application Development Features -> [X] CGI</h4></p>
      <p>- In our VM go to control panel - programs</p>
      <p>- Under programs and Features select "Turn Windows Features on and off".</p>
      <p>- Find "Internet Information Services" and check that box</p>
      

![image](https://github.com/user-attachments/assets/b5606838-a32c-466c-9aec-47c158ed03f9)

<p>- For "CGI", under IIS, drop down "World Wide Web Services", then "Application Development Features" and check the CGI box and click OK</p>

![image](https://github.com/user-attachments/assets/dc40d5fb-79a5-4237-9b8b-0d4f649d09e4)

<h4>(From here on we can use the applications in our folder)</h4>

![image](https://github.com/user-attachments/assets/7149eb44-9083-4f4f-9e0d-29dbf0177309)

  <p>install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)</p>

<p>install the Rewrite Module (rewrite_amd64_en-US.msi)</p>

<p>Create the directory C:\PHP</p>

![image](https://github.com/user-attachments/assets/459518f4-3b08-4178-bfad-a2cb79063916)


<p> unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder</p>

<p> install VC_redist.x86.exe.</p>

<p> install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup -><br />
Launch Configuration Wizard (after install) -><br />
Standard Configuration -><br />
Username: root<br />
Password: root<br />
(User & Pass are the same for simplicity in this example, not recommended for real world application.)
</p>

<p>Open IIS as an Admin

![image](https://github.com/user-attachments/assets/c5e37e6d-af4b-4292-bb1d-f2d671e8df6d)


Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

![image](https://github.com/user-attachments/assets/7deac6e6-31be-4752-9e73-b4aa4a4bbc9d)



Reload IIS (Open IIS, Stop and Start the server)
</p>

<p>
  Install osTicket v1.15.8
From the “osTicket-Installation-Files” folder,
</p>
<p>
  unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”,
</p>
<p> 
  Rename “upload” to “osTicket”
</p>

![image](https://github.com/user-attachments/assets/cd501a0c-e16b-455a-9500-bd6d0bb6c2be)


<p>Reload IIS (Open IIS, Stop and Start the server)</p>

<p>Go to sites -> Default -> osTicket
On the right, click “Browse *:80”
</p>

![image](https://github.com/user-attachments/assets/882ed221-8249-46d6-80e3-0837454540a5)


<p>
  <p>Note that some extensions are not enabled</p>
<p>Go back to IIS, sites -> Default -> osTicket</p>
<p>Double-click PHP Manager</p>
<p>Click “Enable or disable an extension”</p>
<p>Enable: php_imap.dll</p>
<p>Enable: php_intl.dll</p>
<p>Enable: php_opcache.dll</p>
<p>Refresh the osTicket site in your browser, observe the changes</p>
</p>

![image](https://github.com/user-attachments/assets/416ce915-8ce7-4695-8e88-dd378cbd02f6)



<p>Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>

<p>Assign Permissions: ost-config.php</p>
<p>Disable inheritance -> Remove All</p>

![image](https://github.com/user-attachments/assets/02d43351-2d27-4c50-97a5-ade6ed26da93)


  
<p>New Permissions -> Everyone -> Check the "Full Control" box (not recommended to give everyone permissions in real use cases)</p>

![image](https://github.com/user-attachments/assets/faf0c31c-544c-49a5-996f-1a1555620fe6)



</p>

<p>Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)
</p>


![image](https://github.com/user-attachments/assets/63fd3c9b-bc12-4761-b7d2-a9fae441c311)


<p>
  <p>From the “osTicket-Installation-Files” folder, install HeidiSQL.</p>
  
  ![image](https://github.com/user-attachments/assets/ead45e41-b916-4576-aed1-7edb616ada66)

Open Heidi SQL
Create a new session, root/root
Connect to the session

![image](https://github.com/user-attachments/assets/6ac7709b-2790-4f69-900f-cde691d2fbe2)

Create a database called “osTicket”
</p>

![image](https://github.com/user-attachments/assets/ad9ff958-e694-42f6-8195-480a985968b5)
<p>
<p><h4>Continue Setting up osTicket in the browser</h4></p>
<p>cMySQL Database: osTicket</p>
<p>MySQL Username: root</p>
<p>MySQL Password: root</p>
<p>Click “Install Now!”</p>

![image](https://github.com/user-attachments/assets/7aaafd86-65e8-4eb8-8261-6d6f9e98f878)

<br />

<p>Once everything is installed continue to the next steps.</p>

![image](https://github.com/user-attachments/assets/89104b82-7a68-402d-8a62-e434883112a1)

<p>You can check back on HeidiSQL, refresh the database and observe changes.</p>

![image](https://github.com/user-attachments/assets/4b147a61-8b26-4af7-8933-265ba88305a5)

![image](https://github.com/user-attachments/assets/7ed57873-c9ae-4cd5-9c7e-65ab14b0fb53)

<p>Once all steps are completed, on your congratulations page you will see 4 links. We will be using "http://localhost/osTicket/" For users to submit Tickets and "http://localhost/osicket/scp/" to set up osTicket as an Administratior. </p>

![image](https://github.com/user-attachments/assets/12f8407c-2063-49cd-bf85-dab13e30327e)

<p><h3>Administrators</h3></p>

![image](https://github.com/user-attachments/assets/9a2f0939-20ee-4838-9136-886618fc90a2)


<p><h3>User</h3></p>

![image](https://github.com/user-attachments/assets/107233bb-cdee-42d1-abb9-448da3dc0714)

