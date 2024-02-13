<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Setup Resource Group
- Step 2: Ensure Connectivity between the client and Domain Controller 
- Step 3: Install Active Directory 
- Step 4: Create an Admin and Normal User Account in AD
- Step 5: Join Client-1 to your domain (mydomain.com)
- Step 6: Setup Remote Desktop for non -administrative users on Clients-1
- Step 7: Create a bunch of additional users and attempt to log into client-1 with one of the users
- Step 8: Finish.

<h2>Setup Resource Group</h2>

To begin, create a Domain Controller VM (Windows Server 2022) named "DC-1," noting the Resource Group and Virtual Network created. Set the Domain Controller's NIC Private IP address to static.

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/94bfb1b3-42eb-4601-9815-f1c640d58ca1)

Next, create a Client VM (Windows 10) named "Client-1" using the same Resource Group and Vnet from Step 1, ensuring both VMs are in the same Vnet, and verify the topology using Network Watcher.

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/5ee05b7c-6552-4102-bb46-00d5c4777348)

After you have created the second VM, we will set the Domain Controller's NIC Private IP address to static by selecting our DC-1 VM. Then we will select Networking in the settins tab and then we will click on the Network Interface link. 

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/6b83bc1c-5649-46eb-9874-6d9440750557)

Then we will selcet IP Configurations in the settings tab and click on ipconfig1 to bring up the edit IP Configuration window. From there we change the Priivate IP Address settings from dynamic to static and hit save. 

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/9ea2ed9d-9d6e-487e-86cb-8e5f96d30721)

<h2>Ensure Connectivity between the client and Domain Controller</h2>

To sure we have ensured connectivity between client and Domain Controller, we will login to Client-1 and ping DC-1 IP Address with ping -t (propetual ping)

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/7fc55150-0117-4793-b252-67d657c48d75)

We can see that we have time out of our ping request. DC-1 may have a firewall up that is blocking ICMPv4 traffic.

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/0a1cf864-dac7-41d6-a939-870904489870)

Now we will login to the Domain Controller and enable ICMPv4 in on the local windows Firewall

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/7c6e47e2-00c2-4a18-b4c1-8fe685974c63)

Now we can check back at Client-1 to see the ping succeed

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/055bf996-a59c-47f8-a0f7-6b192ef8a9e1)

<h2>Install Active Directory</h2>

Log back into DC-1 and install Active Directory Domain Services

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/82c5019a-5aee-471a-92e4-877912cf4aac)

Clicking the exclamation mark at next to the flag at the top of the page, we will promote the server to a domain controller and setup a new forest as mydomain.com (can be anything, just remember what it is)

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/e6b85216-5834-4e26-8359-5c7c751be7c9)

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/5958bb9b-4d50-4e70-925f-114c5a337ebb)

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/a209b4c1-2b84-4dcc-84f6-2636021c6cda)

After it finishes installing it will restart and I will log back into DC-1 as user: kobeb.com\Tstew5108

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/f932cad4-0445-4113-ad0a-ecc455038f9d)

<h2>Create an Admin and Normal User Account in AD</h2>

In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES” and "_ADMINS"

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/c8e0c014-895d-4245-9d4d-a630bad7327e)

Now lets create a new employee named “Jane Doe” (same password) with the username of “jane_admin” and then add jane_admin to the “Domain Admins” Security Group. Log out/close the Remote Desktop connection to DC-1 and log back in as “kobeb.com\jane_admin”

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/0d4937e4-a02d-4c9f-bc00-aca66be03254)

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/68555c0e-6421-4c63-86e8-8aedc81c1b85)

<h2>Join Client-1 to your domain (kobeb.com)</h2>












 




















