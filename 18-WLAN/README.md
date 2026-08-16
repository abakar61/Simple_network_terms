# Wireless Local Area Network (WLAN) — README

## 1. What Is a WLAN?

**WLAN** stands for **Wireless Local Area Network**.

A WLAN is a local area network that uses **wireless communication**, usually radio waves, to connect devices instead of relying entirely on physical network cables.

WLANs are commonly used in:

* Homes
* Offices
* Schools
* Universities
* Hospitals
* Factories
* Airports
* Hotels
* Public spaces

The most common example of a WLAN is a **Wi-Fi network**.

---

## 2. How Does a WLAN Work?

A WLAN transmits data using **radio waves**.

When a device sends information over a WLAN, the information is divided into smaller units called **packets**.

These packets contain information that helps network devices deliver the data to the correct destination.

Wireless devices also use **MAC (Media Access Control) addresses** to identify network interfaces.

A WLAN therefore uses wireless communication, addressing, and networking protocols to allow devices to communicate.

---

## 3. How Does a Business Benefit From a WLAN?

WLANs provide businesses with flexibility because employees can access network resources without being physically connected to network cables.

Benefits include:

* Greater employee mobility
* Increased productivity
* Easier collaboration
* Flexible workplace arrangements
* Easier device connectivity
* Reduced cabling requirements
* Easier network expansion
* Support for mobile devices
* More flexible office layouts

WLANs can be useful in offices, factories, healthcare facilities, schools, and other organizations.

---

## 4. WLAN Modes

A WLAN can generally operate in two important modes:

1. **Infrastructure mode**
2. **Ad hoc mode**

---

## 5. Infrastructure Mode

In **infrastructure mode**, wireless devices communicate through a central device called an **Access Point (AP)**.

The access point acts as a central connection point for wireless stations.

Infrastructure WLANs are the most common type of Wi-Fi network.

A wireless router used in a home or small office commonly combines several functions, including:

* Access point
* Router
* Network address translation
* DHCP server
* Internet gateway

Infrastructure mode is commonly used when multiple devices need to communicate with each other and access network or Internet resources.

---

## 6. Ad Hoc Mode

**Ad hoc** mode allows wireless devices to communicate directly with each other without requiring a traditional access point.

This provides a basic form of **peer-to-peer (P2P)** wireless communication.

An ad hoc WLAN can be created using two or more wireless devices that support the required wireless functionality.

Ad hoc networks can be useful when devices need to communicate directly and a central access point is not available.

---

## 7. Infrastructure vs Ad Hoc

### Infrastructure WLAN

* Uses an access point
* Centralized wireless communication
* Common in homes, businesses, and schools
* Can provide access to other networks and the Internet
* Easier to manage for larger networks

### Ad Hoc WLAN

* Does not require an access point
* Devices communicate directly
* Useful for simple peer-to-peer communication
* Easier for small temporary networks
* Less suitable for large enterprise networks

---

## 8. WLAN Security

Wireless networks require strong security because wireless signals travel through the air.

A wired network generally requires physical access to the network or another method of gaining access. With a WLAN, an attacker may attempt to connect from within the wireless signal's coverage area.

Therefore, WLAN security is extremely important.

Security mechanisms can include:

* Authentication
* Encryption
* Strong passwords
* Access control
* Network segmentation
* Secure wireless protocols
* Monitoring

---

## 9. MAC Address Filtering

One basic method of controlling WLAN access is **MAC address filtering**.

A network administrator can create a list of permitted MAC addresses and allow only those devices to connect.

However, MAC filtering alone is **not strong security** because MAC addresses can potentially be spoofed.

Therefore, MAC filtering should not be considered a replacement for proper wireless authentication and encryption.

---

## 10. WLAN Encryption

Encryption protects wireless traffic by converting readable information into a form that unauthorized users cannot easily understand.

Wireless security technologies have evolved over time.

### WEP

**WEP (Wired Equivalent Privacy)** was an early wireless security technology.

WEP has serious security weaknesses and should **not be used for modern WLAN security**.

### WPA

**WPA (Wi-Fi Protected Access)** was introduced as an improvement over WEP.

### WPA2

**WPA2** provided stronger security and became widely deployed.

### WPA3

**WPA3** is a newer Wi-Fi security standard that provides improved security features compared with older wireless security technologies.

For modern networks, WPA3 should generally be preferred when supported, while WPA2 remains widely deployed.

---

## 11. What Is Roaming?

**Roaming** occurs when a wireless device moves from the coverage area of one access point to another while maintaining network connectivity.

Roaming is especially important in large WLANs where multiple access points provide overlapping wireless coverage.

For example, a user can move through a building while their phone or laptop changes its connection from one access point to another.

Depending on the network configuration and application, there may sometimes be a brief interruption during the transition.

---

## 12. Access Points and Coverage

An **Access Point (AP)** provides wireless connectivity to nearby devices.

Adding multiple access points can increase the physical area covered by a WLAN.

Access points can be positioned so that their coverage areas overlap. Proper planning of channels, transmit power, and AP placement can improve wireless performance and roaming.

---

## 13. Load Management

When multiple access points are available, a WLAN can distribute wireless clients across different access points.

This can help prevent one access point from becoming overloaded while another access point has available capacity.

Wireless networks can use different techniques to improve client distribution and overall network performance.

---

## 14. What Is a Mesh Network?

A **mesh network** is a wireless network architecture in which multiple access points or nodes can communicate with one another wirelessly.

Mesh networking can provide multiple possible paths for network traffic.

This can help extend wireless coverage to areas where running physical cables to every access point may be difficult.

Mesh networks can use algorithms to determine suitable paths for forwarding traffic.

---

## 15. Advantages of Mesh Networks

Mesh networks can provide:

* Extended wireless coverage
* Flexible deployment
* Multiple communication paths
* Easier expansion
* Reduced cabling requirements in some deployments
* Better coverage in difficult environments

However, wireless mesh networks can also consume wireless capacity because some wireless traffic is used for communication between mesh nodes.

---

# WLAN Architecture

## 16. Stations

A **station (STA)** is a device that participates in a WLAN.

A station can refer to a wireless device such as:

* Laptop
* Smartphone
* Tablet
* Printer
* IoT device

An access point is also a type of WLAN station in IEEE 802.11 terminology.

---

## 17. Basic Service Set (BSS)

A **Basic Service Set (BSS)** is a group of wireless stations associated with a particular WLAN service.

In infrastructure mode, a BSS normally consists of an access point and the wireless clients associated with it.

The BSS is identified using a **BSSID (Basic Service Set Identifier)**.

---

## 18. Independent Basic Service Set (IBSS)

An **Independent Basic Service Set (IBSS)** is a BSS used for an **ad hoc WLAN**.

An IBSS allows wireless stations to communicate directly without an access point providing the normal infrastructure-mode coordination.

---

## 19. Extended Service Set (ESS)

An **Extended Service Set (ESS)** consists of multiple BSSs connected through a **distribution system**.

An ESS allows a WLAN to cover a larger area using multiple access points.

Multiple APs can provide overlapping coverage, allowing wireless clients to move between different coverage areas.

---

## 20. Distribution System

A **Distribution System (DS)** connects access points within an ESS.

The distribution system can use:

* Ethernet
* Fiber
* Other wired connections
* Wireless connections

The distribution system allows multiple access points to work together as part of a larger WLAN.

---

## 21. Wireless Distribution System (WDS)

A **Wireless Distribution System (WDS)** allows access points to communicate with each other wirelessly.

WDS can be used to extend wireless coverage without requiring a physical Ethernet connection between every access point.

Wireless mesh systems can provide similar types of wireless interconnection using their own technologies and protocols.

---

## 22. Fixed Wireless

**Fixed wireless** uses radio communication to connect locations that are relatively far apart.

Unlike typical mobile Wi-Fi usage, fixed wireless connections are generally designed for stationary locations.

Fixed wireless can be used when installing physical cables between locations is difficult or expensive.

---

## 23. Access Point

An **Access Point (AP)** is a network device that provides wireless connectivity to client devices.

The AP acts as a connection point between wireless devices and the network.

Access points can provide:

* Wireless connectivity
* Client authentication
* Wireless encryption
* Network access
* Roaming support
* Wireless management

In larger networks, multiple access points can work together to provide wider coverage.

---

## 24. Bridge

A **bridge** connects different network segments.

In wireless networking, a wireless bridge can connect a WLAN or wireless network segment to another network.

Bridging allows devices or network segments that use different physical connections to communicate at the data-link layer.

---

## 25. Endpoint

An **endpoint** is a device that uses the network.

Examples include:

* Computers
* Smartphones
* Tablets
* Printers
* Cameras
* IoT devices
* Sensors
* Gaming devices

Endpoints can connect to a WLAN through wireless interfaces.

---

# Benefits of WLAN

## 26. Extended Reach

WLANs allow users to access network resources without being physically connected to Ethernet cables.

Wireless coverage can be extended by deploying additional access points.

This allows users to work from different areas within the wireless coverage zone.

---

## 27. Device Flexibility

WLANs can support many different types of devices, including:

* Laptops
* Smartphones
* Tablets
* Printers
* IoT devices
* Cameras
* Gaming systems
* Sensors

This makes WLANs useful in environments with many mobile and wireless devices.

---

## 28. Easier Installation

A WLAN can require less physical cabling than a completely wired network.

This can:

* Reduce installation time
* Reduce cabling requirements
* Make office layouts more flexible
* Simplify adding wireless devices

However, enterprise WLANs still require infrastructure such as access points, switches, network controllers, and wired uplinks in many deployments.

---

## 29. Scalability

WLANs can be relatively easy to expand.

An organization can add additional access points or adjust the existing wireless infrastructure as the number of users increases.

Enterprise WLANs can also use centralized management systems to configure and monitor many access points.

---

## 30. Virtual Network Management

Modern WLANs can be managed through software-based management systems.

Administrators can use centralized management platforms to:

* Configure access points
* Monitor wireless clients
* Monitor network health
* Detect problems
* Manage security policies
* Analyze network performance
* Collect network information

This makes managing large WLAN deployments easier than configuring every device independently.

---

# Important WLAN Terms

### WLAN

**Wireless Local Area Network** — a local network that uses wireless communication to connect devices.

### Wi-Fi

A family of wireless networking technologies based on IEEE 802.11 standards.

### Access Point

A device that provides wireless network connectivity to client devices.

### Station

A device participating in a WLAN.

### BSS

**Basic Service Set** — a group of wireless stations associated with a WLAN service.

### IBSS

**Independent Basic Service Set** — a BSS used for an ad hoc WLAN.

### ESS

**Extended Service Set** — multiple BSSs connected through a distribution system.

### Distribution System

The system that connects access points within an ESS.

### WDS

**Wireless Distribution System** — a method for connecting access points wirelessly.

### Endpoint

A device that uses the network, such as a laptop, phone, printer, or IoT device.

### Roaming

The process of moving a wireless client from one access point to another while maintaining network connectivity.

### Mesh Network

A network in which multiple wireless nodes can communicate with one another and provide multiple possible paths.

### MAC Address

A hardware-level network identifier associated with a network interface.

### WPA

**Wi-Fi Protected Access**, a family of wireless security technologies.

### WPA2

A widely deployed wireless security standard providing stronger security than WEP and original WPA.

### WPA3

A newer Wi-Fi security standard with improved security features.

### WEP

An older wireless security protocol that is considered insecure and should not be used.

---

# Summary

A **WLAN (Wireless Local Area Network)** is a local network that uses wireless radio communication to connect devices.

WLANs are commonly based on Wi-Fi and can be deployed using **infrastructure mode** or **ad hoc mode**. Infrastructure WLANs use access points, while ad hoc WLANs allow wireless devices to communicate directly without a traditional access point.

WLAN security is important because wireless signals travel through the air. Modern WLANs should use strong authentication and encryption, with **WPA3 preferred where supported** and WPA2 still widely used. WEP should not be used because it is insecure.

Multiple access points can extend WLAN coverage and support **roaming**. Wireless mesh networks can further extend coverage by allowing wireless nodes to communicate with each other.

The major WLAN architectural concepts include **stations, BSS, IBSS, ESS, distribution systems, access points, bridges, and endpoints**.

The major benefits of WLANs include **mobility, device flexibility, easier installation, scalability, extended wireless coverage, and centralized software-based management**.

The key idea to remember is:

**WLAN = a LAN that uses wireless communication instead of relying entirely on physical cables.**
