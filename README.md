<h1>Active Directory Home Lab</h1>

<h2>Description</h2>
(Documentation in progress) 

In this project, I installed Active Directory on a Windows Server 2025 Virtual Machine. I assigned two network adapters to the domain controller to allow a Client virtual machine, running windows 11, to connect to the Domain Controller through remote access. I also set up DHCP on the domain controller to allow the client network to automatically be assigned an IP address. 
<br />


<h2>Utilities Used</h2>

- <b>Oracle Virtual Box</b> 

<h2>Environments Used </h2>

- <b>Windows 11</b>
- <b>Windows Server 2025</b>

<h2>Project Diagram:</h2>
<p align="center">
<img src="https://imgur.com/LnA97bk.png" height="80%" width="80%" alt="Home Lab Diagram"/>

<p align="center">

<h2>Project walk-through:</h2>

<p align="center">
Install and Launch Virtual Box: <br/>
<img src="https://imgur.com/KfyUXDH.png" height="80%" width="80%" alt="Virtual box landing page"/>
<br />
<br />
Create a new Virtual Machine and configure settings:  <br/>
<img src="https://imgur.com/TNxihu3.png" height="80%" width="80%" alt="VM Creation Prompt"/>

- Important Settings: 4 Cores, 4GB Ram, 1 NAT Adapter, 1 Internal Network Adapter
  
<br />
<br />
<p align="center">
Run the VM, Follow Windows Server Installation Prompts, Sign In: <br/>
<img src="https://imgur.com/qNLDvEh.png" height="80%" width="80%" alt="Windows Server Desktop on First Sign In"/>

- This is the screen that you will be met with once installation and sign in are complete. Configuration of the server can officially begin!
<br />
<br />
<p align="center">
Configure the IPV4 Properties for the internal network adapter:<br/>
<img src="https://imgur.com/Zx0tE33.png" height="40%" width="40%" alt="Internal Network IPV4 Properties Config"/>
<br />
<br />
<p align="center">
Within the Server Manager, Install Active Directory Domain Services Role and Promote this server to Domain Controller:  <br/>
<img src="https://imgur.com/h3kjnpv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/ixxiL6c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  
- In this step you will
- Add a new forest and configure a domain name
- Set Directory Services Restore Mode Password
<br />
<br />
<p align="center">
Create an Admin Account in the "Active Directory Users and Computers" Menu:<br/>
<img src="https://imgur.com/ZjfRvdB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/aVh43uu.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">
Within the Server Manager, Install Remote Access Role and Configure it to the Internet Interface:<br/>
<img src="https://imgur.com/u8K1zIZ.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/mCHs3go.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">
Within the Server Manager, Install DHCP Role and Configure IPv4 Settings:<br/>
<img src="https://imgur.com/koaGZXG.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/qDucjfG.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">
Once these roles have all been properly configured. Your server manager should look like this:<br/>
<img src="https://imgur.com/OpkSLL2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">
Next, We will set up a client PC, running Windows 11 Pro, and connect to the domain:<br/>
<p align="center">
<img src="https://imgur.com/rAi0shs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

  - Please note that the network port will be set to "Internal Network"
  - When prompted during setup, select "for business" and proceed using domain to avoid creating a windows account. Process may vary depending on version.
  - Once set-up is complete, you should be met with the standard windows desktop. Now we need to confirm the Client PC has a connection with the domain controller. We can use multiple methods to confirm this
<br />
<br />
<p align="center">
Check for the Clients IP Address on the Domain Controllers DHCP and Active Directory Menus...:<br/>
<p align="center">
<img src="https://imgur.com/7ATSJnn.png" height="60%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/5iub2LV.png" height="60%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">
...or Sign In to the Client VM using a user account created on the DC. Then Ping the domain in the Command line:<br/>
<p align="center">
<img src="https://imgur.com/khM7511.png" height="60%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/M8F4VGH.png" height="60%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/iwwKKO3.png" height="60%" width="50%" alt="Disk Sanitization Steps"/>

- I also pinged google.com to confirm the Internal Network was running properly
- As we can see. The DC assigned the client PC an IP address using DHCP.
- The next project within this Active Directory will be to setup and configure Group Policy Management!
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
