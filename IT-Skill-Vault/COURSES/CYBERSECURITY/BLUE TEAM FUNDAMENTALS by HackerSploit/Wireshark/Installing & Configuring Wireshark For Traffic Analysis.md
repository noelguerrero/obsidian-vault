
## Packet List Pane
This show each packet that captured.

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark/Wireshark Img/Pasted image 20260213213355.png]]



## Packet Details Pane
When you highlighted a packet, this shows and display each OSI layer of that packet.

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark/Wireshark Img/Pasted image 20260213212158.png]]

On the highlighted

- **Data Link Layer** (in the OSI) - the first line
- **Network Layer** - 3rd line
- **Transport Layer** - last layer


## Packet Bytes Pane
This is the actual binary packet data.

Most SOC analysts don’t manually read this unless doing deep forensic analysis.

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark/Wireshark Img/Pasted image 20260213214248.png]]

****

## Filtering the traffic that capture
By inputting specific ip, protocol, dest port, and etc.. you can filter packets that wireshark capture

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark/Wireshark Img/Pasted image 20260215100242.png]]

Also you can used the logical operators in programming too when filtering capture packets.

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark/Wireshark Img/Pasted image 20260215103006.png]]