- Suricata is a free and open source threat detection engine.
- It combines IDS, IPS, and network security monitoring.
- Develop by OSIF (Open Information Security Foundation)
	- GitHub Repo: [https://github.com/OISF/suricata](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa0wtNUE4OTF4aXFSZzRXVXRNT2FnZnhNdWVDUXxBQ3Jtc0trRjFacTk2ejlKTmlZalRuemFmVmdwRkpTakNNelBiU2pySklQN3NYNnJHbXZYMk4xdEJxdzNsOWoyVnhtNVFTZzFQMDFwYUk0bEdjZ2s0OFdtWEtkbF9wY0J6MmJKM2FKRS1pVWhXZ080aTV4Ui1kSQ&q=https%3A%2F%2Fgithub.com%2FOISF%2Fsuricata&v=91i7InHVOso)

**It has 2 main operational modes**
- Active (IPS) - Used to alert, log and block network traffic that matches specific rules.
- Passive (IDS) - Used to identify, alert and log suspicious network traffic within a network.


- It is same as snort wherein utilizes predefined rules to identify malicious network traffic.
- Similar to snort, the logs can be imported to a SIEM like Wazuh or Splunk for live security event monitoring.

**Suricata can be place similar to snort**
![[Pasted image 20260616122504.png]]