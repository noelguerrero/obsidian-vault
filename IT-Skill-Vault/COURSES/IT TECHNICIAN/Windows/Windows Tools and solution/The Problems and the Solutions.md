
## 1. Hardware Problems

|Problem|Possible Cause|Troubleshooting|
|---|---|---|
|Computer won't turn on|Faulty PSU, loose power cable, bad outlet|Check power cable, wall outlet, PSU switch, test another PSU.|
|Computer turns on but no display|Loose monitor cable, bad RAM, GPU issue|Check monitor, reseat RAM, reseat GPU, try another monitor.|
|Random shutdown|Overheating, failing PSU|Monitor temperatures, clean fans, replace PSU if necessary.|
|Computer freezes|Bad RAM, overheating, failing SSD/HDD|Test RAM, check temperatures, check disk health.|
|Loud fan noise|Dust buildup, failing fan|Clean fans, replace damaged fan.|
|CPU overheating|Dry thermal paste, poor airflow|Clean heatsink, replace thermal paste, improve airflow.|
|RAM not detected|Improper installation|Reseat RAM, clean contacts, test one stick at a time.|
|Hard drive not detected|Loose SATA cable, drive failure|Check SATA and power cables, test drive on another PC.|
|SSD not detected|Loose connection, BIOS issue|Reseat SSD, check BIOS settings.|
|GPU not detected|Loose PCIe connection|Reseat GPU, update BIOS, test another GPU.|
|Keyboard not working|Faulty USB port or keyboard|Try another USB port, test another keyboard.|
|Mouse not working|Faulty USB port|Test another mouse or USB port.|
|USB ports not working|Driver or motherboard issue|Test different ports, reinstall USB drivers.|
|Laptop battery not charging|Bad charger or battery|Test charger, inspect battery health.|
|CMOS battery failure|Dead CR2032 battery|Replace CMOS battery.|
|Date and time reset after shutdown|CMOS battery dead|Replace CMOS battery.|
|Fan not spinning|Loose cable or failed fan|Reconnect or replace fan.|
|Burning smell|Electrical short|Turn off immediately, inspect PSU and motherboard.|
|Beeping during startup|RAM or hardware error|Check beep codes, reseat RAM or GPU.|
|Monitor flickering|Bad cable or monitor|Replace cable, test another monitor.|
|Hard drive making clicking noise|HDD failure|Back up data immediately and replace drive.|

****
## 2. Operating System (Windows) Problems

|Problem|Possible Cause|Troubleshooting|
|---|---|---|
|Windows won't boot|Corrupted boot files|Startup Repair, Bootrec commands, System Restore.|
|Boot loop|Failed update|Boot Safe Mode, uninstall updates.|
|Blue Screen (BSOD)|Driver or hardware issue|Note stop code, update drivers, test RAM.|
|Black screen after login|Explorer crash|Restart Windows Explorer from Task Manager.|
|Windows Update fails|Corrupted update cache|Windows Update Troubleshooter, clear cache.|
|Activation error|Invalid license|Run Activation Troubleshooter.|
|Windows running slowly|Startup programs|Disable startup apps, clean temporary files.|
|Login problems|Wrong password, corrupted profile|Reset password, create new user profile.|
|Safe Mode won't load|Severe corruption|Use Windows Recovery Environment.|
|Explorer crashes|Corrupted system files|Run `sfc /scannow`.|

****
## 3. Software Problems
|Problem|Possible Cause|Troubleshooting|
|---|---|---|
|Program won't open|Corrupted installation|Reinstall application.|
|Application crashes|Compatibility issue|Update or reinstall software.|
|Program freezes|Low memory|Close background applications, restart PC.|
|Software won't install|Missing administrator rights|Run installer as Administrator.|
|Missing DLL error|Corrupted files|Reinstall software or install missing runtime.|
|Software update fails|Corrupted installer|Download latest installer.|
|License activation failed|Wrong product key|Verify license information.|
|Program running slowly|Too many background processes|Close unused applications.|
|Browser crashes|Corrupted cache|Clear browser cache and extensions.|
|Microsoft Office won't activate|License issue|Sign in with correct Microsoft account.|

****
## 4. Storage Problems

|Problem|Possible Cause|Troubleshooting|
|---|---|---|
|Disk full|Too many files|Delete unnecessary files, use Disk Cleanup.|
|File cannot be deleted|File is in use|Close application, restart PC.|
|Corrupted files|Disk errors|Run `chkdsk`, restore backup.|
|Disk read error|HDD failure|Check SMART status, replace drive.|
|Slow file transfer|USB or disk issue|Test another cable or storage device.|

****
## 5. Network Problems

|Problem|Possible Cause|Troubleshooting|
|---|---|---|
|No internet|Router or ISP issue|Restart modem/router, check ISP.|
|Connected to Wi-Fi but no internet|DNS or gateway issue|Flush DNS, restart router.|
|Ethernet not working|Faulty cable|Replace cable, reinstall network driver.|
|Slow internet|ISP congestion|Run speed test, restart router.|
|DNS server not responding|DNS configuration|Change DNS to 8.8.8.8 or 1.1.1.1.|
|IP conflict|Duplicate IP address|Renew IP using `ipconfig /renew`.|
|Cannot access website|Browser cache or DNS|Clear cache, flush DNS.|
|Wi-Fi disconnects frequently|Weak signal|Move closer to router or change Wi-Fi channel.|
|Ping timeout|Firewall or network issue|Check gateway, firewall, cables.|
|Printer not found on network|Wrong IP|Verify printer IP and network settings.|

****
## 6. Malware & Security Problems

|Problem|Possible Cause|Troubleshooting|
|---|---|---|
|Computer infected with virus|Malicious download|Run Windows Defender or antivirus scan.|
|Pop-up advertisements|Adware|Scan with antivirus, remove suspicious programs.|
|Ransomware|Malicious attachment|Disconnect network immediately and restore from backups if available.|
|Unauthorized login|Weak password|Change password and enable multi-factor authentication (MFA).|
|Antivirus won't update|Internet or software issue|Check connection and reinstall antivirus if needed.|

****
## 7. Common Windows Troubleshooting Commands

|Command|Purpose|
|---|---|
|`ipconfig`|Display IP configuration|
|`ipconfig /all`|Show detailed network configuration|
|`ipconfig /release`|Release IP address|
|`ipconfig /renew`|Request a new IP address|
|`ipconfig /flushdns`|Clear the DNS cache|
|`ping`|Test connectivity to another device|
|`tracert`|Trace the route packets take to a destination|
|`nslookup`|Query DNS records|
|`arp -a`|Display the ARP table|
|`netstat -ano`|Show active network connections and listening ports|
|`hostname`|Display the computer name|
|`systeminfo`|Show detailed system information|
|`tasklist`|List running processes|
|`taskkill /PID <PID> /F`|Forcefully terminate a process by PID|
|`sfc /scannow`|Scan and repair protected Windows system files|
|`DISM /Online /Cleanup-Image /RestoreHealth`|Repair the Windows image used by SFC|
|`chkdsk /f`|Check and repair file system errors on a disk|
|`shutdown /r /t 0`|Restart the computer immediately|
|`shutdown /s /t 0`|Shut down the computer immediately|