# NAT and PAT

## Introduction

**NAT (Network Address Translation)** is a networking method used by routers to translate **private IP addresses into public IP addresses** when devices communicate with external networks such as the Internet.

Private IP addresses are used inside local networks and are not directly routable on the public Internet. NAT allows these private addresses to communicate with external networks by translating them into public addresses.

## NAT

NAT maps an internal private IP address to a public IP address.

For example:

```text
Private Network
192.168.1.10
192.168.1.20
192.168.1.30
       |
       v
     Router
       |
       v
 Public Network
```

NAT can help reduce the need for many public IPv4 addresses.

## PAT

**PAT (Port Address Translation)** is an extension of NAT that allows **many devices to share one public IP address**.

PAT uses different **port numbers** to identify and track each connection.

For example:

```text
PC1: 192.168.1.10:5000 ──┐
PC2: 192.168.1.20:5001 ──┤
PC3: 192.168.1.30:5002 ──┤──> Router ──> 203.0.113.10
PC4: 192.168.1.40:5003 ──┘
```

All devices can use the same public IP, while different port numbers allow the router to distinguish their connections.

## Difference Between NAT and PAT

| NAT                                  | PAT                                      |
| ------------------------------------ | ---------------------------------------- |
| Translates IP addresses              | Translates IP addresses and port numbers |
| Can use multiple public IP addresses | Usually uses one public IP address       |
| Mainly maps addresses                | Tracks multiple connections              |
| One-to-one or pool-based translation | Many-to-one translation                  |

## Advantages

* Saves public IPv4 addresses.
* Allows private networks to access the Internet.
* Allows many devices to share a public IP address with PAT.
* Hides internal private IP addressing from external networks.

## Key Terms

**Private IP:** An IP address used inside a local network.

**Public IP:** An IP address used to communicate across the Internet.

**NAT:** Translates private IP addresses into public IP addresses.

**PAT:** Allows multiple devices to share one public IP by using different port numbers.

**Port:** A number used to identify a specific network connection or service.

## Summary

NAT translates **private IP addresses into public IP addresses**.

PAT extends NAT by using **port numbers**, allowing many devices to share a single public IP address.

```text
NAT = IP Address Translation

PAT = IP Address + Port Translation
```
