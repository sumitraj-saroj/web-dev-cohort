
# How DNS Works

## Why DNS Exists

To connect to any machine on the internet, we need its **IP address**.

Example:
```
google.com -> 17.53.21.253
```

IP addresses are difficult for humans to remember, so DNS provides a **mapping system** from domain names to IP addresses.

---

## DNS and Load Balancing

A single IP address often represents a **load balancer**, not a single server.

- Incoming traffic hits the load balancer
- Load balancer routes requests to multiple backend servers
- These servers typically serve the frontend or APIs

---

## DNS Records and Zones

DNS stores mappings such as:

```
www.google.com -> 17.53.21.253
bard.google.com -> ...
MX, TXT, etc.
```

All DNS records for a domain belong to a **Zone**.

- A zone is a logical entity
- This is what we configure in services like:
  - AWS Route 53
  - GoDaddy
  - Other DNS providers

---

## Authoritative Name Servers

An **Authoritative Name Server**:

- Hosts one or more DNS zones
- Answers DNS queries for the zones it owns

Zones are served by authoritative name servers, usually provided by:
- Cloud providers
- Domain registrars (GoDaddy, etc.)

Example:
```
ns1.gns.com
ns2.gns.com
ns3.gns.com
```

---

## Why DNS Is Decentralized

### Option 1: Centralized System
- One massive system stores all mappings
- Website owners update it
- Everyone queries it

❌ Problems:
- Not scalable
- Not fault-tolerant
- Too many reads, writes, and updates

### Option 2: Decentralized System (DNS)
- No single machine knows everything
- Responsibility is distributed

✅ This is how DNS works

---

## DNS Resolver

A **DNS Resolver**:

- Resolves domain names to IP addresses
- Typically run by:
  - ISPs
  - Home routers
  - Or locally configured by users

Most home routers act as DNS resolvers.

Popular public DNS resolvers:
```
Google DNS: 8.8.8.8
Cloudflare DNS: 1.1.1.1
```

---

## DNS Resolution Flow

Example: resolving `www.google.com`

1. Browser asks the OS
2. OS asks the DNS resolver
3. Resolver queries the Root Name Server
4. Root server returns TLD name servers (`.com`, `.in`, etc.)
5. Resolver queries the TLD server
6. TLD server returns Authoritative Name Server
7. Resolver queries the Authoritative Name Server
8. IP address is returned

---

## Root Name Servers

- There are **13 root name servers** globally
- Each has a fixed IP address
- Operated by organizations like:
  - Verisign
  - USC

Important:
- This does **not** mean only 13 machines
- Root servers are distributed worldwide
- They use **Anycast** (same IP advertised globally)

This ensures:
- Low latency
- High availability

---

## Caching in DNS

DNS heavily relies on caching:

- Browser cache
- OS cache
- Resolver cache
- ISP cache

Root and TLD lookups are infrequent because:
- Their IPs rarely change
- Cached for hours

Each step brings the resolver closer to the machine that knows the answer.

---

## Final Resolution

- Authoritative Name Server checks records for `www`
- May point to a load balancer
- Returns final IP address

The browser then:
- Connects to the IP address
- Sends the actual HTTP request

---

## Summary

DNS resolution:
- Is decentralized
- Is cached aggressively
- Scales globally
- Converts human-readable names into machine-readable IPs

All of this typically completes in **milliseconds**.
