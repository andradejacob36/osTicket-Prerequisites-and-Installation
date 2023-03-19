<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket Help Desk Implementation</h1>
This tutorial will demonstrate how to build a help desk system using osTicket(From Scratch!). This will also teach you how to set up the system and manage tickets<br/>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- osTicket (open-source ticketing system)

    <ol type="a">
      <li> Ticket Properties</li>
      <li> SLAs(Service Level Agreements)</li>
      <li> Departments</li>
      <li> Permissions</li>
      <li> Users</li>
    </ol>

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2) 

<h2>Ticket Lifecycle Stages</h2>

- Intake
- Assignment and Communication
- Working the Issue
- Resolution

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: You need to authenticate and authorize yourself by logging into the Azure portal.
- Step 2: Create a Resource Group.
- Step 3: Create a virtual machine using Windows 10 Pro, version 21H2(free services eligible).
- Step 4: Configure the VM settings, including size, region, and security rules.
- Step 5: Configure remote access to the virtual machines, such as using Remote Desktop Protocol (RDP).
- Step 6: Install osTicket on the VM instance using the command-line interface.
- Step 7: Configure the osTicket instance with the necessary settings, including email, database, and help desk settings.
- Step 8: Navigate to the osTicket web interface and log in using the administrator credentials.
- Step 9: Configure the help desk settings, including the department, email settings, and user accounts.
- Step 10: Set up the email integration by specifying the email server, email account credentials, and notification settings.
- Step 11: Test the help desk system by creating a test ticket and verifying that it is received and processed correctly.
- Step 12: Manage tickets by logging in to the osTicket web interface and viewing, replying to, and closing tickets as necessary.
- Step 13: Optionally, customize the osTicket instance by modifying the templates, themes, and other settings as desired.

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

5. You should be avaible to see the following display:
<p>
<img src="https://i.imgur.com/lpBisFO.png" height="80%" width="80%"/>
</p>
<p>  
 
6. Then click "create"

- Note: By creating a Resource Group, you'll have a container to contain all your related resources in a single place.

<h2>Step 3: Create a virtual machine using Windows 10 Pro, version 21H2(free services eligible)</h2>

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
    
5. Before you move on to Step 6, Locate the check box at the left-lower corner of the website and click "I confirm I have an eligible Windows 10/11 license with multi-tenant hosting rights. Please confirm.")

6. Click on the "Review + create" button and review the settings.

7. Click on the "Create" button to create the virtual machine. (Note: It should take up 1-2 minutes to process the VM)

8. Once the virtual machine Windows 10 Pro (21H2) is created, you can access it through the Azure portal or by using remote desktop tools.
