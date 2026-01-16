# YAML Notes

## What is YAML?

**YAML** stands for **YAML Ain't Markup Language**.  
It is a **human-readable data serialization format** commonly used for configuration files and data exchange.

---

## Why YAML?

- Easy to read and write
- Cleaner than JSON or XML
- Widely used in **DevOps**, **CI/CD**, **Cloud**, and **Backend** systems

---

## Basic Syntax Rules

- Uses **indentation** (spaces) to define structure
- **Tabs are not allowed**
- Indentation must be consistent
- Key-value pairs are written as:
  ```yaml
  key: value
  ```

---

## Scalars (Basic Data Types)

### Strings

```yaml
name: Sumit
city: 'New Delhi'
description: |
  This is a
  multiline string
```

### Numbers

```yaml
age: 22
price: 99.99
```

### Booleans

```yaml
isStudent: true
isWorking: false
```

### Null

```yaml
middleName: null
emptyValue: ~
```

---

## Lists (Sequences)

```yaml
skills:
  - HTML
  - CSS
  - JavaScript
```

Inline list:

```yaml
languages: [JavaScript, Go, Python]
```

---

## Maps (Dictionaries)

```yaml
user:
  name: Sumit
  age: 22
  role: Developer
```

Inline map:

```yaml
user: { name: Sumit, age: 22 }
```

---

## Nested Structures

```yaml
server:
  host: localhost
  ports:
    - 3000
    - 5000
```

---

## Comments

```yaml
# This is a comment
name: Sumit # Inline comment
```

---

## Anchors and Aliases (Reusability)

```yaml
defaults: &defaults
  timeout: 30
  retries: 3

service1:
  <<: *defaults
  name: auth

service2:
  <<: *defaults
  name: payment
```

---

## Environment Variables (Common Use)

```yaml
database:
  url: ${DB_URL}
```

---

## Multi-Document YAML

```yaml
---
name: Document1
---
name: Document2
```

---

## YAML vs JSON

| YAML              | JSON             |
| ----------------- | ---------------- |
| Human-friendly    | Machine-friendly |
| Supports comments | No comments      |
| Indentation-based | Brackets-based   |

---

## Common Use Cases

- Docker Compose
- Kubernetes manifests
- GitHub Actions
- Ansible playbooks
- Application configuration

---

## Common Mistakes

- Using tabs instead of spaces
- Wrong indentation
- Forgetting `:` after keys
- Mixing data types incorrectly

---

## YAML BEST PRACTICES

- Use 2 spaces for indentation
- Keep keys lowercase and meaningful
- Use comments to explain configs
- Validate YAML before use

---
