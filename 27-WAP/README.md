# Wireless Access Point (WAP)

## 1. What is a WAP?

**WAP = Wireless Access Point**

A WAP is a networking device that allows wireless devices to connect to a wired network using **Wi-Fi**.

### Simple definition

> **WAP = connects wireless devices to a network.**

Example:

```text
             WAP
              |
       ┌──────┼──────┐
       |      |      |
     Phone  Laptop  Tablet
```

The WAP provides the wireless connection.

---

# 2. How Does a WAP Work?

A WAP acts as a connection point between:

```text
Wireless Network
       ↕
      WAP
       ↕
 Wired Network
```

For example:

```text
                 INTERNET
                    |
                  Router
                    |
                 Ethernet
                    |
                   WAP
                /   |   \
               /    |    \
          Laptop  Phone  Tablet
```

The laptop sends wireless data to the WAP.

The WAP sends the traffic into the wired network.

When traffic comes back, the WAP sends it wirelessly to the device.

### Easy memory

> **WAP = Wireless ↔ Wired**

---

# 3. Why Use a WAP?

A WAP is useful because it allows devices to connect without Ethernet cables.

Without Wi-Fi:

```text
PC ─── Cable ─── Switch
```

With a WAP:

```text
Laptop  ))))
          ))))
           WAP ─── Switch
          ))))
         Phone
```

This provides:

* Mobility
* Easy device connection
* Less cabling
* Wider Wi-Fi coverage
* Support for many wireless devices

---

# 4. WAP vs Router

A router and a WAP are not exactly the same thing.

### Router

A router connects different IP networks.

```text
LAN ─── ROUTER ─── Internet
```

### WAP

A WAP provides wireless access to a network.

```text
                 WAP
              /   |   \
          Laptop Phone Tablet
```

### Easy memory

> **Router → connects networks**

> **WAP → provides Wi-Fi access**

---

# 5. Home Router vs Separate WAP

Many home routers already contain a built-in wireless access point.

For example:

```text
        HOME ROUTER
     ┌───────────────┐
     │ Router        │
     │ Switch        │
     │ WAP           │
     │ Firewall      │
     └───────────────┘
```

Therefore, you may not need a separate WAP in a small home.

In larger networks, separate WAPs are commonly used.

---

# 6. Why Use Multiple WAPs?

One WAP may not provide enough coverage for a large building.

Example:

```text
        Large Office

   WAP 1              WAP 2
     ))))              ((((
      |                  |
   Room A              Room B
```

Multiple WAPs can provide better coverage.

They can also help distribute wireless clients across different access points.

---

# 7. Wireless Roaming

**Roaming** means a wireless device can move from one area to another and connect to another WAP.

Example:

```text
       WAP 1                 WAP 2
      ))))))                 ((((((
          \                   /
           \                 /
             Laptop
```

You walk from Room A to Room B.

Your laptop or phone can move from:

```text
WAP 1 → WAP 2
```

without requiring you to manually connect to a completely different network.

### Important

Smooth roaming depends on proper wireless design, compatible equipment, and client behavior.

---

# 8. Root Access Point

A **root access point** is an access point connected directly to the wired network.

Example:

```text
                Switch
                  |
                  |
                 WAP
              /   |   \
             /    |    \
          Laptop Phone Tablet
```

The WAP provides wireless access to the wired LAN.

If multiple WAPs are connected to the same LAN:

```text
             Switch
           /   |    \
         WAP1 WAP2  WAP3
          ))   ))    ))
```

Wireless users can move between coverage areas.

---

# 9. Repeater Access Point

A repeater uses a wireless connection to extend coverage.

Example:

```text
Main WAP
   )))
      )))
        Repeater
           )))
              )))
               Client
```

The repeater receives wireless traffic and retransmits it.

### Why use it?

A repeater can help reach an area where the main WAP's signal is weak.

### Important

A wireless repeater can reduce available wireless capacity because it must receive and retransmit traffic, depending on the design and technology.

---

# 10. Bridge

A **wireless bridge** connects networks over a wireless link.

Example:

```text
LAN A                         LAN B

PC ─ Switch ─ Bridge ))) ((( Bridge ─ Switch ─ PC
```

The two bridges create a wireless connection between the two wired networks.

### Simple definition

> **Bridge = connects network segments using a Layer 2 link.**

---

# 11. Workgroup Bridge

A **workgroup bridge** allows wired devices to connect to a wireless network through an access point operating in a client/bridge role.

Example:

```text
PC1 ──┐
PC2 ──┤
Printer┤
       |
     Switch
       |
       |
 Workgroup Bridge
       )))
         )))
          WAP
           |
         LAN
```

This can be useful when several wired devices need wireless connectivity but running Ethernet cables to the main network is difficult.

### Easy memory

> **Workgroup Bridge = wired devices → wireless network**

---

# 12. All-Wireless Network

In some wireless networks, devices communicate through wireless access points without every access point being connected directly to Ethernet.

Example:

```text
        WAP
      /  |  \
    )))  )))  )))
   PC   Phone Laptop
```

The WAP acts as the central wireless connection point.

---

# 13. WAP and Security

A WAP should be properly secured.

Important security features include:

### WPA2 / WPA3

Wireless security protocols used to protect Wi-Fi communication.

Where supported, **WPA3** provides newer security capabilities.

### Strong Password

Use a strong Wi-Fi password.

Avoid:

```text
12345678
password
wifi123
```

### Guest Network

A guest network can separate visitors from internal network resources.

Example:

```text
                Router
                   |
                  WAP
              /        \
             /          \
      Employee Wi-Fi   Guest Wi-Fi
            |              |
        Internal LAN   Internet access
```

---

# 14. Wireless Network Segmentation

A business can separate different groups of users.

For example:

```text
                 WAP
                  |
        ┌─────────┼─────────┐
        |         |         |
      Staff     Guest      IoT
       Wi-Fi     Wi-Fi     Wi-Fi
```

These networks can be mapped to different VLANs.

Example:

```text
Staff Wi-Fi → VLAN 10
Guest Wi-Fi → VLAN 20
IoT Wi-Fi   → VLAN 30
```

This helps separate traffic and protect internal resources.

---

# 15. SSID

**SSID = Service Set Identifier**

In simple English:

> **SSID = Wi-Fi network name.**

Example:

```text
SSID: AUCA-Student-WiFi
```

When you open Wi-Fi settings on your phone, you see available SSIDs.

---

# 16. Wireless Channel

Wi-Fi uses radio channels.

Nearby Wi-Fi networks can interfere with each other when they use overlapping channels or when there is other radio interference.

Example:

```text
WAP 1 → Channel X
WAP 2 → Channel Y
```

A good wireless design chooses channels carefully.

### Goal

> Reduce interference → improve wireless performance.

---

# 17. Transmission Power

A WAP can transmit at different power levels depending on the equipment and configuration.

Higher power does not always mean better Wi-Fi.

Too much power can cause:

* More interference
* Overlapping coverage
* Poor roaming behavior

Wireless design should balance:

```text
Coverage + Capacity + Interference
```

---

# 18. WAP Placement

WAP placement is very important.

A good location is generally:

* Central
* Elevated
* Away from large obstacles
* Away from strong sources of interference

Avoid placing the WAP behind:

* Large metal objects
* Thick walls
* Large appliances
* Enclosures that block radio signals

Example:

```text
GOOD:

       WAP
        |
   ┌────┼────┐
   |    |    |
 Room Room Room
```

---

# 19. WAP Installation

A basic WAP installation looks like this:

### Step 1 — Connect the WAP

Use Ethernet:

```text
Switch ─── Ethernet ─── WAP
```

### Step 2 — Power the WAP

The WAP can use:

* Power adapter
* **PoE (Power over Ethernet)**

With PoE:

```text
Switch
  |
Ethernet + Power
  |
 WAP
```

---

# 20. Configure the WAP

Common settings include:

### SSID

```text
AUCA-WiFi
```

### Security

```text
WPA2 / WPA3
```

### Password

Use a strong password.

### Channel

Choose an appropriate channel.

### Transmission Power

Adjust according to the wireless design.

---

# 21. What is PoE?

**PoE = Power over Ethernet**

PoE allows Ethernet cable to carry:

* Data
* Electrical power

Example:

```text
PoE Switch
     |
     | Ethernet
     | Data + Power
     |
    WAP
```

This is very useful for WAP installation because you may not need a separate power cable near the WAP.

---

# 22. Troubleshooting a WAP

If a device cannot connect to Wi-Fi, check:

### 1. Power

Is the WAP turned on?

### 2. Ethernet

Is the Ethernet cable connected?

```text
Switch ─── Ethernet ─── WAP
```

### 3. SSID

Is the correct Wi-Fi network visible?

### 4. Password

Is the correct password being used?

### 5. Signal

Is the device too far from the WAP?

### 6. Interference

Are there many nearby Wi-Fi networks or other sources of interference?

### 7. IP Address

Did the device receive an IP address?

Example:

```text
192.168.10.50
```

### 8. DHCP

Is DHCP working?

### 9. VLAN

In a business network, is the WAP connected to the correct VLAN?

---

# 23. Basic WAP Troubleshooting Flow

```text
Cannot connect to Wi-Fi
          |
          ↓
     Check WAP power
          |
          ↓
     Check Ethernet
          |
          ↓
      Check SSID
          |
          ↓
     Check password
          |
          ↓
     Check signal
          |
          ↓
   Check interference
          |
          ↓
     Check DHCP/IP
          |
          ↓
      Check VLAN
```

---

# 24. WAP in a Business Network

A business may have many WAPs.

Example:

```text
                     Router
                       |
                     Switch
              _________|_________
             |         |         |
           WAP1       WAP2      WAP3
            )))        )))       )))
           /  \       /  \      /  \
        Users Users  Users     Users
```

The WAPs provide wireless access throughout the building.

In larger deployments, WAPs may be centrally managed using a wireless controller or cloud management platform.

---

# 25. WAP vs Wi-Fi Extender

These devices are different.

| Feature                  | WAP                                | Wi-Fi Extender                         |
| ------------------------ | ---------------------------------- | -------------------------------------- |
| Main purpose             | Provides Wi-Fi access              | Extends existing Wi-Fi                 |
| Typical wired connection | Yes                                | Often wireless                         |
| Performance              | Usually better with wired backhaul | Can be lower with wireless backhaul    |
| Business networks        | Common                             | Less common for primary infrastructure |
| Coverage                 | Can provide new coverage area      | Extends existing coverage              |

### Easy memory

> **WAP = creates/provides Wi-Fi from the network**

> **Extender = repeats existing Wi-Fi**

---

# 26. WAP vs Mesh

### WAP deployment

Multiple WAPs can be connected to the wired network:

```text
             Switch
          /    |    \
        WAP1 WAP2  WAP3
```

### Mesh deployment

Some mesh nodes can communicate wirelessly:

```text
Router
  |
Mesh Node 1 ))) Mesh Node 2 ))) Mesh Node 3
```

Both can provide wide wireless coverage.

---

# 27. Wi-Fi 7

Modern Wi-Fi continues to evolve.

**Wi-Fi 7** is based on the **IEEE 802.11be** standard.

It introduces newer capabilities designed to improve:

* Throughput
* Latency
* Reliability
* Multi-link operation

Wi-Fi 7 can be useful in environments with many connected devices and high traffic requirements.

### Important

A Wi-Fi 7 WAP does not automatically make every device faster.

The client device, Ethernet uplink, Internet connection, configuration, and environment also affect performance.

---

# 28. IoT and WAPs

**IoT = Internet of Things**

IoT devices include:

* Cameras
* Smart TVs
* Sensors
* Smart lights
* Smart appliances

Example:

```text
                  WAP
                   |
        ┌──────────┼──────────┐
        |          |          |
      Laptop     Camera     Sensor
```

A network can place IoT devices into a separate VLAN or SSID.

Example:

```text
Employee Wi-Fi → VLAN 10
Guest Wi-Fi    → VLAN 20
IoT Wi-Fi      → VLAN 30
```

---

# 29. Important WAP Terms

| Term             | Easy meaning                                 |
| ---------------- | -------------------------------------------- |
| WAP              | Wireless Access Point                        |
| Wi-Fi            | Wireless LAN technology                      |
| SSID             | Wi-Fi network name                           |
| Roaming          | Moving between WAP coverage areas            |
| Repeater         | Repeats wireless traffic to extend coverage  |
| Bridge           | Connects network segments                    |
| Workgroup Bridge | Connects wired devices to a wireless network |
| PoE              | Power + data over Ethernet                   |
| WPA2             | Wi-Fi security protocol                      |
| WPA3             | Newer Wi-Fi security protocol                |
| VLAN             | Separates network traffic                    |
| Guest Network    | Separate Wi-Fi for visitors                  |
| Mesh             | Multiple coordinated wireless nodes          |
| Interference     | Signals that disrupt wireless communication  |
| Channel          | Radio-frequency channel used by Wi-Fi        |

---

# 30. Complete WAP Example

```text
                         INTERNET
                             |
                           Router
                             |
                           Switch
                    _________|_________
                   |         |         |
                  WAP1      WAP2      WAP3
                 / | \      / | \      / | \
                /  |  \    /  |  \    /  |  \
             Laptop Phone PC  Phone Camera IoT
```

The switch provides wired connectivity to the WAPs.

The WAPs provide wireless connectivity to users and devices.

---

# 31. Easy Memory

Remember these:

```text
WAP
 ↓
Wireless Access Point
 ↓
Provides Wi-Fi
```

```text
ROUTER
 ↓
Connects Networks
```

```text
SWITCH
 ↓
Connects Devices
```

```text
POE
 ↓
Power + Ethernet Data
```

```text
SSID
 ↓
Wi-Fi Name
```

```text
WPA2/WPA3
 ↓
Wi-Fi Security
```

```text
VLAN
 ↓
Network Separation
```

```text
MESH
 ↓
Multiple Coordinated Wi-Fi Nodes
```

---

# 32. Final Summary

A **Wireless Access Point (WAP)** provides wireless access to a network.

The basic flow is:

```text
Wireless Device
      ↓
     Wi-Fi
      ↓
     WAP
      ↓
   Ethernet
      ↓
    Switch
      ↓
    Router
      ↓
   Internet
```

A WAP can provide:

* Wireless connectivity
* Wider coverage
* Roaming
* Multiple SSIDs
* Guest networks
* VLAN integration
* WPA2/WPA3 security
* Support for many wireless clients

### Most important definition

> **WAP = a device that connects wireless devices to a wired network using Wi-Fi.**

---

# 33. Screenshot Placeholders

### Basic WAP Topology

```text
[Add Screenshot Here]

Laptop )))
          WAP ─── Switch ─── Router ─── Internet
Phone   )))
```

### Multiple WAPs

```text
[Add Screenshot Here]

          Switch
        /   |   \
      WAP1 WAP2 WAP3
```

### WAP with PoE

```text
[Add Screenshot Here]

PoE Switch ─── Ethernet ─── WAP
              Data + Power
```

### Wireless Roaming

```text
[Add Screenshot Here]

WAP 1  )))) Laptop ((((  WAP 2
          Room 1 → Room 2
```

### VLAN-Based Wi-Fi

```text
[Add Screenshot Here]

WAP
 |
 ├── Staff Wi-Fi → VLAN 10
 ├── Guest Wi-Fi → VLAN 20
 └── IoT Wi-Fi   → VLAN 30
```
