<h1 align="center">Summary Diagram</h1>


<p align="center">
<br/>
<img width="950" alt="Portfolio" src="https://i.imgur.com/yNvZ7Lx.png">
<br />
</p>


<br />
<br />

<h1 align="center">Project walk-through</h1>

<br />
<br />

***Files to Prepare***

VirtualBox

- Oracle VirtualBox Platform Package
- Oracle VirtualBox Extension Pack


Windows

- Windows Server ISO file
- Windows 10 ISO file
  - How to bypass installing the Media Creation Tool:
    - Browse the Microsoft Windows 10 download page with Microsoft Edge or Google Chrome.
    - Select [more tools] > [Developer tools] or Press *F12*
    - Select [customize] > [more tools] > [Network Condition]
    - Select [Network condition] > [User agent –BlackBerry BB10]
    - Now you can download the Windows 10 ISO file

---

<h4>Tip: Any configuration options not mentioned in the walkthrough can be left at their default settings</h4>

---

***Installing Virtual Box***
 
- Install VirtualBox Platform Package

  - How to fix the "Missing Dependencies Python Core /win32api" error:
    - Install python (run as Admin) 
    - Check [Use admin Privileges...] and [Add to PATH]
    - Open PowerShell and run: `py –m pip install pywin32`

- Install VirtualBox Extension Pack
    - Extension pack features enhanced user experience, such as the Drag&Drop function

---

***Domain Controller VM Configuration***
 
- VM Name and Operating System
  - Open Oracle VirtualBox
  - Click on [New] 
  - Name: Domain_Controller (or whatever name you prefer)
  - ISO Image: browse and pick the Windows Server ISO file
  - Check the box [Skip Unattended Installation]

<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/jzZy1YC.png">
<br />

- Hardware
  - Base Memory (RAM): 2 ~ 4 GB
  - Processor: 1~4 Cores
    - *The VM's memory and Processor settings will determine its performance. Choose according to your host machine's RAM and Cores.*


- Virtual Hard disk
  - Storage: 40 ~ 60 GB
    - *It is always better to have more storage. Do not go below 40GB to be safe.*
    
- General (advanced)
  - Shared Clipboard: Bidirectional
  - Drag'n'Drop : Bidirectional
    - *The bidirectional option allows you to drag and drop and share the clipboard between your host machine and the VM.*
 
- Network
  - Adapter 1: attached to NAT
  - Adapter 2: attached to Internal Network
    - *The domain controller server will need 2 NICs: One that will connect to the internet (using your house router) and one that will be used for the internal VM clients*

---
 
***Microsoft Server OS Setup***

After configuring all the settings, double-click the VM. Select [next] > [Install now]

 - Select [Windows Server Standard Evaluation (Desktop Experience)]
    - *With this option, your VM will run in a Graphical User Interface (GUI).*
<p align="center">
<br/>
<img width="530" alt="Portfolio" src="https://i.imgur.com/WVvLdyj.png">
<br />
<br />
<br />

 - Choose [Custom: Install Windows only (advanced)]
    - *This means formatting the hard drive and installing it from scratch.*
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/kCXHbZ4.png">
<br />
<br />
<br />

 - When installing, your VM will reboot multiple times. During the black screen, don't touch anything.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/CGvHU5n.png">
<br />
<br />
<br />


 - Set up your Password for the built-in Admin account (in this lab: Password1). You will be asked to press [Ctrl+Alt+Delete] on the locked screen. Instead of using a keyboard, manually click on [input] > [keyboard] >[Insert Ctrl-Alt-Del] at the top-left of your screen. 
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/fNtMwMv.png">
<br />
<br />
<br />

---
***Installing VM guest Addition***
 - Installing the VM guest addition will improve the user experience. It will provide smoother mouse cursor movement and the function to auto-adjust resolution to the VM scroll size.
 - Select [Devices] > [Insert Guest Additions CD image…] at the top left of your screen.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/9ZgudbV.png">
<br />
<br />
<br />

 - Browse to [This PC], and click on the remote drive: [VirtualBox Guest Addition CD drive]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/yyBpdJG.png">
<br />
<br />
<br />

 - Double-click on [VboxWindowsAddition-amd64]
 - Install with default settings. When you are prompt to reboot after installation, click on [I want to manually reboot later]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/a6DvkAD.png">
<br />
  
 - After the installation, shut down the VM. (Clicking restart sometimes gives an error.) Then, rerun the Domain Controller VM.

<br />
<br />

---
***Assigning IP address to the internal network NIC (Network Interface Card)***

 - The Domain Controller VM server will have 2 NICs, one for the Internet and another for the internal network. See the diagram below:
<p align="center">
<br/>
<img width="400" alt="Portfolio" src="https://i.imgur.com/pDxFBwo.png">
<br />
  
  - *The first NIC on the left is NATed, which means it will share the same IP address as your home router. However, we must manually assign an IP address for the second NIC.*

<br />
<br />
<br />
<br />

 - Go to network setting, click on [Change adapter options]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/S7SsvGn.png">
<br />
<br />
<br />
<br />
<br />
  
 - You will see two adapters (NICs). We need to compare the network connection details of each adapter and determine which one is for the internal network.
 - Take a look at the first NIC. The IP address 10.0.2.15 is a default IP address you get from NAT, meaning that this adapter uses your home router.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/kDqJpGv.png">
<br />
<br />
<br />
<br />
    
 - An IP address beginning with 169.254 is called an Automatic Private IP Addressing (APIPA) IP address, which means the adapter was looking for a DHCP server to get an IP address but could not find one. This network is for the VM internal network.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/MnYIErL.png">
<br />
<br />
<br />
<br />
  
 - Rename each network to "_INTERNET_" and "X_Internal_X" (for clarity). 
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/dZasj5s.png">
<br />
<br />
<br />
<br />
  
 - Right-click the "X_Internal_X" and click on [Properties]
 - In the [Networking] tab, select [ Internet Protocol Version 4] > [Properties]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/M4dz5bL.png">
<br />

 - Configure like below:
    - IP address: 172.16.0.1 (or any address that is in the private IP address range)
    - Subnet mask:255.255.255.0
    - Default gateway: n/a (because the domain controller itself serves as a default gateway)
    - Preferred DNS server: either 172.16.0.1 (The same IP address as itself) or 127.0.0.1 (loopback address)
       - *When we install an Active Directory later, it automatically installs DNS. This server will use itself as the DNS server.*

<br />
<br />
<br />
<br />

---

***Installing ADDS (Active Directory Domain Service)***

 - Open [Server Manager]. Click on [Add roles and features]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/4yo7XTQ.png">
<br />
<br />
<br />
<br />

 - You will be asked to pick a server on which you want to install Active Directory. Choose [DomainController]. Click on [Next]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/4Zm3ome.png">
<br />
<br />
<br />
<br />
  
 - Choose ADDS (Active Directory Domain Service). Click on [Next] and [Install]
       - **Again, any configuration options not mentioned in the walkthrough can be left at their default settings**
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/zFHw44X.png">
<br />
<br />
<br />
<br />

---
***Setting up a Domain***


 - We've successfully installed the active directory domain services software. However, we still need to configure a domain.
 - Click on the yellow notification sign for Post-deployment Configuration.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/5i34KvY.png">
<br />
<br />
<br />
<br />
  
 - [Add a new forest] - [Root domain name: mydomain.com]
   - *(you can enter any name you want for your domain.)*
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/majUEGz.png">
<br />
<br />
<br />
<br />

 - Check the box: [Domain Name System (DNS) server)]
    - *We won't use the DSRM function. However, we need to set up a Password to proceed.*
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/JBUWeT3.png">
<br />
<br />
<br />
<br />

 - Uncheck the box [Create DNS delegation], and proceed to [Install]. When the installation is complete, your VM will reboot automatically.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/bqynbT9.png">
<br />
<br />
<br />
<br />

 - You will notice the difference, now MYDOMAIN is displayed on the left side of the built-in admin account. Proceed to log in. 
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/QEAzN97.png">
<br />
<br />
<br />
<br />

---

***Creating a Domain Admin User Account***

 - We will create our own admin account instead of using the built-in admin account.
 - Open the start menu and go to [Windows Administrative Tools] - [Active Directory Users and Computers]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/zbUgEdR.png">
<br />
<br />
<br />
<br />

 - Right-click newly created domain: mydomain.com. Create a new OU (organizational Unit)
    - *We won't go over the concept of OU. For now, you can think of it as a folder in the active directory.*
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/8cMeT7D.png">
<br />
<br />
<br />
<br />

 - Name the OU "_ADMINS." Since this is a lab environment, you can uncheck [Protect container from accidental deletion]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/QteaDVo.png">
<br />
<br />
<br />
<br />

 - Create a new User in [_ADMINS]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/rcC8pp0.png">
<br />
<br />
<br />
<br />

 - Type your first and last name. Set up login name. Click on [Next]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/PjwmtNM.png">
<br />
<br />
<br />
<br />

 - Type the Password for the account. Since we are in a lab environment, we will uncheck the box [User must change Password at next logon] and check the box [Password never expires] 
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/PkJXDCv.png">
<br />
<br />
<br />
<br />


 - We have successfully created a new user account. However, we need to set up the User as Domain Admin.
 - Go to [Properties] of the new User.
 - Select [Member Of] > [Add]. Type "Domain Admins" for the object name. Click on [Check Name] > [OK]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/KXnfkEz.png">
<br />
<br />
<br />
<br />

 - Click on [Apply] > [Ok].
 - Now we have our very own domain admin account!
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/Z1ywwtb.png">
<br />
<br />
<br />
<br />



 - Log out the current account and log in with the new admin account.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/GbxCrdD.png">
<br />
<br />
<br />
<br />

---

***Installing Remote Access Server (RAS) / Network Address Translation (NAT) on the DC***

The purpose of installing RAS/NAT is to allow the Windows 10 VM client (which will be installed later) to be on the private virtual network but still access the Internet via the Domain Controller.
<br />
<br />
<br />
<br />

 - We must install a Remote Access Server (RAS) before installing NAT.
 - Open [Server Manager], click on [Add roles and features]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/71DudxG.png">
<br />
<br />
<br />
<br />


 - Pick the domain controller server. [DomainController.mydomain.com]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/w0mP6rG.png">
<br />
<br />
<br />
<br />


 - Check the [Remote Access] box for the role.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/qBncaQZ.png">
<br />
<br />
<br />
<br />


 - Check both boxes [Routing] and [DirectAccess and VPN (RAS)]. Click [next] and [install]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/JDUAoWG.png">
<br />
<br />
<br />
<br />


 - Now, let's install NAT. Open [Server Manager]. Select [Tools] >[Routing and Remote Access]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/cwVM77z.png">
<br />
<br />
<br />
<br />



 - Right-click on [the domain controller server], then select [Configure and Enable Routing and Remote Access]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/kMSZSM0.png">
<br />
<br />
<br />
<br />



 - Select [Network address translation (NAT)]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/U6exubN.png">
<br />
<br />
<br />
<br />



 - Check the box [use this public interface to connect to the Internet] (if this check box is not active, close the [Routing and Remote Access] window, and try opening it again)
 - Select [_INTERNET_] > [Next] > [Next] > [Finish]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/BedkbQY.png">
<br />
<br />
<br />
<br />




 - After the installation, our DC server is marked with a green icon, which means it is active and no longer "unconfigured."
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/E0vce5D.png">
<br />
<br />
<br />
<br />


---

***Setting up the DHCP server on the DC server***

Setting up the DHCP server on our Domain Controller allows the DC to assign IP addresses to Windows 10 VM clients

<br />
<br />
<br />
<br />

 - Open [Server Manager]. Click on [add roles & features]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/06HMc7y.png">
<br />
<br />
<br />
<br />

 - Select the domain controller server.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/gmkEu2d.png">
<br />
<br />
<br />
<br />


 - Select [DHCP role]. Click on [Next] and [Install].
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/CaZUGdN.png">
<br />
<br />
<br />
<br />

---

***Setting up DHCP scope***

<br />
<br />
<br />

 - You will see the yellow warning sign telling you that configuration is required for the DHCP server.
 - Go to [Tools] > [DHCP]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/lIcEr64.png">
<br />
<br />
<br />
<br />

 - IPv4 and IPv6 under the domain controller are in an "unconfigured" state. (Flagged with the red marks) 
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/WKCLk8z.png">
<br />
<br />
<br />
<br />



 - Click on [New Scope…]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/nVvmTn8.png">
<br />
<br />
<br />
<br />



48
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/eU04f8K.png">
<br />
<br />
<br />
<br />





49
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/GwHQWGi.png">
<br />
<br />
<br />
<br />



50
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/uqoTEfj.png">
<br />
<br />
<br />
<br />


51
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/0ps5Ek3.png">
<br />
<br />
<br />
<br />



52
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/IECqsRf.png">
<br />
<br />
<br />
<br />

53 (the image needs to be fixed !)
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/XIRVYKa.png">
<br />
<br />
<br />
<br />


54
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/iH3s0kP.png">
<br />
<br />
<br />
<br />


55
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/c898UxO.png">
<br />
<br />
<br />
<br />


56
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/xreaWCX.png">
<br />
<br />
<br />
<br />


57
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/haCXAF5.png">
<br />
<br />
<br />
<br />


58
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/KVwJXau.png">
<br />
<br />
<br />
<br />



59
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/q0VjRvh.png">
<br />
<br />
<br />
<br />


60
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/z14KYng.png">
<br />
<br />
<br />
<br />


61
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/T1QLusW.png">
<br />
<br />
<br />
<br />

62
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/Rw8uFXo.png">
<br />
<br />
<br />
<br />

63
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/kmtBW7t.png">
<br />
<br />
<br />
<br />


64
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/t9Wiz50.png">
<br />
<br />
<br />
<br />



65
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/ySOe6dO.png">
<br />
<br />
<br />
<br />


66
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/4KnUfGC.png">
<br />
<br />
<br />
<br />


67
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/7JsUXLt.png">
<br />
<br />
<br />
<br />


68
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/CIgGQau.png">
<br />
<br />
<br />
<br />



69
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/aQtz0NQ.png">
<br />
<br />
<br />
<br />


70
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/nkVGQwl.png">
<br />
<br />
<br />
<br />

71
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/b5lbS0O.png">
<br />
<br />
<br />
<br />

72
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/w9C905T.png">
<br />
<br />
<br />
<br />

73
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/54eUZxx.png">
<br />
<br />
<br />
<br />


74
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/x3royMF.png">
<br />
<br />
<br />
<br />



75
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/2ymfHWu.png">
<br />
<br />
<br />
<br />


76
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/pgDsiKj.png">
<br />
<br />
<br />
<br />

77
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/wbJvvTp.png">
<br />
<br />
<br />
<br />




78
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/KBgYQNj.png">
<br />
<br />
<br />
<br />


79
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/2TsjKBO.png">
<br />
<br />
<br />
<br />


80
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/SSKsv34.png">
<br />
<br />
<br />
<br />

81
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/nc1OeaN.png">
<br />
<br />
<br />
<br />


82
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/85qaMHH.png">
<br />
<br />
<br />
<br />

83
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/4orHm7n.png">
<br />
<br />
<br />
<br />


84
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/J68fYzN.png">
<br />
<br />
<br />
<br />



