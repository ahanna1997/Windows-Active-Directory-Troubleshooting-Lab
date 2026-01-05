Install of Windows Servers2025, Windows11 and Active Directory Troubleshooting Lab Summary (Oracle VituralBox)
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
<img width="796" height="307" alt="Image" src="https://github.com/user-attachments/assets/6e2692da-c95c-438b-87fc-b3b6bf0f958d" />

First thing first lets download Windows 2025 from the Microsoft Evaluation Center by just going to Google and search for "Windows Server 2025".

<img width="1770" height="713" alt="Image" src="https://github.com/user-attachments/assets/78f8ab1b-058f-4fef-9cb5-a5113fe0388b" />

-Click the link and on the Microsoft page you should see Windows Server 2025 scroll down where you see "Download this ISO"and click it leading to the download page  and Click on English (Untied States) ISO download the 64-bit editon for this is the one that I will be using.

- In Orcale VitualBox lets click on the New icon in the top left corner and the Create Virtual Machine page should popup.
  
- On that page fill out all the sections with:
  
  Name: Windows Server 2025(or whatever you want to call it)
  
  ISO image: Using that Windows Server 2025 ISO I just downloaded in the step above you want to find it wherever you saved it and click it. After click that it will fillout the fields for you. Also once all the other fields are filled at the bottom you will see a check box which says Proceed with Unattended Installation make sure you uncheck that box.

  
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


  <img width="500" height="500" alt="Image" src="https://github.com/user-attachments/assets/f329a3b5-b615-413b-9864-2e0adb1d3009" />
  
- Once restarted it will prop you to enter a password for that Administrator account. (which will be Password1).
- On the next page lets login as the Admin.
- Once logged in on the admin account lets Insert Guest addition CD image by hover to the top of the page and clicking on Devices tab ...go  down to Insert Guest Addtions CD image and click on it.
- from there in the virtual machine click on the open File Explore  scroll down to  "This PC" click it and  then double click CD Drive(D)VirtualBox Guest Addtions.
- Once inside folder scroll down until you see VBoxWindowsAddition-amd64 double click it then next and next and Install.You should geta you will have to reset Windows server popup.... click Reboot now and finsih let computer reboot.


Setting up Window Server 2025 and Static IP Configuration
---------------
<img width="310" height="300" alt="Image" src="https://github.com/user-attachments/assets/a12d8754-1b43-4431-a488-7423b8788927" />

<img width="300" height="400" alt="Image" src="https://github.com/user-attachments/assets/b1e57e5e-0bd8-4f61-8381-57b15d3d3523" />

<img width="301" height="401" alt="Image" src="https://github.com/user-attachments/assets/0cc8196f-fc6a-4e39-a139-551d4127fa8b" />


-After creating the admin account lets login useing the password that we used. (Which is Password1)


<img width="300" height="300" alt="Image" src="https://github.com/user-attachments/assets/c6b04155-9298-4944-80e9-04f61189de0b" />

- Once logged in to the Admin account the first thing that you should see pop up is the Server Manger.If not that's okay you can click on the search box at the bottom of the desktop page and type in Server manager and click on it.
 
- Now that we are in the server manager let configure the essential settings on the Windows Server.


1.Lets start by configuring the host name

  <img width="500" height="400" alt="Image" src="https://github.com/user-attachments/assets/9f4c886b-a7c7-4edd-bda0-5003a7cd1acd" />

- In server manager lets find local server on the left hand side click it.
  
<img width="413" height="333" alt="Image" src="https://github.com/user-attachments/assets/10b11d9f-babd-40c6-a4a6-9b44dd645d00" />

- Properties page should have popped up and you will see Computer name click it to change it name
  
<img width="486" height="272" alt="Image" src="https://github.com/user-attachments/assets/b2ab3163-fb4c-4e19-9338-d7e8f838a41b" />

- Once on the next page click change button at the bottom and on the new page you can change the computer name.(Changed mine to Server2025-DC01) and click okay.Will get a prompt that you have to retart your computer to apply changes click restart Now. (In a real world work environment only Server managers with Administrative Rights will be able to change the computer names)
- 
<img width="549" height="391" alt="Image" src="https://github.com/user-attachments/assets/cfe83c36-69a8-4b37-bafb-646e2124654c" />

- After restart log back in and go back to server manager and the Local server to check if the computer name has changed.
  
<img width="600" height="440" alt="Image" src="https://github.com/user-attachments/assets/5920f130-6c9b-405a-bd52-fdde0568d1ba" />
  

2.Next the time zone

<img width="500" height="600" alt="Image" src="https://github.com/user-attachments/assets/6cd0a631-9294-40c2-9839-74df53c9969d" />

- To do this right click on the time and date in the bottom right hand corner and click adjust time and date leading you to the setting page.
  
<img width="507" height="454" alt="Image" src="https://github.com/user-attachments/assets/1ceae41d-3a6d-46ee-81c7-4068d35f5695" />

- Once on the page scroll to Time zone and there you can change the time zone to where ever you need the computer to be. Then close the  window.(Once again you need to have Administrative rights to change the same as the one above)

      
3.Then making sure the server is  up to date with the most updated software update(A crucial step for setting up or looking after a Windows Server because installing updates make sure that the windows Servers are on the lastest serurity patches or big fixes and performance enhancements)

<img width="400" height="463" alt="Image" src="https://github.com/user-attachments/assets/7d718360-058e-486f-8668-a519b4397e7a" />
<img width="400" height="464" alt="Image" src="https://github.com/user-attachments/assets/92b877a9-bf35-471b-be70-aca4bd5669aa" />


-To do this lets go to hover or the window icon right click on it  and scroll and click on settings and from there find Windows Update on the left hand side.


<img width="600" height="452" alt="Image" src="https://github.com/user-attachments/assets/795bd396-b5c7-4c7f-9e85-f7881374ad89" />


-On the Windows update page you will see all the update that are avaiable you can click install all and some updates may require a computer restart click restart.

-After restart log back in and check for updates again to see if all were installed and up to date. Close the window.


<img width="600" height="458" alt="Image" src="https://github.com/user-attachments/assets/b514f935-5882-4515-83a0-9c8d546c73f2" />


4.Finally we will configure the Static IP address( Needed as a Window Server should have a static IP address to ensure consist network communication as Dynamic IP address from DHCP could change causing disruption to services like DNS or file sharing)


<img width="400" height="500" alt="Image" src="https://github.com/user-attachments/assets/980d9bd5-2721-422c-b06d-297b684b6453" />


-From the  Server Manager dashbard click on local Server on the left hand side there all the properties  will be show and let find the Ethernet section and click the that link to change it.(Should have IPv4 address assigned by DHCP,IPv6 enabled by default)

<img width="300" height="400" alt="Image" src="https://github.com/user-attachments/assets/02cd76b9-de3d-47f6-8121-f365c95f78b6" />
<img width="300" height="400" alt="Image" src="https://github.com/user-attachments/assets/83cdf3f2-999a-4697-823b-cb66ca0f1a12" />
<img width="300" height="408" alt="Image" src="https://github.com/user-attachments/assets/c8afbba1-a964-4213-81ed-38fc03496a23" />


-Once click on it right click on ethernet and then properties then on the Ethernet properties popup lets find and click on Internet Protocol version 4(TCP/IPv4) and click on properties.

<img width="300" height="436" alt="Image" src="https://github.com/user-attachments/assets/e8619581-e242-46df-a7a7-bac3bfe2053f" />


-On the General page lets click on the second option which is Use te following IP address so we can configure them. For Ip address lets add 192.168.1.10 then sudnet mask click on the field and it should automatically fill it  and for default gateway  lets add 192.168.1.1. 
-At the bottom for preferred DNS Server 127.0.0.1 if the server will act as DNS server otherwise use the network primary and click ok once done.

<img width="300" height="500" alt="Image" src="https://github.com/user-attachments/assets/3bf87860-e2f6-4340-b000-ab1bbd76dfd9" />
<img width="300" height="400" alt="Image" src="https://github.com/user-attachments/assets/8e4f5241-4e41-405a-9a2f-0eb317eb98a5" />
<img width="300" height="439" alt="Image" src="https://github.com/user-attachments/assets/5261633b-39db-466e-8ead-3ea6d212bd83" />


-Now lets open up our Command Prompt (CMD) by find the search box and typing in CMD open it.In the CMD let type ipconfig for check the Windows IP Configuration and there you should be able to see everything that you just change in the steps above.(If you want to see more info you can type ipconfig /all and it will give more of the Window Server properties)



#Installing the Active Directory (AD)
---
Here we will be doing 2 critical task:

1)Installing the Active Directory Domain Services (AD DS)role.(This step gives us the necessary components and tools for active directory on the sever setting the stage for Centralized Network management.


2)Promoting the server to a Domain Controller(DC) and creating a new domain



Let's start with Installing the AD DS role.


<img width="400" height="500" alt="Image" src="https://github.com/user-attachments/assets/d0c98df9-4117-41e3-9abc-3c6fa8c63fb8" />
<img width="294" height="205" alt="Image" src="https://github.com/user-attachments/assets/4c085571-bb10-447c-bdc1-c5a2a934a705" />

-In Server Manager you can click on Add other servers to manage or you can go to the top right corner and click on "Manage" then add roles and feature.

<img width="409" height="284" alt="Image" src="https://github.com/user-attachments/assets/47119434-eb8b-4a65-87da-c8d0382d628d" />

-You should see this pages.

+Before you begin page,click next.

<img width="445" height="315" alt="Image" src="https://github.com/user-attachments/assets/efd4e3e4-d2a5-4b7a-8ff9-daaf3c02bb6e" />

+Select installation type (By default it will chose Role-based or feature-based installation) click next.

<img width="427" height="313" alt="Image" src="https://github.com/user-attachments/assets/9bd284b4-419a-439e-a634-c88a1ad7d628" />

+Select destination server.(Which should be the server that you have created in the step above mine was Server2025-DC01)Select the Server should be the on you created by default  and hit next.


<img width="533" height="437" alt="Image" src="https://github.com/user-attachments/assets/86cdf425-a30a-4c37-a234-21be12512e5e" />

+ Select the server roles so here you select Active directory domain services once selected a pop up window will saying add features ,click the box and click Add Features and then next.

  
  <img width="428" height="313" alt="Image" src="https://github.com/user-attachments/assets/3ce73e3a-29b1-4e5e-907f-911047a645a9" />

+ Next page is the AD DS just click next nothing to do on that page.

  
<img width="527" height="458" alt="Image" src="https://github.com/user-attachments/assets/33564c19-11a7-486f-8119-79908b829c85" />

+ Finally on the last page click Install .

After install we have to promote the server to a DC.(very important  because it actives AD DS snd sets up the first domain in a new forest establishing the foundation for managing network resources securely)

<img width="329" height="155" alt="Image" src="https://github.com/user-attachments/assets/68d139ed-07f0-4591-833c-cc25a5f4a2af" />
<img width="386" height="215" alt="Image" src="https://github.com/user-attachments/assets/2c5e18fa-884f-45c0-8701-e9206bd0bf59" />

-So in the Server Manager in the right hand corner you will see a flag with a Yellow caution symbol thats the notification center, click it  and you will see  as the very first option promote server this server to a DC click the link. 

<img width="407" height="308" alt="Image" src="https://github.com/user-attachments/assets/9a5f453d-6eb3-429f-9dd0-4f3b29bc4a70" />

-On the pop up window it should be the Deployment Configuraton so here we want to create/Add a new Forest and we will have to make a Root domain Name for the forest .(Can be anything you like Im going to use mydomain.com) Click next

<img width="420" height="305" alt="Image" src="https://github.com/user-attachments/assets/cdadc9c2-635f-4b7d-9841-2574b5b4c2ff" />
<img width="394" height="290" alt="Image" src="https://github.com/user-attachments/assets/e670fa25-ca26-4379-9c76-0f30eb8df2ce" />

-On th DC options page it should default to the lastest Option unless you have to select a backward compatiblity than no need to change.After that set the Directory Service Restore Mode (DSRM) password (Im using Password1) click next.

<img width="389" height="137" alt="Image" src="https://github.com/user-attachments/assets/8e6ae801-ec3e-4472-9500-f1c1a5e114b2" />

-Next page you will see a warning but that okay click next.

<img width="433" height="311" alt="Image" src="https://github.com/user-attachments/assets/ebec3a7c-b8a5-4896-a6b0-7d872260f5e8" />

-on the next page is were you specify the net bios domain name it should be based off of your root domain name.(my root domain is mydomain.com so my bios domain will by MYDOMAIN) Click next.

<img width="410" height="301" alt="Image" src="https://github.com/user-attachments/assets/4e838f59-7330-4ac2-b2eb-e19b52011b9b" />

-Next page Paths is a default you can leave them.(You will only need to modify them if your server has a separate drives for performance or redundancy)Click next.

<img width="416" height="316" alt="Image" src="https://github.com/user-attachments/assets/af3f88c2-ce48-4379-8970-5c2bae2420c1" />

-Next page is just the review page click next.

<img width="433" height="319" alt="Image" src="https://github.com/user-attachments/assets/26afabe1-9dd8-49c4-90ef-5f423058af8c" />
<img width="431" height="304" alt="Image" src="https://github.com/user-attachments/assets/e064397d-422a-49ce-b765-f56a2c675947" />


-Now the next page the prerequisites check page  just basically check to make sure the server meets all the requirements. After the server check hit install and computer will restart after Install.

<img width="600" height="960" alt="Image" src="https://github.com/user-attachments/assets/1dcfa65c-ff1e-4a33-963f-2326585decea" />

-After restrart you can should see then login page.You should now see that you are now in the DC by seeing MYDOMAIN\Admistrator or what you have named your DC.(Mine was MYDOMAIN)


<img width="536" height="349" alt="Image" src="https://github.com/user-attachments/assets/33343d70-411a-419e-92cd-130277484fc7" />
<img width="224" height="338" alt="Image" src="https://github.com/user-attachments/assets/f98ebeaa-b3aa-4821-b4ef-b434dd5e2a2f" />

-Login into Server with the password you created.Once logged in lets verify that the DC in the server Manager on the left had side you should now see AD DS & DNS. If you see those lets go to Tools at the top right corner and click tools.In the drop down you want to make sure you have three things: Active Directory User and Computers ,DNS,and Group Policy management.If you see all three lets proceed.



<img width="551" height="397" alt="Image" src="https://github.com/user-attachments/assets/c2c87522-4f10-4a4d-bdcf-cf9d073bca13" />

-Now we test the DNS resolution. Go to the search box and search Command Prompt and enter.Once the CMD is open type in nslookup  and whatever your domain is. (Mine is nslook mydomain.com ) 


Active Directory Organizational Units(OUs) & Groups
---
In the section we will create our 

1. Organization Units(OUs) which are primarily  used for Administrative Organization , Applying Group Policies(GPOs),Delegating Control.
  
2. Groups which are collections of objects that are used to grant Permissions and Simplify management and allow creates Security Groups or Distribution Groups.


Creating a OU called employees and add groups.
---
<img width="215" height="92" alt="Image" src="https://github.com/user-attachments/assets/1e677f5c-c37c-4985-b501-fae76bf39f50" />

<img width="643" height="385" alt="Image" src="https://github.com/user-attachments/assets/99bcfbd3-ac24-40f4-bd12-37f2e9d40378" />

<img width="327" height="178" alt="Image" src="https://github.com/user-attachments/assets/47df968d-61b3-45c4-8a0f-613a8de5bc76" />

-Power on Windows Server 2025 login and in Server Manager lets go to Tools in the top right corner  click it and in the drop down tab find  Active Directory User and Computer. now you should see on the left handside the domain that you have created.(Mine was mydomain.com)   


<img width="296" height="116" alt="Image" src="https://github.com/user-attachments/assets/2dd089f0-d7d9-494f-9980-16ba76b8ce29" />

<img width="334" height="254" alt="Image" src="https://github.com/user-attachments/assets/6446c796-19aa-43ff-898c-11d22b23a354" />

<img width="331" height="269" alt="Image" src="https://github.com/user-attachments/assets/73d3f9b6-8847-489d-bae9-f40d8ea53a87" />

-Click on the arrow next to it and a drop down should appear with all the organizational untis.Right click on mydomain and find New hover over it  and there you will see oraganizational unit click on it.

<img width="308" height="229" alt="Image" src="https://github.com/user-attachments/assets/68029f3b-adba-4956-8475-db7fb4be4e66" />
-Once inside name the Organizational unit "Employees" then ok.

Now lets create Groups here are the Step to create groups:

<img width="289" height="215" alt="Image" src="https://github.com/user-attachments/assets/3fe0d318-843b-463b-8ac1-9d8ad038757e" />

1.Find Employees lets create some groups now.Right click employees and hover over New and find Group .

<img width="383" height="262" alt="Image" src="https://github.com/user-attachments/assets/5b887f5e-24f7-4a07-99f4-4c8e4fce3460" />

2.On this page create your group name Sale Department.(Make sure in Group scope Global is choosen and in Group type make sure Security is choosen then click ok.)

<img width="390" height="268" alt="Image" src="https://github.com/user-attachments/assets/ead5eaa5-ce95-46fc-8b76-a5c534d6ac23" />

3.Click Employees folder and inside you should see the sales Department in the folder.


<img width="556" height="290" alt="Image" src="https://github.com/user-attachments/assets/b68218fa-5c40-407e-9e36-410519e84f15" />


-Now lets create a couple more Groups by repeating steps 1-3 above for each Department.(IT Department, Operation Department , HR Department ,and Administration Departments)

-Now this is where you will add users in this groups 

 Before Proceding on in Windows Server 25 we need to create our Windows 11 for client side server

 
Installing Windows 11 
--
<img width="400" height="500" alt="Image" src="https://github.com/user-attachments/assets/307ab102-1dd1-4b36-a0f6-2904002e5501" /> <img width="300" height="300" alt="Image" src="https://github.com/user-attachments/assets/836da463-c320-49d0-81d5-549c7526db6a" />

-To install Windows 11 open Google and typoe in the search box "Download Windows 11" click the link.Scroll down to Windows 11 Disk Image(ISO) for x64 devices,click the drop down button and select the Windows 11 then click comfirm.

<img width="400" height="400" alt="Image" src="https://github.com/user-attachments/assets/988211ce-4fca-439c-8c2c-75a7f0480bb3" />

-Once the download is finish open up Oracle VitualBox  click on new and name it Windows 11  and go down to ISO Image and chose the file that you just download and open and it will file out the rest of te fields.(Make sure you do have the box clicked to skip Unattended Installation)

<img width="400" height="400" alt="Image" src="https://github.com/user-attachments/assets/91d27215-428a-415f-9f37-8f8c69e3df50" />

-Next tab which is the unattended Install here select the login username and password.(Here im using Cyberman for the username and the password will be password1)

<img width="400" height="400" alt="Image" src="https://github.com/user-attachments/assets/266a08aa-8da7-4ce4-a67f-7c7621126a4c" />

-Next tab is the Hardware where you chose the Base Mermory and the Processors 

<img width="400" height="400" alt="Image" src="https://github.com/user-attachments/assets/b4e418af-bccd-4f2d-be9b-f3d4792a782c" />

-Next tab hard disk here will see he have 80.00GB by default you cna keepthat and click finish.

- Windows 11 should start running automatically if not just click it and click run. Once it starts go through the install  process by selecting language ,keyboard settings and select setup option after those three pages you will come to a Product Key page selet dont have product key and next.
- 
<img width="400" height="400" alt="Image" src="https://github.com/user-attachments/assets/4d3d700f-ebb7-430a-8c3a-cbd90a63b0a7" />

- Next page select Windows 11 Pro as the OS and next Accept the term and conditions and click next on the Loction to install Windows11 and then Install and it will start installing Windows 11.

- After the install fill out the pages that are presented at the end the Windows update page should start and let it download.After update fill out all the Page after that.Windows 11 should be install and operating on your Vitualbox.

<img width="300" height="411" alt="Image" src="https://github.com/user-attachments/assets/4b3f6fca-8854-4b53-9cb1-9bc57c8ef852" />

<img width="300" height="400" alt="Image" src="https://github.com/user-attachments/assets/4dda6b7e-02aa-423b-ad15-6c4260a4f8ca" />

<img width="300" height="400" alt="Image" src="https://github.com/user-attachments/assets/f8cb3373-178c-4a2d-a177-4f91d5f28fb1" />

<img width="300" height="400" alt="Image" src="https://github.com/user-attachments/assets/fd07bf60-7a3d-4b55-b020-abf50315502e" />

<img width="300" height="400" alt="Image" src="https://github.com/user-attachments/assets/c0d3d070-3610-475f-bf7b-c6f3dfdb4f60" />

<img width="300" height="400" alt="Image" src="https://github.com/user-attachments/assets/f270c025-2f16-4942-a15b-4e004b500910" />

<img width="300" height="400" alt="Image" src="https://github.com/user-attachments/assets/9860e9e3-d63b-495c-b143-7bf3b9b45407" />


- Now once on the desktop of Windows 11  let insert Guest Additions CD images by hitting Control F on your keyboard and clicking devices at the top of the page and hovering down to Insert Guest Additions CD Image .Once you do tha like on the Folder on the Windows 11 desktop  and in thae folder find This PC on the left handside and click the CD Drive(D:) VirtualBox Guest Addtions and inside find VboxWindowsAdditions double click it and go through all the propped pages then install and you will need to Reboot.

<img width="400" height="500" alt="Image" src="https://github.com/user-attachments/assets/267c00e7-614b-4787-aef1-486cf89f3db1" />

- After the reboot login using the password you created for that account. (Mine was password1) and windows 11 is good to good on your Virtual Box.
  
<img width="400" height="522" alt="Image" src="https://github.com/user-attachments/assets/44f7b77d-c2c8-44f1-aa5e-9d7516aa7a59" />

- Now we need to create a second Windows11 and name it Windows11-2. So just repeat the same steps above(Also make User will be cyberman2)


Now back to Windows Server 2025 to create a Network between Windows 11 & Windows11-2 and Windows Server 2025
----

In your VitualBox Manager you should have Windows Server 2025 and Windows 11 & Windows11-2 now on your Vitural box.

<img width="418" height="458" alt="Image" src="https://github.com/user-attachments/assets/81f19293-849d-41c6-8a57-c464f3d986bb" />

<img width="575" height="453" alt="Image" src="https://github.com/user-attachments/assets/8008e6c9-e701-4ecd-85ba-3accd9a9a0cc" />


First lets click on Windows Server 2025 and click on settings.A tab will open on the lefthand side find Network and on the page make sure your in Adapter 1.There you will see "Attached to:" click the drop down and find Internal Network.After clicking Internal network we need to name  it.In the Name section Name it whatever you would like (Im using ADNETWORK & make sure you click the box next to cable connected) click ok.

Now lets work on finishing setting up the Windows11 & 11-2 in a simlar way.

<img width="584" height="489" alt="Image" src="https://github.com/user-attachments/assets/92a0ea4f-d53e-4079-9c21-9e31fa720e13" />

<img width="590" height="489" alt="Image" src="https://github.com/user-attachments/assets/199b7a11-8baa-4f32-9242-5032e9da84eb" />

<img width="586" height="448" alt="Image" src="https://github.com/user-attachments/assets/f2276c8d-e240-499e-85e0-cc1bde5836ab" />

Lets start with Windows 11-2 click on it and go to settings the tab will open on the lefthand side find Network and on the page make sure your in Adapter 1.There you will see "Attached to:" click the drop down and find Internal Network.After clicking Internal network we need to name  it.In the Name section Name it whatever you would like (I'm using ADNETWORK & make sure you click the box next to cable connected) click ok.

<img width="575" height="465" alt="Image" src="https://github.com/user-attachments/assets/0eb97701-8066-4d04-b56c-1f6edabe8d43" />

<img width="586" height="495" alt="Image" src="https://github.com/user-attachments/assets/691f56ee-c5d0-4ec3-a635-81bc0fd77810" />

<img width="587" height="486" alt="Image" src="https://github.com/user-attachments/assets/6de4bd2d-4cf3-4beb-8f0e-49cbe61659d6" />
  
Now do the same thing for Windows11.

Once you added the three virtual machines to the same network now we need to configure the IP addresses and subnet mask and DNS for all three machines.

<img width="443" height="433" alt="Image" src="https://github.com/user-attachments/assets/35ea3f5f-9384-441d-94e6-bb2f661eff59" />

Select Windons Server 2025 and click on start to run the VM.log in with your creditals  that we created earlier(Mine was Password1)

Do the same for Windows11 & 11-2 all three should be running.

Our next step is to need to set the static IP for all three (Important to do this because each machine requires a unique static IP to communicate with the network and the windows 11 machines  need to use the Windows Servers as their DNS server to resolve the domain name) 

<img width="400" height="526" alt="Image" src="https://github.com/user-attachments/assets/ac154290-57c3-42ef-8abe-0ddff67f6ebf" />

<img width="400" height="658" alt="Image" src="https://github.com/user-attachments/assets/3381dda8-0ae6-439d-91f4-8f5127e34db9" />

<img width="442" height="522" alt="Image" src="https://github.com/user-attachments/assets/ad824667-1f97-4acd-9f0f-26b54efd7047" />

Lets start with our Windows Server 2025  and there right click on the start icon in Windows server and find and click into system. On the left hand side find network & internet from there click into ethernet.

<img width="433" height="323" alt="Image" src="https://github.com/user-attachments/assets/6d80a2c4-6600-49d7-8911-fefff5a436a6" />

You will see your all your IP assignment and all the IPv4 settings that we configured for the Server when we created the Windows Server 2025. Click  Edit on the right handside.

<img width="433" height="323" alt="Image" src="https://github.com/user-attachments/assets/e5ada433-f102-4912-a5c4-4954e86d619d" />

Once in the IP setting make sure that the following are correct for the Windows Server 2025.

IP address:192.168.1.10

Subnet mask:255.255.255.0

Gateway:192.168.1.1

Preferred DNS: 127.0.0.1


Click save and lets move to the Windows11 and Windows11-2


<img width="400" height="500" alt="Image" src="https://github.com/user-attachments/assets/563cd3cc-e768-4ebe-872d-27ed3b71c8e0" />

<img width="400" height="422" alt="Image" src="https://github.com/user-attachments/assets/13fc1e7d-6d3d-4f88-9abc-10729bacb7a0" />

<img width="413" height="325" alt="Image" src="https://github.com/user-attachments/assets/5368c182-d149-45ab-a2e1-7b0254c4a01c" />

<img width="402" height="300" alt="Image" src="https://github.com/user-attachments/assets/81a17858-899f-44c1-bf77-32331ce0eb15" />


Lets start with Windows11. In the Windows11 VM in the search box type in Control Panel and click into it. Select Network and Internet then Network and Sharing Centre. On the lefthand side you will see change adapter setting click the link.


<img width="400" height="540" alt="Image" src="https://github.com/user-attachments/assets/e12eba60-8c7f-48b4-96af-3c14e2a496d9" />

<img width="427" height="519" alt="Image" src="https://github.com/user-attachments/assets/a3d8d3f4-cc58-4674-8304-82372efbda72" />

Right click Enthernet and find Properties, in the properties click on Internet Protocol Version 2 (TCP/IPv4) and select properties. there we need to change our IP address. (In a real-world scenario you will click on Obtain an IP address automatically becuase it will be obtaining it from DHCP server or from DHCP that is set up on your router but since we are using VM we will configure ours IP address.)

<img width="427" height="346" alt="Image" src="https://github.com/user-attachments/assets/34c3f47a-4c6b-4449-ae13-7a48f787527c" />

Click on Use the following IP address and fillout the fields with whatever you like(Im using the following:
Windows11

IP address:192.168.1.20

Subnet mask:255.255.255.0

Default gateway:192.168.1.10 (Here we use the IP address of the of the Windows Server 2025 because the machines will be connecting or talking  our windows Server)

At the bottom make sure you click:

Preferred DNS:Leave Empty 

<img width="400" height="654" alt="Image" src="https://github.com/user-attachments/assets/d56bfeca-aa2f-464d-921e-061461a8f85d" />

Once done click ok. Now do the same thing for Windows11-2.

Windows11-2

IP address:192.168.1.21

Subnet mask:255.255.255.0

Default gateway: 192.168.1.10(Here we use the IP address of the of the Windows Server 2025 because the machines will be connecting or talking  our windows Server)

At the bottom make sure you click:

Preferred DNS:  Leave Empty 


Now lets do some pinging to check if these three are able to communicate with each other.

<img width="420" height="316" alt="Image" src="https://github.com/user-attachments/assets/2fc56d78-5be9-4bb5-a080-a39e976640dc" />

Before pinging your Windows11 VM make sure that if use are Windows OS to turn off Windows Defender Firewall. I was pinging in my CMD and could not ping windows11 & 11-2 machines until I turned them off lol trail and error ( you will see in my picture below.
 when pinging for Windows Server 2025)
 
<img width="544" height="422" alt="Image" src="https://github.com/user-attachments/assets/891c5bbf-025c-4b1a-9036-d963f5d55e3b" />

Open Windows11-2 and go to CMD of the computer by searching it. Once in the command prompt let's ping our Server.

<img width="500" height="415" alt="Image" src="https://github.com/user-attachments/assets/64e43bdd-3966-47eb-a6f9-273c6fc43b12" />

Type ping the IP address of your Windows Server2025 (Mine will be ping 192.168.1.10)and  ping our Windows11 computer to make sure that the computer is able to talk (Mine will be ping 192.168.1.20) 



<img width="500" height="400" alt="Image" src="https://github.com/user-attachments/assets/692045e9-fe22-48c0-9f24-dfd1506a263d" />

Do the same for Windows 11 and ping the Server(ping 192.168.1.10) and Windows11-2(ping 192.168.1.21)

<img width="400" height="500" alt="Image" src="https://github.com/user-attachments/assets/d5b01153-8241-4b07-ad6d-ffd894d7a3cc" />

<img width="400" height="500" alt="Image" src="https://github.com/user-attachments/assets/cd95e38e-1a27-4e68-9929-e4bc587a7d12" />

<img width="400" height="500" alt="Image" src="https://github.com/user-attachments/assets/1cf538b0-be00-481c-ab61-f7734cacfad6" />

Go to our Windows Server and lets do the same thing by ping both windows11 and 11-2 computers.Go to CMD of the computer by searching it. Once in the command prompt lets ping our Server.Type ping and the IP address  of your Windows11.(Mine will be ping 192.168.1.20 ). Now lets ping our Windows11 computer to make sure that the computer is able to talk (Mine will be ping 192.168.1.21) 

Now all three machines are connected in the network!


Adding PCs/Computers to Active Directory 
--
- Fisrt thing we need to do is add both machines to the domaian to our active directory  from the two Windows11 machines. Get the Windows Vm's running by starting both Windows11 and 11-2.

- Lets start in Windows 11 and lets add this Windows to our domain. First right click on start icon and find system click on it and here  on the left handside find system again. now on that page scroll to the bottom of the page and find About click into it.

- In the About page find Advance system settings link and click on it.Once the system Properties page  click onthe Computer name tab  and click onto the change button.On the next page at the bottom lets change Member of section from Workgroup to Domain.(We want to change it to Domain because we want to add this Windows machine to the domain that we created in our windows Server which was mydomain.com or whatever you called it)

- After Click ok and a Login popup should be there just login with your login details of your Server administrator.(If you remember our username should be Administrator and the Password should be Password1)

- Thats it you will need to restart your computer do the same thing for Windows11-2.




