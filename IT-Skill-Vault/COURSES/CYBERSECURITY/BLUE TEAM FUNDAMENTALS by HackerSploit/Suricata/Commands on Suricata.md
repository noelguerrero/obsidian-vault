
## DIRECTORIES

### Suricata Conf dir
To display the directory
```bash
ls -al /etc/suricata
```

![[Pasted image 20260618105452.png]]

### Suricata Rules DIR
```bash
ls -al /etc/suricata/rules
```

### Suricata Log DIR
```
ls -al /var/log/suricata
```

****
## Check your IP addresses

```bash
ifconfig
```

```bash
ip a s
```

****
## Suricata Man Page

```bash
suricata --help
```

****
## Suricata Command

To see the status
```bash
sudo systemctl status suricata.service
```

To run suricata
```bash
sudo systemctl start suricata.service
```

To stop suricata
```bash
sudo systemctl stop suricata.service
```

To test the suricata conf file
```bash
sudo suricata -T -c /etc/suricata/suricata.yaml
```