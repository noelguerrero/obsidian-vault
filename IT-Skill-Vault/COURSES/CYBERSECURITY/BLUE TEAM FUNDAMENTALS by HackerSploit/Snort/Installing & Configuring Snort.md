
## A. Install Snort on Ubuntu Terminal
- first update the `apt-get` syntax: `sudo apt-get update`
- Install Snort
```terminal
sudo apt-get install snort -y
```

**Additional:**
- **Snort Website:** snort.org
- **Snort Rules Generator:** http://cyb3rs3c.net/

****

## B. Input the Interface name and address range
- Configure first the terminal UI
`right click terminal -> preferences -> Profile -> Colors -> Built in Schemes -> Choose Linux Console`
#### B.1. Input the device interface

**To Find the device interface name**
- Another terminal: `if config` 
- Get this and input it into snort
![[Pasted image 20260318113512.png]]
- Then enter

#### B2. Input the Address Range
- To get that go to terminal: `ip a s`
- It is this just place the actual ip into 0 In this case: `192.168.2.0/24`
![[Pasted image 20260318114014.png]]
- Then enter

#### B.3. Add another interface (if it shows and if needed)
- Usually the installation of snort goes to two promt of interface card. So after the input of address range snort will prompt you another interface name.
- If you setting up the snort into bare metal server, the first prompt of interface is the router, then next is the interface of switch. Or base on the diagram in the notes
- AI or Search for other Information.

****

**Note:** You can confirm the snort is install by this code 
```terminal
snort --version
```

![[Pasted image 20260318115321.png]]

- Man Page For Snort: 
```terminal
man snort
```

****


## C. Allow Promiscuous Mode
- Vm settings
- Network
- Change network into Bridge Adapter
- Change Promiscuous Mode into Allow all

**If you device is not VM you can to this to set it into Promiscuous Mode**
```terminal
sudo ip link set enp0s3 promisc on
```

****

## D. Configuring Snort
The default configuration file of snort is stored under etc directory.

**To display the contents of etsy directory:** `ls -al /etc/snort`

![[Pasted image 20260318124531.png]]

**rules** - is it where the rules are stored.
**snort.conf** - configure file of snort.


**Note:** Permission required to edit those file, make sure you use account that have prviledge.

**Advise:** Make a copy of the config file to make sure we have back up when we mess around.

#### File navigation

**To open a file example:** 
```terminal
sudo vi /etc/snort/snort.conf
```

Or

```terminal
sudo nano /etc/snort/snort.conf
```

Or

to open with a line number
```terminal
sudo nano -l /etc/snort/snort.conf
```

**Find this section and type you address range:**
![[Pasted image 20260318130646.png]]

**Then leave the External net the is set to Any**
- because attacks and entrusion can come into any network, not just a single subnet.

#### Guideline on how to add a rule
![[Pasted image 20260318131206.png]]

#### Rules Files Section
![[Pasted image 20260318131103.png]]

There are enabled and disabled file, to disable a file just add this key `#` to comment it.


### To test snort
Syntax: `sudo snort -T -i interfaceName snorConfDirectory`

```terminal
sudo snort -T -i enp3s0 -c /etc/snort/snort.conf
```

This part is the important lines 
![[Pasted image 20260318133045.png]]


### In order to how to use snort, disable all the rules set 
Just add `#` in the first part of the rule to comment it or disable it.

Except for this rule 
![[Pasted image 20260407143945.png]]
