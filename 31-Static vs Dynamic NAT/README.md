# Static NAT and Dynamic NAT Lab

## Introduction

Network Address Translation (NAT) changes IP address information in packets as they pass through a routing device. NAT is mainly used to translate private IP addresses into public IP addresses and hide internal IP addresses from external networks.

There are two main types of NAT covered in this lab:

- Static NAT
- Dynamic NAT

## 1. Static NAT

Static NAT creates a permanent one-to-one mapping between a private IP address and a public IP address.

Example:

    Private IP                 Public IP
    192.168.1.10  ----------> 203.0.113.10

The internal device 192.168.1.10 will always be mapped to 203.0.113.10.

### Common Uses

Static NAT is commonly used for devices that need a permanent public address, such as:

- Web servers
- Email servers
- FTP servers
- Other services that need external access

## 2. Dynamic NAT

Dynamic NAT uses a pool of public IP addresses. A private IP address is temporarily mapped to an available public IP address from the pool.

Example:

    Private Network              Public NAT Pool

    192.168.1.10  ------------> 203.0.113.10
    192.168.1.11  ------------> 203.0.113.11
    192.168.1.12  ------------> 203.0.113.12

The public address is assigned dynamically when the internal device communicates with an external network.

## 3. Static NAT vs Dynamic NAT

| Feature | Static NAT | Dynamic NAT |
|---|---|---|
| Mapping | One-to-one | From a public IP pool |
| Mapping type | Permanent | Temporary |
| Public IP | Fixed | Can change |
| Common use | Servers | Client devices |
| External access | Fixed mapping can allow external access | Mainly used for outbound access |
| Public IP requirement | One public IP for each mapped device | Uses a pool of public IP addresses |

## 4. Lab Topology

    PC1 ----------------\
    PC2 ----------------- SW1 -------- R1 -------- Internet/ISP
    PC3 ----------------/

    LAN Network: 192.168.1.0/24

    R1 G0/0 = Inside interface
    R1 G0/1 = Outside interface

## 5. IP Addressing

    R1 G0/0 = 192.168.1.1/24
    R1 G0/1 = 203.0.113.2/24

    PC1 = 192.168.1.10/24
    PC2 = 192.168.1.11/24
    PC3 = 192.168.1.12/24

    Default Gateway for PCs = 192.168.1.1

## 6. NAT Terminology

### Inside Local

The private IP address of an internal device.

Example:

    192.168.1.10

### Inside Global

The public IP address that represents the internal device after NAT.

Example:

    203.0.113.10

### Outside Global

The public IP address of the external destination.

Example:

    8.8.8.8

### Inside Interface

The router interface connected to the private LAN.

Example:

    G0/0

### Outside Interface

The router interface connected to the external network.

Example:

    G0/1

## 7. Configure the Inside Interface

    R1(config)# interface g0/0
    R1(config-if)# ip address 192.168.1.1 255.255.255.0
    R1(config-if)# ip nat inside
    R1(config-if)# no shutdown

### Explanation

    interface g0/0

Selects the LAN-facing interface.

    ip address 192.168.1.1 255.255.255.0

Assigns the router's private LAN address.

    ip nat inside

Tells the router that this interface is connected to the inside network.

    no shutdown

Turns the interface on.

## 8. Configure the Outside Interface

    R1(config)# interface g0/1
    R1(config-if)# ip address 203.0.113.2 255.255.255.0
    R1(config-if)# ip nat outside
    R1(config-if)# no shutdown

### Explanation

    ip nat outside

Tells the router that this interface is connected to the outside network.

## 9. Configure Static NAT

Suppose PC1 has:

    Private IP = 192.168.1.10
    Public IP  = 203.0.113.10

Configure the following command:

    R1(config)# ip nat inside source static 192.168.1.10 203.0.113.10

This creates the permanent mapping:

    192.168.1.10 <------> 203.0.113.10

## 10. Verify Static NAT

Use:

    R1# show ip nat translations

You should see a translation similar to:

    Pro  Inside global       Inside local
    ---  203.0.113.10        192.168.1.10

You can also check NAT statistics:

    R1# show ip nat statistics

## 11. Configure Dynamic NAT

Dynamic NAT uses a pool of public IP addresses.

Example public pool:

    203.0.113.10 - 203.0.113.20

## 12. Create the Dynamic NAT Pool

    R1(config)# ip nat pool PUBLIC_POOL 203.0.113.10 203.0.113.20 netmask 255.255.255.0

### Explanation

    ip nat pool

Creates a pool of public IP addresses.

    PUBLIC_POOL

The name of the NAT pool.

    203.0.113.10 203.0.113.20

Defines the first and last public IP addresses in the pool.

    netmask 255.255.255.0

Defines the subnet mask.

## 13. Create an ACL for the Inside Network

Create an ACL that identifies which internal devices can use Dynamic NAT:

    R1(config)# access-list 1 permit 192.168.1.0 0.0.0.255

This allows the 192.168.1.0/24 network to use the NAT pool.

## 14. Connect the ACL to the NAT Pool

    R1(config)# ip nat inside source list 1 pool PUBLIC_POOL

This tells the router:

    Traffic matching ACL 1
            |
            v
    Use PUBLIC_POOL
            |
            v
    Translate the private IP
    into a public IP

## 15. Complete Dynamic NAT Configuration

    R1(config)# access-list 1 permit 192.168.1.0 0.0.0.255

    R1(config)# ip nat pool PUBLIC_POOL 203.0.113.10 203.0.113.20 netmask 255.255.255.0

    R1(config)# ip nat inside source list 1 pool PUBLIC_POOL

The interfaces must also have NAT inside and NAT outside configured:

    R1(config)# interface g0/0
    R1(config-if)# ip address 192.168.1.1 255.255.255.0
    R1(config-if)# ip nat inside
    R1(config-if)# no shutdown

    R1(config)# interface g0/1
    R1(config-if)# ip address 203.0.113.2 255.255.255.0
    R1(config-if)# ip nat outside
    R1(config-if)# no shutdown

## 16. Test Dynamic NAT

Generate traffic from an internal PC toward an external destination.

Example:

    PC1
    192.168.1.10
         |
         v
        R1
         |
         v
    External Network

Then check:

    R1# show ip nat translations

Example result:

    Pro  Inside global       Inside local
    ---  203.0.113.10        192.168.1.10

Another internal device may receive another public address:

    Pro  Inside global       Inside local
    ---  203.0.113.11        192.168.1.11

## 17. Static NAT Example

    Private IP
    192.168.1.10
          |
          | Permanent mapping
          v
    Public IP
    203.0.113.10

Static NAT always keeps this mapping unless the configuration is changed.

## 18. Dynamic NAT Example

    Private IP
    192.168.1.10
          |
          | Temporary assignment
          v
    +----------------------+
    | Public NAT Pool      |
    | 203.0.113.10         |
    | 203.0.113.11         |
    | 203.0.113.12         |
    | 203.0.113.13         |
    +----------------------+

The router selects an available address from the pool.

## 19. Verification Commands

### Check NAT translations

    R1# show ip nat translations

Shows the current NAT mappings.

### Check NAT statistics

    R1# show ip nat statistics

Shows NAT statistics and NAT configuration information.

### Check interface status

    R1# show ip interface brief

Shows interface IP addresses and whether interfaces are up or down.

### Check the running configuration

    R1# show running-config

Displays the current router configuration.

### Check the ACL

    R1# show access-lists

Shows the configured ACL and its matching counters.

## 20. Clear NAT Translations

To clear dynamic NAT translations:

    R1# clear ip nat translation *

This removes the current dynamic NAT translation entries.

## 21. Troubleshooting

### Problem 1: NAT Translation Does Not Appear

Check:

    R1# show ip nat translations

Then check:

    R1# show ip nat statistics

Also check the configuration:

    R1# show running-config

Make sure the inside interface contains:

    ip nat inside

And the outside interface contains:

    ip nat outside

### Problem 2: ACL Does Not Match

Check:

    R1# show access-lists

Make sure the ACL contains the correct internal network:

    access-list 1 permit 192.168.1.0 0.0.0.255

### Problem 3: Interface Is Down

Check:

    R1# show ip interface brief

If the interface is administratively down:

    R1(config)# interface g0/0
    R1(config-if)# no shutdown

### Problem 4: PC Cannot Reach the Router

Check the PC configuration.

Example:

    IP Address:      192.168.1.10
    Subnet Mask:     255.255.255.0
    Default Gateway: 192.168.1.1

Test connectivity:

    ping 192.168.1.1

## 22. Important Note About PAT

Dynamic NAT and PAT are not exactly the same.

Dynamic NAT normally maps private addresses to public addresses from a configured pool.

PAT, also called NAT overload, allows many private devices to share one public IP address by using different port numbers.

Example:

    PC1 192.168.1.10 ----\
    PC2 192.168.1.11 -----+----> 203.0.113.2
    PC3 192.168.1.12 ----/

PAT is commonly used when many internal users need Internet access but there are only a small number of public IPv4 addresses.

## 23. Quick Comparison

### Static NAT

    Private IP
        |
        | Permanent mapping
        v
    Public IP

    Example:
    192.168.1.10 ---> 203.0.113.10

### Dynamic NAT

    Private IP
        |
        | Temporary assignment
        v
    Public IP Pool

    Example:
    192.168.1.10 ---> 203.0.113.10
    192.168.1.11 ---> 203.0.113.11
    192.168.1.12 ---> 203.0.113.12

## 24. Key Takeaways

1. NAT translates IP addresses between networks.
2. Static NAT creates a permanent one-to-one mapping.
3. Dynamic NAT assigns public addresses from a pool.
4. Static NAT is useful for servers that need a fixed public mapping.
5. Dynamic NAT is useful when internal devices need temporary public addresses.
6. `ip nat inside` identifies the inside interface.
7. `ip nat outside` identifies the outside interface.
8. `ip nat inside source static` creates a Static NAT mapping.
9. `ip nat pool` creates a Dynamic NAT public address pool.
10. `show ip nat translations` displays current NAT translations.
11. `show ip nat statistics` displays NAT statistics.
12. PAT allows many devices to share one public IP by using different port numbers.

## 25. Final Verification Checklist

    [ ] Inside interface configured
    [ ] Outside interface configured
    [ ] Inside interface has "ip nat inside"
    [ ] Outside interface has "ip nat outside"
    [ ] Static NAT mapping configured OR Dynamic NAT pool configured
    [ ] ACL configured for Dynamic NAT
    [ ] NAT rule connected to the ACL and pool
    [ ] PC has the correct IP address
    [ ] PC has the correct default gateway
    [ ] Interfaces are up
    [ ] Connectivity tested
    [ ] show ip nat translations checked
    [ ] show ip nat statistics checked

## Conclusion

Static NAT provides a fixed mapping between a private IP address and a public IP address, while Dynamic NAT assigns public IP addresses temporarily from a configured pool. Understanding both methods is important for configuring, verifying, and troubleshooting IPv4 networks.