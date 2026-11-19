
## Windows Edition

- **Windows XP** - the popular version of windows back then that had a long running microsoft.
- **Windows Vista** - the next version after windows XP but there were many issues and eventually it phased out.
- **Windows 7** - Known as stable, user friendly, and the successor of windows vista.
- **Windows 8.x** - came and left and it was short lived like windows vista.
- **Windows 10 and 11** - the current windows OS for desktop computers.

Add ons:
- The current version of windows OS for servers is Windows Server 2025


## The Desktop (GUI)
The Windows Desktop, aka the graphical user interface or GUI in short, is the screen that welcomes you once you log into a Windows 10 machine.

![[Pasted image 20260103114804.png]]

The above screenshot is an example of a typical Windows Desktop. Each component that makes up the GUI is explained briefly below.

1. The Desktop
2. Start Menu
3. Search Box (Cortana)
4. Task View
5. Taskbar
6. Toolbars
7. Notification Area

## The Desktop
The desktop is where you will have shortcuts to programs, folders, files, etc. These icons will either be well organized in folders sorted alphabetically or scattered randomly with no specific organization on the desktop. In either case, these items are typically placed on the desktop for quick access.


## The Start Menu
In previous versions of Windows, the word **Start** was visible at the bottom left corner of the desktop GUI. The Start Menu provides access to all the apps/programs, files, utility tools, etc., that are most useful.

It have different sections

![[Pasted image 20260103120059.png]]

**1.** This section of the Start Menu provides quick shortcuts to actions that you can perform with your account or login session, such as making changes to your user account, lock your screen, or signing out of your account.

**2.** This section will show all **Recently added** apps/programs at the top and all the installed apps/programs, the first box is where the recently added apps/programs will appear. The second box is where all the installed apps/programs will appear.
![[Pasted image 20260103120726.png]] 


**3.**  The right side of the Start Menu is where you will find icons for specific apps/programs or utilities.


## Taskbar
Any apps/programs, folders, files, etc., that you open/start will appear in the taskbar.

![[Pasted image 20260103121258.png]]


## The Notification Area
This is where the date and time are displayed. Other icons possibly visible in this area like volume icon, network/wireless icon, etc.


****

## Introduction To Windows
The Windows operating system (OS) is a complex product with many system files, utilities, settings, features, etc.

**In this part of lesson i perform Remote Desktop...**

****
## The File System
The file system used in modern versions of  Windows  is the **New Technology File System** or simply  [NTFS](https://docs.microsoft.com/en-us/windows-server/storage/file-server/ntfs-overview) .

NTFS is known as a journaling file system. In case of a failure, the file system can automatically repair the folders/files on disk using information stored in a log file. This function is not possible with FAT.

NTFS addresses many of the limitations of the previous file systems; such as: 

- Supports files larger than 4GB
- Set specific permissions on folders and files
- Folder and file compression
- Encryption ( [Encryption File System](https://docs.microsoft.com/en-us/windows/win32/fileio/file-encryption) or **EFS** )

![[Pasted image 20260106212431.png]]


### Features of NTFS

####  You can set permissions that grant or deny access to files and folders.

On NTFS volumes, you can set permissions that grant or deny access to files and folders.

The permissions are:

- **Full control**
- **Modify**
- **Read & Execute**
- **List folder contents**
- **Read**
- **Write**

![[Pasted image 20260106212743.png]]

How can you view the permissions for a file or folder?

**Right click the specific Folder -> Properties -> Security Tab -> Group names (It list the users and you can see their specific permissions on that file). **

![[Pasted image 20260106213035.png]]

#### Alternate Data Streams ( ADS )
It is a file attribute specific to Windows  NTFS  (New Technology File System).

Every file has at least one data stream ( `$DATA` ), and ADS allows files to contain more than one stream of data. Natively [Window Explorer](https://support.microsoft.com/en-us/windows/what-s-changed-in-file-explorer-ef370130-1cca-9dc5-e0df-2f7416fe1cb1) doesn't display ADS to the user. There are 3rd party executables that can be used to view this data, [PowerShell](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7.1) also gives you the ability to view ADS for files.

From a security perspective, malware writers have used ADS to hide data.

Not all its uses are malicious. For example, when you download a file from the Internet, there are identifiers written to ADS to identify that the file was downloaded from the Internet.


****

## The Windows \ System32 Folders
The Windows folder ( `C:\Windows` ) is traditionally known as the folder which contains the Windows operating system.

But the file that contains OS is not only can place into C, but it can place in any drive and folder also.

This is where environment variables, more specifically system environment variables, come into play.  Even though not discussed yet, the system  environment variable for the Windows directory is `%windir%` .

Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders.

### Environment Variables 
are **named values** that store system-wide or user-specific information which programs can read and use while running.

|Variable|Meaning|
|---|---|
|`PATH`|Where Windows looks for executable programs|
|`TEMP` / `TMP`|Folder for temporary files|
|`USERPROFILE`|Current user’s home folder|
|`SYSTEMROOT`|Windows installation directory|
|`USERNAME`|Logged-in user name|
|`COMPUTERNAME`|PC name|


### There are many folders within the 'Windows' folder. See below.
![[Pasted image 20260106214110.png]]

One of the many folders is **System32** .
![[Pasted image 20260106214135.png]]


### System 32
The System32 folder holds the important files that are critical for the operating system.

You should proceed with extreme caution when interacting with this folder. Accidentally deleting any files or folders within System32 can render the Windows OS inoperational.

**Example Files in System 32**

|File|Purpose|
|---|---|
|`cmd.exe`|Command Prompt|
|`powershell.exe`|PowerShell|
|`taskmgr.exe`|Task Manager|
|`regedit.exe`|Registry Editor|
|`services.msc`|Windows Services|
|`ipconfig.exe`|Network info|
|`ping.exe`|Network testing|


****

## User Accounts, Profiles, and Permissions

User accounts can be one of two types on a typical local Windows system: **Administrator** & **Standard User**.

- An **Administrator** can make changes to the system: add users, delete users, modify groups, modify settings on the system, etc. 
- A **Standard User** can only make changes to folders/files attributed to the user & can't perform system-level changes, such as install programs.

Each user profile will have the same folders; a few of them are:
- Desktop
- Documents
- Downloads
- Music
- Pictures

**Apart from ** `Start Menu -> other User -> System Settings -> Other Users` you can access user information via **Local User and Group Management**.

#### Local User and Group Management.
Run Command -> Type: `lusrmgr.msc`

![[Pasted image 20260106215809.png]]

If you click on Groups, you see all the names of the local groups along with a brief description for each group.

Each group has permissions set to it, and users are assigned/added to groups by the Administrator. When a user is assigned to a group, the user inherits the permissions of that group. A user can be assigned to multiple groups.


****

## User Account Control

Most of Home user account in the windows systems are set as administrators that can make changes to the system.

This such a privileges doesn't need the home user for just basic uses on the system. And this will be cause of malware infect if the user have high authority in the system.

**User Account Control** - Introduced by Microsoft to protect local user with such privileges.

**How is it work?** 
- When a operation require high-level privileges needs to execute,  the user will be prompted to confirm if they permit the operation to run.

In the Security tab, we can see the users/groups and their permissions to this file. Notice that the standard user is not listed.

![[Pasted image 20260110104056.png]]


**When we are using a standard user account type and we are installing this program, there is a shield icon.

![[Pasted image 20260110104649.png]]

This shield icon is an indicator that UAC will prompt to allow higher-level privileges to install the program.

Double-click the program, and you'll see the UAC prompt. Notice that the built-in administrator account is already set as the user name and prompts the account's password. See below.

![[Pasted image 20260110104937.png]]

If the password is not entered, the UAC prompt disappears, and the program doesn't not install.


****

## Settings and the Control Panel

On a Windows system, the primary locations to make changes are the Settings menu and the Control Panel.

For a long time, the Control Panel has been the go-to location to make system changes, such as adding a printer, uninstall a program, etc.

But the Settings menu is now the primary location a user goes to if they are looking to change the system.

**There are similarities and differences between the two menus. Below are screenshots of each.**

**Settings**
![[Pasted image 20260110105345.png]]


**Control Panel**
![[Pasted image 20260110105423.png]]

You can see all the installed and also you can uninstall software in `programs` -> `Program and features`

Control Panel is the menu where you will access more complex settings and perform more complex actions. In some cases, you can start in Settings and end up in the Control Panel.

****

## Task Manager

The Task Manager provides information about the applications and processes currently running on the system. Other information is also available, such as how much CPU and RAM are being utilized, which falls under **Performance**.

![[Pasted image 20260110110446.png]]

