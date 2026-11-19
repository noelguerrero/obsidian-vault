
## Server Commands

Check status of wazuh manager
```
sudo systemctl status wazuh-manager --no-pager
```

Start wazuh manager
```
sudo systemctl start wazuh-manager

```

Enable wazuh manage
```
sudo systemctl enable wazuh-manager
```


Check the status of wazuh indexer
```
sudo systemctl start wazuh-indexer --no-pager
```


Check the status of wazuh dashboard
```
sudo systemctl start wazuh-dashboard --no-pager
```

Check the list of available agent
```
sudo /var/ossec/bin/agent_control -l
```
****
## Agent Commands

To start wazuh
```
NET START WazuhSvc
```

To stop wazuh
```
NET STOP WazuhSvc
```

****



****