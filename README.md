<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<!-- <h2>Video Demonstration</h2> -->

<!-- - ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com) -->

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create a Resource Group in Azure 
- Create a VM in the resource group
- Enable / install IIS in windows
- Download PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) from Microsoft
- Rewrite Module (rewrite_amd64_en-US.msi)
- PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip)
- Microsoft Visual C++ Redistributable(2015-2022)

<h2>Creating Resource Group and Virtual Machine in Azure </h2>
<p>
Create Resource Group
</p>

![Screen Shot 2023-03-31 at 8 18 52 PM](https://user-images.githubusercontent.com/88648101/229257003-f0efd402-35f5-48ec-b9ee-be3897a8f7ae.png)
<p>
Create a Resource Group; in this example I named mine RG-osticket.
</p>
<br />

<p>
Create a Virtual Machine Group
</p>

![Screen Shot 2023-03-31 at 8 46 16 PM](https://user-images.githubusercontent.com/88648101/229257681-625e1d59-2c24-4bf1-aba3-9486e11e8e0b.png)

![Screen Shot 2023-03-31 at 8 48 20 PM](https://user-images.githubusercontent.com/88648101/229257690-750ec14e-76f9-4b32-a251-b88d4fa98a72.png)

![Screen Shot 2023-03-31 at 8 51 04 PM](https://user-images.githubusercontent.com/88648101/229257699-45553362-2016-4194-8b35-44912b5919fd.png)


<p>
  Create a virtual machine and select the Resource Group we created earlier. Make sure the region is set to the same region we created our Resource Group and for the VM image choose window 10 Pro, version 21H2. Enter a username and password for the Administrator Account and make sure to rememeber it as we will use it to log into the VM. under the Networking allow Azure to create a virtual network, a subnet, and a public ip. Click on Review + Create to create the virtual machine.
</p>
<br />

<h2>Connecting to Microsoft Remote Desktop on a mac</h2>

<img width="939" alt="Screen Shot 2023-03-31 at 9 17 51 PM" src="https://user-images.githubusercontent.com/88648101/229258754-a442606d-5909-4251-b814-0aedb5d09aa9.png">
<p>
If you are using a macbook like I am in this example, you will have to download the Microsoft Remote Desktop from the app store.
</p>

<img width="913" alt="Screen Shot 2023-03-31 at 9 21 24 PM" src="https://user-images.githubusercontent.com/88648101/229258988-20e9cfaa-8c78-4140-bf6b-257a8e97fbc8.png">

![Screen Shot 2023-03-31 at 9 27 08 PM](https://user-images.githubusercontent.com/88648101/229259227-b559c183-6fb0-4fb2-8ce8-b4ef6809524c.png)
<p> 
After downloading Microsoft Remote Desktop, open the app and enter the Public IP address of the VM we created in the field of PC name. the IP address can be found in Azure by clicking on the virtual machine and looking in the overview. 
</p>

<img width="988" alt="Screen Shot 2023-03-31 at 9 30 14 PM" src="https://user-images.githubusercontent.com/88648101/229259524-4f019586-1755-40ea-94f6-c0a1b098d175.png">
<p> 
Enter the administrator information we provided while creating the VM. a message will appear click continue to log in to the VM.
</p>
<br />

<h2 align="center"> Installation </h2>
<p>
Installing / Enabling IIS in widows
</p>
<img width="1120" alt="Screen Shot 2023-04-01 at 3 29 10 PM" src="https://user-images.githubusercontent.com/88648101/230892706-81acbca4-43ab-4e0c-8c58-cfb4901a2271.png">

<img width="1729" alt="Screen Shot 2023-04-10 at 7 38 52 AM" src="https://user-images.githubusercontent.com/88648101/230895097-84314540-682f-4a06-bcd5-790a75700da5.png">
<p> 
 In the windows VM, search control panel and clicke on programs. In "Programs and Features" clicke on "Turn Windows Features on or off". A windows features box will appear check internet information services(IIS). Expand IIS by clicking on the plus sign next to it. Expand World Wide Web Services and expand Application Development Features. in Application Development Feautes check CGI. click ok. To check if we did it right, open a web browser and type in the loopback address 127.0.0.1 the default IIS web page should load up as seen in the second image.
</p>
<br />

- Download PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) from Microsoft
- Download Rewrite Module (rewrite_amd64_en-US.msi) and create a directory called PHP in the root of the c: drive
- Download PHP Version 7.3.8 and unzip the contents into the PHP Folder we just created.
- Download Microsoft Visual C++ Redistributable(2015-2022)

Download MySQL Server 5.5. in the setup choose typical for type of setup and finish downloading. a new window will pop up asking to configure instance. select the "standard configuration".  click next and leave the check on "Install As Window Service". click next and enter the a password in "New root password". Make sure to rememeber this password as it will be used to log in to your MySQL instance. click next and execute to finish installing. 
<br />
<p>
 Configuration in IIS
</p>
<img width="1331" alt="Screen Shot 2023-04-10 at 10 45 41 AM" src="https://user-images.githubusercontent.com/88648101/230924896-a4343550-ddae-4c50-a28c-8a7cdf1e82c7.png">
<p>
 Click on start type in IIS and run as an administrator. In IIS,you should see the PHP Manager we downloaded earlier. double click it and click on the Register new PHP version. Select the path of the new PHP by browsing to the PHP folder we created and selecting php-cgi. click ok and restart the  server by clicking on the vm and clicking restart under the Manage Server.
</p>
<br />
<p>
Download osTicket
  
 https://drive.google.com/drive/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6
<p/>