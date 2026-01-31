# 📡 Understanding HTTP (HyperText Transfer Protocol)

HTTP is the foundation of communication on the web. It defines how clients (like browsers) and servers communicate with each other.

---

## 🔹 Key Characteristics of HTTP

### 1. Stateless

HTTP is a **stateless protocol**, meaning:

- The server does **not remember past interactions**
- Each HTTP request contains **all the information** needed to process it
- Every request is treated as **brand new**

**Why this matters:**
- Requests can be handled **independently**
- Easier to **scale horizontally**
- More **fault-tolerant**
- Well suited for **cloud-native and microservices architectures**

---

### 2. Client–Server Model

- The **client** initiates communication
- The **server** responds to client requests
- The server never sends data unless the client asks for it

**Important points:**
- Communication is always **client-initiated**
- HTTP typically runs over **TCP**
- TCP makes HTTP **connection-based and reliable**

---

## 🔹 Evolution of HTTP Versions

### HTTP/0.9 (1991)

**Purpose:** Fetch simple documents

- Only supported `GET`
- No headers
- No status codes
- Only plain text

**Why:**  
The early web consisted only of text documents.

---

### HTTP/1.0 (1996)

- Each request opened a **new TCP connection**
- Inefficient and slow

---

### HTTP/1.1 (1997)

**Goal:** Improve performance

- Persistent connections (keep-alive)
- Multiple requests over a single connection
- Added caching support
- Introduced the `Host` header

✅ Still widely used today

---

### HTTP/2 (2015)

**Goal:** Speed and efficiency

- Binary protocol (faster than text)
- Multiplexing (multiple requests at once)
- Header compression
- One connection handles everything

**Solved:**  
Head-of-line blocking in HTTP/1.1

---

### HTTP/3 (2022+)

**Goal:** Faster and more reliable connections

- Runs on **QUIC** instead of TCP
- Uses **UDP**
- Faster connection setup
- Better performance on poor networks

**Why it exists:**  
TCP became a bottleneck for modern web needs.

---

## 🔹 HTTP Summary

1. HTTP is stateless  
2. HTTP/1.1 is still everywhere  
3. HTTP/2 improves performance  
4. HTTP/3 improves reliability  
5. HTTPS = HTTP + Encryption (TLS)

---

## 🔹 HTTP Headers

### Request Headers

- `User-Agent`
- `Authorization`
- `Cookie`
- `Accept`

Used by the server to understand client preferences.

---

### General Headers

- `Date`
- `Cache-Control`
- `Connection`

---

### Representation Headers

- `Content-Type`
- `Content-Length`
- `Content-Encoding`
- `ETag`

---

### Security Headers

- `Strict-Transport-Security`
- `Content-Security-Policy`
- `X-Frame-Options`
- `X-Content-Type-Options`
- `Set-Cookie`

---

## 🔹 HTTP Extensibility

HTTP is highly extensible because headers can be added or customized without changing the protocol itself.

---

## 🔹 HTTP Methods

| Method | Description |
|------|------------|
| GET | Fetch data |
| POST | Create data |
| PUT | Replace data |
| PATCH | Update data |
| DELETE | Remove data |

Methods define the **intent** of the request.

---

## 🔹 Idempotent vs Non-Idempotent

### Idempotent

Repeating the same request produces the **same result**.

Examples:
- GET
- PUT
- DELETE
- HEAD
- OPTIONS

---

### Non-Idempotent

Repeating the same request **changes the result**.

Examples:
- POST
- PATCH

---

## 🔹 OPTIONS Method

- Used to ask the server what operations are allowed
- Used heavily in **CORS preflight**

---

## 🔹 CORS (Cross-Origin Resource Sharing)

A browser security mechanism that controls access between different origins.

Only browsers enforce CORS.  
Postman and curl ignore it.

---

## 🔹 Origin Definition

```
Origin = protocol + domain + port
```

---

## 🔹 Cross-Origin Request Types

### Simple Request

Allowed without preflight.

- Methods: GET, POST, HEAD
- Content-Types:
  - text/plain
  - application/x-www-form-urlencoded
  - multipart/form-data

---

### Preflight Request

Browser sends an OPTIONS request first when:

- Method is PUT, PATCH, DELETE
- Custom headers are used
- Content-Type is application/json

---

## 🔹 Preflight Cache

```http
Access-Control-Max-Age: 86400
```

Browser will skip preflight for 24 hours.
