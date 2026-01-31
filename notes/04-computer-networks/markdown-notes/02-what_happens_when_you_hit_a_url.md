
# What Happens When We Hit a URL in the Browser?

## 1. What Constitutes a URL?

A URL is a **human-readable way** to identify what resource we want on the internet.

### Example
```
https://www.google.com/api/search?q=home
```

### URL Components

- **Scheme**  
  Tells the browser which protocol to use while connecting.  
  Examples: `http`, `https`, `ws`

- **Domain**  
  The human-readable name of the server (e.g., `google.com`).

- **Path**  
  Specifies the resource we are interested in.  
  Example: `/api/search`

- **Query Parameters**  
  Optional key-value pairs used to send additional information.  
  Example: `?q=home`

---

## 2. DNS Resolution

Every machine on the internet has an **IP address** that allows it to be reached over the network.

- IP addresses are hard to remember.
- Domain names are easier for humans.

### Example
```
google.com  ->  17.53.21.253
```

DNS exists to convert **domain names into IP addresses**.

---

## 3. DNS Lookup Process

1. Browser checks its **local cache**
2. OS cache is checked
3. DNS resolver is queried
4. Root name servers may be involved
5. Result is cached heavily at multiple levels

> DNS resolution can be **iterative or recursive**.

After DNS resolution, the browser now has the IP address of the server.

---

## 4. Establishing a Connection

Once the IP address is known:

- The browser establishes a **TCP connection** with the server.
- Now the browser and server can communicate over the network.

Behind a single IP, there may be:
- Load balancers
- Hundreds or thousands of machines
- Multiple services (`svc1`, `svc2`, `svc3`)

---

## 5. Sending the Request

The browser converts the request into an **HTTP-compliant message**.

### Example HTTP Request
```
GET /api/search?q=home HTTP/1.1
Host: www.google.com
Connection: keep-alive
```

### HTTP Headers
- Instructions for the server
- Metadata about the request

Simply typing a URL usually results in an **HTTP GET request**.

---

## 6. Why Protocols Exist

Protocols define:
- How data is packed
- What happens before, during, and after communication

### HTTP is a Protocol That Specifies:
1. How to format requests and responses
2. Rules for communication between client and server

---

## 7. Server Processes the Request

Once the server receives the HTTP request:

- It parses the request
- Understands what needs to be done

The server may:
- Load a file from disk
- Query a database
- Return an error if the request is malformed

The server then sends back an HTTP response over the same TCP connection.

---

## 8. HTTP Response

### Example HTTP Response
```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 2042
```

The response body may contain:
- HTML
- JSON
- Plain text
- Other formats

---

## 9. Browser Receives the Response

The browser:
- Parses the HTTP message
- Extracts headers and body
- Uses `Content-Type` to decide how to handle the response

If the browser does not support the response type, it downloads the file locally.

---

## 10. Rendering the Page

When HTML is rendered, the browser may encounter:

1. Linked CSS files
2. Image tags
3. Inline or external JavaScript

The browser fetches additional resources using the **same process**.

### JavaScript Execution
- JavaScript starts executing
- May trigger more HTTP requests (API calls)

---

## Summary

What looks like a simple URL hit actually involves:
- DNS resolution
- TCP connection setup
- HTTP request/response cycle
- Server-side processing
- Browser rendering and execution

All of this happens in **milliseconds**.
