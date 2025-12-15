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
  
1.Lets start by configuring the host name

- In server manager lets find local server on the left hand side click it.

- Properties page should have popped up and you will see Computer name click it to change it name

- Once on the next page click change button at the bottom and on the new page you can change the computer name.(Changed mine to Server2025-DC01) and click okay.Will get a prompt that you have to retart your computer to apply changes click restart Now. (In a real world work environment only Server managers with Administrative Rights will be able to change the computer names)

- After restart log back in and go back to server manager and the Local server to check if the computer name has changed.

2.Next the time zone

- To do this right click on the time and date in the bottom right hand corner and click adjust time and date leading you to the setting page.

- Once on the page scroll to Time zone and there you can chnage the time zone to whereever you need the computer to be. Then close the  window.(Once again you need to have Administrative rights to change the same as the one above)

      
3.Then making sure the server is  up to date with the most updated software update(A crucial step for setting up or looking after a Windows Server because installing updates make sure that the windows Servers are on the lastest serurity patches or big fixes and performance enhancements)

-To do this lets go to hover or the window icon right click on it  and scroll and click on settings and from there find Windows Update on the left hand side.

-on the Windows update poage you will see all the update that are avaiable you can click install all and some updates may require a computer restart click restart.

-After restat log back in and check for updates again to see if all were installed and up to date. Close the window.

4.Finally we will configure the Static IP address( Needed as a Window Server should have a static IP address to ensure consist network communication as Dynamic IP address from DHCP could change causing disruption to services like DNS or file sharing)

-From the  Server Manager dashbard click on local Server on the left hand side there all the properties  will be show and let find the Ethernet section and click the that link to change it.(Should have IPv4 address assigned by DHCP,IPv6 enabled by default)

-once click on it right click on ethernet and then properties then on the Ethernet properties popup lets find and click on Internet Protocol version 4(TCP/IPv4) and click on properties.

-On the General page lets click on the second option which is Use te following IP address so we can configure them. For Ip address lets add 192.168.1.10 then sudnet mask click on the field and it should automatically fill it  and for default gateway  lets add 192.168.1.1. 

-At the bottom for preferred DNS Server 127.0.0.1 if the server will act as DNS server otherwise use the network primary and click ok once done.

-Now lets open up our Command Prompt (CMD) by find the search box and typing in CMD open it.In the CMD let type ipconfig for check the Windows IP Configuration and there you should be able to see everything that you just change in the steps above.(If you want to see more info you can type ipconfig /all and it will give more of the Window Server properties)



#Installing the Active Directory (AD)
---
Here we will be doing 2 critical task:

1)Installing the Active Directory Domain Services (AD DS)role.(This step gives us the necessary components and tools for active directory on the sever setting the stage for Centralized Network management.


2)Promoting the server to a Domain Controller(DC) and creating a new domain



Let's start with Installing the AD DS role.

-In Server Manager you can click on Add other servers to manage or you cna go to the top right corner and click on "Manage" then add roles and feature.

-You should see this pages.
+Before you begin page,click next.
+Select installation type (By default it will chose Role-based orfeature-based installation) click next.
+Select destination server.(Which should be the server that you have created in the step above mine was Server2025-DC01)Select the Server should be the on you created by default  and hit next.
+ Select the server roles so here you select Active directory domain services once selected a pop up window will saying add features ,click the box and click Add Features nd then next.
+ Next page is the AD DS just click next nothing to do on that page.
+ Finally on the last page click Install .

After install we have to promote the server to a DC.(very important  because it actives AD DS snd sets up the first domain in a new forest establishing the foundation for managing network resources securely)

-So in the Server Manager in the right hand corner you will see a flag with a Yellow caution symbol thats the notification center, click it  and ypou will see  as the very first option promote server this server to a DC click the link. 

-On the pop up window it should be the Deployment Configuraton so here we want to create/Add a new Forest and we will have to make a Root domain Name for the forest .(Can be anything you like Im going to use mydomain.com) Click next

-On th DC options page it should default to the ;lastest Option unless you have to select a backward compatiblity than no need to change.After that set the Directory Service Restore Mode (DSRM) password (Im using Password1) click next.

-Next page you willsee a warning but that okay click next.

-on the next page is were you specify the net bios domain name it should be based off of your root domain name.(my root domain is mydomain.com so my bios domain will by MYDOMAIN) Click next.

-Next page Paths is a default you cn leave them.(You will only need to modify them if your server has a separate drives for performance or redundancy)Click next.

-Next page is just the review page click next.

-Now the next page the prerequisites check page  just basically check to make sure the server meets all the requirements. After the server check hit install and computer will restart after Install.

-After restrart you can 

-
