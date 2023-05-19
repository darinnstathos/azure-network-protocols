<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1: Create a Resource Group in Microsoft Azure, 1 Virtual Machine for Microsoft Windows, 1 Virtual Machine for Linux Ubuntu
- Step 2: Connect the Micrsoft Windows VM via Remote Desktop Connection
- Step 3: Download and Install Wireshark through the Windows VM
- Step 4: Observe ICMP in Wireshark & Open the command line in Windows (Powershell) and ping/connect to Linux Ubuntu VM
- Step 5: Test out various other networking protocols (SSH, RDP, DNS, HTTP/S, ICMP)

<h2>Actions and Observations</h2>

<h3>Create Resource Group and Virtual Machines: Windows & Linux</h3>

<Strong>What are Resource Groups?</strong>
<p>Resource groups in Microsoft Azure are containers that help manage and organize related Azure resources. They provide a logical grouping for resources, such as virtual machines, storage accounts, and networks, allowing administrators to manage, monitor, and apply policies to the resources collectively.</p>

<Strong>What are Virtual Machines?</Strong>
<p>Virtual machines, in simple terms, are like computers within computers. They are software emulations of physical computers that allow you to run multiple operating systems or applications on a single physical machine. Virtual machines provide flexibility, allowing you to create and use different environments or systems without the need for separate physical hardware.</p>

<h4>Creating our Resource Group & Microsoft Windows Virtual Machine</h4>
1. Within Microsoft Azure, navigate to 'Resource Groups' via the search bar or quick access icon. Select 'Create Resource Group'
2. For this example, we'll name the Resource Group: "RG-NSGP" (ResourceGroup--NetworkSecurityGroupsProtocol)
3. It is recommended to place it the Resource Group in the United States (Example: (US) West US 3)
4. There is nothing left for us to alter so select 'Review + Create'

<p>Now that the Resource Group has been created, we can now place both our Virtual Machines (Windows & Linux Ubuntu) inside of it. First, we will create our Windows Virtual Machine.</p>

5. Within Azure, naviagte to 'Virtual Machines' via the search bar or quick access icon. Select 'Create Virtual Machine'
6. Next to ‘Resource Group’, we want to select the Resource Group we just created: "RG-NSGP"
7. VM Name: 'VM1-Windows', Operating System Image: ‘Windows 10 Pro, version 22H2 - x64 Gen2', Size: 2vcpus (anything above 1vcpu will allow the VM to run efficiently. Otherwise, it'll be slow and lag.)
8. Create a username and password. We will be asked for this later when connecting to our VM via Remote Desktop Connection. 
9. Select the blue check mark under licensing: 'I confirm I have an eligible Windows 10/11 license with multi-tenant hosting rights.’
10. There is nothing to change here, but take notice on how Azure automatically assigned/created a Virtual Network. In this case, it is named ‘(new) VM1-Windows-vnet’. When creating our Linux Virtual Machine, we’ll want to make sure it is also on this same network so that our two Virtual Machines are under one network and can communicate with one another.
11. Select 'Review + Create'

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h4>Creating our Linux Ubuntu Virtual Machine</h4>
1. Azure > naviagte to 'Virtual Machines' via the search bar or quick access icon. Select 'Create Virtual Machine'
2. Next to 'Resource Group', we want the Resource Group created previously: "RG-NSGP"
3. VM Name: 'VM2-Linux', Operating System Image: 'Ubuntu Server 20.04 LTS -x64 Gen2', Size: 2vcpu
4. Under ‘Administrator Account’, instead of selecting ‘SSH’, we want to select ‘Password’ and create a username and password again. This username and password will be necessary when we access this Linux command line from our Windows VM
5. We’ll forward from ‘Next: Disks >’ and then to ‘Next: Networking >’: 

We can see that we have the same virtual network as our Microsoft Windows VM. Again, this allows for our Virtual Machines to better communicate with one another as they are now on the same network
6. There is nothing left to alter so we will select ‘Review + Create’ and ‘Create’

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>












<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
