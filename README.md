<p align="center">
<img src="https://i.imgur.com/1t12J8p.png"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
Widely-used the open source support system osTicket seamlessly integrates inquieries created via email, phone and web-based forms into a simple easy-to-use multi-user web interface. Manage, organize and archive all your support requests and responses in one place while providing your customers the high quality service they deserve.
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Technologies and Environments Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- osTicket Installation files
- Heidi SQL

<h2>Installation Steps</h2>
Welcome to this tutorial!

I have provided a link here: [osTicket prerequisite and installation files](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)
<br>
That link will provide you with all the material needed to download and get osTicket up and running.

**Here a Step by step guide line Doc**: [CLICK ME](https://docs.google.com/document/d/1NwkGnj89wmbUcU-N2-20DjQNER1iwr_t/edit?usp=share_link&ouid=111907008899833271635&rtpof=true&sd=true)

Let's get started quickly by creating our resource group and virtual machine (VM) in the Microsoft Azure portal. Creating the virtual machine will automatically create the resource group. In order to protect our physical machine from any event that may occur, we will use a VM and connect to it via RDP (Remote Desktop Protocol) for the next steps in our tutorial.

<img src="https://i.imgur.com/MxVXQ77.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/9QRjRka.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Now that the Virtual Machine is created we can see the public IP address and we will use that to do our remote connection.

<img src="https://i.imgur.com/gYsmhFz.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now ,simply connect to our newly created VM via RDP using the VM public IPv4 address and log in as "labuser".
Note:If you are a Mac user, you will have to download Microsoft Remote Desktop to be able to remotely connect to the VM.
<img src="https://i.imgur.com/TQmWD8Y.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

Now that we are connected to the VM we will have to enable **IIS (Internet Information Services)**. To do so, 1-Access the Control Panel > 2-Program > 3-On the upper left hand side select **"Turn Windows features On or Off"**> 4- Enable the **IIS** (Internet Information Services) > 5-Expand the World Wide Web Services > 6-Expand Application Development features > 7-Check the **CGI box and click OK to install**.


<img src="https://i.imgur.com/FC5URDa.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

We also need to make sure all boxes are checked in the Common HTTP Features and the IIS Management Consol in Web Management Tools is checked as well. Once everthing is checked click ok to apply the changes.

<img src="https://i.imgur.com/HAlV0xU.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/qFPos6P.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

</p>
<p>

 To verify that we have installed **IIS** installed correctly we can check by opening a web brower in the virtual machine and going to a random IP address such as 127.0.0.1 and we should get a page that looks like the following:

 <img src="https://i.imgur.com/2B86w51.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
 
</p>
<p>
 
**From the installation files, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)**

<p>
<img src="https://i.imgur.com/m8nEJVP.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
 
<img src="https://i.imgur.com/FPriEZH.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<br />

**From the installation files, install the Rewrite Module (rewrite_amd64_en-US.msi)**

<p>
<img src="https://i.imgur.com/jMhMj4O.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/8MDdeDl.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<p></p>
<br />

**Next we are going to create the directory C:\PHP on the local drive**


<img src="https://i.imgur.com/yhiFoat.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>


**From the installation files, unzip PHP 7.3.8(phph-7.3.8-nts-Win32-VC15-x86.zip) into the C:/PHP directory we created.**

<p>
<img src="https://i.imgur.com/iwBCNaD.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/R05sDMM.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/cLbq5ed.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
 

</p>
<p></p>
<br />

**From the installation files install VC_redist.x86.exe.**

<p>
<img src="https://i.imgur.com/4x8DCoL.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/3vix1kz.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

**From the installation files install MySQL 5.5.62 (mysql-5.5.62-win32.msi)**

**Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Password1**

<p>
<img src="https://i.imgur.com/ycbRuOV.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

<p>
<img src="https://i.imgur.com/x0JBJN6.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

<p>
<img src="https://i.imgur.com/qyutvAG.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

<p>
<img src="https://i.imgur.com/Dyr8TV2.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

**Open IIS as an Administrator**

<p>
<img src="https://i.imgur.com/eeCZTzl.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

 **Register PHP by double clicking the PHP Manager, clicking Register New PHP Version,and browsing to the PHP excutable file**
 
<img src="https://i.imgur.com/GXdOKkI.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/HIqcvhp.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/PDaEaO8.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

**Do a quick restart to refresh the server** **(This is not required just recomennded)**

<p>
<img src="https://i.imgur.com/varqghK.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

<h2>Install osTicket v1.15.8</h2>

**Download the osTicket-v1.15.8 zip folder from the Installation Files**

<p>
<img src="https://i.imgur.com/HiFXvwg.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

**After downloading the zip file open the folder and locate the Upload folder**

<p>
<img src="https://i.imgur.com/mqrqp7L.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

**Next open a second file explorer and locate and open the folder C:\inetpub**

<p>
<img src="https://i.imgur.com/AI83dab.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

**In the folder C:\inetpub locate the folder "wwwroot" and drag the "Upload" folder from the osTicket Folder into the "wwwroot" folder.**

<p>
<img src="https://i.imgur.com/ILaNIMr.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>

<p>
<img src="https://i.imgur.com/IbxUg7D.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

**Finally rename the upload folder to osTicket**

<p>
<img src="https://i.imgur.com/KGuFBx3.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

**Do a quick restart to refresh the server**

<p>
<img src="https://i.imgur.com/varqghK.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />




Go back into IIS manager and enable some extensions. To do this you have to go to Sites->Default->osTicket Then double click on PHP manager. Click on **Disable or enable an extension** Enable  "phph_imap" - "php_intl.dll"  &  "php_opcache.dll" then refresh the osTicket webserver and obsereve the changes.




Go back into c:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php rename the file to c:\inetpub\wwwroot\osTicket\include\ost-config.php Assign permissions to ost-config.php Disable inheritance->Removeall New Permissions->Everyone->all
<p>
<img src="https://i.imgur.com/K8rJfTj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

After changing the ost-config.php file and clicking continue and you should see the following screen

<p>
<img src="https://i.imgur.com/ezp9fFm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>Once the above information is filled in click save changes at the bottom of the screen
<br />
After saving you should see this screen. Click continue at the bottom of the screen

<p>
<img src="https://i.imgur.com/SafFTug.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

Congratulations! Your osTicket installation has been completed successfully.
<p>
<img src="https://i.imgur.com/8QmIKZo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

From the installation files install HeidiSQL
Open Heidi SQL
Create a new session, root/Password1, Connect to the session, Create a database called “osTicket”, Click Open

<img src="https://i.imgur.com/qcY4V4w.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p></p>
<br />

Success! You made it. You have installed osTicket! 

<p>
<img src="https://i.imgur.com/m0pfONL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

Thank You for reading!

