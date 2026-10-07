# BGP – Border Gateway Protocol

## 1. What is BGP?

BGP stands for **Border Gateway Protocol**.

BGP is the routing protocol used to exchange routing information between different **Autonomous Systems (ASes)** on the Internet.

The Internet is a **network of networks**, and BGP helps these networks decide which path should be used to reach a destination.

A simple way to remember BGP:

> **BGP is like the postal service of the Internet.**

Just as the postal service chooses where mail should go, BGP helps routers choose where network traffic should go.

---

## 2. What is an Autonomous System?

An **Autonomous System (AS)** is a large network or group of networks operated by a single organization.

Examples of organizations that can operate an AS include:

* Internet Service Providers (ISPs)
* Technology companies
* Universities
* Government organizations
* Scientific institutions

Each AS has an **Autonomous System Number (ASN)**.

The ASN identifies the AS when exchanging routing information with other networks.

The Internet can therefore be viewed as:

```text
Internet
   |
   +-- AS1
   |
   +-- AS2
   |
   +-- AS3
   |
   +-- AS4
```

BGP allows these different autonomous systems to exchange routes.

---

## 3. How BGP Selects a Path

A destination can sometimes be reached through multiple autonomous systems.

For example:

```text
AS1 → AS2 → AS3
```

or:

```text
AS1 → AS6 → AS5 → AS4 → AS3
```

BGP uses different **path attributes** to decide which route should be preferred.

Therefore, BGP does not simply choose a route because it has fewer physical hops.

It uses a set of routing attributes and policies to select the preferred path.

---

## 4. BGP Peering

BGP routers establish **peering sessions** with neighboring networks.

These sessions allow autonomous systems to exchange routing information.

BGP uses **TCP** to establish its routing sessions.

Through these sessions, routers learn:

* New routes
* Available paths
* Changes to routes
* Routes that are no longer available

This information allows BGP routers to keep their routing information updated.

---

## 5. External BGP and Internal BGP

There are two main types of BGP:

### eBGP

**eBGP = External BGP**

eBGP is used to exchange routing information between different autonomous systems.

Example:

```text
AS100              AS200

Router A -------- Router B
        eBGP
```

### iBGP

**iBGP = Internal BGP**

iBGP is used to exchange BGP routing information between routers **inside the same autonomous system**.

Example:

```text
        AS100
   +-------------+
   |             |
Router A ------ Router B
       iBGP
```

An organization using eBGP does not necessarily have to use iBGP. It can use another internal routing protocol inside its AS.

---

## 6. BGP Attributes

BGP uses **attributes** to help select the preferred path when multiple routes are available.

Important attributes include:

### Weight

Weight is a **Cisco-proprietary attribute**.

It is used to indicate which local path a Cisco router should prefer.

### Local Preference

Local preference helps determine which **outbound path** an AS should use.

### Origin

Origin helps indicate how a route was introduced into BGP.

### AS Path Length

AS Path Length represents the number of autonomous systems in the path.

BGP generally prefers a shorter AS path when other relevant attributes are equal.

---

## 7. BGP Route Selection

BGP considers path attributes in a specific order.

For example, a Cisco router can consider:

```text
1. Weight
2. Local Preference
3. Route Origin
4. AS Path Length
5. Other BGP attributes
```

The exact route-selection process contains additional steps and attributes.

The important idea is:

> **BGP uses path attributes and routing policies to choose a preferred path.**

---

## 8. BGP and Business Policies

BGP path selection is not based only on technical distance.

Autonomous systems are operated by different organizations, and they can have business relationships with each other.

For example:

```text
Network A
    |
    | traffic
    ↓
Network B
```

An organization may prefer one network connection over another because of cost, business agreements, or routing policy.

Therefore, BGP is both a **routing protocol** and a way to apply routing policies between networks.

---

## 9. BGP Security Problems

BGP traditionally relies heavily on trust between networks.

A network can accidentally or intentionally advertise incorrect routing information.

This can cause traffic to be sent through an incorrect path.

This type of problem is commonly called **BGP hijacking** when incorrect route announcements cause traffic to be redirected.

Possible consequences include:

* Traffic redirection
* Denial of service
* Traffic interception
* Phishing
* Impersonation
* Data manipulation

---

## 10. BGP Hijacking

**BGP hijacking** occurs when an unauthorized or incorrect BGP route announcement causes traffic to be redirected.

For example:

```text
Normal:

User → AS1 → AS2 → Website


Incorrect route:

User → AS1 → Attacker → Wrong destination
```

The attacker or incorrectly configured network can potentially receive traffic that was intended for another network.

BGP hijacking can happen accidentally or deliberately.

---

## 11. RPKI

**RPKI** stands for **Resource Public Key Infrastructure**.

RPKI is a security framework used to help validate BGP route announcements.

It uses cryptographically signed records called **Route Origin Authorizations (ROAs)**.

A ROA can indicate which network operator is authorized to announce a particular IP prefix.

The basic idea is:

```text
IP Prefix
   |
   ↓
ROA
   |
   ↓
Authorized Network
```

This helps networks identify unauthorized route announcements.

---

## 12. Key BGP Terms

| Term             | Meaning                                                       |
| ---------------- | ------------------------------------------------------------- |
| BGP              | Border Gateway Protocol                                       |
| AS               | Autonomous System                                             |
| ASN              | Autonomous System Number                                      |
| eBGP             | BGP between different ASes                                    |
| iBGP             | BGP inside the same AS                                        |
| Peering          | BGP relationship between neighboring networks                 |
| Weight           | Cisco-proprietary BGP attribute                               |
| Local Preference | Helps select outbound paths                                   |
| AS Path          | List of ASes in a BGP path                                    |
| AS Path Length   | Number of ASes in the path                                    |
| BGP Hijacking    | Incorrect/unauthorized route advertisement                    |
| RPKI             | Framework for validating BGP route announcements              |
| ROA              | Record identifying an authorized network to announce a prefix |

---

## 13. Simple Summary

```text
BGP
 |
 +-- Exchanges routes between Autonomous Systems
 |
 +-- Uses TCP for BGP sessions
 |
 +-- Uses path attributes to select routes
 |
 +-- eBGP → between different ASes
 |
 +-- iBGP → inside the same AS
 |
 +-- Can apply routing and business policies
 |
 +-- Can be affected by incorrect route advertisements
 |
 +-- RPKI helps improve BGP security
```

### Remember

**BGP is the routing protocol that allows different autonomous systems to exchange routing information and select preferred paths across the Internet.**
