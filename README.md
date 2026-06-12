# IP Addressing Basics

This repository contains notes on IPv4 addressing, including IP classes, public and private IP ranges, CIDR notation, NAT, and commonly reserved IP addresses.

---

# What is an IPv4 Address?

An IPv4 address is a 32-bit numerical address used to identify devices on a network.

Example:

```text
192.168.1.10
```

Each octet ranges from:

```text
0 - 255
```

Total possible IPv4 addresses:

```text
2^32 = 4,294,967,296
```

---

# IP Classes (Classful Addressing)

| Class | First Octet Range | Default Subnet Mask | Usage |
|---------|------------------|-------------------|---------|
| A | 1 - 126 | 255.0.0.0 (/8) | Large Networks |
| B | 128 - 191 | 255.255.0.0 (/16) | Medium Networks |
| C | 192 - 223 | 255.255.255.0 (/24) | Small Networks |
| D | 224 - 239 | N/A | Multicast |
| E | 240 - 255 | N/A | Experimental |

## Examples

### Class A

```text
10.5.1.20
```

### Class B

```text
172.16.5.20
```

### Class C

```text
192.168.1.10
```

### Special Notes

```text
127.x.x.x -> Loopback
0.x.x.x   -> Reserved
```

Modern networking uses CIDR instead of classful addressing.

---

# Public IP Addresses

Public IP addresses are globally unique and routable on the Internet.

Examples:

```text
8.8.8.8
1.1.1.1
142.250.x.x
```

Characteristics:

- Globally unique
- Internet routable
- Assigned by ISP
- Used for communication over the Internet

---

# Private IP Addresses

Private IP addresses are used inside local networks and are not routable on the Internet.

## Private Class A

```text
10.0.0.0/8
```

Range:

```text
10.0.0.0 - 10.255.255.255
```

---

## Private Class B

```text
172.16.0.0/12
```

Range:

```text
172.16.0.0 - 172.31.255.255
```

---

## Private Class C

```text
192.168.0.0/16
```

Range:

```text
192.168.0.0 - 192.168.255.255
```

Common home router IPs:

```text
192.168.0.1
192.168.1.1
```

---

# Public vs Private IP

| Feature | Public IP | Private IP |
|----------|----------|-----------|
| Internet Routable | Yes | No |
| Globally Unique | Yes | No |
| Assigned by ISP | Yes | No |
| Reusable Across Networks | No | Yes |

Examples:

```text
Public IP  : 8.8.8.8
Private IP : 192.168.1.10
```

---

# NAT (Network Address Translation)

NAT allows multiple private IP devices to share a single public IP.

Example:

```text
Laptop  -> 192.168.1.10
Phone   -> 192.168.1.20
Tablet  -> 192.168.1.30

Router Public IP -> 49.x.x.x
```

Without NAT, private IPs cannot communicate with the Internet directly.

---

# Common Reserved IP Ranges

| Range | Purpose |
|---------|---------|
| 127.0.0.0/8 | Loopback |
| 127.0.0.1 | Localhost |
| 169.254.0.0/16 | APIPA / Link Local |
| 224.0.0.0 - 239.255.255.255 | Multicast |
| 255.255.255.255 | Broadcast |
| 0.0.0.0 | Unspecified / Default Route |

---

# Loopback Address

```text
127.0.0.1
```

Used to refer to the local machine itself.

Example:

```bash
ping 127.0.0.1
```

---

# APIPA (Automatic Private IP Addressing)

Range:

```text
169.254.0.0 - 169.254.255.255
```

Assigned automatically when a device cannot obtain an IP address from a DHCP server.

---

# CIDR Notation (Classless Inter-Domain Routing)

CIDR replaces traditional classful networking.

Examples:

```text
10.0.0.0/8
172.16.0.0/12
192.168.1.0/24
```

Meaning of:

```text
192.168.1.0/24
```

```text
24 bits -> Network Portion
8 bits  -> Host Portion
```

Equivalent Subnet Mask:

```text
255.255.255.0
```

Network Address:

```text
192.168.1.0
```

Usable Hosts:

```text
192.168.1.1 - 192.168.1.254
```

Broadcast Address:

```text
192.168.1.255
```

---

# Quick Interview Cheat Sheet

## Private Ranges

```text
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
```

## Loopback

```text
127.0.0.1
```

## APIPA

```text
169.254.0.0/16
```

## Multicast

```text
224.0.0.0 - 239.255.255.255
```

## Broadcast

```text
255.255.255.255
```

## Class Ranges

```text
Class A : 1 - 126
Class B : 128 - 191
Class C : 192 - 223
Class D : 224 - 239
Class E : 240 - 255
```

---

# Easy Rule to Remember

If an IP starts with:

```text
10.x.x.x
172.16.x.x - 172.31.x.x
192.168.x.x
```

then it is a Private IP Address.

All other addresses are generally Public IP Addresses unless they belong to another reserved range.
