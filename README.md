<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket Help Desk Implementation</h1>
This tutorial will demonstrate how to build a help desk system using osTicket from scratch! This will also teach you how to set up the system and manage tickets<br/>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machine/Resource Group)
- Remote Desktop
- osTicket (open-source ticketing system)
- IIS (Internet Information Services)
<h2>Operating Systems Used </h2>

- Windows 10 Pro, version 21H2(free services eligible)</b> 

<h2>What You Will Learn</h2>

- Ticket Properties
- SLAs(Service Level Agreements)
- Departments
- Permissions
- Users

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: You need to authenticate and authorize yourself by logging into the Azure portal.
- Step 2: Create a Resource Group.
- Step 3: Create a virtual machine using Windows 10 Pro, version 21H2(free services eligible) and your desired specifications.
- Step 4: Configure remote access to the virtual machines, such as using Remote Desktop Protocol (RDP).
- Step 5: Install osTicket on the VM.
- Step 6: Configure the osTicket instance with the necessary settings, including email, database, and help desk settings.
- Step 7: Navigate to the osTicket web interface and log in using the administrator credentials.
- Step 8: Configure the help desk settings, including the department, email settings, and user accounts.
- Step 9: Set up the email integration by specifying the email server, email account credentials, and notification settings.
- Step 10: Test the help desk system by creating a test ticket and verifying that it is received and processed correctly.
- Step 11: Manage tickets by logging in to the osTicket web interface and viewing, replying to, and closing tickets as necessary.
- Step 12: Optionally, customize the osTicket instance by modifying the templates, themes, and other settings as desired.

<h2>Step 1: You need to authenticate and authorize yourself by logging into the Azure portal</h2>
 
1. Go to the Azure Portal website (https://portal.azure.com/) and sign-in with your Azure account credentials. (Note: If you do not have an Azure account, you will need to sign up for one before you can log-in.)

2. Once you have successfully authenticated, you will be redirected to the Azure portal dashboard where you can create and manage your resources. You should be able to see the following display:

<p>
<img src="https://i.imgur.com/zr0sGpt.png" height="80%" width="80%"/>
</p>
<p>  

<h2>Step 2: Create a Resource Group</h2>

1. Click on the "Seach resources, services, docs (G+/)" 

2. In the search bar, type "Research Groups"

3. Click on the "+ Create" button located on the right top corner by "Switch to classic".
    <ol type="a">
      <li>Choose your subscription.</li>
      <li>Create a name of your resource group.</li>
      <li>Choose a region to deploy the virtual machine to.</li>   
    </ol>

4. After, typing your desired specifications click on the box "Review + create" 

5. You should be able to see the following display:
<p>
<img src="https://i.imgur.com/lpBisFO.png" height="80%" width="80%"/>
</p>
<p>  
 
6. Then click "create"

- Note: By creating a Resource Group, you'll have a container to contain all your related resources in a single place.

<h2>Step 3: Create a virtual machine using Windows 10 Pro, version 21H2(free services eligible) and your desired specifications</h2>

1. Again, click on the "Seach resources, services, docs (G+/)"
2. In the search bar, type "Virtual Machines"
3. Click on the "+ Create" button located on the right top corner by "Switch to classic".
4. Choose the option "Azure virtual machine", enter the following information:
    <ol type="a">
      <li>Choose your subscription.</li>
      <li>Create a name for resource group(Use: RG-osTicket)</li>
      <li>Enter a unique name for the virtual machine(Use: vm-osticket)</li>
      <li>Choose the desired "region", "image", "size", "Username", "Password", "Public inbound ports", and "Select inbound ports"</li>
    </ol>

- Note: Here are the examples below of the specifications I used:
<p>
<img src="https://i.imgur.com/eXXnWIY.png" height="80%" width="80%"/>
</p>
<p>  
<p>
<img src="https://i.imgur.com/kXU9EyC.png" height="80%" width="80%"/>
</p>
<p>  
    
- Note: Remember to keep your username and password you created in your notes, as you will need them later.

5. Locate the check box at the bottom-left corner of the website and click "I confirm I have an eligible Windows 10/11 license with multi-tenant hosting rights. Please confirm.")

6. Click on the "Review + create" button and review the settings.

7. Click on the "Create" button to create the virtual machine. (Note: It should take up 1-2 minutes to process the VM)

8. Once the virtual machine Windows 10 Pro (21H2) is created, you can access it through the Azure portal or by using remote desktop tools.

<h2>Step 4: Configure remote access to the virtual machines, such as using Remote Desktop Protocol (RDP)</h2>

1. Click on the "Seach resources, services, docs (G+/)"

2. In the search bar, type "Virtual Machines"

3. After creating your VM, you should be able to click "vm-osticket"

4. On the "Overview" tab, find/copy the Public IP Address located within the Essentials category.

- Note: See the image below: 

<p>
<img src="https://i.imgur.com/k30oAxe.png" height="80%" width="80%"/>
</p>
<p>  

5. For Windows users click the "Start" Button (Windows logo) located at the bottom-left corner and search for "Remote Desktop Connection". (Note: For Mac Users download the app "remote- Microsoft Remote Desktop" from the App Store.)

6. Paste the Public IP Address on the computer name field and click "Connect". (Note: For Mac User's paste the IP Address on "PC-name" and click "add")

7. Afterwards make sure to log-in your user's/password's creditial from Step 3. (Ex: Username: labuser/Password: Your unique password).

- Note: For Windows Users click "yes" to connect to the remote computer. Observe the following display:
 
<p>
<img src="https://i.imgur.com/xHG3t9h.png" height="80%" width="80%"/>
</p>
<p>  
 
8. Choose the options for "Choose privacy settings for your device": 
    <ol type="a">
      <li>Location: No </li>
      <li>Diagnostic Data: No</li>
      <li>Tailored experiences: No</li>
      <li>Find my device: No</li>
     <li>Inking and Typing: No</li>
     <li>Advertising ID: No</li>
    </ol>

9. Click "Accept"

<h2>Step 5: Install osTicket on the VM</h2>

1. Install/Enable CGI on IIS. Do the following: 
    <ol type="a">
      <li>Right click the "Start" Button (Windows logo) and click "Run"</li>
      <li>Type "control" for control panel</li>
      <li>Under "Programs and features", click "Turn Windows features on or off"</li>
      <li>Turn on "Internet Information Services" by checking the box next to it.</li>
     <li>Expand IIS and click on "World Wide Web Services" </li>
     <li>Under WWWS, expand "Application Development Features"</li>
      <li>Turn on "CGI" by clicking the check box next to it.</li>
      <li>Click "Okay"</li>
       <li>After the installation is complete make sure to close it.</li>
       <li>Now, open up Microsoft Edge and type on the URL "127.0.0.1 (To verify your webserver is up & running"</li>
    </ol>

- Note by Installing/Enabling CGI on IIS, it lets you provide the necessary infrastructure for OSTicket to function correctly. Without CGI, the application would not work properly

2. Download/Install PHP Manager for IIS  
    <ol type="a">
      <li>Download PHP Manager from the following link: https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view </li>
      <li>After downloading PHP Manager, go to File Explorer</li>
      <li>Double click "PHPManagerForIIS_V1.5.0 from the "Download" section</li>
      <li>By double clicking the program, you should be able to complete the instalation after accepting the License Agreement</li>
    </ol>
- Note: You need to download and install PHP Manager for IIS when using osticket system because it simplifies the process of installing and configuring PHP on IIS, which is required for osticket to run properly
