# Sec 3.1. Windows Fundamentals 1-2-3

# **Windows Fundamentals 1**

#### **Task 1 - Windows Editions**

Windows XP, Windows Vista, Windows 7, Windows 8.x, Windows 10, Windows 11 

Windows Server 2025, Windows Server 2022, Windows Server 2019, Windows Server 2016

**BitLocker** is a Windows security feature that **encrypts the entire hard drive** to protect data from unauthorized access if a device is lost, stolen, or tampered with. It uses encryption keys and may require a **recovery key** to unlock the drive.

**Answer the questions below**

> What encryption can you enable on Pro that you can't enable in Home? BitLocker
> 

#### **Task 2 - The Desktop (GUI)**

![](https://assets.tryhackme.com/additional/win-fun1/win-desktop2.png)

1. The Desktop
2. Start Menu
3. Search Box (Cortana)
4. Task View
5. Taskbar
6. Toolbars
7. Notification Area

**The Desktop:** The desktop is where you will have shortcuts to programs, folders, files, etc. 

![](https://assets.tryhackme.com/additional/win-fun1/win-desktop-menu.png)

Under **Display settings** , you can make changes to the screen's resolution and orientation. In case you have multiple computer screens, you can make configurations to the multi-screen setup here.

![](https://assets.tryhackme.com/additional/win-fun1/win-desktop-setdisplay.png)

**Note** : In a Remote Desktop session, some of the display settings will be disabled.

![](https://assets.tryhackme.com/additional/win-fun1/win-display-settings.png)

You can also change the wallpaper by selecting **Personalize** .

![](https://assets.tryhackme.com/additional/win-fun1/win-desktop-personalize.png)

Under Personalize, you can change the background image to the Desktop, change fonts, themes, color scheme, etc.

![](https://assets.tryhackme.com/additional/win-fun1/win-personalize-settings.png)

**The Start Menu:** The Start Menu provides access to all the apps/programs, files, utility tools, etc., that are most useful. Clicking on the Windows logo, the Start Menu will open. The Start Menu is broken up into sections. See below.

![](https://assets.tryhackme.com/additional/win-fun1/win-start-menu.png)

 

**The Taskbar:** Some of the components are enabled and visible by default. The Toolbar (6), for example, was enabled for demonstration purposes. If you're like me and want to disable some of these components, you can right-click on Taskbar to bring up a context menu that will allow you to make changes.

![](https://assets.tryhackme.com/additional/win-fun1/win-taskbar1.png)

Any apps/programs, folders, files, etc., that you open/start will appear in the taskbar.

![](https://assets.tryhackme.com/additional/win-fun1/win-taskbar-chrome.png)

**Answer the questions below**

> Which selection will hide/disable the Search box? Hidden
> 

> Which selection will hide/disable the Task View button? Show Task View button
> 

> Besides Clock and Network, what other icon is visible in the Notification Area?Action Center
> 

#### **Task 3 - The File System**

The file system used in modern versions of  Windows  is the **New Technology File System** or simply  [NTFS (opens in new tab)](https://docs.microsoft.com/en-us/windows-server/storage/file-server/ntfs-overview). Before NTFS, there was  **FAT16/FAT32** (File Allocation Table) and **HPFS** (High Performance File System). You still see FAT partitions in use today. For example, you typically see FAT partitions in USB devices, MicroSD cards, etc.  but traditionally not on personal Windows computers/laptops or Windows servers. NTFS is known as a journaling file system. In case of a failure, the file system can automatically repair the folders/files on disk using information stored in a log file. This function is not possible with FAT. NTFS addresses many of the limitations of the previous file systems; such as:

- Supports files larger than 4GB
- Set specific permissions on folders and files
- Folder and file compression
- Encryption ( [Encryption File System (opens in new tab)](https://docs.microsoft.com/en-us/windows/win32/fileio/file-encryption)or **EFS** )

 On NTFS volumes, you can set permissions that grant or deny access to files and folders. The permissions are:

- **Full control**
- **Modify**
- **Read & Execute**
- **List folder contents**
- **Read**
- **Write**

The below image lists the meaning of each permission on how it applies to a file and a folder. How can you view the permissions for a file or folder?

- Right-click the file or folder you want to check for permissions.
- From the context menu, select `Properties` .
- Within Properties, click on the `Security` tab.
- In the `Group or user names` list, select the user, computer, or group whose permissions you want to view.

In the below image, you can see the permissions for the `Users` group for the Windows folder.

![](https://assets.tryhackme.com/additional/win-fun1/windows-folder-permissions.png)

#### **Task 4 - The Windows\System32 Folders**

The Windows folder ( `C:\Windows` ) is traditionally known as the folder which contains the Windows operating system. The folder doesn't have to reside in the C drive necessarily. It can reside in any other drive and technically can reside in a different folder. This is where environment variables, more specifically system environment variables, come into play. Even though not discussed yet, the system  environment variable for the Windows directory is `%windir%` . 

![](https://assets.tryhackme.com/additional/win-fun1/windows-folder.png)

One of the many folders is **System32** .

![](https://assets.tryhackme.com/additional/win-fun1/windows-system32.png)

The System32 folder holds the important files that are critical for the operating system.

**Answer the questions below**

> What is the system variable for the Windows folder? %windir%
> 

#### **Task 5 - User Accounts, Profiles, and Permissions**

User accounts can be one of two types on a typical local Windows system: **Administrator** & **Standard User**. The user account type will determine what actions the user can perform on that specific Windows system.

- An Administrator can make changes to the system: add users, delete users, modify groups, modify settings on the system, etc.
- A Standard User can only make changes to folders/files attributed to the user & can't perform system-level changes, such as install programs.

One way is to click the `Start Menu` and type `Other User`. A shortcut to `System Settings > Other users` should appear.

![](https://assets.tryhackme.com/additional/win-fun1/win-other-user1.png)

If you click on it, a Settings window should now appear. See below.

![](https://assets.tryhackme.com/additional/win-fun1/win-other-user.png)

Since you're the Administrator, you see an option to **Add someone else to this PC**. Click on the local user account. More options should appear: **Change account type** and **Remove**.

![](https://assets.tryhackme.com/additional/win-fun1/win-other-user2.png)

Click on Change account type. The value in the drop-down box (or the highlighted value if you click the drop-down) is the current account type.

![](https://assets.tryhackme.com/additional/win-fun1/win-other-user3.png)

When a user account is created, a profile is created for the user. The location for each user profile folder will fall under is C:\Users. For example, the user profile folder for the user account Max will be C:\Users\Max.

The creation of the user's profile is done upon initial login. When a new user account logs in to a local system for the first time, they'll see several messages on the login screen. One of the messages, User Profile Service, sits on the login screen for a while, which is at work creating the user profile. See below.

![](https://assets.tryhackme.com/additional/win-fun1/win-profile-service.png)

Once logged in, the user will see a dialog box similar to the one below (again), indicating that the profile is in creation.

![](https://assets.tryhackme.com/additional/win-fun1/win-profile-service2.png)

 

Another way to access this information, and then some, is using **Local User and Group Management**. Right-click on the Start Menu and click **Run**. Type `lusrmgr.msc`. See below

![](https://assets.tryhackme.com/additional/win-fun1/win-lusrmgr.gif)

**Note**: The Run Dialog Box allows us to open items quickly. Back to lusrmgr, you should see two folders: **Users** and **Groups**. If you click on Groups, you see all the names of the local groups along with a brief description for each group. Each group has permissions set to it, and users are assigned/added to groups by the Administrator. When a user is assigned to a group, the user inherits the permissions of that group. A user can be assigned to multiple groups. **Note**: If you click on **Add someone else to this PC** from **Other users**, it will open **Local Users and Management**.

**Answer the questions below**

> What is the name of the other user account? tryhackmebilly
What groups is this user a member of? Remote Desktop Users,Users
What built-in account is for guest access to the computer? Guest
What is the account description? window$Fun1!
> 

#### **Task 6 - User Account Control**

To protect the local user with such privileges, Microsoft introduced **User Account Control** (UAC). **Note** : UAC (by default) doesn't apply for the built-in local administrator account.

How does UAC work? When a user with an account type of administrator logs into a system, the current session doesn't run with elevated permissions. When an operation requiring higher-level privileges needs to execute, the user will be prompted to confirm if they permit the operation to run. In the Security tab, we can see the users/groups and their permissions to this file. Notice that the standard user is not listed.

![](https://assets.tryhackme.com/additional/win-fun1/win-wireshark.png)

Log in as the standard user and try to install this program. To do this, you can remote desktop into the machine as the standard user account. **Note** : You have the username and password for the standard user. It's visible in `lusrmgr.msc` . Before installing the program, notice the icon. Do you see the difference?  When you're logged in as the standard user, the shield icon is on the program's default icon. See below.

![](https://assets.tryhackme.com/additional/win-fun1/win-wireshark.png)

This shield icon is an indicator that UAC will prompt to allow higher-level privileges to install the program.

![](https://assets.tryhackme.com/additional/win-fun1/win-wireshark2.png)

Double-click the program, and you'll see the UAC prompt. Notice that the built-in administrator account is already set as the user name and prompts the account's password. See below.

![](https://assets.tryhackme.com/additional/win-fun1/win-uac.png)

**Answer the questions below**

> What does UAC mean? User Account Control
> 

#### **Task 7 - Settings and the Control Panel**

**Settings** :

![](https://assets.tryhackme.com/additional/win-fun1/win-settings.png)

**Control Panel** :

![](https://assets.tryhackme.com/additional/win-fun1/win-control-panel.png)

Now, if you want to see which applications are installed on the system, click `Programs` button shown here in the control panel. Then select `Programs and Features`. This will list all installed applications along with their names, publishers, and versions. In this way, you can verify any software that has been added to the system. The screenshot below shows the installed applications of another machine through this feature:

![](https://assets.tryhackme.com/additional/win-fun1/win-settings-cp.png)

For example, in Settings, click on **Network & Internet** . From here, click on **Change adapter options** .

![](https://assets.tryhackme.com/additional/win-fun1/win-change-adapter1.png)

Notice that the next window that pops up is from the Control Panel.

![](https://assets.tryhackme.com/additional/win-fun1/win-change-adapter2.png)

If you're unclear which to open if you wish to change a setting, use the Start menu and search for it.

![](https://assets.tryhackme.com/additional/win-fun1/win-change-wallpaper.png)

If we click on the Best match, a window to the Settings menu appears to make changes to the wallpaper.

![](https://assets.tryhackme.com/additional/win-fun1/win-change-wallpaper2.png)

**Answer the questions below**

> In the Control Panel, change the view to Small icons. What is the last setting in the Control Panel view? Windows Defender Firewall
> 

#### **Task 8 - Task Manager**

The Task Manager provides information about the applications and processes currently running on the system. Other information is also available, such as how much CPU and RAM are being utilized, which falls under **Performance**.

![](https://assets.tryhackme.com/additional/win-fun1/win-task-manager.png)

Task Manager will open in Simple View and won't show much information.

![](https://assets.tryhackme.com/additional/win-fun1/win-task-manager2.png)

Click on `More details`, and the view changes.

![](https://assets.tryhackme.com/additional/win-fun1/win-task-manager3.png)

**Answer the questions below**

> What is the keyboard shortcut to open Task Manager? Ctrl+Shift+Esc
> 

# **Windows Fundamentals 2**

#### **Task 1 - System Configuration and Advanced System Settings**

The **System Configuration** utility (`MSConfig`) is for advanced troubleshooting, and its main purpose is to help diagnose startup issues.

![](https://assets.tryhackme.com/additional/win-fun2/msconfig-start.png)

The utility has five tabs across the top. Below are the names for each tab. We will briefly cover each tab in this task.

1. General
2. Boot
3. Services
4. Startup
5. Tools

![](https://assets.tryhackme.com/additional/win-fun2/msconfig1.png)

![](https://assets.tryhackme.com/additional/win-fun2/msconfig2.png)

![](https://assets.tryhackme.com/additional/win-fun2/msconfig3.png)

![](https://assets.tryhackme.com/additional/win-fun2/msconfig4.png)

**Task Manager (**`taskmgr`**)** to manage (enable/disable) startup items. The System Configuration utility is **NOT** a startup management program.

**Advanced System Settings:** 


<img width="665" height="772" alt="image" src="https://github.com/user-attachments/assets/76bb339f-509d-4c73-b377-98a7a1966d3c" />


**Answer the questions below**

> What is the name of the service that lists Systems Internals as the manufacturer? PsShutdown 
Whom is the Windows license registered to? Windows User
What is the command for Windows Troubleshooting? C:\Windows\System32\control.exe /name Microsoft.Troubleshooting 
What command will open the Control Panel? (The answer is  the name of .exe, not the full path) control.exe
> 

#### **Task 2 - Change UAC Settings**

- **Always notify:** This is the highest security. Windows notifies you whenever any apps or you yourself try to make changes, and the desktop dims (Secure Desktop).
- **Notify for apps**: Windows notifies only when *apps* try to make changes, but not when you change Windows settings. This option is enabled by default.
- **Notify without dimming:** Same as above (Notify for apps), but this time the screen does not dim.
- **Never notify:** Notifications are turned off. Windows won’t warn you about any changes made by you or any apps.

You can find the current level by looking at the position of the slider in the `User Account Control settings` window, as shown below:

![](https://assets.tryhackme.com/additional/win-fun2/uac.png)

**Answer the questions below**

> What is the command to open User Account Control Settings?
> 

UserAccountControlSettings.exe

#### **Task 3 - Computer Management**

The **Computer Management** (`compmgmt`) ****utility has three primary sections: System Tools, Storage, and Services and Applications.

![](https://assets.tryhackme.com/additional/win-fun2/compmgmt1.png)

**System Tools**


<img width="495" height="227" alt="image 1" src="https://github.com/user-attachments/assets/67406a0c-f363-4062-9ae1-5ea04eef8d8f" />


**Shared Folders** is where you will see a complete list of shares and folders shared that others can connect to.

![](https://assets.tryhackme.com/additional/win-fun2/shared-folders.png)

In the above image, under Shares, are the default share of Windows, C$, and default remote administration shares created by Windows, such as ADMIN$. In **Performance**, you'll see a utility called **Performance Monitor** (`perfmon`). Perfmon is used to view performance data either in real-time or from a log file. This utility is useful for troubleshooting performance issues on a computer system, whether local or remote.

![](https://assets.tryhackme.com/additional/win-fun2/perfmon.png)

**Device Manager** allows us to view and configure the hardware, such as disabling any hardware attached to the computer.

![](https://assets.tryhackme.com/additional/win-fun2/device-mgr.png)

**Storage:** Under Storage is **Windows Server Backup** and **Disk Management**. We'll only look at Disk Management in this room.

![](https://assets.tryhackme.com/additional/win-fun2/disk-mgmt.png)

**Services and Applications**


<img width="492" height="213" alt="image 2" src="https://github.com/user-attachments/assets/8e6eb80e-5f88-4bdc-979f-7b657262bbe1" />


**Answer the questions below**

> What is the command to open Computer Management? compmgmt.msc
> 

> When is the npcapwatchdog scheduled task set to run at? At system startup
> 

> What is the name of the hidden folder that is shared? sh4r3dF0Ld3r
> 

#### **Task 4 - System Information**

What is the **System Information** (`msinfo32`) tool? *Windows includes a tool called Microsoft System Information (Msinfo32.exe).  This tool gathers information about your computer and displays a comprehensive view of your hardware, system components, and software environment, which you can use to diagnose computer issues.* The  information in **System Summary** is divided into three sections:

- **Hardware Resources**
- **Components**
- **Software Environment**

System Summary will display general technical specifications for the computer, such as processor brand and model.

![](https://assets.tryhackme.com/additional/win-fun2/system-summary.png)

The information displayed in **Hardware Resources** is not for the average computer user. If you want to learn more about this section, refer to the official Microsoft [page(opens in new tab)](https://docs.microsoft.com/en-us/windows-hardware/drivers/kernel/hardware-resources#:~:text=Hardware%20resources%20are%20the%20assignable,of%20bus%2Drelative%20memory%20addresses.).

![](https://assets.tryhackme.com/additional/win-fun2/hardware-resources.png)

![](https://assets.tryhackme.com/additional/win-fun2/env-variables.png)

*Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders.* 

Another method to view environment variables is `Control Panel > System and Security > System > Advanced system settings > Environment Variables` **OR** `Settings > System > About > system info > Advanced system settings > Environment Variables`.

![](https://assets.tryhackme.com/additional/win-fun2/env-variables2.png)

The detour is over. Let's redirect our attention back to `msinfo32` and pick up where we left off. Towards the very bottom of this utility, there is a search bar. Please give it a go. Select Components and search for `IP address`.

![](https://assets.tryhackme.com/additional/win-fun2/msinfo32-search.png)

**Answer the questions below**

> What is the command to open System Information? msinfo32.exe
What is listed under System Name? THM-WINFUN2
Under Environment Variables, what is the value for ComSpec? %SystemRoot%\system32\cmd.exe
> 

#### **Task 5 - Resource Monitor**

What is **Resource Monitor** (`resmon`)?  *Resource Monitor displays per-process and aggregate CPU, memory, disk, and network usage information, in addition to providing details about which processes are using individual file handles and modules. Advanced filtering allows users to isolate the data related to one or more processes (either applications or services), start, stop, pause, and resume services, and close unresponsive applications from the user interface. It also includes a process analysis feature that can help identify deadlocked processes and file locking conflicts so that the user can attempt to resolve the conflict instead of closing an application and potentially losing data.* In the Overview tab, Resmon has four sections:

- **CPU**
- **Disk**
- **Network**
- **Memory**

![](https://assets.tryhackme.com/additional/win-fun2/resmon1.png)

**Answer the questions below**

> What is the command to open Resource Monitor? resmon.exe
> 

#### **Task 6 - Command Prompt**

The command prompt (`cmd`) can seem daunting at first, but it's really not that bad once you understand how to interact with it. The command **hostname** will output the computer name.

![](https://assets.tryhackme.com/additional/win-fun2/hostname.png)

The command **whoami** will output the name of the logged-in user.

![](https://assets.tryhackme.com/additional/win-fun2/whoami.png)

 A command used often is `ipconfig`. This command will show the network address settings for the computer.

![](https://assets.tryhackme.com/additional/win-fun2/ipconfig.png)

A  command to retrieve the help manual for a command is `/?`.

For example, to see the help manual for **ipconfig**, you can use the following command: `ipconfig /?`

![](https://assets.tryhackme.com/additional/win-fun2/ipconfig-help.png)

**Note**: To clear the command prompt screen, the command is `cls`. The next command is `netstat`. Per the help manual, this command will display protocol statistics and current TCP/IP network connections.

![](https://assets.tryhackme.com/additional/win-fun2/netstat.png)

The structure tells us the **netstat** command can be run alone or with parameters, such as `-a`,  `-b`,  `-e`, etc. When any of the parameters are appended to the root command, **netstat** in this case, the output changes. Play with a few to see for yourself. The `net` command is primarily used to manage network resources. This command supports sub-commands. If you type **net** without a sub-command, the output will show the syntax for the root command showing a few of the sub-commands you can use.

![](https://assets.tryhackme.com/additional/win-fun2/net.png)

For the net command, to display the help manual `/?` will not work. In this case, you need to use different syntax, which is `net help`.

![](https://assets.tryhackme.com/additional/win-fun2/net-help.png)

So, if you wish to see the help information for `net user` , the command is `net help user`.

![](https://assets.tryhackme.com/additional/win-fun2/net-help-user2.png)

**Answer the questions below**

> In System Configuration, what is the full command for Internet Protocol Configuration? C:\Windows\System32\cmd.exe /k %windir%\system32\ipconfig.exe 
For the ipconfig command, how do you show detailed information? ipconfig /all
> 

#### **Task 7 - Registry Editor**

The **Windows Registry** (per Microsoft) is a central hierarchical database used to store information necessary to configure the system for one or more users, applications, and hardware devices. The registry contains information that Windows continually references during operation, such as:

- Profiles for each user
- Applications installed on the computer and the types of documents that each can create
- Property sheet settings for folders and application icons
- What hardware exists on the system
- The ports that are being used.

There are various ways to view/edit the registry. One way is to use the **Registry Editor** (`regedit`).

![](https://assets.tryhackme.com/additional/win-fun2/regedit.png)

# **Windows Fundamentals 3**

#### **Task 1 - Introduction**

- In [Windows Fundamentals 1](https://tryhackme.com/room/windowsfundamentals1xbx), we covered the desktop, the file system, user account control, the control panel, settings, and the task manager.
- In [Windows Fundamentals 2](https://tryhackme.com/room/windowsfundamentals2x0x), we covered various utilities, such as System Configuration, Computer Management, Resource Monitor, etc.

#### **Task 2 - Windows Updates**

Updates are typically released on the 2nd Tuesday of each month. This day is called **Patch Tuesday**. That doesn't necessarily mean that a critical update/patch has to wait for the next Patch Tuesday to be released. If the update is urgent, then Microsoft will push the update via the Windows Update service to the Windows devices.

#### **Task 3 - Windows Security**

Per Microsoft, "***Windows Security** is your home to manage the tools that protect your device and your data*".

![](https://assets.tryhackme.com/additional/win-fun3/windows-security.png)

In the above image, focus your attention on **Protection areas**.

- **Virus & threat protection**
- **Firewall & network protection**
- **App & browser control**
- **Device security**

![](https://assets.tryhackme.com/additional/win-fun3/windows-security2.png)

**Answer the questions below**

> Checking the Security section on your VM, which area needs immediate attention? Virus & threat protection
> 

#### **Task 4 - Virus & threat protection**

Virus & threat protection is divided into two parts:

- **Current threats**
- **Virus & threat protection settings**

The image below only focuses on **Current threats**.

![](https://assets.tryhackme.com/additional/win-fun3/windows-security3.png)

**Scan options**

- **Quick scan** - Checks folders in your system where threats are commonly found.
- **Full scan** - Checks all files and running programs on your hard disk. This scan could take longer than one hour.
- **Custom scan** - Choose which files and locations you want to check.

**Threat history**

- **Last scan** - Windows Defender Antivirus automatically scans your device for viruses and other threats to help keep it safe.
- **Quarantined threats** - Quarantined threats have been isolated and prevented from running on your device. They will be periodically removed.
- **Allowed threats** - Allowed threats are items identified as threats, which you allowed to run on your device.

**Warning**: Allow an item to run that has been identified as a threat only if you are **100%** sure of what you are doing.

Next is **Virus & threat protection settings**.

![](https://assets.tryhackme.com/additional/win-fun3/windows-security4.png)

**Virus & threat protection settings**

- **Real-time protection** - Locates and stops malware from installing or running on your device.
- **Cloud-delivered protection** - Provides increased and faster protection with access to the latest protection data in the cloud.
- **Automatic sample submission** - Send sample files to Microsoft to help protect you and others from potential threats.
- **Controlled folder access** - This feature, if enabled, protects files, folders, and memory areas on your device from unauthorized changes by malicious or unknown applications. If it is enabled, only approved and trusted apps would be allowed to modify the files in the protected folders. To enable this feature, click on the `Manage controlled folder access` button under `Controlled Folder Access` and turn it on.
- **Exclusions** Windows Defender Antivirus allows you to exclude any files or folders from the antivirus scanning. This is done to reduce the number of false positives. Administrators might not want the antivirus to scan specific files or folders. By adding them to the exclusions list, the antivirus would ignore them and scan all the other files and folders. To add any file or folder to the Windows Defender exclusion list, click on the `Add or remove exclusions` button under `Exclusions` and add as many exclusions as you want.
- **Notifications** - Windows Defender Antivirus will send notifications with critical information about the health and security of your device.

Warning: Excluded items could contain threats that make your device vulnerable. Only use this option if you are **100%** sure of what you are doing.

**Virus & threat protection updates**

- **Check for updates** - Manually check for updates to update Windows Defender Antivirus definitions.

**Ransomware protection**

- **Controlled folder access** - Ransomware protection requires this feature to be enabled, which in turn requires Real-time protection to be enabled.

**Answer the questions below**
Specifically, what is turned off that Windows is notifying you to turn on? Real-time protection

#### **Task 5 - Firewall & network protection**

What is a **firewall**? "*Traffic flows into and out of devices via what we call ports. A firewall is what controls what is - and more importantly isn't - allowed to pass through those ports. You can think of it like a security guard standing at the door, checking the ID of everything that tries to enter or exit*".

![](https://assets.tryhackme.com/additional/win-fun3/windows-firewall.png)

Per Microsoft, "*Windows Firewall offers three firewall profiles: domain, private and public".*

- **Domain** - *The domain profile applies to networks where the host system can authenticate to a domain controller.*
- **Private** - *The private profile is a user-assigned profile and is used to designate private or home networks.*
- **Public** - *The default profile is the public profile, used to designate public networks such as Wi-Fi hotspots at coffee shops, airports, and other locations.*

If you click on any firewall profile, another screen will appear with two options: **turn the firewall on/off** and **block all incoming connections**.

![](https://assets.tryhackme.com/additional/win-fun3/windows-firewall2.png)

**Warning**: Unless you are **100%** confident in what you are doing, it is recommended that you leave your Windows Defender Firewall enabled.

**Allow an app through firewall**

![](https://assets.tryhackme.com/additional/win-fun3/windows-firewall3.png)

You can view what the current settings for any firewall profile are. In the above image, several apps have access in the Private and/or Public firewall profile. Some of the apps will provide additional information if it's available via the `Details` button.

**Advanced Settings**

![](https://assets.tryhackme.com/additional/win-fun3/windows-firewall4.png)

Configuring the **Windows Defender Firewall** is for advanced Windows users. Refer to the following Microsoft documentation on best practices [here(opens in new tab)](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/best-practices-configuring).**Tip:** Command to open the Windows Defender Firewall is `WF.msc`.

**Answer the questions below**

> If you were connected to airport Wi-Fi, what most likely will be the active firewall profile? Public network
> 

#### **Task 6 - App & browser control**

"*Microsoft Defender SmartScreen protects against phishing or malware websites and applications, and the downloading of potentially malicious files*".

![](https://assets.tryhackme.com/additional/win-fun3/windows-app-control.png)

**Check apps and files**

- **Windows Defender SmartScreen** helps protect your device by checking for unrecognized apps and files from the web.

![](https://assets.tryhackme.com/additional/win-fun3/windows-smartscreen.png)

**Exploit protection**

- Exploit protection is built into Windows 10 (and, in our case, Windows Server 2019) to help protect your device against attacks.

![](https://assets.tryhackme.com/additional/win-fun3/windows-exploit-protection.png)

#### **Task 7 - Device security**

Even though you'll probably never change any of these settings, for completion's sake, it will be covered briefly.

![](https://assets.tryhackme.com/additional/win-fun3/windows-device-sec.png)

**Core isolation**

- **Memory Integrity** - Prevents attacks from inserting malicious code into high-security processes.

![](https://assets.tryhackme.com/additional/win-fun3/windows-mem-integrity2.png)

Warning: Unless you are 100% confident in what you are doing, it is recommended that you leave the default settings. The below images are from another machine to show another security feature that should be available in a personal Windows 10 device.

![](https://assets.tryhackme.com/additional/win-fun3/windows-sec-processor.png)

![](https://assets.tryhackme.com/additional/win-fun3/windows-tpm.png)

What is the **Trusted Platform Module** (**TPM**)? "*Trusted Platform Module (TPM) technology is designed to provide hardware-based, security-related functions. A TPM chip is a secure crypto-processor that is designed to carry out cryptographic operations. The chip includes multiple physical security mechanisms to make it tamper-resistant, and malicious software is unable to tamper with the security functions of the TPM*".

**Answer the questions below**

> What is the TPM? Trusted Platform Module
> 

#### **Task 8 - BitLocker**

What is **BitLocker**? "*BitLocker Drive Encryption is a data protection feature that integrates with the operating system and addresses the threats of data theft or exposure from lost, stolen, or inappropriately decommissioned computers*".

On devices with TPM installed, BitLocker offers the best protection. Per Microsoft, "*BitLocker provides the most protection when used with a Trusted Platform Module (TPM) version 1.2 or later. The TPM is a hardware component installed in many newer computers by the computer manufacturers. It works with BitLocker to help protect user data and to ensure that a computer has not been tampered with while the system was offline*".

**Answer the questions below**

> We should use a removable drive on systems without a TPM version 1.2 or later. What does this removable drive contain? startup key
> 

#### **Task 9 - Volume Shadow Copy Service**

the Volume Shadow Copy Service (VSS) coordinates the required actions to create a consistent shadow copy (also known as a snapshot or a point-in-time copy) of the data that is to be backed up. Volume Shadow Copies are stored on the System Volume Information folder on each drive that has protection enabled. If VSS is enabled (**System Protection** turned on), you can perform the following tasks from within **advanced system settings**.

- **Create a restore point**
- **Perform system restore**
- **Configure restore settings**
- **Delete restore points**

![](https://assets.tryhackme.com/additional/win-fun3/vss1.png)

![](https://assets.tryhackme.com/additional/win-fun3/vss2.png)

> What is VSS? Volume Shadow Copy Service
> 

### Windows Fundamentals 1

This document provides an introduction to the fundamentals of the Windows operating system, focusing on essential features, user management, file systems, and system administration concepts commonly encountered in IT and cybersecurity.

**Key topics covered:**

- **Windows Editions:** Introduces various Windows desktop and server versions and highlights differences between editions, such as the availability of **BitLocker** encryption in Windows Pro.
- **Desktop and Graphical User Interface (GUI):** Explains the main components of the Windows interface, including the Desktop, Start Menu, Taskbar, Search Box, Notification Area, and personalization settings.
- **NTFS File System:** Describes the New Technology File System (NTFS), its advantages over FAT, and features such as journaling, file permissions, compression, encryption (EFS), and support for large files.
- **System32 Folder:** Explains the importance of the `C:\Windows\System32` directory, which stores critical operating system files, and introduces the `%windir%` environment variable.
- **User Accounts and Permissions:** Covers Administrator and Standard User accounts, user profiles, local groups, and how permissions are inherited through group membership.
- **User Account Control (UAC):** Discusses how UAC enhances security by requiring administrator approval before privileged actions can be performed.
- **Settings vs. Control Panel:** Compares the modern Settings application with the traditional Control Panel and explains how each is used to manage Windows configurations.
- **Task Manager:** Introduces Task Manager as a tool for monitoring running applications, processes, system performance, and resource usage.

Overall, the material provides a solid foundation for understanding the Windows operating system, including its interface, file management, security mechanisms, and administrative tools, making it valuable for beginners in IT support, system administration, and cybersecurity.

### Windows Fundamentals 2

**Windows Fundamentals 2** expands on core Windows administration and system management concepts, introducing essential tools used for troubleshooting, monitoring, and securing Windows systems. It is designed to help beginners in IT and cybersecurity understand how Windows operates behind the scenes.

**Key Topics Covered**

- **System Configuration (MSConfig):** Introduces the MSConfig utility for diagnosing startup issues and managing boot options, services, startup programs, and troubleshooting tools.
- **User Account Control (UAC):** Explains the different UAC notification levels and how UAC protects Windows by requiring administrative approval before privileged actions are performed.
- **Computer Management:** Covers the Computer Management console, including Shared Folders, Device Manager, Disk Management, Performance Monitor, Task Scheduler, and Services, providing centralized administration of system resources.
- **System Information (MSInfo32):** Demonstrates how to view detailed information about hardware, software, drivers, environment variables, and system components to assist with diagnostics and troubleshooting.
- **Resource Monitor:** Introduces Resource Monitor as a tool for analyzing CPU, memory, disk, and network utilization, helping identify performance bottlenecks and resource-intensive processes.
- **Command Prompt (CMD):** Covers essential command-line utilities such as `hostname`, `whoami`, `ipconfig`, `netstat`, and `net`, along with using help commands to explore available options for system and network administration.
- **Windows Registry:** Provides an introduction to the Windows Registry and Registry Editor (`regedit`), explaining its role as the central database that stores operating system, hardware, application, and user configuration settings.

**Overall Summary**

This module builds upon the foundational knowledge introduced in Windows Fundamentals 1 by focusing on Windows administration, diagnostics, and troubleshooting tools. It equips learners with practical skills for managing system configuration, monitoring performance, gathering system information, using command-line utilities, and understanding the Windows Registry. These concepts are essential for IT support professionals, system administrators, and aspiring cybersecurity practitioners who need to maintain, troubleshoot, and secure Windows environments.

### Windows Fundamentals 3

**Windows Fundamentals 3** focuses on Windows security features, system protection, and update mechanisms. It introduces the built-in tools that help protect Windows devices from malware, unauthorized access, and data loss, making it an essential module for IT support and cybersecurity beginners.

**Key Topics Covered**

- **Windows Updates:** Explains the importance of keeping Windows up to date through Windows Update and introduces **Patch Tuesday**, Microsoft's regular monthly security update release schedule.
- **Windows Security:** Provides an overview of the Windows Security dashboard, including protection areas such as Virus & Threat Protection, Firewall & Network Protection, App & Browser Control, and Device Security.
- **Virus & Threat Protection:** Covers Microsoft Defender Antivirus features, including Quick, Full, and Custom scans, real-time protection, cloud-delivered protection, ransomware protection, exclusions, and threat history management.
- **Firewall & Network Protection:** Explains how Windows Defender Firewall secures network communications using Domain, Private, and Public firewall profiles, and discusses firewall rules and application permissions.
- **App & Browser Control:** Introduces Microsoft Defender SmartScreen and Exploit Protection, which help defend against phishing attacks, malicious downloads, and software exploits.
- **Device Security:** Describes hardware-based security technologies such as **Trusted Platform Module (TPM)** and **Memory Integrity**, which enhance system protection against tampering and advanced attacks.
- **BitLocker Drive Encryption:** Explains how BitLocker encrypts drives to protect sensitive data and highlights the role of TPM in securely managing encryption keys.
- **Volume Shadow Copy Service (VSS):** Introduces VSS as a backup and recovery feature that enables system restore points, snapshots, and file recovery to help restore systems after failures or malware incidents.

**Overall Summary**

Windows Fundamentals 3 emphasizes the security features built into modern Windows operating systems. It covers system updates, antivirus protection, firewalls, encryption, hardware security, and recovery mechanisms that help defend against cyber threats and data loss. Together, these concepts provide a strong foundation for understanding how Windows safeguards devices, making this knowledge valuable for IT professionals, system administrators, and cybersecurity practitioners.
