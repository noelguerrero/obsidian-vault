
**ARP (Address Resolution Protocol)** is a network protocol used to find the **MAC address** of a device when you already know its **IPv4 address**.

Basically when the PC isn't know the MAC address of the device that they communicate base on the IP address

it sends ARP request 
Example: 
- who is this: 192.168.1.11 
- then the other device send its MAC address AA:AA:AA:AA:AA:AA

**ND (Neighbor Discovery)** is the IPv6 version of ARP. It helps devices discover the MAC address of another device, routers, and other network information.

#### 2 Primary Address assigned in a device on the Network
- **Physical Address** - the MAC address.
- **Logical Address** - the IP Address.

#### Destination on Same Network

Also when sending a network frame in the same network, inside of it there is also a Destination and Source MAC address also Source and Destination IP address of the desired device.
![[Pasted image 20260810142315.png]]An example on how Network packet (Ethernet Frame) send within the same LAN

#### Destination on Remote Network

When sending a internet packet in other network, the destination MAC address will be the default gateway (router interface).

**Packet Flow Between Different Networks**

![[Pasted image 20260810210027.png]]
- **PC1 checks the destination IP** `10.1.1.10` and sees it is on a different network.
- PC1 sends the packet to its **default gateway (R1)**.
- PC1 uses **ARP** to find R1's MAC address.
- **PC1 sends the packet to R1:**


![[Pasted image 20260810210104.png]]
- **R1 removes the old MAC addresses** and creates a new Ethernet frame for R2.
- **R1 sends the packet to R2:**
- R2 receives the packet and sees that `10.1.1.10` is on its directly connected network.


![[Pasted image 20260810210146.png]]
- R2 uses **ARP** to find PC2's MAC address.
- **R2 sends the packet to PC2:**
- **Key point:** The **IP addresses remain the same**, while the **MAC addresses change at every router hop**.

****
### Broadcast Containment

**Broadcast Domain** - a local area network with 1 or more switches.

As the network grows, more hosts are added the more network traffic have excessive and LAN has a limit on its capability to support network traffic, so it is necessary to divide it.

**Router used to divide network into multiple broadcast domain.**
![[Pasted image 20260811213659.png]]

****
### ARP Process
ARP request is a broadcast message that uses `FF:FF:FF:FF:FF:FF` MAC address (All the devices receive a network frame when that is the destination MAC Address)

**3 Step process that ARP uses to determine the MAC address of the specific host.**
- Sends a broadcast network frame (uses broadcast MAC address) that contain the IPv4 address of a target host.
- The hosts receive the network frame and they compare the IPv4 address inside the message with there IP address, the host that didn't match there IP address will discard the message, but the intended host will send its MAC address to the sender of that message.
- The sending host stores the MAC address and IP address information in a table for future use.

Note: If the destination is on another network, the host ARPs for the **default gateway's MAC address**, not the destination host's MAC address.