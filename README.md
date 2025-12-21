Install of Windows Servers2025,Windows11 and Active Directory Troubleshooting Lab Summary (Oracle VituralBox)
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

-After restrart you can should see then login page.You should now see that you are now in the DC by seeing MYDOMAIN\Admistrator or what you have named your DC.(Mine was MYDOMAIN)

-Login into Server with the password you created.Once logged in lets verify that the DC in the server Manager on the left had side you should now see AD DS & DNS. If you see those lets go to Tools at the top right corner and click tools.In the drop down you want to make sure you have three things: Active Directory User and Computers ,DNS,and Group Policy management.If you see all three lets proceed.

-Now we test the DNS resolution. Go to the search box and search Command Prompt and enter.

-Once the CMD is open type in nslookup  and whatever your domain is. (Mine is nslook mydomain.com ) 


Active Directory Organizational Units(OUs) & Groups
---
In the section we will create our 

1. Organization Units(OUs) which are primarily  used for Administrative Organization , Applying Group Policies(GPOs),Delegating Control.
  
2. Groups which are collections of objects that are used to grant Permissions and Simplify management and allow creates Security Groups or Distribution Groups.


Lets start by creating a OU called employees and add groups.
---

-So lets go to Tools in the top right corner  click it and in the drop down tab find  Active Directory User and Computer. now you should see on the left handside the domain that you have created.(Mine was mydomain.com)   

-Click on the arrow next to it and a drop down should appear with organizational untis.Right click on mydomain and find New hover over it  and there ypu will see oraganizational unit click on it.

-once inside name the Organizational unit Employees then ok.

Now lets create Groups here are the Step to create groups:

1.Find Employees lets create some groups nowy.Right click employees and hover over New and find Group .

2.On this page create your group name Sale Department.(Make sure in Group scope Global is choosen and in Group type make sure Security is choosen then click ok.)

3.Click Employees folder and inside you should see the sales Department in the folder.

-Now lets create a couple more Groups by repeating steps 1-3 above for each Department.(IT Department, Operation Department , HR Department , and Administration Departments)

-Now this is where you will add users in this groups 

 Before Proceding on in Windows Server 25 we need to create our Windows 11 for client side server

 
Installing Windows 11 
--

-To install Windows 11 open Google and typoe in the search box "Download Windows 11" click the link.Scroll down to Windows 11 Disk Image(ISO) for x64 devices,click the drop down button and select the Windows 11 then click comfirm.

-Once the download is finish open up Oracle VitualBox  click on new and name it Windows 11  and go down to ISO Image and chose the file that you just download and open and it will file out the rest of te fields.(Make sure you do not click the box to skip Unattended Installation)

-Next tab which is the unattended Install here select the login username and password.(Here im using Cyberman for the username and the password will be password1)

-Next tab is the Hardware where you chose the Base Mermory and the Processors 

-Next tab hard disk here will see he have 80.00GB by default you cna keepthat and click finish.

- Windows 11 should start running automatically if not just click it and click run. Once it starts go through the install  process by selecting language ,keyboard settings and select setup option after those three pages you will come to a Product Key page selet dont have product key and next.

- Next page select Windows 11 Pro as the OS and next Accept the term and conditions and click next on the Loction to install Windows11 and then Install and it will start installing Windows 11.

- After the install  fill out the pages that are presented at the end the Windows update page should start and let it download.after update fill out all the Page after that.Windows 11 shpuld be install and operating on your Vitualbox.

- Now once on the desktop of Windows 11  let insert Guest Additions CD images by hitting Control F on your keyboard snd clicking devices at the top of the page and hovering down to Insert Guest Additions CD Image .Once you do tha like on the Folder on the Windows 11 desktop  and in thae folder find This PC on the left handside and click the CD Drive(D:) VirtualBox Guest Addtions and inside find VboxWindowsAddons double click it and hit install and you will need to Reboot.

- After the reboot login using the password you created for that account. (Mine was password1) and windows 11 is good to good on your Virtual Box.

- Now we need to create a second Windows11 and name it Windows11-2. So just repeat the same steps above


Now back to Windows Server 2025 to create a Network between Windows 11 & Windows11-2 and Windows Server 2025
-

In your VitualBox Manager you should have Windows Server 2025 and Windows 11 & Windows11-2 now on your Vitural box.

First lets click on Windows Server 2025 and click on settings.A tab will open on the lefthand side find Network and on the page make sure your in Adapter 1.There you will see "Attached to:" click the drop down and find Internal Network.After clicking Internal network we need to name  it.In the Name section Name it whatever you would like (Im using ADNETWORK & make sure you click the box next to cable connected) click ok.

Now lets work on finishing setting up the Windows11 & 11-2 in a simlar way.

Lets start with Windows 11-2 click on it and go to settings the tab will open on the lefthand side find Network and on the page make sure your in Adapter 1.There you will see "Attached to:" click the drop down and find Internal Network.After clicking Internal network we need to name  it.In the Name section Name it whatever you would like (Im using ADNETWORK & make sure you click the box next to cable connected) click ok.
  
Now do the same thing for Windows11.

Once you added the three virtual machines to the same network now we need to configure the IP addresses and subnet mask and DNS for all three machines.

Select Windons Server 2025 and click on start to run the VM.log in with your creditals  that we created earlier(Mine was Password1)

do the same for Windows11 &11-2 all three should be running.

Our next step is to need to set the static IP for all three (important to do this because each machine requires a unique static IP to communicate with the network and the windows 11 machines  need to use the Windows Servers as their DNS server to resolve the domain name) 


Lets start with our Windows Server 2025  and there let click on the start icon in Windows server  and find and click into system. On the left hand side find network & internet from there click into ethernet.

There you will see your all your IP assignment and all the IPv4 settings that we configured for the Server when we created the Windows Server 2025. Click  Edit on the right handside.

Once in the IP setting make sure that the following are correct for the Windows Server 2025.

IP address:192.168.1.10

Subnet mask:255.255.255.0

Gateway:192.168.1.1

Preferred DNS: 127.0.0.1


Click save and lets move to the Windows11 and Windows11-2

Lets start with Windows11. In the Windows11 VM in the search box type in Control Panel and click into it.Select Network and Internet then Network and Sharing Centre.On the lefthand side you will see chnage adapter setting click the link.

Right click Enthernet and find Properties, in the properties click on Internet Protocol Version 2(TCP/IPv4) and select properties. there we need to change our IP address.(In a real-world scenario you will click on Obtain an IP address automatically becuase it will be obtaining it from DHCP server or from DHCP that is set up on your router but since we are using VM we will configure ours IP address)

Click on Use the following IP address and fillout the fields with whatever you like(Imausing the following:
Windows11
IP address:192.168.1.20
Subnet mask:255.255.255.0
Default gateway:192.168.1.10(Here we usethe Ip address of the of the Windows Server 2025 because the machines will be connecting or talking  our windows Server) 

Once done click ok. Now do the same thing for Windows11-2.

Windows11-2
IP address:192.168.1.21
Subnet mask:255.255.255.0
Default gateway:192.168.1.10(Here we usethe IP address of the of the Windows Server 2025 because the machines will be connecting or talking  our windows Server) 



Now lets do some pinging to check if these three are able to communicate with each other.

Open Windows11-2 and go to CMD of the computer by searching it. Once in the command prompt lets ping our Server.


Type ping and the IP address  of your Windows Server.(Mine will be ping 192.168.1.10 ). 





Now lets ping our Windows11 computer to make sure that the computer is able to talk (Mine will be ping 192.168.1.20) 






Go to our Windows Server and lets do the same thing by ping both windows 11 computers.go to CMD of the computer by searching it. Once in the command prompt lets ping our Server.

Type ping and the IP address  of your Windows11.(Mine will be ping 192.168.1.20 ). 


Now lets ping our Windows11 computer to make sure that the computer is able to talk (Mine will be ping 192.168.1.21) 


