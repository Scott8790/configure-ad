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
<img width="1186" alt="ADlab2" src="https://github.com/Scott8790/configure-ad/assets/172638339/d607e0d4-a9d8-4532-b593-e04baf8e9751">


</p>
<p>
On DC-1 firewall setting, allow ICMPv4 traffic to come in. This allows you to ping the DC private IP from the client VM to ensure connectivity. Ping will not work unless you enable these two rules in the DC firewall settings
</p>
<br />

<p>
<img width="745" alt="ADlab3" src="https://github.com/Scott8790/configure-ad/assets/172638339/5a5d2cfb-bc45-476f-803d-01db3e85ada4">


</p>
<p>
On DC-1 open server manager and click add roles and features. Make sure to have the correct AD selected and follow all the on-screen prompts to begin the installation 
</p>
<br />

<p>
<img width="651" alt="ADlab4" src="https://github.com/Scott8790/configure-ad/assets/172638339/2567480b-f46d-4a1a-a17b-5a969a5f4ece">

</p>
<p>
Create two Organizational Units (OUs): One called employees and the other admins. Then create a new admin user. Log out and log back in as the new admin user.
</p>
<br />

<p>
<img width="626" alt="ADlab5" src="https://github.com/Scott8790/configure-ad/assets/172638339/10d9f089-7b5c-4d39-825c-0e5fbdbf54ff">

</p>
<p>
From Azure portal, go into client 1 DNS settings and change the DNS to the private IP of the DC. This way client 1 will not confuse the domain with another random one.
</p>
<br />

<p>
<img width="876" alt="ADlab6" src="https://github.com/Scott8790/configure-ad/assets/172638339/02dee5ee-af97-454f-b227-faecdd9ee6aa">

</p>
<p>
From client-1, join the DC by renaming the PC to the domain created with the DC-1 VM. Then sign in using an admin account created previously
</p>
<br />

<p>
<img width="880" alt="ADlab7" src="https://github.com/Scott8790/configure-ad/assets/172638339/e5c60e14-a9d5-4adf-95ef-ca10ef685e14">

</p>
<p>
Setup remote desktop access for any user on the DC to connect to client-1
</p>
<br />

<p>
<img width="591" alt="ADlab8" src="https://github.com/Scott8790/configure-ad/assets/172638339/d342084b-f1d0-475c-8abe-b16d2e170c2b">

<img width="597" alt="ADlab9" src="https://github.com/Scott8790/configure-ad/assets/172638339/95cb5912-5bac-426f-bd8d-521e7b4bb6ec">

<img width="432" alt="ADlab10" src="https://github.com/Scott8790/configure-ad/assets/172638339/070b65d1-bca4-4a85-9d89-18e65689d0cf">




</p>
<p>
Login to DC-1 as jane_admin, open PowerShell as admin, create a new file, paste the user-creating script, click run, and watch the accounts created. Then attempt to log in as one of the newly created users.
</p>
<br />
