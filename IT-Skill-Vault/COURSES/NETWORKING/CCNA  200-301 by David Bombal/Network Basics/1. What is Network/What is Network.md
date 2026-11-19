
## Computer Network
- it is a set of computers connected and sharing resources/information to each other.
- Computer use common communication protocols over digital interconnections  to communicate to each other

### Host
- a device connected to a computer network.
- a host may work as a server offering information resources, services, and applications to users.

****
## Client-Server Model
it is a way of computers to communicate on a network
- The **client** is the device or program that **requests** something.
- The **server** is the device or program that **provides** the service or resource.

**the real server is look like this:**
![[Pasted image 20260527170423.png]]

**and the client must be your phone, laptop, desktop, or other devices.**

- it connected both client and server through cable or wifi.
****
## Internet Protocol (IP) address
- it is a logical address for a host on a network.

In network today we use either **TCP IPv4** or **TCP IPv6**

In network a specific device is allocated an IP address either manually or **DHCP (Dynamic Host Configuration Protocol)**.

****
## DHCP (Dynamic Host Configutation Protocol)
- It is a protocol that assign an IP address on a specific device that connected on the network.

Generally on the internet we use easy to remember name like google.com, youtube.com and so on, but those name will be translated into IP addresses using a protocol **DNS**.

****
## DNS (Domain Name System)
- It is a protocol that converts a website name into Ip addresses.
- Because device doesn't use name, they used IP addresses and MAC addresses.

****
## Media Access Control (MAC) Addresses
- it is a hardware address that place on the network interface card of a device in a network.
- It is not changable like ip address

****
## Port Number
- is a logical “door” on a computer that helps network traffic go to the correct application or service.

Your computer can run many services at the same time:
- Web browser
- Discord
- SSH
- Wazuh agent
- Games

The **IP address** identifies the computer, while the **port number** identifies the specific service on that computer.

Example: Our web browser use HTTP or HTTPS protocol to connect t a web server (like: google.com). Those web server use port number of 80 for HTTP and 443 for HTTPS

Example to understanding a port:
**Port** - door
**Service/Program** - person inside
**Web browser that requesting a connection** - Person outside

When the person outside knock the door and there is a person inside. the door will open by the person inside. However when there is no person inside, and the person outside knock the door, there is no person who will open the door.

****
## Communication Protocol 
- it is a language or set of rules that devices follow so they can communicate correctly on the network.
- without it the devices would send the data in different formats, or they didn't understand each other.


**Simple analogy**
It is like two people talking on phone call, and they need a rules like:
- what language to use
- when to speak
- how to greet
- how to end the call


**The communication protocol define:**
- how data is sent
- how data is received
- how devices identify each other
- what happens if error occur.

**Examples of Protocl**
- HTTP - which is how we send traffic thorugh the web.
- HTTPS - Secured version of HTTP (HTTP + SSL/TLS)
- SSL (secure socket layer)- it is a security protocol that encrypt the communication between the client and the server.
- TLS (Transport Layer Security) - it is a upgraded version of SSL

****
## NIC (Network Interface Controller)
- It is a hardware component that allows a device to connect to a network through cables or wifi.
- Or also known as **Network Interface Card**. 
- Each NIC have a unique MAC addresses.

![[Pasted image 20260527182302.png]]

A device is known by MAC address so when we send traffic across the internet or wifi, the device has to have MAC address built in by manufacturer to communicate and it also have IP address used to communicate in local network or for to communicate on other network.