# 🎓 Influential Research & Reference Papers

> Search these titles on Google Scholar or the venue's official archive for the authoritative, current link — venue URLs shift over time.

## Foundational SQL Injection Research
- Halfond, W. G., Viegas, J., & Orso, A. — *"A Classification of SQL-Injection Attacks and Countermeasures"* (IEEE ISSSE) — a widely-cited taxonomy of SQLi types and defense categories
- Boyd, S. W., & Keromytis, A. D. — *"SQLrand: Preventing SQL Injection Attacks"* — early academic proposal for randomizing SQL keywords as a defense
- Su, Z., & Wassermann, G. — *"The Essence of Command Injection Attacks in Web Applications"* (POPL) — formalizes the code/data confusion problem underlying SQLi

## Detection & Static/Dynamic Analysis
- Livshits, V. B., & Lam, M. S. — *"Finding Security Vulnerabilities in Java Applications with Static Analysis"* — foundational static taint-analysis work applicable to SQLi detection
- Kieyzun, A., Guo, P. J., Jayaraman, K., & Ernst, M. D. — *"Automatic Creation of SQL Injection and Cross-Site Scripting Attacks"* — dynamic test-generation research for finding injection flaws in authorized test contexts

## Prepared Statements & Mitigation
- NIST — *Guide to General Server Security* (SP 800-123) and related NIST SP 800-series publications on secure configuration
- MITRE — CWE-89 entry (SQL Injection) includes structured mitigation guidance and mapped real-world examples: https://cwe.mitre.org/data/definitions/89.html

## Runtime Protection
- Research on Runtime Application Self-Protection (RASP) approaches for injection defense — search recent USENIX Security / IEEE S&P proceedings for current work, as this is an active area

---

### How to Use This List
Use these as **conceptual grounding**, not attack tutorials — academic SQLi papers are almost always framed around detection, classification, and mitigation, which aligns directly with this repository's defensive focus.
