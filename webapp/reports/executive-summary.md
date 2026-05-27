# Web Application Security Assessment — Executive Summary

## Project KAVACH

### Assessment Scope

This assessment was performed as part of Project KAVACH using local, intentionally vulnerable lab applications:

- DVWA
- OWASP Juice Shop

The objective was to identify common web application security weaknesses, validate them with practical evidence, and document business-focused remediation recommendations.

No production systems or third-party targets were tested.

---

## Executive Overview

The web application assessment identified multiple high-impact security weaknesses across input validation, access control, authentication, and configuration areas.

The most serious issue was an Insecure Direct Object Reference vulnerability in OWASP Juice Shop, where an authenticated user was able to access another user's basket data by modifying a numeric object identifier in the API request.

SQL Injection and Cross-Site Scripting were also successfully demonstrated in DVWA, showing how unsafe input handling can allow backend query manipulation and browser-side script execution.

The overall result indicates that the tested applications require stronger server-side validation, strict authorization checks, secure authentication controls, and production-grade hardening before being considered safe for real-world use.

---

## Key Findings Summary

| ID | Finding | OWASP Category | Severity | Status |
|---|---|---|---|---|
| F-01 | SQL Injection | A03 Injection | High | Confirmed |
| F-02 | Cross-Site Scripting | A03 Injection | High | Confirmed |
| F-03 | IDOR / Broken Access Control | A01 Broken Access Control | Critical | Confirmed |
| F-04 | Authentication Weaknesses | A07 Identification and Authentication Failures | Medium-High | Confirmed |
| F-05 | Security Misconfiguration | A05 Security Misconfiguration | Medium | Confirmed |

---

## Most Important Risks

### 1. Unauthorized Data Access

The IDOR finding demonstrated that changing a basket identifier in an authenticated API request allowed access to another user's basket data.

In a real financial services environment, the same weakness could expose customer account details, transaction records, statements, or loan-related information.

This is the most important risk because it directly affects confidentiality and customer trust.

---

### 2. Unsafe Input Handling

SQL Injection and XSS findings showed that user-controlled input was not handled safely.

SQL Injection can allow backend database manipulation or data extraction.  
XSS can allow script execution in a user's browser, which may lead to session theft, phishing, or unauthorized actions.

These issues usually become more dangerous when combined with weak access control or poor monitoring.

---

### 3. Weak Authentication and Hardening Controls

The application accepted weak passwords and did not show visible protection against repeated login attempts.

In a real deployment, this could increase exposure to credential stuffing, brute-force attempts, and account takeover attacks.

The header review also identified permissive CORS behavior and missing browser security hardening headers, which may assist attackers during reconnaissance or client-side exploitation.

---

## Business Impact

If similar weaknesses existed in a production NBFC or financial services platform, the likely business impact would include:

- unauthorized access to customer data
- exposure of transactional or account-related information
- increased risk of account takeover
- regulatory and compliance concerns
- reputational damage
- loss of customer trust
- higher incident response and remediation cost

For a customer-facing financial portal, the combination of broken access control and injection vulnerabilities would be especially serious.

---

## Evidence-Based Observations

The assessment was supported with practical evidence including:

- SQL Injection payload execution
- UNION-based database extraction
- XSS popup execution
- Stored XSS behavior
- authenticated API replay using cURL
- unauthorized basket data access
- weak password acceptance
- repeated login attempts without visible lockout
- response header review

Evidence screenshots are stored under:

```text
webapp/screenshots/
```

Detailed finding reports are stored under:

```text
webapp/findings/
```

---

## Recommended Priority Actions

### Priority 1 — Fix Broken Access Control

Implement strict server-side ownership validation for every object-level request.

Example:

```javascript
if (basket.UserId !== authenticatedUser.id) {
    return res.status(403).send('Forbidden');
}
```

This should be treated as the highest-priority fix because it prevents unauthorized access to user-owned resources.

---

### Priority 2 — Remove SQL Injection Risk

Replace dynamic SQL query construction with parameterized queries or prepared statements.

This prevents attacker-controlled input from changing backend query logic.

---

### Priority 3 — Prevent XSS

Apply proper output encoding and input sanitization before rendering user-controlled data.

A Content Security Policy should also be implemented to reduce browser-side script execution risk.

---

### Priority 4 — Strengthen Authentication

Recommended authentication controls include:

- strong password policy
- rate limiting
- account lockout after repeated failures
- CAPTCHA after suspicious activity
- authentication monitoring
- MFA for sensitive accounts

---

### Priority 5 — Harden Security Configuration

Recommended hardening actions include:

- restrict CORS to trusted origins
- disable verbose errors in production
- add Content-Security-Policy
- add Strict-Transport-Security
- remove unnecessary response headers
- review secure deployment configuration

---

## Overall Risk Rating

The overall web application risk is assessed as:

```text
High
```

Reason:

Although the environment is intentionally vulnerable, the confirmed findings represent real-world vulnerability classes that commonly affect production systems. The IDOR finding in particular demonstrated unauthorized access to another user's resource, which would be a serious issue in any multi-user financial application.

---

## Final Assessment Conclusion

The web application assessment confirmed five OWASP Top 10 aligned findings across injection, access control, authentication, and configuration areas.

The strongest finding was the authenticated IDOR issue, where object identifier manipulation exposed another user's basket data. SQL Injection and XSS further demonstrated unsafe input handling, while authentication and configuration reviews showed gaps in hardening controls.

From a business perspective, the most important recommendation is to prioritize access control enforcement first, followed by secure input handling and authentication hardening.

The project evidence is reproducible from the repository and supported by screenshots, payload notes, remediation guidance, and finding-level documentation.
