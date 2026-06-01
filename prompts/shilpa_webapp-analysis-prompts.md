# Shilpa Soni - Web Application Analysis Prompts

## Prompt 1 - Initial Security Review

Review the application and identify anything that appears insecure or unusual.

Look for:

- Input validation issues
- Authorization weaknesses
- Error messages
- Exposed functionality

Provide findings with severity ratings.

---

## Prompt 2 - Injection Testing

Examine user-controlled inputs and determine whether they can influence backend processing.

Check for:

- SQL Injection
- Command Injection
- Input handling weaknesses

List successful payloads and observed responses.

---

## Prompt 3 - Browser-Based Attacks

Test application fields for client-side execution opportunities.

Identify:

- Reflected XSS
- Stored XSS
- Unsafe rendering behavior

Include evidence and screenshots where applicable.

---

## Prompt 4 - Access Control Validation

Determine whether users can access information or functions beyond their assigned permissions.

Review:

- URL manipulation
- Object references
- Resource ownership checks

Document any unauthorized access discovered.

---

## Prompt 5 - Security Findings Review

Summarize the assessment results and prioritize findings based on risk.

For each finding provide:

- Severity
- Likelihood
- Potential Impact
- Suggested Remediation

Focus on practical actions that reduce overall risk.
