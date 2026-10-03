# NAT64 — Network Address Translation for IPv6

## Introduction

NAT64 is a network translation technology that allows IPv6-only devices to communicate with IPv4-only devices.

It is mainly used during the transition from IPv4 to IPv6.

NAT64 translates:

- IPv6 packets → IPv4 packets
- IPv4 packets → IPv6 packets

## Why Do We Need NAT64?

IPv4 and IPv6 are different protocols and are not directly compatible.

NAT64 is useful because:

- Many new devices use IPv6.
- Many older servers still use IPv4.
- IPv4 addresses are becoming limited.
- IPv6-only clients still need to access IPv4-only servers.
- IPv4-only clients may need to access IPv6-only servers.

### Simple Example

```text
IPv6 Client
    |
    | IPv6
    v
+-------------+
|   NAT64     |
|   Router    |
+-------------+
    |
    | IPv4
    v
IPv4 Server
```

The NAT64 router translates traffic between IPv6 and IPv4.

# IPv4 and IPv6 Transition Methods

There are three common methods for IPv4/IPv6 transition:

1. Dual Stack
2. Tunneling
3. Translation

## 1. Dual Stack

A device runs both IPv4 and IPv6.

```text
Device
 ├── IPv4
 └── IPv6
```

It can communicate using either protocol.

## 2. Tunneling

One protocol is carried inside another protocol.

```text
IPv6 Packet
     |
     v
IPv4 Network
     |
     v
IPv6 Packet
```

Tunneling provides coexistence, but it does not directly translate IPv4 into IPv6.

## 3. Translation

A translator changes an IPv4 packet into an IPv6 packet or an IPv6 packet into an IPv4 packet.

NAT64 is an example of translation.

```text
IPv6 → NAT64 → IPv4
IPv4 → NAT64 → IPv6
```

# Types of NAT64

There are two main types:

1. Stateless NAT64
2. Stateful NAT64

## Stateless NAT64

Stateless NAT64 does not maintain translation state.

It generally uses a 1:1 mapping.

```text
IPv6 Address
      |
      | 1:1
      v
IPv4 Address
```

### Characteristics

- No translation state is maintained.
- Uses 1:1 address mapping.
- Requires an IPv4 address for each IPv6 address.
- Does not conserve many IPv4 addresses.
- Provides address transparency.

## Stateful NAT64

Stateful NAT64 maintains translation information for active connections.

It can allow many IPv6 clients to share IPv4 addresses.

```text
IPv6 Client 1 ----\
IPv6 Client 2 -----+---- NAT64 ---- IPv4 Server
IPv6 Client 3 ----/
```

Different connections can use different port numbers.

### Characteristics

- Maintains translation state.
- Supports many-to-one translation.
- Conserves IPv4 addresses.
- Can use IPv4 address overloading.
- Similar to PAT in IPv4 NAT.

# Stateless vs Stateful NAT64

| Feature | Stateless NAT64 | Stateful NAT64 |
|---|---|---|
| Translation | 1:1 | 1:N |
| State maintained | No | Yes |
| IPv4 conservation | No | Yes |
| Address mapping | Fixed | Dynamic |
| IPv4 address requirement | More addresses | Fewer addresses |
| Port overloading | No | Yes |
| Translation bindings | Not created | Created |

# Main Components of NAT64

There are three important components in a typical NAT64 solution:

1. NAT64 Prefix
2. DNS64
3. NAT64 Router

## 1. NAT64 Prefix

The NAT64 prefix is used to represent an IPv4 address inside an IPv6 address.

The well-known NAT64 prefix is:

```text
64:ff9b::/96
```

Example:

```text
IPv4 address:
10.1.113.2

IPv4 in hexadecimal:
0a01:7102

NAT64 IPv6 address:
64:ff9b::0a01:7102
```

## 2. DNS64

DNS64 helps an IPv6-only client discover an IPv4-only server.

Normally, an IPv6 client requests an AAAA record.

If the server does not have an AAAA record, DNS64 looks for an A record.

```text
IPv6 Client
     |
     | AAAA request
     v
   DNS64
     |
     | A request
     v
 IPv4 DNS
     |
     | IPv4 address
     v
   DNS64
```

DNS64 then creates a synthetic IPv6 address using the NAT64 prefix.

## 3. NAT64 Router

The NAT64 router performs the actual translation.

```text
IPv6 Network
     |
     | IPv6
     v
+-------------+
| NAT64 Router|
+-------------+
     |
     | IPv4
     v
IPv4 Network
```

# Stateful NAT64 Packet Flow

Suppose:

```text
IPv6 Client:
2001:DB8:3001::9

IPv4 Server:
10.1.113.2
```

The IPv6 client wants to communicate with the IPv4 server.

## Step 1 — DNS Request

The IPv6 client asks DNS64 for:

```text
www.example.com
```

It sends an AAAA request.

## Step 2 — DNS64 Checks IPv6

DNS64 checks whether the server has an IPv6 AAAA record.

If there is no AAAA record, DNS64 looks for an IPv4 A record.

## Step 3 — DNS64 Finds IPv4 Address

DNS64 finds:

```text
10.1.113.2
```

## Step 4 — DNS64 Creates IPv6 Address

The IPv4 address is converted to hexadecimal:

```text
10.1.113.2
     ↓
0a01:7102
```

The NAT64 prefix is added:

```text
2800:1503:2000:1:1::/96
```

Result:

```text
2800:1503:2000:1:1::0a01:7102
```

The IPv6 client believes it is communicating with an IPv6 server.

## Step 5 — IPv6 Packet Travels to NAT64

The client sends an IPv6 packet:

```text
Source:
2001:DB8:3001::9

Destination:
2800:1503:2000:1:1::0a01:7102
```

The packet reaches the NAT64 router.

## Step 6 — NAT64 Translates the Packet

The NAT64 router:

1. Removes the NAT64 prefix.
2. Extracts the IPv4 address.
3. Changes the IPv6 header into an IPv4 header.
4. Translates the IPv6 source address into an IPv4 address.
5. Creates a translation state.

The destination becomes:

```text
10.1.113.2
```

## Step 7 — IPv4 Packet Is Forwarded

The translated packet is sent into the IPv4 network.

```text
NAT64
  |
  | IPv4
  v
10.1.113.2
```

## Step 8 — Server Replies

The IPv4 server sends a response back to the NAT64 router.

The NAT64 router checks its translation state.

## Step 9 — NAT64 Translates Back

The router converts the IPv4 response into IPv6.

```text
IPv4
  ↓
NAT64
  ↓
IPv6
```

The response is then sent back to the IPv6 client.

# Complete Communication

```text
             IPv6 Network

        +------------------+
        |   IPv6 Client    |
        | 2001:DB8:3001::9 |
        +------------------+
                 |
                 | IPv6
                 |
                 v
        +------------------+
        |   NAT64 Router   |
        +------------------+
                 |
                 | IPv4
                 |
                 v
        +------------------+
        |   IPv4 Server    |
        |   10.1.113.2     |
        +------------------+
```

NAT64 performs:

```text
IPv6 → IPv4
IPv4 → IPv6
```

# NAT64 Prefix Example

Example IPv4 address:

```text
10.1.113.2
```

Convert each IPv4 octet to hexadecimal:

```text
10  = 0A
1   = 01
113 = 71
2   = 02
```

Therefore:

```text
10.1.113.2
```

becomes:

```text
0a01:7102
```

With the NAT64 prefix:

```text
2800:1503:2000:1:1::/96
```

the resulting IPv6 address is:

```text
2800:1503:2000:1:1::0a01:7102
```

# Cisco NAT64 Configuration

## 1. Configure the IPv6 Interface

The interface facing the IPv6 network must have an IPv6 address.

```cisco
interface GigabitEthernet0/0
 ipv6 address 2001:DB8:3001::1/64
 ipv6 enable
 no shutdown
```

## 2. Configure the IPv4 Interface

The interface facing the IPv4 network must have an IPv4 address.

```cisco
interface GigabitEthernet0/1
 ip address 10.1.113.1 255.255.255.0
 no shutdown
```

## 3. Configure the NAT64 Stateful Prefix

```cisco
nat64 prefix stateful 2800:1503:2000:1:1::/96
```

This prefix is used to represent IPv4 destinations as IPv6 addresses.

## 4. Create an IPv4 Address Pool

Example:

```cisco
nat64 v4 pool POOL1 10.50.50.50
```

The pool provides IPv4 addresses that can be used for translation.

## 5. Create an IPv6 ACL

Example:

```cisco
ipv6 access-list NAT64-ACL
 permit ipv6 2001:DB8:3001::/64 any
```

This identifies IPv6 traffic that can use NAT64.

## 6. Enable NAT64 Translation

Example:

```cisco
nat64 v6v4 list NAT64-ACL pool POOL1 overload
```

`overload` allows multiple IPv6 clients to share an IPv4 address using different port numbers.

# Verification Commands

After configuring NAT64, use these commands to verify it.

## Show NAT64 Translations

```cisco
show nat64 translations
```

This shows active translation entries.

## Show NAT64 Statistics

```cisco
show nat64 statistics
```

This shows NAT64 traffic and translation statistics.

## Test Connectivity

Example:

```cisco
ping 2800:1503:2000:1:1::0a01:7102
```

If the configuration is correct, the IPv6 host should be able to reach the IPv4 server through NAT64.

# Scenario 2 — IPv4 Client to IPv6 Server

NAT64 can also be used in the opposite direction.

```text
IPv4 Client
     |
     | IPv4
     v
+-------------+
|    NAT64    |
|   Router    |
+-------------+
     |
     | IPv6
     v
IPv6 Server
```

In this scenario:

- The client uses IPv4.
- The server uses IPv6.
- The NAT64 router performs the translation.
- DNS64 is not required in this particular static-mapping scenario.
- A static IPv4-to-IPv6 mapping can be configured on the NAT64 router.

# Important Terms

| Term | Meaning |
|---|---|
| NAT64 | Translates between IPv6 and IPv4 |
| DNS64 | Creates synthetic IPv6 records for IPv4 servers |
| Stateful | Keeps translation information |
| Stateless | Does not keep translation state |
| NAT64 Prefix | IPv6 prefix used to represent IPv4 addresses |
| IPv4 Pool | IPv4 addresses used for translation |
| ACL | Controls which traffic can be translated |
| Overload | Allows multiple clients to share an IPv4 address |
| AAAA | DNS record containing an IPv6 address |
| A | DNS record containing an IPv4 address |
| Binding | Mapping between IPv6 and IPv4 addresses |
| PAT | Uses port numbers to allow address sharing |

# Key Points to Remember

1. **NAT64 connects IPv6 and IPv4 networks.**
2. **DNS64 helps IPv6 clients discover IPv4-only servers.**
3. **Stateful NAT64 maintains translation state.**
4. **Stateless NAT64 uses fixed 1:1 mappings.**
5. **The NAT64 prefix represents an IPv4 address inside IPv6.**
6. **IPv4 address overloading can conserve IPv4 addresses.**
7. **ACLs can control which IPv6 traffic is translated.**
8. **`show nat64 translations`** is used to check active translations.
9. **`show nat64 statistics`** is used to check NAT64 statistics.

# Basic NAT64 Concept

```text
             DNS64
               |
               |
IPv6 Client → NAT64 Router → IPv4 Server
     IPv6          |             IPv4
                   |
              Translation

        IPv6  ←→  IPv4
```

NAT64 provides a way for IPv6-only and IPv4-only networks to communicate during the transition from IPv4 to IPv6.