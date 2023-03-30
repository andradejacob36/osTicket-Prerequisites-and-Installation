<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket: Prerequisites and Installation</h1>
This tutorial will demonstrate how to build a help desk system using osTicket. Before installing it, this tutorial will also teach you how to set-up the pre-requirement applications<br/>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machine/Resource group)
- Remote Desktop Connection 
- osTicket (open-source ticketing system)
- CGI (Computer-Generated Imagery) 
- IIS (Internet Information Services)
- PHP (Hypertext Preprocessor)
- VC_redist.x86.
- MySQL 5.5.62
- HeidiSQL
<h2>Operating Systems Used </h2>

- Windows 10 Pro, version 21H2 (free services eligible)</b> 

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: You need to authenticate and authorize yourself by logging into the Azure portal.
- Step 2: Create a Resource group
- Step 3: Create a virtual machine using Azure and some given specifications
- Step 4: Configure remote access to the virtual machine using Remote Desktop Protocol
- Step 5: Download/Install these applications on your VM: CGI on IIS, PHP Manager, Rewrite Module, PHP 7.3.8, VC_redist.x86.exe, & MySQL 5.5.62
- Step 6: Open IIS as an Admin & Register PHP from within IIS
- Step 7: Install osTicket on the VM
- Step 8: Configure the osTicket with the necessary settings, including email, database, and help desk settings
- Step 9: Navigate to the osTicket web interface and log in using the administrator credentials

<h2>Step 1: You need to authenticate and authorize yourself by logging into the Azure portal</h2>
 
1. Go to the Azure Portal website (https://portal.azure.com/) and sign-in with your Azure account credentials. 
- Note: If you do not have an Azure account, you will need to sign up for one before you can log-in.
2. Once you have successfully logged-in, you will be redirected to the Azure portal dashboard where you can create and manage your resources. 
3. You should be able to see the following display:
<p>
<img src="https://i.imgur.com/zr0sGpt.png" height="80%" width="80%"/>
</p>
<p>  

<h2>Step 2: Create a Resource group</h2>

1. Locate the search bar and type "Research groups".
2. To create a new item, click on the "+ Create" button located in the top left-corner next to the "Manage View" option.
   <ol type="a">
      <li>Choose your subscription (For Ex: Azure Subscription 1).</li>
      <li>Create a name of your resource group (Use: RG-osTicket).</li>
      <li>Choose a region to deploy the virtual machine to (For Ex: West US 3).</li>   
    </ol>

3. After, typing the given specifications click on the box "Review + create".
4. You should be able to see the following display:
<p>
<img src="https://i.imgur.com/ILYejQz.png" height="80%" width="80%"/>
</p>
<p>   

5. Then click "Create" located at the bottom left-corner.
 
- Note: By creating a Resource group, it would be like creating a container that will hold all of your related resources in one centralized location.

<h2>Step 3: Create a virtual machine using Azure and some given specifications</h2>

1. Again, click on the search bar and type "Virtual Machines".
2. Click on the "+ Create" button located on the top left-corner by "Switch to classic".
3. Choose the option "Azure virtual machine", enter the following information:
    <ol type="a">
      <li>Choose your subscription (For Ex: Azure Subscription 1).</li>
      <li>Create a name for resource group (Use: RG-osTicket).</li>
      <li>Enter a unique name for the virtual machine (Use: vm-osticket).</li>
      <li>For "Image" use: Windows 10 Pro, version 21H2 (free services eligible). </li>
      <li>For "Size" use: Standard_D4s_v3 - 4 vcpus, 16 GiB memory. </li>
      <li>For "Username" use: labuser.</li>
      <li>For "Password" make sure to make up one.</li>
      <li>For "Public inbound ports" click on "Allow selected ports".</li>
      <li>For "Select inbound ports" use: RDP 3389.</li>
    </ol>

- Note: After you checkmarked "I confirm I have an eligible Windows 10/11 license with multi-tenant hosting rights. Please confirm." located at bottom-left corner. Also, after you clicked on the "Review + create" button and review the settings. You should be able to see the following display:
<p>
<img src="https://i.imgur.com/mFRfIOw.png" height="80%" width="80%"/>
</p>
<p>  
    
- Note: Remember to keep your username and password you created in your notepad, as you will need them later. Also, verify that your information is correct!

4. Click on the "Create" button to create the virtual machine. 

- Note: It should take up 1-2 minutes to process the VM

5. Once the virtual machine Windows 10 Pro (21H2) is created, you can access it through the Azure portal or by using remote desktop tools.

<h2>Step 4: Configure remote access to the virtual machine using Remote Desktop Protocol</h2>

1. On the search bar, type "Virtual Machines".
- Note: After you created your VM, you should be able to see the following display:

<p>
<img src="https://i.imgur.com/yiGKwd4.png" height="80%" width="80%"/>
</p>
<p>  

2. Click the blue link "vm-osticket" located under "Name".
3. On the "Overview" tab, find/copy the Public IP address located under "Size"; Essentials.
<p>
<img src="https://i.imgur.com/6WKUKJ0.png" height="80%" width="80%"/>
</p>
<p>  

4. To access Remote Desktop Connection on Windows, navigate to the bottom-left corner and click on the "Start" button (Windows logo), then search for "Remote Desktop Connection" and open it. For Mac users download the app "remote- Microsoft Remote Desktop" from the App Store.
 
5. Paste the Public IP address(from your VM) in the computer name field and click "Connect". For Mac users paste the IP Address on "PC-name" and click "add".
 
 <p>
<img src="https://i.imgur.com/So0Dn0n.png" height="80%" width="80%"/>
</p>
<p>  
 
6. Afterwards, make sure to log-in your credentials from Step 3 (Use Username: labuser/Password: Your unique password).

- Note: For Windows users click "Yes" to connect to your VM. Observe the following display: 
<p>
<img src="https://i.imgur.com/xHG3t9h.png" height="80%" width="80%"/>
</p>
<p>  
 
7. Please wait until your virtual machine logs you in.
8. Then choose the following options for "Choose privacy settings for your device": 
    <ol type="a">
      <li>Location: No </li>
      <li>Diagnostic Data: No</li>
      <li>Tailored experiences: No</li>
      <li>Find my device: No</li>
     <li>Inking and Typing: No</li>
     <li>Advertising ID: No</li>
    </ol>
9. Click "Accept"

<h2>Step 5: Download/Install the following applications on your VM: CGI on IIS, PHP Manager, Rewrite Module, PHP 7.3.8, VC_redist.x86.exe, & MySQL 5.5.62</h2>

1. Install/Enable CGI on IIS. Do the following: 
    <ol type="a">
      <li>Right-click the "Start" Button (Windows logo) and click "Run"</li>
      <li>Type "control" for the "Run" panel and click "OK"</li>
      <li>On the Control Panel, do not click "Uninstall a program". Click "Programs".  </li>
      <li>Under "Programs and features", click "Turn Windows features on or off"</li>
      <li>By checking the box next to it, turn on "Internet Information Services.</li>
      <li>Expand IIS with "+" icon and double-click on "World Wide Web Services".</li>
      <li>Under WWWS, expand "Application Development Features" by double-clicking it.</li>
      <li>Check on the box next "CGI".</li>
      <li>Click "Okay".</li>
      <li>After the installation is complete make sure to close it.</li>
      <li> To verify your webserver is up & running, open Microsoft Edge and type on the URL "127.0.0.1".</li>
    </ol>  
- Note: By Installing/Enabling CGI on IIS, it lets you provide the necessary infrastructure for OSTicket to function correctly. Without CGI, the application would not work properly.

- Image Display of Step 5: 1.D
<p>
<img src="https://i.imgur.com/nhrzyaE.png" height="80%" width="80%"/>
</p>
<p> 

- Image Display of Step 5: 1.E-H
<p>
<img src="https://i.imgur.com/toQ7vio.png" height="80%" width="80%"/>
</p>
<p> 
 
2. Download/Install PHP Manager for IIS  
    <ol type="a">
      <li>On your VM, open Microsoft Edge and paste the following link: https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view </li>
      <li>After downloading PHP Manager, go to Downloads; File Explorer.</li>
      <li>Double-click "PHPManagerForIIS_V1.5.0 from the "Download" section.</li>
      <li>To agree to the License Agreement, navigate through the settings and click on the "agree" button.</li>
    </ol>
- Note: Note: You need to download and install PHP Manager for IIS when using osticket system because it is required for osticket to run properly.

- Image Display of Step 5: 2.A 
<p>
<img src="https://i.imgur.com/CkmZM9S.png" height="80%" width="80%"/>
</p>
<p> 

- Image Display of Step 5: 2.A
<p>
<img src="https://i.imgur.com/KhtmG5X.png" height="80%" width="80%"/>
</p>
<p> 

3. Download/Install Rewrite Module 
    <ol type="a">
      <li>On your VM, open Microsoft Edge and paste the following link: https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view </li>
      <li>Repeat previous instructions from Step 5: 2B, 2C, & 2D for "rewrite_amd64_en-US". </li>
    </ol>
- Note: The purpose of Rewrite Module for osticket is to improve the user experience and search engine optimization of your osticket installation. 

4. Create the directory C:\PHP
     <ol type="a">
      <li> On File Explorer, click "This PC".</li>
      <li> Under Devices & drives, proceed by double-clicking "Windows (C:)".</li>
      <li> Right-click, and click on "New" to create a folder.</li>
      <li> Name the folder to "PHP".</li>
    </ol>
  
- Note: The purpose of "PHP" folder within C:\PHP is to unzip the contents of the following program: PHP 7.3.8.

- Image Display of Step 5: 4.A-D
<p>
<img src="https://i.imgur.com/e0JaClP.png" height="80%" width="80%"/>
</p>
<p> 

5. Download PHP 7.3.8 and unzip the contents into C:\PHP
     <ol type="a">
      <li> On your VM, open Microsoft Edge and paste the following link: https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view </li>
      <li> Go to Downloads; File Explorer. </li>
      <li> Right-click on "php-7.3.8" and click on "Extract All".</li>
      <li> On the panel, "Extract Compressed (Zipped) Folders" click on "Browse".</li>
      <li> Re-do instructions from 4A & 4B.</li>
      <li> Double-click on "PHP" folder.</li>
      <li> At the right bottom corner of "Selection a destination", click on "Select Folder".</li>
      <li> Click on "Extract".</li>
    </ol>
    
- Note: You need to download PHP 7.3.8 and unzip the contents into C:\PHP for osticket because it is a requirement for running PHP scripts on your web server.

- Image Display of Step 5: 5.A
<p>
<img src="https://i.imgur.com/4xjzlyg.png" height="80%" width="80%"/>
</p>
<p> 
 
- Image Display of Step 5: 5.D
<p>
<img src="https://i.imgur.com/fwQJaHW.png" height="80%" width="80%"/>
</p>
<p> 

- Image Display of Step 5: 5.F-G
<p>
<img src="https://i.imgur.com/G9vj0ay.png" height="80%" width="80%"/>
</p>
<p> 

- Image Display of Step 5: 5.H
<p>
<img src="https://i.imgur.com/fLkULxx.png" height="80%" width="80%"/>
</p>
<p> 
 
6. Download/Install VC_redist.x86.exe
     <ol type="a">
      <li> On your VM, open Microsoft Edge and paste the following link: https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view </li>
      <li> Repeat previous directions from 2B, 2C, & 2D for "VC_redist.x86.exe". </li>
    </ol>

- Note: Downloading & installing VC_redist.x86.exe is necessary to ensure that osTicket can run on your computer without any issues.

7. Download/Install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
     <ol type="a">
      <li> On your VM, open Microsoft Edge and paste the following link: https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view </li>
      <li> Repeat previous directions from 2B & 2C for "MySQL 5.5.62".</li>
      <li> After agreeing to "End User License Agreement". You will see the following display: </li>      
      <li> Click "Typical".</li>
      <li> Afterwards, install the application.</li>
      <li> Click "Finish".</li>
      <li> Click "Next" on "Welcome to the MySQL Server Instance Configuration Wizard 1.0.17.0".</li>
      <li> Choose "Standard Configuration" and click "Next".</li>
      <li> Both on "New root password" & "Confirm" use:Password1(Optional).</li>
      <li> Click "Next" and click "Execute".</li>
      <li> After the download is complete click on "finish".</li>
    </ol>

- Note: The reason why you need to download and install this specific version of MySQL is because osticket was designed to work with it. Installing a different version of MySQL or a different database management system altogether may cause compatibility issues and may prevent osticket from functioning properly.

- Image Display of Step 5: 7.D
<p>
<img src="https://i.imgur.com/KxlTZ32.png" height="80%" width="80%"/>
</p>
<p> 
 
- Image Display of Step 5: 7.H
<p>
<img src="https://i.imgur.com/6NlwNgo.png" height="80%" width="80%"/>
</p>
<p> 

- Image Display of Step 5: 7.I-J
<p>
<img src="https://i.imgur.com/feFhhht.png" height="80%" width="80%"/>
</p>
<p> 

<h2>Step 6: Open IIS as an Admin & Register PHP from within IIS</h2>

1. At the bottom left corner, click on "Windows" Button.
2. Type "ISS", right-click it and choose the option: "Run as administrator".
3. Double-click "PHP Manager".
4. To enable PHP Manager, under PHP Setup, click on "Register new PHP version".
5. Double-click on "PHP" folder and click on "php-cgi".
6. Go back to vm-osticket Home, by clicking the server "vm-osticket (vm-osticket\labuser)" located at the top-left corner.
7. Then restart the server, under Manage Server, by clicking on "Restart". 
 
- Note: Opening IIS as an administrator and registering PHP allows the process of PHP files, which are required to run osticket on a Windows server.

- Image Display of Step 6.3 
<p>
<img src="https://i.imgur.com/04zJAen.png" height="80%" width="80%"/>
</p>
<p> 

- Image Display of Step 6.4
<p>
<img src="https://i.imgur.com/OwhmRH5.png" height="80%" width="80%"/>
</p>
<p> 
 
- Image Display of Step 6.5 
<p>
<img src="https://i.imgur.com/kWoXKd4.png" height="80%" width="80%"/>
</p>
<p> 
 
- Image Display of Step 6.7
<p>
<img src="https://i.imgur.com/ete7bMT.png" height="80%" width="80%"/>
</p>
<p> 
  
<h2>Step 7: Install osTicket on the VM</h2>

1. On your VM, download osTicket-v1.15.8.zip from the following link: https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

- Image Display of Step 7.1
<p>
<img src="https://i.imgur.com/7YQBvuQ.png" height="80%" width="80%"/>
</p>
<p> 

<h2>Step 8: Configure the osTicket with the necessary settings, including email, database, and help desk settings</h2>

1. Extract and copy "upload" folder to c:\inetpub\wwwroot
     <ol type="a">
      <li> Open File Explorer and have it open on "This PC" and double-click on "Windows (C:)".</li>
      <li> Double-click on "inetpub" folder and then proceed by double-clicking on "wwwroot".</li>      
      <li> Separately, open another Windows File Explorer and go to Downloads.</li>
      <li> Then double-click on "osTicket-v1.15.8" zip file.</li>
      <li> Now, have both Windows File Explorers on display to drag "upload" folder to wwwwroot.</li>
      <li> Within the wwwroot file folder, rename "upload" to "osTicket".</li>
    </ol>

- Image Display of Step 8: 1.A-B
<p>
<img src="https://i.imgur.com/JkpPG8Y.png" height="80%" width="80%"/>
</p>
<p> 
    
- Image Display of Step 8: 1.E
<p>
<img src="https://i.imgur.com/5reVM7j.png" height="80%" width="80%"/>
</p>
<p>     

- Image Display of Step 8: 1.F
<p>
<img src="https://i.imgur.com/thKmnkv.png" height="80%" width="80%"/>
</p>
<p>     
    
    
    
    
    
    
    
    


    
2. Reload ISS (Open IIS, Stop and Start the server) 
     <ol type="a">
      <li> To refresh it again, go back to the Internet Information Services(IIS) Manager App and repeat Step 6: 6 & 7.</li>
      <li> On the upper left corner, under "Connections", double-click on "Sites", "Default Web Site", & then "os-Ticket" file.</li>
      <li> Then on the upper-right corner, under "Manage Folder", click on "Browse *:80".</li>
      <li> After clicking "Browse *:80", you should have the following display open:</li>
    </ol> 
- Note: If you don't have the osTicket Installer browser open, you can re-do all of your steps from the beginning or troubleshoot the issue.

- Image Display of Step 8: 2.B
<p>
<img src="" height="80%" width="80%"/>
</p>
<p>  

- Image Display of Step 8: 2.C
<p>
<img src="" height="80%" width="80%"/>
</p>
<p>  

- Image Display of Step 8: 2.D
<p>
<img src="" height="80%" width="80%"/>
</p>
<p>  





3. Enable extensions for Osticket Installer on ISS. 
     <ol type="a">
      <li> Return to Internet Information Services(IIS) Manager App and at the upper-left corner, under "Connections", click on "vm-osticket" </li>
      <li> Then proceed by clicking "Sites" and afterwards "Osticket" </li>
      <li> Click on "PHP Manager" which is located between "Output Caching" and "Request Filtering"</li>
      <li> Under PHP Extensions, click on "Enable or disable an extension" </li>
      <li> It should look like this </li>
      <li> Look for php_imap.dll, php_intl.dll, & php_opcache.dll</li>
      <li> One by one you should be able to enable them by clicking "Enable" located at the upper right corner, under "actions"</li>
      <li> Go back to Osticket Installer site and refresh the it, and observe the changes.</li>
      <li> You should see the difference here: show two picture after and before</li>
    </ol> 
4. Rename: ost-config.php
     <ol type="a">
      <li> Go to File Explorer; then to "This Pc", "Windows (C:)", "inetpub", "wwwroot", "osTicket", and "Include"</li>
      <li> Scroll down to find "Ost-sampleconfig.php" and by right-clicking it rename it to "ost-config-php"</li>
    </ol> 
5. Assign Permissions:: ost-config.php
     <ol type="a">
      <li> Again right click "ost-config.php" and click on "Properties" and then go to "Security"</li>
      <li> Below "Permissions for SYSTEM" click on "Advanced" </li>
      <li> Click on "Disable inheritance" from the following display:</li>
      <li> Click "Remove all inherited permissions fomr this object"</li>
      <li> Click "add" </li>
      <li> Select "Select a principle" </li>
      <li> On the "Enter the object name to object" type "everyone" </li>
      <li> Click "Check Names", then "Okay" </li>
      <li> check on the box "Full control", then "Okay"</li>
      <li> Click okay for "Advanced Security Settings" and click "Apply"</li>
    </ol> 
6. Download/Install HeidiSQL
     <ol type="a">
      <li> Nagivate to this link to download it: https://docs.google.com/document/d/1WovrX2DaS9xkfaSr4LXyB4YnnWpXIgPCMMbbfgHmGVw/edit</li>
      <li> Go to "Downloads" on File Explorer. Also, Double click HeidiSQL to set it up </li>
      <li> After agreeing the License Agreement, keep clicking next until you see the install option</li>
      <li> Click "install". After that is finished click on "Finish" </li>
      <li> You should see the following display: </li>
      <li> At bottom left corner click on "New". Do not click on the down arrow button.</li>
      <li> For the "User" name remember it is "root" and for password it is "Password1" </li>
      <li> At the bottom click on "Open"  </li>
      <li> Right-click on "Unnamed", click on "Create new" and click on "Database" </li>
      <li> On the panel "Create database". Type "osTicket" on "Name". Click "Okay" </li>
    </ol> 
7. Continue Setting up osTicket Installer in the browser
     <ol type="a">
      <li> Go back to OSTicket Installer and click "Continue" at the bottom of the installation page</li>
      <li> Under System Settings, on "Helpdesk Name", & "Default Email",  type your desired name/email </li>
      <li> Under Admin User, type your desired "First Name", "Last Name", & "Email Address" </li>
      <li> For this Username use: user_admin & Password use: Password1 </li>
      <li> Under Database Settings, on "MySQL Database", "MySQL Username", & "MySQL Password" put the following info as:"OsTicket"(Name created from HeidiSQL), "root", (from), & "Password1"(from) </li>
- Note: Make sure you save this information on your notepad just in case if we need this info later on.
      <li> At the bottom click "Install Now"</li>  
      <li> If successful you should see the following display: </li>    
    </ol> 


<h2>Step 9: Navigate to the osTicket web interface and log-in using the administrator credentials</h2>

1. Before you navigate the osTicket web interface, we need to clean Up first.
     <ol type="a">
      <li> go back to osTicket Folder on File Explorer </li>
      <li> From "This PC" go to "inetpub, "wwwroot", and "osticket </li>
    <li> You should see the following display:  </li>
      <li> Right- click on "setup" and "Delete" it </li>
      <li> Inside of C:\inetpub\wwwroot\osTicket\include\ost-config.php reset the permissions back to ost-config.php</li>
      <li> Find "ost-config.php" and right click on it to "Properties"</li>
        <li> Go to Security</li>
        <li>under Permissions for Eveyone, click on "Advanced" </li>
        <li> click the following: " Allow Eveyone". Afterwards "Edit" </li>
        <li> See the following image: </li>
        <li> Uncheck the following: "Full control", "Modify", & "Write"</li>
        <li> click "Okay". Then click "Apply". Afterwards click "Okay". </li>
    </ol> 
    
2. Congrats, hopefully the Osticket app is installed with no errors!
     <ol type="a">
      <li> Browse to your help desk login page: http://localhost/osTicket/scp/login.php </li>
      <li> Type in your Email or Username/Password.(From Intruction D Step 8)</li>
      <li> Wallah! You should see the following:  </li>
      <li> Congrats of having it working!</li>
    </ol> 
