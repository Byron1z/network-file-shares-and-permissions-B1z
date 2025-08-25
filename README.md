<p align="center">
<img src="https://i.imgur.com/AeiqMDZ.png" alt="Traffic Examination"/>
</p>

<h1>Network File Shares and Permissions in the Cloud (Azure)</h1>
<p>
  In this tutorial, we'll learn about Network File Shares and Permissions. Network File Shares is a way for users to access another computer’s folder over the Network. And users can assign different permissions to other users or groups.

  For this Lab, we’ll utilize the installation of the Active Directory lab.
</p>
<br />

<h2>Software and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Domain Controller/Client Machine)
- Remote Desktop
- Active Directory Users and Computers (ADUC)
- Shared Network Files

<h2>Operating Systems Used </h2>

- Windows Server (2022)
- Windows 10 Pro</b> (22H2)

<h2> What is Network File Shares & Permissions</h2>
<p>
  <img src="https://i.imgur.com/eL7VqU9.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
</p>
<p>
Network File Shares is a way for users to access another computer’s folder over the Network. And users can assign different permissions to other users or groups.
  
For this Lab, we’ll utilize the installation of the Active Directory lab.
</p>
<h2>When might we use File Share</h2>
<p>
  <img src="https://i.imgur.com/EKaUOTR.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
</p>
<br />
<h2>Create some sample file shares with various permissions</h2>
<p>
  1. Connect/log into "DC-1" as your Domain Admin account (mydomain.com\jane_admin)
  
  2. Connect/log into "Client-1" as a Normal User (mydomain\<someuser>) – (biv.fim)

  3. On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting”.

     For this lab, these folders will be named to the specific tasks and access we’ll be providing these folders.
</p>
<p>
  <img src="https://i.imgur.com/wYS7Ok7.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
</p>
<p>
  4. Set the following permissions (share the folder) 
</p>


