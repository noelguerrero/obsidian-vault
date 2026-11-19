## A. What is a Cloud Service Provider?
- is a company which:
	- provides multiple cloud services e.g. tens to hundreds of services.
	- those cloud services **can be chained together** to create cloud architectures.
	- those cloud services are accessible **via single unified API** e.g. AWS API
	- those cloud services utilized metered billing based on usage e.g. per second, per hour, VPCU, memory
	- those cloud services have rich monitoring built in e.g. AWS CloudTrail (Every API action is track).
	- those cloud services have an infrastructure as a service (IaaS) offering. (that means they have networking compute, storage, databases, and etc).
	- those cloud services offers automation via infrastructure as CODE (IaC)

Note: 
- **VPCU** - Virtual Processing Core Unit - it refers to virtual CPU resources.
- IaaS - Infrastructure as a Service - It is a cloud computing model where a provider delivers virtualized computing resources over the internet.

### Example of a architecture where a simple web application running on EC2
![[Pasted image 20250201215616.png]]

If company offers multiple cloud services under a single UI but do not meet most of or all of these requirements, it would be referred to as a **Cloud Platform** e.g. Twillio, HashiCorp, Databricks 

and the AWS, Azure, GCP are cloud service providers



## B. Landscape of CSPs

**this is generally broke down into tiers:**

![[Pasted image 20250203172913.png]]

**Tier-1 (Top Tier)** - Early to market, wide offering, strong synergies between services, well recognized in the industry.
- Amazon Web Services (AWS)
- Microsoft Azure
- Google Cloud Platform (GCP)
- Alibaba Cloud


**Tier-2 (Mid Tier)** - Backed by well-known tech companies, slow to innovate and turned to specialization.
- IBM Cloud 
	- they try to be top provider but didn't keep up on the big providers like AWS.
	- They specialized in AI Services
- Oracle Cloud 
	- they try to be the cheapest but there service is not that good.
- Huawei Cloud
- Tencent Cloud


**Tier-3 (Light Tier)** - Virtual Private Servers (VPS) turned to offer core IaaS offering. Simple, cost effective.
- Vultr (Vulture)
- Digital Ocean
- Akamai Connected Cloud (Linode)


**Tier-4 (Private Tier)** - Infrastructure as Service software deployed to run in an organization's own private data center
- OpenStack (Rackspace)
- Apache CloudStack
- `*Vmware vSphere`



## C. Gartner Magic Quadrant for Cloud

How do we determine who is the leader in cloud?
-> One way of indicating that is the **Gartner Magic Quadrant**.
#### Magic Quadrant (MQ)
is a series of market research reports published by IT consulting firm Gartner that rely on proprietary qualitative data analysis methods to demonstrate market trends, such as direction, maturity and participants.

![[Pasted image 20250203174758.png]]

Note: the graphics shows a diagram that summarizes all the information (this is should not be in the public).



## D. Common Cloud Services

A Cloud service provider **can have hundreds of cloud services** that are grouped into various types of services

The four most common types of cloud services (the 4 core) for Infrastructure as a Service (IaaS) would be:

- **Compute** - Imagine having a virtual computer that can run application, programs and code.

- **Networking** - Imagine having virtual network defining internet connection or network isolations between services or outbound to the internet.

- **Storage** - Imagine having a virtual hard-drive that can store files.

- **Databases** - Imagine a virtual database for storing reporting data or a database for general purpose web-applications


**Facts**: AWS has over 200+ cloud services

**Note:** The term "Cloud Computing" can be used to refer to all categories, even though it has "compute" in the name.


## E. AWS Technology Overview

#### Any Cloud Service Provider (CSP) that are Infrastructure as a Service (IaaS) will always have 4 core cloud service offerings:

1. Compute
	- EC2 virtual Machines

2. Storage
	- EBS Virtual Hard drives

3. Database
	- RDS SQL databases

4. Networking and Content Delivery (but really its Networking)
	- VPC Private Cloud Network


#### The categories outside the 4 core

1. Analytics
2. Application Integration
3. AR & VR
4. AWS Cost management
5. Blockchain
6. Business Applications
7. Containers
8. Customer Engagement
9. Developer Tools
10. End User Computing
11. Game Tech
12. Internet of Things (IoT)
13. Machine Learning
14. Management & Governance
15. Media Services
16. Migration & Transfer
17. Mobile
18. Quantum technologies
19. Robotics
20. Satellites
21. Security, Identity & Compliance
22. And more...