
## SOC AUTOMATION PROJECT

Wazuh - for SIEM & XDR
Hybe - case management
Shuffle - for sour capabilities
Sysmon - For Logs the events in windows

****
## Virtual Machine
- Ubuntu - for wazuh server, and hive
- Kali - for attacker machine
- Windows10/tiny10 - for client, wazuh agent

**Noted: you can use tiny10 if the device can't run smoothly the windows10**
****
## Diagram
![[SOC Automation Project Diagram.drawio.png]]

**Link:** https://drive.google.com/file/d/1VQBtZG9zzRFXmvEmCbUHxeZa7nyxMtzY/view?usp=drive_link

**Diagram 1 (with Icon)**
1. **Windows 10 Client:** Sent events over to internet, then goes to wazuh manager.
2. **Wazuh Manager:** Receive the events.
3. **Wazuh Manager:** Creates an alerts and then send over shuffle.
4. **Shuffle:** Receive the alerts, and it performs open source intelligent gathering using internet to enrich the IOCS. Once its done enriching the IOCS, it send it back into shuffle.
5. **Shuffle:** Sends alerts into thehive.
6. **Shuffle:** Send an email to SOC Analyst.
7. **SOC Analyst:** Send & receive the email. It contains details about the alerts and should ask the question if He/She want to contain or perform a certain action (Yes or No). 
8. **SOC Analyst:** The action sent goes to internet and goes over to shuffle.
9. **Shuffle:** sent the response over to wazuh manager. 
10. **Wazuh Manager:** Instruct the agent to perform the responsive action.

**Diagram 2 (text)**
1. **Windows 10:** Send events 
2. **Wazuh Manager:** Look those events, trigger alerts and perform responsive actions. Then send alert over to shuffle.
3. **Shuffle:** Receive wazuh alerts and send responsive actions.
4. **OSINT:** Enriching the IOCS
5. **Shuffle:** Send alerts to Thehive
6. **Thehive:** Creates an alerts on their case management system.
7. **Shuffle:** Sent an email and responsive action.

****
## Installing Sysmon

#### Downloading Sysmon and Sysmonconfig File
Sysmon Link: https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon

sysmonconfig.xml link: https://github.com/olafhartong/sysmon-modular
Noted: when download the sysmonconfig, click first the sysmonconfig, then click raw -> save as sysmonconfig

### Installing

- Place the download sysmon on the folder
- Extract it on that folder
- Then place the `sysmonconfig.xml` on the same location
- Open powershell with administrator priviledges
- CD on that directory ex: `cd C:\Users\Pc1\download\sysmonfolder`
- then installed it `.\Sysmon64.exe -i .\sysmonconfig.xml`

**You can check if it installed**
- Go to services and find `sysmon64`
  
**Noted: refresh it, if it doesn't there.**

Or 
- Go to event viewer.
- Open the Applications and Services Logs -> Microsoft -> windows, then find `sysmon`

**Noted: refresh it, if it doesn't there.**

