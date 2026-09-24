# Network Hub

## 1. What is a Hub?

A **hub** is a basic networking device used to connect multiple computers and devices in a **LAN (Local Area Network)**.

A hub works mainly at **OSI Layer 1 (Physical Layer)**.

### Simple definition

> **Hub = connects devices and sends received data to all other ports.**

Example:

```text
        PC1
         |
         |
PC2 --- HUB --- PC3
         |
         |
        PC4
```

If PC1 sends data to PC3, the hub does **not** know that PC3 is the destination.

Instead, it sends the data to:

```text
PC2
PC3
PC4
```

PC3 accepts the data, while the other devices ignore it.

---

# 2. How Does a Hub Work?

A hub is a **central connection point**.

Each device connects directly to the hub.

```text
PC1 ───┐
PC2 ───┤
PC3 ───┤── HUB
PC4 ───┘
```

When the hub receives a signal:

1. The hub receives the signal.
2. It repeats the signal.
3. It sends the signal out of its other ports.
4. All connected devices receive it.
5. Only the intended device processes the data.

### Important

A hub does **not** examine:

* Destination MAC address
* Destination IP address
* Routing table
* MAC address table

It simply **repeats/broadcasts the signal** to the other ports.

---

# 3. What Does a Hub Do?

The main job of a hub is:

> **Connect multiple devices and repeat incoming signals to other ports.**

For example:

```text
PC1 → HUB → PC2
          ↘ PC3
          ↘ PC4
```

PC1 sends a signal to the hub.

The hub repeats it to PC2, PC3, and PC4.

---

# 4. Hub and Bandwidth

One important problem with hubs is that all devices share the same **collision domain** and bandwidth.

Example:

```text
             HUB
        /     |     \
      PC1    PC2    PC3
```

If PC1 and PC2 transmit at the same time, their signals can collide.

This is called a:

> **Collision**

Because of this, traditional Ethernet hubs use **CSMA/CD** to deal with collisions.

---

# 5. Collision Domain

A **collision domain** is an area where devices can experience Ethernet collisions.

With a hub:

```text
PC1 ───┐
PC2 ───┤
PC3 ───┤── HUB
PC4 ───┘

All devices = ONE collision domain
```

With a switch:

```text
PC1 ───┐
PC2 ───┤
PC3 ───┤── SWITCH
PC4 ───┘

Each switch port = separate collision domain
```

This is one reason switches are much better for modern Ethernet networks.

---

# 6. Hub vs Switch

This is one of the most important comparisons.

| Feature             | Hub                   | Switch                           |
| ------------------- | --------------------- | -------------------------------- |
| OSI Layer           | Layer 1               | Layer 2                          |
| Uses MAC addresses? | No                    | Yes                              |
| MAC address table   | No                    | Yes                              |
| Sends data          | To all other ports    | Usually only to destination port |
| Collision domains   | One shared domain     | One per port                     |
| Bandwidth           | Shared                | More efficient                   |
| Duplex              | Typically half-duplex | Full-duplex commonly supported   |
| Performance         | Lower                 | Higher                           |
| Modern networks     | Rare                  | Common                           |

### Easy memory

> **HUB → Layer 1 → Signal → Everyone**

> **SWITCH → Layer 2 → MAC → Correct port**

---

# 7. Does a Hub Have an IP Address?

Normally, **no**.

A basic hub does not need an IP address because it does not communicate with devices using IP.

It simply works at the physical layer.

```text
PC1 ─── HUB ─── PC2
```

The hub does not need:

```text
192.168.1.1
```

or another IP address to perform its basic job.

### Compare

```text
HUB
↓
No IP required

SWITCH
↓
Basic Layer 2 switching does not require an IP
Management IP can be configured

ROUTER
↓
Uses IP addresses for routing
```

---

# 8. Does a Hub Slow Down the Network?

Yes, a hub can reduce network performance.

There are several reasons:

### 1. Shared bandwidth

All devices share the same network capacity.

### 2. Collisions

Multiple devices may transmit at the same time.

### 3. Unnecessary traffic

The hub sends the signal to all other ports.

Example:

```text
PC1 → HUB

       ↓
    PC2
    PC3
    PC4
```

Even though PC3 may be the intended destination, PC2 and PC4 also receive the signal.

---

# 9. Hub and Broadcast

A hub repeats signals to all other ports.

This can look similar to broadcasting from the perspective of the connected devices, but technically a hub itself does **not understand Ethernet broadcast frames**.

It simply repeats the physical signal.

So remember:

> **Hub = repeats signals**

> **Switch = makes forwarding decisions using MAC addresses**

> **Router = makes forwarding decisions using IP addresses**

---

# 10. When Were Hubs Used?

Hubs were commonly used in older Ethernet networks.

They were attractive because they were:

* Simple
* Easy to install
* Cheap
* Easy to understand

However, switches became more popular because they provide much better performance.

---

# 11. Are Network Hubs Still Used?

Hubs are now **rare in modern Ethernet networks**.

Most networks use **switches instead**.

A switch is better because it can:

* Learn MAC addresses
* Forward frames to the correct port
* Reduce unnecessary traffic
* Provide separate collision domains
* Support full-duplex communication
* Support VLANs
* Support features such as STP, port security, and EtherChannel/LACP

Therefore:

```text
OLD NETWORK
     ↓
   HUB

MODERN NETWORK
     ↓
  SWITCH
```

---

# 12. Hub Network Example

Imagine four computers connected to a hub:

```text
                 HUB
          ┌──────┼──────┐
          │      │      │
         PC1    PC2    PC3
                 │
                PC4
```

If PC1 sends data:

```text
PC1
 ↓
HUB
 ↓
 ├── PC2
 ├── PC3
 └── PC4
```

The hub sends the signal to all other ports.

It does not ask:

> "Which port has PC3?"

It simply repeats the signal.

---

# 13. Hub vs Router vs Switch

Remember these three devices:

### Hub

```text
HUB
↓
Connects devices
↓
Layer 1
↓
Repeats signals
```

### Switch

```text
SWITCH
↓
Connects devices
↓
Layer 2
↓
Uses MAC addresses
```

### Router

```text
ROUTER
↓
Connects networks
↓
Layer 3
↓
Uses IP addresses
```

### Easy memory

> **Hub → Signal**

> **Switch → MAC**

> **Router → IP**

---

# 14. Important Hub Terms

| Term             | Easy meaning                                                    |
| ---------------- | --------------------------------------------------------------- |
| Hub              | Device that repeats signals to other ports                      |
| LAN              | Local Area Network                                              |
| Port             | Physical connection on a device                                 |
| Layer 1          | Physical layer                                                  |
| Collision        | Two devices transmit at the same time                           |
| Collision domain | Area where collisions can occur                                 |
| Bandwidth        | Network capacity                                                |
| Half-duplex      | Send or receive, but not both at the same time                  |
| Full-duplex      | Send and receive at the same time                               |
| CSMA/CD          | Method used by traditional shared Ethernet to handle collisions |
| Repeater         | Device that regenerates/repeats a signal                        |

---

# 15. Important Corrections

Some descriptions of hubs can be confusing.

### ❌ "Hub is an efficient way to share data"

Not really.

A hub is simple, but it is **less efficient than a switch** because it sends traffic to all other ports and shares one collision domain.

### ❌ "Hub prevents bottlenecks"

Not generally.

A hub creates a **shared bandwidth environment**, so many devices transmitting at the same time can reduce performance.

### ❌ "Gaming or streaming may benefit from a hub"

Generally, a modern switch is preferable for these uses. A hub does not provide a performance advantage over a switch.

### ❌ "Hub sends packets"

More precisely:

> A hub operates at Layer 1 and **repeats physical signals/bits**. It does not make Layer 2 frame-forwarding decisions.

---

# 16. Hub in the OSI Model

```text
OSI MODEL

Layer 7  Application
Layer 6  Presentation
Layer 5  Session
Layer 4  Transport
Layer 3  Network       ← Router
Layer 2  Data Link     ← Switch
Layer 1  Physical      ← HUB
```

### Memory

```text
HUB    → Layer 1 → Signal
SWITCH → Layer 2 → MAC
ROUTER → Layer 3 → IP
```

---

# 17. Final Summary

A **hub** is a basic Layer 1 networking device used to connect multiple devices.

Its main job is to:

* Receive a signal
* Repeat the signal
* Send it to the other connected ports

A hub:

* Does not learn MAC addresses
* Does not use a MAC address table
* Normally does not need an IP address
* Creates one shared collision domain
* Shares bandwidth between devices
* Can cause unnecessary traffic
* Is mostly replaced by switches today

### Most important memory

```text
HUB
 ↓
Layer 1
 ↓
Repeats signals
 ↓
All other ports
 ↓
One collision domain
```

```text
SWITCH
 ↓
Layer 2
 ↓
MAC address
 ↓
MAC address table
 ↓
Correct port
```

```text
ROUTER
 ↓
Layer 3
 ↓
IP address
 ↓
Routing table
 ↓
Different networks
```

---

# 18. Screenshot Placeholders

### Hub Topology

```text
[Add Screenshot Here]

Example:
PC1 ───┐
PC2 ───┤
PC3 ───┤── HUB
PC4 ───┘
```

### Hub Traffic

```text
[Add Screenshot Here]

PC1 → HUB → PC2
          → PC3
          → PC4
```

### Hub vs Switch

```text
[Add Screenshot Here]

HUB:
One shared collision domain

SWITCH:
Separate collision domain per port
```
