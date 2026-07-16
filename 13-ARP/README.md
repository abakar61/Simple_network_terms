# Address Resolution Protocol (ARP)

## Overview

**Address Resolution Protocol (ARP)** is a network protocol used to map an **IP address** to a **MAC (Media Access Control) address** on a **Local Area Network (LAN)**.

Since computers communicate using MAC addresses on a local network, ARP helps find the correct MAC address that belongs to a known IP address.

---

## What is ARP?

ARP stands for **Address Resolution Protocol**.

It is responsible for translating:

```
IP Address  →  MAC Address
```

This translation allows devices on the same LAN to communicate with each other.

---

## Why is ARP Needed?

Every device has:

- **IP Address** → Logical address (Layer 3)
- **MAC Address** → Physical address (Layer 2)

When a device wants to send data to another device on the same network, it knows the destination IP address but needs the destination MAC address.

ARP provides that MAC address.

Without ARP, devices on a LAN would not know where to send Ethernet frames.

---

## Why Does Translation Happen?

The addresses are different sizes.

| Address | Size |
|----------|------|
| IPv4 Address | 32 bits |
| MAC Address | 48 bits |

ARP translates the 32-bit IP address into the corresponding 48-bit MAC address.

---

## ARP and the OSI Model

ARP works between the **Network Layer (Layer 3)** and the **Data Link Layer (Layer 2)**.

| OSI Layer | Address Used |
|-----------|--------------|
| Layer 3 (Network) | IP Address |
| Layer 2 (Data Link) | MAC Address |

ARP connects these two layers.

---

## How ARP Works

Suppose:

```
PC A

IP: 192.168.1.10
MAC: AA-AA-AA-AA-AA-AA
```

wants to send data to:

```
PC B

IP: 192.168.1.20
MAC: BB-BB-BB-BB-BB-BB
```

### Step 1

PC A knows the destination IP address:

```
192.168.1.20
```

but does not know its MAC address.

---

### Step 2

PC A checks its **ARP Cache**.

If the MAC address already exists, it uses it immediately.

---

### Step 3

If no entry exists, PC A sends an **ARP Request** to every device on the LAN.

Example:

```
Who has IP address 192.168.1.20?
Tell 192.168.1.10
```

This request is called a **broadcast** because every device receives it.

---

### Step 4

Only PC B recognizes its IP address and replies.

Example:

```
192.168.1.20 is at
BB-BB-BB-BB-BB-BB
```

This reply is called an **ARP Reply**.

---

### Step 5

PC A stores the information in its **ARP Cache**.

```
192.168.1.20

↓

BB-BB-BB-BB-BB-BB
```

Now PC A can send Ethernet frames directly to PC B.

---

## What is an ARP Cache?

An **ARP Cache** is a small table stored in a computer's memory.

It keeps recently learned IP-to-MAC address mappings.

Example:

| IP Address | MAC Address |
|------------|-------------|
| 192.168.1.10 | AA-AA-AA-AA-AA-AA |
| 192.168.1.20 | BB-BB-BB-BB-BB-BB |

Using the cache avoids sending unnecessary ARP requests.

---

## Dynamic ARP Cache

Most ARP entries are created automatically.

Characteristics:

- Created automatically
- Stored temporarily
- Deleted after several minutes
- Updated when needed

---

## Static ARP Entry

A network administrator can manually create an ARP entry.

Characteristics:

- Created manually
- Does not expire automatically
- Used in special network environments

---

## Why Does ARP Cache Expire?

ARP entries are removed to:

- Save memory
- Remove outdated information
- Improve security
- Prevent communication with inactive devices

---

## Broadcast and Unicast in ARP

### ARP Request

Sent to every device on the LAN.

```
Broadcast
```

---

### ARP Reply

Sent only to the requesting device.

```
Unicast
```

---

## Functions of ARP

ARP is used for:

- Finding MAC addresses
- Enabling communication on LANs
- Connecting Layer 3 to Layer 2
- Reducing network traffic using ARP cache
- Supporting Ethernet communication

---

## ARP Example

Suppose:

```
Laptop

IP: 192.168.1.5
```

wants to communicate with:

```
Printer

IP: 192.168.1.100
```

Process:

```
Laptop knows IP

↓

Needs Printer's MAC Address

↓

Checks ARP Cache

↓

No entry found

↓

Broadcast ARP Request

↓

Printer sends ARP Reply

↓

Laptop stores MAC Address

↓

Data transmission begins
```

---

## ARP and DHCP

### DHCP (Dynamic Host Configuration Protocol)

DHCP automatically assigns IP addresses to devices.

Example:

```
DHCP

↓

Assigns

192.168.1.20
```

DHCP answers:

> **"What IP address should this device use?"**

---

## ARP and DNS

### DNS (Domain Name System)

DNS translates:

```
Domain Name

↓

IP Address
```

Example:

```
www.google.com

↓

142.250.xxx.xxx
```

DNS answers:

> **"What IP address belongs to this website?"**

---

## Difference Between ARP, DHCP, and DNS

| Protocol | Purpose |
|----------|---------|
| ARP | Converts IP Address → MAC Address |
| DHCP | Assigns IP addresses automatically |
| DNS | Converts Domain Name ↔ IP Address |

---

## Advantages of ARP

- Enables communication between devices on a LAN
- Automatically discovers MAC addresses
- Reduces manual configuration
- Uses ARP cache to improve performance
- Supports efficient Ethernet communication

---

## Disadvantages of ARP

- Works only on local networks (LAN)
- Vulnerable to ARP spoofing attacks
- Broadcast requests increase network traffic
- ARP cache entries can become outdated

---

## Key Points

- ARP stands for **Address Resolution Protocol**.
- ARP translates an **IP address** into a **MAC address**.
- Works on **Local Area Networks (LANs)**.
- Operates between **OSI Layer 2** and **Layer 3**.
- ARP Request is a **broadcast**.
- ARP Reply is a **unicast**.
- ARP stores mappings in an **ARP Cache**.
- DHCP assigns IP addresses.
- DNS translates domain names into IP addresses.

---

## Conclusion

Address Resolution Protocol (ARP) is an essential networking protocol that enables communication between devices on a Local Area Network. By translating IP addresses into MAC addresses, ARP allows Ethernet frames to reach the correct destination. Together with DHCP and DNS, ARP plays a vital role in making modern computer networks function efficiently.