# ✅ Secure Coding Checklist — SQL Injection Prevention

## Primary Defenses (pick at least one — prefer #1)
- [ ] **Use parameterized queries / prepared statements** for all database access
- [ ] **Use a well-maintained ORM** correctly (avoid raw-query escape hatches with unsanitized input)
- [ ] **Use stored procedures** defined with parameterized inputs (not dynamic SQL built inside the procedure)

## Defense in Depth (use in addition to, never instead of, the above)
- [ ] Validate and constrain input types, lengths, formats, and ranges (allowlist over denylist)
- [ ] Apply least privilege to the database account used by the application (no `DROP`/`ALTER` rights for a read-heavy service, for example)
- [ ] Escape output appropriately if query results are rendered elsewhere (HTML, JSON, logs)
- [ ] Never concatenate untrusted input directly into query strings
- [ ] Never build queries dynamically from user-controlled table/column names — use a strict allowlist if dynamic identifiers are unavoidable
- [ ] Disable detailed database error messages in production (avoid leaking schema info)
- [ ] Store credentials in a secrets manager, never in source code
- [ ] Keep database drivers/ORMs patched and up to date

## Testing
- [ ] Include SQLi-focused test cases in your test suite (e.g., inputs like `' OR '1'='1`, `1; DROP TABLE users;--` as *test fixtures*, asserting they are safely handled)
- [ ] Run SAST tooling in CI to flag dynamic query construction
- [ ] Include authorized DAST scanning against staging environments

## Review
- [ ] Every PR touching a data-access layer gets a security-focused review pass
- [ ] New raw SQL requires explicit justification and sign-off
