---
title: Introduction to Computer Networks
module_number: 1
description: Fundamental concepts of computer networking, network architecture, and the OSI model
---

## Overview

This module introduces the fundamental concepts of computer networking, including network types, topologies, and the layered architecture approach.

## Learning Objectives

After completing this module, you should be able to:

- Define what a computer network is and explain its purpose
- Identify different types of networks (LAN, WAN, MAN, PAN)
- Understand network topologies and their characteristics
- Explain the OSI and TCP/IP models
- Describe the function of each layer in the network architecture

## What is a Computer Network?

A **computer network** is a collection of interconnected computing devices that can exchange data and share resources. Networks enable communication and resource sharing between computers, servers, and other devices.

### Types of Networks

1. **Personal Area Network (PAN)**
   - Short-range network (typically within 10 meters)
   - Examples: Bluetooth connections, USB connections
   - Used for personal devices

2. **Local Area Network (LAN)**
   - Covers a small geographic area (building or campus)
   - High data transfer rates
   - Typically owned by a single organization

3. **Metropolitan Area Network (MAN)**
   - Spans a city or metropolitan area
   - Connects multiple LANs
   - Examples: Cable TV networks, city-wide Wi-Fi

4. **Wide Area Network (WAN)**
   - Covers large geographic areas (countries, continents)
   - Lower data rates compared to LANs
   - Example: The Internet

## Network Topologies

Network topology refers to the arrangement of different elements (links, nodes) in a computer network.

### Common Topologies

- **Bus Topology**: All devices connected to a single cable
- **Star Topology**: All devices connected to a central hub
- **Ring Topology**: Devices connected in a circular fashion
- **Mesh Topology**: Multiple connections between devices
- **Hybrid Topology**: Combination of two or more topologies

## The OSI Model

The **Open Systems Interconnection (OSI)** model is a conceptual framework that standardizes network communication into seven layers:

| Layer | Name | Function |
|-------|------|----------|
| 7 | Application | User interface and application services |
| 6 | Presentation | Data formatting, encryption, compression |
| 5 | Session | Session management and control |
| 4 | Transport | End-to-end communication, reliability |
| 3 | Network | Routing and logical addressing |
| 2 | Data Link | Physical addressing, error detection |
| 1 | Physical | Physical transmission of raw bits |

### Layer Functions

**Application Layer (Layer 7)**
- Provides network services to applications
- Protocols: HTTP, FTP, SMTP, DNS

**Presentation Layer (Layer 6)**
- Data translation and encryption
- Format conversion (ASCII, JPEG, etc.)

**Session Layer (Layer 5)**
- Establishes, manages, and terminates sessions
- Synchronization and dialog control

**Transport Layer (Layer 4)**
- Reliable data transfer
- Segmentation and reassembly
- Protocols: TCP, UDP

**Network Layer (Layer 3)**
- Logical addressing (IP addresses)
- Routing between networks
- Protocol: IP

**Data Link Layer (Layer 2)**
- Physical addressing (MAC addresses)
- Frame creation and error detection
- Protocols: Ethernet, Wi-Fi

**Physical Layer (Layer 1)**
- Physical connection between devices
- Bit transmission over physical medium
- Specifications for cables, connectors, voltages

## TCP/IP Model

The **TCP/IP model** is a more practical four-layer model used in the Internet:

1. **Application Layer** (combines OSI layers 5-7)
2. **Transport Layer** (OSI layer 4)
3. **Internet Layer** (OSI layer 3)
4. **Network Access Layer** (combines OSI layers 1-2)

## Key Terms

- **Protocol**: A set of rules governing data communication
- **Bandwidth**: Maximum data transfer rate of a network
- **Latency**: Delay in network communication
- **Packet**: Unit of data transmitted over a network
- **Node**: Any device connected to a network
- **Host**: A computer connected to a network

## Summary

Computer networks are essential for modern communication and resource sharing. Understanding network types, topologies, and the layered architecture (OSI and TCP/IP models) provides the foundation for studying more advanced networking concepts.

## Further Reading

- "Computer Networks" by Andrew S. Tanenbaum
- RFC 1122 - Requirements for Internet Hosts
- OSI Model - ISO/IEC 7498-1 standard

## Exercises

1. Draw and label the seven layers of the OSI model
2. Compare and contrast the OSI and TCP/IP models
3. Identify the network topology used in your home or school
4. Research a real-world example of each network type (PAN, LAN, MAN, WAN)
