# SQL Injection Handbook
### A Beginner to Intermediate Guide for Ethical Learning

> Version: 1.0
>
> Author: AtiaAbk
>
> Status: Work in Progress

---

# Disclaimer

This repository is created **only for educational and defensive security purposes**.

All demonstrations should be performed only on:

- Your own applications
- Intentionally vulnerable labs
- CTF challenges
- Systems where you have explicit written permission

Never test real websites without authorization.

---

# Table of Contents

1. Introduction
2. What is SQL?
3. What is a Database?
4. What is DBMS?
5. Client-Server Architecture
6. HTTP & HTTPS
7. URL & URI
8. GET vs POST
9. Request & Response
10. Cookies & Sessions
11. Web Application Flow
12. Database Fundamentals
13. SQL Basics
14. SQL Injection (Concept)
15. Why SQL Injection Happens
16. Prevention Techniques
17. Practice Labs
18. Resources
19. Glossary

---

# Introduction

SQL Injection is one of the most well-known web application security issues.

Understanding how SQL Injection occurs helps developers build secure applications and helps security professionals identify and prevent vulnerabilities during authorized security assessments.

This handbook focuses on understanding concepts, web technologies, databases, and secure coding practices using legal practice environments.

---


---

# What is SQL?

SQL stands for

Structured Query Language

It is the standard language used to communicate with relational databases.

SQL allows applications to:

- Store data
- Retrieve data
- Update data
- Delete data
- Manage databases

---

# What is a Database?

A database is an organized collection of information.

Example:
| ID | Name  | Department |
| -- | ----- | ---------- |
| 1  | Alice | CSE        |
| 2  | Bob   | ICE        |
| 3  | Carol | EEE        |

Think of a database as a digital filing cabinet.

---


Think of a database as a digital filing cabinet.

---

# What is DBMS?

DBMS = Database Management System

It is software used to create, manage, and maintain databases.

Popular DBMS:

| Database | Company |
|------------|---------------|
| MySQL | Oracle |
| PostgreSQL | PostgreSQL |
| Microsoft SQL Server | Microsoft |
| Oracle Database | Oracle |
| SQLite | SQLite |

---

# 🌐 Client–Server Architecture

A simple visual representation of how a client communicates with a server over a network.

---

# 📖 What is Client–Server Architecture?

Client–Server Architecture is a distributed computing model where:

- **Client** requests services or resources.
- **Server** processes the request.
- The server sends back a response.
- Communication usually occurs over protocols like **HTTP**, **HTTPS**, **FTP**, **TCP**, or **WebSocket**.

---

# 🏗 Basic Architecture

```mermaid
flowchart LR

    A[👤 Client] -->|Request| B[(Internet / Network)]
    B --> C[🖥 Server]
    C -->|Response| B
    B --> A
```

---

# 🔄 Request–Response Flow

```mermaid
sequenceDiagram

    participant Client
    participant Server

    Client->>Server: HTTP Request
    Server->>Server: Process Request
    Server-->>Client: HTTP Response
```

---

# 🌍 Multiple Clients

```mermaid
flowchart TB

    C1[📱 Mobile App]
    C2[💻 Desktop App]
    C3[🌐 Web Browser]

    C1 --> S
    C2 --> S
    C3 --> S

    S[🖥 Application Server]

    S --> DB[(Database)]
```

---

# 🏛 Three-Tier Client–Server Architecture

```mermaid
flowchart LR

    Client[Client Layer]

    App[Application Server]

    Database[(Database Server)]

    Client --> App
    App --> Database
    Database --> App
    App --> Client
```

---

# ☁ Modern Web Architecture

```mermaid
flowchart LR

    User[👤 User]

    Browser[🌐 Browser]

    API[REST API]

    Auth[Authentication]

    App[Application Server]

    Cache[(Redis Cache)]

    DB[(Database)]

    User --> Browser
    Browser --> API
    API --> Auth
    API --> App

    App --> Cache
    App --> DB

    Cache --> App
    DB --> App

    App --> API
    API --> Browser
```

---

# 📦 Components

| Component | Description |
|-----------|-------------|
| Client | Initiates requests |
| Network | Transfers data |
| Server | Processes requests |
| Database | Stores persistent data |
| Cache | Speeds up responses |
| API | Communication interface |
| Authentication | Verifies user identity |

---

# 🔁 Workflow

```text
Client
   │
   ▼
Send Request
   │
   ▼
Network
   │
   ▼
Server
   │
   ├── Validate Request
   ├── Authenticate User
   ├── Execute Business Logic
   ├── Read/Write Database
   │
   ▼
Generate Response
   │
   ▼
Network
   │
   ▼
Client
```

---

# ✅ Advantages

- Centralized data management
- Easier maintenance
- High scalability
- Improved security
- Resource sharing
- Supports multiple clients simultaneously

---

# ❌ Disadvantages

- Server can become a single point of failure.
- Heavy traffic may reduce performance.
- Requires continuous network connectivity.
- Infrastructure costs can be high.

---

# 🚀 Real-World Examples

- Web Applications
- Email Systems
- Banking Systems
- Online Games
- Social Media Platforms
- Cloud Services
- File Sharing Systems
- Streaming Platforms

---

# 📚 Common Protocols

| Protocol | Purpose |
|-----------|----------|
| HTTP | Web communication |
| HTTPS | Secure web communication |
| TCP | Reliable data transfer |
| UDP | Fast data transfer |
| FTP | File transfer |
| SSH | Secure remote access |
| WebSocket | Real-time communication |

---

# 🎯 Summary

```text
          Client
             │
      Request │
             ▼
        Internet
             │
             ▼
         Server
        /      \
   Database   Cache
        \      /
         Response
             │
             ▼
          Client
```

Client–Server Architecture separates the responsibilities of requesting services (client) and providing services (server), making systems more scalable, maintainable, and secure.

---

# HTTP

HTTP stands for

HyperText Transfer Protocol

Used to transfer web pages and data.

Common Methods

GET

Retrieve information.

POST

Send information.

PUT

Update information.

DELETE

Remove information.

---

# HTTPS

HTTPS = HTTP Secure

Adds encryption using TLS.

Benefits

✔ Encryption

✔ Integrity

✔ Authentication

---

# URL

URL

Uniform Resource Locator

Example

https://example.com/products/view.php?id=25

https://

Protocol

example.com

Domain

/products/

Directory

view.php

Resource

?id=25

Query Parameter

---

# URI

URI

Uniform Resource Identifier

Every URL is a URI.

Not every URI is a URL.

---

# Query Parameters

Example
?id=25
Multiple Parameters
?page=2&category=books

Common Parameters
id

page

category

article

news

lang

product

user

search

sort

---

# GET vs POST

| GET | POST |
|------|------|
| Visible in URL | Hidden from URL |
| Bookmarkable | Not Bookmarkable |
| Used for Reading | Used for Sending |

---

# Request and Response

Browser

↓

HTTP Request

↓

Server

↓

Database

↓

Server

↓

HTTP Response

↓

Browser

---

# Cookies

Cookies store small pieces of information.

Examples

- Session ID
- Language
- Theme
- Login State

---

# Sessions

A session stores user information on the server.

Example

---

# Database Structure

Database

↓

Tables

↓

Rows

↓

Columns

Example

Users Table

| ID | Username | Email |
|----|----------|----------------|
|1|Alice|alice@test.com|
|2|Bob|bob@test.com|

---

# Primary Key

A unique identifier.

Example

Student ID

Employee ID

Roll Number

---

# SQL Categories

DDL

CREATE

ALTER

DROP

TRUNCATE

DML

SELECT

INSERT

UPDATE

DELETE

DCL

GRANT

REVOKE

TCL

COMMIT

ROLLBACK

SAVEPOINT

---

# Common SQL Data Types

INT

VARCHAR

TEXT

DATE

TIME

BOOLEAN

FLOAT

DOUBLE

---

# SQL Injection (Concept)

SQL Injection is a class of web application vulnerability that can occur when user input is incorporated into SQL queries without proper handling.

Understanding this concept helps developers and security professionals build and evaluate applications that resist this type of flaw.

---

# Why Can It Happen?

Some applications improperly process user-supplied input before interacting with a database.

Secure development practices help prevent this class of issue.

---

# Prevention

Always use

✔ Prepared Statements

✔ Parameterized Queries

✔ Input Validation

✔ ORM Frameworks

✔ Least Privilege

✔ Secure Error Handling

✔ Regular Security Testing

---

# Secure Development Checklist

□ Validate Input

□ Escape Output

□ Parameterized Queries

□ Strong Authentication

□ Principle of Least Privilege

□ Logging

□ Monitoring

□ Backup

□ Patch Management

---

# Safe Practice Labs

DVWA

OWASP Juice Shop

WebGoat

PortSwigger Web Security Academy

bWAPP

Google Gruyere

All of these are intentionally designed for learning.

---

# Recommended Books

The Web Application Hacker's Handbook

Web Security for Developers

SQL Antipatterns

Real World Bug Hunting

OWASP Testing Guide

---

# Recommended Websites

OWASP

PortSwigger Academy

MDN Web Docs

Oracle MySQL Documentation

PostgreSQL Documentation

SQLite Documentation

---

# Learning Checklist

□ Learn HTTP

□ Learn HTML

□ Learn CSS

□ Learn JavaScript Basics

□ Learn PHP / Python / Node.js

□ Learn SQL

□ Learn Databases

□ Learn Authentication

□ Learn Sessions

□ Learn Secure Coding

□ Complete PortSwigger Labs

□ Complete DVWA

□ Read OWASP Top 10

---

# Glossary

SQL
Structured Query Language

DBMS
Database Management System

HTTP
HyperText Transfer Protocol

HTTPS
HTTP Secure

URL
Uniform Resource Locator

URI
Uniform Resource Identifier

TLS
Transport Layer Security

Cookie
Small client-side storage

Session
Server-side user state

Database
Collection of structured information

---

# Final Notes

Cybersecurity is about protecting systems, understanding technology, and practicing responsibly.

Always obtain explicit authorization before testing any application or system.

Learning through official labs and intentionally vulnerable environments is the safest and most ethical path.

Happy Learning!
