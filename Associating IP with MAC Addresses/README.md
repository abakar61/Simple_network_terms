# ARP – Associating IP with MAC Addresses

## 1. What is ARP?

**ARP** stands for **Address Resolution Protocol**.

ARP is used in **IPv4 networks** to find the **MAC address associated with an IP address**.

### Easy memory

```text
IP address → ARP → MAC address
```

A computer may know the destination IP address but not the destination MAC address.

ARP helps the computer discover the MAC address.

---

## 2. Why Do We Need ARP?

When a computer wants to send data, it needs:

* **IP address** → identifies the destination at Layer 3
* **MAC address** → identifies the next device on the local network at Layer 2

For example:

```text
PC
IP: 192.168.1.10

Router
IP: 192.168.1.1
MAC: 00:13:FE:19:C7:9E
```

The PC knows:

```text
Router IP = 192.168.1.1
```

But it does not know:

```text
Router MAC = ?
```

Therefore, the PC uses ARP.

---

# 3. Example: PC Wants to Browse a Website

Suppose you type:

```text
www.google.com
```

The computer first needs to find the website's IP address.

It sends a **DNS query**:

```text
PC → DNS Server
"What is the IP address of www.google.com?"
```

In this example, the **home router is the DNS server**.

So the PC needs to send the DNS query to:

```text
DNS/Router IP = 192.168.1.1
```

But the PC still needs the router's MAC address.

---

# 4. ARP Request

The PC temporarily puts the DNS packet on hold.

Then it creates an **ARP request**.

The question is:

```text
"Who has 192.168.1.1?
Tell me your MAC address."
```

Because the PC does not know the destination MAC address, the ARP request is sent as a **broadcast**.

Broadcast MAC address:

```text
FF:FF:FF:FF:FF:FF
```

### ARP Request

```text
PC
IP: 192.168.1.10
        |
        | ARP Request
        | "Who has 192.168.1.1?"
        |
        v
   LAN / Switch
    /   |   \
   /    |    \
 PC2   PC3   Router
              |
              | IP: 192.168.1.1
```

All devices on the local LAN receive the broadcast.

However, only the device with:

```text
192.168.1.1
```

needs to respond.

---

# 5. ARP Reply

The router receives the ARP request.

It sees:

```text
My IP = 192.168.1.1
```

So it sends an **ARP reply** back to the PC:

```text
"I have IP 192.168.1.1.
My MAC address is 00:13:FE:19:C7:9E."
```

### ARP Reply

```text
Router
IP: 192.168.1.1
MAC: 00:13:FE:19:C7:9E
        |
        | ARP Reply
        | "My MAC is 00:13:FE:19:C7:9E"
        |
        v
       PC
```

---

# 6. ARP Cache

The PC saves the information in its **ARP cache/table**.

Example:

```text
IP Address       MAC Address
192.168.1.1  →   00:13:FE:19:C7:9E
```

Now the PC knows:

```text
192.168.1.1 → 00:13:FE:19:C7:9E
```

It does not need to send another ARP request every time it sends a packet to the router.

The ARP entry stays in memory for a limited time and can eventually expire.

---

# 7. Sending the DNS Query

Now the PC has everything it needs.

### IP packet

```text
Source IP:
192.168.1.10

Destination IP:
192.168.1.1
```

### Ethernet frame

```text
Source MAC:
PC's MAC

Destination MAC:
00:13:FE:19:C7:9E
```

So:

```text
PC
 |
 | Ethernet Frame
 | Destination MAC = Router MAC
 |
 v
Router
 |
 | DNS Query
 v
DNS processing
```

The router receives the DNS query and can perform the DNS lookup.

---

# 8. Complete Process

The complete process is:

```text
1. User enters:
   www.google.com

2. PC creates a DNS query.

3. PC knows the DNS server IP:
   192.168.1.1

4. PC checks its ARP cache.

5. MAC address is not found.

6. PC sends ARP Request:
   "Who has 192.168.1.1?"

7. Router sends ARP Reply:
   "192.168.1.1 is
    00:13:FE:19:C7:9E"

8. PC stores the mapping:
   192.168.1.1
        ↓
   00:13:FE:19:C7:9E

9. PC sends the DNS query
   to the router.

10. Router processes the DNS query.
```

---

# 9. ARP Cache Commands

On Linux, you can view the ARP/neighbor table with:

```bash
ip neigh
```

Example:

```text
192.168.1.1 dev eth0 lladdr 00:13:fe:19:c7:9e REACHABLE
```

This means:

```text
192.168.1.1
      ↓
00:13:FE:19:C7:9E
```

You can also use:

```bash
arp -n
```

if the `arp` command is installed.

---

# 10. Important Terms

| Term        | Meaning                                          |
| ----------- | ------------------------------------------------ |
| ARP         | Finds MAC address from IPv4 address              |
| ARP Request | Asks "Who has this IP?"                          |
| ARP Reply   | Provides the MAC address                         |
| ARP Cache   | Stores IP-to-MAC mappings                        |
| Broadcast   | Message sent to all devices on the LAN           |
| MAC Address | Layer 2 address                                  |
| IP Address  | Layer 3 address                                  |
| DNS Query   | Request to find an IP address from a domain name |

---

# 11. Easy Memory

Remember this:

```text
DNS
Domain Name → IP Address
```

```text
ARP
IP Address → MAC Address
```

So the overall process is:

```text
www.google.com
       |
       | DNS
       v
   IP Address
       |
       | ARP
       v
   MAC Address
       |
       v
   Ethernet Frame
       |
       v
     Router
```

## Key Point

**ARP connects Layer 3 addressing (IP) with Layer 2 addressing (MAC) on the local IPv4 network.**

```text
IP = Where?
MAC = Which local device?
ARP = Find the MAC for an IP
```
