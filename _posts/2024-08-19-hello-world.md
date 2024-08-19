---
title: "Hello World Blog"
description: "The blog side try with write a post"
date: 2024-08-19 23:57:29 +0530
categories:
  - FirstTry
tags:
  - HelloWorld
published: true
media_subpath: /assets/
---

# Hello Word

[!INFO] > We can create an Active Directory Lab using a single client as well but there are certain AD attacks that require two clients to perform. Depending on your use case you may skip the setup of the second 2nd client.


Banner Background by [logturnal](https://www.freepik.com/free-vector/gradient-white-color-background-abstract-modern_34010189.htm) on Freepik  
Hacker Image by [catalyststuff](https://www.freepik.com/free-vector/hacker-operating-laptop-cartoon-icon-illustration-technology-icon-concept-isolated-flat-cartoon-style_11602236.htm) on Freepik

For the Active Directory (AD) Lab we are going to configure three VMs. The first VM will be the Domain Controller (DC) of the environment. We will use Windows Server 2019 for this machine. The other two VMs will be the clients that use this environment. For the client VMs, we will use Windows 10 Enterprise. 

Microsoft provided Evaluation copies for both of them. Windows Server 2019 has a license of 180 days while Windows 10 Enterprise has a license of 90 days. They should function just fine even after the evaluation period expires. After setting up the lab we will create snapshots for the VMs. The snapshots can also be used to roll back to the start of the evaluation period once it expires.  

> [!INFO] 
> We can create an Active Directory Lab using a single client as well but there are certain AD attacks that require two clients to perform. Depending on your use case you may skip the setup of the second 2nd client. 

## Downloading Windows ISO Files

### Windows Server 2019

Go to the following URL: [Windows Server 2019 \| Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019)

Click on the **`64-bit edition`** download. The ISO file is ~5GB.


### Windows 10 Enterprise

Go to the following URL: [Windows 10 Enterprise \| Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/download-windows-10-enterprise)

Click on the **`64-bit edition`** Enterprise ISO download option. The ISO file is ~5GB.


### ISO File Names

Pay attention to the names of the downloaded files. Microsoft uses the OS build number as the filename. You can rename the files to avoid confusion.


|                                          ISO Name                                          |         OS Name         |
| :----------------------------------------------------------------------------------------: | :---------------------: |
|         `17763.3650.221105-1748.rs5_release_svc_refresh_SERVER_EVAL_x64FRE_en-us`          |  `Windows Server 2019`  |
| `19045.2006.220908-0225.22h2_release_svc_refresh_CLIENTENTERPRISEEVAL_OEMRET_x64FRE_en-us` | `Windows 10 Enterprise` |

> [!INFO]
> The build number maybe different when you download the images. These are the latest versions that are available as for writing of this module (Dec, 2023).


## Creating the VMs

### Windows Server 2019

Click on <u>Tools</u> from the VirtualBox sidebar and select **`New`**.


Gave the VM a <u>name</u>. Ensure that the <u>Folder</u> option points to the location where all the Home Lab-related VMs are saved. For the <u>ISO Image</u> select the downloaded Windows Server 2019 image. Select the **`Skip Unattended Installation`** option and then click on **`Next`**. 


Increase the <u>Memory</u> to **`4096MB`** (4GB) and click on **`Next`**.


Increase the <u>Hard Drive</u> size to **`100GB`** and then click on **`Next`**.


Confirm that all the values look correct and then click on **`Finish`**.


#### Adding VM to Group

Right-click on the Windows Server 2019 VM and choose **`Move to Group -> [New]`**.


Right-click on the group name and select **`Rename Group`**. Name the group **`Active Directory`**.


Right-click on the group name (Active Directory) and choose **`Move to Group -> Home Lab`**.

The final output should look as follows:

### Windows 10 Enterprise VM1

From the VirtualBox sidebar select <u>Tools</u> and then click on **`New`**.


Give the VM a <u>name</u>. Ensure that the <u>Folder</u> option is pointing to the location where all the Home Lab VMs are saved. For the <u>ISO Image</u> option select the Windows 10 Enterprise image. Tick the **`Skip Unattended Installation`** option. Click on **`Next`** to continue.


Leave Memory and CPU on its default value. Click on **`Next`**.


Increase the <u>Hard Disk</u> size to **`100GB`** and then click on **`Next`**. 


Verify that all the options are correct and then click on **`Finish`**

#### Adding VM to Group

Right-click on the VM and then choose **`Move to Group -> Home Lab/Active Directory`**.


The final result should match the following:

### Windows 10 Enterprise VM2

Follow the same steps as above to create the VM for the second AD user. 


#### Adding VM to Group


## Configuring the VMs

### Windows Server 2019

Select the Windows Server 2019 VM and click on **`Settings`** from the toolbar.


Go to **`System -> Motherboard`**. For <u>Boot Order</u> ensure **`Hard Disk`** is not the top followed by **`Optical`**. Disable **`Floppy`**.


Go to **`Network -> Adapter 1`**. For the <u>Attacked to</u> field select **`Internal Network`**. For <u>name</u> select **`LAN 2`**. Click on **`OK`** to save the settings.


### Windows 10 Enterprise VM1

Select Windows 10 Enterprise VM1 from the sidebar and then from the toolbar choose **`Settings`**.


Go to **`System -> Motherboard`**. For <u>Boot Order</u> ensure **`Hard Disk`** is on the top followed by **`Optical`**. Disable **`Floppy`**.


Go to **`Network -> Adapter 1`**. For the <u>Attacked to</u> field select **`Internal Network`**. For <u>name</u> select **`LAN 2`**. Click on **`OK`** to save the settings.

### Windows 10 Enterprise VM2

Follow the same steps as above to change the settings for the AD User 2 VM.


## Windows Server 2019 Setup

### OS Installation

Select Windows Server 2019 from the sidebar and click on **`Start`** from the toolbar.


Click on **`Next`**.


Click on **`Install now`**.


Select **`Windows Server 2019 Standalone Evaluation (Desktop Experience)`** and click on **`Next`**.


<u>Accept</u> the agreement and click on **`Next`**.


Select **`Custom: Install Windows only (Advanced)`**.

Select **`Disk 0`** and click on **`Next`**.


The VM will restart a couple of times during the installation process.


### OS Setup & Configuration

Once the installation is complete we will be asked to set the password for the Administrator account. Once set click on **`Finish`**.


We won't be able to log in by using the **`Ctrl+Alt+Delete`** shortcut. This will open the system settings menu of the host system.

VirtualBox has a shortcut configured to perform this action. Use the shortcut **`Right Ctrl+Delete`** to access the login screen. Enter the configured password to access the VM. 

To view the configured shortcuts from the main VirtualBox wind

Select **`Input -> Virtual Machine`**. If we scroll down we should see that **`Ctrl+Alt+Delete`** has been mapped to **`Host+Delete`**. The default mapping for the host key is **`Right Ctrl`**.


Once we log in. <u>Server Manager</u> will automatically open. A popup will also open asking us to try Windows Admin Center. Click on <u>Don't show this message again</u> and then click on **`X`** to close the popup.

#### Guest Additions Installation

To make the VM screen size bigger we need to install <u>Guest Additions</u>. From the VM toolbar click on **`Devices -> Optical Devices -> Remove disk from virtual drive`**. This will remove the Windows Server 2019 image from the disk drive.  

Then select **`Devices -> Insert Guest Additions CD image`**.


From the <u>taskbar</u> open **`File Explorer`**. Once the disk is loaded it will show up in the <u>sidebar</u>. Click on it to view its content. Double-click on **`VBoxWindowsAdditions`** (4th file from bottom) to start the installer.

Click on **`Next`**.


Click on **`Next`**.


Click on **`Next`** again to install the requirement components.


Choose **`Reboot now`** and click on **`Finish`**. The VM will restart automatically.

After restart, log into the system. From the VM toolbar click on **`Devices -> Optical Drivers -> Remove disk from virtual drive`** to remove the Guest Additions image.  


Use the shortcut **`Right Ctrl+F`** to enter <u>Fullscreen mode</u>. The VM will automatically scale to fill the entire screen. Use the same shortcut to exit Fullscreen mode.

#### Network Configuration

During the pfSense setup module (Part 2) we disabled <u>DHCP</u> on the **`AD_LAB`** interface because of this our VM will not be automatically assigned an IP address. From the taskbar right-click on the <u>network icon</u> and select **`Open Network & Internet settings`**. 


Click on "<u>Change adapter options</u>".

On the Network Connections page, we should see the <u>Eth

Select **`Internet Protocol Version 4 (TCP/IPv4)`** and c

Enter the details as shown below and then click on **`OK`**. Click on **`OK`** again to close the Ethernet Properties menu.

IP address: **`10.80.80.2`**  
Subnet mask: **`255.255.255.0`**  
Default gateway: **`10.80.80.1`**  
Preferred DNS Server: **`10.80.80.2`**

Windows will display a banner to allow internet access click on **`Yes`**.


Close the Network Connections page.

In the <u>Settings app</u> click on the **`Home`** button (above search bar).

#### Renaming the System

Before we can set up the machine to be a Domain Controller l

Click on <u>About</u> on the sidebar and then click on the "<u>Rename this PC</u>" button. Give the PC an easy-to-remember name and then click on **`Next`**.


Click on "<u>Restart now</u>" for the changes to take effect.


#### Active Directory & DNS Installation

After login wait for Server Manager to load. Click on the **`Manage`** button from the top right corner and select "<u>Add Roles and Features</u>".


Click on **`Next`** till you reach the <u>Server Roles</u> page.


On this page enable "<u>Active Directory Domain Services</u>" and "<u>DNS Server</u>".


When you enable a feature the "<u>Add Roles and Features Wizard</u>" will open click on "<u>Add Features</u>" to confirm the selection.


Once both the features are selected click on **`Next`** to proceed with installation.


Click **`Next`** till you reach the Confirmation page. Here click on **`Install`** to start the installation of the selected features.


Once the installation is complete click on **`Close`** to exit the Wizard.

#### Active Directory Configuration

Click on the Flag icon present in the top right of the toolbar in Server Manager. From the dropdown click on "<u>Promote this server to a domain controller</u>".


The AD Domain Servers Configuration Wizard will open. For <u>deployment operation</u> select **`Add a new Forest`**. Give the domain a <u>name</u>. For my setup, I will be using the domain name **`ad.lab`**. After selecting the name click on **`Next`**.


> [!INFO]
> The name assigned to the domain has to be made of two words that are separated by a period.

On this page enter a <u>password</u> to use for using the AD Restore feature.


Ignore the warning that is shown and click on **`Next`**.


The <u>NetBIOS name</u> should automatically be filled. It will be the first part of the domain name. Click on **`Next`** to continue.


Click on **`Next`**.


Click on **`Next`**.


Click on **`Install`** to start the Domain Services setup process.


Once the install process is complete the machine will need to restart. Click on **`Close`** to reboot the system.


On restart, you will notice that the name that is shown on the login page has changed. The first part of the domain name is prepended to the username. This means the machine has successfully been configured as the domain controller. Log in using the Administrator password.


#### DNS Configuration

Since we enabled <u>DNS</u> on this machine (Domain Controller). This machine (DC) will act as the DNS server for devices that are connected to the **`ad.lab`** environment. For the DNS service to function properly we need to configure a <u>Forwarder</u>. Forwarder is the device to which the DNS queries will be sent when the DC cannot resolve it. In our case, we need to forward the request to <u>pfSense</u>. The DNS service of pfSense will then perform the lookup.

Open the <u>Start</u> menu expand the "<u>Windows Administrative Tools</u>" folder and select **`DNS`**.


In the sidebar select the <u>Domain Controller</u> (in my case DC1) and from the right menu double-click on "<u>Forwarders</u>".


Go to **`Forwarders -> Edit`**.


This will open the Forwarder configuration page. Enter the IP address of the **`AD_LAB`** interface (**`10.80.80.1`**) and press **`Enter`**. 


Once added. Click on **`OK`** to confirm the change.


Click on **`Apply`** then **`OK`** to save the changes.


#### DHCP Installation

Since <u>DHCP</u> is disabled on the **`AD_LAB`** interface when new devices are added they will not be assigned an IP address. We will enable the DHCP service on the DC. Once set devices that connect to the **`AD_LAB`** network will be automatically assigned an IP address by the Domain Controller DHCP server.  

Click on <u>Manage</u> from the toolbar in Server Manager. Then choose "<u>Add Roles and Features</u>".


Keep clicking **`Next`** till you reach the "<u>Server Roles</u>" page. Enable "<u>DHCP Server</u>" then click on "<u>Add Features</u>". 



Keep clicking **`Next`** till you reach the Confirmation page. Click **`Install`** to enable DHCP.


#### DHCP Configuration

After the installation is complete click on the <u>Flag</u> present in the toolbar of Server Manager and click on "<u>Complete DHCP configuration</u>".


Click on **`Commit`**.


Click on **`Close`** to complete the installation.


From the <u>Start</u> menu click on "<u>Windows Administrative Tools</u>" and then choose **`DHCP`**.


Expand the DHCP server (in my case **`dc1.ad.lab`**) dropdown on the left side of the window.

Right-click on **`IPv4`**. Then select "<u>New Scope</u>". The scope defines the range of IP addresses that can be assigned to devices by the DHCP server.



Enter a <u>Name</u> and <u>Description</u> for the new scope.



Enter the details as shown below.

Start IP address: **`10.80.80.11`**  
End IP address: **`10.80.80.253`**  
Length: **`24`**  
Subnet mask: **`255.255.255.0`**


> [!NOTE]  
> You can chose the Start IP address to be **`10.80.80.3`**. I have purposely left the starting IP addresses out of the DHCP scope. In the future if the need arises I can use these IPs for static IP assignment.  


> [!INFO]
> Since we increased the lease duration when a IP address is assigned to a device the device will be allowed to use that IP address without requesting a new IP address for 365 days. 
