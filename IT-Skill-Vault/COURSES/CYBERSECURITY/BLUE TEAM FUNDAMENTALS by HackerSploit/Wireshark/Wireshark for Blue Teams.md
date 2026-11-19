## Introduction to Wireshark
- Wireshark is a open-source network protocol and traffic analyzer
- It used to capture network traffic, troubleshoot and etc.

****
## Packets
- Also known as network frame, it is a piece of data sent over network.
- It contains data and also various header that used to specify the type of packet, source, destination IP, protocol, and etc.

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark/Wireshark Img/Pasted image 20260210205832.png]]

****

## Wireshark for Blue Teams
- for Blue team operations wireshark used to analyze previously capture traffic stored in the form of PCAP file for analysis and threat identification.
- Wireshark can identify packet data and header (source, destination IP, type of protocol).
- It is used to identify malicious activity **pinpointing the time of attack, type of attack, IP address that targeted and so on.**

### Wireshark features
- Live traffic / Packet capture
- Packet dissection
- Ability to import / export capture traffic (PCAP) 
- Robust capture and display filters
- Ability to search for packets
- Customize and color code packets based on our requirements.
- and so on..

****
## PCAP (Packet Capture) file
- it is a API and data format used to store capture network traffic, recording raw data packets as they travel across a network from layer 2-7 of the OSI model.
- Wireshark utilize the `.pcap` file format to capture and store packets for later analysis.
- also it allows analysis to import and analyze network traffic that was captured on another network at different time.

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark/Wireshark Img/Pasted image 20260210211535.png]]

****

## Installing Wireshark
- it is a cross platform and is available for both UNIX (Linux OS), Mac OS and Windows.
- **Link:**https://www.wireshark.org/

****

**PCAP files used for demonstration link:** https://github.com/AlexisAhmed/Wireshark-Traffic-Analysis

**Note:** 
- It contains malicious activity.
- It not recommend in analyzing it on windows OS.