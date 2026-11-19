
## Things that we should aware of:

### 1. Sandbox Environment
A **sandbox environment** is a **safe, isolated place to test things** without risking your real system or data.

**Common examples:**
- **Virtual Machines (VMs)** – VirtualBox, VMware
- **Browser sandboxes** – Chrome isolates tabs
- **Online sandboxes** – VirusTotal, Any.Run
- **Cloud sandboxes** – AWS test environments

Simply create virtual machine doesn't mean they are in sandbox environment, we need to configure our virtual machine properly to avoid infecting our real machine.


### 2. Snapshots
It is basically saving a specific state of a system so that if there is a happen we can go back to that previous state.

We need to create snapshots of the stable state of our machine before testing something else.


### 3. Specifications
We need to aligned our virtual machine specs in our real machine.

Example: we can run 10 virtual machine simultaneouslyin 4gb ram laptop

****

## Different Network Settings in Virtual Machine


### 1. NAT (Network Address Translation) - Default

![[Pasted image 20260202204733.png]]

- It can use internet.
- Each VMs have separate network using the host network adapter.

When you use **NAT**, the virtual machine can go out to the internet using your real computer, but nothing can come back to it. It’s like the VM is borrowing your internet quietly. This is the simplest option and works well when you only want internet access inside the VM.



### 2. NAT Network
![[Pasted image 20260202205604.png]]
- It is similar NAT but the other VM's can talk to each other and also can access the internet. 
- But the real device cannot talk the VM's


A **NAT Network** is similar to NAT, but with a small improvement. Multiple virtual machines can talk to each other and also access the internet, but your real computer still cannot talk to them directly. It’s like a private group that can go online together.



### 3. Bridged
![[Pasted image 20260202205639.png]]

- VM's can act as physical machine on the network and have internet access.
- **Noted: don't execute malware in the bridged!!!!**
- The VM's and your physical machine is on the same network.

When you use a **Bridged Adapter**, the virtual machine behaves like a real computer on the same network as you. Your router gives it its own IP address, just like your phone or another laptop. Because of that, your real computer and other devices can see it and connect to it. This is useful if you want to access the VM from outside or run services on it.


### 4. Host-Only Network
![[Pasted image 20260202205940.png]]
- the VM's can communicate into your physical machine but there is no internet access.
- It is like there is a cable between you physical machine and the VM's


### 4. Internal Network
![[Pasted image 20260202210209.png]]

- VM's can talk to each other but they cannot talk into your physical machine or in the internet.
- **Note: in VMware it is called "LAN Segment"**


An **Internal Network** is even more isolated. In this case, virtual machines can talk to each other, but they cannot talk to your real computer or the internet. It’s like putting several virtual computers in a locked room where only they can communicate. This is useful for practice labs or networking experiments.


### 5. Not Attached
![[Pasted image 20260202210625.png]]

It basically the VMs is not attached on anything 

When a virtual machine is set to **Not Attached**, it’s like the network cable is unplugged. The virtual machine has a network card, but it is not connected to anything. Because of that, it cannot access the internet, it cannot talk to your real computer, and it cannot talk to other virtual machines.


### Summarize
![[Pasted image 20260202212150.png]]


****

## Scenarios for each Network Settings

1. Testing Tools with Internet Connectivity
**You can use:**
- Default Network Setting

2. Analyze Malware
**You can use:**
- Not Attached - most recommended
- Internal Network - if its need a two or more VMs