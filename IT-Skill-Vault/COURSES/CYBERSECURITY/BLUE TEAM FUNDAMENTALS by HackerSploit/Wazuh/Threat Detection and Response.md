## Deploying Agent

### Option 1: (Recommended)
1. Download the wazuh agent based on your OS
![[Pasted image 20260606130316.png]]

2. Installed and configure.
![[Pasted image 20260606130343.png]]
- Input the Ip address of the server 
- You don't need to enter the authentication key
- then start it: `manage tab->start`

You can explore those tab
- On manage tab you can see the Start, stop, and status
- On the view tab you can see the logs and config file that use to configure the wazuh agent.

### Option 2:
You can deploy wazuh agent on the wazuh dashboard.

- Go to `wazuh->agents`
- Then follow the instructions.
****
## To View Agents

`Wazuh Tab -> Agent Management -> Summary`

**Note:** for the best practices, you need also deploy an agent in wazuh server device

****
## To View Agent Events

- `Wazuh Tab -> Discovery`
- Add filter, then set:
	- field: `agent.name` 
	- Operator: `is`
	- `deviceName`

![[Pasted image 20260612133016.png]]

****
## Vulnerability Detection
Detect the possible vulnerabilities of the agent devices

![[Pasted image 20260608201216.png]]

And also you can find the meaning of those CVE by clicking it.
![[Pasted image 20260615143658.png]]
****
## Threat Hunting (Or Security Events)
- It shows all alerts and security events
![[Pasted image 20260608203256.png]]

****
## File Integrity Monitoring
- It basically check if a certain file is changed

****
## Response on the Bruteforce Attack

**Assuming that we detect an bruteforce attack in our server or agent**

- Go to Server Management -> Configuration -> Settings -> Edit Configuration.
- We add active response rule. Because wazuh has incident response or IPS
- Add this on active response section.
```ossec.conf
<active-response>
<command>firewall-drop</command>
<location>localhost</location>
<rule_id></rule_id>
<timeout>1000</timeout>
</actice-response>
```
note: you put the rule-id of the bruteforce attacker that you find in the wazuh threat detection to `<rule-id>HERE</rule-id>`

Then when the attacker try to attack again the request of SSH will just drop. 
![[Pasted image 20260612134226.png]]
****
## Security Configuration Assessment or Configuration Assessment
It is a feature of wazuh wherein it audit the security of your agent like:

- If the windows firewall is enable
- Are the user account password is weak
- Is there unnecessary service is running
- and so on.

Basically it compares the system against the best security practices such as CIS (Center for Internet Security) Benchmarks. And gives you a recommends to improve the security of your system (your agent)

**Go to:**
Agent -> Configuration Assessment.

![[Pasted image 20260615142500.png]]

****
## MITRE ATT&CK
This tab organize the tactics and techniques that attacker used during cyberattack that our wazuh system detect, this dashboard showing as what kinds of attacker behavior are we seeing the most. 

We can know how it works, the one who used, and other information about that kind of attack.

![[Pasted image 20260615145852.png]]