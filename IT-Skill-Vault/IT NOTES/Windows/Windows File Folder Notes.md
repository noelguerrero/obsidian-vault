
### Common Windows System Folders

|Folder|Description|Purpose|
|---|---|---|
|**C:\Windows**|Contains the Windows operating system files.|Stores the core files required for Windows to boot and function.|
|**C:\Program Files**|Default installation folder for **64-bit applications**.|Keeps installed applications separated from system files.|
|**C:\Program Files (x86)**|Default installation folder for **32-bit applications** on a 64-bit Windows.|Allows older 32-bit software to run properly.|
|**C:\Users**|Contains profiles for every user account.|Stores each user's personal files and settings.|
|**C:\ProgramData**|Hidden folder shared by all users.|Stores application data accessible to every user on the computer.|
|**C:\PerfLogs**|Performance Logs folder.|Stores performance monitoring and diagnostic logs.|
|**C:\Recovery**|Recovery environment files.|Used to repair or recover Windows if it fails to boot.|
|**C:\System Volume Information**|Protected system folder.|Stores System Restore points, indexing data, and file system metadata.|
|**C:$Recycle.Bin**|Hidden Recycle Bin folder.|Temporarily stores deleted files before permanent deletion.|
|**C:\Boot** _(Legacy BIOS systems)_|Boot configuration files.|Contains files needed during the Windows boot process.|
|**C:\Windows.old**|Previous Windows installation.|Created after upgrading or reinstalling Windows, allowing rollback or file recovery.|

---

### Important Subfolders Inside `C:\Windows`

| Folder                   | Description                                                            | Purpose                                                                       |
| ------------------------ | ---------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| **System32**             | Contains essential Windows system files, DLLs, drivers, and utilities. | The heart of Windows—required for the OS to operate.                          |
| **SysWOW64**             | Stores 32-bit system files on 64-bit Windows.                          | Allows 32-bit applications to run on a 64-bit operating system.               |
| **WinSxS**               | Windows Side-by-Side component store.                                  | Stores multiple versions of Windows components for updates and compatibility. |
| **Temp**                 | Temporary files created by Windows.                                    | Stores files needed temporarily during installation or operation.             |
| **Logs**                 | Windows log files.                                                     | Records system events and troubleshooting information.                        |
| **Fonts**                | Installed fonts.                                                       | Provides fonts available to Windows and applications.                         |
| **INF**                  | Driver installation information files.                                 | Contains driver setup files used when installing hardware.                    |
| **Installer**            | Windows Installer cache.                                               | Stores installation packages needed for repairing or updating applications.   |
| **Panther**              | Windows Setup logs.                                                    | Stores installation and upgrade logs.                                         |
| **SoftwareDistribution** | Windows Update files.                                                  | Stores downloaded updates before installation.                                |
| **Tasks**                | Scheduled task files.                                                  | Stores scheduled tasks created by Windows Task Scheduler.                     |
| **Web**                  | Windows wallpapers and themes.                                         | Contains default wallpapers and web resources.                                |
| **Resources**            | UI resources such as themes and icons.                                 | Used by Windows to display its graphical interface.                           |
| **PolicyDefinitions**    | Administrative Templates.                                              | Stores Group Policy templates used by administrators.                         |

---

### Important Subfolders Inside `C:\Users`

|Folder|Description|Purpose|
|---|---|---|
|**Desktop**|User's desktop files.|Stores files and shortcuts shown on the desktop.|
|**Documents**|Personal documents.|Default location for text files and office documents.|
|**Downloads**|Downloaded files.|Default folder for downloaded content.|
|**Pictures**|Image files.|Stores photos and screenshots.|
|**Music**|Audio files.|Stores music and audio recordings.|
|**Videos**|Video files.|Stores movies and video recordings.|
|**AppData** _(Hidden)_|Application settings and cache.|Stores user-specific application data.|

---

### AppData Subfolders

|Folder|Description|Purpose|
|---|---|---|
|**Roaming**|User settings that can roam with a domain account.|Stores application settings and profiles.|
|**Local**|Data specific to one computer.|Stores cache files and large application data.|
|**LocalLow**|Data for low-privilege applications.|Used by sandboxed or protected applications (e.g., browsers).|

---

### Important Subfolders Inside `System32`

|Folder/File|Description|Purpose|
|---|---|---|
|**drivers**|Device drivers.|Allows Windows to communicate with hardware.|
|**config**|Windows Registry hive files.|Stores system configuration databases.|
|**DriverStore**|Driver repository.|Keeps copies of installed device drivers.|
|**wbem**|Windows Management Instrumentation (WMI).|Supports system management and scripting.|
|**spool**|Print spooler files.|Temporarily stores print jobs.|
|**catroot**|Cryptographic catalog files.|Used to verify Windows updates and drivers.|
|**LogFiles**|System log files.|Stores logs for diagnostics and troubleshooting.|
|**winevt**|Windows Event Logs.|Stores Event Viewer logs.|

---

### Common Folder Locations IT Professionals Frequently Use

|Folder|Why it's important|
|---|---|
|`C:\Windows\System32`|Core Windows files and troubleshooting.|
|`C:\Users\<username>\AppData`|Application settings, malware analysis, browser data.|
|`C:\Program Files`|Installed software.|
|`C:\ProgramData`|Shared application configuration.|
|`C:\Windows\Temp`|Temporary files; useful for cleanup and investigations.|
|`C:\Windows\Logs`|Troubleshooting Windows issues.|
|`C:\Windows\System32\drivers`|Device drivers and networking drivers.|
|`C:\Windows\System32\config`|Registry hive files (important in forensics).|
|`C:\Windows\System32\winevt\Logs`|Windows Event Viewer logs, commonly examined in cybersecurity investigations.|
|`C:\Windows\SoftwareDistribution`|Windows Update troubleshooting.|
