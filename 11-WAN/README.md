# Wide Area Network (WAN) — README

## 1. What Is a Wide Area Network (WAN)?

A **Wide Area Network (WAN)** is a computer network that connects networks over a large geographical area. A WAN can connect computers, offices, branches, data centers, or other networks located in different cities, countries, or continents.

Organizations commonly use WANs to connect multiple **Local Area Networks (LANs)**. For example, a company may have one LAN in its headquarters and other LANs in different countries. A WAN allows these separate LANs to communicate with each other.

The **Internet** is also considered a WAN because it connects networks across the world.

---

## 2. What Is a Local Area Network (LAN)?

A **Local Area Network (LAN)** is a network that covers a small, localized geographical area.

Examples include:

* Home networks
* School networks
* Office networks
* Computer laboratories
* Small business networks

A LAN is normally managed by the organization or person responsible for that location. Network devices commonly used in a LAN include switches, routers, wireless access points, computers, servers, and printers.

---

## 3. WAN vs LAN

The main difference between a LAN and a WAN is their geographical coverage.

A **LAN** connects devices within a relatively small area, while a **WAN** connects networks across large geographical distances.

### LAN

* Covers a small area
* Usually managed by one organization
* Commonly uses Ethernet or Wi-Fi
* Connects local devices
* Usually has lower latency

### WAN

* Covers a large geographical area
* Can connect cities, countries, or continents
* Often uses infrastructure provided by telecommunications companies or ISPs
* Connects multiple LANs
* Can use leased lines, VPNs, MPLS, Internet connections, or SD-WAN

---

## 4. How WANs Connect LANs

A company with multiple offices can use a WAN to allow the different office networks to communicate.

Each office can have its own LAN, while the WAN provides connectivity between those LANs.

WAN communication normally involves routers because routers determine how packets should travel from one network to another.

WANs may use infrastructure that belongs to an Internet service provider or telecommunications provider because organizations generally cannot build their own physical network infrastructure across hundreds or thousands of kilometers.

---

## 5. What Is a Leased Line?

A **leased line** is a dedicated network connection rented from a telecommunications provider or ISP.

Instead of building and maintaining its own long-distance physical infrastructure, an organization can rent a dedicated connection from a provider.

A leased line can provide:

* Dedicated connectivity
* Predictable performance
* Reliable communication
* Business-to-business connectivity
* Connections between offices and data centers

The main disadvantage is that leased lines can be expensive compared with ordinary Internet connections.

---

## 6. What Is Tunneling?

**Tunneling** is a networking technique in which one packet is encapsulated inside another packet.

The original packet becomes the payload of another packet. The outer packet is then used to transport the original packet across the network.

Tunneling can be useful when traffic needs to travel through a network using a logical path that is different from the original packet's normal path.

The basic process is:

1. The original packet is created.
2. The packet is encapsulated inside another packet.
3. The encapsulated packet travels through the network.
4. The outer packet is removed at the destination.
5. The original packet is delivered.

---

## 7. What Is Encapsulation?

**Encapsulation** is the process of adding additional information, such as headers, to data as it moves through networking layers.

In tunneling, an existing network packet can be encapsulated inside another packet.

This allows the original packet to be transported using the addressing and routing information of the outer packet.

---

## 8. What Is a VPN?

**VPN** stands for **Virtual Private Network**.

A VPN creates a logical connection through another network, commonly the public Internet.

VPNs can use encryption to protect data while it travels between two endpoints.

VPNs are commonly used for:

* Connecting company branches
* Secure remote access
* Protecting data over public networks
* Connecting remote employees to company networks
* Creating secure site-to-site connections

A VPN is therefore more than simply a tunnel. A VPN commonly provides security features such as encryption and authentication.

---

## 9. Encrypted Tunneling

Not every tunnel is encrypted.

An **encrypted tunnel** protects the contents of the packets from unauthorized users who might intercept the traffic.

Encrypted tunnels are commonly associated with VPNs.

For example, **IPsec** can be used to provide encryption, authentication, and integrity for IP communications.

---

## 10. IPsec

**IPsec (Internet Protocol Security)** is a group of protocols and technologies used to secure IP communications.

IPsec can provide:

* **Confidentiality** — prevents unauthorized users from reading the data.
* **Authentication** — verifies the identity of communicating parties.
* **Integrity** — helps ensure that data has not been modified.
* **Secure communication** — protects IP traffic while it travels through an untrusted network.

IPsec is commonly used for VPN connections.

---

## 11. Tunneling Overhead

Tunneling introduces **overhead** because additional information must be added to the original packet.

Encryption can also require additional processing.

As a result, tunneling can:

* Increase packet size
* Require additional CPU resources
* Increase processing time
* Increase latency
* Reduce effective network performance

The larger packet created by encapsulation can also create problems if it exceeds the maximum size supported by a network link.

---

## 12. Fragmentation

**Fragmentation** occurs when a packet is too large to be transmitted across a particular network link and must be divided into smaller pieces.

Tunneling and encapsulation can increase the size of packets, which can contribute to fragmentation when the resulting packet exceeds the supported **MTU (Maximum Transmission Unit)**.

Fragmentation can introduce additional processing and may reduce network efficiency.

---

## 13. What Is SD-WAN?

**SD-WAN** stands for **Software-Defined Wide Area Network**.

SD-WAN is a modern WAN architecture that uses software to manage and control WAN connectivity.

Traditional WANs may depend heavily on specific hardware and dedicated connections. SD-WAN can work with multiple types of network connections and use software-based policies to determine how traffic should be handled.

SD-WAN can use connectivity such as:

* Broadband Internet
* MPLS
* 4G/LTE
* 5G
* Other Internet connections

---

## 14. Advantages of SD-WAN

SD-WAN can provide:

* Flexible WAN management
* Centralized configuration
* Better use of multiple WAN links
* Easier deployment
* Improved application traffic management
* Greater scalability
* Reduced dependence on a single WAN technology

SD-WAN is particularly useful for organizations with many branch offices.

---

## 15. Software-Defined Networking (SDN)

**Software-Defined Networking (SDN)** is a broader networking approach that uses software to control and manage network behavior.

SD-WAN is one application of software-defined networking principles specifically focused on WAN connectivity.

The basic idea is to make network management more programmable and centralized instead of relying entirely on manually configured hardware.

---

## 16. What Is WAN-as-a-Service?

**WAN-as-a-Service** is a cloud-based model for providing WAN connectivity and management.

Instead of purchasing and managing all WAN infrastructure themselves, organizations can use a provider's cloud-based WAN services.

Customers can use software-based tools to configure and manage their WAN.

WAN-as-a-Service can simplify:

* WAN deployment
* Network management
* Scaling
* Connectivity between locations
* Centralized network control

---

## 17. MPLS

**MPLS (Multiprotocol Label Switching)** is a technology commonly used in enterprise WANs.

MPLS forwards network traffic using labels. These labels help network devices determine how traffic should be forwarded through the provider's network.

MPLS has traditionally been popular for organizations that require reliable and predictable WAN connectivity.

Modern organizations may combine MPLS with Internet connections and SD-WAN.

---

## 18. WAN Infrastructure

WAN infrastructure can include many different technologies and components, such as:

* Routers
* Switches
* Leased lines
* Fiber-optic connections
* Internet connections
* MPLS
* VPNs
* IP tunnels
* Cellular connections
* SD-WAN platforms
* Telecommunications provider networks

The exact infrastructure depends on the organization's requirements, budget, geographical locations, security requirements, and performance needs.

---

## 19. Important WAN Terms

### WAN

A network that connects networks across a large geographical area.

### LAN

A network that connects devices within a relatively small geographical area.

### Leased Line

A dedicated network connection rented from a telecommunications provider.

### Tunneling

The process of encapsulating one packet inside another packet to transport it through a network.

### VPN

A virtual private network that can create secure communication through another network.

### IPsec

A set of protocols used to secure IP communications.

### Encapsulation

The process of adding additional networking information around existing data or packets.

### Overhead

Additional data or processing required to perform a networking operation.

### Fragmentation

The process of dividing a large packet into smaller pieces.

### MTU

**Maximum Transmission Unit**, the largest packet size that can normally be transmitted over a particular network link.

### SD-WAN

A software-defined approach to managing and controlling WAN connectivity.

### MPLS

A WAN technology that forwards traffic using labels.

### WAN-as-a-Service

A cloud-based model for providing and managing WAN connectivity.

---

## 20. Advantages of WANs

WANs allow organizations to:

* Connect offices in different locations
* Share resources between branches
* Access centralized applications
* Communicate between distant networks
* Connect remote employees
* Access centralized data centers
* Support international businesses
* Provide communication between geographically separated systems

---

## 21. Disadvantages of WANs

WANs can also have disadvantages:

* Higher cost than many LAN connections
* Greater latency over long distances
* Dependence on service providers
* More complex configuration
* Greater security requirements
* Potential connectivity failures
* Higher troubleshooting complexity
* Possible bandwidth limitations

---

## 22. Summary

A **Wide Area Network (WAN)** connects networks over large geographical distances. Organizations commonly use WANs to connect multiple LANs located in different offices, cities, countries, or continents.

WAN connectivity can be provided using technologies such as **leased lines, VPNs, tunneling, MPLS, Internet connections, and SD-WAN**.

A **leased line** provides a dedicated connection from a service provider. **Tunneling** encapsulates one packet inside another packet. A **VPN** can use encryption to protect tunneled traffic. **IPsec** is one of the technologies commonly used to secure IP-based VPN communication.

**SD-WAN** provides a software-defined approach to WAN management and can use multiple types of network connections. **WAN-as-a-Service** provides WAN capabilities through cloud-based services.

The most important concept to remember is:

**LAN = connects devices locally.**

**WAN = connects networks over long distances.**
