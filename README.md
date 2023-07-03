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



<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/Hkeszlp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once you created your resource group p"AD-lab" you'll begin to create your Domain Controller VM. Take note of the vnet created with AD lab for the domain controller needs to have the same vnet. 
</p>
<br />

<p>
<img src="https://i.imgur.com/aO8889M.png" height="100%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Set the domain controllers NIC (network interface card) IP address from private to static. To do so, navigate to DC's vm & click networking and where you see "network interface" you'll click that. 
</p>
<br />

<p>
<img src="https://i.imgur.com/v6c3DM1.png" height="100%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The left side with the navigational list you'll see "IP configuration" once you click that option you can then proceed to click the name & change the domain controller's IP address from private to static. 
</p>
<br />

<p>
<img src="" height="100%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now create the Client VM using the same resource group and same vnet. 
</p>
<br />

<p>
<img src="" height="100%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we need to ensure connectivity between client-1 and the domain controller. First, we need to login to client-1 and ping DC's private address. Notice once you ping the DC's IP address it will keep replying.
</p>
<br />

<p>
<img src="" height="100%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

