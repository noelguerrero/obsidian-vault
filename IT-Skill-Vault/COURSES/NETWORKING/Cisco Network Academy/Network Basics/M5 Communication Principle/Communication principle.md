There is a rules and principle that governs communication between devices across the internet, it is called protocols

****
## Network Communication Models

#### Network Protocols
Common Network Protocols:
- Ethernet - allows devices communicate each other in LAN.
- IP - allows addressing and delivering data packets on the device whether they're on the same network or across the internet.
- TCP - make sure that data arrives 
- HTTP - used to transfer web pages and other data between web browser and web server.

#### Two basic Type of Model
**Reference model**
- a framework that explains how network communication should be organized.
- It describes each function of the layer, but didn't specify exact protocol
- Ex. OSI Reference Model

**Protocol Model**
- It describes the actual protocols that devices use to communicate over a network.

#### Protocols Stack
- it is a collection of network protocols that work together. 
- ex. TCP/IP model

#### TCP/IP model (Transmission Control Protocol/Internet Protocol model)
- it is a framework that describes how data transmitted across the networks, including the internet.
- Multiple protocols work together to do a single task.

![[Pasted image 20260713202014.png]]


Example protocols in each layer:

| TCP/IP Layer              | Main Protocols              | Purpose                            |
| ------------------------- | --------------------------- | ---------------------------------- |
| **Application**           | HTTP, HTTPS, FTP, DNS, SMTP | Provides services for applications |
| **Transport**             | TCP, UDP                    | Delivers data between applications |
| **Internet**              | IP, ICMP                    | Routes packets between networks    |
| **Network Access (Link)** | Ethernet, Wi-Fi             | Sends data over the local network  |


#### The OSI References Model
- Referred to as OSI model
- Created by Open System Interconnection (OSI)
- It is used for data network design, operation specifications, and troubleshooting.

| OSI Layer              | Description                                                                                                            |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| 7 - Application Layer  | Provides network services that allow applications like web browsers and email clients to communicate over the network. |
| 6 - Presentation Layer | Translates, encrypts, and compresses data so both devices can understand it.                                           |
| 5 - Session            | Creates, manage, and ends communication sessions between applications.                                                 |
| 4 - Transport Layer    | Transfers the data and ensures that it delivered correctly at the right application                                    |
| 3 - Network Layer      | Delivers data between different networks                                                                               |
| 2 - Data Link Layer    | Delivers data between devices on the same LAN                                                                          |
| 1 - Physical Layer     | Responsible for transmitting raw data over the physical medium.                                                        |

Devices Associated with each layer:

| Layer          | Devices                                       |
| -------------- | --------------------------------------------- |
| 7 Application  | Web server, browser, email client             |
| 6 Presentation | Encryption/compression software               |
| 5 Session      | Application session management                |
| 4 Transport    | Firewalls, load balancers (can inspect ports) |
| 3 Network      | Routers                                       |
| 2 Data Link    | Switches, NICs                                |
| 1 Physical     | Cables, hubs, repeaters                       |

#### OSI Model and TCP/IP Model Comparison
![[Pasted image 20260713210556.png]]

![[Pasted image 20260713210834.png]]
****

thabu