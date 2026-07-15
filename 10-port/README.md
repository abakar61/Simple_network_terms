# Network Port

## 📖 What is a Network Port?

A **network port** is a virtual communication endpoint used by computers to send and receive data over a network.

Ports are software-based and are managed by the operating system. They allow a single computer to run multiple network services at the same time.

Each network service or application uses a specific port number to identify itself.

---

# 🎯 Why are Ports Important?

Ports help computers determine which application or service should receive incoming data.

For example:

- Web traffic goes to the web browser.
- Emails go to the email application.
- File transfers go to the FTP application.

Without ports, a computer would not know which program should process the received data.

---

# 💡 Real-World Example

Imagine an apartment building.

- The building's address is like an **IP Address**.
- Each apartment number is like a **Port Number**.

The mail carrier first finds the correct building (IP Address), then delivers the letter to the correct apartment (Port Number).

Similarly:

- IP Address identifies the computer.
- Port Number identifies the application running on that computer.

---

# What is a Port Number?

A **port number** is a unique number assigned to a specific service or application.

Port numbers range from:

```
0 – 65535
```

Each port is associated with a particular protocol or network service.

---

# Port Number Ranges

There are three categories of port numbers.

| Range | Name | Description |
|--------|----------------|-------------------------------|
| 0–1023 | Well-Known Ports | Used by common services |
| 1024–49151 | Registered Ports | Used by applications |
| 49152–65535 | Dynamic (Private) Ports | Temporary ports used by clients |

---

# Common Port Numbers

| Port | Protocol | Purpose |
|------:|----------|--------------------------------|
| 20 | FTP | Data Transfer |
| 21 | FTP | File Transfer Control |
| 22 | SSH | Secure Remote Login |
| 23 | Telnet | Remote Login (Not Secure) |
| 25 | SMTP | Sending Email |
| 53 | DNS | Domain Name Resolution |
| 67 | DHCP | DHCP Server |
| 68 | DHCP | DHCP Client |
| 69 | TFTP | Trivial File Transfer |
| 80 | HTTP | Web Browsing |
| 110 | POP3 | Receiving Email |
| 123 | NTP | Time Synchronization |
| 143 | IMAP | Email Access |
| 161 | SNMP | Network Monitoring |
| 162 | SNMP Trap | Alert Messages |
| 179 | BGP | Border Gateway Protocol |
| 443 | HTTPS | Secure Web Browsing |
| 500 | ISAKMP | IPsec VPN |
| 587 | SMTP Secure | Secure Email Sending |
| 3389 | RDP | Remote Desktop |

---

# Ports in the OSI Model

Ports operate at the **Transport Layer (Layer 4)** of the OSI Model.

The transport protocols that use ports are:

- TCP
- UDP

The Network Layer (IP) identifies the destination device.

The Transport Layer identifies the destination application.

---

# TCP and UDP Ports

## TCP

TCP provides:

- Reliable communication
- Error checking
- Packet ordering
- Connection-oriented communication

Examples:

- HTTP
- HTTPS
- SSH
- FTP

---

## UDP

UDP provides:

- Faster communication
- No error checking
- Connectionless communication

Examples:

- DNS
- DHCP
- VoIP
- Online Gaming
- Video Streaming

---

# How Ports Work

Suppose you open your web browser and visit:

```
https://www.google.com
```

The communication happens like this:

1. Your browser sends a request.
2. DNS resolves the domain name.
3. TCP establishes a connection.
4. The request is sent to **Port 443**.
5. Google's web server responds.

The browser knows to use Port 443 because HTTPS uses that standard port.

---

# Why Do Firewalls Block Ports?

A firewall protects a network by allowing or blocking traffic based on port numbers.

For example:

Allow:

- Port 80 (HTTP)
- Port 443 (HTTPS)
- Port 53 (DNS)

Block:

- Port 23 (Telnet)
- Port 3389 (RDP) if remote access is not needed

Blocking unused ports reduces the risk of cyber attacks.

---

# Real-World Example

Suppose a company has a web server.

The firewall may allow:

```
Port 80
Port 443
```

But block:

```
Port 21
Port 23
Port 3389
```

This improves network security by reducing unnecessary access.

---

# Difference Between IP Address and Port Number

| IP Address | Port Number |
|------------|-------------|
| Identifies a device | Identifies an application |
| Layer 3 | Layer 4 |
| Example: 192.168.1.10 | Example: 80 |
| Used for routing | Used for delivering data to the correct service |

---

# Advantages of Using Ports

- Allow multiple applications to communicate simultaneously.
- Organize network traffic efficiently.
- Enable specific network services.
- Improve communication between devices.
- Support network security through firewalls.

---

# Key Points

- A network port is a virtual communication endpoint.
- Port numbers identify specific applications or services.
- Ports range from 0 to 65535.
- TCP and UDP use port numbers.
- Firewalls use ports to control network access.
- Ports work together with IP addresses to deliver data correctly.

---

# Conclusion

Network ports are an essential part of computer networking. While an IP address identifies the destination device, a port number identifies the specific service or application on that device. Understanding ports helps network engineers configure services, troubleshoot connectivity issues, and improve network security.