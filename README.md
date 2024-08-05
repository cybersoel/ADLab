<h1>Summary Diagram</h1>


<br/>
<img src="https://i.imgur.com/yNvZ7Lx.png" height="80%" width="80%" alt="Summary Diagram"/>
<br />



# Project walk-through


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

<h4>Tip: any configurations that are not mentioned in the walkthrough can be left as default setting</h4>

---

***Installing Virtual Box***
 
- Install VirtualBox Platform Package

  - How to fix the "Missing Dependencies Python Core /win32api" error:
    - Install python (run as Admin) 
    - Check [Use admin Privileges...] and [Add to PATH]
    - Open PowerShell and run: [py –m pip install pywin32]

- Install VirtualBox Extension Pack
    - Extension pack features enhanced user experience, such as the Drag&Drop function

---

***Domain Controller VM Configuration***
 
- Set up Name and Operating System
  - Click on [New] 
  - Name: DomainController (or whatever name you prefer)
  - Type: Microsoft Windows
  - Version: Other Windows (64bits)
  - ISO Image: browse and pick the Windows Server ISO file


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

<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/WVvLdyj.png">
<br />




