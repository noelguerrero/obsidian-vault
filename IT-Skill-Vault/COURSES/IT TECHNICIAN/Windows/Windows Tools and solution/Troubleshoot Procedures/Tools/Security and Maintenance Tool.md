- it is a built-in utility that monitors the health, security, and maintenance status of the computer
- It alerts when the computer needs attention, such as disable antivirus, pending windows updates, etc.
- `Control Panel - System and Security - Security and Maintenance`

****
#### It has 2 sections

**1. Security** -  Checks if computer is protected.
It monitors:
- Windows Security (Microsoft Defender)
- Firewall status
- Virus & threat protection
- User Account Control (UAC)
- SmartScreen
- Windows Update

![[Pasted image 20260919141147.png]]

| Module                         | Description                                                                                                                                                      |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Network Firewall**           | Monitors whether Windows Firewall (or another firewall) is enabled to protect your computer from unauthorized network access.                                    |
| **Virus Protection**           | Checks whether an antivirus program (such as Microsoft Defender Antivirus) is installed, enabled, and up to date.                                                |
| **Internet Security Settings** | Monitors the security configuration of Internet Options (used by Internet Explorer and some Windows components) and verifies they are set to recommended levels. |
| **User Account Control (UAC)** | Checks whether UAC is enabled to help prevent unauthorized system changes by prompting for administrator approval when needed.                                   |

****
**2. Maintenance** - Check if the windows running properly
It Monitors:
- Drive Health
- Device drivers
- Windows Update installation
- Backup status
- Automatic maintenance
- Problem reports
- Troubleshooting history

![[Pasted image 20260919141313.png]]

| Module                                               | Description                                                                                                                                      | Common Troubleshooting Use                                                                 |
| ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Report Problems**                                  | Monitors Windows Error Reporting (WER) and collects information about application crashes, hardware failures, and system errors.                 | Use **Reliability History** to identify when crashes or errors started.                    |
| **Automatic Maintenance**                            | Automatically performs maintenance tasks such as Windows Updates, security scans, diagnostics, and drive optimization when the computer is idle. | Run maintenance manually if scheduled tasks haven't completed or the PC is running slowly. |
| **File History**                                     | Shows whether File History is enabled. File History automatically backs up personal files to another drive or network location.                  | Enable File History to protect user documents from accidental deletion or drive failure.   |
| **Drive Status**                                     | Checks the health of storage drives and reports if Windows detects problems.                                                                     | If the status isn't **OK**, investigate the drive using SMART tools or **CHKDSK**.         |
| **Device Software**                                  | Monitors device drivers and related software to ensure they are functioning correctly.                                                           | Update or reinstall drivers if devices are malfunctioning or have compatibility issues.    |
| **Recovery** _(Located at the bottom of the window)_ | Opens Windows Recovery options such as **Reset this PC**, **System Restore**, **Advanced Startup**, and **Startup Repair**.                      | Use when Windows fails to boot or has serious system problems.                             |