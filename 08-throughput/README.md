# Throughput vs Latency in Computer Networks 🌐⚡

## Overview

Network performance depends on many factors, but two of the most important measurements are:

- **Latency**
- **Throughput**

Both determine how efficiently data moves through a network, but they measure different things.

---

# What is Network Latency? ⏱️

**Latency** is the delay that occurs when data travels from a source to a destination.

It measures how long a packet takes to move across a network.

Latency is measured in:

```
Milliseconds (ms)
```

Example:

```
Client → Server

Low latency:
10 ms

High latency:
500 ms
```

### Low latency means:

✅ Faster response time  
✅ Better user experience  
✅ Improved real-time communication  

### High latency causes:

❌ Slow applications  
❌ Delayed responses  
❌ Poor performance  

---

# What is Network Throughput? 📊

**Throughput** is the actual amount of data successfully transferred through a network during a specific time period.

It measures:

- Number of packets successfully delivered
- Actual data transfer rate
- Network performance in real conditions

Throughput is measured in:

- Bits per second (bps)
- Kilobits per second (Kbps)
- Megabits per second (Mbps)
- Gigabits per second (Gbps)

Example:

```
Network bandwidth: 100 Mbps

Actual throughput: 80 Mbps
```

The difference occurs because of:

- Network congestion
- Packet loss
- Protocol overhead
- Device limitations

---

# Why Are Latency and Throughput Important? ⭐

Network speed depends on both latency and throughput.

## Latency affects:

- Response time
- User experience
- Real-time communication

## Throughput affects:

- Amount of data transferred
- Number of users supported
- Network capacity

A high-performance network has:

```
Low Latency + High Throughput
```

Example:

```
Video conference
Online gaming
IoT systems
Cloud applications
```

require both high throughput and low latency.

---

# Key Differences: Latency vs Throughput ⚖️

| Feature | Latency | Throughput |
|---|---|---|
| Meaning | Delay in data transmission | Amount of data successfully transferred |
| Measures | Time taken by data | Data volume transferred |
| Unit | Milliseconds (ms) | Mbps, Gbps, MBps |
| Test Method | Ping / RTT | Network testing tools |
| Goal | Reduce delay | Increase data transfer |

---

# Measuring Latency 📏

The common method to measure latency is the **Ping command**.

Example:

```bash
ping 8.8.8.8
```

Output:

```
64 bytes from 8.8.8.8:
time=20 ms
```

The value represents the:

```
Round Trip Time (RTT)
```

Meaning:

```
Device → Destination → Device
```

---

# Measuring Throughput 📈

Throughput can be measured using:

- Network testing tools
- File transfer tests

Example:

Sending a file:

```
File size = 100 MB

Transfer time = 10 seconds

Throughput = 10 MB/s
```

---

# Factors Affecting Latency 🔍

## 1. Distance

The longer the physical distance, the higher the latency.

Example:

```
User in Africa
       |
       |
Server in America
```

Data travels a longer distance.

---

## 2. Network Congestion

Too much traffic causes delays.

Example:

```
Many users
     ↓
Traffic congestion
     ↓
Higher latency
```

---

## 3. Protocol Efficiency

Some protocols require additional steps.

Example:

TCP uses:

- Connection establishment
- Error checking
- Retransmission

These increase delay.

---

## 4. Network Infrastructure

Overloaded devices can increase latency.

Examples:

- Routers
- Switches
- Firewalls

---

# Factors Affecting Throughput 🚀

## 1. Bandwidth

Bandwidth limits the maximum possible throughput.

Example:

```
Bandwidth = 100 Mbps

Throughput cannot exceed 100 Mbps
```

---

## 2. Processing Power

Network devices with better hardware process packets faster.

Examples:

- High-performance routers
- Specialized network processors

---

## 3. Packet Loss

Lost packets must be retransmitted.

Effects:

- More delay
- Lower throughput
- Poor performance

---

## 4. Network Topology

A good network design improves throughput.

A good topology provides:

- Multiple paths
- Less congestion
- Efficient communication

---

# Relationship Between Bandwidth, Latency, and Throughput 🔗

These three concepts work together.

## Bandwidth

The maximum capacity of a network.

Example:

```
1 Gbps connection
```

---

## Throughput

The actual data transferred.

Example:

```
1 Gbps bandwidth

Actual throughput:
700 Mbps
```

---

## Latency

The delay during transmission.

Example:

```
10 ms delay
```

---

Analogy:

Imagine a highway:

```
Bandwidth = Number of lanes

Latency = Time taken for a car to travel

Throughput = Number of cars reaching the destination
```

---

# How to Improve Latency and Throughput 🔧

## 1. Use Caching

Store frequently used data closer to users.

Examples:

- Proxy servers
- Content Delivery Networks (CDNs)

Benefits:

- Lower latency
- Higher throughput

---

## 2. Optimize Transport Protocols

Two common protocols:

## TCP

Advantages:

✅ Reliable delivery  
✅ Error checking  

Disadvantages:

❌ Higher latency

Used for:

- Web browsing
- File transfer
- Email

---

## UDP

Advantages:

✅ Low latency  
✅ Faster transmission

Disadvantages:

❌ No delivery guarantee

Used for:

- Online gaming
- Video streaming
- Voice calls

---

# 3. Quality of Service (QoS)

QoS manages network traffic by assigning priorities.

Example:

High priority:

```
VoIP calls
Video conferences
Business applications
```

Low priority:

```
Large downloads
Background traffic
```

Benefits:

- Reduces delay
- Improves throughput
- Prevents congestion

---

# Real-World Example 🌍

When watching an online video:

## High Latency

```
Video request
      |
      ↓
Long delay
      |
      ↓
Buffering
```

## High Throughput + Low Latency

```
Fast response
      |
      ↓
Smooth streaming
```

---

# Summary Table 📋

| | Throughput | Latency |
|-|-|-|
| Measures | Data volume transferred | Data delay |
| Unit | Mbps / Gbps | Milliseconds |
| High Value | Good | Bad |
| Low Value | Bad | Good |
| Affected By | Bandwidth, packet loss, topology | Distance, congestion, protocols |
| Testing Tool | Speed tests, file transfer | Ping |

---

# Conclusion

Latency and throughput are two essential network performance measurements.

A good network should have:

```
High Throughput
+
Low Latency
=
High Performance Network
```

Network engineers monitor and optimize both factors to provide:

✅ Faster applications  
✅ Better user experience  
✅ Reliable communication  
✅ Efficient network operations  

---

## Author

Created as part of my networking learning journey.