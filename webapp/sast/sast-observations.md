# Static Application Security Testing (SAST) Observations

## Overview

As part of the web application security assessment, lightweight Static Application Security Testing (SAST) concepts and secure coding review practices were considered during analysis activities.

The primary focus of the assessment was dynamic testing against intentionally vulnerable applications running within a controlled Docker-based environment. However, secure coding observations were also documented based on identified vulnerability patterns.

---

# Objective

The purpose of the SAST review activity was to identify:
- insecure coding patterns
- unsafe input handling
- missing validation controls
- weak authentication logic
- insecure configuration practices

---

# Scope

Applications reviewed during testing:

- DVWA (Damn Vulnerable Web Application)
- OWASP Juice Shop

Environment:

- Local Docker deployment
- Controlled security lab environment

---

# Key Secure Coding Observations

## 1. Unsafe SQL Query Construction

Observed Pattern:

```php
$query = "SELECT * FROM users WHERE id = '$id'";
```

### Risk

Direct concatenation of user-controlled input into SQL statements increases exposure to SQL Injection vulnerabilities.

### Recommended Secure Practice

Use parameterized queries or prepared statements.

---

## 2. Missing Output Encoding

Observed Pattern:

```php
echo $_GET['name'];
```

### Risk

Rendering untrusted user input directly into HTML responses may allow Cross-Site Scripting attacks.

### Recommended Secure Practice

Apply secure output encoding before rendering user-controlled data.

---

## 3. Weak Authorization Validation

Observed Pattern:

```http
GET /rest/basket/:id
```

### Risk

Predictable object references without ownership validation may allow unauthorized resource access.

### Recommended Secure Practice

Enforce strict server-side authorization checks for every resource request.

---

## 4. Weak Authentication Hardening

Observed Behaviors:
- weak password acceptance
- no visible brute-force protections
- no rate limiting controls observed

### Risk

Weak authentication controls increase exposure to automated credential attacks.

### Recommended Secure Practice

Implement strong password policies, rate limiting, and account protection mechanisms.

---

## 5. Missing Security Headers

Observed Missing Headers:
- Content-Security-Policy
- Strict-Transport-Security

### Risk

Missing browser security headers may increase exposure to client-side attacks and transport security weaknesses.

### Recommended Secure Practice

Apply secure response header hardening policies in production environments.

---

# Secure Development Recommendations

The following secure development practices are recommended:

- secure-by-default coding standards
- centralized input validation
- secure output encoding
- parameterized database queries
- strict authorization middleware
- dependency vulnerability monitoring
- regular code reviews
- automated security scanning integration

---

# Suggested SAST Tools

The following SAST tools may be integrated into CI/CD pipelines for automated source code analysis:

| Tool | Purpose |
|---|---|
| SonarQube | Secure code quality analysis |
| Semgrep | Lightweight rule-based security scanning |
| Bandit | Python security analysis |
| ESLint Security Plugin | JavaScript security linting |
| GitHub CodeQL | Automated code scanning and vulnerability detection |

---

# Assessment Notes

This project primarily focused on Dynamic Application Security Testing (DAST) activities using real-world attack simulations within intentionally vulnerable applications.

The SAST observations included in this document are based on:
- identified vulnerability patterns
- insecure coding behaviors
- exposed application responses
- secure coding best practice analysis

---

# Conclusion

The assessment identified multiple coding and configuration patterns commonly associated with OWASP Top 10 security risks.

Applying secure coding standards together with automated SAST tooling can significantly reduce exposure to injection attacks, authentication weaknesses, authorization flaws, and security misconfigurations during the software development lifecycle.
