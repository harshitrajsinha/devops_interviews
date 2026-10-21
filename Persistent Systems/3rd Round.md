## Interview Questions:  Client 1st Round | Client name: Thermo Fisher

1. Can you introduce yourself?
2. Can you explain your day-to-day activities in your current role?
3. You mentioned shift-left security. What major steps have you taken to promote shift-left security?
4. What do you do when you identify a vulnerability?
5. Are you involved in vulnerability handling activities?
6. If a scan report contains vulnerabilities, how do you handle the report?
7. If security gates are not enabled, how would you handle vulnerabilities?
8. How do you prioritize vulnerabilities?
9. How do you decide which vulnerabilities should be fixed first?
10. How do you use CVSS scores to prioritize vulnerabilities?
11. What would you do if a team says they cannot fix a vulnerability?
12. How do you handle vulnerability exceptions?
13. How do you ensure teams fix vulnerabilities within the agreed timeline?
14. How do you follow up with teams on pending vulnerabilities?
15. How do you track outstanding vulnerabilities?
16. How familiar are you with SBOM?
17. What are the characteristics of a good SBOM?
18. What are the characteristics of a bad SBOM?
19. What are some best practices for maintaining good SBOM hygiene?
20. Are you familiar with Package URL (PURL)?
21. Are you familiar with Common Platform Enumeration (CPE)?
22. How do you handle engineering teams that refuse to fix vulnerabilities?
23. How do you handle pushback from engineering teams?
24. How do you resolve ownership conflicts when multiple teams are responsible for a vulnerability?
25. What is the difference between SAST and SCA scans?
26. At what stages of the SDLC do you perform SAST, SCA, and DAST scans?
27. What type of DAST scans do you perform?
28. Do you scan APIs, web applications, or both?
29. Given a CVE, how do you identify which application or component is affected?
30. How do you identify the correct team responsible for fixing a vulnerability?
31. Have you heard of SQL Injection?
32. How do you remediate SQL Injection?
33. Are you familiar with the OWASP Top 10?
34. What changes were made in the latest OWASP Top 10?
35. Which scan is used to identify open-source dependencies?
36. Which scan is used for software composition analysis (libraries)?
37. Which scan is used for source code analysis?
38. Have you heard of KEV (Known Exploited Vulnerabilities)?
39. Have you heard of CISA KEV?
40. Are you familiar with recursive or transitive dependencies?
41. Can you explain transitive dependencies with an example?
42. Have you worked with CI/CD pipelines?
43. Can you explain exactly what you've worked on in your CI/CD pipeline?
44. How have you integrated security tools into your CI/CD pipeline?

45. Are you familiar with the job role and job description? Do you have any questions about it?
46. Are you primarily into cloud or DevSecOps?
47. Did you start your career in core DevOps or DevSecOps?
48. Can you explain one of the projects you've worked on related to vulnerability management and DevSecOps?
49. Who performs vulnerability triaging?
50. Which tools do you use for SAST and DAST?
51. Do you have experience with any other security tools?
52. Have you worked only on tool configuration, or also on maintenance and monitoring?
53. Are you the console administrator for the security tools?
54. How do you reduce false positives?
55. If an application that previously had almost no vulnerabilities in a manual VAPT suddenly reports hundreds of vulnerabilities after onboarding to SAST/DAST, how would you handle it?
56. How do you convince application owners when automated scans report significantly more vulnerabilities than manual VAPT?
57. How do you deal with a large number of vulnerabilities reported by security tools?
58. If manual VAPT and automated scanning produce different results, which one do you trust?
59. How do you differentiate between true positives and false positives?
60. How do you determine whether a finding is a true positive or a false positive?
61. Do you review the codebase to inspect input parameters, headers, and security controls?
62. Do you personally review the code, or do developers perform that analysis?
63. What is your role in validating evidence for false positives?
64. Where does the security analyst fit into the vulnerability validation process?
65. Can you explain important HTTP security headers?
66. Have you heard of Content Security Policy (CSP)?
67. Have you heard about CORS headers?
68. What do you know about SBOM?
69. Why do we need to maintain an SBOM?
70. Who manages SBOM generation and SBOM scanning in your project?
71. How do you generate an SBOM? Can you explain the process?

---

# Questions: Combined follow-up questions into single question


---

# Answers


---


# Persistent Systems – DevSecOps Client Interview Preparation

## Part 1: Consolidated interview question list

The original 71 questions can be consolidated by combining overlapping questions and their follow-ups. The list below preserves the main topics while reducing repetition.

### A. Introduction and role

1. Can you introduce yourself and summarize your current DevSecOps role and day-to-day responsibilities?
2. What steps have you taken to promote shift-left security in the SDLC?
3. Can you explain a real-world project involving DevSecOps, vulnerability management, and security-tool onboarding?
4. Are you primarily focused on cloud engineering, core DevOps, or DevSecOps, and how did you start your career?
5. Are you familiar with the job description, and do you have any questions about the role?

### B. Vulnerability management and prioritization

6. What do you do when a security scan identifies vulnerabilities, and how do you handle the scan report from identification through remediation?
7. How do you handle vulnerabilities when security gates are not enabled in the CI/CD pipeline?
8. How do you prioritize vulnerabilities using CVSS, exploitability, business impact, exposure, and other risk factors?
9. What do you do when an engineering team says it cannot or will not fix a vulnerability, and how do you handle pushback?
10. How do you manage vulnerability exceptions, risk acceptance, and remediation deadlines?
11. How do you follow up with teams and track outstanding vulnerabilities until closure?
12. Who performs vulnerability triage, and how do security analysts, DevSecOps engineers, developers, and application owners collaborate?
13. How do you identify the affected application and the responsible engineering team from a CVE or vulnerability finding?
14. How do you handle ownership conflicts when multiple teams are responsible for a vulnerability?
15. What is CISA KEV, and how does it influence vulnerability prioritization?

### C. SBOM, SCA, and dependency security

16. What is an SBOM, why is it required, and what are the characteristics of a good or bad SBOM?
17. What are the best practices for maintaining SBOM hygiene throughout the software lifecycle?
18. How do you generate an SBOM, and who is responsible for generation, scanning, and maintenance in your project?
19. What are Package URL (PURL) and Common Platform Enumeration (CPE), and how are they used to identify software components?
20. What are direct, recursive, and transitive dependencies? Explain with an example.
21. What is the difference between SAST and SCA, and which tools do you use for each?

### D. SAST, DAST, and application security

22. At which stages of the SDLC do you perform SAST, SCA, and DAST, and how do you integrate them into CI/CD?
23. What types of DAST scans do you perform, and do you scan web applications, APIs, or both?
24. Which tools do you use for SAST, DAST, and other security testing?
25. How do you reduce false positives and distinguish true positives from false positives?
26. How do you validate security findings using code review, request/response evidence, input parameters, headers, and existing security controls?
27. What is your role in validating false-positive claims, and how do security analysts and developers participate?
28. If automated SAST/DAST scans report hundreds of findings after manual VAPT found very few, how do you investigate and explain the difference to application owners?
29. If manual VAPT and automated scans disagree, how do you determine which findings are valid?
30. What is SQL injection, and how do you remediate it?
31. What is the OWASP Top 10, and what are the major changes in the latest edition?
32. What are HTTP security headers, Content Security Policy (CSP), and Cross-Origin Resource Sharing (CORS)?

### E. CI/CD and security-tool operations

33. Can you explain your CI/CD pipeline and the specific responsibilities you have handled?
34. How have you integrated security tools into CI/CD pipelines, and how do you enforce security gates?
35. Have you worked with security-tool configuration, maintenance, monitoring, and administration, or mainly with tool onboarding?
36. How do you manage security-tool access, permissions, scan failures, and operational issues?
37. Which tools and technologies have you used for vulnerability detection, SAST, DAST, SCA, secrets scanning, and container security?

### F. Practical scenarios and engineering collaboration

38. How do you handle a large volume of vulnerabilities without overwhelming engineering teams?
39. How do you ensure remediation SLAs are met and escalate overdue or high-risk findings?
40. How do you explain the value of automated security scanning to teams that rely heavily on manual VAPT?
41. How do you coordinate remediation across development, platform, infrastructure, and security teams?
42. How do you ensure vulnerabilities are not reintroduced after remediation?

## Part 2: Interview-ready answers — Questions 1–10

### Question 1

Question:

Can you introduce yourself?

Answer:

Hi, I’m YOUR NAME, and I have over four years of experience in DevOps and DevSecOps, working across CI/CD pipelines, cloud infrastructure, and application security.

Currently, I work on a fintech project at In-Solutions Global, where my primary responsibility is integrating and managing security tools throughout the software development lifecycle. I work with tools such as Fortify for SAST and DAST, Sonatype for SCA and SBOM, SonarQube for code quality, Trivy for container scanning, and GitLeaks for secrets detection.

My responsibilities include security-tool onboarding, scan execution and monitoring, vulnerability triage, coordinating remediation with development teams, and helping teams follow secure coding practices. I also work with Jenkins, GitLab CI/CD, Docker, Kubernetes, and AWS-based environments.

Since the project operates in the financial services domain, security governance, vulnerability remediation, and compliance are particularly important.

My main focus is to help engineering teams identify and address security issues early, automate security checks in CI/CD pipelines, and improve the overall security posture without unnecessarily slowing down development.

### Question 2

Question:

Can you explain your day-to-day activities in your current role?

Answer:

My day-to-day activities primarily focus on DevSecOps security-tool operations, vulnerability management, and developer enablement.

- Security-tool onboarding: I coordinate with application teams to onboard their applications into security tools and configure the required scanning workflows.
- CI/CD integration: I support the integration and operation of security scans within Jenkins and GitLab pipelines, depending on the application setup.
- Scan monitoring: I monitor scan execution, investigate failures, and troubleshoot issues related to tool connectivity, configuration, authentication, and report generation.
- Vulnerability triage: I review scan results, help distinguish actionable findings from potential false positives, and prioritize vulnerabilities based on severity and risk.
- Remediation coordination: I work with application owners and developers to communicate findings, track remediation progress, and follow up on pending vulnerabilities.
- Security governance: I help teams follow agreed security standards, remediation timelines, access-control requirements, and exception processes.
- Continuous improvement: I identify opportunities to automate repetitive tasks and improve security-tool integrations and reporting.

I also collaborate with development, platform, and security teams to resolve operational issues and improve the effectiveness of security checks across the SDLC.

### Question 3

Question:

You mentioned shift-left security. What major steps have you taken to promote shift-left security?

Answer:

Shift-left security means identifying and addressing security issues as early as possible in the development lifecycle, rather than waiting until pre-production or production.

In my current project, I promote shift-left security through several activities.

First, I help integrate security tools into CI/CD pipelines so that source-code analysis, dependency scanning, secrets detection, and container-image scanning can happen earlier in the build process.

For example, we use Fortify for SAST, Sonatype for SCA and SBOM, GitLeaks for secrets detection, and Trivy for container security scanning, depending on the application's technology stack and pipeline configuration.

Second, I encourage teams to scan feature branches or pull requests where supported, so developers receive feedback before changes are merged.

Third, I help establish security gates based on agreed policies. For example, a pipeline may fail when a new, critical security vulnerability or exposed secret is detected. Existing findings can be handled through an approved baseline or exception process, rather than blocking every build indiscriminately.

Fourth, I work with development teams to explain findings, support remediation, and encourage secure coding practices.

Finally, I promote continuous monitoring of remediation status and recurring vulnerability patterns.

The objective is to make security an integral part of the development workflow, reduce the cost of fixing defects, and prevent vulnerabilities from progressing into production.

### Question 4

Question:

What do you do when you identify a vulnerability?

Answer:

When I identify a vulnerability, I follow a structured process from validation to remediation and closure.

First, I validate the finding. I review the scanner output, affected application or component, vulnerability details, evidence, and whether the finding is applicable to the application. If necessary, I coordinate with the security analyst or developer to investigate potential false positives.

Second, I assess the risk. I consider the CVSS severity, exploitability, whether the vulnerability is known to be exploited, application exposure, business criticality, and the potential impact.

Third, I identify the owner. I map the finding to the responsible application or platform team and communicate the affected component, evidence, recommended remediation, and target timeline.

Fourth, I track remediation. The development team implements the fix, such as upgrading a vulnerable dependency, correcting insecure code, removing an exposed secret, or changing an insecure configuration.

Fifth, I arrange validation. We rerun the relevant security scan or use other appropriate verification methods to confirm that the issue has been resolved.

Finally, I update the tracking record and close the finding when the remediation is verified. If remediation is not immediately possible, I ensure that the risk is documented and handled through the approved exception process.

For a critical vulnerability that is actively exploited or exposed to the internet, I would escalate immediately and coordinate urgent mitigation rather than waiting for the normal remediation cycle.

### Question 5

Question:

Are you involved in vulnerability handling activities?

Answer:

Yes. Vulnerability handling is one of my key responsibilities within the DevSecOps process.

My involvement includes monitoring security scans, reviewing findings, coordinating vulnerability triage, communicating issues to application teams, and tracking remediation progress.

For example, when a Fortify SAST scan or Sonatype SCA scan identifies vulnerabilities, I review the affected code or dependency information, severity, available evidence, and potential impact. I then work with the relevant team to establish ownership and communicate the required remediation.

I also follow up on unresolved findings, help investigate false-positive claims, and support rescanning after fixes are implemented.

For high-risk findings, I ensure the appropriate security and application stakeholders are informed and that remediation or mitigation is prioritized.

I want to clarify that my role is primarily focused on security-tool operations, vulnerability triage, coordination, and remediation tracking. The application developers generally implement code-level fixes, while the security team and application owners make decisions within their respective responsibilities.

### Question 6

Question:

If a scan report contains vulnerabilities, how do you handle the report?

Answer:

When I receive a security scan report, I follow a consistent workflow.

1. Review the report: I check the scan status, application or project identity, scan timestamp, affected files or components, and severity distribution.
2. Validate findings: I examine the evidence and determine whether findings are actionable, potentially duplicated, or require further investigation.
3. Prioritize risks: I consider CVSS, exploitability, internet exposure, business impact, and known exploitation, rather than relying solely on severity labels.
4. Assign ownership: I identify the responsible application or platform team and ensure that each actionable finding has a clear owner.
5. Communicate remediation: I share the finding details, affected component, recommended fix, and applicable remediation SLA.
6. Track progress: I maintain the status of findings, monitor due dates, follow up with owners, and escalate overdue high-risk issues.
7. Verify closure: After remediation, I arrange or review a new scan to confirm that the vulnerability is resolved.

If a team disputes a finding, I review the technical evidence with the relevant stakeholders. If the finding is a false positive, it should be documented and suppressed only through the approved process, with justification.

For vulnerabilities that cannot be fixed within the required timeline, I ensure that the risk, compensating controls, accountable approver, and exception expiry date are documented.

This process provides traceability from detection through verified remediation.

### Question 7

Question:

If security gates are not enabled, how would you handle vulnerabilities?

Answer:

If security gates are not enabled, I would first assess the existing pipeline and understand why enforcement is missing. I would then work with the application, DevOps, and security teams to introduce appropriate controls.

My approach would be gradual and risk-based.

First, I would establish security scanning at suitable pipeline stages—for example, SAST and secrets scanning during development, SCA during dependency resolution or build, and container scanning before image promotion.

Initially, I might run the scans in a reporting or non-blocking mode to establish a baseline and understand the existing vulnerability volume.

Next, I would define policies with the security team, such as blocking new critical vulnerabilities, exposed credentials, or other explicitly prohibited findings. I would also configure approved exception handling to prevent legitimate releases from being blocked without a documented risk decision.

Once the policies are validated, I would enable enforcement at the appropriate gates and monitor pipeline failures, false positives, and remediation trends.

If an existing pipeline has no security gates and vulnerabilities are discovered, I would report and prioritize them, notify the application owners, and escalate critical risks through the established security governance process.

The key point is that the absence of an automated gate does not mean vulnerabilities should be ignored. Until enforcement is implemented, risk must be managed through visibility, ownership, remediation tracking, and appropriate release approvals.

### Question 8

Question:

How do you prioritize vulnerabilities?

Answer:

I use a risk-based approach rather than prioritizing vulnerabilities solely by the number or severity of findings.

The main factors I consider are:

- Severity: CVSS score and severity rating.
- Exploitability: Whether a practical exploit exists and how difficult it is to exploit.
- Known exploitation: Whether the vulnerability appears in CISA's Known Exploited Vulnerabilities catalog or has credible evidence of active exploitation.
- Exposure: Whether the affected application or component is internet-facing, externally accessible, or restricted to an internal network.
- Business criticality: Whether the affected system supports payment processing, sensitive data, authentication, or another critical business function.
- Impact: Potential consequences for confidentiality, integrity, availability, and compliance.
- Remediation feasibility: Whether an upgrade, configuration change, patch, or compensating control is available.

For example, an actively exploited critical vulnerability in an internet-facing payment service would receive immediate attention. A high-CVSS vulnerability in an isolated, non-production component with no applicable exploit path might receive a different priority, although it would still need appropriate tracking.

I also consider the organization's remediation SLAs and any regulatory or contractual requirements.

The final priority should reflect the actual risk to the business, and the rationale should be documented so that application owners understand why one issue must be fixed before another.

### Question 9

Question:

How do you decide which vulnerabilities should be fixed first?

Answer:

I decide based on the combination of technical severity, likelihood of exploitation, potential business impact, and exposure.

For example, suppose we have three findings:

- A critical vulnerability in an internet-facing payment API with evidence of active exploitation.
- A high-severity vulnerability in a dependency used by an internal application.
- A medium-severity vulnerability in a non-production component with limited exposure.

I would prioritize the payment API vulnerability first because it combines high severity, external exposure, and active exploitation. I would coordinate immediate escalation and remediation or mitigation.

Next, I would assess the high-severity dependency vulnerability based on its reachability, exploitability, and the importance of the application. The medium-severity issue would remain tracked under its applicable remediation SLA.

I would also check whether a vulnerable dependency is actually present in the deployed application, whether the affected functionality is reachable, and whether a fixed version is available.

Where a fix is not immediately possible, I would evaluate temporary controls, such as restricting network access or disabling the affected functionality, where technically appropriate.

The final ordering is agreed with the relevant security and application stakeholders, following the organization's risk policy and remediation SLAs.

### Question 10

Question:

How do you use CVSS scores to prioritize vulnerabilities?

Answer:

CVSS, or the Common Vulnerability Scoring System, provides a standardized way to assess the technical severity of a vulnerability. Scores range from 0.0 to 10.0.

The commonly used CVSS severity bands are:

| CVSS score | Severity |
| ---------- | -------- |
| 0.0        | None     |
| 0.1–3.9    | Low      |
| 4.0–6.9    | Medium   |
| 7.0–8.9    | High     |
| 9.0–10.0   | Critical |

I use CVSS as an important input to vulnerability prioritization, but I do not treat it as the only deciding factor.

I review the vulnerability's attack vector, attack complexity, required privileges, user interaction, and potential impact on confidentiality, integrity, and availability. I then combine that information with the application's exposure, business criticality, exploitability, and evidence of active exploitation.

For example, a CVSS 9.8 vulnerability in an internet-facing payment application with a known exploit would normally require urgent remediation. A vulnerability with the same base score might have a different practical priority if the affected component is not present in the deployed application or the vulnerable functionality is demonstrably unreachable.

I also consider threat-informed signals, such as the CISA KEV catalog, and follow the organization's remediation SLAs.

In short, CVSS tells me how severe a vulnerability can be; contextual risk assessment helps me determine how urgently we need to address it.

