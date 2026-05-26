# Finding ID: F-01 — SQL Injection Vulnerability

## Severity
High

## OWASP Category
OWASP A03:2021 — Injection

---

## Overview

During testing of the DVWA SQL Injection module, it was observed that user-supplied input was being processed directly within backend SQL queries without proper sanitization or parameterized handling.

By manipulating the input parameter with crafted SQL payloads, it was possible to alter backend query behavior, retrieve database-related information, and enumerate internal database structures.

The issue was reproducible consistently under the configured low-security testing mode.

---

## Affected Component

- Application: DVWA (Damn Vulnerable Web Application)
- Module: SQL Injection
- Environment: Local Docker Deployment
- Security Level: Low

---

## Testing Approach

The assessment began with normal application interaction to understand expected behavior before attempting malicious input manipulation.

Initial testing confirmed that the application returned a single user record when valid numeric input was supplied. Further testing focused on identifying whether backend SQL queries could be influenced through crafted payloads.

The testing process included:
- basic injection validation
- query structure discovery
- UNION-based extraction
- database metadata enumeration

---

## Payloads Executed and Observations

### 1. Basic SQL Injection Validation

Payload used:

```sql
1' OR '1'='1
```

### Observation

The application returned multiple records instead of restricting results to a single user ID.

This confirmed that user input was directly influencing backend query execution.

---

### 2. Column Enumeration Using ORDER BY

Payloads tested:

```sql
1' ORDER BY 1#
```

```sql
1' ORDER BY 2#
```

```sql
1' ORDER BY 3#
```

### Observation

The queries using ORDER BY 1 and ORDER BY 2 executed successfully, while ORDER BY 3 generated an application error.

This behavior indicated that the backend query was constructed using two columns.

This step was important because UNION-based payloads require the correct column count to execute successfully.

---

### 3. UNION-Based SQL Injection

Payload used:

```sql
1' UNION SELECT user(), database()#
```

### Observation

The payload successfully returned:
- database user
- active database name

Values observed during testing:
- User: app@localhost
- Database: dvwa

This demonstrated that attacker-controlled SQL statements were being executed successfully against the backend database.

---

### 4. Database Metadata Enumeration

Payload used:

```sql
1' UNION SELECT table_name, table_schema FROM information_schema.tables#
```

### Observation

The application returned internal database metadata including table names and schema references.

This confirmed that the injection vulnerability could be leveraged beyond simple authentication bypass attempts and used for deeper database reconnaissance.

---

## Evidence Collected

| Screenshot | Description |
|---|---|
| sqli-normal-query.png | Normal application behavior using valid numeric input |
| sqli-basic-bypass.png | SQL Injection payload returning multiple user records |
| sqli-column-discovery-success.png | Successful ORDER BY payload execution confirming valid column positions |
| sqli-column-discovery-error.png | Error generated after exceeding valid column count using ORDER BY 3 |
| sqli-union-user-db.png | UNION-based SQL Injection extracting database user and database name |
| sqli-table-enumeration.png | Enumeration of internal database tables using information_schema |

---

## Technical Root Cause

---

## Technical Root Cause

The vulnerability exists because application input is directly concatenated into SQL statements without proper validation or prepared statement handling.

The backend application does not enforce parameterized query execution, allowing malicious input to alter the intended database query structure.

---

## Potential Business Impact

In a real-world financial services environment, successful exploitation of this vulnerability could allow an attacker to:

- bypass access restrictions
- enumerate sensitive backend data
- retrieve internal database information
- identify application structure
- potentially access customer-related records

If left unaddressed in production systems, this type of vulnerability could lead to data exposure, compliance issues, and reputational damage.

---

## Risk Assessment

| Category | Rating |
|---|---|
| Likelihood | High |
| Impact | High |
| Overall Risk | Critical |

---

## Recommended Remediation

The following remediation measures are recommended:

- replace dynamic SQL queries with parameterized queries
- validate and sanitize all user-controlled input
- restrict unnecessary database permissions
- disable verbose database error messages
- implement centralized input validation routines

---

## Secure Coding Recommendation

### Vulnerable Pattern

```php
$query = "SELECT * FROM users WHERE id = '$id'";
```

### Recommended Secure Approach

```php
$stmt = $pdo->prepare("SELECT * FROM users WHERE id = ?");
$stmt->execute([$id]);
```

---

## Conclusion

The testing confirmed that the SQL Injection vulnerability allowed backend query manipulation through unsanitized user input.

The issue was successfully leveraged to:
- alter query logic
- enumerate query structure
- retrieve database details
- access internal metadata

The findings demonstrate the importance of secure query handling and proper server-side input validation within web-facing applications.
