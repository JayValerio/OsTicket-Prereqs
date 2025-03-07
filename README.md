<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- osTicket

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>What We Will Do</h2>

- Create Virtual Machine Using Asure
- Launch Virtual Machine using Remote Desktop (Mac/Windows)
- Download required files on Virtual Machine
- osTicket initial set up

<h2>Installation Steps</h2>

<p>
<h3>Create a Virtual Machine (VM) Using Azure</h3><br/>
  
In the Azure Portal, search for "Virtual Machines" in the search bar.

Click "Create" > "Azure Virtual Machine".

<h3><blockquote>Configure Basic Settings:</blockquote></h3>

<p>Subscription: Select your Azure subscription.</p>
<p>Resource Group: Create or use an existing resource group.</p>
<p>VM Name: Enter a name for the VM (e.g., osTicket-VM).</p>
<p>Region: Choose a preferred region.</p>
<p>Image: Select Ubuntu Server 20.04 LTS (or Windows if preferred).</p>
<p>Size: Choose a VM size (at least 2 vCPUs, 4GB RAM for osTicket).</p>

Administrator Account:

Select SSH public key or password authentication.
If using SSH, generate or use an existing SSH key.
Networking:

Under Public inbound ports, select Allow HTTP, HTTPS, and SSH (22).
Configure additional network settings if required.
Review & Create:

Click "Review + Create", ensure all configurations are correct, and click "Create".
Wait for deployment to complete.
</p>
<br />
_________



<p>
<h3>Launch Virtual Machine using Remote Desktop (Mac/Windows)</h3>
</p>
<p>
<h4>To set up Remote Desktop Protocol (RDP) on a Mac, follow these steps:</h4>

Download Microsoft Remote Desktop – Get it from the Mac App Store.

Set Up the Connection on Mac – Open Microsoft Remote Desktop, click Add PC, enter the PC’s IP address, and save.

Connect – Select the PC in the app, enter Windows login credentials, and start the session.


<h4>For Windows:</h4>

Simply press your windows key and type in "Remote Desktop Connection".

Find your VM public IP Address and enter it into the RDC program to find your VM.

Use your windows Log in credentials to log in.


</p>
<br />
_________
<p>
<h3>Download required files on Virtual Machine</p><h3>
</p>
<p><h5>for convenience I provide a folder where all required downloads are kept together: https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD</h5></p>
<p>Install / Enable IIS in Windows WITH CGI
  World Wide Web Services -> Application Development Features -> [X] CGI</p>

  <p>nstall PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)</p>

<p>install the Rewrite Module (rewrite_amd64_en-US.msi)</p>

<p>Create the directory C:\PHP</p>

<p> unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder</p>

<p> install VC_redist.x86.exe.</p>

<p> install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Username: root
Password: root
</p>

<p>Open IIS as an Admin

Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

Reload IIS (Open IIS, Stop and Start the server)
</p>

<p>Install osTicket v1.15.8
From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”</p>

<p>Reload IIS (Open IIS, Stop and Start the server)</p>

<p>Go to sites -> Default -> osTicket
On the right, click “Browse *:80”
</p>

<p>Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browser, observe the changes
</p>

<p>Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>

<p>Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All
</p>

<p>Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)
</p>

<p>From the “osTicket-Installation-Files” folder, install HeidiSQL.
Open Heidi SQL
Create a new session, root/root
Connect to the session
Create a database called “osTicket”
</p>

<p>Continue Setting up osTicket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: root
Click “Install Now!”
</p>

<p></p>


</p>
<br />
