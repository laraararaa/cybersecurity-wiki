# Networking Basics

## What is a Network?

A **network** is a collection of computers connected together so they can communicate and share resources.

### Simple Example

Imagine your home:
- Your laptop
- Your phone  
- Your printer

If they're all connected via WiFi, they form a network. They can find and communicate with each other.

## Why Networking Matters in Cybersecurity

Most modern attacks happen over networks:
- Hackers scan networks to find vulnerable systems
- Malware spreads across networks
- Data is stolen across networks
- Defenders monitor networks to detect attacks

---

## The Internet Protocol Suite

Computers communicate using **protocols** (agreed-upon rules for communication).

### IP (Internet Protocol)

**IP** is the fundamental protocol that routes data across networks.

#### IP Addresses

Every device on a network has an **IP address** - like a postal address for computers.

**IPv4** format: `192.168.1.100` (4 numbers, each 0-255)

**IPv6** format: `2001:0db8:85a3:0000:0000:8a2e:0370:7334` (newer, longer)

#### Public vs Private IP Addresses

**Private IP ranges** (used on internal networks):
```
10.0.0.0 - 10.255.255.255
172.16.0.0 - 172.31.255.255
192.168.0.0 - 192.168.255.255
```

### TCP (Transmission Control Protocol)

**TCP** ensures reliable, ordered delivery of data. It establishes a connection before sending data.

#### Three-Way Handshake

Before sending data, TCP performs a "handshake":

```
Client                    Server
  │                         │
  ├──────── SYN ────────────┤
  │                         │
  │◄────── SYN-ACK ─────────┤
  │                         │
  ├──────── ACK ────────────┤
  │                         │
  └──────── Connected ──────┘
```

### UDP (User Datagram Protocol)

**UDP** is faster but less reliable than TCP. It doesn't establish connections, just sends data.

### TCP vs UDP

| Aspect | TCP | UDP |
|--------|-----|-----|
| **Connection** | Establishes connection | No connection |
| **Reliability** | Guaranteed delivery | No guarantee |
| **Speed** | Slower | Faster |
| **Use** | Email, web, SSH | Video, gaming, DNS |

---

## Ports and Services

### What is a Port?

A **port** is a logical endpoint for network communication. Think of it as a "door" to a service.

IP addresses identify computers; **ports identify specific services on those computers**.

### Common Ports

| Port | Service | Purpose |
|------|---------|----------|
| 22 | SSH | Secure shell (remote access) |
| 80 | HTTP | Web (unencrypted) |
| 443 | HTTPS | Web (encrypted) |
| 3306 | MySQL | Database |
| 3389 | RDP | Remote desktop |
| 5432 | PostgreSQL | Database |

---

## DNS (Domain Name System)

### The Problem

Computers need IP addresses to communicate. But humans can't remember `93.184.216.34`—that's why we have domain names like `example.com`.

### How DNS Works

```
You type: example.com
  ↓
Your computer asks DNS: "What's the IP for example.com?"
  ↓
DNS responds: "93.184.216.34"
  ↓
Your computer connects to 93.184.216.34
```

### DNS Records

DNS stores different types of records:

- **A record**: Maps domain to IPv4 address
- **AAAA record**: Maps domain to IPv6 address
- **MX record**: Mail server for the domain
- **CNAME record**: Alias to another domain
- **TXT record**: Text information
- **NS record**: Nameserver for the domain

---

## MAC Addresses

### What is a MAC Address?

A **MAC (Media Access Control) address** identifies devices on a *local* network.

Format: `00:1A:2B:3C:4D:5E` (48 bits, written as 6 pairs of hex digits)

### MAC vs IP

| Aspect | MAC | IP |
|--------|-----|----|
| **Scope** | Local network only | Internet-wide |
| **Use** | Find devices locally | Route across networks |

---

## Key Takeaways

✅ Networks allow computers to communicate

✅ IP addresses identify computers; ports identify services

✅ TCP is reliable; UDP is fast

✅ DNS translates domain names to IP addresses

✅ Understanding networking is essential for cybersecurity

---

## Next Steps

1. Explore your network configuration (ifconfig, ipconfig)
2. Try pinging servers (google.com, 8.8.8.8)
3. Look up DNS records (nslookup)
4. Move on to [Command Line Essentials](03_command_line.md)
