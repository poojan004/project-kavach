# Poojan Web Application Analysis Prompts

## Purpose

These prompts were used to assist with web application security testing activities performed during Project KAVACH. The objective was to understand vulnerabilities, validate findings, and identify possible remediation approaches while maintaining evidence-based analysis.

---

# Prompt 1 – Understanding Application Functionality

```text
Review the following web application page and explain:

1. What functionality is being provided?
2. What user inputs are accepted?
3. What backend processing may occur?
4. Which security risks should be considered?

Provide the explanation in simple language suitable for a security assessment report.
```

---

# Prompt 2 – SQL Injection Assessment

```text
I am testing a web application input field.

Based on the following request and response:

[Paste Request]
[Paste Response]

Help me determine:

1. Whether SQL Injection may be possible.
2. What indicators support the finding.
3. Safe test cases to validate the vulnerability.
4. Possible impact if exploitation is successful.
```

---

# Prompt 3 – Cross-Site Scripting Analysis

```text
Analyze the following application response after an XSS payload was submitted.

[Paste Response]

Determine:

1. Whether the payload executed.
2. Type of XSS observed.
3. Evidence supporting the finding.
4. Potential business impact.
5. Recommended remediation.
```

---

# Prompt 4 – Authentication Review

```text
Review the following authentication workflow.

[Paste Workflow]

Identify:

1. Weak authentication controls.
2. Password policy concerns.
3. Session management issues.
4. Brute-force attack exposure.
5. Security improvement recommendations.
```

---

# Prompt 5 – Authorization Testing

```text
Review the following authenticated request.

[Paste Request]

Determine:

1. Whether authorization controls appear effective.
2. Potential IDOR exposure.
3. Objects that should be access controlled.
4. Additional test cases that should be performed.
```

---

# Prompt 6 – Security Header Validation

```text
Analyze the following HTTP response headers.

[Paste Headers]

Identify:

1. Missing security headers.
2. Incorrect header configurations.
3. Risks created by missing protections.
4. Recommended secure configuration.
```

---

# Prompt 7 – Vulnerability Reporting

```text
Based on the evidence below, help draft a professional vulnerability finding.

[Paste Evidence]

Include:

- Title
- Description
- Technical Details
- Impact
- Risk Rating
- Remediation
- References
```

---

# Prompt 8 – Remediation Verification

```text
Review the before and after implementation.

[Paste Original Code]

[Paste Updated Code]

Explain:

1. What vulnerability existed originally.
2. What security controls were added.
3. Whether the remediation is effective.
4. Any remaining risks.
```

---

# Prompt 9 – SAST Findings Review

```text
Review the following SAST output.

[Paste Findings]

Help classify:

1. True Positive
2. False Positive
3. Risk Severity
4. Recommended Fix
5. Validation Steps
```

---

# Prompt 10 – Executive Summary Support

```text
Summarize the following assessment findings for a non-technical audience.

[Paste Findings]

Focus on:

- Business impact
- Overall risk level
- Key vulnerabilities discovered
- Remediation status
- Recommended next steps
```

---

## Notes

These prompts were used as supporting guidance during the web application security assessment. All findings, conclusions, and remediation recommendations were validated against observed application behavior and collected evidence before inclusion in project deliverables.
