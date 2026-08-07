# 🧪 Practice Labs (Legal & Authorized Only)

All labs below are **purpose-built, legally practicable vulnerable applications or platforms** designed for security education. Only practice on these — or on systems you own/have explicit written authorization to test.

---

### 1. OWASP Juice Shop
- **Purpose:** Modern, intentionally-vulnerable web app covering the full OWASP Top 10, including SQLi
- **Difficulty:** Beginner → Advanced (challenge-based scoring)
- **Skills learned:** Recognizing injection points, understanding impact, secure fix mapping
- **Estimated time:** 10–20 hrs for SQLi-relevant challenges
- **Prerequisites:** Docker or Node.js
- **Official link:** https://owasp.org/www-project-juice-shop/

### 2. DVWA (Damn Vulnerable Web Application)
- **Purpose:** Classic PHP/MySQL training app with adjustable difficulty (low/medium/high/impossible)
- **Difficulty:** Beginner → Intermediate
- **Skills learned:** How difficulty/security settings map to code-level defenses; comparing vulnerable vs. "impossible" (secure) source code side by side
- **Estimated time:** 8–15 hrs
- **Prerequisites:** Docker or LAMP stack basics
- **Official link:** https://github.com/digininja/DVWA

### 3. OWASP WebGoat
- **Purpose:** Guided, lesson-based vulnerable app with built-in explanations
- **Difficulty:** Beginner → Intermediate
- **Skills learned:** Structured, explanation-driven learning of SQLi and other injection flaws
- **Estimated time:** 10–15 hrs
- **Prerequisites:** Docker or Java
- **Official link:** https://owasp.org/www-project-webgoat/

### 4. Mutillidae II
- **Purpose:** Broad OWASP Top 10 training app, good for classroom use
- **Difficulty:** Beginner → Intermediate
- **Skills learned:** Wide coverage of vulnerability classes in one app
- **Estimated time:** 8–12 hrs
- **Prerequisites:** XAMPP/Docker
- **Official link:** https://github.com/webpwnized/mutillidae

### 5. PortSwigger Web Security Academy
- **Purpose:** Free, extremely well-explained labs directly from the makers of Burp Suite; arguably the best structured SQLi curriculum available
- **Difficulty:** Beginner → Expert (labeled per lab)
- **Skills learned:** Every SQLi category, with clear "how it works" and "how to prevent it" sections per lab
- **Estimated time:** 20–30 hrs for the full SQLi learning path
- **Prerequisites:** None — browser-based
- **Official link:** https://portswigger.net/web-security/sql-injection

### 6. TryHackMe (SQL-related rooms)
- **Purpose:** Guided, beginner-friendly rooms with structured walkthroughs
- **Difficulty:** Beginner → Intermediate
- **Skills learned:** Guided application of concepts in a browser-based VM
- **Estimated time:** Varies by room (2–6 hrs each)
- **Prerequisites:** Free account
- **Official link:** https://tryhackme.com/

### 7. Hack The Box Academy
- **Purpose:** Structured, authorized modules with theory + practice
- **Difficulty:** Beginner → Advanced
- **Skills learned:** Professional-style methodology and reporting
- **Estimated time:** Module-dependent
- **Prerequisites:** Free/paid account
- **Official link:** https://academy.hackthebox.com/

### 8. Root Me
- **Purpose:** Large catalog of authorized challenges, including SQLi-focused ones
- **Difficulty:** Beginner → Advanced
- **Skills learned:** Broad, self-directed practice
- **Estimated time:** Self-paced
- **Prerequisites:** Free account
- **Official link:** https://www.root-me.org/

### 9. SQLi-Labs (Audi-1)
- **Purpose:** A dedicated, progressively-difficult set of purpose-built SQLi challenges
- **Difficulty:** Beginner → Advanced
- **Skills learned:** Deep, focused SQLi pattern recognition across many query contexts
- **Estimated time:** 15–25 hrs
- **Prerequisites:** Local PHP/MySQL setup or Docker
- **Official link:** https://github.com/Audi-1/sqli-labs

### 10. CTFtime
- **Purpose:** Directory of Capture The Flag competitions (web categories often include SQLi challenges) — all run on isolated, purpose-built infrastructure
- **Difficulty:** All levels
- **Skills learned:** Time-boxed, competitive problem solving
- **Estimated time:** Event-dependent
- **Prerequisites:** None
- **Official link:** https://ctftime.org/

---

## Setup Tip

Most of these run cleanly in Docker:

```bash
# Example: OWASP Juice Shop
docker pull bkimminich/juice-shop
docker run -d -p 3000:3000 bkimminich/juice-shop
```

Always run these in an isolated VM or container, never on a machine with sensitive data, and never expose them to the public internet.
