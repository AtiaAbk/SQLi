# 🗺️ Full Learning Roadmap

> Legend: 🟢 Beginner · 🟡 Intermediate · 🔴 Advanced

---

## Phase 1 — Database & SQL Fundamentals 🟢

- Relational database concepts: tables, rows, columns, keys, relationships
- Core SQL: `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `WHERE`, `JOIN`, `GROUP BY`
- Database engines overview: MySQL, PostgreSQL, SQLite, Microsoft SQL Server, Oracle
- Database architecture: client-server model, connection pooling, query parsing/execution
- **Resources:** official docs for each engine (see [resources/github-repositories.md](../resources/github-repositories.md))
- **Checkpoint:** Can you write a query joining two tables and filtering with a `WHERE` clause? Can you explain the difference between a query and a query *plan*?

## Phase 2 — Web Apps, Auth & Sessions 🟢

- How web applications talk to databases (ORMs, drivers, connection strings)
- Authentication flows and session handling
- Where user input enters an application (forms, URL params, headers, cookies, APIs)
- **Checkpoint:** Trace a login form's data flow from browser → server → database → response.

## Phase 3 — How SQL Injection Occurs (Conceptual) 🟢🟡

- The core problem: **mixing code and data** in a single string
- Why string concatenation of untrusted input into queries is dangerous
- Common developer mistakes that introduce SQLi (dynamic query building, trusting client-side validation only, over-privileged DB accounts)
- High-level overview of SQLi categories — taught as *concepts to recognize and defend against*, not as attack tutorials:
  - **In-band / Classic SQLi** — results returned directly in the application response
  - **Error-based SQLi** — database error messages leak structural information
  - **UNION-based SQLi** — combining results of two queries
  - **Blind SQLi** — no visible output; inferred through application behavior
  - **Time-based Blind SQLi** — inferred through response timing
  - **Second-order SQLi** — malicious input stored and triggered later in a different query context
- For each category, focus on: *how would a code reviewer or automated scanner recognize this risk, and what's the one-line fix?*
- **Checkpoint:** Given a code snippet, identify whether it's vulnerable and why — without writing an exploit.

## Phase 4 — Hands-On Practice (Authorized Labs Only) 🟡

- Set up OWASP Juice Shop and DVWA locally (Docker recommended)
- Work through PortSwigger Web Security Academy's SQLi learning path
- Document what you observed and *how you'd fix the vulnerable code* — that's the deliverable, not just "solving" the lab
- See [`labs/README.md`](../labs/README.md) for the full list with setup instructions

## Phase 5 — Secure Coding 🟡🔴

- Prepared statements / parameterized queries (the primary defense)
- ORMs and query builders — when they help and when they don't (raw query escape hatches)
- Stored procedures — benefits and caveats
- Input validation as defense-in-depth (never the *only* defense)
- Output encoding for contexts where query results are rendered elsewhere
- Hands-on: implement the same secure CRUD module in 2+ languages (see [`secure-coding/`](../secure-coding/))

## Phase 6 — Defense in Depth 🔴

- Least-privilege database accounts (per-service, per-function credentials)
- Secrets management (never hardcoded credentials)
- Database hardening (disabling unnecessary features, network segmentation)
- Web Application Firewalls (WAF) — what they catch, what they miss
- Full breakdown: [`defensive-security/DEFENSE-IN-DEPTH.md`](../defensive-security/DEFENSE-IN-DEPTH.md)

## Phase 7 — Detection & Monitoring 🔴

- Logging query patterns and anomalies
- Alerting thresholds for suspicious database activity
- Static Application Security Testing (SAST) for catching SQLi patterns pre-deployment
- Dynamic Application Security Testing (DAST) in authorized environments/CI pipelines

## Phase 8 — Code Review & Threat Modeling 🔴

- Structured code review using [`cheat-sheets/code-review-checklist.md`](../cheat-sheets/code-review-checklist.md)
- Lightweight threat modeling (STRIDE) applied to a data-access layer
- Secure SDLC: where security gates belong in your pipeline

## Phase 9 — Certifications & Career Paths

See [`resources/certifications.md`](../resources/certifications.md) for when to pursue eJPT, Security+, CySA+, PNPT, and (eventually) OSCP.

---

## Suggested Pacing

| Plan | Pace |
|---|---|
| **Weekly** | 1 phase every 1–2 weeks, ~5–8 hrs/week |
| **Monthly milestone** | Phases 1–3 (Month 1) → Phases 4–5 (Month 2) → Phases 6–9 (Month 3) |

Track your own pace in [`PROGRESS-TRACKER.md`](../PROGRESS-TRACKER.md).
