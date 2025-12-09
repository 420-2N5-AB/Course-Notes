---
title: Transport Layer - TCP and UDP
module_number: 5
description: Transport layer protocols, TCP reliability, UDP efficiency, and port numbers
---

## Overview

The Transport Layer (Layer 4) provides end-to-end communication services for applications. The two main protocols are TCP (reliable) and UDP (fast).

## Learning Objectives

After completing this module, you should be able to:

- Understand the functions of the transport layer
- Compare TCP and UDP protocols
- Explain TCP's reliability mechanisms
- Understand port numbers and socket programming
- Describe flow control and congestion control

## Transport Layer Functions

### Main Responsibilities

1. **End-to-End Communication**: Between processes on different hosts
2. **Segmentation**: Breaking application data into segments
3. **Multiplexing/Demultiplexing**: Using port numbers
4. **Error Detection**: Ensuring data integrity
5. **Flow Control**: Managing sender's rate
6. **Congestion Control**: Preventing network overload

## Port Numbers

Port numbers identify specific applications or services.

### Port Number Ranges

- **Well-Known Ports** (0-1023): Reserved for standard services
- **Registered Ports** (1024-49151): Assigned to specific applications
- **Dynamic/Private Ports** (49152-65535): Temporary assignments

### Common Port Numbers

| Port | Protocol | Service |
|------|----------|---------|
| 20, 21 | TCP | FTP (File Transfer Protocol) |
| 22 | TCP | SSH (Secure Shell) |
| 23 | TCP | Telnet |
| 25 | TCP | SMTP (Email) |
| 53 | TCP/UDP | DNS (Domain Name System) |
| 67, 68 | UDP | DHCP |
| 80 | TCP | HTTP (Web) |
| 110 | TCP | POP3 (Email) |
| 143 | TCP | IMAP (Email) |
| 443 | TCP | HTTPS (Secure Web) |
| 3389 | TCP | RDP (Remote Desktop) |

### Sockets

A **socket** is the combination of IP address and port number:
- Example: `192.168.1.100:80`
- Uniquely identifies a communication endpoint

## User Datagram Protocol (UDP)

UDP is a simple, connectionless transport protocol.

### UDP Characteristics

- **Connectionless**: No handshake before sending
- **Unreliable**: No guarantee of delivery
- **No Order Guarantee**: Packets may arrive out of order
- **Fast**: Minimal overhead
- **Lightweight**: Small header (8 bytes)

### UDP Header Format

```
+----------------+----------------+
| Source Port    | Dest Port      | (16 bits each)
+----------------+----------------+
| Length         | Checksum       | (16 bits each)
+----------------+----------------+
| Data ...                        |
```

### When to Use UDP

- Real-time applications (VoIP, video streaming)
- Simple request-response (DNS)
- Broadcast/multicast applications
- Applications with their own reliability (gaming)

### UDP Applications

- DNS (Domain Name System)
- DHCP (Dynamic Host Configuration Protocol)
- SNMP (Simple Network Management Protocol)
- TFTP (Trivial File Transfer Protocol)
- VoIP (Voice over IP)
- Online gaming

## Transmission Control Protocol (TCP)

TCP is a reliable, connection-oriented transport protocol.

### TCP Characteristics

- **Connection-Oriented**: Establishes connection before data transfer
- **Reliable**: Guarantees delivery of data
- **Ordered**: Data arrives in sequence
- **Flow Control**: Manages data transmission rate
- **Congestion Control**: Adjusts to network conditions
- **Full-Duplex**: Bidirectional communication

### TCP Header Format

```
+----------------+----------------+
| Source Port    | Dest Port      | (16 bits each)
+----------------+----------------+----------------+----------------+
| Sequence Number                                                  | (32 bits)
+------------------------------------------------------------------+
| Acknowledgment Number                                            | (32 bits)
+------+-----+---+---+---+---+---+---+----------------+------------+
| Data | Res |   |   |   |   |   |   | Window Size    | Checksum   |
| Offs |     | Flags (6 bits)      |                |            |
+------+-----+---+---+---+---+---+---+----------------+------------+
| Urgent Pointer        | Options (if any)                         |
+----------------+------+------------------------------------------+
```

### TCP Flags

- **SYN** (Synchronize): Initiate connection
- **ACK** (Acknowledgment): Acknowledge received data
- **FIN** (Finish): Terminate connection
- **RST** (Reset): Abort connection
- **PSH** (Push): Send data immediately
- **URG** (Urgent): Urgent data

## TCP Connection Management

### Three-Way Handshake (Connection Establishment)

```
Client                    Server
  |                         |
  |-----SYN (seq=x)-------->|
  |                         |
  |<--SYN-ACK (seq=y,-------|
  |        ack=x+1)         |
  |                         |
  |-----ACK (ack=y+1)------>|
  |                         |
  Connection Established
```

**Steps**:
1. Client sends SYN with initial sequence number
2. Server responds with SYN-ACK
3. Client sends ACK, connection established

### Four-Way Handshake (Connection Termination)

```
Client                    Server
  |                         |
  |-----FIN---------------->|
  |                         |
  |<----ACK-----------------|
  |                         |
  |<----FIN-----------------|
  |                         |
  |-----ACK---------------->|
  |                         |
  Connection Closed
```

## TCP Reliability

### Sequence Numbers and Acknowledgments

- Each byte has a sequence number
- Receiver sends ACK with next expected byte
- Sender retransmits if ACK not received

### Retransmission

**Timeout-Based**:
- Sender starts timer when sending segment
- Retransmits if timer expires before ACK received

**Fast Retransmit**:
- Triggered by duplicate ACKs
- Retransmit immediately after 3 duplicate ACKs

### Cumulative Acknowledgment

- ACK number indicates next expected byte
- Acknowledges all bytes up to that point
- Example: ACK=1000 means bytes 0-999 received

## Flow Control

Flow control prevents sender from overwhelming receiver.

### Sliding Window Protocol

- Receiver advertises **receive window** (buffer size)
- Sender limits unacknowledged data to window size
- Window size changes dynamically

### Window Size

- Specified in TCP header (16 bits)
- Can be scaled (up to 1 GB with window scaling option)
- Zero window stops transmission

## Congestion Control

Congestion control prevents network overload.

### TCP Congestion Control Algorithms

**1. Slow Start**
- Start with small congestion window (cwnd)
- Exponentially increase cwnd each RTT
- Continue until threshold or packet loss

**2. Congestion Avoidance**
- Linearly increase cwnd after slow start
- Additive Increase, Multiplicative Decrease (AIMD)

**3. Fast Recovery**
- After fast retransmit
- Reduces cwnd but not as drastically as timeout

### Congestion Detection

- Packet loss indicates congestion
- Timeout or duplicate ACKs
- Reduce sending rate accordingly

## TCP vs UDP Comparison

| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable | Unreliable |
| Ordering | Ordered | Unordered |
| Speed | Slower (overhead) | Faster |
| Header Size | 20-60 bytes | 8 bytes |
| Flow Control | Yes | No |
| Congestion Control | Yes | No |
| Use Cases | File transfer, email, web | Streaming, gaming, DNS |

## Summary

The transport layer provides crucial end-to-end communication services. TCP offers reliability at the cost of overhead, while UDP provides speed with minimal services. Understanding when to use each protocol is essential for application design.

## Key Terms

- **Segment**: Transport layer PDU
- **Socket**: IP address + port number
- **RTT (Round-Trip Time)**: Time for packet to reach destination and return
- **MSS (Maximum Segment Size)**: Largest TCP segment
- **MTU (Maximum Transmission Unit)**: Largest packet size

## Exercises

1. Explain the TCP three-way handshake with a diagram
2. Calculate throughput given window size and RTT
3. Compare scenarios where TCP vs UDP would be more appropriate
4. Trace a TCP connection from establishment to termination
5. Explain how TCP handles packet loss
