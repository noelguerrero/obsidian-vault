## System Configuration and Advanced System Settings 

The **System Configuration** utility (`MSConfig`) is for advanced troubleshooting, and its main purpose is to help diagnose startup issues.

![[Pasted image 20260110115219.png]]
**Note**: You need local administrator rights to open this utility.


![[Pasted image 20260110115229.png]]

The utility has five tabs across the top. Below are the names for each tab. We will briefly cover each tab in this task. 

1. General
2. Boot
3. Services
4. Startup
5. Tools

### Tabs of Sytem Configuration
#### General Tab
we can select what devices and services for Windows to load upon boot. The options are: **Normal**, **Diagnostic**, or **Selective**.
![[Pasted image 20260110115229.png]]


#### Boot Tab
we can define various boot options for the Operating System.
![[Pasted image 20260110115510.png]]


#### Service Tab
lists all services configured for the system regardless of their state (running or stopped). A service is a special type of application that runs in the background.
![[Pasted image 20260110115640.png]]


#### Startup
To configure startup application you need to go to task manager.

Microsoft advises using **Task Manager (**`taskmgr`**)** to manage (enable/disable) startup items. The System Configuration utility is **NOT** a startup management program.

![[Pasted image 20260110115809.png]]

Unlike OS Windows 10 and 11, other OS cannot see startup configuration in the Task manager or `msconfig`, To go that you need to 

Press: `win + R` and type `shell:startup`
![[Pasted image 20260110120405.png]]

 This will display all startup programs as shortcuts or executables that are configured to run automatically the next time a user logs in. This is where you can verify applications that are configured to launch at startup.


### List of Various utilities Tools Tab
There is a list of various utilities (tools) in the Tools tab here that we can run to configure the operating system further. There is a brief description of each tool to provide some insight into what the tool is for.

![[Pasted image 20260110120658.png]]

**Note: You can find the full command of each tool below**
![[Pasted image 20260112122423.png]]

### Advance System Settings
Windows gives additional settings as well, which we can use to control performance behavior and recovery.

Search: `view advanced system settings` 

![[Pasted image 20260110121202.png]]


#### Performance Settings

Windows uses a page file as an extra virtual memory space when the physical RAM becomes full. This helps to prevent slowdowns or application crashes when the system runs out of memory.

**Page file** - The page file is a portion of your hard drive or SSD that Windows uses like extra RAM when your physical memory (RAM) is not enough.

![[Pasted image 20260110121521.png]]

![[Pasted image 20260110121716.png]]

 In this Performance tab, the **Advanced** option can also tell you about the page file size configured for the drives. In this case, it's `1048 MB`. The other settings here can give you the following information:

- The drive where the page file is stored
- The initial size (MB)
- The maximum size
- Whether Windows manages the size automatically.


#### Startup and Recovery Settings
Windows can create a crash dump file whenever it encounters a critical error, such as a Blue Screen of Death. This crash dump helps the administrators or analysts understand what went wrong during the crash.

![[Pasted image 20260110122324.png]]

![[Pasted image 20260110122339.png]]

Here, you will find different settings for the startup and recovery. The `Write debugging information` dropdown tells you the type of crash dump configured for the system. Windows supports different dump types, such as:

- Automatic memory dump
- Kernel memory dump
- Small memory dump (256 KB)
- Complete memory dump
- None

This setting shows how much information Windows will save in the crash dump when a system crash occurs.


****

## Change UAC Settings

**Continuation of System Configuration panel settings:**

This settings can me changed or even turn off (not recommended). We can move the slider to change the UAC settings. 

You can find it:
**Search:**`User Account Control Settings`

![[Pasted image 20260110163103.png]]

**This slider has 4 security levels:**

- **Always notify** - This is the highest security. Windows notifies you whenever any apps or you yourself try to make changes, and the desktop dims (Secure Desktop).
- **Notify for apps** - Windows notifies only when _apps_ try to make changes, but not when you change Windows settings. This option is enabled by default.
- **Notify without dimming** - Same as above (Notify for apps), but this time the screen does not dim.
- **Never notify** - Notifications are turned off. Windows won’t warn you about any changes made by you or any apps.


****

## Computer Management

The **Computer Management** (`compmgmt`) utility has three primary sections: System Tools, Storage, and Services and Applications.

![[Pasted image 20260110164355.png]]

### System Tools

#### A. Task Scheduler 
- The computer management allow us to create and manage common task the automatically execute of the computer (run an application, a script, etc.).
- That task can run at any point. Either log on, log off, or by schedule.

![[Pasted image 20260110164957.png]]

**Note:** It is also important to note that some scheduled tasks are not recurring and are made to run just once at a specific time.


#### B. Event Viewer
Event Viewer allows us to view events that have occurred on the computer. This is use to diagnosed problems and investigate actions executed on the system


![[Pasted image 20260110170150.png]]

**Event Viewer has three panes.**

1. The pane on the left provides a hierarchical tree listing of the event log providers. (as shown in the image above)
2. The pane in the middle will display a general overview and summary of the events specific to a selected provider.
3. The pane on the right is the actions pane.


**There are five types of events that can be logged.** 

![[Pasted image 20260110170239.png]]

**The standard logs are visible under Windows Logs**

![[Pasted image 20260110170445.png]]


#### C. Shared Folder
is where you will see a complete list of shares and folders shared that others can connect to.

![[Pasted image 20260110170859.png]]


#### D. Local Users and Groups
It discuss in Windows Fundamental 1


#### E. Performance Monitor
 is used to view performance data either in real-time or from a log file. This utility is useful for troubleshooting performance issues on a computer system, whether local or remote.
 
 ![[Pasted image 20260110171341.png]]

#### F. Device Manager
 It allows us to view and configure the hardware, such as disabling any hardware attached to the computer.

![[Pasted image 20260110171453.png]]



### Storage
Under Storage is **Windows Server Backup** and **Disk Management**. We'll only look at Disk Management in this room.

Note: the Windows Server Backup and other utilities are not visible in Win 10 & 11.

![[Pasted image 20260110171727.png]]

Disk Management is a system utility in Windows that enables you to perform advanced storage tasks.  Some tasks are:

- Set up a new drive
- Extend a partition
- Shrink a partition
- Assign or change a drive letter (ex. E:)


### Services and Applications

#### Services
Recall from the previous task, a service is a special type of application that runs in the background. You can see all the services and their statuses by clicking the Services button given under the Services and Applications section, as shown below:

![[Pasted image 20260110172813.png]]

![[Pasted image 20260110172958.png]]


#### WMI (Windows Management Instrumentation) Service 
WMI allows scripting languages (such as VBScript or Windows PowerShell) to manage Microsoft Windows personal computers and servers, both locally and remotely. Microsoft also provides a command-line interface to WMI called Windows Management Instrumentation Command-line (WMIC)._"


****

## System Information 

This tool gathers information about your computer and displays a comprehensive view of your hardware, system components, and software environment, which you can use to diagnose computer issues

How to Go or Open:
- Run Dialog and Type: `msinfo32`
- Or Cmd and type: msinfo32.exe

The information in System Summary is Divided into 3 section:
- Hardware Resources
- Components
- Software Environment

![[Pasted image 20260112105646.png]]


### System Summary 
will display general technical specifications for the computer, such as processor brand and model.

![[Pasted image 20260112105746.png]]


###  Hardware Resources 
is not for the average computer user. If you want to learn more about this section, refer to the official Microsoft [page](https://docs.microsoft.com/en-us/windows-hardware/drivers/kernel/hardware-resources#:~:text=Hardware%20resources%20are%20the%20assignable,of%20bus%2Drelative%20memory%20addresses.).

![[Pasted image 20260112105823.png]]


### Components 
you can see specific information about the hardware devices installed on the computer. Some sections don't show any information, but some sections do, such as **Display** and **Input**.

![[Pasted image 20260112105941.png]]


### Software Environment 
In this section you can see the running and installed software into the operating system. And other information such as Environmental Variables and Network Connections.

![[Pasted image 20260112110147.png]]

The Environmental variables it discuss on window fundamental 1

**Environmental Variables** - it is the a variables that holds about the information of operating system like path and location of temporary folders.

**Example of Environmental variables**
![[Pasted image 20260112110641.png]]

Another method to view **Environmental Variables:**
`Control Panel > System and Security > System > Advanced system settings > Environment Variables` 

**OR** `Settings > System > About > system info > Advanced system settings > Environment Variables`

![[Pasted image 20260112111017.png]]


****

## Resource Monitor
is a built-in diagnostic tool used to **monitor and troubleshoot system resource usage in real time**.

- One of the tool in System Configuration
- Displays per-process and aggregate CPU, memory, disk, and network usage information.
-  Providing details about which processes are using individual file handles and modules.
- Advanced filtering allows users to isolate the data related to one or more processes (either applications or services), start, stop, pause, and resume services, and close unresponsive applications from the user interface.
-  Includes a process analysis feature that can help identify deadlocked processes and file locking conflicts so that the user can attempt to resolve the conflict instead of closing an application and potentially losing data.

**Run Dialog:**`resmon`
**Cmd:**`resmon.exe`

![[Pasted image 20260112113439.png]]

**It has 4 sections:**
- CPU
- Disk
- Network
- Memory


Note that each tab has additional information for each. An image is shown below for each tab.


### CPU Section
![[Pasted image 20260112113505.png]]


### Memory Section
![[Pasted image 20260112113520.png]]


### Disk Section
![[Pasted image 20260112113535.png]]


### Network Section
![[Pasted image 20260112113553.png]]


****

## Command Prompt
is a **text-based command-line interface** in Windows that lets you **interact with the operating system by typing commands** instead of using the mouse and graphical menus.

- One of the tools in System Configuration panel
- In early operating systems, the command line was the sole way to interact with the operating system.

**Run Dialog:**`cmd`


### Simple Command

#### 1.`hostname`
The command **hostname** will output the computer name.
![[Pasted image 20260112115312.png]]

#### 2. `whoami`
The command **whoami** will output the name of the logged-in user.
![[Pasted image 20260112115400.png]]

#### 3. `ipconfig`
This command will show the network address settings for the computer.
![[Pasted image 20260112115442.png]]

#### 4. `cls`
To clear command screen

#### 5. `/?` - Help or Manual
In **command-line syntax (especially in Windows CMD)**, **`/?`** means **“show help”** for a command.

For example, to see the help manual for **ipconfig**, you can use the following command: `ipconfig /?`

![[Pasted image 20260112115846.png]]


#### 6. `netstat`
It is used to **display network connections, listening ports, and network statistics** on a computer.

![[Pasted image 20260112120156.png]]

Per the help manual (/?), this command will display protocol statistics and current TCP/IP network connections.

`netstat /?`
![[Pasted image 20260112120340.png]]
note to use the option in the image above just add `netstat` Ex: `netstat -a`


#### 7. `net`
It is used to **manage network-related services, users, and shared resources** on a computer or network.

![[Pasted image 20260112121441.png]]

To see the manual add `help`

```
net help
```
![[Pasted image 20260112121533.png]]



****


## Windows Registry
- one of the tools in System Configuration
- is a **central hierarchical database** that stores **configuration settings and options** for the Windows operating system and installed applications.

The registry contains information that Windows continually references during operation, such as:

- Profiles for each user
- Applications installed on the computer and the types of documents that each can create
- Property sheet settings for folders and application icons
- What hardware exists on the system
- The ports that are being used.

**Warning**: The registry is for advanced computer users. Making changes to the registry can affect normal computer operations.

**Run Dialog:** `regedit` Or `regedt32`
**Cmd:**`regedit.exe` Or `regedt32.exe`


![[Pasted image 20260112125622.png]]


**The registry is organized into keys and values, similar to folders and files.**

|Hive|Purpose|
|---|---|
|**HKEY_LOCAL_MACHINE (HKLM)**|System-wide settings (hardware, drivers, software)|
|**HKEY_CURRENT_USER (HKCU)**|Settings for the currently logged-in user|
|**HKEY_CLASSES_ROOT (HKCR)**|File types and program associations|
|**HKEY_USERS (HKU)**|Settings for all user profiles|
|**HKEY_CURRENT_CONFIG (HKCC)**|Current hardware configuration|