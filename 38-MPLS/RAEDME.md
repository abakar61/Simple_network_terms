# Multiprotocol Label Switching (MPLS)

## 1. Introduction

**Multiprotocol Label Switching (MPLS)** is a networking technology that forwards packets through a network using labels instead of relying only on destination IP addresses.

MPLS is commonly used by Internet Service Providers (ISPs) to connect company branches over a Wide Area Network (WAN).

It is sometimes called a **Layer 2.5 technology** because it operates between the Data Link Layer (Layer 2) and the Network Layer (Layer 3).

## 2. How Normal IP Routing Works

In normal IP routing, each router examines the destination IP address of a packet and checks its routing table to select the next hop.

### Example

A packet travels from Kigali to N'Djamena:

```text
PC Kigali
    |
    v
Router R1
    |
    v
Router R2
    |
    v
Router R3
    |
    v
PC N'Djamena
```

Each router uses its routing table to decide where to forward the packet next.

If the routing information changes, packets may follow a different path.

## 3. How MPLS Works

MPLS forwards packets using labels that identify forwarding instructions within the MPLS network.

Instead of relying on a full IP routing lookup at every intermediate router, MPLS routers use the label to determine how to forward packets.

### Example Topology

```text
Company A                                      Company B
Kigali Office                                  N'Djamena Office
     |                                               |
     v                                               v
   CE1 ---- PE1 -------- P1 -------- P2 -------- PE2 ---- CE2
             |           |           |           |
             +----------- MPLS NETWORK ---------+
```

* **CE (Customer Edge):** Router connected to the customer's network.
* **PE (Provider Edge):** Provider router that connects the customer to the MPLS network.
* **P (Provider):** Router inside the provider's MPLS network.

### Packet Forwarding Process

1. The ingress PE router receives the packet and classifies it into a Forwarding Equivalence Class (FEC).
2. The router attaches an MPLS label to the packet.
3. Intermediate provider routers use the label to forward the packet.
4. A router may replace the incoming label with another label. This process is called **label swapping**.
5. The egress PE router removes the MPLS label when appropriate and forwards the packet toward its destination.

## 4. Important MPLS Terms

### 4.1 Forwarding Equivalence Class (FEC)

A FEC is a group of packets that receive the same forwarding treatment.

For example, packets going toward the same destination network may belong to the same FEC.

### 4.2 MPLS Label

An MPLS label is a short identifier used by an MPLS router to make forwarding decisions.

The label is not the same as a destination IP address.

### 4.3 Label-Switched Path (LSP)

An LSP is the path that labeled packets follow through an MPLS network.

```text
PE1 ---- P1 ---- P2 ---- PE2
       Label-switched path
```

### 4.4 Label Switching

Label switching is the process of forwarding packets based on their MPLS labels.

### 4.5 Label Swapping

Label swapping occurs when a router replaces an incoming MPLS label with an outgoing label before forwarding the packet.

### 4.6 Label Edge Router (LER)

An LER is an MPLS edge router that classifies traffic and adds or removes MPLS labels as needed.

### 4.7 Label Switching Router (LSR)

An LSR is a router that forwards labeled packets using its label forwarding information.

## 5. MPLS and the OSI Model

MPLS is commonly described as operating at Layer 2.5.

| OSI Layer | Name      | Function                          |
| --------- | --------- | --------------------------------- |
| Layer 3   | Network   | IP addressing and routing         |
| Layer 2.5 | MPLS      | Label-based forwarding            |
| Layer 2   | Data Link | Ethernet frames and MAC addresses |
| Layer 1   | Physical  | Transmission of bits              |

Layer 2.5 is an informal description, not an official OSI layer.

## 6. Is MPLS a Private and Secure Network?

MPLS can provide traffic separation between customers using mechanisms such as MPLS VPNs.

However, **MPLS does not automatically encrypt traffic**.

If encryption is required, technologies such as IPsec VPNs can be used alongside MPLS.

## 7. Advantages of MPLS

* Supports communication between geographically separated company branches.
* Provides controlled traffic forwarding paths.
* Supports Quality of Service (QoS) for different types of traffic.
* Can support reliable and predictable WAN connectivity.
* Supports different network-layer protocols.

## 8. Disadvantages of MPLS

* Often more expensive than ordinary Internet connectivity.
* Can require complex configuration and provider coordination.
* May take time to deploy across multiple locations.
* Does not provide encryption by default.
* Traffic routed through central locations may create bottlenecks.
* May be less flexible for organizations that rely heavily on cloud services.

## 9. Where Is MPLS Used?

MPLS is commonly used for:

* Connecting company branch offices.
* Enterprise Wide Area Networks (WANs).
* Connecting campuses and data centers.
* Service provider networks.
* Supporting traffic prioritization through QoS.
* MPLS Layer 3 VPN and Layer 2 VPN services.

## 10. MPLS vs. Normal IP Routing

| Feature                | Normal IP Routing                | MPLS                                                         |
| ---------------------- | -------------------------------- | ------------------------------------------------------------ |
| Forwarding information | Destination IP and routing table | MPLS label and label forwarding table inside the MPLS domain |
| Forwarding method      | IP-based forwarding              | Label-based forwarding                                       |
| Path                   | Selected hop by hop              | Can use an established LSP                                   |
| Encryption             | Not automatic                    | Not automatic                                                |
| Common use             | General Internet routing         | Enterprise WANs and service provider networks                |

## 11. MPLS vs. SD-WAN

**MPLS** is a label-switching technology commonly used in provider WANs.

**SD-WAN** is a software-defined approach to managing WAN connectivity across links such as MPLS, broadband Internet, and LTE/5G.

Organizations may use SD-WAN to improve flexibility, optimize application traffic, and reduce WAN costs. SD-WAN can also operate alongside MPLS.

## 12. Verification and Practice

To study MPLS in a lab, you can build a topology with several Cisco routers.

Practice these concepts:

1. Configure IP addresses on router interfaces.
2. Establish basic IP connectivity between routers.
3. Configure an interior gateway protocol, such as OSPF.
4. Enable MPLS and label distribution on supported router interfaces.
5. Verify label bindings and label-switched forwarding.
6. Test end-to-end connectivity between customer networks.

Common Cisco IOS verification commands include:

```text
show mpls ldp neighbor
show mpls ldp bindings
show mpls forwarding-table
show mpls interfaces
show ip route
```

**Note:** These commands require an IOS image that supports the relevant MPLS features. Exact command availability depends on the platform and software version.

## 13. Conclusion

MPLS is a technology that uses labels to forward packets through a network. It is widely used by service providers to connect business branches and build WAN services.

Remember these three important terms:

* **FEC:** Group of packets receiving the same forwarding treatment.
* **Label:** Identifier used to forward packets through an MPLS network.
* **LSP:** Path followed by labeled packets.

Understanding these concepts provides a foundation for learning MPLS VPNs, LDP, traffic engineering, and service provider networking.
