![[Pasted image 20260115125925.png]]

1. When you type a domain name, your computer first checks its **local cache** to see if it already knows the IP address. If not, it asks a **Recursive DNS Server** (usually from your ISP).

2. The recursive server also checks its cache. If it finds the answer, it sends it back right away. If not, it asks the **root DNS servers**, which point it to the correct **Top-Level Domain (TLD) server** (like `.com`).

3. The TLD server then tells it where the **authoritative DNS server** is. This authoritative server stores the actual DNS records for the domain and gives the correct answer.

4. The result is sent back to your computer and **cached** for a set time called **TTL (Time To Live)**, so future requests are faster.