In network we have physical topology and logical topology
****
## Physical Topology 
- The physical topology is layout on how device connected to each other.

**Example:**
- bus topology
- start topology
- mesh topology
****
## Logical Topology
- Logical topology it refers on how data moves thorough the network.


| **Physical topology** | How devices and cables are physically connected      |
| --------------------- | ---------------------------------------------------- |
| **Logical topology**  | How data travels or communicates through the network |

****
## Bus Topology or Bus Network
is a network setup where **all devices are connected to one main cable**, called the **backbone cable** or **bus**.

![[Pasted image 20260529133625.png]]

we have:
- 10base5
- 10base2

Both **10BASE5** and **10BASE2** are **old Ethernet standards** that use **bus topology** and **coaxial cables**.

- **10** = 10Mbps speed
- **BASE** = Baseband transmission (one signal type at a time)
- **5** or **2** = maximum cable length

**Mbps**= Mega (Million) bits per second

****
## Star Topology (hub)
- It have a internet hub
- uses rj45 cable
![[Pasted image 20260529140046.png]]

### Hub: 
- it connects all device using UTP or RJ45 cable
- It sends the data in all connected devices
- also known as dumb device

But the hub send all the data in the connected device that cause collision, so to prevent that they have random back off timer, then try again to send the data. It is called **CSMA/CD**

#### CSMA/CD (Carrier Sense Multiple Access/Collision Detection)

**CSMA**
- It is a method used in older Ethernet networks to control how devices share the same network cable.
- Before they send data, they make sure first that there is no device speaking

#### CD
- Detects collision

### Token Ring Switch
- sends the data in sequence
- Device A -> Device B -> Device C and so on.

![[Pasted image 20260529141715.png]]

****
## Unicast / Broadcast / Multicast

- **Unicast:** one device talking to one.
- **Broadcast:** one device talking to everyone.
- **Multicast** one device to certain sub group.

****
## Bridge Network

### Bridge
- it is network device that connects two network segments together, and helps control traffic betwen them.
- Forward traffic base on MAC addresses
![[Pasted image 20260529145324.png]]

****
## Switch Network

### Switch
- Also known as multi-port bridge, it is the evolve version of bridge
- It connects many devices/segments
- it forwards traffic base on MAC addresses
- It uses **ASIC (Application-Specific Integrated Circut)** - that allows move traffic quickly.

**Types of Switch**
- Manage switch - it is switch that can manage the configuration.
- Unmanage switch - switch that can't manage configuration.

****
## Router Network
![[Pasted image 20260529174013.png]]

![[Pasted image 20260529174104.png]]

![[Pasted image 20260529174826.png]]
Usually the home router like this can do multiple network devices functionalities like:
- Router
- switch
- firewall
- Access point

****
## Firewall
- It is a hardware or software that filter inbound and outbound traffic
- It protects the network or the device from malicious activity.

**Hardware firewall:**
![[Pasted image 20260529174638.png]]
this medium size firewall is for small business, and for the larger or bigger enterprises they use much bigger hardware firewalls.


**Devices → Switch → Firewall → Router → Internet**
![[Pasted image 20260529175550.png]]
- This set up is much secure since the router only sees the filtered traffic.
- Less flexible for internet-side filtering policies.
- Real world set up.


**Devices → Switch → Router → Firewall → Internet**
![[Pasted image 20260529175754.png]]
- Strong security control setup and better for enterprise designs.
- But router already processes traffic before filtering.
- Less early protection, but flexible

**One of the feature of firewall is IDS and IPS**

****
## IDS VS IPS

**IDS (Intrusion Detection System)**
- It allows us to detect malicious traffic.
- It sniffs the traffic and alerts you.

**IPS (Intrusion Prevention System)**
- It allows us to prevent malicious traffic
- It sniffs the traffic and automatically blocks it.

****
## Wi-Fi (Wireless Fidelity)
- It is a wireless network technology that allows devices to connect to a network or internet without cables.

**Access Point (AP)** - It is a network device that allows wireless devices to connect to wire network.
![[Pasted image 20260529181919.png]]

**Wireless Lan Controller** - It is used to configure one or more AP at the same time.
![[Pasted image 20260529182136.png]]