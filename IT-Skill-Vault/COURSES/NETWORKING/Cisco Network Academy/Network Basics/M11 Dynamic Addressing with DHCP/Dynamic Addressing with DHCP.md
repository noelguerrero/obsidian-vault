**Static Addressing** - Manually configuring network information for a host,
- IP Address - Identifies the host on the network
- Subnet mask - Use to identify network and host portion on the address.
- Default Gateway - the address of the networking device that host uses to connect in the internet.

Note: when using static address that address is permanently in a host unless changed it.

**Dynamic Addressing** - Automatically assign network information (IP Address, Subnet Mask, Default Gateway) into a host using DHCP protocol.

Note: when using Dynamic address, the address is not permanent, the address have a period of time in the host and when the host is powered off, the address will become available and can reuse by other host.

****
### DHCP Server
Your device can automatically receive the IP address via DHCP client (software on the client device) from DHCP server (DHCP service software typically installed in the router or in the other network device).

![[Pasted image 20260806160814.png]]


**How DHCP works:**
1. **DHCP Discovery** - when client request a IP address it sends a broadcast packet in all the device in the network. 
2. **DHCP Offer** - the DHCP server only respond on the broadcast and suggest IP address for the client.
3. **DHCP Request** - the client sent a request that it accept the address given by the server.
4. **DHCP Acknowledgment** - the server respond with acknowledgement