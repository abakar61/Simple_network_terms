# Routing Information Protocol (RIP)

## 1. What is RIP?

**RIP (Routing Information Protocol)** is a **distance-vector dynamic routing protocol**.

It helps routers learn how to reach different networks.

RIP chooses the best path mainly by counting **hops**.

### What is a hop?

A **hop** means one router that a packet passes through.

For example:

```text
Router A → Router B → Router C → Network X
```

To reach Network X:

* Router A → B = 1 hop
* B → C = 1 hop
* C → Network X = next network

RIP prefers the route with the **fewest hops**.

### Maximum hop count

RIP has a maximum of **15 hops**.

* 1–15 hops = reachable
* 16 hops = unreachable

This limits RIP to relatively small networks.

---

# 2. History of RIP

RIP is one of the oldest dynamic routing protocols.

Its history started in the **late 1970s** with a routing protocol developed by **Xerox** for its networking systems.

The protocol was later adapted for UNIX systems and became widely used in **BSD UNIX**.

RIP was formally documented in **RFC 1058 in 1988**.

---

# 3. How RIP Works

RIP works in a simple way.

Each RIP router has a **routing table**.

The table contains information such as:

* Destination network
* Number of hops
* Next router to use

### RIP updates

Every **30 seconds**, a RIP router sends its routing information to neighboring routers.

When a router receives an update:

1. It looks at the route.
2. It adds **1 hop**.
3. It compares the route with its existing route.
4. If the new route has fewer hops, it uses the new route.

### Example

```text
Router A → Router B → Network X
```

Suppose:

* Router A knows Network X is 2 hops away.
* Router B learns this information from Router A.
* Router B adds 1 hop.

Therefore:

```text
2 + 1 = 3 hops
```

Router B considers Network X to be **3 hops away**.

This process continues until routers learn the available routes.

---

# 4. RIP Versions

There are three important versions:

## RIPv1

**RIPv1** is the original version.

Main characteristics:

* Classful routing
* Does not send subnet mask information
* Does not support VLSM
* Uses broadcast updates
* No built-in authentication

Because it is classful, it has limitations when using modern subnetting techniques.

---

## RIPv2

**RIPv2** improved many limitations of RIPv1.

Main characteristics:

* Classless routing
* Supports subnet masks
* Supports VLSM
* Uses multicast for updates
* Supports authentication

RIPv2 is more flexible than RIPv1.

---

## RIPng

**RIPng** means **Routing Information Protocol next generation**.

It was designed for **IPv6** networks.

It keeps the basic RIP idea:

```text
Choose the route using hop count
```

But it uses mechanisms and message formats suitable for IPv6.

---

# 5. RIP Metric

The main RIP metric is:

**Hop count**

RIP does not normally choose a route based on:

* Bandwidth
* Latency
* Load

It mainly asks:

> "Which route has fewer routers to cross?"

Example:

```text
Path A: Router → R1 → R2 → Network
        2 hops

Path B: Router → R3 → R4 → R5 → Network
        3 hops
```

RIP chooses **Path A** because it has fewer hops.

---

# 6. Advantages of RIP

### Easy to configure

RIP is simple and beginner-friendly.

### Wide compatibility

It works with many routers and older network devices.

### Low resource usage

RIP is relatively simple, so it does not require much CPU or memory.

### Loop prevention

The maximum hop count of **15** helps prevent routing loops from continuing forever.

---

# 7. Disadvantages of RIP

### Limited scalability

The maximum of 15 hops makes RIP unsuitable for large networks.

### Slow convergence

When the network changes, RIP can take time to learn the new network information.

**Convergence** means the time routers need to learn and agree on the new network situation.

### Simple metric

RIP mainly considers hop count.

For example:

```text
Path A: 2 hops, slow links
Path B: 3 hops, very fast links
```

RIP may choose Path A because it has fewer hops.

### Security limitations

RIPv1 does not have built-in authentication.

This means it cannot verify that routing updates come from a trusted source.

---

# 8. When is RIP Used?

RIP is mainly useful for:

### Small networks

Small networks with simple designs can use RIP.

### Learning and laboratories

RIP is very useful for learning **dynamic routing**.

It is a good protocol to understand before studying more advanced protocols such as:

* OSPF
* BGP

### Legacy networks

Some older networks may still use RIP because replacing the existing infrastructure may not be practical.

---

# 9. Important RIP Terms

| Term            | Easy meaning                                   |
| --------------- | ---------------------------------------------- |
| RIP             | Routing Information Protocol                   |
| Distance-vector | Routing method based on distance and direction |
| Hop             | One router crossed by a packet                 |
| Metric          | Value used to choose a route                   |
| Hop count       | Number of hops to a destination                |
| Convergence     | Time routers need to learn a network change    |
| RIPv1           | Original RIP version                           |
| RIPv2           | Improved IPv4 version                          |
| RIPng           | RIP version for IPv6                           |
| VLSM            | Using different subnet masks in a network      |
| Routing table   | Table containing routes                        |
| Neighbor        | Router directly connected to another router    |
| Dynamic routing | Routers automatically learn routes             |

---

# 10. RIP Process — Simple Flow

```text
Router starts RIP
       ↓
Learns directly connected networks
       ↓
Sends routing information
       ↓
Neighbor receives the update
       ↓
Adds 1 hop
       ↓
Compares routes
       ↓
Chooses the route with fewer hops
       ↓
Updates routing table
       ↓
Sends updated information
```

---

# 11. Key Points to Remember

* **RIP = Routing Information Protocol**
* RIP is a **dynamic routing protocol**.
* RIP uses the **distance-vector** approach.
* Its main metric is **hop count**.
* RIP prefers the route with the **fewest hops**.
* **15 hops** is the maximum reachable distance.
* **16 hops means unreachable**.
* RIP sends routing updates every **30 seconds**.
* **RIPv1** is classful.
* **RIPv2** supports classless routing and VLSM.
* **RIPng** supports IPv6.
* RIP is simple but has **slow convergence and poor scalability**.
* RIP is mainly useful for **small networks, labs, and learning**.
