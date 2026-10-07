# OSPF – Open Shortest Path First

## 1. What is OSPF?

OSPF stands for **Open Shortest Path First**.

OSPF is a **link-state dynamic routing protocol**.

Its main purpose is to calculate the **best path to every IP destination** in a network.

For example, if a network has many routers and several possible paths, OSPF automatically calculates which path should be used.

Unlike static routing, OSPF can automatically react when:

* A link goes down
* A new link is added
* The network topology changes

---

## 2. How OSPF Works

Each router runs its **own independent OSPF process**.

OSPF routers exchange information about their connected links.

The routers use this information to build a complete view of the network.

The basic process is:

```text id="z0n4yh"
OSPF Process
     ↓
Discover Neighbors
     ↓
Exchange Link-State Information
     ↓
Build LSDB
     ↓
Run SPF / Dijkstra Algorithm
     ↓
Calculate Best Paths
     ↓
Update Routing Table
```

---

## 3. OSPF Process

The OSPF process runs locally on each router.

The process uses:

* Tables
* Databases
* OSPF messages

Its final goal is to calculate the best routes and place them in the router's routing table.

On Cisco devices, OSPF is disabled by default.

A **process ID** is used to identify the OSPF process on the router.

The process ID is **locally significant**.

This means that the OSPF process ID does not have to be the same on every router.

---

## 4. Router ID

Every OSPF router needs a unique **32-bit Router ID (RID)**.

The Router ID identifies the router within the OSPF process.

OSPF uses the following order to select the Router ID:

### Step 1 – Manually configured Router ID

If a Router ID is explicitly configured, OSPF uses it.

### Step 2 – Highest Loopback IP

If no Router ID is manually configured, OSPF chooses the highest active loopback IP address.

### Step 3 – Highest non-loopback IP

If there is no suitable loopback address, OSPF chooses the highest active non-loopback IP address.

The general recommendation is to **manually configure the Router ID**.

---

## 5. OSPF Neighbors

After the OSPF process gets a Router ID, it sends **Hello messages** through OSPF-enabled interfaces.

When two routers are connected to the same network segment, they can discover each other and become OSPF neighbors.

For example:

```text id="6c0j7x"
Router 1
   |
   | OSPF Hello
   |
Router 2
```

OSPF neighbors have two important purposes:

1. Dynamically discover other OSPF routers.
2. Exchange link-state information.

---

## 6. Link-State

A **link** is basically a router interface.

For example:

```text id="1m8e2y"
Router
 |
 +-- Interface A
 |
 +-- Interface B
 |
 +-- Interface C
```

The **link state** describes properties of the interface, such as:

* IP address
* Subnet mask
* Interface type
* Relationship with neighboring routers

Routers advertise this information to their OSPF neighbors.

---

## 7. LSA – Link-State Advertisement

**LSA** stands for **Link-State Advertisement**.

An LSA contains link-state information about the network.

For example, a router can advertise information about its connected links to its neighbors.

```text id="7ukq2r"
Router R1
   |
   | LSA
   ↓
Router R2
```

LSAs are an important part of how OSPF routers learn about the network topology.

---

## 8. LSA Flooding

OSPF uses a process called **LSA flooding**.

When a router receives a new LSA, it updates its database and forwards the LSA to its other neighbors.

This continues until the LSA reaches all routers that should receive it.

Example:

```text id="q7w2lp"
R1 → R2 → R3 → R4
       ↓
      R5
```

The purpose is to make sure routers receive the information about topology changes.

---

## 9. LSDB

LSDB stands for **Link-State Database**.

Each router stores the LSAs it receives in its LSDB.

The LSDB contains information about the OSPF network topology.

In a single OSPF area, the routers maintain a consistent view of the network through their LSDBs.

The important relationship is:

```text id="4k2f8a"
LSA
 ↓
LSDB
 ↓
SPF Algorithm
 ↓
Best Path
```

---

## 10. SPF Algorithm

SPF stands for **Shortest Path First**.

OSPF uses the **Dijkstra algorithm** to calculate the shortest paths through the network.

The SPF algorithm uses the information in the LSDB as its input.

It creates a **shortest-path tree** from the perspective of the local router.

For example:

```text id="c4t8ns"
        R2
       /  \
      R1   R3
       \   /
        R4
```

The best path can be different for each router because the calculation is made from that router's own perspective.

---

## 11. OSPF Cost

OSPF uses a metric called **cost**.

Cost is assigned to links and is used by the SPF algorithm when selecting paths.

### Important rule

> **Lower OSPF cost is preferred.**

OSPF commonly calculates cost based on the outgoing interface bandwidth.

A commonly used formula is:

```text id="x3w8kj"
Cost = Reference Bandwidth / Link Bandwidth
```

For example:

```text id="8y5nq1"
10 Mbps link:

100 / 10 = 10

Cost = 10
```

And:

```text id="7d2m4p"
100 Mbps link:

100 / 100 = 1

Cost = 1
```

Therefore, a higher-bandwidth link normally has a lower cost.

---

## 12. Cumulative Cost

When there are multiple paths to a destination, OSPF adds the costs of the links along each path.

Example:

```text id="p2v8kf"
Path 1:

10 + 10 + 1 + 1 + 10 = 32


Path 2:

10 + 10 + 10 + 1 + 10 = 41
```

OSPF chooses:

```text id="8s6n2k"
Path 1
Total Cost = 32
```

because **32 is lower than 41**.

Therefore:

> **OSPF prefers the path with the lowest total cost.**

---

## 13. OSPF Routing Table

After SPF calculates the best paths, OSPF places those routes into the router's routing table.

For example:

```text id="4p7x9c"
LSDB
  ↓
SPF
  ↓
Best Path
  ↓
Routing Table
```

An OSPF route in a Cisco routing table is normally identified with:

```text id="q1x7vm"
O
```

The default administrative distance of OSPF is **110**.

---

## 14. OSPF Scaling Problem

LSA flooding can become expensive in a very large network.

For example, imagine a network with:

* 1,000+ routers
* 10,000+ links

Every topology change can generate LSAs that need to be processed.

This can require more:

* CPU
* RAM
* Processing time

A larger LSDB also means the SPF algorithm has more information to process.

Therefore:

> **More routers and links can require more CPU and RAM and can increase the time needed to react to topology changes.**

---

## 15. OSPF Areas

To solve scaling problems, OSPF uses **areas**.

An area is a segment of the OSPF network where routers exchange routing information.

Areas divide a large OSPF network into smaller sections.

Example:

```text id="n8j3kw"
             OSPF Network
                  |
        +---------+---------+
        |                   |
     Area 1              Area 2
        |                   |
     Routers              Routers
```

Areas help reduce the amount of information that each router must process.

---

## 16. Benefits of OSPF Areas

### 1. Reduced LSA Flooding

LSAs are primarily flooded within an area.

This reduces unnecessary flooding across the entire OSPF network.

### 2. Smaller LSDB

Each area has its own link-state database.

A smaller database requires fewer resources.

### 3. Better Scalability

Dividing a large network into areas makes OSPF more suitable for large networks.

### 4. Reduced SPF Processing

A topology change in one area does not necessarily require routers in another area to run SPF for that internal change.

This can improve resource usage and convergence behavior.

---

## 17. Simple OSPF Process

```text id="5y7r2n"
1. Start OSPF
       ↓
2. Select Router ID
       ↓
3. Send Hello messages
       ↓
4. Discover neighbors
       ↓
5. Become neighbors
       ↓
6. Exchange LSAs
       ↓
7. Build LSDB
       ↓
8. Run SPF / Dijkstra
       ↓
9. Calculate lowest-cost paths
       ↓
10. Install best routes
```

---

## 18. Key OSPF Terms

| Term         | Meaning                                                             |
| ------------ | ------------------------------------------------------------------- |
| OSPF         | Open Shortest Path First                                            |
| Link-State   | Information describing a router's links                             |
| Router ID    | Unique 32-bit identifier for an OSPF router                         |
| Hello        | Message used to discover OSPF neighbors                             |
| Neighbor     | OSPF router that has formed a relationship with another OSPF router |
| LSA          | Link-State Advertisement                                            |
| LSA Flooding | Process of distributing LSAs                                        |
| LSDB         | Link-State Database                                                 |
| SPF          | Shortest Path First                                                 |
| Dijkstra     | Algorithm used by OSPF to calculate shortest paths                  |
| Cost         | OSPF metric used to select paths                                    |
| Area         | Section of an OSPF network used for scalability                     |
| Process ID   | Local identifier for the OSPF process                               |

---

## 19. Key Takeaways

* **OSPF is a link-state dynamic routing protocol.**
* Each router runs its own independent OSPF process.
* OSPF needs a unique **Router ID**.
* Routers use **Hello messages** to discover neighbors.
* Routers exchange **LSAs**.
* LSAs are stored in the **LSDB**.
* The **SPF/Dijkstra algorithm** uses the LSDB to calculate paths.
* OSPF prefers the path with the **lowest total cost**.
* OSPF commonly uses interface bandwidth when calculating cost.
* **Areas** help OSPF scale to large networks.
