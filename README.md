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
- Ensure connectivity between the Client-1 and Domain Controller (DC-1)
- Install Active Directory
- Create an Admin and normal user account in Active Directory
- Join Client-1 to your Domain

<h2>Deployment and Configuration Steps</h2>

<p>
<a href="https://ibb.co/Twgtv8h"><img src="https://i.ibb.co/51RLM8c/Screen-Shot-2023-10-20-at-1-54-54-PM.png" alt="Screen-Shot-2023-10-20-at-1-54-54-PM" border="0" /></a>
</p>
<p>
To setup your resources in Azure, first create the Domain Controller VM (DC-1) with a Windows Server image application. Next, create the Client-1 VM with a Windows 10 OS and make sure you use the same resource group and Vnet that was created in step one during the creation the the Domain Controller (you can check the topology with Network Watcher). To ensure both run smoothly, select a VM size of at least 2 vcpus.
</p>
<br />

<p>
<a href="https://ibb.co/99g0VBY"><img src="https://i.ibb.co/fYFWnZ0/Screen-Shot-2023-10-20-at-2-14-55-PM.png" alt="Screen-Shot-2023-10-20-at-2-14-55-PM" border="0" /></a>
</p>

<p>
<a href="https://ibb.co/B2yK6PD"><img src="https://i.ibb.co/RT346Sn/Screen-Shot-2023-10-20-at-2-15-42-PM.png" alt="Screen-Shot-2023-10-20-at-2-15-42-PM" border="0" /></a>
</p>

<p>
To ensure connectivity between the Client-1 and DC-1, we are going to log in to to Client-1 with Remote Desktop and ping DC-1s Private IP Address with ping -t (IP Address). We'll notice that when we do this, the request times out. To fix this we need to log in to DC-1 with Remote Desktop and enable ICMPv4 on the local Windows Firewall. After doing this, check back at Client-1 to see the ping succeed.
</p>
<br />

<p>
<a href="https://ibb.co/VSYngs1"><img src="https://i.ibb.co/T8Mj4sf/Screen-Shot-2023-10-20-at-2-39-55-PM.png" alt="Screen-Shot-2023-10-20-at-2-39-55-PM" border="0" /></a>
</p>
<p>
To install Active Directory, log in to to DC-1 and open the Service Manager Dashboard and navigate to where it says "Add Roles and Features". From here, install Active Directory Domain Services. Next, promote this server to a Domain Controller by setting up a new forest with whatever domain name you choose. Restart and log back in to the DC-1 VM as your newly created domain user.
</p>
<br />

<p>
<a href="https://ibb.co/89dJ0CX"><img src="https://i.ibb.co/njnTbGR/Screen-Shot-2023-10-20-at-2-54-33-PM.png" alt="Screen-Shot-2023-10-20-at-2-54-33-PM" border="0" /></a>
</p>
<p>
In Active Directory Users and Computers (ADUC), create two new Organizational Units "Employees" and "Admins". Create a new employee, and add them to the Domain Admins Security Group. Log out of the Remote Desktop connection to the DC-1 VM and log back in with the newly created employees credentials.
</p>
