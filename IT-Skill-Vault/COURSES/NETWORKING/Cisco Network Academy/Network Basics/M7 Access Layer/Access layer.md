## Encapsulation and the Ethernet Frame

**Ethernet frame** is the basic unit of data transmitted over an Ethernet network. It encapsulates the data being sent between devices, such as computers, switches, and routers.

**Encapsulation** - is a process of wrapping a message or data into another message or data.

Note: the actual sent across the network is the Ethernet frame and the network packet is inside of it.

| Premble | Destination MAC | Source MAC | Type/length | Data/Payload | FCS |
| ------- | --------------- | ---------- | ----------- | ------------ | --- |

|Field|Size|Purpose|
|---|---|---|
|**Preamble**|7 bytes|Synchronizes the sender and receiver.|
|**Start Frame Delimiter (SFD)**|1 byte|Marks the beginning of the frame. (Often considered part of the preamble.)|
|**Destination MAC Address**|6 bytes|Identifies the intended receiving device.|
|**Source MAC Address**|6 bytes|Identifies the sending device.|
|**Type/Length**|2 bytes|Specifies the protocol carried in the payload (e.g., IPv4, ARP, IPv6) or the payload length.|
|**Data (Payload)**|46–1500 bytes|Contains the actual information being transmitted. If the payload is less than 46 bytes, padding is added.|
|**Frame Check Sequence (FCS)**|4 bytes|Contains a CRC (Cyclic Redundancy Check) used to detect transmission errors.|

Note: Ethernet frame can contain not only the IP packets but also other packet like ARP, LLDP, and so on.

****
## Access Layer