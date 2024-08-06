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
  
 - Set up your Password for the built-in Admin account (in this lab: Password1). You will prompt to press [Ctrl+Alt+Delete] on the locked screen. Instead of using a keyboard, manually click on [input] > [keyboard] >[Insert Ctrl-Alt-Del] at the top-left of your screen. 
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/fNtMwMv.png">
<br />
<br />
<br />

7
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/9ZgudbV.png">
<br />
<br />
<br />

8
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/yyBpdJG.png">
<br />
<br />
<br />

9
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/a6DvkAD.png">
<br />
<br />
<br />

10
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/pDxFBwo.png">
<br />
<br />
<br />

  
11
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/S7SsvGn.png">
<br />
<br />
<br />
  
12
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/kDqJpGv.png">
<br />
<br />
<br />
  
13
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/MnYIErL.png">
<br />
<br />
<br />
  
14
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/dZasj5s.png">
<br />
<br />
<br />
  
15
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/M4dz5bL.png">
<br />
<br />
<br />
  
16
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/4yo7XTQ.png">
<br />
<br />
<br />

17
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/4Zm3ome.png">
<br />
<br />
<br />
  
18
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/zFHw44X.png">
<br />
<br />
<br />
  
19
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/5i34KvY.png">
<br />
<br />
<br />
  
20
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/majUEGz.png">
<br />
<br />
<br />

21
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/JBUWeT3.png">
<br />
<br />
<br />

22
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/bqynbT9.png">
<br />
<br />
<br />

23
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/QEAzN97.png">
<br />
<br />
<br />

24
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/zbUgEdR.png">
<br />
<br />
<br />

25
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/8cMeT7D.png">
<br />
<br />
<br />

26
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/QteaDVo.png">
<br />
<br />
<br />

27
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/rcC8pp0.png">
<br />
<br />
<br />

28
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/PjwmtNM.png">
<br />
<br />
<br />

29
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/PkJXDCv.png">
<br />
<br />
<br />


30
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/KXnfkEz.png">
<br />
<br />
<br />


31
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/Z1ywwtb.png">
<br />
<br />
<br />



32
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/GbxCrdD.png">
<br />
<br />
<br />


33
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/71DudxG.png">
<br />
<br />
<br />


34
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/w0mP6rG.png">
<br />
<br />
<br />


35
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/qBncaQZ.png">
<br />
<br />
<br />


36
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/JDUAoWG.png">
<br />
<br />
<br />


37
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/cwVM77z.png">
<br />
<br />
<br />



38
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/kMSZSM0.png">
<br />
<br />
<br />



39
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/U6exubN.png">
<br />
<br />
<br />



40
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/BedkbQY.png">
<br />
<br />
<br />




41
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/E0vce5D.png">
<br />
<br />
<br />


42
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/06HMc7y.png">
<br />
<br />
<br />

43
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/gmkEu2d.png">
<br />
<br />
<br />


44
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/CaZUGdN.png">
<br />
<br />
<br />


45
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/lIcEr64.png">
<br />
<br />
<br />


46
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/WKCLk8z.png">
<br />
<br />
<br />



47
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/nVvmTn8.png">
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





49
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/GwHQWGi.png">
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


51
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/0ps5Ek3.png">
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

53 (the image needs to be fixed !)
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/XIRVYKa.png">
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


55
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/c898UxO.png">
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


57
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/haCXAF5.png">
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



59
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/q0VjRvh.png">
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


61
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/T1QLusW.png">
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

63
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/kmtBW7t.png">
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



65
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/ySOe6dO.png">
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


67
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/7JsUXLt.png">
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




69
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/aQtz0NQ.png">
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

71
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/b5lbS0O.png">
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

73
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/54eUZxx.png">
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



75
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/2ymfHWu.png">
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

77
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/wbJvvTp.png">
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


79
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/2TsjKBO.png">
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

81
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/nc1OeaN.png">
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

83
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/4orHm7n.png">
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



