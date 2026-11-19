**For Ubuntu Linux:**
- `sudo apt-get install snort` - to install sno
- `sudo snort -T -i enp3s0 -c /etc/snort/snort.conf` - To test snort

- `sudo snort -q -l /var/log/snort -i -A enp0s3 -A console -c /etc/snort/snort.conf` - Start snort


****
**For Kali Linux**
- `msfconsole` - to open metasploit console


****
## To open a certain file

- `ls -al /etc/snort` - to show directories of snort

- `sudo gedit -l /etc/snort/rules/local.rules`  - to open local.rules file.

- `sudo gedit -l /etc/snort/snort.conf` to open snort config file with line number

Note: Before using the GNOME text editor (gedit) download it first: `sudo apt install gedit`

****
### Controls on Nano Editor

`ctrl + o` - Save
`ctrol + g` - Help


****
### Snort Syntax Guide:

`-A` **alert mode** - is the operating mode where Snort monitors network traffic and generates alerts when it detects suspicious activity or matches a rule.

| Mode      | Meaning                          |
| --------- | -------------------------------- |
| `fast`    | Short/simple alerts              |
| `full`    | Detailed alert information       |
| `console` | Show alerts directly in terminal |
| `none`    | No alerts displayed              |
| `cmg`     | Very detailed packet/hex dump    |
| `unsock`  | Send alerts to UNIX socket       |
Ex: `snort -A fast`

****

`-l` **log-dir -** is used to specify where Snort saves its log files.

Ex: `snort -l /var/log/snort`

****

`-c` **configuration file -** It tells Snort which config file to use when starting.

Ex: `snort -c /etc/snort/snort.conf`

****

`-i` **interface -** It tells Snort which network interface to monitor.

Ex: `snort -i eth0`

****

`-q` **Quiet operation -** It reduces unnecessary output on the terminal while Snort is running.

Ex: `snort -q -A fast -i eth0`

****

`-Q` **Enable inline mode -** It allows Snort to work as an IPS (Intrusion Prevention System), meaning it can actively block or drop malicious traffic instead of only detecting it.

Ex: `snort -Q -c /etc/snort/snort.conf -i eth0`


