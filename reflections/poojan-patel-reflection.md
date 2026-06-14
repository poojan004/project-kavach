# Individual Reflection – Poojan Patel

## Project KAVACH

### Q1. Identify a specific packet, frame, or flow in your chosen capture that changed how you thought about what was happening.

The network capture I analyzed was `2025-01-30-XLoader-infection-traffic.pcap`.

The flow that changed my understanding was not a single packet but the repeated pattern of DNS requests followed by outbound HTTP communication from the internal host `10.1.30.242`.

Initially, I assumed the traffic might be related to normal web browsing. However, after filtering DNS traffic in Wireshark, I observed multiple lookups to suspicious domains such as:

* physicsbrain.xyz
* bydotoparca.net
* autonomousrich.xyz
* sigmaque.today
* hotethereum.xyz

The pattern became more suspicious when these DNS lookups were followed by HTTP activity and POST requests to external systems.

At that point, my understanding shifted from "possibly normal browsing traffic" to "likely malware-related communication." This flow helped me understand how network evidence can reveal attacker activity even when malware samples are not available.

---

### Q2. Describe one hypothesis your team formed about the network capture that turned out to be wrong.

One of my early hypotheses was that the traffic could represent normal user browsing mixed with advertising redirects.

This assumption seemed reasonable because the capture contained a large number of DNS requests and external connections that initially looked similar to normal internet activity.

After deeper analysis, this hypothesis became less convincing because:

* Many domains had unusual naming patterns.
* Several domains used uncommon top-level domains.
* DNS requests appeared unrelated to each other.
* External HTTP communication occurred shortly after DNS resolution.
* HTTP POST requests were present.

Based on this evidence, I concluded that the traffic was more consistent with malware activity than normal browsing behavior.

This taught me the importance of validating assumptions with evidence rather than relying on first impressions.

---

### Q3. Pick one vulnerability your team demonstrated in the web environment. Walk through the exact payload progression.

The vulnerability I worked on most extensively was SQL Injection in DVWA.

I began with simple payloads to understand how the backend query behaved.

The first step was determining the number of columns returned by the application.

```sql
1' ORDER BY 1#
```

The application responded successfully.

```sql
1' ORDER BY 2#
```

This also worked.

```sql
1' ORDER BY 3#
```

This generated an error.

From this result, I concluded that the query returned two columns.

After confirming the column count, I moved to UNION-based testing.

```sql
1' UNION SELECT user(), database()#
```

The application returned database information, confirming that SQL Injection was possible.

The most important lesson was that understanding query structure first made exploitation easier and more reliable.

---

### Q4. For the same vulnerability, describe the remediation you wrote at the code level.

The remediation focused on replacing dynamic SQL queries with parameterized queries.

The insecure implementation looked similar to:

```php
$query = "SELECT first_name, last_name FROM users WHERE user_id = '$id'";
```

A safer implementation uses prepared statements:

```php
$stmt = $connection->prepare(
    "SELECT first_name, last_name FROM users WHERE user_id = ?"
);

$stmt->bind_param("i", $id);
$stmt->execute();
```

I selected this remediation because prepared statements separate user input from SQL commands, preventing malicious input from altering query logic.

Although input validation remains important, prepared statements provide a stronger and more reliable defense against SQL Injection attacks.

---

### Q5. Where in the engagement did an LLM mislead you?

One situation where the LLM misled me was during repository organization.

At one stage, additional folders and artifacts were suggested that appeared useful but were not explicitly required by the Project KAVACH brief.

When I reviewed the project document again, I realized that some recommendations were expanding the scope beyond the required deliverables.

I corrected this by comparing every folder and file against the official project instructions before creating or updating repository content.

This experience taught me that AI can significantly accelerate documentation work, but final decisions should always be validated against project requirements and evidence collected during the engagement.

---

### Q6. Identify one finding from network analysis that could connect to the web portal or vice versa.

The network investigation indicated that an internal workstation was likely communicating with suspicious external infrastructure.

In a real-world environment, an infected workstation could become an entry point for additional attacks against internal applications or web portals.

One possible attack path would be:

1. User opens a malicious attachment.
2. Malware infects the workstation.
3. Credentials or browser session information are stolen.
4. An attacker gains access to internal applications.
5. Existing web vulnerabilities increase the impact of the compromise.

The IDOR testing performed in the web assessment demonstrated how weak authorization controls could amplify the damage caused by stolen credentials.

This highlighted how network and web security findings are often connected rather than independent issues.

---

### Q7. What is one defense-in-depth decision you would lose sleep over if you were the CISO?

The decision I would spend the most time evaluating is network segmentation.

Segmentation can significantly reduce the ability of attackers to move laterally after compromising a workstation. However, implementing segmentation across a business environment introduces operational complexity.

Potential challenges include:

* Additional firewall management
* Application connectivity issues
* Increased support effort
* Higher implementation costs

Despite these challenges, I would still recommend segmentation because the network analysis demonstrated how a compromised endpoint can communicate externally and potentially serve as a starting point for larger attacks.

The trade-off between security and operational complexity would require careful planning and executive support.

---

### Q8. Look at your repository commit history. Identify the commit you are most proud of and the commit you would redo.

The commit I am most proud of is:

```text
d110f25
Add security assessment methodology documentation
```

This commit helped establish a structured approach for the engagement. The methodology document defined objectives, testing activities, evidence collection methods, and reporting expectations. Once this foundation was established, the remaining project work became more organized and easier to manage.

The commit I would redo is:

```text
e0f7fc8
Delete doc/test
```

This was part of an early repository cleanup effort while the project structure was still evolving.

If I were doing the project again, I would first finalize the folder structure against the project requirements before making structural changes. While the cleanup itself was not a problem, it reminded me that repository organization should always align with deliverables defined in the project brief.

Overall, the project strengthened my understanding of network forensics, web application security testing, remediation planning, and evidence-based security reporting.
