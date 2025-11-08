<p align="center">
<img src="https://i.imgur.com/AeiqMDZ.png" alt="Traffic Examination"/>
</p>

<h1>Network File Shares and Permissions in the Cloud (Azure)</h1>
<p>
  In this tutorial, we'll learn about Network File Shares and Permissions. Network File Shares is a way for users to access another computer’s folder over the Network. And users can assign different permissions to other users or groups.

  For this Lab, we’ll utilize the installation of the Active Directory lab.
</p>
<br />

<h2>💻⚙️ Software and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Domain Controller/Client Machine)
- Remote Desktop
- Active Directory Users and Computers (ADUC)
- Shared Network Files

<h2>💻 Operating Systems Used</h2>

- **Windows Server (2022)**
- **Windows 10 Pro</b> (22H2)**

<h2> What is Network File Shares & Permissions</h2>
<p>
  <img src="https://i.imgur.com/eL7VqU9.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
Network File Shares is a way for users to access another computer’s folder over the Network. And users can assign different permissions to other users or groups.
  
For this Lab, we’ll utilize the installation of the Active Directory lab.
</p>
<br />

<h2>How are File Permissions enforced in a Network environment?</h2>
<p>

  File Permissions in a network environment are enforced by the operating system and network protocols. When a user attempts to access a file, the system checks the user's permissions against the file's **Access Control List (ACL)**. 
  
  If the user has the necessary permissions, access is granted; otherwise, it is denied. This process ensures that only authorized users can access or modify files, maintaining security and data integrity
</p>
<br />
<h2>When might we use File Share</h2>
<p>
  <img src="https://i.imgur.com/EKaUOTR.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h2>📂 Create some sample File Shares with various Permissions</h2>
<p>
  
  1. Connect/log into "DC-1" as your Domain Admin account (mydomain.com\jane_admin)
  
  2. Connect/log into "Client-1" as a Normal User (mydomain\<someuser>) – **(*biv.fim*)**

  3. On DC-1, on the C:\ drive, create 4 folders: “**read-access**”, “**write-access**”, “**no-access**”, “**accounting**”.

     For this lab, these folders will be named to the specific tasks and access we’ll be providing these folders.
</p>
<p>
  <img src="https://i.imgur.com/wYS7Ok7.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

  4. Set the following permissions (share the folder) from DC-1. 

  Go to the location of the folder, right-click, **Properties -> Sharing -> Share...**, then type the name of the group you want to give File Permissions. 

  a. Folder: “**read access**”, Group: “Domain Users”, Permission: “Read”
</p>
<p>
  <img src="https://i.imgur.com/gjKHbvd.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

  b. Folder: “**write-access**”, Group: “Domain Users”, Permissions: “Read/Write” 
</p>
<p>
  <img src="https://i.imgur.com/7SMSzyx.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

  c. Folder: “**no-access**”, Group: “**Domain Admins**” (Not Domain Users❗️), “Permissions: “Read/Write” 
</p>
<p>
   <img src="https://i.imgur.com/5c58CBu.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
  For this folder, only Domain Admins will have access, not Domain Users. Here's why by answering the question "What are the risks of sharing folders with Domain Users?".

  Sharing folders with Domain Users can expose sensitive data to a large group of people, increasing the risk of unauthorized access or data breaches. It is important to carefully manage permissions and only grant access to users who need it for their work. Additionally, auditing and monitoring access can help detect and prevent misuse of shared resources.
  
  d. (Skip "accounting" folder for now)
</p>
<br />

<h2>🟢 Attempt to access File Shares as a Normal User from Client-1</h2>
<p>
   5. On Client-1, navigate to the shared folder (start, run, \\dc-1) 
</p>
<p>
  <img src="https://i.imgur.com/tJv6M5S.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/ouMEknQ.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

  6. Try to access the folders you just created. Which folders can you access? Which folders can you create stuff in? Does it make sense?

  For the "**Read-Access**" Folder, Domain Users are only allowed to view, not to create or modify.
</p>
<p>
  <img src="https://i.imgur.com/kAPHvLn.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

  For the "**Write-Access**" Folder, Domain Users are allowed to view, write, or create files on the Write-Access folder.
</p>
<p>
  <img src="https://i.imgur.com/Ti6A8zr.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

  And for the "**No-Access**" folder, as a Domain User (not a Domain Admin), we’re not allowed to view or open it entirely.
</p>
<p>
  <img src="https://i.imgur.com/wq8YTk9.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h2>🔵 Create an “ACCOUNTANTS” Security Group, assign Permissions, and test Access</h2>
<p>
  7. Go back to DC-1, in Active Directory Users & Computers (ADUC), create a security group called “ACCOUNTANTS”.
</p>
<p>
  <img src="https://i.imgur.com/lZzjbR2.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/IrBtCfC.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/c6ehk25.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
  8. On the “Accounting” folder that was created earlier, set the following permissions: 

  a. Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write” 
</p>
<p>
  <img src="https://i.imgur.com/JiPGT05.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
 9. On Client-1, log in as (someuser), try to access the "Accounting" folder. It should fail.
</p>
<p>
  <img src="https://i.imgur.com/N5mz0LZ.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
  10. Log out of Client-1 as (someuser). 

  11. Go back to DC-1, make that same someuser (biv.fim) a member of the “ACCOUNTANTS” Security Group.
</p>
<p>
   <img src="https://i.imgur.com/CME8hf6.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/wrD94cF.png" height="100%" width="90%" alt="Disk Sanitization Steps"/>
</p>
<p>
  12. Sign back into Client-1 as (biv.fim) and try to access the “accounting” folder share in
\\DC-1\ - Does it work now?

  Yes it works now, Domain User "biv.fim" now has access to the "Accounting" folder.
</p>
<p>
  <img src="https://i.imgur.com/hHyv6Nq.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<br />
<p>
  You can finally delete the VMs if you are done with the lab or keep using them for practice!
</p>



