## Technologies used to secure Wi-Fi networks nowadays

### Wi-Fi protected Access (WPA)
- is a security protocol designed to enhance protection of wireless network.
- It addresses the vulnerabilities found in older Wire Equivalent Privacy (WEP), which was the originally security protocol for WI-FI.


## Hyper Text Transfer Protocol (HTTP)
- It is a foundational protocol used for communication on the World Wide Web. HTTP defines how message are formatted and transmitted and how web servers and browser should respond in the various request.
- But HTTP is not secure at all because it didn't encrypt your data that flow through servers. 


## When you using HTTP you are vulnerable in this attack or technologies


### A. Machine-in-the-Middle Attacks (MitM)
- This attack is a type of cybersecurity threat where an attacker secretly intercept and possible alters the communication between two parties without their knowledge.

When we are visiting the website, the website download this file called HTML and this what is look like
```
<!DOCTYPE HTML>
	<body>
		...
	<body>
</HTML>
```

And it is possible the attack inject some script or technology to those file to get your data.
```
<!DOCTYPE HTML>
	<body>
		<script src="ad.js"></script>
		...
	<body>
</HTML>
```

The common scenario of this attack when the coffee shops or the hotel whose WI-FI you using wants to inject advertisements into or maybe each every website you visit, even if the website didn't not design for advertisements.

The reason why that machine in the middle are able to do this, because your data is not encrypted or you are using an old protocol (like HTTP) that is not support encryption.


### B. Packet Sniffing
- is a technique used to capture and analyze data packets travel through network, it is performed using specialize software or hardware(tool) called packet sniffer.
- Packet sniffer can intercept, log, and analyze network traffic, making them useful for both legitimate purpose (like network trouble shooting) and malicious activities (like stealing sensitive data).

The data travels like a delivering virtual envelop that contains your data, So someone possible sniff or open that envelop and when the data is not encrypted inside, it can steal your data.

**Example of what could be inside of that envelop or data packets**

Get /search?q=cats HTTP/3 
Host: example.com  

On the top is a content that you want and protocol you use and the bottom is host or website where you visiting

It is a message that requesting a webpage from a server.

When you go to your search engine and search a content like cats, your device creates an virtual envelop or data packets that contains a message like that, and the server that receive will reply. So that envelop contains the content that you want to search, technology you have and the website you visiting for and when that envelop is not encrypted someone can see the message like that inside.


### C. Cookies (it is not a threat but it is vulnerable from a threat given below)
- are a small text files that websites store on a user's device, when the user visits the site. These files contains data that helps the website remember the user's actions, preferences, or session information.
- But both can be used in legitimate purposes (like enhancing browsing experience, enabling specific functionalities and etc) and malicious activities.

When you visiting a website that you need to log in to, and that needs to remember you, when you click on different pages. for instances, like to access different emails, add different things for shopping cart, and etc. What actually server does or responds to your request is something like this.

HTTP/3 200
Set-Cookie: session=123abcd

On the top HTTPS response says 200 is a status code means Ok and the bottom is  a ability of the server to remember you

The server giving you like a stamp on your hand or something that identify your identity and this helps the website to remember you when you log in or the things you do (like adding something on the cart) instead of typing password again or doing that things again (like remember what items on that cart). just by checking those stamps

When you visiting a website again and again, of course i doesn't have a hand to show. So rather, it sends its own message via HTTP like this inside of its own envelop back to server every time when you click another like, add something to your cart or etc, on the site which you logged in.

Get / HTTP / 3
Cookie: session=1234abcd

The top part is getting some page from the sever. Then the bottom is sending not set cookie, but a cookie that contains a value that is equivalent of presenting your stamp from your hand, then sending a value a exact value before, that the server will identify you. 

This cookie might be store in memory temporarily or it might actually be installed long term on your devices, for a day, week, or months, depending on how the server's been configured.

Cookies can solve a very useful problem of retaining a state, that is remembering who you are, so they are vulnerable potentially to **session hijacking** if you are not using HTTPS which is support encryption.

#### Session Hijacking
- is a cyberattack where an attacker takes over a user's session on a network, typically to impersonate the user and gain unauthorized access to sensitive information or resources. 
- This type of attack exploits the session tokens that are used to authenticate users after they log in to a website or service.



## Hyper Text Transfer Protocol Secure(HTTPS)
- It is a extension of HTTP that has security protocol.
- It offers features like encryption, authentication, and data integrity (ensure that the data transfer has not altered or corrupt). 

### Protocol that handles encrypting on HTTP traffic

### Transfer Layer Secure (TLS)
- It is a cryptographic protocol designed to provide secure communication over the network (like email, voice over IP (VoIP), and etc).
- The recent or improve version of Secure Sockets Layer (SSL) 

### HTTPS has Authentication 

HTTPS uses **digital certification** such as provided by a **Certificate of Authority (CA)** - trusted organization or entity that issues and manage digital certificates, these certificates verify the identity of a website are legitimate or not.

TLS verifies the two parties of the communication (client and server) using **digital certificates** (it include a digital signature that we study earlier)

This ensure that the client connects to the intended server (not malicious on), or optionally the server recognizes the client.

The certificates technically are a type called **X.509** - it is a type of standard format of digital certificates that is used a public key infrastructure.

**This is How it works**

- first when visiting a website and it is presenting you a certificate the browser download the that certificate signed by a CA.
- the browser calculates a hash value using a specific hash function.

	**Certificate --> Hash**

- Then the browser use the public key of the signer on that certificate (The CA) to decrypt the signature (that assuming that a CA who signed that signature) and then it create a hash value that should produce a exact amount of hash value.

	**Public Key -->**
	**Signature -->         --> Hash value**


### Does HTTPS, and in turn TLS, keep you secure?

#### SSL Stripping or refers also TLS Stripping
- is a type of cyberattack where an attacker downgrade a secure HTTPS connection to unencrypted HTTP connection. This allows the attacker to intercept and manipulate the data transmitted between parties.
- It is a Man-In-The-Middle (MITM) attack where a attack exploits the fact that the users are unaware that their connection is downgraded into HTTP.

**How it works?**

- **Intercepting the Connection**:
    - The attacker positions themselves between the victim and the web server (e.g., by compromising a public Wi-Fi network).

- **Downgrading to HTTP**:
    - When the victim tries to connect to a secure website (via HTTPS), the attacker intercepts the request.
    - The attacker forwards the request to the web server but removes the **HTTPS** requirement, forcing the connection to fall back to **HTTP**.
    
- **Proxying the Traffic**:
    - The attacker establishes a secure HTTPS connection with the web server on behalf of the victim (it will mirror the victims action while interacting the server).
    - However, the connection between the attacker and the victim remains HTTP (unencrypted), allowing the attacker to view and modify the data.

- **Stealing Information**:
    - Sensitive information such as login credentials, credit card numbers, or personal data can be captured by the attacker in plaintext.

### How could avoid this kind of attack?

You can use the protocol called **HSTS** into your server.
#### HTTP Strict Transport Security (HSTS)
- is a web security protocol mechanism that ensure the web browser will interact only with a website with a secure HTTPS connection, and never allowing insecure HTTP communication.

If you are the server, just configure the server to send an additional HTTP header like this per virtual envelop (or data packets) that browser sends and receive. So when you accidentally type a HTTP, it will automatically switch into HTTPS.

```
Strict-Security: max-age=3153600
```

Note: 3153600 is a seconds of a 1 year, this means the strict security will be at least a year.

But you cannot only strict when it comes from the browser, but also you can say use strict security for subdomains as well.

```
Strict-Security: max-age=3153600; includeSubDomains
```

And if you are administrator of the server you can do one step further include the keyword preload. So to tell the world that would like to preload this information into Chrome, into other browsers that users download, so you will avoid the first window opportunity of the attack, Because you can have your domain name included, essentially, in the source for browsers like chrome.

So when other users download chrome itself, and visit your website. Your browser will already know that should use HTTPS not HTTP.

```
Strict-Security: max-age=3153600; includeSubDomains; preload
```


### How else can you keep your system secure?

#### Virtual Private Network (VPN)
- is a technology that creates a secure and encrypted connection between the user device and the remote server.
- It acts as a private network, protecting your data and masking (hiding) your online activity.
- It acts as a middle man between user device and the server (websites or services)

##### How a VPN Works

1. **Encryption**: A VPN encrypts the data traveling between your device and the VPN server, making it unreadable to hackers, ISPs, or anyone else attempting to intercept it.

2. **IP Masking**: It hides your IP address by routing your traffic through the VPN server. This makes it appear as if you're browsing from the VPN server's location instead of your actual one.

3. **Tunneling**: Your internet connection is "tunneled" through a secure, virtual pathway to the VPN server, ensuring your data is safe.
##### How the VPN Acts as a Middleman

1. **User Device to VPN Server**:
    
    - Your device establishes an **encrypted tunnel** to the VPN server.
    - Any data sent from your device (like a request to visit a website) is first encrypted and then sent to the VPN server.
2. **VPN Server to Final Destination**:
    
    - The VPN server decrypts your request and forwards it to the destination server (e.g., a website or online service).
    - To the destination, it looks like the request originated from the **VPN server’s IP address**, not your actual device or location.
3. **Response from Destination to VPN Server**:
    
    - The destination server sends the response (like a webpage or data) back to the VPN server.
4. **VPN Server to User Device**:
    
    - The VPN server encrypts the response and sends it back through the secure tunnel to your device.
    - Your device decrypts the response, making it readable to you.


Note: It protects only the identity of user device, but if the destination server did't not follow the proper and secure practice. the traffic will be intercept. 


### Beyond that there are other technology that encrypt communication.

#### Secure Shell (SSH)
- Is a cryptographic network protocol used to securely access and manage devices, servers, and systems over an unsecured network.
- It provides a secure way to perform remote logins, file transfers, and administrative tasks by encrypting the communication between the client and server.
- It encrypts only the SSH session-related traffic.

##### How SSH Works

1. **Client-Server Model**:
    
    - The **SSH client** (on your local machine) initiates a connection to an **SSH server** (on the remote machine).
    - Default port: **22**.
2. **Secure Handshake**:
    
    - The client and server establish a secure session using encryption protocols (e.g., RSA, DSA, or Ed25519).
    - They authenticate each other and agree on encryption keys for the session.
3. **Encrypted Communication**:
    
    - Once the session is established, all communication between the client and server is encrypted, including login credentials and transmitted data.



### Difference between VPN and SSH

| Feature              | SSH                                    | VPN                                             |
| -------------------- | -------------------------------------- | ----------------------------------------------- |
| Encrypts all traffic | No (only SSH session-related traffic)  | Yes (all traffic from your device)              |
| Primary use case     | Remote system access and file transfer | Online privacy, security, and anonymity         |
| Applies Globally     | No (per session/connection basis)      | Yes (applies to all apps and services)          |
| IP Masking           | No (doesn't change your browsing IP)   | Yes (replaces your IP with the VPN server's IP) |

### The outside of the Virtual Envelop that's helping to these envelops get their source to their destination.  

#### Port
- in networking port is a logical endpoint that serves as a communication gateway for data traveling across a network.
- It is like a door virtual door or channel that helps direct incoming and outgoing data to the correct application or service on a computer or server.

###### Analogy: Port as a Mailbox Slot
Imagine a server is like a house, and each room represents a specific application (e.g., a web server, email service, etc.). The house has a single address (its IP address), but there are multiple mailboxes (ports) at the door to ensure letters (data packets) are delivered to the right room.

###### How Ports Work with Data Packets

1. **IP Address**:
    - Acts like the destination address for the packet (the "house").
    - Ensures the packet reaches the correct device on the network.
    
1. **Port Number**:
    - Acts as a "door" or "mailbox" inside the device.
    - Every application or service in device have a different mailbox or doors (ports) on their own. So it directs the virtual envelop (packet) to the specific application or service through doors or mailbox that running on the device.
    
    For example:
    - Port **80**: Used for HTTP (web browsing).
    - Port **443**: Used for HTTPS (secure web browsing).
    - Port **22**: Used for SSH (secure shell access).

Maybe the attacker is sniffing the ports of every data packets, to track what is the destination and purpose of that data packets. But their have many ports that starts from 0 to 65,000 so they might difficult to identify what is that port. But their ha a attack called **port scanning**.

##### Port Scanning
- is a process of systematically checking the open ports on a network device (usually a server or computer) to identify which services or application are running and which port are accessible.
- It is commonly used by network administrator to assess security or by the attackers to identify potential vulnerabilities.

###### How Port Scanning Works

When you perform a port scan, you send network packets to specific ports on a target device and analyze the responses. The goal is to identify:

1. **Open Ports**: Ports that are actively accepting connections, which usually indicates a running service (e.g., web server on port 80, SSH on port 22).
2. **Closed Ports**: Ports that are not accepting connections (these could be blocked by firewalls or not in use).
3. **Filtered Ports**: Ports that may be protected by firewalls or other security mechanisms, preventing any response.

In the world of port scanning, is specific example of what we might call **penetration testing** more generally **pen testing**.


##### Penetration Testing
- often referred to as pen testing is a skills or technique to attack a computer system, network, web application designed to identify and exploit vulnerabilities.
- It allows company or organizations to fix the weaknesses of their system before the hackers can take those as advantage.
- Penetration testing is commonly done after performing port scanning, which helps to identify open ports and running services that could potentially be exploited.

**Key Objectives of Penetration Testing:**
- **Identify vulnerabilities**: Discover weak points or gaps in a system, network, or application that could be exploited by attackers.
- **Test defenses**: Evaluate how well an organization’s defenses (firewalls, intrusion detection systems, etc.) can resist an attack.
- **Demonstrate risk**: Show the potential impact of an attack by exploiting the identified vulnerabilities.
- **Provide mitigation advice**: Recommend ways to fix or mitigate security issues to strengthen the system.


##### Ethical Hacking
- is the authorize practice of identifying and exploiting vulnerabilities in computer system, network, or software applications.
- The "White-hat hackers" or "Penetration Testers" are work to find and fix security weaknesses before the malicious hackers, known as "Black-hat hackers" can exploit them.

## Technology that can help to keep the attacks out

### Firewall
- is a security system designed to monitor, filter, and control incoming and outgoing network traffic based on the predetermined security rules.
- Its primary purpose is to act as a barrier between the internal network and untrusted external network, such as the internet, to prevent unauthorized access and protect sensitive data.

##### How Firewalls Work

- 1. **Packet Filtering**:
    - Firewalls inspect packets of data using filters.
    - Each packet has a header containing information such as source and destination IP addresses, port numbers, and protocols.
    - If a packet meets the firewall’s rules (e.g., allowing traffic from a trusted IP), it is permitted; otherwise, it is blocked.
    
2. **Stateful Inspection**:
    - Maintains a table of active connections and checks if incoming packets belong to a known and valid connection.
    - Prevents unsolicited packets from entering the network unless they’re part of an established connection.

3. **Deep Packet Inspection (DPI)**:
    - Examines the content of data packets to identify malicious payloads, like viruses or malware.
    - This method is more resource-intensive but provides better security.

4. **Proxy Services**:
    - A proxy firewall acts as an intermediary between users and external networks.
    - Instead of directly connecting to the destination, users connect to the proxy server, which forwards requests and filters responses. 
    

Every data packet that firewall monitor, it contain the IP address of a certain server or a website. So if you want to block a certain website, you can configure your firewall to prevent access to the IP addresses of that website. 

You monitor network traffic not only **based on IP address, but port number also.** You can use your firewall to block all of those port number, but if you realize that you want to remote a desktop, you can open just one port number, for instance 22. if you want to allow SSH back and forth. Or whatever port number you preferred VPN software uses instead.

So you can use firewall to block traffic based on IP address, port numbers or even sophisticatedly via **deep packet inspection**.

#### Deep Packet Inspection (DPI)
- is a advance method of examining the contents of data packets that travel across the network.
- Unlike basic packet filtering that only inspects the headers of packets (e.g., source and destination IP, port numbers), DPI search into payload of the packets to analyze their contents.

##### How Deep Packet Inspection Works

1. **Packet Analysis**:
    
    - Each data packet consists of two main components: the **header** (containing metadata) and the **payload** (the actual data being transmitted).
    - DPI examines both the header and the payload to identify the type of data, its purpose, and any anomalies.

2. **Pattern Matching**:
    
    - DPI compares the contents of packets against predefined patterns or rules to detect malicious code, viruses, or unusual behavior.
    - For example, it may identify known signatures of malware or suspicious activities like SQL injection attempts.

3. **Protocol Validation**:
    
    - Validates whether data conforms to expected communication protocols (e.g., HTTP, FTP, or DNS).
    - This helps detect and block protocol misuse or exploitation attempts.

4. **Decision Making**:
    
    - Based on its analysis, DPI can allow, block, redirect, or log the traffic for further investigation.


## How might a company university, or even a home implement this kind of firewalling, or more deeply, this deep packet inspection?


### Proxy
- is an intermediary server that acts as a gateway between user's device and the internet. 
- It facilitates request from clients (such as web browser) to server and can provide benefits like anonymity, security, and performance enhancement.

##### How a Proxy Works

1. **User Request**:
    - A user sends a request to access a resource, such as a webpage or file, on the internet.
2. **Interception by Proxy**:
    - The request is routed through the proxy server, which evaluates it according to configured rules.
3. **Forwarding**:
    - The proxy server forwards the request to the target server on behalf of the user.
4. **Response**:
    - The target server sends back the data, such as the webpage, to the proxy.
5. **Delivery to User**:
    - The proxy server relays the response to the user.


## How the company or organization be observing or keeping an eye out either for good or evil purpose?

They might actually doing something like **URL rewriting**.

### URL Rewriting
- is the process of modifying a URL's structure, either for aesthetic, functional, or technical reasons.
- This technique is commonly used in web development and server management to improve usability, security, and SEO (Search Engine Optimization). URL rewriting can be done dynamically by a Web server or statically by developers. 

##### Why Use URL Rewriting?

1. **Improve Readability and Usability**:
    
    - Rewrites long, complex URLs into clean and user-friendly ones.  
        Example:
        - Original: `https://example.com/products?category=electronics&id=12345`
        - Rewritten: `https://example.com/products/electronics/12345`

2. **Enhance SEO**:
    
    - Search engines favor descriptive and structured URLs that include keywords.  
        Example:
        - Original: `https://example.com/page.php?id=42`
        - Rewritten: `https://example.com/about-us`

3. **Mask Internal Structure**:
    
    - Hides implementation details such as file extensions or query parameters.  
        Example:
        - Original: `https://example.com/index.php?page=home`
        - Rewritten: `https://example.com/home`

4. **Simplify Dynamic Links**:
    
    - Converts dynamically generated URLs into static-looking ones that are easier for users and search engines to process.

5. **Redirect Traffic**:
    
    - Redirects users from old URLs to new ones without breaking links or affecting user experience.


When the company or university monitor you using proxy server, they prevent you from accessing malicious or phishing website and they apply rewriting technique on your URL to improve your security.


## What is it were trying to keep out of our system?

### Malware
- is a malicious software that designed to harm our computer devices or websites.
- malware is the biggest threat in our computer or systems, because it can do many harmful activities.

## Types of malware

### Virus
- is a type of malware that designed to replicate itself in one computer to another and harm our computer devices or websites.
- it needs a user intervention to operate.

### Worm
- is a type of malware that designed also to replicate itself in one computer to another and harm our computer devices or websites.
- Unlike virus that need user intervention, worm is automatically operate without the need of user intervention.

### Botnet
- (short for "robot network") is a collection of internet connected devices (like computers, smartphones, IoT devices and etc) that has infected by a malicious software and controlled remotely by a group or single person, referred as botmaster without the user knowledge.
- The devices within the botnet referred to as bots or zombie.

By using a group of infected devices you can use it to attack a specific server or website via sending email or you can command it to mining all device a bitcoin and etc.

The infected computers has a much power to attack a specific server or website, this attack is form **Denial-of-Service Attack (DoS)**.

#### Denial-of-Service Attack (Dos)
- is a type of cyber attack aimed at making a system, network, and services unavailable to its intended users. 
- This is achieved by overwhelming the target with an excessive amount of traffic or exploiting vulnerabilities to disrupt its normal functioning using a single device or network.

#### Distributed Denial of Service Attack (DDos)
- like Dos it is a type of cyber attack where making the system or network unavailable by overwhelming it with an excessive amount of traffic. 
- Unlike DoS that use a single device or network, DDoS uses multiple sources (botnet of compromised devices).


#### DoS vs DDoS

| Feature            | Dos                  | DDos                      |
| ------------------ | -------------------- | ------------------------- |
| Attack source      | Single System        | Multiple Systems (botnet) |
| Scale              | Limited              | Massive                   |
| Impact             | Localized disruption | Global disruption         |
| Ease of Mitigation | Easier               | Harder                    |
| Complexity         | Simple               | Complex                   |

## So how do we keep it out?

### Antivirus
- is a software designed to detect, prevent, and remove malicious software from computers, networks, and other devices.
- Its acts as protective layer to safeguard systems from the malwares that can compromise data, privacy, and system performance.

But there's a problem with antivirus software, that it has to actually be current or updated for the attacks that device facing, to know the specific virus updates. So you can on the **Automatic Updates** to be your antivirus is updated in the latest types of malwares.

But the catch is that there are also these attacks known **Zero-Day Attacks**.

#### Zero-Day Attacks
- is a cyberattack that exploits a previously unknown vulnerability in software, hardware or firmware.
- The term Zero-day indicates that developers have had zero days to fix vulnerability because it was discovered and exploited before it was publicly known or patched.