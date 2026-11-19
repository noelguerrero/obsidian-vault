
## A. AWS Services Preview

Note: You can learn and know the features of each product in AWS websites.


## B. Evolution of Computing

#### Dedicated
- A physical server **wholly utilized by a single customer.**
- You have to guess you capacity
- You'll overpay for an underutilized server
- You can't vertical scale, you need a manual migration
- Replacing a server is very difficult
- You are limited by your Host Operating System
- Multiple apps can result in conflicts in resource sharing
- You have a ==**guarantee of security, privacy, and full utility of underlying resources**==

Its more secure, but it depends on your skills to make it secure. But if you had a virtual machine or anything the CSP are responsible to provide and make a secure machine.

**Why would you use dedicated machine?** Maybe you need a high performance computing that you chose to use a physical machine that is only for you.

![[Pasted image 20250207124302.png]]


#### Virtual Machines (VMs)
- You can run **multiple Virtual Machines on one machine**
- ===Hypervisor=== is the software layer that lets you run the VMs
- A physical server shared by multiple customers (you can share the cost with multiple customers.)
- You are to pay for a fraction of the server
- You'll over pay for an underutilized Virtual Machine
- You are limited by your Guest Operating System (but since its virtualize its easy to migrate a way)
- Multiple apps on a single Virtual Machine can result in conflicts in resource sharing
- Easy to export or import image for migration
- Easy to Vertical or Horizontal scale

Note: simple analogy, VMS are each app gets its own OS -> It can be heavy and slow.

VMs is most popular and common offering for compute because people are very comfortable with those.

![[Pasted image 20250207125304.png]]


#### Containers
- **Virtual Machine running multiple containers**
- ===Docker Deamon=== is the name of the software layer that lets you run multiple containers
- You can maximize the utilize of the available capacity which is more cost-effective (you can add new and resize those containers for flexibility)
- Your containers share the same underlying OS so containers are more efficient than multiple VMs
- Multiple apps can run side by side without being limited to the same OS requirements and will not cause conflicts during resource sharing (but its lot work to maintain)

![[Pasted image 20250207130937.png]]

Note: Simple analogy, VMS are each app gets its own OS -> It can be heavy and slow. While Containers are app live in separate apartments but share the same building OS -> efficient and fast.


#### Functions
- Are managed VMs running managed containers 
- Known as Serverless Compute
- You upload a piece of code, choose the amount of memory and duration
- Only responsible for code and data, nothing else
- Very-cost effective, only pay for the time code is running, VMs only run when there is code to be executed
- Cold Starts is a side effect of this setup

![[Pasted image 20250207133543.png]]


## C. Types of Cloud Computing

![[Pasted image 20250209120436.png]]

Note: 
- **SaaS** - all you need to do is you use the app. 
- **PaaS** - all you need todo is to give the code and don't worry about configuring or understanding the hardware or OS. The service provider will do the rest.
- **IaaS** - You don't need to worry about the IT staff, data centers, and hardware. you all need todo is configuration of the software. 



## D. Cloud Computing Deployment Models

![[Pasted image 20250209121704.png]]

![[Pasted image 20250209122945.png]]
##### Public Cloud
- a type of cloud computing where a cloud services (servers, storage, applications) are provide over the internet by a third-party provider (like AWS, Azure, GCP)
- The services are share among multiple customers

##### Private Cloud
- is a type of cloud computing where the services is exclusively use by a single organization.
- Unlike public cloud that the resources are shared among multiple customers, a Private cloud is dedicated its resources into a only to one company. 
- either hosted on-premises (in the company's data centers)


##### Hybrid Cloud
- Mix of both public and private clouds, allowing the data and applications move between them.
- It combines the benefits of both models, offering flexibility, scalability, and security.


##### Cross Clouds
- The idea of this is the organization uses multiple CSPs (AWS, Azure, GCP) to run different workloads.
- Unlike hybrid that combines both private and public cloud, the Cross cloud is uses multiple public clouds for different vendors.
- Example service is the Azure arc (that is on the picture above), Athos.



## E. Deployment Model Use Cases

![[Pasted image 20250209124030.png]]
