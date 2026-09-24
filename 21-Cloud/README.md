# Cloud Networking

## 1. What is Cloud Networking?

Cloud networking is the use of **cloud-based and virtual network resources** to connect users, applications, servers, and other resources.

In traditional networking, a company may need to buy and manage physical:

- Routers
- Switches
- Firewalls
- Servers
- WAN links
- Data center equipment

This can be expensive and difficult to maintain.

With cloud networking, many of these resources can be created and managed using **software** through a cloud provider such as AWS, Microsoft Azure, or Google Cloud.

### Simple idea

Traditional Network:

    Office
       |
    Router
       |
    Firewall
       |
    WAN
       |
    Company Data Center
       |
    Servers

Cloud Network:

    Office
       |
    Internet
       |
    VPN / Gateway
       |
    Cloud Virtual Network
       |
    Cloud Servers
       |
    Applications

The physical hardware still exists, but the cloud provider manages much of the physical infrastructure.

> **Cloud networking = networking using virtual resources managed through a cloud platform.**

---

## 2. Types of Cloud Networking

There are four main types:

1. Public Cloud
2. Private Cloud
3. Hybrid Cloud
4. Multi-Cloud

---

## 3. Public Cloud

A **public cloud** is cloud infrastructure owned and operated by a cloud provider.

Examples:

- AWS
- Microsoft Azure
- Google Cloud

Multiple customers can use the provider's physical infrastructure, while their virtual resources are logically isolated.

### Advantages

- Easy to start
- No need to buy physical infrastructure
- Easy to scale
- Resources can be created quickly

### Simple example

    Cloud Provider
          |
    +-----+-----+
    |     |     |
   Org A Org B Org C

The physical infrastructure is shared, but each organization has logically isolated resources.

### Important terms

**Elasticity** = ability to increase or decrease resources when needed.

**Provisioning** = creating and preparing resources for use.

---

## 4. Private Cloud

A **private cloud** is a cloud environment dedicated to one organization.

It can run:

- In the organization's own data center
- On dedicated infrastructure managed by a cloud provider

### Example

    Organization
         |
    Private Cloud
         |
    Virtual Network
      /     \
   Server   Database

### Advantages

- More control
- Strong network isolation
- More control over sensitive data
- Custom security policies

> **Private cloud = cloud environment dedicated to one organization.**

---

## 5. Hybrid Cloud

A **hybrid cloud** combines on-premises infrastructure with cloud infrastructure.

### Example

    Company Office
          |
    On-Premises Network
          |
        Router
          |
       Internet
          |
        VPN
          |
    Cloud Network
          |
       Servers

A company may keep some applications and servers on-premises while moving other applications to the cloud.

### Why use hybrid cloud?

A company may already have physical infrastructure and may not want to move everything to the cloud at once.

> **Hybrid cloud = on-premises + cloud.**

---

## 6. Multi-Cloud Networking

**Multi-cloud** means using more than one cloud provider.

### Example

    Company
      |
      +-------- AWS
      |
      +-------- Azure
      |
      +-------- Google Cloud

A company may use different cloud providers for different applications or requirements.

### Advantage

- More flexibility
- Can use services from different providers
- Can distribute workloads across different clouds

### Challenge

The organization must manage connectivity and traffic between different cloud platforms.

> **Multi-cloud = multiple cloud providers.**

---

# 7. Cloud Networking Benefits

The main benefits are:

1. Efficient network management
2. Increased scalability
3. Easier security
4. Better monitoring and maintenance
5. Better network performance
6. Hybrid and multi-cloud support

---

## 8. Efficient Network Management

Traditional networking often requires physical equipment.

For example:

    Buy Router
        ↓
    Install Router
        ↓
    Configure Router
        ↓
    Maintain Router
        ↓
    Replace Router

Cloud networking allows administrators to create and change many network resources using software.

For example:

    Cloud Console
         ↓
    Create Virtual Network
         ↓
    Create Subnet
         ↓
    Create Route
         ↓
    Create Gateway

### Important terms

**Streamlined** = made simpler and more efficient.

**Overhead** = extra cost, work, or resources needed to operate something.

---

## 9. Increased Scalability

**Scalability** is the ability to increase or decrease resources according to demand.

### Traditional networking

Adding a new branch may require:

- Router
- Switch
- Firewall
- Cables
- WAN connection
- Installation
- Configuration

This can take a long time.

### Cloud networking

Many resources can be created and configured through software.

    Create Network
         ↓
    Create Subnet
         ↓
    Create VPN
         ↓
    Configure Routing
         ↓
    Connect Branch

### Important terms

**Scale up** = increase resources.

**Scale down** = decrease resources.

**Decommission** = remove a resource from service because it is no longer needed.

---

## 10. Easier Security

Cloud networking allows organizations to create virtual security controls.

Examples:

- Firewalls
- Security rules
- Network segmentation
- Access controls
- Encryption
- Monitoring

Example:

    Internet
       |
    Firewall
       |
    Public Subnet
       |
    Application
       |
    Private Subnet
       |
    Database

Cloud providers also protect the underlying physical infrastructure.

However, cloud networking is not automatically secure. Administrators still need to configure security correctly.

> **Cloud security is a shared responsibility between the cloud provider and the customer.**

---

## 11. Improved Monitoring and Maintenance

Cloud networking allows administrators to monitor networks using software tools.

They can monitor:

- Network traffic
- Connections
- Errors
- Resource usage
- Network performance
- Logs

Example:

    Cloud Monitoring
          |
    +-----+-----+
    |     |     |
  Traffic Errors Logs

### Monitoring

**Monitoring = continuously checking a system to understand what is happening.**

Cloud networking also reduces the need to physically maintain network equipment.

---

# 12. Network Performance

Cloud networking can improve performance by managing how traffic travels between:

- Users
- Applications
- Servers
- Databases
- Other resources

Cloud platforms can dynamically route traffic.

This can help reduce:

- Latency
- Congestion
- Server overload

---

## 13. Latency

**Latency = the delay experienced when data travels from one point to another.**

Example:

    User
      |
      | Long distance
      |
      ↓
    Server

Longer physical distances can increase latency.

Using cloud resources closer to users can help reduce latency.

---

# 14. Load Balancing

A **load balancer** distributes network or application traffic across multiple servers.

### Without Load Balancing

    Users
      |
      ↓
    Server 1

Server 1 may become overloaded.

### With Load Balancing

                  Server 1
                 /
    Users → Load Balancer → Server 2
                 \
                  Server 3

The load balancer distributes requests among the servers.

### Example

    900 requests
          |
    Load Balancer
       /   |   \
     300  300  300
      |    |    |
     S1   S2   S3

This can improve performance and availability.

---

# 15. Hybrid and Multi-Cloud Support

Cloud networking can connect:

- On-premises networks
- Public clouds
- Private clouds
- Multiple cloud providers

Example:

    On-Premises
         |
        VPN
         |
       Cloud
       /    \
     AWS    Azure

This allows organizations to use different environments without completely redesigning their network.

---

# 16. How Does Cloud Networking Work?

Traditional networking may look like:

    Office
      |
    Router
      |
    WAN
      |
    Data Center
      |
    Physical Servers

Cloud networking can look like:

    Office
      |
    Internet
      |
    VPN
      |
    Cloud Gateway
      |
    Virtual Network
      |
    Cloud Servers

The cloud provider owns and manages the underlying physical infrastructure.

The customer creates and manages virtual network resources using software.

> **Cloud networking is still networking, but many network resources are virtual.**

---

# 17. Virtualization

**Virtualization = using software to create virtual versions of physical resources.**

Examples:

- Virtual routers
- Virtual firewalls
- Virtual switches
- Virtual load balancers
- Virtual servers
- Virtual networks

Example:

    Physical Infrastructure
             |
       Virtualization
             |
       +-----+-----+
       |     |     |
    Router Firewall Load
    Virtual Virtual Balancer

Multiple virtual resources can use the same underlying physical infrastructure while remaining logically separated.

---

# 18. Virtual Private Cloud (VPC)

A **VPC (Virtual Private Cloud)** is a logically isolated virtual network inside a cloud provider.

You can think of a VPC as:

> **Your own virtual data center in the cloud.**

Example:

    AWS
     |
    VPC: 10.0.0.0/16
     |
    +------------------+
    |                  |
    ↓                  ↓
    Subnet 1           Subnet 2
    10.0.1.0/24        10.0.2.0/24
    |                  |
    Servers            Database

Inside a VPC, you can create:

- Subnets
- Route tables
- Gateways
- Security controls
- Virtual servers
- Other cloud resources

---

# 19. VPC and Subnets

A VPC can be divided into smaller networks called **subnets**.

Example:

    VPC
    10.0.0.0/16
         |
    +----+----+
    |         |
    ↓         ↓
    Subnet A  Subnet B
    10.0.1.0  10.0.2.0
    /24       /24

This is similar to traditional IP subnetting.

### Important

**VPC = large virtual network**

**Subnet = smaller network inside the VPC**

---

# 20. Availability Zone

An **Availability Zone (AZ)** is an isolated location within a cloud region.

Example:

    AWS Region
         |
    +----+----+----+
    |         |   |
   AZ-A      AZ-B AZ-C

You can place resources in different Availability Zones.

Example:

    VPC
     |
    +-----------+
    |           |
    AZ-A       AZ-B
     |           |
    Server 1    Server 2

Using multiple Availability Zones can help improve availability.

---

# 21. Region

A **Region** is a geographic area containing multiple Availability Zones.

Example:

    AWS Region
       |
    +--+--+--+
    |  |  |  |
   AZ-A AZ-B AZ-C

Organizations choose regions based on factors such as:

- User location
- Latency
- Cost
- Compliance
- Availability

---

# 22. VPC Isolation

VPCs are logically isolated from other VPCs.

Example:

    VPC A                  VPC B
    10.0.0.0/16            172.16.0.0/16
       |                       |
    Servers                  Servers

They do not automatically communicate with each other.

Network connectivity must be configured when communication is required.

---

# 23. VPN in Cloud Networking

**VPN = Virtual Private Network**

A VPN creates a secure connection over a network such as the Internet.

Example:

    Company Office
          |
       Router
          |
      Internet
          |
         VPN
          |
    Cloud Gateway
          |
         VPC

This allows an organization to securely connect its on-premises network to cloud resources.

---

# 24. Gateway

A **gateway** provides a path between different networks.

Example:

    Office Network
          |
        Router
          |
      Internet
          |
    Cloud Gateway
          |
         VPC

Think of a gateway as a **connection point between networks**.

---

# 25. Cloud Networking vs Cloud Computing

Cloud networking is one part of cloud computing.

### Cloud Computing

Cloud computing provides services such as:

- Compute
- Storage
- Databases
- Networking
- Applications
- Serverless services

### Cloud Networking

Cloud networking focuses on:

- Virtual networks
- Subnets
- Routing
- VPN
- Gateways
- Firewalls
- Load balancing
- Network connectivity

### Simple relationship

    Cloud Computing
          |
    +-----+------+---------+
    |            |         |
  Compute      Storage   Networking
    |                      |
  Servers                  VPC
                          Subnet
                          Routing
                          VPN
                          Firewall

> **Cloud networking is a part of cloud computing.**

---

# 26. On-Premises

**On-premises** means infrastructure that is located and managed at the organization's own facility or data center.

Example:

    Company Data Center
          |
    +-----+-----+
    |     |     |
  Router Switch Server

Cloud:

    Cloud Provider
          |
    Virtual Resources
          |
    Servers / Networks

---

# 27. Challenges of Cloud Networking

The main challenges are:

1. Vendor lock-in
2. Limited control
3. Latency

---

# 28. Vendor Lock-In

**Vendor lock-in** means becoming highly dependent on one cloud provider, making it difficult or expensive to move to another provider.

Example:

    Company
       |
      AWS
       |
    AWS-specific
    services
       |
    Migration to Azure
       |
    Difficult / Expensive

A company should consider interoperability and portability when designing its cloud network.

### Important terms

**Interoperability** = ability of different systems to work together.

**Vendor lock-in** = difficulty moving from one provider to another.

---

# 29. Limited Control

In a traditional network, an administrator may have direct control over physical equipment.

Example:

    Cisco Router
         |
    Administrator
         |
    Full device configuration

In public cloud networking:

    Customer
       |
    Virtual Network
       |
    Cloud Provider
       |
    Physical Infrastructure

The customer controls their virtual resources, but the cloud provider controls much of the underlying physical infrastructure.

> **Cloud gives you control over your virtual network, but not full control over the provider's physical network.**

---

# 30. Latency Challenges

Cloud applications can experience latency when users are far away from the cloud resources they access.

Example:

    User in Rwanda
          |
          |
      Long distance
          |
          ↓
    Cloud Server

Choosing an appropriate cloud region can help reduce network latency.

Other techniques can also help, such as:

- Traffic optimization
- Load balancing
- Content Delivery Networks (CDNs)
- Better resource placement

---

# 31. Important AWS Networking Services

AWS provides many networking services.

Some important examples are:

### Amazon VPC

Creates a logically isolated virtual network in AWS.

> **VPC = your virtual network in AWS.**

### AWS PrivateLink

Provides private connectivity to supported services without requiring traffic to be exposed through the public Internet.

> **PrivateLink = private service connectivity.**

### AWS Transit Gateway

Connects multiple VPCs, AWS accounts, and on-premises networks through a central gateway.

Example:

              Transit Gateway
              /      |      \
             /       |       \
          VPC 1    VPC 2    VPC 3
                              |
                         On-Premises

> **Transit Gateway = central connection point for multiple networks.**

### AWS App Mesh

Helps manage communication between application services.

Example:

    Service A
        |
    Service B
        |
    Service C

It is more focused on application/service communication than basic IP networking.

### Amazon VPC Lattice

Helps connect, monitor, and secure communication between application services.

---

# 32. Important Vocabulary

| Term | Easy Meaning |
|---|---|
| Cloud networking | Networking using cloud/virtual resources |
| Cloud computing | Computing services delivered through the cloud |
| Virtual | Created using software |
| Virtualization | Creating virtual resources using software |
| Infrastructure | Equipment and systems used to provide IT services |
| Public cloud | Cloud provided using a provider's shared infrastructure |
| Private cloud | Cloud dedicated to one organization |
| Hybrid cloud | On-premises + cloud |
| Multi-cloud | Using multiple cloud providers |
| VPC | Virtual private network in a cloud |
| Subnet | Smaller network inside a larger network |
| Gateway | Connection point between networks |
| VPN | Secure virtual connection over a network |
| Scalability | Ability to increase or decrease resources |
| Elasticity | Ability to automatically/quickly grow or shrink resources |
| Provisioning | Creating and preparing resources |
| Decommission | Removing a resource from service |
| Latency | Delay when data travels |
| Load balancing | Distributing traffic across servers |
| Isolation | Keeping resources separated |
| On-premises | Infrastructure located at the organization's facility |
| Vendor lock-in | Difficulty moving away from a cloud provider |
| Interoperability | Ability of different systems to work together |
| Monitoring | Watching and checking network activity |
| Traffic | Data moving through a network |
| Workload | Application or task running on IT resources |

---

# 33. Traditional Networking vs Cloud Networking

| Traditional Networking | Cloud Networking |
|---|---|
| Physical routers | Virtual routers/gateways |
| Physical switches | Virtual networking |
| Physical firewall | Virtual/cloud firewall |
| Physical servers | Cloud servers/instances |
| Physical WAN | Cloud connectivity |
| Physical data center | Cloud data center |
| Manual hardware installation | Software-based provisioning |
| Hardware scaling can be slow | Resources can scale quickly |
| Physical maintenance | Provider manages much of the infrastructure |
| Direct hardware control | Mainly virtual resource control |

---

# 34. Final Summary

Cloud networking means using **virtual network resources in a cloud environment**.

The cloud provider manages much of the physical infrastructure, while the organization manages its virtual network.

### Remember the four types:

    PUBLIC  → Cloud provider
    PRIVATE → One organization
    HYBRID  → On-premises + Cloud
    MULTI   → Multiple cloud providers

### Remember the main components:

    VPC
     |
    Subnets
     |
    Routing
     |
    Gateways
     |
    VPN
     |
    Firewalls
     |
    Load Balancers

### Remember the main benefits:

    Cloud Networking
          |
    +-----+-----+-----+-----+
    |     |     |     |     |
  Easy  Scale Security Monitor Performance
  Mgmt

### Remember the main challenges:

    Vendor Lock-In
    Limited Control
    Latency

## Key Idea

> **Cloud networking is still networking. The main difference is that many network resources are virtual and are managed through software instead of being directly managed as physical hardware.**

---

# 35. Screenshot Placeholders

## Screenshot 1 — Cloud Networking Diagram

Add your cloud networking diagram here.

`![Cloud Networking Diagram](screenshots/cloud-networking-diagram.png)`

## Screenshot 2 — Public Cloud

Add public cloud example here.

`![Public Cloud](screenshots/public-cloud.png)`

## Screenshot 3 — VPC and Subnets

Add your VPC/subnet diagram here.

`![VPC and Subnets](screenshots/vpc-subnets.png)`

## Screenshot 4 — Hybrid Cloud

Add your hybrid cloud diagram here.

`![Hybrid Cloud](screenshots/hybrid-cloud.png)`

## Screenshot 5 — AWS Networking

Add your AWS VPC/networking configuration here.

`![AWS Networking](screenshots/aws-networking.png)`