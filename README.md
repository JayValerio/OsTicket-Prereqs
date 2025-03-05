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

<h2>Operating Systems Usedd </h2>

- Windows 10</b> (21H2)

<h2>What We Will Do</h2>

- Create Virtual Machine Using Asure
- Launch Virtual Machine using Remote Desktop (Mac/Windows)
- Download required files on Virtual Machine
- osTicket initial set up

<h2>Installation Steps</h2>

<p>
<h3>Create a Virtual Machine (VM)</h3><br/>
  
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
<p>
Install / Enable IIS in Windows WITH CGI
 - World Wide Web Services -> Application Development Features -> [X] CGI

</p>
<br />
