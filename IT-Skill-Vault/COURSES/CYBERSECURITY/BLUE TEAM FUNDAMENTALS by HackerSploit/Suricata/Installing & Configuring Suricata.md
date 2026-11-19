**Website:** suricata.io

****
## Installing Suricata

```
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:oisf/suricata-stable
sudo apt-get update && sudo apt-get install suricata
```

****
**Note:** Suricata can be stopped or started with systemd or the init system in our distribution. If we want to run suricata in system startup.

Then we can enable the service
```
sudo systemctl enable suricata
```
Noted: it consumed much more resources

Other related terminal prompt
```
sudo systemclt status suricata
sudo systemctl stop suricata
sudo systemctl start suricata
```
****
## Check the directory
```
ls -al /etc/suricata
```
![[Pasted image 20260618111149.png]]

Check if there is a rules folder, the dir must be in here
```
ls -al /etc/suricata
```
or
```
ls /var/lib/suricata/
```

If not just run this commands
```
which suricata-update
/usr/bin/suricata-update
sudo suricata-update
```

****
## Configure the suricata.yml

`suricata.yml` -> is the configure file of suricata.

To open suricata.yml
```bash
sudo gedit /etc/suricata/suricata.yml
```

**Change this part into your network range**
![[Pasted image 20260618112517.png]]in my case it is `192.168.100.0/24`

**Also specify your network interface in this parts**
![[Pasted image 20260618112837.png]]
![[Pasted image 20260618113148.png]]
In my case it is `enp0s3`

**This is optional**
![[Pasted image 20260618113459.png]]
set this to true

****
## You can download rules sets based on your needs

To list the available resources
```
sudo suricata-update list-sources
```

![[Pasted image 20260618115704.png]]
Note: if its commercial, it is subscription. But if its MIT, it is open source. 

**To download the resource syntax**
```
sudo suricata-update enable-source nameOfSource
```

then update it
```
sudo suricata-update
```


****
## Test the suricata conf file

```bash
sudo suricata -T -c /etc/suricata/suricata.yaml
```

![[Pasted image 20260622121808.png]]

****
## Starting suricata

```bash
sudo systemctl start suricata.service
```

****
## Suricata Logs

To go to log dir
```bash
ls -al /var/log/suricata
```

![[Pasted image 20260622122745.png]]
- `eve.json` stores logs in json format
- `fast.log` stores logs in standard format

****
## To test if the malicous activity is log

```bash
curl http://testmynids.org/uid/index.html
```

Check if the activity is logged
```bash
sudo cat /var/log/suricata/fast.log 
```

![[Pasted image 20260622123655.png]]

****
## Custom Rules

```bash
sudo nano /var/lib/suricata/rules/local.rules
```

Add this ICMP alert
```
alert icmp any any -> $HOME_NET (msg:"ICMP Ping"; sid:1; rev:1;)
```
Note: suricata rules syntax is the same as snort.

Then open the suricata.yaml
```
sudo nano /etc/suricata/suricata.yaml
```

Add this on the rule-files section
```
/var/lib/suricata/rules/local.rules
```
Then saved

Then check the suricata.yaml
```
sudo suricata -T -c /etc/suricata/suricata.yaml -v
```
If its good we can run suricata

Run suricata
Then ping it with other machine
Then check the logs
```bash
sudo cat /var/log/suricata/fast.log
```

![[Pasted image 20260622131826.png]]

****
## Utilizing json command line processing tool or JQ
It allows us to view the json format logs (`eve.json`)

Install the JQ
```bash
sudo apt-get install jq 
```

Ping the machine with other machine 

then
```
sudo tail -f /var/log/suricata/eve.json | jq 'select(.event_type=="alert")'
```
![[Pasted image 20260622133422.png]]
