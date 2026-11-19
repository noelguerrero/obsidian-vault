
### ICMP Ping Detection

**On the rules config file:**
`alert icmp any any ->$HOME_NET any (msg:"ICMP Ping Detected"; sid:10001; rev:1;)` `

**On the terminal**
`sudo snort -q -l /var/log/snort -i enp0s3 -c /etc/snort/snort.conf`

Then Ping a device
![[Pasted image 20260502100905.png]]

****
### SSH Authentication Attempt Detection

**On the snort rules config file of victim device:**
`alert tcp any any -> $HOME_NET 22 (msg:"SSH Authentication Attempt"; sid: 100002; rev: 1;)`

**On the terminal of victim device:**
`sudo snort -q -l /var/log/snort -i enp0s3 -c /etc/snort/snort.conf`

**On the attacker device:**
![[Pasted image 20260502110450.png]]
Note: The mr-ubuntu@192.168.100.172 is the victim device and the password that i type is also the victim password.


![[Pasted image 20260502110929.png]]

****
## Using Snort Tools

Link: [`https://snorpy.cyb3rs3c.net/`](https://snorpy.cyb3rs3c.net/)
![[Pasted image 20260508100355.png]]

### FTP Authentication Attempt

![[Pasted image 20260508102703.png]]
Note: in this case i put the defender ip address in dest port


**On the Defender machine**
- `alert tcp any any -> 192.168.100.172 21 (msg:"FTP Authentication Attempt"; sid:100003; rev:1;)` - Put it into snort.conf file
- Then start the Snort

**On the attacker machine terminal**
- `ftp 192.168.100.188 21`
- Input the email and password of the target's machine

**On the defender machine this will display**
![[Pasted image 20260508102333.png]]

****
## Another great resource to learn snort is to take a look the rules written by the community


You can download this rules in the snort website
![[Pasted image 20260508130713.png]]

Open the community rules file it includes various community rules
![[Pasted image 20260508131645.png]]

### Eternal Blue Rule
**EternalBlue rules** - In snort community this rules made to identify traffic related to the **EternalBlue exploit**.

**EternalBlue exploit** - is a hacking tool/exploit that attacks a weakness in Microsoft Windows’ SMB (Server Message Block) service.

**Note:** EternalBlue only works at windows devices

![[Pasted image 20260508131810.png]]

**Then put it into local rules file** (but you can just include the community.rules file into the snort.conf to import all the rules inside of it)
![[Pasted image 20260508132818.png]]

**On attacker machine**
- `msfconsole` - on terminal
- `search eternalblue` - on metasploit console
- ![[Pasted image 20260512222736.png]]
- `use exploit/windows/smb/ms17_010_eternalblue`
- `set RHOST 192.168.100.4` - the target device (windows)

![[Pasted image 20260512224357.png]]

**The ubuntu must display this**
![[Pasted image 20260512224513.png]]

****
## You can utilize Wireshark to identify the malicous activity in the network packets that snort record

**All the snort logs are goes into this directory**
`/var/log/snort
![[Pasted image 20260515102315.png]]

**So you need to open those file with using wireshark to analyze the network packets**
![[Pasted image 20260515102634.png]]

But in this case we log our network traffic in the console (terminal), it is saved by the snort in raw that's why cannot open it without wireshark. So we need to log our traffic in file so that we can open it without the help of wireshark. 
****
## We can log our traffic in a file 

**instead of this:**
`sudo snort -q -l /var/log/snort -i -A enp0s3 -A console -c /etc/snort/snort.conf`

**we do this:**
`sudo snort -q -l /var/log/snort -i -A enp0s3 -A fast -c /etc/snort/snort.conf`

**Simple  guide:**

| Mode      | Meaning                          |
| --------- | -------------------------------- |
| `fast`    | Short/simple alerts              |
| `full`    | Detailed alert information       |
| `console` | Show alerts directly in terminal |
| `none`    | No alerts displayed              |
The `console` is just display the traffic in the terminal, but the `fast` and `full` log it into specific file

### `fast`

**On ubuntu terminal:**
`sudo snort -q -l /var/log/snort -i -A enp0s3 -A fast -c /etc/snort/snort.conf`

**So when we create a traffic**
![[Pasted image 20260515103810.png]]

**We can see it in this file**
![[Pasted image 20260515104118.png]]


![[Pasted image 20260515104050.png]]

### `full`

**On ubuntu terminal:**

`sudo snort -q -l /var/log/snort -i -A enp0s3 -A full -c /etc/snort/snort.conf`

**This is what it looks like:**
![[Pasted image 20260515105016.png]]