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
- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin User in Active Directory
- Join Client-1 to the domain
- Setup Remote Desktop for non-administrative users on Client-1

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/jRBF117.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Inside Azure, create two virtual machines; one, our domain controller (DC-1), as a windows server and the other (Client-1) as windows 10. Create both under the same resource group and virtual network.
</p>
<br />

<p>
<img src="https://i.imgur.com/U6snyrO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Enable ICMPv4 traffic through DC-1's firewall, then ping DC-1 on Client-1's command prompt to ensure connectivity between both machines.
</p>
<br />

<p>
<img src="https://i.imgur.com/n5ykCTe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On DC-1, Install Active Directory Domain Services through Windows 10 server manager.
</p>
<br />

<p>
<img src="https://i.imgur.com/rgshFrj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a new user in Active Directory, assign "Domain Admin" security group, and then log in with this user.
</p>
<br />

<p>
<img src="https://i.imgur.com/hqpAgJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Azure, set Client-1's DNS server to DC-1's private IP address; restart Client-1.
</p>
<br />

<p>
<img src="https://i.imgur.com/Io6I52r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From Client-1, join DC-1's domain and log in with the domain admin user.
</p>
<br />

<p>
<img src="https://i.imgur.com/1JDS4rw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On Client-1, go to system properties/remote desktop and add "Domain Users". This enables non-admin users to log into Client-1.
</p>
<br />

<p>
<img src="https://i.imgur.com/dij8f6h.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
For the fun of it, on DC-1 I ran a script in Powershell ICE to create 10,000 users. 
</p>
<br />

<p>
<img src="https://i.imgur.com/nMewvJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Logging into one of the random users created.
</p>
<br />

<p>
<img src="https://i.imgur.com/R2IEoHR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now you have a domain with 10,000 users! With only 2 computers in the domain...
</p>
<br />
