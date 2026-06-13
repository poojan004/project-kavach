# Prompt Log - Shilpa Soni

## Prompt 1

**Prompt:**  
Give me step-by-step guide to setup DVWA and OWASP Juice Shop using Docker.

**Tool used:**  
ChatGPT

**Response:**  
Provided Docker commands to run OWASP Juice Shop on port 3000 and DVWA on port 8080.

**How I used it:**  
I followed the commands in PowerShell and verified both applications opened in browser.

**Where it was wrong:**  
Docker Desktop was not running initially, so the first command failed. I had to start Docker Desktop first.


## Prompt 2

**Prompt:**  
Help me analyze PCAP file in Wireshark and create IOC list.

**Tool used:**  
ChatGPT + Wireshark

**Response:**  
Provided steps to filter HTTP, DNS, and IP traffic and identify client IP, server IP, DNS queries, HTTP requests, and suspicious indicators.

**How I used it:**  
I opened the PCAP in Wireshark, applied filters like `http`, `dns`, and `ip.addr == 145.254.160.237`, then documented findings in `iocs.csv`.

**Where it was wrong:**  
Some details were not visible from screenshots, so I had to open specific packets and share more screenshots.


## Prompt 3

**Prompt:**  
Give me README content for SQL Injection, XSS, IDOR, Authentication Failure, and Command Injection findings.

**Tool used:**  
ChatGPT + DVWA + OWASP Juice Shop

**Response:**  
Provided finding templates with vulnerability name, tool used, exact payload, evidence, business impact, root cause, remediation, and screenshot reference.

**How I used it:**  
I created finding folders under `webapp/findings/` and added README files and screenshots for each vulnerability.

**Where it was wrong:**  
IDOR finding was skipped at first, so I had to go back and complete `F-03-idor` later.


## Prompt 4

**Prompt:**  
Give me synthesis files for threat model, defense-in-depth, executive readout, and retro.

**Tool used:**  
ChatGPT

**Response:**  
Provided content for:
- `synthesis/threat-model.md`
- `synthesis/defense-in-depth.md`
- `synthesis/exec-readout.md`
- `retro.md`

**How I used it:**  
I created the files in VS Code and added the final project summary, STRIDE threat model, defense layers, recommendations, and retrospective.

**Where it was wrong:**  
The requirement mentioned `exec-readout.pdf`, but I first created `exec-readout.md`. It may need to be exported as PDF later.


## Prompt 5

**Prompt:**  
Explain what “joint threat model using STRIDE or PASTA” means and which one we used.

**Tool used:**  
ChatGPT

**Response:**  
Explained that STRIDE includes Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, and Elevation of Privilege.

**How I used it:**  
I confirmed that our project used STRIDE in `synthesis/threat-model.md`.

**Where it was wrong:**  
No major issue. STRIDE was the correct and simpler choice for this project.


## Prompt 6

**Prompt:**  
Give me README file for webapp folder as a whole.

**Tool used:**  
ChatGPT

**Response:**  
Provided a complete `webapp/README.md` covering objective, lab applications, scope, folder structure, findings summary, evidence, SAST note, and conclusion.

**How I used it:**  
I added the README inside the `webapp` folder to summarize all web application security testing work.

**Where it was wrong:**  
No major issue, but the SAST part was documented as planned rather than fully executed.