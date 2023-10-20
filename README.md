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

- Setup resources in Azure
- Ensure connectivity between the Client and Domain Controller
- Install Active Directory
- Create an Admin and normal user account in Active Directory
- Join Client-1 to your Domain

<h2>Deployment and Configuration Steps</h2>

<p>
<a href="https://ibb.co/Twgtv8h"><img src="https://i.ibb.co/51RLM8c/Screen-Shot-2023-10-20-at-1-54-54-PM.png" alt="Screen-Shot-2023-10-20-at-1-54-54-PM" border="0" /></a>
</p>
<p>
To setup your resources in Azure, first create the Domain Controller VM with a Windows Server image application. Next, create the Client VM with a Windows 10 OS and make sure you use the same resource group and Vnet that was created in step one during the creation the the Domain Controller (you can check the topology with Network Watcher). To ensure both run smoothly, select a VM size of at least 2 vcpus.
</p>
<br />

<p>
<a href="https://ibb.co/99g0VBY"><img src="https://i.ibb.co/fYFWnZ0/Screen-Shot-2023-10-20-at-2-14-55-PM.png" alt="Screen-Shot-2023-10-20-at-2-14-55-PM" border="0" /></a>
</p>

<p>
<a href="https://ibb.co/B2yK6PD"><img src="https://i.ibb.co/RT346Sn/Screen-Shot-2023-10-20-at-2-15-42-PM.png" alt="Screen-Shot-2023-10-20-at-2-15-42-PM" border="0" /></a>
</p>

<p>
To ensure connectivity between the Client and Domain Controller, we are going to login to Client-1 with Remote Desktop and ping DC-1s Private IP Address with ping -t (IP Address). We'll notice that when we do this, the request times out. To fix this we need to login to the Domain Controller with Remote Desktop and enable ICMPv4 on the local Windows Firewall. After doing this, check back at Client-1 to see the ping succeed.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To install Active Directory, login to Domain Controller and open the Service Manager Dashboard and navigate to where it says "Add Roles and Features". From here, install Active Directory Domain Services.
</p>
<br />
