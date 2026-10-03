# NAT Overload (PAT)

## Introduction

Port Address Translation (PAT), also known as NAT Overload, is a type of Network Address Translation (NAT) that allows multiple devices on a local network with private IP addresses to share a single public IP address when accessing external networks such as the Internet. :contentReference[oaicite:0]{index=0}

To understand PAT, it is important to understand sockets, TCP sessions, IP addresses, and port numbers.

## What Is a Socket?

A socket is an endpoint used for sending and receiving data between devices over a network.

A socket is made from:

```text
IP_Address:Port_Number
```

For example:

```text
10.1.1.1:43000
```

When two applications communicate, each application uses a socket. A connection is created by pairing the client socket with the server socket. :contentReference[oaicite:1]{index=1}

## What Is a TCP Session?

A TCP session is a communication connection between two sockets.

Example:

```text
TCP  10.1.1.1:43000  →  65.3.2.1:443
TCP  10.1.1.1:43001  →  65.3.2.1:443
TCP  10.1.1.1:43002  →  65.3.2.1:443
```

The client uses different port numbers for different connections.

For example:

```text
10.1.1.1:43000 → 65.3.2.1:443
10.1.1.1:43001 → 65.3.2.1:443
```

These are two different TCP sessions because the client-side ports are different. :contentReference[oaicite:2]{index=2}

## Why Are Ports Important?

A pair of local and remote sockets uniquely identifies a TCP/UDP connection.

For example:

```text
10.1.1.1:43000 - 65.3.2.1:443
```

is one unique TCP session.

If the same host creates another connection to the same server, it can use another port:

```text
10.1.1.1:43001 - 65.3.2.1:443
```

The server normally listens on a fixed port such as:

```text
HTTP  → 80
HTTPS → 443
```

Therefore, the client uses different source ports to distinguish its different connections. :contentReference[oaicite:3]{index=3}

## Multiple Hosts Communicating With One Server

Different hosts can use the same source port because their IP addresses are different.

Example:

```text
PC1: 10.1.1.1:43000 → Server: 65.3.2.1:443
PC2: 10.1.1.2:43000 → Server: 65.3.2.1:443
PC3: 10.1.1.3:43000 → Server: 65.3.2.1:443
```

The server can distinguish these connections because the source IP addresses are different. :contentReference[oaicite:4]{index=4}

## What Is Port Address Translation (PAT)?

PAT allows multiple private IPv4 addresses to share one public IPv4 address.

PAT does this by changing the complete socket:

```text
IP Address + Port
```

Instead of changing only the IP address, PAT changes both the IP address and port number.

Example:

```text
PC1
10.1.1.1:40591
       |
       |
       v
     PAT
       |
       v
37.3.1.1:4096
```

Another client:

```text
PC2
10.1.1.2:49399
       |
       |
       v
     PAT
       |
       v
37.3.1.1:4097
```

Another client:

```text
PC3
10.1.1.3:61278
       |
       |
       v
     PAT
       |
       v
37.3.1.1:4098
```

All three clients use the same public IP address:

```text
37.3.1.1
```

but different port numbers.

The server can therefore distinguish the connections. :contentReference[oaicite:5]{index=5}

# How Does PAT Work?

PAT, also called NAT Overload, translates many private IP addresses into one public IP address.

Example:

```text
PC1 ── 10.1.1.1 ──┐
                   |
PC2 ── 10.1.1.2 ──┼── PAT ── 37.3.1.1 ── Internet
                   |
PC3 ── 10.1.1.3 ──┘
```

The server sees the connections as coming from the same public IP address:

```text
37.3.1.1:4096
37.3.1.1:4097
37.3.1.1:4098
```

PAT is widely used because it allows many private devices to access external networks while using a small number of public IPv4 addresses. :contentReference[oaicite:6]{index=6}

## Advantages of PAT

- Multiple private devices can share one public IPv4 address.
- It reduces the need for public IPv4 addresses.
- It is widely used in home networks.
- It is widely used in enterprise networks.
- Different connections are identified using port numbers.

## Disadvantages of PAT

PAT mainly works with client-server communication.

It can also make inbound connections from the Internet more complicated.

For example, an internal server cannot normally be reached directly from the outside using basic PAT. In such situations, static one-to-one NAT can be used for the internal server. :contentReference[oaicite:7]{index=7}

# PAT Configuration

In this example, there are three internal clients that need Internet access.

The router has only one public IPv4 address on Ethernet0/1.

```text
                    Internet
                       |
                       |
                 37.3.1.1/30
                       |
                +-------------+
                |    Router   |
                |    PAT      |
                +-------------+
                       |
                  10.1.1.254/24
                       |
             +---------+---------+
             |         |         |
            PC1       PC2       PC3
         10.1.1.1  10.1.1.2  10.1.1.3
```

PAT allows all three PCs to access the Internet using:

```text
37.3.1.1
```

The configuration has three main steps:

1. Define inside and outside interfaces.
2. Define the inside local addresses.
3. Configure the PAT rule.

# Step 1 — Define Inside and Outside

First, tell the router which interface is connected to the inside network and which interface is connected to the outside network.

```cisco
interface Ethernet0/0
 ip address 10.1.1.254 255.255.255.0
 ip nat inside
!
interface Ethernet0/1
 ip address 37.3.1.1 255.255.255.252
 ip nat outside
!
```

Ethernet0/0 is the inside interface.

Ethernet0/1 is the outside interface. :contentReference[oaicite:8]{index=8}

# Step 2 — Define Inside Local Addresses

Next, configure an access list that identifies which internal IP addresses should be translated.

```cisco
ip access-list standard INSIDE_LOCAL
 permit 10.1.1.0 0.0.0.255
!
```

This means the router should translate addresses from:

```text
10.1.1.0/24
```

The access list gives the router control over which internal networks should be translated. :contentReference[oaicite:9]{index=9}

# Step 3 — Configure the PAT Rule

Configure PAT using:

```cisco
ip nat inside source list INSIDE_LOCAL interface Ethernet0/1 overload
!
```

## Command Explanation

### `ip nat inside`

```text
ip nat inside
```

The translation is for hosts located on the inside network.

### `source`

```text
source
```

The source IP address of the packet will be translated.

### `list INSIDE_LOCAL`

```text
list INSIDE_LOCAL
```

Uses the access list to identify which inside IP addresses should be translated.

### `interface Ethernet0/1`

```text
interface Ethernet0/1
```

The IP address configured on Ethernet0/1 will be used as the public IP address.

### `overload`

```text
overload
```

Enables PAT/NAT Overload.

It allows multiple inside clients to share one public IPv4 address by using different port numbers. :contentReference[oaicite:10]{index=10}

# Complete PAT Configuration

```cisco
interface Ethernet0/0
 ip address 10.1.1.254 255.255.255.0
 ip nat inside
!
interface Ethernet0/1
 ip address 37.3.1.1 255.255.255.252
 ip nat outside
!
ip access-list standard INSIDE_LOCAL
 permit 10.1.1.0 0.0.0.255
!
ip nat inside source list INSIDE_LOCAL interface Ethernet0/1 overload
!
```

# Verifying PAT

After clients generate traffic toward an outside server, use:

```cisco
show ip nat translations
```

or:

```cisco
sh ip nat translations
```

Example output:

```text
Pro Inside global      Inside local       Outside local      Outside global
tcp 37.3.1.1:4096      10.1.1.1:40591     8.8.8.8:23         8.8.8.8:23
tcp 37.3.1.1:4097      10.1.1.2:49399     8.8.8.8:23         8.8.8.8:23
tcp 37.3.1.1:4098      10.1.1.3:61278     8.8.8.8:23         8.8.8.8:23
```

This shows that the three private addresses:

```text
10.1.1.1
10.1.1.2
10.1.1.3
```

are translated to the same public IP:

```text
37.3.1.1
```

but with different ports:

```text
4096
4097
4098
```

This is the main idea of PAT. :contentReference[oaicite:11]{index=11}

# Verify PAT Statistics

Use:

```cisco
show ip nat statistics
```

Example:

```text
NAT# show ip nat statistics
Total active translations: 3
Outside interfaces:
  Ethernet0/1
Inside interfaces:
  Ethernet0/0
Hits: 140
Misses: 0
```

The statistics provide information about active translations, interfaces, hits, misses, and dynamic mappings. :contentReference[oaicite:12]{index=12}

# Important PAT Terms

| Term | Meaning |
|---|---|
| NAT | Network Address Translation |
| PAT | Port Address Translation |
| NAT Overload | Another name for PAT |
| Inside Local | Private IP address of the internal device |
| Inside Global | Public IP address used after translation |
| Outside Local | Outside address as seen from the inside |
| Outside Global | Actual outside/public address |
| Socket | IP address + port number |
| Port | Identifies an application connection |
| Overload | Allows many devices to share one public IP |
| ACL | Identifies which IP addresses should be translated |
| Inside Interface | Interface connected to the private network |
| Outside Interface | Interface connected to the external network |

# NAT vs PAT

| Feature | NAT | PAT |
|---|---|---|
| Translation | IP address | IP address + port |
| Public IPs required | More | Fewer |
| Address sharing | Usually 1:1 | Many-to-one |
| Uses ports | No | Yes |
| IPv4 conservation | Lower | Higher |
| Common name | NAT | NAT Overload |

# Simple PAT Example

```text
Private Network

PC1: 10.1.1.1:40591
PC2: 10.1.1.2:49399
PC3: 10.1.1.3:61278
          |
          |
          v
      +-------+
      |  PAT  |
      +-------+
          |
          |
          v
Public IP: 37.3.1.1

Translated connections:

10.1.1.1:40591 → 37.3.1.1:4096
10.1.1.2:49399 → 37.3.1.1:4097
10.1.1.3:61278 → 37.3.1.1:4098
```

The important point is:

```text
Many private IP addresses
          ↓
     One public IP
          ↓
Different port numbers
```

# Key Points to Remember

1. **PAT stands for Port Address Translation.**
2. **PAT is also called NAT Overload.**
3. **PAT allows many private devices to share one public IPv4 address.**
4. **PAT changes the source IP address and port number.**
5. **The port number helps identify different connections.**
6. **`ip nat inside` identifies the inside interface.**
7. **`ip nat outside` identifies the outside interface.**
8. **An ACL identifies which inside addresses should be translated.**
9. **`overload` enables PAT.**
10. **`show ip nat translations` displays active translations.**
11. **`show ip nat statistics` displays NAT/PAT statistics.**
12. **PAT is commonly used for Internet access from private networks.**

# Basic PAT Concept

```text
          PRIVATE NETWORK
               
 PC1 ── 10.1.1.1:40591 ──\
                            \
 PC2 ── 10.1.1.2:49399 ─────+── PAT ── 37.3.1.1 ── Internet
                            /
 PC3 ── 10.1.1.3:61278 ───/

PAT translates:

10.1.1.1:40591 → 37.3.1.1:4096
10.1.1.2:49399 → 37.3.1.1:4097
10.1.1.3:61278 → 37.3.1.1:4098
```

**PAT allows many private IPv4 devices to access external networks by sharing one public IPv4 address and using different port numbers to keep their connections separate.**