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

<h3>1. Setup Resources In Azure</h3>
<p>
<img src="https://i.imgur.com/Hkeszlp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once you created your resource group "AD-lab" you'll begin to create your Domain Controller VM. Take note of the vnet created with AD lab for the domain controller needs to have the same vnet. 
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
<img src="https://i.imgur.com/gki4y0C.png" height="100%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now create the Client VM using the same resource group and same vnet. 
</p>
<br />

<h3> 2. Ensure connectivity between client and domain controller</h3>
<p>
<img src="https://i.imgur.com/MMuw8Wz.png" height="100%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We now need to ensure connectivity between client-1 and the domain controller. Once you log into client-1 and ping DC private address you'll notice it fails. From there you will log into DC-1 using remote desktop connection and in the search bar once logged in type in "wf.msc" and click on inbound rules and enable ICMPv4. Now you'll see successful connectivity.
</p>
<br />

<h3>3. installing Active Directory</h3>
<p>
<img src="https://i.imgur.com/8g3vsmL.png" height="100%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
In DC you will click on "add roles and features" and install active directory services. Upon successful completion notice the yellow caution sign once it finishes downloading. You'll click that and it will have an option saying to promote this server to a domain controller. Setup a new forest as "mydomain.com". It will then restart and you will login DC-1 as ther user "mydomain.com/labuser"
</p>
<br />

<h3>4. Create an Admin & Normal user account in AD</h3>

<p>
<img src="https://i.imgur.com/W2VDluw.png" height="100%" width="80%" alt="Disk Sanitization Steps"/>

<p>
In active directory users and computers were going to create some organizational units.

<ul>
  <li>Create an organizationl unit called "_EMPLOYEES"</li>
  <li>Create an organizational unit called "_ADMIN"</li>
</ul>
</p>
<br />

<p>
<img src="https://i.imgur.com/joTFOSE.png" height="100%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create an employee named "jane doe" (same password) wiht username of "jane_admin"
  <ul>
    <li>add jane_admin to "domain admins" Security Group by rick clicking on jane doe and clicking "add to group" and putting it in domain admins and check the name.</li>
    <li>logout/close remote desktop connection to DC-1 and log back in as "mydomain.com\jane_admin"</li>
    <li>Use jane_admin as your admin account from now on</li>
  </ul>
</p>
<br />

<h3>5. Join Client-1 to your domain</h3>
<p>
<img src="https://i.imgur.com/BCR5TE8.png" height="100%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From Azure portal set client 1's DNS settings to DC-1's private IP address, after restart client-1.

  <ul>
    <li>Login to client-1 as the original local admin (labuser)</li>
    <li>Go to settiings</li>
    <li>Rename this pc (advanced)</li>
    <li>change</li>
    <li>use user/password used for jane_admin</li>
  </ul>
</p>

<p>
<img src="https://i.imgur.com/qiwqNTC.png" height="100%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Login to DC-1 to verify client-1 shows up in the active directory users and computers in the "computers" folder.
  <ul>
    <li>create a new OU named "_CLIENTS" and drag client-1 into that folder </li>
  </ul>
</p>
<br />
