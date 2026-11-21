Network Mapper or Nmap, is an open-source utility used for network discovery and security auditing.

It scan local machine to derermine the potential vulnerabilities including open and unmanaged ports.

All workstations require open ports and services to communicate and perform task like printing, sharing a file, or browsing the we. Administrators also use Nmap for monitoring hosts or managing service upgrade schedules.

**Nmap Determines:**
- what hosts are available on the network
- what services are running
- what OS are running
- what packer filters or firewall are running.

****
**Ports guide:**
All communication using ports, and they are using to types of communication protocol TCP and UDP.

- Well-known Ports (0-1023)
- Registered Ports (1024-49,151)
- Dynamic /Private Ports (49,152 - 65,535)

****
**Common Ports**

| **Port** | **Associated Services**                    |
| -------- | ------------------------------------------ |
| 20/21    | File Transfer Protocol (FTP)               |
| 22       | Secure Shell (SSH)                         |
| 23       | Telnet remote login service                |
| 25       | Simple Mail Transfer Protocol (SMTP)       |
| 53       | Domain Name System (DNS)                   |
| 67/68    | Dynamic Host Configuration Protocol (DHCP) |
| 69       | Trivial File Transfer Protocol (TFTP)      |
| 80       | Hypertext Transfer Protocol (HTTP)         |
| 110      | Post Office Protocol version 3 (POP3)      |
| 123      | Network Time Protocol (NTP)                |
| 143      | Internet Message Access Protocol (IMAP)    |
| 161/162  | Simple Network Management Protocol (SNMP)  |
| 443      | HTTP Secure (HTTPS)                        |
****
**Common logical ports that are most common targets by attackers**

|**Port**|**Common Logical Port / Service**|
|---|---|
|20/21|FTP|
|22|SSH|
|23|Telnet|
|25|SMTP|
|50/51|IPsec|
|53|DNS|
|67/68|BOOTP|
|69|TFTP|
|80|HTTP|
|110|POP3|
|111|Port Map|
|119|NNTP|
|123|NTP|
|137–139|NetBIOS|
|143|IMAP|
|161|SNMP|
|389|LDAP|
|443|SSL|

****
**Nmap Syntaxs**

**1.** `nmap localhost` 
It is use to see which ports are open, closed, or filtered in your machine


Example Output:
```
Starting Nmap 7.95
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0000060s latency).

PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   closed http
631/tcp  open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.10 seconds
```
- Then the attacker can do possible exploitation base on the open ports


**2.** `sudo nmap -sU localhost`
It scan the UDP ports on your computer when they are open, closed, and filtered


**Possible outputs**
```
Starting Nmap 7.95

Nmap scan report for localhost (127.0.0.1)
Host is up.

PORT    STATE         SERVICE
53/udp  open          domain
67/udp  closed        dhcps
123/udp open          ntp
631/udp open|filtered ipp

Nmap done: 1 IP address (1 host up) scanned
```
- Then the attacker can do possible exploitation base on the open ports


**3.** `nmap -sV localhost`
This option is to identify the services and its version running on each port.

**Possible outputs:**
```
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 9.6p1 Ubuntu
80/tcp  open  http    Apache httpd 2.4.58
631/tcp open  ipp     CUPS 2.4
```


**4.** `nmap -A localhost`
This option perform more detailed scan it identify open and close ports, version, displayed SSH host keys, and other information

**Possible outputs**
```
[analyst@secOps ~]$ nmap -A localhost
Starting Nmap 7.80 ( https://nmap.org ) at 2026-11-21 11:39 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00016s latency).
Not shown: 997 closed ports

PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 2.0.8 or later
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_ftp-syst:
| ftp-syst:
|   STAT:
| FTP server status:
|     Connected to 127.0.0.1
|     Logged in as ftp
|     TYPE: ASCII
|     No session bandwidth limit
|     Session timeout in seconds is 300
|     Control connection is plain text
|     Data connections will be plain text
|     At session startup, client count was 1
|     vsFTPd 3.0.5 - secure, fast, stable
|_End of status

22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.1 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   256 fe:b7:82:5e:38:db:f3:54:a3:cd:75:b2:ff:b5:ce:29 (ECDSA)
|_  256 12:e2:5b:5c:ef:f1:35:eb:9e:8f:a2:2f:39:de:94:18 (ED25519)

23/tcp open  telnet  Linux telnetd

Service Info: Host: Welcome; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 19.29 seconds
```


**4.** `man nmap`
It shows the manual and other commands for nmap