---
title: Network Layer and IP Addressing
module_number: 4
description: IP addressing, subnetting, routing, and network layer protocols
---

## Overview

The Network Layer (Layer 3) is responsible for routing packets from source to destination across multiple networks. This module covers IP addressing, subnetting, and routing fundamentals.

## Learning Objectives

After completing this module, you should be able to:

- Understand IPv4 and IPv6 addressing
- Perform subnetting calculations
- Explain routing concepts and algorithms
- Describe network layer protocols (IP, ICMP, ARP)
- Understand NAT and its applications

## Internet Protocol (IP)

IP is the primary network layer protocol for the Internet.

### IP Functions

- Logical addressing (IP addresses)
- Packet routing
- Fragmentation and reassembly
- Best-effort delivery (unreliable)

## IPv4 Addressing

IPv4 uses 32-bit addresses, written in dotted-decimal notation.

### IPv4 Address Format

- 32 bits divided into 4 octets
- Example: `192.168.1.100`
- Binary: `11000000.10101000.00000001.01100100`

### IPv4 Address Classes

| Class | First Octet | Default Mask | Network/Host Bits | Range |
|-------|-------------|--------------|-------------------|-------|
| A | 1-126 | 255.0.0.0 (/8) | 8/24 | 1.0.0.0 - 126.255.255.255 |
| B | 128-191 | 255.255.0.0 (/16) | 16/16 | 128.0.0.0 - 191.255.255.255 |
| C | 192-223 | 255.255.255.0 (/24) | 24/8 | 192.0.0.0 - 223.255.255.255 |
| D | 224-239 | N/A | Multicast | 224.0.0.0 - 239.255.255.255 |
| E | 240-255 | N/A | Reserved | 240.0.0.0 - 255.255.255.255 |

### Special IP Addresses

- **Loopback**: `127.0.0.1` - refers to local machine
- **Private Addresses**:
  - Class A: `10.0.0.0/8`
  - Class B: `172.16.0.0/12`
  - Class C: `192.168.0.0/16`
- **APIPA**: `169.254.0.0/16` - automatic private addressing
- **Broadcast**: Last address in subnet (all host bits = 1)
- **Network Address**: First address in subnet (all host bits = 0)

## Subnet Masks

A subnet mask separates the network portion from the host portion of an IP address.

### CIDR Notation

- Classless Inter-Domain Routing
- Example: `192.168.1.0/24`
- `/24` means first 24 bits are network portion

### Common Subnet Masks

| CIDR | Subnet Mask | Host Bits | Number of Hosts |
|------|-------------|-----------|-----------------|
| /8 | 255.0.0.0 | 24 | 16,777,214 |
| /16 | 255.255.0.0 | 16 | 65,534 |
| /24 | 255.255.255.0 | 8 | 254 |
| /25 | 255.255.255.128 | 7 | 126 |
| /26 | 255.255.255.192 | 6 | 62 |
| /27 | 255.255.255.224 | 5 | 30 |
| /28 | 255.255.255.240 | 4 | 14 |
| /30 | 255.255.255.252 | 2 | 2 |

## Subnetting

Subnetting divides a network into smaller subnetworks.

### Subnetting Example

Given: `192.168.1.0/24`, create 4 subnets

**Solution**:
- Need 2 bits for 4 subnets (2² = 4)
- New mask: /26 (255.255.255.192)
- Each subnet has 64 addresses (2⁶)

**Subnets**:
1. `192.168.1.0/26` (0-63)
2. `192.168.1.64/26` (64-127)
3. `192.168.1.128/26` (128-191)
4. `192.168.1.192/26` (192-255)

### Subnetting Steps

1. Determine number of subnets needed
2. Calculate bits needed (2ⁿ ≥ subnets)
3. Calculate new subnet mask
4. Calculate subnet ranges
5. Identify network, broadcast, and usable host addresses

## IPv6

IPv6 uses 128-bit addresses to solve IPv4 exhaustion.

### IPv6 Address Format

- 128 bits (16 bytes)
- Written as 8 groups of 4 hexadecimal digits
- Example: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`

### IPv6 Address Abbreviation

- Leading zeros can be omitted: `2001:db8:85a3:0:0:8a2e:370:7334`
- Consecutive zero groups can be replaced with `::` (once only)
- Example: `2001:db8::1`

### IPv6 Address Types

- **Unicast**: Single interface
  - Global unicast: Internet-routable (2000::/3)
  - Link-local: Same link (fe80::/10)
  - Loopback: ::1
- **Multicast**: Group of interfaces (ff00::/8)
- **Anycast**: Nearest of multiple interfaces

## Routing

Routing is the process of forwarding packets from source to destination.

### Routing Concepts

- **Router**: Device that forwards packets between networks
- **Routing Table**: Database of network paths
- **Next Hop**: Next router on path to destination
- **Metric**: Cost of a route (hops, bandwidth, delay)

### Routing Table Entries

- **Destination Network**: Network address
- **Subnet Mask**: Network mask
- **Next Hop**: Router IP or interface
- **Metric**: Route cost
- **Interface**: Outgoing interface

### Types of Routing

**1. Static Routing**
- Manually configured routes
- Simple, predictable
- No overhead
- Not scalable

**2. Dynamic Routing**
- Routes learned automatically via protocols
- Adapts to network changes
- More complex
- Scalable

### Routing Protocols

**Distance Vector Protocols**
- RIP (Routing Information Protocol)
- Uses hop count as metric
- Bellman-Ford algorithm
- Periodic updates

**Link State Protocols**
- OSPF (Open Shortest Path First)
- Each router has complete topology
- Dijkstra's algorithm
- Event-triggered updates

**Path Vector Protocol**
- BGP (Border Gateway Protocol)
- Used between autonomous systems
- Internet backbone routing

## Network Address Translation (NAT)

NAT translates private IP addresses to public IP addresses.

### Types of NAT

**1. Static NAT**
- One-to-one mapping
- Private IP ↔ Public IP

**2. Dynamic NAT**
- Pool of public IPs
- First-come, first-served

**3. Port Address Translation (PAT) / NAT Overload**
- Many-to-one with port numbers
- Most common type
- Enables multiple devices to share one public IP

### NAT Benefits

- Conserves public IP addresses
- Provides security (hides internal network)
- Simplifies network management

### NAT Drawbacks

- Breaks end-to-end connectivity
- Complicates some protocols
- Adds latency

## Additional Protocols

### ICMP (Internet Control Message Protocol)

- Error reporting and diagnostic protocol
- Used by `ping` and `traceroute`
- Common messages:
  - Echo Request/Reply (ping)
  - Destination Unreachable
  - Time Exceeded
  - Redirect

### ARP (Address Resolution Protocol)

- Maps IP addresses to MAC addresses
- Broadcasts ARP request
- Target responds with MAC address
- Cached in ARP table

## Summary

The network layer provides logical addressing and routing capabilities essential for internetworking. Understanding IP addressing, subnetting, and routing is fundamental to network design and troubleshooting.

## Key Terms

- **IP Address**: Logical network address
- **Subnet**: Logical subdivision of a network
- **Gateway**: Default router for a network
- **TTL (Time to Live)**: Hop limit for packets
- **Fragmentation**: Breaking packets into smaller pieces

## Exercises

1. Subnet `172.16.0.0/16` into 8 equal subnets
2. Calculate the broadcast address for `10.5.12.50/22`
3. Convert IPv6 address to shortest form: `2001:0db8:0000:0000:0000:0000:0000:0001`
4. Draw a routing table for a three-router network
5. Explain how NAT allows multiple devices to share one public IP
