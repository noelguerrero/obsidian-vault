### Default gateway 
is the device (usually a router) that your computer or phone uses to send data to networks outside the LAN, such as internet.

![[Pasted image 20260807145927.png]]


****
### Network Address Translation (NAT) 
it allows a device in private network to send and receive a traffic into the public network (Internet).

**How it works:**

**WHEN THE HOST SEND A PACKET IN THE INTERNET**
It have Source and destination address

Example:
```Packet
Source_Address: 192.168.1.100
Dest_address: 200.100.5.5
```

- the NAT network change the source address into public address to represent that host. 192.168.1.100  to 220.100.58.1 <- It is base on the router's public address

```Packet
Source_Address:220.100.58.1
Dest_address: 200.100.5.5
```

- Then it i sends on the desired receiver of that packet.



**WHEN IT RECEIVE A PACKET**
```
Source_Address:200.100.5.5
Dest_address: 220.100.58.1
```

- NAT networks look at the destination address if there is a private IP address that represent that public destination address (200.100.5.5). and if it is.

- It change the destination address into that specific private address on the private network
```
Source_Address:200.100.5.5
Dest_address: 192.168.1.100
```

- Then the packet is send to the desired host base on the destination address.

