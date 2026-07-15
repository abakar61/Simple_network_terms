# IP Address

## 📖 What is an IP Address?

An **IP Address (Internet Protocol Address)** is a unique numerical identifier assigned to every device connected to a network.

Just as every house has a unique postal address, every device on a network has an IP address so that data can be sent to the correct destination.

Without IP addresses, devices would not be able to communicate over the Internet or a local network.

---

# 🎯 Why is an IP Address Important?

An IP address allows devices to:

- Identify each other on a network.
- Send and receive data.
- Access websites and online services.
- Communicate across local and global networks.

Every device connected to the Internet, such as a computer, smartphone, printer, or router, requires an IP address.

---

# 💡 Real-World Example

Imagine you want to send a letter to your friend.

The postal service needs your friend's home address to deliver the letter.

Similarly, when you visit a website, your computer sends a request to the web server using its IP address.

The server then sends the requested webpage back to your IP address.

---

# How an IP Address Works

When you type:

```
www.google.com
```

The following happens:

1. DNS translates the domain name into an IP address.
2. Your computer sends a request to Google's IP address.
3. Google's server processes the request.
4. The webpage is sent back to your device.

Without IP addresses, this communication would not be possible.

---

# IPv4 Address

IPv4 (Internet Protocol Version 4) is the most commonly used IP addressing system.

An IPv4 address consists of **32 bits**, divided into **4 octets**.

Example:

```
192.168.1.10
```

Each octet ranges from:

```
0 to 255
```

---

# IPv6 Address

IPv6 (Internet Protocol Version 6) was created because the Internet is running out of IPv4 addresses.

IPv6 uses **128 bits**, allowing for a much larger number of unique addresses.

Example:

```
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

IPv6 supports billions of connected devices and is designed for the future of networking.

---

# Structure of an IPv4 Address

An IPv4 address contains two parts:

- **Network ID** – Identifies the network.
- **Host ID** – Identifies the device within that network.

Example:

```
192.168.1.10
```

- Network ID: 192.168.1
- Host ID: 10

---

# Binary Representation

Computers understand binary numbers.

Example:

Binary:

```
11000000.10101000.00000001.00001010
```

Decimal:

```
192.168.1.10
```

---

# Public IP Address

A **Public IP Address** is assigned by an Internet Service Provider (ISP).

It allows your network to communicate with devices on the Internet.

Example:

```
102.45.67.89
```

Characteristics:

- Unique across the Internet.
- Assigned by the ISP.
- Accessible from anywhere on the Internet.

---

# Private IP Address

A **Private IP Address** is used only inside a local network (LAN).

Private IP addresses cannot be accessed directly from the Internet.

Common private IP ranges:

| Address Range | Description |
|---------------|-------------|
| 10.0.0.0 – 10.255.255.255 | Class A Private |
| 172.16.0.0 – 172.31.255.255 | Class B Private |
| 192.168.0.0 – 192.168.255.255 | Class C Private |

Example:

```
192.168.1.100
```

---

# Public vs Private IP Address

| Public IP | Private IP |
|------------|------------|
| Accessible from the Internet | Used inside a local network |
| Assigned by ISP | Assigned by the router |
| Globally unique | Can be reused in different networks |
| Used for Internet communication | Used for local communication |

---

# IP Address Classes (IPv4)

Before CIDR, IPv4 addresses were divided into classes.

| Class | First Octet | Default Subnet Mask | Number of Hosts |
|--------|------------|--------------------|----------------|
| A | 1 – 126 | 255.0.0.0 | Over 16 Million |
| B | 128 – 191 | 255.255.0.0 | 65,534 |
| C | 192 – 223 | 255.255.255.0 | 254 |

Today, most modern networks use **CIDR (Classless Inter-Domain Routing)** instead of classes.

---

# CIDR Notation

CIDR is a modern method of writing IP addresses.

Example:

```
192.168.1.0/24
```

The **/24** means:

- 24 bits are used for the network.
- 8 bits are used for hosts.

CIDR makes IP address allocation more efficient.

---

# Common Uses of IP Addresses

IP addresses are used for:

- Web browsing
- Sending emails
- Video streaming
- Online gaming
- File sharing
- Cloud computing
- Remote access

---

# Security Considerations

Public IP addresses are visible to websites and online services.

Attackers may use public IP addresses to launch cyber attacks such as:

- DDoS (Distributed Denial of Service)
- Port scanning
- Unauthorized access attempts

For this reason, organizations use firewalls, VPNs, and intrusion prevention systems to protect their networks.

---

# Advantages of IP Addresses

- Enable communication between devices.
- Identify devices uniquely.
- Support Internet access.
- Allow routing of data across networks.
- Enable modern cloud and online services.

---

# Key Points

- An IP address uniquely identifies a device on a network.
- IPv4 uses 32 bits.
- IPv6 uses 128 bits.
- IP addresses contain a Network ID and a Host ID.
- Public IP addresses communicate over the Internet.
- Private IP addresses are used inside local networks.
- CIDR is the modern method of IP addressing.

---

# Conclusion

An IP address is one of the most fundamental concepts in computer networking. It enables devices to identify one another and exchange information across local networks and the Internet. Understanding IPv4, IPv6, public and private IP addresses, and CIDR notation is essential for anyone learning networking, cybersecurity, or cloud computing.