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

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Enable internet information services (IIS)
- Install web-platform installer 
- Install MySQL & set up name and password 
- Install C++ re-distributable
- Configure permissions & install OsTicket

<h2>Installation Steps</h2>
Part 1: Creating a Virtual Machine in Azure

1. Establish a Resource Group.
2. Set up a Windows 10 Virtual Machine (VM) featuring 2-4 Virtual CPUs.
    - While configuring the VM, authorize the creation of a new Virtual Network (Vnet).

Create an Azure Virtual Machine with the following specifications:
- Name: Vm-osticket
- Username: labuser (customize as needed)
- Password: Choose a password, for instance, osTicketPassword1!

Part 2: Installing/Enabling IIS in Windows with CGI and Common HTTP Features

1. Navigate to World Wide Web Services -> Application Development Features during the installation.
    - Enable CGI and Common HTTP Features:
        - [X] CGI
        - [X] Common HTTP Features

2. Additionally, include the IIS Management Console in the installation process.
   - Access Internet Information Services -> Web Management Tools -> IIS Management Console.
       - [X] IIS Management Console
<p>
</p>
<p>
  - Obtain the PHP Manager for IIS installation by downloading and installing the file PHPManagerForIIS_V1.5.0.msi from the provided Installation Files.

  - Install the Rewrite Module by downloading and installing the file rewrite_amd64_en-US.msi from the Installation Files.

- Establish a directory at C:\PHP.

- Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) from the Installation Files, and extract its contents into the C:\PHP directory.
<br />

<p>
</p>
<p>
1. Download and install VC_redist.x86.exe from the Installation Files.

2. Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the Installation Files. Follow the Typical Setup, launch the Configuration Wizard after installation, choose Standard Configuration, and set the password to "Password1."

3. Open IIS as an Administrator.

4. Register PHP from within IIS.

5. Reload IIS by stopping and starting the server.

6. Install osTicket v1.15.8:
   - Download osTicket from the Installation Files Folder.
   - Extract and copy the "upload" folder to C:\inetpub\wwwroot.
   - Rename the "upload" folder within C:\inetpub\wwwroot to "osTicket."

7. Reload IIS by stopping and starting the server.

8. Access sites -> Default -> osTicket. Click "Browse *:80" on the right.

9. Note that some extensions are not enabled. Go back to IIS, sites -> Default -> osTicket. Double-click PHP Manager.
   - Click "Enable or disable an extension."
   - Enable: php_imap.dll, php_intl.dll, php_opcache.dll.
   - Refresh the osTicket site in your browser and observe the changes.

10. Rename ost-config.php:
    - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
    - To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

11. Assign Permissions to ost-config.php:
    - Disable inheritance -> Remove All.
    - New Permissions -> Everyone -> All.

12. Continue setting up osTicket in the browser (click Continue).
    - Name: Helpdesk
    - Default email (receives emails from customers).

13. Download and install HeidiSQL from the Installation Files.
    - Open Heidi SQL.
    - Create a new session with root/Password1.
    - Connect to the session.
    - Create a database called "osTicket."

14. Continue setting up osTicket in the browser:
    - MySQL Database: osTicket
    - MySQL Username: root
    - MySQL Password: Password1
    - Click "Install Now!"

15. Congratulations! Verify the installation with no errors.
    - Browse to your help desk login page: http://localhost/osTicket/scp/login.php.

16. Clean up:
    - Delete C:\inetpub\wwwroot\osTicket\setup.
    - Set Permissions to "Read" only for C:\inetpub\wwwroot\osTicket\include\ost-config.php.

Notes:
- Browse to your help desk login page: http://localhost/osTicket/scp/login.php.
- End Users osTicket URL: http://localhost/osTicket/.

Part 3 (Post Installation Setup):

17. Configure Roles:
    - Admin Panel -> Agents -> Roles.
    - Supreme Admin.

18. Configure Departments:
    - Admin Panel -> Agents -> Departments.
    - System Administrators.

19. Configure Teams:
    - Admin Panel -> Agents -> Teams.
    - Level I Support, Level II Support.

20. Allow anyone to create tickets:
    - Admin Panel -> Settings -> User Settings.
    - Registration Required: Require registration and login to create tickets.

21. Configure Agents (workers):
    - Admin Panel -> Agents -> Add New.
    - Jane, John.

22. Configure Users (customers):
    - Agent Panel -> Users -> Add New.
    - Karen, Ken.

23. Configure SLA:
    - Admin Panel -> Manage -> SLA.
    - Sev-A (1 hour, 24/7), Sev-B (4 hours, 24/7), Sev-C (8 hours, business hours).

24. Configure Help Topics:
    - Admin Panel -> Manage -> Help Topics.
    - Business Critical Outage, Personal Computer Issues, Equipment Request, Password Reset.

Part 4 (Tickets and Ticket Lifecycle):

25. Practice creating, triaging, and solving tickets. Watch the video for guidance.

Ticket Examples:
- Sev-A (1 hour, 24/7): Entire mobile/online banking system is down. Assign to SysAdmins.
- Sev-B (4 hours, 24/7): Accounting department needs Adobe upgrade, broken.
- Sev-B/C (2 hours, business hours): CFO’s laptop seems a bit slow.
</p>
<br />
