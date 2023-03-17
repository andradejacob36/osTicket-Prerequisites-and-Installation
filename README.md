<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket Help Desk Implementation</h1>
This tutorial will demonstrate how to build a help desk system using osTicket(From Scratch!). This will also teach you how to set up the system and manage tickets<br/>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- osTicket (open-source ticketing system)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)   (Edit Later)

<h2>Ticket Lifecycle Stages</h2>

- Intake
- Assignment and Communication
- Working the Issue
- Resolution

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: You need to authenticate and authorize yourself by logging into the Azure portal.
- Step 2: Create a virtual machine using the Windows Server 2022 and Windows 10(Edit later). Set up the VMs with the desired specifications.
- Step 3: Configure the VM settings, including size, region, and security rules.
- Step 4: Configure remote access to the virtual machines, such as using Remote Desktop Protocol (RDP).
- Step 5: Install osTicket on the VM instance using the command-line interface.
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

<h2>Step 2: Create a virtual machine using the Windows Server 2022 and Windows 10(Edit later). Set up the VMs with the desired specifications</h2>

1. Click on the "Seach resources, services, docs (G+/)" located next to "Upgrade".
2. In the search bar, type "Virtual Machine".
3. Click on the "+ Create" button located on the right top corner by "Switch to classic". (Edit: Picture)
4. Choose the option "Azure virtual machine", enter the following information:

    <ol type="a">
      <li>Choose your subscription(Ex:).</li>
      <li>Create a name for resource group, where all your VMs, storage accounts, and virtual networks will be located at. (Ex:) </li>
      <li>Enter a unique name for the virtual machine(You can call it VM). (Ex:)</li>
      <li>Choose a region to deploy the virtual machine to. (Ex:)</li>
      <li>Choose the desired "image" and "size" (Ex:)</li>
      <li>Choose the desired "Username", "Password", "Public inbound ports", and "Select inbound ports" (Ex: ).</li>     
    </ol>
    
- (Note: Here is an example of the specifications I am using(Edit Picture) . Also, once you finish before you do Step 6 make sure to check the box: "I confirm I have an eligible Windows 10/11 license with multi-tenant hosting rights. Please confirm.")

5. Click on the "Review + create" button and review the settings.
6. Click on the "Create" button to create the virtual machine. (Note: It should take up 1-2 minutes to process the VM)
7. Repeat steps 2-6 for creating Windows 10 (21H2) virtual machine.
- Once the virtual machines(Windows Server 2022 and Windows 10 (21H2)) are created, you can access them through the Azure portal or by using remote desktop tools.
