**Wire shark filter guide**
note: by using this filter you can limit the packets that capture of you device base on the filter that you put.

- **IP address -** src 10.10.10.1
- **Port -** port 10
- **Protocol -** Just type the protocol (ex tcp)

Also you can use logical operators like **'and'** and **'or'** 

Example: src 10.10.1.10 and port 80

****

## Display Filters
Same as filter you can use logical operators here but instead use the simbol
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260220082319.png]]


**Example:** `ip.src == 10.0.2.15 && ip.dst == 185.125.190.18 && tcp.port == 80`

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260220085913.png]]

****

## Netdiscover
- is a utility that allows you to discover other ip address or host on a local network by sending arp  and base on response we can identify if that device is online

### arp (address resolution protocol)
it used to resolve ip addresses to mac addresses

**To install it into ubuntu**

```terminal
sudo apt-get install netdiscover -y
```

**To use it**
```terminal
sudo netdiscover -i enp0s3 -r 10.0.2.1/24
```

**enp0s3 -** is the interface you can find it just type in the terminal `ifconfig`

When you enter that and capture the packets this is what it looks like
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260220091635.png]]

on this part
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260220091649.png]]
**It means:** “What is the MAC address of 10.0.2.2? Please respond to me (10.0.2.67).”

****

## How to Identify malicious Activity or Document came to Website or Attachment

**Assuming that the IP address of the website or atachment is** `10.10.10.31`

We can put in the display filter

```wireshark
ip.addr == 10.10.10.31 && http.request
```

To filter and find the packets that related on that particular website or attachment.

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223110921.png]]

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223111022.png]]

Also you can filter specific request method

```wireshark
ip.addr == 10.10.10.31 && http.request == "POST"
```

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223111239.png]]

Add ons:

**Filter for host address:**
```
https.host == ADDRESS HERE
```

**For Data Link Layer**
```
eth.addr == MAC ADDRESS HERE
```

****

## Protocol Filtering

### DNS Traffic

- Example we filter google.com
- Then filter dns only in wireshark

Basically our machine asking -> what is the IP address of Google.com

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223113044.png]]

**Type A** - it means we are requesting ipv4 format of google ip address

**Also the machine is requesting for IPv6 ip address**
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223114213.png]]
**Type AAA** - it means we are requesting ipv6 format of google ip address


Here's the response and the ip address of google that we requesting
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223114048.png]]

Also there is response for ipv6 format.

**We can use**
```wireshark
dns.a
```

To show only the packets that containing request of IPv4 address and response

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223114452.png]]

****
### FTP Traffic

There is a vulnerable linux service that is running on a particular subnet or nat network that has the ip address, that are running ftp server, telnet and also has SSH running.

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223120725.png]]

#### The goal is Accessing the file directory of the target device.

On the terminal syntax: `ftp TargetAddress 21`
```terminal
ftp 10.0.2.15
```
And  login guessing the email and password

When we are lucky we can input this to access the file directory of that device.
```
dir
```

Basically it works when other device send a ftp request on the specific device. There are no packet personally show in my wireshark.

But for the sake of notes this what it looks like.
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223123340.png]]

Since the ftp here is not encrypted, we can clearly see what activity is happening.

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223124040.png]]

This is important because you can identify bruteforce attack and other unauthorized access.

**When we right click a particular screen and follow up into TCP Stream**
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223142044.png]]

We can see all thing together.
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223142100.png]]

We can see how protocol communicates in the perspective of application layer.

****
### Telnet Traffic

**Same scenario example there is a unauthorize user that access your telnet**

```terminal
telnet TargetAddress
```

Then guess the email and password.

**This will the in the wiresshark of target host:**
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223144152.png]]

****
## Saving Pcap File


![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223145731.png]]
Also you can open Pcap file using wireshark

****
## SSH Traffic

**Switch to lo**

**lo** - means loop back, it records all the packets that you send into your self.

**Create an ssh packets**
- If there is no ssh, install it first

```terminal
ssh Username@YourAddress
```

![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223205909.png]]

****
## Coloring Rule
- We can set a color base on the specific packets
- view tab -> coloring rule
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223210625.png]]

Example:
**Name** - HTTP POST
**Filter** - `http.request.method == "POST"`
**Color** - Bright Pink -> to easily identify


****
## HTTP Traffic

When i login in this website whether the credentials is correct or not that will captured by the wireshark.
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223214115.png]]

This will also show
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223214056.png]]
Also notice the coloring rule that we add

And when we dig deep
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223214352.png]]
![[CYBERSECURITY/BLUE TEAM FUNDAMENTALS by HackerSploit/Wireshark For Blue Teams/Wireshark Img/Pasted image 20260223214745.png]]

Because the connection is not encrypted we can see the credentials