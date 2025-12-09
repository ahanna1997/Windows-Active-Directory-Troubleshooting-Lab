Active Directory Troubleshooting Lab Summary (Oracle VituralBox)
----

Overview:
This project involves building a full Windows Server + AD environment to simulate enterprise IT support tasks.

Key Components:
- Configured Domain Controller, AD users, groups, and OUs.
  
- Applied Group Policies for security, printers, passwords, and software restrictions.
  
- Simulated 10+ troubleshooting scenarios (GPO failures, account lockouts, file share permissions). - Performed root cause analysis and documented resolutions.
  
Skills Demonstrated:
- Active Directory Administration
  
- Windows troubleshooting
  
- Group Policy Management
  
- Permission & access troubleshooting

Lets create the Active Diretory using Windows Server 2025
-----

First thing first lets download Windows 2025 from the Microsoft Evaluation Center by just going to Google and search for "Windows Server 2025".

-Click the link and on the Microsoft page you should see Windows Server 2025 scroll down where you see "Download this ISO"and click it leading to the download page  and Click on English (Untied States) ISO download the 64-bit editon for this is the one that I will be using.

- In Orcale VitualBox  lets click on the New icon in the top left corner and the Create Virtual Machine page should popup.
  
- On that page fill out all the sections with:
  Name: Windows Server 2025(or whatever you want to call it)
  ISO image: Using that Windows Server 2025 ISO I just downloaded in the step above you want to find it wherever you saved it and click it. After click that it will fillout the fields for you. Also once all the other fields are filled at the bottom you will see a check box which says Skip Unattended Installation make sure you check that box.
  
- Next go down to Hardware where you can choose the Base Memory and Processors.(Recommand using atleast 2048 MB+ and 3 CPU+  depending on how much Hardware space that you have on your computer or laptop) Also make sure to click that check box that says Enable EFI(Special OSes only).

- Next Hard Disk in that drop down you will see that it is already set to 50.00 GB and that should be enough to run the Virtual enviroment.

- Click Finsih and your virtual machine will be created.
  
- Now let run the Virtual Machine by either double clicking or clicking it and then clicking on Start to start running the machine

- Once running when the vitual machine first boots up make sure to press Enter key so it goes to the Windows Sever Setup pages.
- First page select language settings
- Keyboard settings
- last page should be setup option click on "Install Windows Server" and click the checbox and the next
- Select Image page click "Windows server 2025 Standard Evalution(Desktop Experience)" and next then Accept.
- next page which is location to install Windows Server should only be one option which is DISK 0 click next and next click Install.
- Comptuer /Laptop will restart
- Once restarted it will prop you to enter a password for that Administrator account. (which will be Password1).
- On the next page lets login as the Admin.
- Once logged in on the admin account lets Insert Guest addition CD image by hover to the top of the page and clicking on Devices tab ...go  down to Insert Guest Addtions CD image and click on it.
- from there in the virtual machine click on the open File Explore  scroll down to  "This PC" click it and  then double click CD Drive(D)VirtualBox Guest Addtions.
- Once inside folder scroll down until you see VBoxWindowsAddition-amd64 double click it then next and next and Install.You should geta you will have to reset Windows server popup.... click Reboot now and finsih let computer reboot.


Setting up Window Server 2025 and Static IP Configuration
---------------
-After creating the admin account lets login useing the password that we used. (Which is Password1)

- Once logged in to the Admin account the first thing that you should see pop up is the Server Manger.If not that's okay you can click on the search box at the bottom of the desktop page and type in Server manager and click on it.
 
- Now that we are in the server manager let configure the essential settings on the Windows Server.
  
1)Lets start by configuring the host name
2) next the time zone
3) then making sure the server is  up to date with the most updated software update
4) finally we will configure the static IP address



#
