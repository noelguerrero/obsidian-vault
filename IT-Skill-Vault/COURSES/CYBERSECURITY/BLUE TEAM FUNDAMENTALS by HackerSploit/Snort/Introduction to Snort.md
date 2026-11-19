## Snort
- is a popular free and open-source IDS/IPS system that is used to perform traffic/protocol analysis, content matching and can be used to detect and prevent various attacks based on predefined rules.
  
  - it has been active development and has thousands of users and contributors that develop rules to keep snort up to date with the latest attacks.

- Snort has 3 main operation modes
	- **Packet Sniffing** - Collects and displays network traffic like Wireshark does.
	- **Packet Logging** - Collects and logs network traffic into a file.
	- **Network Intrusion Detection** - Analyzes packets and matches traffic against signatures (Attack patterns).

- Snort rules are very similar to a typical firewall rule, whereby, they are used to match network activity against specific patterns or signatures and consequently make a decision as to whether to send an alert or drop the traffic (in the case of IPS).

****
## Snort Versions
- Short was initially developed in 1998 and has been continuously improved since then.

- There are currently 2 versions of snort available:
	- Snort 2.X - De facto version of snort.
	- Snort 3.0 - Latest version of Snort that features improved efficiency, performance, scalability and usability over Snort 2.
	  
- In the tutorial, we will using Snort 2.x as it is the most widely implemented version and has extensive support, documentation & rule-sets.

**Note:** Rules written for Snort 2 will need to be re-written or converted to the new Snort 3 format.

****
## Snort Rules
- Snort has 3 types of rules / rule-sets:
	- **Community rules** - Free rule-sets created by the Snort Community
	- **Registered rules** - Free rule-sets created by Talos. In order to use them, you must register for an account.
	- **Subscription only rules** - These rule-sets require an active paid subscription in order to be accessed and used.
	  
- Or, we can write our own rules based on your requirements.

****
## Snort Rule Syntax
![[Pasted image 20260227180638.png]]This rule says:

If 192.168.1.10 sends ANY ICMP traffic (like ping) to any system, generate an alert called "ICMP Attempt Attack".

****
## How Snort Works
![[Pasted image 20260227181624.png]]

****
## Snort IDS network placement
![[Pasted image 20260227181819.png]]

**In this diagram snort is used in 2 cases:**
- The top one use Snort as **Intrusion Prevention System**.
- The bottom one use Snort as **Intrusion Detection System**.

****
## Lab Environment
![[Pasted image 20260227182357.png]]