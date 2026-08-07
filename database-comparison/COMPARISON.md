# 🗄️ Database Engine Comparison

| Engine | Typical Use Cases | Security Features | Authentication | Strengths | Weaknesses |
|---|---|---|---|---|---|
| **MySQL** | Web apps, WordPress-style stacks, read-heavy workloads | Roles/privileges, SSL/TLS connections, `sql_mode` strict settings | Native password, `caching_sha2_password`, LDAP/PAM plugins | Huge ecosystem, fast reads, wide hosting support | Historically permissive defaults; requires care with `sql_mode` |
| **PostgreSQL** | Complex queries, data integrity-critical apps, geospatial (PostGIS) | Row-level security, robust role system, SSL, extensions like `pgcrypto` | `scram-sha-256`, LDAP, certificate auth | Strong standards compliance, extensibility, RLS is excellent for multi-tenant isolation | Slightly steeper ops learning curve |
| **SQLite** | Embedded apps, mobile, local/dev/test environments | File-level permissions; no network-facing auth by default | N/A (file-based) | Zero-config, embedded, great for local dev and labs (used across this repo's labs) | Not built for concurrent multi-user production workloads |
| **MariaDB** | MySQL-compatible deployments wanting more open governance | Similar to MySQL plus additional storage engines, `PARSE_SYSVAR` protections | Same family as MySQL + extensions | Drop-in MySQL alternative, active open governance | Occasional compatibility drift from MySQL over time |
| **Microsoft SQL Server** | Enterprise .NET environments | Always Encrypted, Row-Level Security, Transparent Data Encryption, fine-grained permissions | Windows Auth, SQL Auth, Azure AD | Deep enterprise tooling/integration, strong encryption features | Licensing cost; typically Windows/Azure-centric (though Linux support exists) |
| **Oracle Database** | Large enterprise, legacy systems, high-compliance industries | Virtual Private Database, Data Redaction, fine-grained auditing | Kerberos, PKI, database vault | Extremely mature security tooling, strong compliance features | Complex licensing, steep learning curve |

## Security-Relevant Notes for SQLi Defense

- **Parameterization support** is universal across all six — every modern driver/ORM for each engine supports prepared statements.
- **PostgreSQL's Row-Level Security** is a strong additional layer: even if a query is manipulated, RLS can constrain which rows are visible per session/role.
- **SQL Server's Always Encrypted** and **Oracle's Data Redaction** reduce the impact of a successful data exposure by keeping sensitive columns encrypted/masked at the engine level.
- **SQLite** is ideal for local lab work in this repository precisely because it requires no server setup — but production apps should not rely on it for multi-user, network-exposed workloads.
- Regardless of engine, **the primary SQLi defense is identical**: parameterized queries. Engine-specific security features are defense-in-depth, not substitutes.
