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


4
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/kCXHbZ4.png">
<br />


5
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/CGvHU5n.png">
<br />

6
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/fNtMwMv.png">
<br />


7
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/9ZgudbV.png">
<br />


8
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/yyBpdJG.png">
<br />


9
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/a6DvkAD.png">
<br />


10
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/pDxFBwo.png">
<br />

11
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/S7SsvGn.png">
<br />

12
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/kDqJpGv.png">
<br />

13
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/MnYIErL.png">
<br />

14
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/dZasj5s.png">
<br />

15
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/M4dz5bL.png">
<br />

16
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/4yo7XTQ.png">
<br />


17
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/4Zm3ome.png">
<br />

18
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/zFHw44X.png">
<br />

19
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/jzZy1YC.png">
<br />

20
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/jzZy1YC.png">
<br />



