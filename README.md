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

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- [Link to Downloads](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)

<h2>Installation Steps</h2>

<br /><h2>Step 1 - Create an Azure Virtual Machine and Resource Group</h2>
<p> Start with the creation of an Azure Virtual Machine alongside a Resource Group. Access the Azure Portal and proceed to create a new Virtual Machine. Establish a new Resource Group and give it a suitable name.</p>
<p>
<img src="https://imgur.com/uRuN09F.png" height="70%" width="70%" alt="Create Azure Virtual Machine"/>
</p>
<p>
<img src="https://imgur.com/LiZ9WQp.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/DzckhoM.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Configure the virtual machine to run Windows 10 Pro, version 22H2. We will configure the deployment with 4 vCPUs and 16 GiB of RAM. Set up your login credentials to gain access to the virtual machine. Confirm that the licensing checkbox is ticked and that a virtual network exists in the Networking Tab.  Once all specifications are completed, navigate to 'Review + Create' and proceed to create the virtual machine. 
</p>
<br />



<br /><h2>Step 2 - Remote Desktop to the Virtual Machine</h2>
<p>
Access the new Virtual Machine in the Azure Portal, identify the Public IP Address, and copy it. Launch "Remote Desktop Connection" on your local machine and enter the copied IP address. Sign in with the credentials you created during the VM setup.
</p>
<p>
<img src="https://imgur.com/Gysrja1.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/1uCVT0n.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/TXHprkA.png" height="35%" width="35%" alt="Resources"/>
</p>



<br /><h2>Step 3 - Install / Enable IIS in Windows with CGI and Common HTTP Features</h2>
<p>
After accessing the Virtual Machine, launch the Control Panel and choose 'Programs'. Next, click on 'Turn Windows Features on and off'. 
</p>
<p>
<img src="https://imgur.com/xmOrou5.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/t59Rt51.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
To enable IIS on Windows along with CGI and Common HTTP Features, ensure that the appropriate options are chosen.

World Wide Web Services -> Application Development Features -> [X] CGI [X] Common HTTP Features

Internet Information Services -> Web Management Tools -> IIS Management Console
	[X] IIS Management Console
</p>
<p>
<img src="https://imgur.com/WK5LzCC.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/h83r69D.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
Once all the correct checkboxes have been selected, click ok to apply the changes. To check if the changes were applied correctly, launch a web browser and input '127.0.0.1' into the search bar, which should display the 'Internet Information Services' page below.
</p>
<p>
<img src="https://imgur.com/XFqN4S9.png" height="70%" width="70%" alt="Resources"/>
</p>



<br /><h2>Step 4 - Install PHP Manager for IIS, along with the Rewrite Module and Microsoft Visual C++ Redistributable.</h2>
<p>
From the <a href="https://drive.google.com/drive/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Link to Files</a>, Download the following files: 'PHPManagerForIIS_V1.5.0.msi', 'rewrite_amd64_en-US.msi', and 'VC_redist.x86.exe'. Once the files are downloaded, proceed to install all three on the virtual machine.
</p>
<p>
<img src="https://imgur.com/ArPd1UX.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/Ir51bAt.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/wMW5Jmk.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/wO0tn61.png" height="35%" width="35%" alt="Resources"/>
</p>




<br /><h2>Step 5 - Download and Install PHP 7.3.8</h2>
<p>
Locate the 'php-7.3.8-nts-Win32-VC15-x86.zip' file and download it. 

!! ATTENTION !!
If you see this message, select “Keep” to retain the file:
</p>
<p>
<img src="https://imgur.com/B9yxJvO.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/AxzgeXG.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
Next, navigate to the C:\ directory, create a new folder, and name it 'PHP'. Extract the contents of the 'php-7.3.8-nts-Win32-VC15-x86.zip' file into the newly created C:\PHP directory.
</p>
<p>
<img src="https://imgur.com/QjLTS57.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/0JClFWb.png" height="70%" width="70%" alt="Resources"/>
</p>




<br /><h2>Step 6 - Download and Install MySQL5.5.62</h2>
<p>
Find the 'mysql-5.5.62-win32.msi' file and download it. Once the download is complete, start the setup wizard: choose Typical Setup -> Launch Configuration Wizard (post-installation) -> Standard Configuration. Assign 'Password1' as the root password, then click 'Execute' and 'Finish' when finished.
</p>
<p>
<img src="https://imgur.com/bonUtb3.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/jU3gHJJ.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/vDeMJak.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/hdNKUYg.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/sz9tXMW.png" height="35%" width="35%" alt="Resources"/>
</p>


<br /><h2>Step 7 - Register PHP from within IIS</h2>
<p>
With the files downloaded and installed, search for IIS in the Windows search bar. Launch IIS with administrative privileges. Click on 'PHP Manager' to access it.
</p>
<p>
<img src="https://imgur.com/WP7tgMH.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Choose 'Register new PHP Version'.
</p>
<p>
<img src="https://imgur.com/BdvpC3A.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Specify the path for the PHP executable 'php-cgi.exe'. This file can be found in the PHP directory at 'C:\PHP'. Once you have selected the file path, click 'OK'.
</p>
<p>
<img src="https://imgur.com/OfcKCDT.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
After completing the steps, restart the IIS server.
</p>
<p>
<img src="https://imgur.com/3yoQJba.png" height="70%" width="70%" alt="Resources"/>
</p>



<br /><h2>Step 8 - Download and install osTicket</h2>
<p>
First, download the zip file labeled ‘osTicket-v1.15.8’. Afterward, unpack the file and place the extracted ‘upload’ folder into ‘c:\inetpub\wwwroot’. Rename this folder from ‘upload’ to ‘osTicket’.
</p>
<p>
<img src="https://imgur.com/OaICJQD.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/wNBcanU.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
After finishing, reopen IIS and restart the service. Head to Sites, choose Default, then osTicket. On the right side of the IIS Manager, click on ‘Browse *:80’, which will launch your browser and bring up the osTicket installation screen.
</p>
<p>
<img src="https://imgur.com/dWxMo7h.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/8PG5ABd.png" height="70%" width="70%" alt="Resources"/>
</p>




<br /><h2>Step 9 - Enable osTicket Extensions</h2>
<p>
To activate the required extensions, return to the IIS manager, go to Sites -> Default -> osTicket, and double-click PHP Manager. In the PHP Extensions section, select ‘Enable or disable an extension’.
</p>
<p>
<img src="https://imgur.com/5UDDMoK.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/dLDGji8.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Turn on the following extensions:
	
- php_imap.dll
- php_intl.dll
- php_opcache.dll
</p>
<p>
<img src="https://imgur.com/aKDapBY.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
 After completing the steps, refresh the osTicket installer to see the changes.
</p>


<br /><h2>Step 10 - Rename ost-config.php and Assign Permissions</h2>
<p>
Go to 'C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php'. Change the name of 'ost-sampleconfig.php' to 'ost-config.php'.
</p>
<p>
<img src="https://imgur.com/FccMkNC.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Once the file is renamed, right-click on ‘ost-config.php’, choose ‘Properties’, go to the ‘Security’ tab, click on ‘Advanced’, and disable inheritance to remove all inherited permissions.
</p>
<p>
<img src="https://imgur.com/i8jKtdF.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Next, click ‘Add’ and select ‘Choose a principal’. Enter ‘everyone’ in the field, ensure that all permission boxes are checked, then click ‘OK’. Afterward, select ‘Apply’ and finish by clicking ‘OK’ again.
</p>
<p>
<img src="https://imgur.com/c025Ek8.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/O1VmwRF.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/AKKetNf.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/XqNgnPA.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/8k31PH2.png" height="70%" width="70%" alt="Resources"/>
</p>


<br /><h2>Step 11 - Download and install HeidiSQL</h2>
<p>
Begin by downloading and installing HeidiSQL. Once the setup process is finished, open the program. Click ‘New’ in the lower-left corner, enter ‘root’ as the username and ‘Password1’ as the password, then choose ‘Open’.
</p>
<p>
<img src="https://imgur.com/z6e86F9.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/9wd9nQQ.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
After clicking ‘Open’, a new HeidiSQL instance will appear. Right-click on ‘Unnamed’, choose ‘Create new’, then select ‘Database’. Enter ‘osTicket’ as the database name, and press ‘OK’.
</p>
<p>
<img src="https://imgur.com/21RPVtH.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/xegg4yM.png" height="35%" width="35%" alt="Resources"/>
</p>


<br /><h2>Step 12 - Finish osTicket Setup</h2>
<p>
After finishing the HeidiSQL setup, return to the osTicket webpage and select ‘Continue’. Complete the required fields under ‘System Settings’, ‘Admin User’, and ‘Database Settings’.

In this lab, use ‘Lab Help Desk’ as the ‘Helpdesk Name’ and set the default email to ‘lab@helpdesk.com’. 

For the ‘Admin User’ details, fill in the ‘First Name’ (such as user), ‘Last Name’ (such as admin), ‘Email Address’ (for example, user_admin@helpdesk.com), ‘Username’ (like user_admin), and ‘Password’ (for instance, Password1). 

For ‘Database Settings’, confirm that the ‘MySQL Database’ name is ‘osTicket’, the ‘MySQL Username’ is ‘root’, and the ‘MySQL Password’ is ‘Password1’.

After completing all the fields, click on ‘Install Now’ to proceed.
</p>
<p>
<img src="https://imgur.com/m7DFiwF.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Once the process is finished, osTicket should be successfully set up! Congratulations!
</p>
<p>
<img src="https://imgur.com/FEE32n7.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>