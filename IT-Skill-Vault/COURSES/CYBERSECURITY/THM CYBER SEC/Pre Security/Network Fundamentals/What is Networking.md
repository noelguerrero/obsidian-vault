## What is Networking?
- Networks are simply things connected. For example, your friendship circle: you are all connected because of similar interests, hobbies, skills and sorts.

![[Pasted image 20260102114015.png]]

- In computing, a network can be formed by anywhere from 2 devices to billions.

### What is Internet?
Internet is one giant network that consists of many, many small networks within itself.

![[Pasted image 20260102113934.png]]

Internet is made of many small networks that all joined together. These small network is the private network, and the one the connecting this small network is public network (or Internet).

- Private Network
- Public Network


### Identifying Devices on a Network
To communicate and maintain order, devices must be both identifying and identifiable on a network.

In us, Humans we can change our name, but we can't change our fingerprints and every individual have a unique that identifies there self. It is same in the devices.

- Internet Protocol (IP) address - As a name
- Media Access Control (MAC) Address - As a fingerprints, think of it as similar to a serial number.

### Internet Protocol (IP) Address
It can be used to identifying a host (devices) on a network for a period of time. 

IP address is divided into four Octets, each value combination of those 4 octets is the IP address of a device.

![[Pasted image 20260102115529.png]]

And this ip address calulated through a technique called IP addressing or subnetting.

IP address follow a set of standards known as protocols. These protocols are the backbone of networking and force many devices to communicate in the same language.

Devices can determine which they are in (public or private network) using public or private address.

- Public Address - Used to identify device on the internet.
- Private Address - Used to identify device among other devices. (It assigned into our router by ISP)

![[Pasted image 20260102120959.png]]
These devices will able to use their private IP address to communicate with each other. And the public address of the devices is the address of their router assigned by Internet Service Provider (ISP).

#### IPv4 (Internet Protocol version 4)
is a **network protocol** used to identify devices on a network and route data between them, It supports 2^32 IP addresses (4.29 Billion). 

Example:
```
192.168.0.1
```


#### IPv6 (Internet Protocol version 6) 
is the **newer version of IP** designed to replace IPv4 and solve its address-shortage problem, It supports 2^128 of IP addresses (340 trillion-plus).

Example:
```
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```


### Media Access Control (MAC) Address
Every devices will have physical network interface which is a microchip board that will found in device's motherboard. This network interface is assigned a unique address called MAC address.

Example:
```
a4:c3:f0:85:ac:2d
```

The first six characters represent the company that made the network interface, and the last six is a unique number.

![[Pasted image 20260102123047.png]]

**MAC address can be spoofed or faked**
A spoofed MAC address means the MAC address of a device has been deliberately changed or faked so it appears as a different device on a network.

![[20260102-0459-25.0766884.mp4]]

**Possible happen when the MAC address is spoofed on the network:**
- Network access may be gained (or lost)
- Another device may get disconnected
- Network instability and errors
- Traffic interception or redirection
- Bypassing restrictions or limits
- etc



### Ping (ICMP)
- One of the most fundamental tools available for us
- It uses ICMP (Internet Control Message Protocol) packets to determine the perfomance of a connection between devices, for example, if the connection exists or is reliable.

Pings can be performed against devices on a network, such as your home network or resources like websites. This tool can be easily used and comes installed on Operating Systems (OSs) such as Linux and Windows. The syntax to do a simple ping is `ping IP address or website URL`. Let's see this in action in the screenshot below.

![[Pasted image 20260102125234.png]]
Here we are pinging a device that has the private address of _192.168.1.254_. Ping informs us that we have sent six ICMP packets, all of which were received with an average time of 4.16 milliseconds.


