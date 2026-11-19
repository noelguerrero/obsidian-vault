## Troubleshooting Commands
- Ipconfig - display IP configuration information
- ping - Test connection to other IP host
- netstat - display network connections.
- tracert - display the route taken to the destination
- nslookup - directly queries the IP name of the server of website.

****
## The `ipconfig` Command

- `ipconfig` - display the IP information
- `ipconfig /all` - display all the IP information
- `ipconfig /renew` - it gets a new IP address
- `ipconfig /release` - it removes its previous IP address

****
## The `ping` Command
- echo request - is the one that sent to the target host
- echo reply - is the response of the target host
- best practices is ping the default gateway to identify if the problems comes at local host
- If the ping works in both domain name and IP address the services of the application that want to access is have the problem 

**Syntax:** `ping ipAdd/domainName`

```example
ping google.com
ping 192.168.1.100
```

**Other options for ping**

|Option|Description|Example|
|---|---|---|
|`-t`|**Continuous ping** — keeps sending ping requests until you stop it with `Ctrl + C`. Useful for monitoring a connection.|`ping -t 8.8.8.8`|
|`-a`|**Resolve address** — tries to convert the destination IP address into its hostname.|`ping -a 192.168.1.1`|
|`-n`|**Number of requests** — specifies how many ICMP Echo Requests to send.|`ping -n 10 8.8.8.8`|
|`-l`|**Packet size** — specifies the amount of data, in bytes, sent in each ping packet.|`ping -l 1000 8.8.8.8`|
|`-f`|**Don't Fragment** — prevents an IPv4 packet from being fragmented while traveling through the network. Useful for testing MTU.|`ping -f -l 1500 8.8.8.8`|
|`-i`|**TTL value** — sets the Time To Live value, which limits how many routers/hops the packet can pass through.|`ping -i 5 8.8.8.8`|
|`-w`|**Timeout** — specifies how long Windows waits for a reply, in milliseconds, before considering the request timed out.|`ping -w 2000 8.8.8.8`|
|`-r`|**Record route** — records the route taken by the packet through the network (IPv4).|`ping -r 9 8.8.8.8`|
|`-s`|**Timestamp** — records timestamps for hops along the route (IPv4).|`ping -s 4 8.8.8.8`|
|`-4`|**Force IPv4** — makes `ping` use IPv4 instead of IPv6.|`ping -4 google.com`|
|`-6`|**Force IPv6** — makes `ping` use IPv6 instead of IPv4.|`ping -6 google.com`|
****
