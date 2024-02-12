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
- Step 2: Ensurew Connectivity between the client and Domain COntroller 
- Step 3:  Install Acrtive Directory 
- Step 4: Create an Admin and Normal User Account in AD
- Step 5: Join Client-1 to your domain (mydomain.com)
- Step 6: Setup Remote Desktop for non -administrative users on Clients-1
- Step 7: Create a bunch of additional users and attempt to log into client -1 with one of the users
- Step 8: Finish. 

<h2>Deployment and Configuration Steps</h2>


First, create a Domain Controller VM (Windows Server 2022) named "DC-1," noting the Resource Group and Virtual Network created. Set the Domain Controller's NIC Private IP address to static. Next, create a Client VM (Windows 10) named "Client-1" using the same Resource Group and Vnet from Step 1, ensuring both VMs are in the same Vnet, and verify the topology using Network Watcher.

![image](https://github.com/Tstewart2408/Configure-Ad/assets/158493074/e3912d89-f028-4f8a-a0a6-891175232f77)







