# 🧭 OWASP-Aligned Testing Checklist

Based on the structure of the OWASP Testing Guide and ASVS. For use in **authorized** testing (your own apps, staging environments, or approved lab platforms) only.

## Reconnaissance (Understanding, Not Attacking)
- [ ] Map all input points: forms, URL parameters, headers, cookies, file uploads, API request bodies
- [ ] Identify which inputs eventually reach a database query
- [ ] Identify the database engine in use (from docs/config, not error-message probing on systems you don't control)

## Functional Verification
- [ ] Confirm all data-access code uses parameterized queries (via code review, not blind testing)
- [ ] Confirm error messages don't leak stack traces or SQL syntax to end users
- [ ] Confirm database accounts follow least privilege
- [ ] Confirm input validation exists as defense-in-depth (not the sole defense)

## Automated Testing (CI/CD)
- [ ] SAST scan flags any dynamic SQL construction
- [ ] Dependency scan confirms DB drivers/ORM versions are current and patched
- [ ] DAST scan runs against a staging environment you control, with results routed to the dev team

## Reporting (if testing professionally / in a lab)
- [ ] Document the endpoint, the finding, business impact, and a concrete remediation (e.g., "switch to parameterized query using X driver")
- [ ] Reference the relevant OWASP ASVS control or CWE ID (e.g., CWE-89)
- [ ] Retest after remediation

## Reference
- OWASP ASVS: https://owasp.org/www-project-application-security-verification-standard/
- OWASP Testing Guide: https://owasp.org/www-project-web-security-testing-guide/
- CWE-89 (SQL Injection): https://cwe.mitre.org/data/definitions/89.html
