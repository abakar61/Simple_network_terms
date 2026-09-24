# What is a Router?

## 1. What is a Router?

A **router** is a network device that connects **two or more different networks**.

Its main job is to:

1. Connect different networks
2. Forward data packets between networks
3. Choose the best path for packets
4. Allow multiple devices to share an Internet connection

### Simple example

    LAN 1
    192.168.1.0/24
          |
        Router
          |
    LAN 2
    192.168.2.0/24

The router allows devices in different networks to communicate.

> **Router = connects different networks and forwards packets between them.**

---

# 2. LAN and WAN

## LAN

**LAN = Local Area Network**

A LAN is a network covering a small area such as:

- Home
- Office
- School
- Building

Example:

    PC1 ----\
    PC2 ----- Switch ---- Router
    PC3 ----/

All these devices can belong to the same LAN.

---

## WAN

**WAN = Wide Area Network**

A WAN connects networks over a large geographic area.

For example, a company may have offices in:

- Kigali
- Nairobi
- Kampala

Each office can have its own LAN.

    Kigali LAN
         |
       Router
         |
        WAN
         |
       Router
         |
    Nairobi LAN

The WAN connects the different LANs.

> **LAN = small/local network**

> **WAN = large network connecting different locations**

---

# 3. Router vs Switch

A very important difference:

### Switch

A **switch** mainly connects devices within the **same network**.

    PC1
      |
    Switch
    /   \
  PC2   PC3

The switch forwards frames between devices in the LAN.

### Router

A **router** connects **different networks**.

    Network A
        |
      Router
        |
    Network B

### Easy memory

> **Switch = connects devices**

> **Router = connects networks**

---

# 4. How Does a Router Work?

Think of a router like a **traffic controller**.

A packet needs to reach a destination.

Example:

    PC1
     |
     | Packet
     ↓
   Router
     |
     ↓
  Network B
     |
     ↓
 Destination

The router checks where the packet needs to go and decides where to send it.

---

# 5. Routing Table

A router uses a **routing table** to decide where packets should go.

A routing table contains information about:

- Destination networks
- Next hop
- Exit interface
- Route information

Example:

    Router R1

    Destination        Next Hop
    192.168.2.0/24     10.0.0.2
    192.168.3.0/24     10.0.0.6
    0.0.0.0/0          ISP

When R1 receives a packet, it checks the destination IP address and looks for a matching route.

---

# 6. Packet Forwarding

Suppose PC1 wants to communicate with a server.

    PC1
    192.168.1.10
        |
        ↓
      R1
        |
        ↓
      R2
        |
        ↓
    Server
    192.168.3.10

PC1 sends a packet toward the server.

R1 checks:

    Destination IP = 192.168.3.10

R1 looks at its routing table.

It finds a route to:

    192.168.3.0/24

Then R1 forwards the packet to the next hop.

> **Packet forwarding = sending a packet toward its destination.**

---

# 7. Router's Two Main Jobs

According to the basic definition, a router mainly does two things:

## 1. Routing

**Routing = deciding which path a packet should take.**

Example:

    Network A
       |
      R1
     /  \
    R2  R3
     \  /
      R4
       |
    Network B

The router chooses an appropriate path to Network B.

---

## 2. Forwarding

**Forwarding = actually sending the packet out through the correct interface.**

Simple difference:

    Routing
       ↓
    Decide the path

    Forwarding
       ↓
    Send the packet

> **Routing = decision**

> **Forwarding = action**

---

# 8. Router and Internet Sharing

A home router can allow many devices to share one Internet connection.

Example:

             Internet
                 |
               Modem
                 |
               Router
              /  |  \
             /   |   \
           PC   Phone Laptop

The router connects all these devices to the Internet.

Often, home routers also perform functions such as:

- NAT
- DHCP
- Firewalling
- Wi-Fi

---

# 9. Router vs Modem

A **router** and a **modem** are different devices, although many home devices combine both functions.

## Router

The router:

- Connects networks
- Forwards packets
- Manages traffic
- Can connect multiple devices

## Modem

A modem connects the customer's network to the ISP's access technology.

It converts signals as required by the access connection.

### Simple example

    Internet / ISP
          |
        Modem
          |
        Router
       /  |  \
      PC Phone Laptop

### Easy memory

> **Modem = connects to the ISP connection**

> **Router = connects and manages networks**

Many home devices are actually **modem + router in one box**.

---

# 10. What Happens if You Have Only a Router?

Suppose Bob has:

    Router
      |
    PC
    Phone
    Laptop

The router can create/connect a local network.

But without an appropriate Internet/ISP connection, the devices cannot access the Internet.

---

# 11. What Happens if You Have Only a Modem?

Suppose Alice has:

    Modem
      |
     PC

The PC may be able to connect to the ISP.

However, a typical modem by itself does not provide the same multi-device network functions as a router.

To connect multiple devices, a router is normally used.

---

# 12. Router + Modem

Carol has both:

    Internet
       |
     Modem
       |
     Router
    /  |   \
   PC Phone Laptop

Now the router can provide network connectivity to multiple devices.

---

# 13. Types of Routers

There are several types of routers.

The important types in this topic are:

1. Wireless router
2. Wired router
3. Core router
4. Edge router
5. Virtual router

---

# 14. Wireless Router

A **wireless router** provides network connectivity using Wi-Fi.

Example:

    Internet
       |
     Router
     / |  \
    /  |   \
  Phone Laptop Tablet

The router uses radio signals to communicate wirelessly with devices.

### WLAN

**WLAN = Wireless Local Area Network**

A WLAN is a LAN that uses wireless communication.

> **Wireless router = router that provides wireless network connectivity.**

---

# 15. Wired Router

A **wired router** uses physical network cables.

Example:

    Internet
       |
     Router
     / |  \
    /  |   \
   PC  PC  Server

The devices connect using Ethernet cables.

> **Wired router = router that uses physical cables for network connections.**

---

# 16. Wireless vs Wired Router

| Wireless Router | Wired Router |
|---|---|
| Uses Wi-Fi | Uses cables |
| Uses radio signals | Uses Ethernet/network cables |
| Creates/connects WLAN | Connects wired LAN devices |
| Useful for phones/laptops | Useful for wired devices |

---

# 17. Core Router

A **core router** operates in the central/core part of a large network.

It handles a large amount of traffic.

Example:

    Network A
        |
      Edge
        |
    Core Router
        |
      Core
        |
    Core Router
        |
      Edge
        |
    Network B

### Main idea

> **Core router = high-performance router used in the core of a large network.**

Core routers mainly handle traffic inside large networks.

---

# 18. Edge Router

An **edge router** operates at the edge of a network.

It connects the organization's internal network to external networks.

Example:

    Internal Network
          |
      Core Router
          |
      Edge Router
          |
       Internet
          |
    Other Networks

An edge router can communicate with external networks.

### BGP

Edge routers commonly use **BGP (Border Gateway Protocol)** to exchange routing information with other autonomous systems.

> **Edge router = connects the organization's network to external networks.**

---

# 19. Core Router vs Edge Router

| Core Router | Edge Router |
|---|---|
| Works in the network core | Works at network edge |
| Handles internal traffic | Handles internal/external traffic |
| High-speed forwarding | External connectivity |
| Usually does not connect directly to external networks | Connects to external networks |
| Used in large networks | Often uses BGP for external routing |

---

# 20. Virtual Router

A **virtual router** is software that performs routing functions.

Instead of using a physical router:

    Physical Router

you can have:

    Virtual Router
          |
       Software
          |
    Virtual Network

Virtual routers can run in:

- Data centers
- Cloud environments
- Virtual machines
- Network simulators

This is similar to the virtual routers you use in **GNS3**.

> **Virtual router = router implemented using software.**

---

# 21. VRRP and Virtual Routers

**VRRP = Virtual Router Redundancy Protocol**

VRRP provides redundancy by allowing multiple routers to work together as a virtual router.

Example:

             Virtual IP
             192.168.1.1
                  |
            +-----+-----+
            |           |
           R1           R2
         Master       Backup

R1 can be the active/master router.

R2 can be the backup router.

If R1 fails, R2 can take over the virtual IP.

This is similar to the **VRRP lab you have practiced in GNS3**.

---

# 22. What is SSID?

**SSID = Service Set Identifier**

In simple English:

> **SSID = the name of a Wi-Fi network.**

Example:

    Wi-Fi Networks

    AUCA_WiFi
    Home_WiFi
    Campus_WiFi

When you open Wi-Fi settings on your phone, these names are SSIDs.

---

# 23. SSID Example

A wireless router broadcasts:

    SSID: Home_WiFi

Your phone sees:

    Available Wi-Fi

    Home_WiFi
    Campus_WiFi
    AUCA_WiFi

You select:

    Home_WiFi

Then enter the Wi-Fi password.

> **SSID = Wi-Fi network name.**

---

# 24. Router Security Challenges

Routers can have security problems.

The main challenges mentioned are:

1. Vulnerable firmware
2. DDoS attacks
3. Weak/default administrator credentials

---

# 25. Firmware Vulnerabilities

**Firmware** is software built into a hardware device such as a router.

It controls many of the router's functions.

Example:

    Router Hardware
          |
       Firmware
          |
    Router Functions

Like other software, firmware can contain security vulnerabilities.

Attackers may exploit these vulnerabilities.

---

# 26. Why Update Router Firmware?

Router manufacturers release updates to:

- Fix security vulnerabilities
- Fix bugs
- Improve performance
- Add features

An old, unpatched router may be easier for attackers to compromise.

> **Keep router firmware updated.**

---

# 27. DDoS Attacks

**DDoS = Distributed Denial-of-Service**

A DDoS attack sends a large amount of traffic toward a target.

Example:

    Many Devices
    /   |   |   \
   ↓    ↓   ↓    ↓
   +----+---+----+
            |
         Router
            |
         Network

The huge amount of traffic can consume resources and cause service disruption.

### Unmitigated

**Unmitigated = not controlled or reduced.**

So:

> **Unmitigated DDoS attack = DDoS traffic that has not been stopped or reduced.**

---

# 28. Administrative Credentials

Routers have administrator accounts.

Example:

    Username: admin
    Password: admin

Using default credentials is dangerous because attackers may know common default usernames and passwords.

### Good practice

Change default credentials immediately.

Example:

    Default password
          ↓
    Change password
          ↓
    Strong unique password

Also use other security controls where supported.

---

# 29. Basic Router Security

Good router security practices include:

- Change default administrator credentials
- Use strong passwords
- Update firmware
- Disable unnecessary services
- Use secure management protocols
- Restrict management access
- Monitor router activity
- Use appropriate firewall/security controls
- Protect against DDoS attacks where needed

---

# 30. Router Packet Flow

A simple packet flow:

    PC1
    192.168.1.10
       |
       ↓
     Switch
       |
       ↓
     Router R1
       |
       | Routing Table
       ↓
     Router R2
       |
       ↓
    Server
    192.168.3.10

### What happens?

1. PC1 creates a packet.
2. The packet contains a destination IP address.
3. The packet reaches R1.
4. R1 reads the destination IP.
5. R1 checks its routing table.
6. R1 selects the appropriate route.
7. R1 forwards the packet.
8. The packet eventually reaches the destination.

---

# 31. Important Router Terms

| Term | Easy Meaning |
|---|---|
| Router | Connects different networks |
| Routing | Deciding the path |
| Forwarding | Sending the packet |
| Packet | Small unit of network data |
| IP address | Address used to identify a network interface/device |
| Routing table | List of routes |
| Next hop | Next router/device on the path |
| LAN | Local/small network |
| WAN | Large network |
| Modem | Connects to an ISP access connection |
| WLAN | Wireless LAN |
| SSID | Wi-Fi network name |
| Core router | Router in the core of a large network |
| Edge router | Router at the edge of a network |
| Virtual router | Router implemented in software |
| VRRP | Provides router redundancy |
| Firmware | Software inside network hardware |
| DDoS | Attack that overwhelms a service/network with traffic |
| Credentials | Username and password used for access |

---

# 32. Router vs Switch vs Modem

| Device | Main Job |
|---|---|
| Router | Connects different networks |
| Switch | Connects devices within a network |
| Modem | Connects the local network/device to the ISP access connection |

### Easy memory

    Switch
       ↓
    Devices

    Router
       ↓
    Networks

    Modem
       ↓
    ISP connection

---

# 33. Router Types — Easy Memory

Remember:

    Wireless → Wi-Fi
    Wired    → Ethernet cables
    Core     → Network center
    Edge     → Network boundary
    Virtual  → Software

---

# 34. Real-World Example

A company has three offices:

    Kigali Office
         |
       Router
         |
        WAN
         |
       Router
         |
    Nairobi Office
         |
       Router
         |
        WAN
         |
       Router
         |
    Kampala Office

Each office can have its own LAN.

The routers connect the LANs together through the WAN.

    LAN 1 ---- Router ---- WAN ---- Router ---- LAN 2
                                      |
                                      |
                                    Router
                                      |
                                     LAN 3

This is one of the main purposes of routers.

---

# 35. Final Summary

A **router** is a network device that connects different networks and forwards packets toward their destination.

Its important functions include:

- Connecting networks
- Maintaining routing information
- Selecting routes
- Forwarding packets
- Connecting LANs to WANs
- Connecting networks to the Internet

### Main router types

    Wireless Router
    Wired Router
    Core Router
    Edge Router
    Virtual Router

### Important protocols/concepts

    IP
    Routing
    Routing Table
    BGP
    VRRP
    NAT
    VPN

### Security concerns

    Firmware Vulnerabilities
    DDoS Attacks
    Default Credentials

### Most important idea

> **A switch connects devices in a network, while a router connects different networks and forwards packets between them.**

---

# 36. Screenshot Placeholders

## Screenshot 1 — Basic Router

Add your basic router topology here.

`![Basic Router](screenshots/basic-router.png)`

## Screenshot 2 — Routing Table

Add your router routing table here.

`![Routing Table](screenshots/routing-table.png)`

## Screenshot 3 — Router and Switch

Add your router and switch topology here.

`![Router and Switch](screenshots/router-switch.png)`

## Screenshot 4 — LAN and WAN

Add your LAN/WAN topology here.

`![LAN and WAN](screenshots/lan-wan.png)`

## Screenshot 5 — VRRP

Add your VRRP topology here.

`![VRRP](screenshots/vrrp-router.png)`

## Screenshot 6 — Wireless Router

Add your wireless router configuration here.

`![Wireless Router](screenshots/wireless-router.png)`