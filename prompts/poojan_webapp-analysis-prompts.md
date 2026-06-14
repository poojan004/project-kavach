# Poojan Web Application Analysis Prompts

## Purpose

These prompts were used during Project KAVACH to support web application security assessment activities. The prompts helped analyze findings, understand vulnerabilities, validate security controls, and document remediation recommendations.

---

# Prompt 1 – Understanding Application Functionality

```text
Review the functionality of the target web application and identify:

1. Purpose of the page or feature.
2. User inputs accepted by the application.
3. Backend processing that may occur.
4. Potential security risks associated with the feature.

Provide the explanation in simple language suitable for a security assessment report.
```

---

# Prompt 2 – SQL Injection Assessment

```text
I tested the DVWA SQL Injection page using multiple payloads.

Observed Results:

- Input 1 displayed valid user information.
- Input 2 displayed valid user information.
- Input 3 generated a database error.

Based on these observations:

1. Does this indicate SQL Injection?
2. What type of SQL Injection is likely present?
3. What evidence should be included in the report?
4. What remediation should be recommended?
5. What business impact could result from exploitation?
```

---

# Prompt 3 – Cross-Site Scripting (XSS) Analysis

```text
I tested the application using multiple JavaScript payloads.

Observed Results:

- JavaScript alert box executed successfully.
- User-supplied input was reflected in the browser.
- Payload execution occurred without sanitization.

Help me:

1. Identify the XSS category.
2. Explain the security impact.
3. Draft a professional finding description.
4. Recommend remediation steps.
5. Determine the risk severity.
```

---

# Prompt 4 – Authentication Review

```text
I reviewed the application's authentication process.

Observations:

- Weak passwords were accepted.
- No account lockout mechanism was observed.
- Error messages revealed login behavior.

Help identify:

1. Authentication weaknesses.
2. Associated OWASP risks.
3. Business impact.
4. Recommended security improvements.
5. Appropriate severity level.
```

---

# Prompt 5 – Authorization and IDOR Testing

```text
I tested basket-related API requests in OWASP Juice Shop.

Observations:

- Requests were made using different basket IDs.
- Authorization tokens were present.
- Access control behavior was reviewed.

Help determine:

1. Whether IDOR risk exists.
2. Evidence required to support the finding.
3. Proper authorization controls.
4. Recommended remediation.
5. Risk rating for the vulnerability.
```

---

# Prompt 6 – Security Header Review

```text
I reviewed the HTTP response headers returned by the application.

Help identify:

1. Missing security headers.
2. Incorrect header configurations.
3. Risks associated with missing protections.
4. Recommended secure header configuration.
5. Overall security posture of the application.
```

---

# Prompt 7 – Vulnerability Documentation

```text
Based on the collected testing evidence, help draft a professional vulnerability finding.

Include:

- Vulnerability Title
- Description
- Technical Details
- Evidence
- Impact
- Risk Rating
- Remediation
- References
```

---

# Prompt 8 – Remediation Verification

```text
A vulnerability was identified and a remediation was implemented.

Help evaluate:

1. Whether the original vulnerability has been resolved.
2. Security controls introduced by the fix.
3. Any remaining security risks.
4. Additional hardening recommendations.
5. Validation steps that should be performed.
```

---

# Prompt 9 – SAST Findings Review

```text
Review the static application security testing findings.

Help classify:

1. True Positives
2. False Positives
3. Severity Level
4. Remediation Recommendations
5. Verification Approach
```

---

# Prompt 10 – Executive Summary Support

```text
Summarize the web application assessment findings for management.

Focus on:

- Key vulnerabilities discovered
- Overall risk level
- Business impact
- Remediation activities completed
- Recommended next steps

The summary should be concise, professional, and suitable for non-technical stakeholders.
```

---

## Notes

These prompts were used as supporting guidance during the web application security assessment activities performed in Project KAVACH. All findings, conclusions, and remediation recommendations were validated against actual testing evidence collected from DVWA and OWASP Juice Shop environments before inclusion in project deliverables.
