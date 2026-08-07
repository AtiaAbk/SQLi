# 🔍 Code Review Checklist — Data Access Layers

Use this when reviewing any PR that touches database queries.

## Red Flags to Search For
- [ ] String concatenation or f-strings/template literals building SQL with variables (`"SELECT * FROM users WHERE id = " + userId`)
- [ ] `%s` / `.format()` / f-strings used to insert values directly into SQL text (as opposed to driver-level placeholders)
- [ ] Raw query methods on an ORM (`.raw()`, `.executeQuery()`) called with unsanitized input
- [ ] Table or column names built from user input
- [ ] `ORDER BY`/`LIMIT` clauses built from unsanitized user input (a commonly missed injection point)
- [ ] Database errors returned directly to the client/API response
- [ ] Overly broad database credentials (`root`, `sa`, `admin`) used by an application service account

## Questions to Ask
1. Where does the input to this query originate — is any of it user-controlled?
2. Is this using a parameterized query / prepared statement, or is it string-built?
3. If dynamic identifiers (table/column names) are required, is there a strict allowlist?
4. What database privileges does this connection use, and are they minimal?
5. Are errors from this query handled without leaking schema/database details?
6. Is there a test case proving this endpoint safely handles malicious-looking input?

## Approve Checklist
- [ ] All new queries use parameterization
- [ ] No new raw SQL without documented justification
- [ ] Least-privilege DB account confirmed
- [ ] Relevant tests added/updated
