
# TCP and HTTP – Deep Dive with Diagrams Explained

This document converts and improves the handwritten notes, adds missing concepts,
and explains all diagrams step-by-step.

---

## 1. TCP – Transmission Control Protocol

TCP is a transport layer protocol that uses an acknowledgement-based feedback
mechanism to ensure reliable data transfer.

### What TCP Does

1. Sends data at an appropriate transmission rate
2. Segments data into manageable chunks
3. Performs congestion control to avoid network overload
4. Detects errors and retransmits lost or corrupted data

---

## 2. Applications Using TCP

- FTP → Port 21
- SSH → Port 22
- Email (SMTP) → Port 25
- Web Browsing → HTTP/HTTPS (80/443)

---

## 3. Key Features of TCP

- Connection-oriented
- Full-duplex communication
- Point-to-point
- Error control
- Flow control
- Congestion control

---

## 4. TCP Segment Header (20–60 bytes)

Includes:
- Source & Destination Port (16 bits)
- Sequence & Acknowledgement Number (32 bits)
- Flags: SYN, ACK, FIN, RST, PSH, URG
- Window size
- Checksum
- Options (MSS, etc.)

FIN consumes one sequence number.

---

## 5. TCP 3-Way Handshake

1. SYN → Client initiates connection
2. SYN + ACK → Server responds
3. ACK → Client confirms

---

## 6. TCP Data Transfer

- TCP uses byte numbering
- ACK = next expected byte
- ACKs may be piggybacked or pure

---

## 7. TCP Connection Termination

Uses 4-way handshake because TCP is full-duplex:
FIN → ACK → FIN → ACK

---

## 8. HTTP Basics

- Application-layer protocol
- Runs on TCP
- Stateless
- Default port 80

---

## 9. Persistent vs Non-Persistent HTTP

HTTP/1.0:
- New connection per object
- Higher RTT and overhead

HTTP/1.1:
- Persistent connections
- Lower latency

---

## Summary

- TCP ensures reliable communication
- HTTP relies on TCP
- Persistent connections improve performance
