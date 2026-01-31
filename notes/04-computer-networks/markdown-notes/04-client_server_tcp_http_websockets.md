
# Client–Server Model, TCP, HTTP, and WebSockets

## 1. Client–Server Model

The **client–server model** is the most common way for two machines to communicate over a network.

- **Client (C)**: Requests or demands something
- **Server (S)**: Processes the request and does the job

### Examples
- Get my profile information
- Delete a post I created
- Spin up a new server

Communication happens over a **network connection** between the client and server.

---

## 2. Transport Protocols: TCP and UDP

There are two main transport-layer protocols used for data exchange:

- **TCP (Transmission Control Protocol)**  
  Reliable, ordered, and widely used (~99.9% of web traffic)

- **UDP (User Datagram Protocol)**  
  Faster but unreliable and unordered

Most application-level protocols (like HTTP) use **TCP**.

---

## 3. Important Properties of TCP

### 3.1 Connection Setup
- TCP requires a **3-way handshake** to establish a connection  
  (`SYN → SYN-ACK → ACK`)

### 3.2 Connection Teardown
- TCP requires a **2-way handshake** to close a connection  
  (`FIN → ACK`)

### 3.3 Persistent Connections
- A TCP connection does **not** break immediately after data exchange
- It remains open until:
  - Network interruption occurs, or
  - Client/server explicitly closes it

This allows reuse of the same connection for multiple messages.

---

## 4. Protocols Over TCP

TCP does **not** define:
- What data looks like
- How data should be interpreted

It only guarantees **reliable delivery**.

### Application Protocols
A **protocol** is a mutually agreed format between client and server.

Example:
- **HTTP** is a protocol built on top of TCP

HTTP is simply a structured format that both client and server understand.

> You can even define your own protocol as long as:
> 1. Client sends data in the agreed format  
> 2. Server parses and processes it correctly

---

## 5. HTTP Versions Overview

There are multiple versions of HTTP:
- HTTP/1.1
- HTTP/2
- HTTP/3

**HTTP/1.1** is still one of the most widely used versions.

---

## 6. Properties of HTTP/1.1

1. Client and server must establish a **TCP connection**
2. Connection is typically closed after the response is sent
3. Almost a **new TCP connection per request/response**
   - This makes it relatively expensive

### Keep-Alive Connections

To reduce overhead, clients send:
```
Connection: keep-alive
```

This header requests the server to **not close the connection** immediately.

> Note: Whether the connection stays open depends on server configuration.

---

## 7. WebSockets

**WebSockets** are designed for **bi-directional communication**.

### Key Characteristics
- Full-duplex (client ↔ server)
- Server can proactively send data
- Client does not need to request every update

This eliminates repeated request–response cycles.

---

## 8. Why WebSockets Are Fast

- TCP connection is established **once**
- No repeated handshakes
- Very **low latency**
- Ideal for real-time communication

### Comparison

| Feature | HTTP/1.1 | WebSockets |
|------|---------|------------|
| Communication | Request–response | Bi-directional |
| Latency | Higher | Very low |
| Server push | ❌ | ✅ |
| Connection reuse | Limited | Continuous |

---

## 9. When to Use WebSockets

Use WebSockets when you need **real-time, low-latency communication**, such as:

- Chat applications
- Live comments on streams
- Stock market tickers
- Online multiplayer games
- Collaborative editors

---

## Summary

- Client–server model is the backbone of web communication
- TCP provides reliable transport
- HTTP defines how data is exchanged
- HTTP/1.1 is simple but inefficient at scale
- WebSockets enable real-time, bi-directional communication

Choosing the right protocol depends on your **latency**, **scalability**, and **real-time** needs.
