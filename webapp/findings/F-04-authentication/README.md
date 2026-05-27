# Finding ID: F-04 — Authentication Weaknesses

## Severity
Medium

## OWASP Category
OWASP A07:2021 — Identification and Authentication Failures

---

## Overview

During authentication testing of OWASP Juice Shop, multiple weaknesses related to password policy enforcement and authentication hardening controls were identified.

Although the application properly returned generic login error messages, additional testing revealed weak password acceptance and lack of brute-force protection mechanisms.

The assessment focused on evaluating the application's resilience against common authentication-related attack scenarios.

---

## Affected Component

- Application: OWASP Juice Shop
- Module: User Authentication
- Environment: Local Docker Deployment

---

## Testing Approach

Authentication testing was performed through manual interaction with the application's login and registration functionality.

The assessment included:
- invalid login testing
- account enumeration validation
- password policy assessment
- brute-force protection evaluation

---

## Authentication Error Message Validation

### Test 1 — Invalid User Login

Tested credentials:

```text
Email: abc@abc.com
Password: invalidpassword
```

### Observation

The application returned a generic authentication failure message:

```text
Invalid email or password.
```

---

### Test 2 — Valid User with Incorrect Password

Tested credentials:

```text
Email: poojan004@test.com
Password: incorrectpassword
```

### Observation

The application returned the same generic error message:

```text
Invalid email or password.
```

This behavior helps reduce account enumeration risks by avoiding disclosure of whether a specific account exists.

---

## Weak Password Policy Assessment

### Test Performed

A new account registration was attempted using a weak password value:

```text
12345
```

### Observation

The application accepted the weak password successfully during account registration.

This indicates insufficient password complexity enforcement and increases the likelihood of weak credential usage across the platform.

---

## Brute Force Protection Assessment

### Test Performed

Multiple invalid login attempts were performed consecutively against the authentication interface.

### Observation

No observable brute-force protection mechanisms were identified during testing.

The application did not implement:
- account lockout
- CAPTCHA verification
- rate limiting
- authentication delays

This behavior may allow automated password guessing attacks against user accounts.

---

## Evidence Collected

| Screenshot | Description |
|---|---|
| auth-invalid-user.png | Authentication attempt using invalid user credentials |
| auth-valid-user-wrong-password.png | Authentication attempt using valid user with incorrect password |
| auth-weak-password-test.png | Successful registration attempt using weak password |
| auth-no-rate-limit.png | Repeated authentication attempts without brute-force protection controls |

---

## Technical Root Cause

The identified weaknesses appear to stem from insufficient authentication hardening controls and lack of enforced password security policies.

Although generic error messaging was implemented correctly, additional authentication safeguards were not consistently enforced.

---

## Potential Business Impact

If present within a production financial services environment, these weaknesses could increase exposure to:

- credential stuffing attacks
- brute-force password attacks
- weak credential compromise
- unauthorized account access
- increased account takeover risk

Weak authentication controls are commonly targeted by attackers attempting automated access against internet-facing applications.

---

## Risk Assessment

| Category | Rating |
|---|---|
| Likelihood | Medium |
| Impact | High |
| Overall Risk | Medium-High |

---

## Recommended Remediation

The following remediation measures are recommended:

- enforce strong password complexity requirements
- implement rate limiting on authentication endpoints
- apply account lockout protections
- introduce CAPTCHA after repeated failed login attempts
- monitor abnormal authentication activity
- enforce minimum password length and complexity standards

---

## Secure Authentication Recommendations

### Recommended Password Policy

- minimum 12 characters
- uppercase and lowercase characters
- numeric characters
- special characters
- block common dictionary passwords

---

## Conclusion

The assessment identified multiple authentication hardening weaknesses related to password policy enforcement and brute-force protection mechanisms.

While generic authentication error handling was implemented appropriately, additional security controls are necessary to improve resistance against automated authentication attacks and weak credential usage.
