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

- Setup Resources in Azure
- Ensure Connectivity between the client and Domain Controller (DC)
- Install Active Directory (AD)
- Create an Admin & Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on client-1
- Create a bunch of additional users & attempt to log into client-1 with one

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="1874" alt="ADlab1" src="https://github.com/Scott8790/configure-ad/assets/172638339/390a31fc-5458-4814-bdf3-b8818450bc1b">

</p>
<p>
Create two VMs within the same resource group. One VM is the domain controller and the other is the client VM that will access the DC. Make sure both VMs share the same private IP address and that the DC private IP is set to static so it will not change
</p>
<br />

<p>
<img width="1567" alt="ADlab2" src="https://github.com/Scott8790/configure-ad/assets/172638339/24bf438f-e646-47c8-ab94-131b77a4c140">

</p>
<p>
On DC-1 firewall setting, allow ICMPv4 traffic to come in. This allows you to ping the DC private IP from the client VM to ensure connectivity. Ping will not work unless you enable these two rules in the DC firewall settings
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
