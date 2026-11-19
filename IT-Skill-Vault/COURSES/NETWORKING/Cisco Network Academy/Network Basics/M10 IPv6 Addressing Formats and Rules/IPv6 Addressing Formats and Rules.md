
The depletion of IPv4 space and the limitations is the reason why IPv4 is develop

### 3 Migration Techniques to Migrate from IPv4 to IPv6
- **Dual Stack** - running both IPv4 and IPv6 simultaneously.
- **Tunneling** - Encapsulate IPv6 packet at IPv4 packet.
- **Translation** - Using NAT64 to translate IPv6 packet to IPv4 and vise versa.

****

### IPv6 Addressing Formats
- IPv6 using Hexadecimal numbers. **0 1 2 3 4 5 6 7 8 9 A B C D E F** , Numbers 0-9 and letters A-F
- IPv6 has 128 bits or 32 hexadecimal (hextels)
![[Pasted image 20260805132704.png]]
- Example of IPv6 Address: `2001 : 0db8 : 0000 : 1111 : 0000 : 0000 : 0000: 0200`
![[Pasted image 20260805133611.png]]

#### Preferred format
It is a standard way of writing IPv6 address using eight Hextet contains four hexadecimal digits including 0

Ex: `2001:0DB8:0000:0000:0000:FF00:0042:8329`
- It contains **8 hextets**.
- Each hextet has **exactly 4 hexadecimal digits** (leading zeros are included).
- The hextets are separated by colons (`:`).


#### Rules in IPv6
- **A. Leading zeros can be omitted or remove**
```
0001 → 1
00AB → AB
0042 → 42
0000 → 0
```
Example: 
`2001:0DB8:0000:0000:0000:FF00:0042:8329` 
Becomes -> `2001:DB8:0:0:0:FF00:42:8329`

- **B. If there are two or more consecutive hextets that are all `0000`, they can be compressed into `::`.**
Example:
`2001:DB8:0000:0000:0000:FF00:42:8329`
Becomes -> `2001:DB8::FF00:42:8329`

**Note:** Double colon can use only once, so use it into a longest zero string part of IPv6. But if there is another zero string just omit the leading zeros. If the strings are equal the double colon should use in the first string.
![[Pasted image 20260805135146.png]]