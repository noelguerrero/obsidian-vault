
## Firewall
- It can be software or hardware that protects devices by scanning each data packets the will in and out.

## Firewall & Network Protection
![[Pasted image 20260113113634.png]]

Per Microsoft, "_Windows Firewall offers three firewall profiles: domain, private and public"._

- **Domain** - _The domain profile applies to networks where the host system can authenticate to a domain controller._ 
- **Private** - _The private profile is a user-assigned profile and is used to designate private or home networks._
- **Public** - _The default profile is the public profile, used to designate public networks such as Wi-Fi hotspots at coffee shops, airports, and other locations._

| Network Type | Description                                 |
| ------------ | ------------------------------------------- |
| **Domain**   | Managed by an organization (company/school) |
| **Private**  | Trusted home or office network              |
| **Public**   | Untrusted networks (cafes, airports)        |


If you click on any firewall profile, another screen will appear with two options: **turn the firewall on/off** and **block all incoming connections**.

![[Pasted image 20260113114116.png]]


**Allow an app through firewall**
![[Pasted image 20260113114223.png]]
You can view what the current settings for any firewall profile are. In the above image, several apps have access in the Private and/or Public firewall profile. Some of the apps will provide additional information if it's available via the `Details` button.


**Advanced Settings**
![[Pasted image 20260113114405.png]]
Configuring the **Windows Defender Firewall** is for advanced Windows users. Refer to the following Microsoft documentation on best practices [here](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/best-practices-configuring).

**Cmd:**`WF.msc`