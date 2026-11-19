**When you extract the file it have wireshark SSL key**
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224203043.png]]

- This is SSL encryption keys in order to decrypt SSL Traffic.  
- This keys captured during Man-In-a-Middle-Attack

****

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224203646.png]]

```Wireshark filter
tls.handshake.type eq 1
```

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224203957.png]]

Since it is SSL packets it is encrypted, in order to decrypt them we need to use the keys that included on the file.

**To decrypt that go to**
```
Edit -> Preferences -> Protocol -> TLS -> (Pre)-Master-Secret log filename -> Browse the SSL key file
```

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224204437.png]]

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224204508.png]]

Back to the that filter
```Wireshark
tls.handshake.type eq 1
```

Select a specific packet -> Follow -> TLS Stream

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224204752.png]]

Then Filter
```Wireshark
(http.request or tls.handshake.type eq 1) and !(ssdp)
```
This query will get either http request or the handshark, however it exclude the ssdp.

As we can see there is interesting packet here
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224205416.png]]
- So basically it requesting or downloading a dll resource and its called invest_20.dll

To give a background what type of malware that a system on this network dealing it is essentially infected by **dryex malware**

**Dryex malware** (also known as **Bugat v5**) is a type of **banking trojan** that steals financial information from victims, especially online banking credentials.

So when we see the HTTP stream of that packet

We can see whats happening in the HTTP request on the top.
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224210541.png]]
And eventually below that, that is the invest_20.dll or its content.

****

**As a malware analyst or threat hunter we need to download the content of this dll or save this and analyze it using tool like virus total.** 

**What we will do?**

We can export it as a object.

Highlight the packet -> File -> Export Objects -> HTTP -> then look for the invest_20.dll -> Save
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224210951.png]]

Then We can use virus total

Chrome -> Virus Total -> upload the file
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224211543.png]]

- We can see its real name `CrowdDry.dll`
- It marks as a trojan malware

We can see other details in details tab
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224211729.png]]

We can see also the history of the file
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224211947.png]]


It imports other dll file, it is malicous especially it utilize the win32 or the kernel32 dll file
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224211824.png]]

**Information about those dll files:**

**KERNEL32.dll**  
Core Windows system functions (process creation, memory management, file handling).

**USER32.dll**  
Handles user interface actions (keyboard input, mouse input, windows interaction).

**GDI32.dll**  
Manages graphics and screen drawing (can be used for screenshots).

**ole32.dll**  
Supports COM and Object Linking & Embedding (used for component interaction and some persistence methods).

**WS2_32.dll**  
Windows networking library (used for internet connections and C2 communication).

**ADVAPI32.dll**  
Advanced Windows functions (registry editing, services, security, privilege changes).

****

As you can see there is a couple of post request that being send in this particular IP Server
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224213150.png]]
It looks like after the connection or the infection it connects into C2 server operated by the attacker


**When we put** `nbns` in filter
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260224213708.png]]
We can see the desktop host name.

So we have a good idea as a threat analyst what system was infected and we can pass this information to incident response team and the scope of the information.