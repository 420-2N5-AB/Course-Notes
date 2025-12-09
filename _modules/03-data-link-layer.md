---
title: Data Link Layer
module_number: 3
description: MAC addressing, framing, error detection, and data link protocols
---

## Overview

The Data Link Layer (Layer 2) is responsible for reliable data transfer between adjacent nodes over a physical link. It handles framing, addressing, error detection, and flow control.

## Learning Objectives

After completing this module, you should be able to:

- Understand the functions of the data link layer
- Explain MAC addressing and its purpose
- Describe framing and error detection techniques
- Understand the Ethernet protocol
- Explain the difference between switches and hubs

## Data Link Layer Functions

### Main Responsibilities

1. **Framing**: Encapsulate network layer packets into frames
2. **Physical Addressing**: Add MAC addresses to frames
3. **Error Detection**: Detect transmission errors
4. **Error Correction**: Correct errors (optional)
5. **Flow Control**: Manage data transmission rate
6. **Access Control**: Determine which device can use the medium

## MAC Addressing

**Media Access Control (MAC) Address** is a unique 48-bit hardware address assigned to network interfaces.

### MAC Address Format

- 48 bits (6 bytes)
- Written as 6 pairs of hexadecimal digits
- Example: `00:1A:2B:3C:4D:5E`

### Components

- **First 3 bytes**: Organizationally Unique Identifier (OUI) - manufacturer
- **Last 3 bytes**: Network Interface Controller (NIC) specific

### Types of MAC Addresses

- **Unicast**: Single destination (LSB of first byte = 0)
- **Multicast**: Group of destinations (LSB of first byte = 1)
- **Broadcast**: All devices (`FF:FF:FF:FF:FF:FF`)

## Framing

A frame is the unit of data at the data link layer.

### Frame Structure

```
+----------+-------------+----------+------+-----+
| Preamble | Destination | Source   | Type | FCS |
|          | MAC         | MAC      |      |     |
+----------+-------------+----------+------+-----+
```

### Components

- **Preamble**: Synchronization pattern
- **Destination Address**: Recipient's MAC address
- **Source Address**: Sender's MAC address
- **Type/Length**: Protocol type or frame size
- **Data**: Actual payload (46-1500 bytes)
- **Frame Check Sequence (FCS)**: Error detection

## Error Detection

### Parity Check

- Single bit added to make number of 1s even or odd
- Can detect single-bit errors
- Simple but limited

### Checksum

- Sum of data segments
- Sender computes and sends checksum
- Receiver recomputes and compares
- Used in IP and TCP

### Cyclic Redundancy Check (CRC)

- Most common in data link layer
- Uses polynomial division
- Can detect:
  - All single-bit errors
  - All double-bit errors
  - Burst errors up to length of CRC
- Example: CRC-32 used in Ethernet

## Flow Control

Flow control prevents sender from overwhelming receiver.

### Stop-and-Wait

1. Sender sends one frame
2. Waits for acknowledgment (ACK)
3. Sends next frame only after receiving ACK

**Problems**: Low efficiency, especially on high-latency links

### Sliding Window

- Sender can send multiple frames before receiving ACK
- Window size determines how many unacknowledged frames allowed
- More efficient than stop-and-wait

## Media Access Control (MAC) Protocols

### Channel Allocation Methods

**1. Static Allocation**
- TDMA (Time Division Multiple Access)
- FDMA (Frequency Division Multiple Access)
- Fixed allocation, inefficient for bursty traffic

**2. Dynamic Allocation**
- Better for variable traffic patterns
- Examples: CSMA/CD, CSMA/CA

## CSMA/CD (Carrier Sense Multiple Access with Collision Detection)

Used in traditional Ethernet networks.

### Operation

1. **Carrier Sense**: Listen before transmitting
2. **Multiple Access**: All stations can access medium
3. **Collision Detection**: Detect if collision occurs
4. **Backoff**: Wait random time before retrying

### Algorithm

```
1. If medium is idle, transmit
2. If medium is busy, wait
3. While transmitting, monitor for collision
4. If collision detected:
   - Send jam signal
   - Wait random backoff time
   - Retry (with exponential backoff)
```

## Ethernet

Ethernet is the most widely used LAN technology.

### Ethernet Standards

| Standard | Speed | Medium | Distance |
|----------|-------|--------|----------|
| 10BASE-T | 10 Mbps | Twisted pair | 100m |
| 100BASE-TX | 100 Mbps | Twisted pair | 100m |
| 1000BASE-T | 1 Gbps | Twisted pair | 100m |
| 10GBASE-T | 10 Gbps | Twisted pair | 100m |
| 100GBASE-SR | 100 Gbps | Fiber optic | 100m |

### Ethernet Frame Format

- **Preamble**: 7 bytes (10101010 pattern)
- **Start Frame Delimiter (SFD)**: 1 byte (10101011)
- **Destination MAC**: 6 bytes
- **Source MAC**: 6 bytes
- **Type/Length**: 2 bytes
- **Data**: 46-1500 bytes
- **FCS (CRC)**: 4 bytes

## Switches vs. Hubs

### Hub (Layer 1)
- Broadcasts to all ports
- Single collision domain
- No intelligence
- Half-duplex operation

### Switch (Layer 2)
- Forwards frames based on MAC addresses
- Separate collision domain per port
- Learns MAC addresses dynamically
- Full-duplex operation
- Much more efficient than hubs

### Switch Operation

1. **Learning**: Build MAC address table
2. **Forwarding**: Send frames to correct port
3. **Filtering**: Drop frames if unnecessary
4. **Flooding**: Broadcast if destination unknown

## Virtual LANs (VLANs)

VLANs allow logical segmentation of networks.

### Benefits

- Improved security
- Better traffic management
- Simplified administration
- Reduced broadcast traffic

### VLAN Tagging

- IEEE 802.1Q standard
- 4-byte VLAN tag inserted into Ethernet frame
- Contains VLAN ID (12 bits = 4096 VLANs)

## Summary

The data link layer provides reliable communication between adjacent network nodes. Understanding MAC addressing, framing, error detection, and Ethernet is crucial for network operation and troubleshooting.

## Key Terms

- **MAC Address**: Unique hardware address
- **Frame**: Data link layer PDU
- **Collision Domain**: Network segment where collisions can occur
- **Full-Duplex**: Simultaneous bidirectional communication
- **Half-Duplex**: One direction at a time

## Exercises

1. Convert a MAC address from hexadecimal to binary
2. Calculate a CRC checksum for given data
3. Explain why switches are more efficient than hubs
4. Design a VLAN structure for a small business network
5. Trace the path of an Ethernet frame through a switched network
