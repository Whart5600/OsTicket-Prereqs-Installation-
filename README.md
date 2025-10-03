

osTicket - Prerequisites and Installation

This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.
Environments and Technologies Used
* Microsoft Azure (Virtual Machines/Compute)
* Microsoft Remote Desktop (RDP)
* Internet Information Services (IIS)
Operating Systems Used 
* Windows 10
List of Prerequisites
* Azure Virtual Machine
* osTicket Installation files
* Heidi SQL
Installation Steps

Welcome to my first in-depth IT tutorial! To begin we will have to create a Virtual machine using the Microsoft Azure portal(portal.azure.com). We will be using a VM(virtual machine) which is a remote computer. We are using a VM in order to protect our physical machine just in case something malfunctions, and also have a clean slate computer to continually replicate the lab on. Create a resource group and title it "osTicket". Afterwards create a VM with 2-4 CPUs. In this example I will be using 4 CPUs.
<img width="1919" height="968" alt="image" src="https://github.com/user-attachments/assets/a094cff4-c0d3-4bde-a918-0ae1024cc781" />



Next simply connect to your newly created VM using RDP using the public IPv4 address. If you are a Mac user you will have to download Microsoft Remote Desktop(RDP). 
<img width="406" height="253" alt="osticket2" src="https://github.com/user-attachments/assets/3ae0e1f0-d37e-441e-80db-e7fe0a9cd30d" />




Alright, now that you are connected to your VM you will have to enable IIS. Simply access the control panel then select uninstall a program. Off to the left select "Turn windows features on or off". A list will appear then you will enable Internet Information Services.
<img width="1122" height="591" alt="image" src="https://github.com/user-attachments/assets/c2ec3de8-50b2-45b6-811e-fc17141f349d" />




Excellent. Now that you have enabled IIS we need to install Web Platform Installer. I have provided a link here: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6 That link will provide you with all of the material you need to download to get osTicket up and running. Simply click the link and install the Web Platform Installer
<img width="495" height="387" alt="image" src="https://github.com/user-attachments/assets/908b6a3d-8170-401b-957d-a9439ef9d098" />


Once you have installed Web Installer Platform open it. From inside the application you are going to install MySQL 5.5 Afterwards install x86 version of PHP up until 7.3. There are some failed files such as C++ redistributable package as well as PHP 7.3.8 and PHP Manager for IIS those files can be found with the install link.
<img width="890" height="608" alt="image" src="https://github.com/user-attachments/assets/5fb93c46-63c9-4291-ae16-739f3774c254" />


Next download osTicket. Then extract and copy the "upload" folder into c:\inetpub\wwwroot. Afterwards rename the folder to osTicket
<img width="1150" height="660" alt="image" src="https://github.com/user-attachments/assets/960ca2bb-210c-46fb-a1d0-2d22ecefb120" />




Open IIS Manager and restart the server. Once inside IIS manager go to Sites->Default->osTicket on the right, click "Browse*.80" from there your default browser should open osTicket webserver.
<img width="1425" height="752" alt="image" src="https://github.com/user-attachments/assets/f0e6c53a-40b8-4fd6-89ab-60e2555902f1" />



Go back into IIS manager and enable some extensions. To do this you have to go to Sites->Default->osTicket Then double click on PHP manager. Click on "Disable or enable an extension" Enable "php_intl.dll" & "php_opcache.dll" then refresh the osTicket webserver and obsereve the changes "Intl Extension" should now be enabled. 
<img width="1424" height="753" alt="image" src="https://github.com/user-attachments/assets/dd031976-fc43-48e2-80d5-6f9b4d8c945f" />



Go back into c:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php rename the file to c:\inetpub\wwwroot\osTicket\include\ost-config.php Assign permissions to ost-config.php Disable inheritance->Removeall New Permissions->Everyone->all
<img width="1470" height="697" alt="image" src="https://github.com/user-attachments/assets/e3a4097d-93a4-4ce4-8142-db13565fd3f6" />



Afterwards continue setting up osTicket in the browser (click continue) then you will name the Helpdesk to your liking. Select a default email that will receive emails from customers who submit tickets. 
<img width="889" height="950" alt="image" src="https://github.com/user-attachments/assets/54bf8a4f-a01f-4648-ab70-9e2c66a1eda5" />



Continue Setting up osticket in the browser MySQL Database: osTicket MySQL Username: root MySQL Password: Password1 Click “Install Now!” Congratulations, hopefully it is installed with no errors! Clean up Delete: C:\inetpub\wwwroot\osTicket\setup Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php Login to the osTicket Admin Panel (http://localhost/osTicket/scp/login.php)
