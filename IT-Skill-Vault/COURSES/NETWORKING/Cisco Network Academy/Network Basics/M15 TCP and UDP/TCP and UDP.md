## Transport Layer Protocol
A communication protocol that uses to send packet across the network.

**TCP (Transport Control Protocol)**
- Used acknowledgment to track each segment of packets.
- Used sequence number to sort each part of packet.
- Manly used in sending email, bank transfer, and etc.

**UDP (User Datagram Protocol)**
- A fast connection communication protocol that doesn't used acknowledgment and sequence number.
- Mainly used in live streaming, and watching movies.

****
## Port Numbers
It identifies the applications or service in the server that host use. Example;
- Web Server - 80
- FTP Server - 21
- Mail Server - 25

![[Pasted image 20260827211836.png]]

Example on how Web Browser Accessing a Web Server
1. User opens a website in a web browser.
2. Browser chooses a **random temporary port**, e.g. `52341`.
3. Browser sends a request to the web server:
    - **Source port:** `52341`
    - **Destination port:** `443`
    - **Transport protocol:** `TCP`
4. The web server receives the request on **port 443**, which is the **HTTPS service**.
5. The server sends the response back to the browser's **port 52341**.

**Well known ports** (Common Service) 0 - 1023
- 22 → SSH
- 53 → DNS
- 80 → HTTP
- 443 → HTTPS

**Registered Ports** (assigned to specific applications/services) 1024 - 49151
- 1433 → Microsoft SQL Server
- 3306 → MySQL
- 8080 → Alternative HTTP / Web server
- 5432 → PostgreSQL

**Dynamic/Ephemeral/ Private Ports** (Temporary ports that automatically assigned to applications) 49152 - 65535
- 52341 → Browser connection
- 52342 → Another browser connection
- 55001 → Temporary application connection


**Example well known port numbers and associated transport and application protocol**

|Port Number|Transport|Application Protocol|
|--:|---|---|
|20|TCP|FTP – Data|
|21|TCP|FTP – Control|
|22|TCP|Secure Shell (SSH)|
|23|TCP|Telnet|
|25|TCP|Simple Mail Transfer Protocol (SMTP)|
|53|UDP, TCP|Domain Name Service (DNS)|
|67|UDP|Dynamic Host Configuration Protocol (DHCP) – Server|
|68|UDP|DHCP – Client|
|69|UDP|Trivial File Transfer Protocol (TFTP)|
|80|TCP|Hypertext Transfer Protocol (HTTP)|
|110|TCP|Post Office Protocol version 3 (POP3)|
|143|TCP|Internet Message Access Protocol (IMAP)|
|161|UDP|Simple Network Management Protocol (SNMP)|
|443|TCP|Hypertext Transfer Protocol Secure (HTTPS)|
**Search the IANA website for port registry to view the full list of port numbers and associated applications.**

****
## Socket Pairs
- It is a combination of source IP address and source port number, destination IP address and destination port number.
- It is used to identify the server and service that being requested by the client.

Example socket

![[Pasted image 20260828113736.png]]
- The client socket in Web request must be: 192.168.1.5:1099
- The Server socket in Web server must be: 192.168.1.7:80
- And these two combine called **Socket Pairs**: 192.168.1.5:1099, 192.168.1.7:80

****
## The `netstat` Command
- It is a network command that identifies which TCP connection are open and running on a network host.
- Unexplained TCP connection can pose a major threat so we need to monitor it.
![[Pasted image 20260828115403.png]]
By default, the **netstat** command will attempt to resolve IP addresses to domain names and port numbers to well-known applications.  Add this. to display
- `-t` → TCP connections
- `-u` → UDP connections
- `-l` → listening ports
- `-n` → show numeric IP addresses/ports
- `-p` → show the process/program using the port


![[Pasted image 20260828115951.png]]

|Column|Meaning|In your example|
|---|---|---|
|**Proto**|Protocol being used|`TCP`|
|**Local Address**|Your computer's IP address + port|`127.0.0.1:63628`|
|**Foreign Address**|The other endpoint's IP/hostname + port|`database:63629`|
|**State**|Current status of the connection|`ESTABLISHED`|
