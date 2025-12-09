---
title: Application Layer Protocols
module_number: 6
description: HTTP, DNS, FTP, SMTP, and other application layer protocols
---

## Overview

The Application Layer (Layer 7) provides network services directly to user applications. This module covers the most important application layer protocols used on the Internet.

## Learning Objectives

After completing this module, you should be able to:

- Understand common application layer protocols
- Explain HTTP/HTTPS and web communication
- Describe DNS operation and hierarchy
- Understand email protocols (SMTP, POP3, IMAP)
- Explain FTP and file transfer mechanisms

## Domain Name System (DNS)

DNS translates human-readable domain names to IP addresses.

### DNS Hierarchy

```
                    Root (.)
                       |
        +--------------+--------------+
        |              |              |
      .com           .org           .edu
        |              |              |
    example.com    example.org    mit.edu
        |
    www.example.com
```

### DNS Record Types

| Type | Purpose | Example |
|------|---------|---------|
| A | IPv4 address | `192.168.1.1` |
| AAAA | IPv6 address | `2001:db8::1` |
| CNAME | Canonical name (alias) | `www` → `example.com` |
| MX | Mail server | `mail.example.com` |
| NS | Name server | `ns1.example.com` |
| TXT | Text information | SPF, DKIM records |
| PTR | Reverse lookup | IP → domain name |

### DNS Query Process

1. User enters URL in browser
2. Browser checks local cache
3. Query sent to recursive DNS resolver
4. Resolver queries root server
5. Root server directs to TLD server
6. TLD server directs to authoritative server
7. Authoritative server returns IP address
8. Response cached and returned to user

### DNS Query Types

- **Recursive**: DNS server does all the work
- **Iterative**: DNS server refers client to other servers

## HyperText Transfer Protocol (HTTP)

HTTP is the foundation of web communication.

### HTTP Versions

- **HTTP/1.0**: One request per connection
- **HTTP/1.1**: Persistent connections, pipelining
- **HTTP/2**: Multiplexing, server push, header compression
- **HTTP/3**: Built on QUIC (UDP), improved performance

### HTTP Request Methods

| Method | Purpose | Idempotent |
|--------|---------|------------|
| GET | Retrieve resource | Yes |
| POST | Submit data | No |
| PUT | Update/create resource | Yes |
| DELETE | Delete resource | Yes |
| HEAD | Get headers only | Yes |
| OPTIONS | Get allowed methods | Yes |
| PATCH | Partial update | No |

### HTTP Request Format

```
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
Accept: text/html
Accept-Language: en-US
Connection: keep-alive

[Optional message body]
```

### HTTP Response Format

```
HTTP/1.1 200 OK
Date: Mon, 09 Dec 2024 12:00:00 GMT
Server: Apache/2.4.41
Content-Type: text/html
Content-Length: 1234
Connection: keep-alive

[Response body - HTML content]
```

### HTTP Status Codes

- **1xx**: Informational
- **2xx**: Success
  - 200 OK
  - 201 Created
  - 204 No Content
- **3xx**: Redirection
  - 301 Moved Permanently
  - 302 Found (Temporary)
  - 304 Not Modified
- **4xx**: Client Error
  - 400 Bad Request
  - 401 Unauthorized
  - 403 Forbidden
  - 404 Not Found
- **5xx**: Server Error
  - 500 Internal Server Error
  - 502 Bad Gateway
  - 503 Service Unavailable

### HTTPS (HTTP Secure)

- HTTP over TLS/SSL
- Encrypts communication
- Uses port 443
- Provides:
  - Confidentiality (encryption)
  - Integrity (tampering detection)
  - Authentication (certificate validation)

## Email Protocols

### SMTP (Simple Mail Transfer Protocol)

- Used for **sending** email
- Port 25 (standard), 587 (submission), 465 (SSL)
- Push protocol

**SMTP Process**:
1. Client connects to SMTP server
2. Client sends `HELO` or `EHLO`
3. Client sends `MAIL FROM`
4. Client sends `RCPT TO`
5. Client sends `DATA` followed by message
6. Client sends `QUIT`

### POP3 (Post Office Protocol v3)

- Used for **receiving** email
- Port 110 (standard), 995 (SSL)
- Downloads messages to client
- Typically deletes from server

**POP3 Commands**:
- `USER`: Username
- `PASS`: Password
- `LIST`: List messages
- `RETR`: Retrieve message
- `DELE`: Delete message
- `QUIT`: Disconnect

### IMAP (Internet Message Access Protocol)

- Used for **receiving** email
- Port 143 (standard), 993 (SSL)
- Manages messages on server
- Supports folders and synchronization

**IMAP Advantages over POP3**:
- Access email from multiple devices
- Server-side message management
- Selective downloading
- Folder support

## File Transfer Protocol (FTP)

FTP transfers files between client and server.

### FTP Characteristics

- Uses two connections:
  - **Control connection**: Port 21 (commands)
  - **Data connection**: Port 20 or dynamic (file transfer)
- Active vs. Passive modes
- Plain text (insecure)

### FTP Modes

**Active Mode**:
- Client opens random port
- Server initiates data connection
- Problems with firewalls

**Passive Mode**:
- Server opens random port
- Client initiates data connection
- Better for firewalls

### Secure Alternatives

- **FTPS**: FTP over SSL/TLS
- **SFTP**: SSH File Transfer Protocol
- **SCP**: Secure Copy Protocol

## Dynamic Host Configuration Protocol (DHCP)

DHCP automatically assigns IP addresses to devices.

### DHCP Process (DORA)

1. **Discover**: Client broadcasts to find DHCP server
2. **Offer**: Server offers IP configuration
3. **Request**: Client requests offered configuration
4. **Acknowledge**: Server acknowledges and assigns

### DHCP Lease

- IP address assigned for specific time
- Lease can be renewed
- Released when expired or client disconnects

### DHCP Information Provided

- IP address
- Subnet mask
- Default gateway
- DNS servers
- Lease duration

## Other Application Protocols

### SSH (Secure Shell)

- Secure remote access
- Port 22
- Encrypted communication
- Authentication methods:
  - Password
  - Public key

### Telnet

- Remote access protocol
- Port 23
- **Insecure** (plain text)
- Replaced by SSH

### SNMP (Simple Network Management Protocol)

- Network device management
- Ports 161 (agent), 162 (manager)
- Versions: SNMPv1, SNMPv2c, SNMPv3

### NTP (Network Time Protocol)

- Time synchronization
- Port 123
- Hierarchical time sources (stratum)

## Web Architecture

### Client-Server Model

- Client requests resources
- Server provides resources
- Stateless communication (HTTP)

### Cookies

- Store state information
- Sent with each request
- Types:
  - Session cookies (temporary)
  - Persistent cookies (stored on disk)

### Web Caching

- Reduces latency
- Reduces server load
- Types:
  - Browser cache
  - Proxy cache
  - CDN (Content Delivery Network)

## RESTful APIs

REST (Representational State Transfer) is an architectural style for web services.

### REST Principles

1. Client-Server architecture
2. Stateless communication
3. Cacheable responses
4. Uniform interface
5. Layered system

### RESTful HTTP

- Use HTTP methods semantically
- Resources identified by URLs
- JSON or XML responses
- Status codes indicate results

## Summary

Application layer protocols provide the services that users directly interact with. Understanding these protocols is essential for web development, network administration, and troubleshooting.

## Key Terms

- **URL**: Uniform Resource Locator
- **URI**: Uniform Resource Identifier
- **MIME Type**: Media type (e.g., text/html, image/jpeg)
- **Session**: Series of related transactions
- **API**: Application Programming Interface

## Exercises

1. Perform a DNS lookup using `nslookup` or `dig`
2. Capture HTTP traffic using browser developer tools
3. Explain the complete process of loading a web page
4. Compare IMAP and POP3 for different use cases
5. Trace the DHCP DORA process with packet capture
