
### 3 Network Transmission
- Unicast - sending packet from single device to single device
- Broadcast - sending packet from single device to multiple devices within the LAN
- Unicast - sending a packet from single device to selected group of device.
	- Ex: 172.16.4.1 send a packet into 172.16.4.2 - 172.16.4.5

****
### Types of IPv4 Adresses
#### RFC 1918 Address Range
- address that can only use of reserved for private organizations like home, school, and company networks.
- It cannot be routed in the internet, so devices need NAT device (like router) to communicate with them

| Network Address and Prefix | RFC 1919 Private Address Range |
| -------------------------- | ------------------------------ |
| 10.0.0.0/8                 | 10.0.0.0 - 10.255.255.255      |
| 172.16.0.0/12              | 172.16.0.0 - 172.32.255.255    |
| 192.168.0.0/16             | 192.168.0.0 - 192.168.255.255  |

#### Network Address Translation (NAT)
- It translate the source IP address of the packet before ISP deliver it into public network

![[Pasted image 20260727134017.png]]

#### Special use IPv4 Address 
- **Loopback addresses (127.0.0.0 /8 or 127.0.0.1 to 127.255.255.254)** - is a special IP address that a computer uses to **communicate with itself**. It never leaves the device or travels across the network.
- **Link-local addresses (169.254.0.0 /16 or 169.254.0.1 to 169.254.255.255)** - known as Automatic Private IP Addressing (APIPA). the IP address that assigns to itself when DHCP is not available. 

#### Legacy Classful Addressing
- **Class A (0.0.0.0 /8 to 127.0.0.0 /8)** - use to support very large organization. 16 million host addresses.
- **Class B (128.0.0.0 /16 or 192.255.0.0 /16)** - use to support moderate to large organization. 65K+ host addresses. 
- **Class C (192.0.0.0 /24 - 223.255.255.0 /24)** - Use to support small networks, with 254 hosts.
- **Class D (224.0.0.0 to 239.0.0.0)** - multicast block
- **Class E (240.0.0.0 to 255.0.0.0)** - experimental address block

Note: This classful addressing was replace by much efficient way. it is the class less addressing where it ignores the rules of classes (A.B.C and so on).  

Both IPv4 and IPv6 are managed by Internet Assigned Numbers Authority (IANA). and the IANA manages and allocates IP address blocks to the five Regional Internet Registries (RIRs)

#### Regional Internet Registries (RIR)
![[Pasted image 20260727141435.png]]

****
### Network Segmentation

#### Broadcast Domain
![[Pasted image 20260730151829.png]]
When sending broadcast or using ARP request to find the Ip address of a device the switch broadcast it in all interface except for the one who send it, but the broadcast doesn't go to the other domain or ethernet LAN. This is called layer 2  broadcast domain.

Note: by default router didn't forward the Ipv4 broadcast packet.

#### Problems with Large Broadcast Domain
A large broadcast domain that connects many host in the network can generate excessive amount of broadcast that can affect the network.

The solution on that is subnetting where in you divide the broadcast network into tiny subnet networks to reduce the size of the network and impeoves network performance.

![[Pasted image 20260730153016.png]]
noted: the broadcast that came from LAN 1 can propagate into the LAN 2 and vise versa.

#### Illustration on how Network Administrator group devices and services into subnets

**Subnetting by Location**
![[Pasted image 20260730153406.png]]


**Subnetting by Group or Function**
![[Pasted image 20260730153513.png]]


**Subnetting by Device Type**
![[Pasted image 20260730153556.png]]