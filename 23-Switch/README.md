# Network Switch — Easy English Notes

## 1. What is a Network Switch?

A **network switch** is a device that connects multiple devices together inside a network, usually a **LAN**.

Examples of devices connected to a switch:

* PCs
* Laptops
* Servers
* Printers
* Access points
* Routers
* Other switches

### Simple definition

> **Switch = connects devices inside a network and forwards data to the correct device.**

Example:

```text
PC1 ──┐
PC2 ──┤
PC3 ──┤── Switch
PC4 ──┘
```

The switch allows these devices to communicate with each other.

---

# 2. Switch vs Router

The main difference is:

> **Switch = connects devices/networks inside a LAN**
>
> **Router = connects different networks**

Example:

```text
Internet
   |
 Router
   |
 Switch
 ┌─┼────┬────┐
PC1 PC2 PC3  PC4
```

### Router

A router decides **which network/path** a packet should use.

Example:

```text
LAN 1 ── Router ── LAN 2
```

### Switch

A switch connects devices within the same network.

```text
PC1 ──┐
PC2 ──┤
PC3 ──┤── Switch
PC4 ──┘
```

### Easy memory

**Router → Network to Network**

**Switch → Device to Device**

---

# 3. What is a LAN?

**LAN = Local Area Network**

It is a group of devices connected within a small geographical area.

Examples:

* Home network
* School network
* University network
* Office network
* Computer lab

Example:

```text
PC1
 |
PC2 ── Switch ── Router ── Internet
 |
PC3
```

The PCs and switch form part of the LAN.

---

# 4. What is Ethernet?

**Ethernet** is a technology used to send data between devices using a physical network cable.

Example:

```text
PC ───── Ethernet cable ───── Switch
```

The cable normally uses an **RJ-45 Ethernet connector**.

### Easy definition

> **Ethernet = wired network communication.**

Wi-Fi is wireless, while Ethernet normally uses a cable.

---

# 5. How Does a Switch Forward Data?

A Layer 2 switch mainly uses **MAC addresses** to decide where to send Ethernet frames.

Example:

```text
PC1 ── Port 1
PC2 ── Port 2
PC3 ── Port 3
```

If PC1 wants to send data to PC3:

```text
PC1 → Switch → PC3
```

The switch checks the destination MAC address and sends the frame through **Port 3**.

It does not normally send the frame to every port when it already knows where the destination is.

---

# 6. What is a MAC Address?

**MAC = Media Access Control**

A MAC address is an identifier associated with a network interface.

Example:

```text
00:1A:2B:3C:4D:5E
```

A switch uses MAC addresses to identify devices at **Layer 2**.

### Easy definition

> **MAC address = Layer 2 device/interface identifier.**

---

# 7. MAC Address vs IP Address

This is very important.

| MAC Address                    | IP Address                              |
| ------------------------------ | --------------------------------------- |
| Layer 2                        | Layer 3                                 |
| Used by switches               | Used by routers                         |
| Used inside the local network  | Used for communication between networks |
| Identifies a network interface | Identifies a network-layer endpoint     |
| Example: `00:1A:2B:3C:4D:5E`   | Example: `192.168.1.10`                 |

### Easy memory

> **MAC → Switch → Layer 2**

> **IP → Router → Layer 3**

---

# 8. What is a CAM Table?

A Layer 2 switch keeps a table that maps:

```text
MAC address → Switch port
```

This table is commonly called a **CAM table**.

**CAM = Content Addressable Memory**

Example:

| MAC Address       | Port |
| ----------------- | ---- |
| AA:AA:AA:AA:AA:AA | 1    |
| BB:BB:BB:BB:BB:BB | 2    |
| CC:CC:CC:CC:CC:CC | 3    |

The switch now knows:

```text
MAC AA → Port 1
MAC BB → Port 2
MAC CC → Port 3
```

So if the switch receives a frame destined for MAC `BB:BB:BB:BB:BB:BB`, it sends it to **Port 2**.

---

# 9. How Does a Switch Learn MAC Addresses?

A switch learns MAC addresses automatically.

Suppose:

```text
PC1 ── Port 1
PC2 ── Port 2
PC3 ── Port 3
```

PC1 sends a frame.

The frame enters the switch through **Port 1**.

The switch looks at the **source MAC address**.

It learns:

```text
PC1 MAC → Port 1
```

The switch adds this information to its MAC/CAM table.

---

# 10. Important Rule: Switch Learns from Source MAC

Remember this:

> **Switch learns from SOURCE MAC.**

When a frame enters the switch:

```text
Source MAC → learn it
Destination MAC → look it up
```

### Easy memory

**Source = Learn**

**Destination = Forward**

This is one of the most important switch concepts.

---

# 11. What is Flooding?

**Flooding** means sending a frame out of multiple ports.

Suppose the switch does **not know** where the destination MAC address is.

Example:

```text
PC1 → Switch → ??? destination
```

The switch sends the frame out the other appropriate ports.

```text
          ┌── PC2
          |
PC1 → Switch ── PC3
          |
          └── PC4
```

This is called **flooding**.

The switch normally does **not** send it back out the port where the frame arrived.

---

# 12. Unknown Unicast

If the switch knows the destination MAC:

```text
PC1 → Switch → PC3
```

It sends the frame only toward PC3.

If it does not know the destination MAC:

```text
PC1 → Switch → Unknown destination
```

It floods the frame out the other ports in the VLAN.

This is called an **unknown unicast**.

---

# 13. What Happens When a Switch Starts?

When a switch is powered on, its dynamic MAC table is initially empty.

Example:

```text
MAC Address     Port
------------    ----
?               ?
?               ?
?               ?
```

Then devices start sending frames.

The switch learns:

```text
PC1 MAC → Port 1
PC2 MAC → Port 2
PC3 MAC → Port 3
```

The table becomes:

```text
MAC Address     Port
------------    ----
PC1 MAC         1
PC2 MAC         2
PC3 MAC         3
```

If the switch loses its dynamic MAC table, it must learn the addresses again.

---

# 14. Layer 2 Switch

A **Layer 2 switch** operates mainly at **OSI Layer 2 — Data Link Layer**.

It uses:

> **MAC addresses**

to forward Ethernet frames.

Example:

```text
PC1 ── Switch ── PC2
       Layer 2
```

Most traditional access switches are Layer 2 switches.

---

# 15. Layer 3 Switch

A **Layer 3 switch** can perform Layer 3 routing functions.

It can use:

> **IP addresses**

to forward traffic between different IP networks.

Example:

```text
VLAN 10 ──┐
          │
      L3 Switch
          │
VLAN 20 ──┘
```

A Layer 3 switch can route between VLANs.

### Easy memory

```text
Layer 2 Switch → MAC
Layer 3 Switch → IP
```

Some switches support both Layer 2 switching and Layer 3 routing.

---

# 16. Switch vs Layer 3 Switch

| Feature            | Layer 2 Switch  | Layer 3 Switch                           |
| ------------------ | --------------- | ---------------------------------------- |
| Main layer         | Layer 2         | Layer 3                                  |
| Uses               | MAC addresses   | MAC + IP addresses                       |
| Switching          | Yes             | Yes                                      |
| Routing            | Usually no      | Yes                                      |
| Inter-VLAN routing | Usually no      | Yes                                      |
| Common use         | Connect devices | Connect devices + route between networks |

---

# 17. What is an Unmanaged Switch?

An **unmanaged switch** is a simple switch.

You normally just connect cables and use it.

Example:

```text
PC1 ──┐
PC2 ──┤
PC3 ──┤── Unmanaged Switch
PC4 ──┘
```

It usually does not provide advanced configuration features.

### Easy definition

> **Unmanaged switch = plug-and-play switch with little configuration.**

---

# 18. What is a Managed Switch?

A **managed switch** can be configured by a network administrator.

It provides many features such as:

* VLANs
* Trunking
* STP
* Port security
* EtherChannel/LACP
* QoS
* SNMP
* Spanning-tree configuration
* Monitoring
* Security features

Example:

```text
Administrator
      |
   Managed
   Switch
      |
 ┌────┼────┐
PC1  PC2  Server
```

### Easy definition

> **Managed switch = configurable switch used for network control and management.**

---

# 19. Unmanaged vs Managed Switch

| Unmanaged               | Managed                      |
| ----------------------- | ---------------------------- |
| Simple                  | Advanced                     |
| Little/no configuration | Configurable                 |
| Plug and play           | Administrator controlled     |
| Small networks          | Business/enterprise networks |
| Limited features        | VLAN, STP, security, etc.    |

### Easy memory

> **Unmanaged = Plug and Play**

> **Managed = Configure and Control**

---

# 20. What is a VLAN?

**VLAN = Virtual Local Area Network**

A VLAN divides one physical switch into separate logical networks.

Example:

```text
             Switch
        ┌──────┼──────┐
        │      │      │
     VLAN 10 VLAN 20 VLAN 30
       HR      IT    Guest
```

Even though the devices may use the same physical switch, VLANs separate them logically.

### Easy definition

> **VLAN = logically separates devices into different networks on a switch.**

---

# 21. What is a Trunk Port?

A **trunk port** carries traffic for multiple VLANs.

Example:

```text
Switch 1 ================= Switch 2
             Trunk
          VLAN 10,20,30
```

A trunk is commonly used between:

* Switch ↔ Switch
* Switch ↔ Router
* Switch ↔ Layer 3 switch
* Switch ↔ Access Point

### Easy memory

> **Access port = usually one VLAN**

> **Trunk port = multiple VLANs**

---

# 22. Why Do Large Networks Need Switches?

Imagine an office with 100 computers.

Connecting every computer directly to the router would be impractical.

Instead:

```text
                  Router
                    |
                 Switch
          ┌─────────┼─────────┐
         PC1       PC2       PC3
          |
        ... many devices
```

Switches provide many Ethernet ports and organize device connectivity.

Large networks can use many switches:

```text
                 Router
                   |
             Core Switch
              /        \
       Switch 1        Switch 2
       /  |  \         / |  \
     PC1 PC2 PC3     PC4 PC5 PC6
```

---

# 23. Switch and Broadcast

A switch handles **broadcast frames** differently from known unicast traffic.

Example:

```text
PC1 → Broadcast
```

The switch normally floods the broadcast within the same VLAN.

```text
           ┌── PC2
           |
PC1 → Switch ── PC3
           |
           └── PC4
```

A router normally separates broadcast domains.

---

# 24. Collision Domain

A switch creates a separate collision domain for each switch port.

Example:

```text
PC1 ── Port 1
PC2 ── Port 2
PC3 ── Port 3
```

Each port is a separate collision domain.

With modern full-duplex Ethernet, collisions are normally not an issue.

### Easy definition

> **Collision domain = area where Ethernet collisions can occur.**

---

# 25. Broadcast Domain

A broadcast domain is the group of devices that can receive the same Layer 2 broadcast.

Without VLANs, devices in the same switched LAN can belong to the same broadcast domain.

VLANs can divide the broadcast domain:

```text
VLAN 10 → Broadcast Domain 1
VLAN 20 → Broadcast Domain 2
VLAN 30 → Broadcast Domain 3
```

### Easy memory

> **VLAN = separates broadcast domains.**

---

# 26. Why Does STP Matter on Switches?

**STP = Spanning Tree Protocol**

Switches can have redundant links for backup.

Example:

```text
Switch 1 -------- Switch 2
    \              /
     \            /
      Switch 3
```

This provides redundancy, but it can create a Layer 2 loop.

STP prevents the loop by placing some redundant ports into a blocking/discarding state.

### Easy definition

> **STP = prevents Layer 2 switching loops.**

---

# 27. Important Switch Terms

| Term             | Easy meaning                          |
| ---------------- | ------------------------------------- |
| Switch           | Connects devices                      |
| MAC address      | Layer 2 address                       |
| CAM table        | MAC-to-port table                     |
| Layer 2          | MAC-based switching                   |
| Layer 3          | IP-based routing                      |
| VLAN             | Logical network separation            |
| Trunk            | Carries multiple VLANs                |
| Access port      | Usually carries one VLAN              |
| Managed switch   | Configurable switch                   |
| Unmanaged switch | Simple plug-and-play switch           |
| Flooding         | Send frame out multiple ports         |
| STP              | Prevents Layer 2 loops                |
| Broadcast domain | Devices receiving a Layer 2 broadcast |
| Collision domain | Area where collisions can occur       |

---

# 28. Simple Packet Flow

Suppose PC1 wants to communicate with PC2.

```text
PC1
 |
 | Ethernet frame
 v
Switch
 |
 | checks destination MAC
 v
PC2
```

The switch:

1. Receives the frame.
2. Reads the source MAC.
3. Learns the source MAC and incoming port.
4. Reads the destination MAC.
5. Checks its CAM table.
6. Finds the destination port.
7. Forwards the frame through that port.

### Remember

```text
SOURCE MAC      → LEARN
DESTINATION MAC → FORWARD
```

---

# 29. Switch vs Router vs Modem

| Device | Main job                                            |
| ------ | --------------------------------------------------- |
| Switch | Connects devices in a LAN                           |
| Router | Connects different networks                         |
| Modem  | Connects your network to an ISP's access technology |

Simple picture:

```text
Internet
   |
 Modem
   |
 Router
   |
 Switch
 ┌─┼──┬──┐
PC1 PC2 PC3 PC4
```

---

# 30. Easy Real-World Example

Imagine a university network.

```text
                  Internet
                     |
                  Router
                     |
                Core Switch
                /         \
         Building 1      Building 2
             |               |
          Switch            Switch
         /  |  \           / |  \
       PC  PC  AP         PC PC Server
```

The switches connect many devices.

VLANs can separate departments:

```text
VLAN 10 → Students
VLAN 20 → Staff
VLAN 30 → Administration
VLAN 40 → Guest
```

STP can help prevent Layer 2 loops.

Port security can help control which devices can use certain ports.

---

# 31. Important Cisco Switch Commands

### Show MAC address table

```text
show mac address-table
```

Shows MAC addresses learned by the switch.

### Show interfaces

```text
show interfaces
```

Shows detailed interface information.

### Show interface status

```text
show interfaces status
```

Shows a quick summary of switch ports.

### Show VLANs

```text
show vlan brief
```

Shows VLAN information.

### Show trunk ports

```text
show interfaces trunk
```

Shows trunk information.

### Show spanning tree

```text
show spanning-tree
```

Shows STP information.

---

# 32. Easy Memory

Remember these four relationships:

```text
SWITCH
   ↓
MAC address
   ↓
Layer 2
   ↓
CAM table
```

And:

```text
ROUTER
   ↓
IP address
   ↓
Layer 3
   ↓
Routing table
```

---

# 33. Most Important Things to Remember

1. **Switch connects devices in a LAN.**
2. **Layer 2 switches use MAC addresses.**
3. **Layer 3 switches can use IP addresses for routing.**
4. **CAM table maps MAC addresses to switch ports.**
5. **Switch learns from the source MAC address.**
6. **Switch uses the destination MAC address to decide where to forward.**
7. **Unknown destination MAC → flooding.**
8. **Managed switches can be configured.**
9. **Unmanaged switches are simple plug-and-play devices.**
10. **VLANs separate a switch into logical networks.**
11. **Trunks carry traffic for multiple VLANs.**
12. **STP prevents Layer 2 loops.**

---

# 34. One-Line Exam Definitions

**Network switch:**

> A device that connects devices in a LAN and forwards Ethernet frames to the correct port.

**Layer 2 switch:**

> A switch that forwards frames using MAC addresses.

**Layer 3 switch:**

> A switch that can perform Layer 3 routing using IP addresses.

**CAM table:**

> A table that maps MAC addresses to switch ports.

**MAC address:**

> A Layer 2 identifier used to identify a network interface.

**Flooding:**

> Sending a frame out multiple ports when the destination is unknown or when the frame is broadcast.

**Managed switch:**

> A configurable switch that provides advanced network management features.

**Unmanaged switch:**

> A simple plug-and-play switch with little configuration.

**VLAN:**

> A logical separation of a LAN into different networks.

**Trunk:**

> A link that carries traffic for multiple VLANs.

**STP:**

> A protocol that prevents Layer 2 loops.

---

# 35. Final Picture

```text
                         INTERNET
                            |
                         ROUTER
                       Layer 3
                            |
                       L3 SWITCH
                    Layer 3 + Layer 2
                            |
                     MANAGED SWITCH
                         Layer 2
                            |
              ┌─────────────┼─────────────┐
              |             |             |
            PC1            PC2           PC3
           VLAN 10        VLAN 20       VLAN 30
```

### The easiest way to remember everything:

```text
ROUTER  → connects NETWORKS
SWITCH  → connects DEVICES
MAC     → Layer 2
IP      → Layer 3
CAM     → MAC → PORT
VLAN    → separates NETWORKS
TRUNK   → carries MULTIPLE VLANs
STP     → prevents LOOPS
```

---

# 36. Screenshot Placeholders

### Screenshot 1 — Switch topology

```text
[Add screenshot here]
```

### Screenshot 2 — MAC address table

```text
[Add screenshot here]
```

### Screenshot 3 — VLAN configuration

```text
[Add screenshot here]
```

### Screenshot 4 — Trunk configuration

```text
[Add screenshot here]
```

### Screenshot 5 — STP

```text
[Add screenshot here]
```
