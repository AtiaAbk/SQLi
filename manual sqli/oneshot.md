# Manual SQL Injection Notes

> ⚠️ **Disclaimer**
>
> This document is intended **only for educational purposes** and should be used **only on systems you own or have explicit permission to test**, such as local labs, CTFs, or intentionally vulnerable applications (DVWA, OWASP Juice Shop, WebGoat, etc.).

---

# Useful Browser Extensions

## Google Chrome
https://chromewebstore.google.com/detail/link-gopher/bpjdkodgnbfalgghnbeggfbfjpcfamkf

## Mozilla Firefox
https://addons.mozilla.org/en-US/firefox/addon/link-gopher/

---

# URL and URI

**URL**
- Uniform Resource Locator

**URI**
- Uniform Resource Identifier

---

# URL Structure

Example:

```
https://example.com/products/view.php?id=25
```

Breakdown:

```
https://        -> Protocol
example.com     -> Domain
/products/      -> Directory
view.php        -> File
?id=25          -> Query Parameter
```

Another Example

```
https://example.com/search.php?category=books&page=2
```

Query Parameters

```
category = books
page = 2
```

Multiple Parameters

```
?
&
=
```

Example

```
https://example.com/search.php?category=books&page=2&sort=price
```

---

# Common Parameter Examples

```
?id=25
?user=admin
?page=2
?category=books
?product=15
?article=10
?news=5
?lang=en
?file=readme
```

---

# Base64 Example

```
YXJlbmEgd2ViIHNlY3VyaXR5IA==
```

Some applications encode values before sending them to the server.

---

# Typical Learning Workflow

## Step 1 — Identify User Input

Locate pages that accept user-controlled input.

Example:

```
https://example.com/product.php?id=25
```

Understand which parts of the URL are controlled by the user.

---

## Step 2 — Understand Input Handling

Learn how applications process URL parameters and why improper validation can create security risks.

Topics:

- User Input
- Server-side Processing
- SQL Queries
- Input Validation

---

## Step 3 — Learn Database Interaction

Understand how web applications communicate with databases.

Topics:

- SELECT
- INSERT
- UPDATE
- DELETE

Understand the role of SQL queries inside applications.

---

## Step 4 — Learn Secure Development

Modern applications should use:

- Prepared Statements
- Parameterized Queries
- ORM Frameworks
- Input Validation
- Output Encoding
- Least Privilege Principle

---

## Step 5 — Practice Responsibly

Practice only in:

- DVWA
- OWASP Juice Shop
- WebGoat
- PortSwigger Web Security Academy
- Capture The Flag (CTF) Labs

Never test systems without explicit authorization.

---

# Useful Terms

```
GET
POST
Cookie
Header
HTTP
HTTPS
Request
Response
Status Code
Session
Authentication
Authorization
```

---

# Recommended Labs

- PortSwigger Web Security Academy
- DVWA
- OWASP Juice Shop
- WebGoat
- bWAPP

---

# References

- OWASP Top 10
- PortSwigger Academy
- OWASP Cheat Sheet Series

---

# Reminder

Always follow responsible disclosure and obtain proper authorization before performing any security testing.

This repository exists to improve secure software development and defensive security knowledge.
