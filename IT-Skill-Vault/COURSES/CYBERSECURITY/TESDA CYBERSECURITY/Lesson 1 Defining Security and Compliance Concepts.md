As more business data is being accessed from outside of the traditional corporate; network, security and compliance have become concerns. Organizations need to understand how they can protect their data.


### TOPIC 1: Shared Responsibility Model

The responsibility of implementing security and compliance in an organization depends on the service it utilizes:

**On-premises Hardware and Software** - the organization is 100% responsible for implementation.

**Cloud-based Services** - The responsibility is shared between customer and cloud service provider.

#### Shared Responsibility Model
- It defines which security tasks are handles by the cloud provider and which is for customers.
- When organization move to the cloud, some responsibilities are transfer to the cloud and some for customer.
![[Pasted image 20251023211806.png]]
![[Pasted image 20251023211836.png]]

![[Pasted image 20251023212142.png]]



**The responsibilities vary depending on where the workload is hosted.**

![[Pasted image 20251023212300.png]]

**Software as a Service**
- It is hosted and managed by the cloud provider.

- **Customer responsibilities:** least amount of management.
- **Cloud provider responsibilities:** managing everything except data, devices, accounts, and identities.

**Platform as a Service**
- It provides an environment for building, testing, and developing software applications. It helps you create applications without managing infrastructure 

- **Customer responsibilities:** Applications and data
- **Cloud provider responsibilities:** Hardware and operating system

**Infrastructure as a Service**
- It is the most complex cloud service, requiring the most management from the cloud customer.
- The customer uses the computing infrastructure of cloud provider

- **Customer responsibilities:** Software: operating system, network controls, applications, and data protections 
- **Cloud provider responsibilities:** Infrastructure

**On-premises Datacenters**
- The customer has the responsibility for everything from physical security to encrypting sensitive data.



### TOPIC 2: Defense in Depth Confidentiality, Integrity, Availability

![[Pasted image 20251023215405.png]]


**Layered Approach** 
- Defense in depth uses multiple layers of security instead of a single perimeter.

**Mechanisms to Slow Attacks**
- A series of mechanism are employed to slow down the progress of an attack.

**Protection at Each Layer**
- Each layer offers protection, ensuring that if one later is breached, another later will prevent unauthorized access to data.


**Example layers of security might include:**
![[Pasted image 20251023220049.png]]

- **Physical security -** limits datacenter access to authorized personnel.
- **Identity and access -** Use multifactor authentication and condition-based access.
- **Perimeter security -** Implements DDoS protection to prevent large-scale attacks.
- **Network security -** Uses network segmentation and access control.
- **Compute layer security -** Secures virtual machines by closing certain ports.
- **Application layer security -** Ensures applications are free of vulnerabilities.
- **Data layer security -** Manages access to data and use encryption for protection.