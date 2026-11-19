**Dividing the Local Network**![[Pasted image 20260814113221.png]]
- We devide a LAN network into small broadcast domain using router.
- To avoid a device receive unnecessary broadcast.   
- To avoid excessive network traffic.
- To increase network security.

**Routing** - is a process to determine the best path to a destination.

****
### Routing Table
![[Pasted image 20260818132846.png]]

#### Communication within the network
1. H1 sends a message to H2 the packet will be.

| Dest_Mac | Source_Mac | Dest_IP      | Source_IP    |
| -------- | ---------- | ------------ | ------------ |
| ---      | AA-AA      | 192.168.2.20 | 192.168.1.10 |
2. If H1 doesn't know the MAC address of H2, it sends a ARP request then gets a reply and put it into the Ethernet frame.

| Dest_Mac | Source_Mac | Dest_IP      | Source_IP    |
| -------- | ---------- | ------------ | ------------ |
| BB-BB    | AA-AA      | 192.168.1.20 | 192.168.1.10 |
3. then the ethernet frame travel from H1 -> Switch -> H2.


### Communication between the network
1. When H1 sends a message to H3, the packet will be. The message travel from H1 -> Switch -> R1

| Dest_Mac | Source_Mac | Dest_IP      | Source_IP    |
| -------- | ---------- | ------------ | ------------ |
| ---      | AA-AA      | 192.168.2.50 | 192.168.1.10 |
2. Since the destination is outside of **the network the frame will send to the router 1**, (if the H1 doesn't know the router MAC address it sends the ARP request and then gets an reply) then the mac address will be.

| Dest_Mac | Source_Mac | Dest_IP      | Source_IP    |
| -------- | ---------- | ------------ | ------------ |
| 11-11    | AA-AA      | 192.168.2.20 | 192.168.1.10 |

3. Then the router 2 check its ARP cache to find the MAC address associated to the Destination IP address then the router removes the old ethernet frame and creates a new with the Dest_Mac of the designated receiver.

| Dest_Mac | Source_Mac | Dest_IP      | Source_IP    |
| -------- | ---------- | ------------ | ------------ |
| DD-DD    | AA-AA      | 192.168.2.20 | 192.168.1.10 |

4. Then the router forward it, so the ethernet frame travel from router 2 -> switch -> H4.

**Notes: Switches forward frames using MAC addresses. Routers forward packets using IP addresses and create a new Ethernet frame for the next network.**

****
### Routing Tables
- Router use routing tables to determine the best path to send a message. 
- it not concerned of the address of individual host, but it contain the address of the other networks and the best path to reach those network.

**Router table can be made in 2 ways**
- Dynamic - Dynamically update by the information received on other routers in a network.
- Manual - Manually configure by the network administrator.

![[Pasted image 20260818141928.png]]
- **Type -** The connection type. C stands for directly connected.
- **Network -** The network address.
- **Port -** The interface used to forward packets to the network.

****
### Default Gateway
When a host send message on the other host that is located on the remote network, the message will be send into the Default Gateway (router) then forwards it to the router of the destination host's network.