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
# Consolidated Interview Questions

## Revised question list

1. Can you introduce yourself and summarize your DevOps and DevSecOps experience?
2. Can you explain your day-to-day responsibilities in your current role and the major security tools you manage?
3. You mentioned shift-left security. What steps have you taken to integrate security early into the SDLC and CI/CD pipelines?
4. When a security scan identifies vulnerabilities, how do you validate, triage, report, and manage them through remediation?
5. If security gates are not enabled, or a SAST scan reports hundreds of findings, how do you decide whether to block the pipeline or allow the release to proceed?
6. How do you prioritize vulnerabilities using CVSS, exploitability, business impact, affected assets, and CISA Known Exploited Vulnerabilities (KEV)?
7. How do you handle engineering teams that resist vulnerability remediation, dispute findings, or cannot fix vulnerabilities within the agreed timeline?
8. How do you manage vulnerability exceptions, resolve ownership conflicts, enforce remediation SLAs, follow up with teams, and track outstanding vulnerabilities?
9. What is an SBOM, why is it important, and how is it used in vulnerability management and software supply-chain security?
10. What are the characteristics of a good or bad SBOM, and what best practices do you follow to maintain SBOM hygiene?
11. What are Package URL (PURL) and Common Platform Enumeration (CPE), and how are they used to identify software components and vulnerabilities?
12. What is the difference between SAST, SCA, and DAST, and which tools do you use for each?
13. At which stages of the SDLC do you perform SAST, SCA, and DAST, and what types of web application and API scans do you perform?
14. Given a CVE, how do you identify the affected application, vulnerable component, dependency path, and responsible engineering team?
15. What is SQL injection, and how would you identify and remediate it?
16. What is the OWASP Top 10, and what significant changes were introduced in the latest edition?
17. What is CISA KEV, and how do you use it alongside CVSS during vulnerability prioritization?
18. What are direct, recursive, and transitive dependencies? Can you explain transitive dependencies with an example?
19. What hands-on CI/CD pipeline experience do you have, and how have you integrated security tools, policy enforcement, reporting, and quality gates?
20. Are you familiar with the job description, and what questions would you ask to understand the role and its responsibilities?
21. Are you primarily focused on cloud or DevSecOps, and did you begin your career in core DevOps or DevSecOps?
22. Can you explain a real project where you implemented vulnerability management and DevSecOps practices?
23. Who performs vulnerability triage, and which SAST, DAST, SCA, container-scanning, and secret-detection tools have you used?
24. Have you worked only on security-tool configuration, or have you also handled installation, maintenance, monitoring, upgrades, integrations, and console administration?
25. How do you reduce false positives and determine whether a security finding is a true positive or a false positive?
26. If automated scanning identifies hundreds of vulnerabilities in an application that previously had few findings in manual VAPT, how would you investigate the discrepancy and convince the application owner to address the findings?
27. When manual VAPT and automated scans produce different results, how do you validate the findings, inspect code and evidence, and involve developers and security analysts?
28. What are important HTTP security headers, and how do Content Security Policy (CSP) and Cross-Origin Resource Sharing (CORS) help secure web applications?
29. Who is responsible for SBOM generation and scanning in your project, and how do you generate, validate, publish, and maintain an SBOM?

# Interview-Ready Answers: Questions 1–10

## Question 1

Question:

Can you introduce yourself and summarize your DevOps and DevSecOps experience?

Answer:

Thank you for the opportunity. My name is NAME, and I have over four years of experience across DevOps and DevSecOps.

I started my career at TCS as a DevOps Engineer, where I worked on Jenkins-based CI/CD pipelines, build and deployment automation, Docker, Kubernetes, Terraform, Ansible, and cloud infrastructure.

Currently, I work at Talakunchi Networks, deployed to In-Solutions Global, a fintech company that provides payment gateway solutions to banking clients.

My primary responsibility is managing and integrating the DevSecOps security stack into application delivery pipelines. I work with tools such as Fortify for SAST and DAST, Sonatype Lifecycle for SCA, SBOM tooling, Gitleaks for secret detection, and Trivy for container-image scanning.

I also support security-tool administration, vulnerability triage, remediation coordination, reporting, automation, and secure SDLC adoption. Since the project operates in a financial-services environment, security governance, access control, and compliance are important considerations.

My overall focus is to help development teams identify vulnerabilities early, remediate them efficiently, and deliver applications securely without unnecessarily disrupting releases.

## Question 2

Question:

Can you explain your day-to-day responsibilities in your current role and the major security tools you manage?

Answer:

My day-to-day responsibilities primarily involve operating and improving the DevSecOps security stack and supporting its integration with development workflows.

My key activities include:

- Security-tool administration: Managing configurations, user access, integrations, scan operations, and troubleshooting for our security platforms.
- CI/CD integration: Working with Jenkins pipelines and GitLab repositories to integrate security scans into application build and delivery workflows.
- Vulnerability management: Reviewing scan results, validating findings, coordinating with application teams, and tracking remediation.
- SAST and SCA: Working with Fortify to identify source-code vulnerabilities and Sonatype Lifecycle to analyze open-source dependencies and related risks.
- DAST and container security: Supporting Fortify WebInspect scans against running web applications and APIs, and Trivy scans against container images.
- Secret detection: Using Gitleaks to identify potentially exposed credentials and secrets in source repositories.
- Automation and reporting: Using scripts and APIs to collect scan results, aggregate vulnerability metrics, and simplify reporting and operational activities.
- Developer collaboration: Helping developers understand findings, remediation approaches, and secure coding practices.

I also participate in tool onboarding, troubleshooting, and security-process improvements. My primary focus is security engineering and vulnerability management, while I collaborate with DevOps teams on infrastructure and deployment-related activities.

## Question 3

Question:

You mentioned shift-left security. What steps have you taken to integrate security early into the SDLC and CI/CD pipelines?

Answer:

Shift-left security means identifying and addressing security issues as early as possible in the development lifecycle instead of waiting until production or the final security assessment.

In my current project, I support this approach in several ways.

First, we integrate security tools into the existing CI/CD workflows so that vulnerabilities can be identified during development and build activities.

For example:

- Gitleaks helps detect exposed secrets in source-code changes.
- Fortify SAST identifies potential vulnerabilities in application source code.
- Sonatype Lifecycle SCA identifies vulnerable open-source dependencies and evaluates component policies.
- Trivy scans container images for known vulnerabilities.
- Fortify WebInspect DAST tests running applications and supported API endpoints for runtime security issues.

Second, we use security policies and quality gates to identify findings that require action before an application progresses through the delivery process.

Third, we work with development teams to explain findings, recommend fixes, and establish remediation timelines. Where a finding requires further investigation or cannot be fixed immediately, we follow the defined exception and approval process rather than bypassing controls informally.

Finally, we use scan reports and vulnerability trends to identify recurring issues and improve developer awareness.

The objective is to make security a continuous part of software delivery, reduce late-stage remediation costs, and maintain a balance between security requirements and release timelines.

## Question 4

Question:

When a security scan identifies vulnerabilities, how do you validate, triage, report, and manage them through remediation?

Answer:

When a scan identifies vulnerabilities, I follow a structured process from initial validation through closure.

First, I review and validate the findings. I check the vulnerability details, affected application or component, severity, supporting evidence, and whether the finding appears relevant to the application.

For SCA findings, I examine the affected package, installed version, dependency path, and available fixed version. For SAST findings, I review the reported source-code location and vulnerability category. For DAST findings, I review the affected endpoint, request and response evidence, and reproduction details.

Second, I prioritize the findings. I consider CVSS severity, exploitability, known exploitation, exposure, business criticality, and potential impact.

Third, I identify the responsible team. Depending on the finding, this may be the application development team, platform team, infrastructure team, or security team.

Fourth, I communicate the findings. I share the relevant evidence, recommended remediation, severity, ownership, and expected remediation timeline.

Fifth, I track remediation. I monitor progress through the agreed vulnerability-management process and follow up on overdue findings.

Finally, I arrange or review a rescan to verify that the issue has been fixed. If the finding is disputed, I review the supporting evidence with the relevant team. If remediation is not immediately possible, I follow the formal risk-acceptance process.

This approach ensures that findings are not merely reported but are assigned, tracked, remediated, and verified.

## Question 5

Question:

If security gates are not enabled, or a SAST scan reports hundreds of findings, how do you decide whether to block the pipeline or allow the release to proceed?

Answer:

I would not automatically block a release simply because a scan reports hundreds of findings. I would first assess the severity, validity, exploitability, and release risk.

If security gates are not enabled, I would recommend introducing them through an agreed security policy, starting with clearly defined high-risk conditions and expanding the controls as the process matures.

For example, if a scan reports 200 findings, I would:

1. Validate and triage the results to identify actionable findings and potential false positives.
2. Prioritize critical and high-risk issues, considering exploitability, business impact, and whether the application is externally exposed.
3. Apply agreed release criteria. A confirmed critical vulnerability or a high-risk issue that violates the release policy may require the pipeline to fail or the release to be held.
4. Allow lower-risk findings to be tracked with appropriate owners and remediation deadlines where policy permits.
5. Require formal approval for exceptions. If an issue cannot be fixed before release, the designated business or risk owner must approve a documented, time-bound exception with compensating controls where appropriate.

In my project, I work with the development teams and relevant stakeholders to apply security controls without unnecessarily disrupting delivery. Exceptions are subject to the required approval; I do not independently waive security requirements.

The objective is to prevent unacceptable security risks from progressing while ensuring that remediation decisions are consistent, traceable, and risk-based.

## Question 6

Question:

How do you prioritize vulnerabilities using CVSS, exploitability, business impact, affected assets, and CISA Known Exploited Vulnerabilities (KEV)?

Answer:

I use a risk-based approach rather than relying only on the CVSS score.

My prioritization considers five main factors:

1. CVSS severity: The score and severity provide an initial assessment of the technical impact and characteristics of the vulnerability.
2. Exploitability: I check whether a working exploit is available, whether exploitation requires authentication or special conditions, and whether the vulnerability is being actively exploited.
3. CISA KEV: If the vulnerability appears in the Known Exploited Vulnerabilities catalog, I treat it as a strong prioritization signal because it is known to have been exploited in the wild.
4. Asset and business criticality: A vulnerability in an internet-facing payment application or a critical production service may require more urgent attention than a similar finding in an isolated development environment.
5. Exposure and impact: I consider network accessibility, affected functionality, potential data exposure, privilege escalation, and available mitigations.

For example, suppose we identify a high-severity vulnerability in an open-source library used by a payment application. If the vulnerability is actively exploited, the affected application is externally accessible, and a fixed version is available, I would prioritize remediation urgently.

On the other hand, a high CVSS score alone does not always establish the highest operational priority if the component is not actually present or affected. The finding still needs validation.

I use the organization's remediation SLAs and risk policies to assign deadlines, escalate overdue critical findings, and document exceptions where required.

In short, CVSS helps assess technical severity, while exploitability, KEV status, exposure, and business impact help determine the actual remediation priority.

## Question 7

Question:

How do you handle engineering teams that resist vulnerability remediation, dispute findings, or cannot fix vulnerabilities within the agreed timeline?

Answer:

I handle these situations through technical evidence, collaboration, and a clearly defined risk-management process.

First, I understand the team's concern. Sometimes the finding is a false positive, the affected code is not reachable, a dependency upgrade could introduce breaking changes, or the fix requires significant regression testing.

If the team disputes the finding, I review the scanner evidence with them and involve the appropriate security analyst or application security specialist when deeper validation is required.

If the finding is valid but remediation is difficult, I help the team evaluate options such as upgrading to a patched dependency, applying a code fix, removing an unused component, or implementing a temporary compensating control.

I also explain the potential business and security impact so the team understands why remediation matters.

If the team cannot meet the agreed deadline, I ask for the reason, a realistic remediation plan, an accountable owner, and an expected completion date. I track the issue and escalate overdue high-risk findings through the established governance process.

If remediation is genuinely not feasible before release, the team must obtain formal risk acceptance from the authorized business or security owner, with documented justification, compensating controls, and an expiry or review date.

My approach is to help teams resolve issues rather than simply send reports or block releases. However, a team cannot unilaterally ignore a valid, high-risk vulnerability or bypass a mandatory security gate.

## Question 8

Question:

How do you manage vulnerability exceptions, resolve ownership conflicts, enforce remediation SLAs, follow up with teams, and track outstanding vulnerabilities?

Answer:

I manage vulnerability remediation through a centralized and traceable process.

For ownership, I identify the affected application, component, repository, or infrastructure asset and map it to the responsible application or platform team. If multiple teams are involved, I distinguish between the team responsible for the vulnerable component and the team responsible for integrating or deploying it. I coordinate with both teams and establish clear ownership.

For remediation SLAs, I use the organization's severity-based timelines and consider exploitability, exposure, and business criticality. Critical and actively exploited vulnerabilities receive higher priority and closer monitoring.

For follow-ups, I track the assigned owner, finding status, remediation target date, and any blockers. I send reminders for approaching deadlines and escalate overdue findings through the established governance process.

For exceptions, I ensure that the finding, business justification, risk assessment, compensating controls, approving authority, and expiry or review date are documented. An exception is not the same as fixing the vulnerability, and it should not remain open indefinitely without reassessment.

For tracking, I use the available security-tool dashboards, scan reports, and tracking mechanisms to monitor open, in-progress, overdue, remediated, and accepted-risk findings. I also review trends such as recurring vulnerabilities, remediation aging, and SLA compliance.

Once a team reports that a vulnerability has been fixed, I verify the result through an appropriate rescan or other technical evidence before considering it resolved.

This process gives stakeholders visibility into the outstanding risk and helps ensure that remediation remains accountable and measurable.

## Question 9

Question:

What is an SBOM, why is it important, and how is it used in vulnerability management and software supply-chain security?

Answer:

An SBOM, or Software Bill of Materials, is a structured inventory of the components that make up a software application. It can include direct and transitive dependencies, package names, versions, supplier information, unique identifiers, and dependency relationships.

An SBOM is important because modern applications rely heavily on third-party and open-source components. Without a reliable component inventory, it can be difficult to determine whether an application is affected when a new vulnerability is disclosed.

In vulnerability management, an SBOM helps us:

- Identify the libraries and components included in an application.
- Map known vulnerabilities, such as CVEs, to affected component versions.
- Understand direct and transitive dependency relationships.
- Support license and software supply-chain risk analysis.
- Identify which applications may be affected by a newly disclosed vulnerability.
- Improve incident response, compliance evidence, and remediation planning.

In my current project, we work with Sonatype Lifecycle and SBOM-related tooling to analyze open-source components and support software composition analysis.

The general workflow is to generate an SBOM from supported source, build, or artifact inputs, validate the component inventory, evaluate known vulnerabilities and applicable policies, and make the results available to the relevant teams.

An SBOM should be tied to the specific application version or build it describes. It should also be updated and regenerated as dependencies change. An SBOM itself does not guarantee that software is secure; it provides the inventory needed to assess and manage component-related risks.

## Question 10

Question:

What are the characteristics of a good or bad SBOM, and what best practices do you follow to maintain SBOM hygiene?

Answer:

A good SBOM should be accurate, complete for its intended scope, machine-readable, traceable, and maintained throughout the software lifecycle.

The main characteristics of a good SBOM are:

- Accurate component identification: Components should have correct names, versions, supplier information where available, and suitable identifiers.
- Dependency relationships: It should represent direct and transitive dependencies where the generation method supports them.
- Standard format: Formats such as CycloneDX and SPDX support machine-readable exchange and integration with security tools.
- Traceability: The SBOM should be associated with the correct application, version, build, or artifact.
- Freshness: It should reflect the actual components included in the relevant software release.
- Validation: The document should pass format and schema validation, and its generation process should be documented.
- Useful metadata: It should include relevant generation-tool information, timestamps, and other metadata required by the chosen standard and workflow.

A bad SBOM may contain missing or inaccurate versions, duplicate or unidentified components, incomplete dependency relationships, stale inventory data, or components that cannot be reliably mapped to known vulnerabilities. A syntactically valid SBOM can still be incomplete if the generation process misses relevant dependencies.

To maintain good SBOM hygiene, I would:

1. Generate SBOMs consistently through automated CI/CD workflows.
2. Prefer reliable dependency metadata, such as lockfiles and build information, alongside appropriate artifact or image inspection.
3. Validate the output against the selected standard and schema.
4. Associate each SBOM with the correct build or release.
5. Scan components for known vulnerabilities and applicable license or policy violations.
6. Regenerate and retain updated SBOMs as dependencies change.
7. Track tool versions, generation failures, and coverage limitations.
8. Restrict access to sensitive build metadata and protect SBOM artifacts against unauthorized modification.


## Question 11

Question:

What are Package URL (PURL) and Common Platform Enumeration (CPE), and how are they used to identify software components and vulnerabilities?

Answer:

PURL and CPE are standardized identifiers used to identify software packages and products, helping security tools match components to vulnerability information.

- PURL (Package URL): Identifies a software package using details such as package type, namespace, name, version, and optional qualifiers. It is widely used in SBOMs and software composition analysis.
- CPE (Common Platform Enumeration): Provides a standardized naming scheme for identifying applications, operating systems, and hardware platforms, particularly in vulnerability databases and security assessment tools.

For example, a PURL for a Maven package might look like:

`pkg:maven/org.apache.logging.log4j/log4j-core@2.14.1`

This identifies the `log4j-core` package, including its version.

A CPE identifier may represent a specific vendor's product and version in a vulnerability database.

In vulnerability management, security tools use these identifiers to correlate software inventory with known vulnerabilities, such as CVEs. PURL is particularly useful for package-level identification in SBOMs, while CPE is commonly used for product-level identification in vulnerability databases.

However, identifier matching alone is not sufficient. I would also verify the affected version range, dependency context, and applicable vulnerability advisory before concluding that a component is vulnerable.

## Question 12

Question:

What is the difference between SAST, SCA, and DAST, and which tools do you use for each?

Answer:

SAST, SCA, and DAST address different aspects of application security.

- SAST (Static Application Security Testing): Analyzes application source code or supported compiled artifacts without executing the application. It identifies potential coding vulnerabilities such as SQL injection, insecure data handling, and hardcoded secrets, depending on the tool's capabilities. In my project, we use Fortify SAST.
- SCA (Software Composition Analysis): Analyzes third-party and open-source dependencies to identify known vulnerabilities, license risks, and component-related policy violations. We use Sonatype Lifecycle for dependency analysis and vulnerability management.
- DAST (Dynamic Application Security Testing): Tests a running application by sending requests and analyzing responses to identify runtime security weaknesses. We use Fortify WebInspect for supported web application testing.

We also use Trivy for container-image vulnerability scanning and Gitleaks for detecting exposed secrets in repositories.

These tools complement each other. SAST identifies potential weaknesses in our code, SCA identifies risks in third-party components, and DAST tests the application's behavior at runtime. Combining them provides broader coverage across the SDLC.

## Question 13

Question:

At which stages of the SDLC do you perform SAST, SCA, and DAST, and what types of web application and API scans do you perform?

Answer:

I recommend integrating security testing at multiple stages of the SDLC so that issues are detected as early as possible.

- During development and pull requests: Run appropriate SAST and secret-detection checks to identify coding issues and exposed credentials before changes are merged.
- During dependency resolution and builds: Run SCA to analyze direct and transitive dependencies, identify vulnerable packages, and evaluate component policies.
- During container builds: Use tools such as Trivy to scan container images for operating-system and application-package vulnerabilities.
- In CI/CD before release: Apply agreed security policies and quality gates based on severity, exploitability, and organizational requirements.
- In a test or staging environment: Run DAST against a deployed application because the scanner needs a running target.
- Before production and periodically afterward: Perform appropriate security assessments and rescan when major changes, new vulnerabilities, or other risk conditions warrant it.

For DAST, the scan types can include passive and active testing, authenticated and unauthenticated scans, crawling, and tests for common web application vulnerabilities. API testing can include endpoint discovery, authentication and authorization checks, input validation, and tests for injection vulnerabilities.

For APIs, the scanner should be configured with the correct API specification or endpoint information, authentication mechanism, and test environment. Active scans must be carefully controlled to avoid disrupting services or modifying production data.

In my project, I support Fortify WebInspect-based DAST for supported applications. The exact coverage depends on the application, scanner configuration, authentication setup, and approved testing scope.

## Question 14

Question:

Given a CVE, how do you identify the affected application, vulnerable component, dependency path, and responsible engineering team?

Answer:

I follow a systematic process to establish whether the CVE affects our environment and identify who needs to address it.

First, I review the CVE advisory. I check the affected product, package, vulnerable version range, fixed versions, severity, and available remediation guidance.

Second, I search the software inventory and SBOMs. I use SCA platforms such as Sonatype Lifecycle and available SBOM data to identify applications containing the affected component.

Third, I verify the dependency path. I determine whether the component is a direct dependency or a transitive dependency introduced by another package. I also verify whether the vulnerable version is actually present in the relevant build or artifact.

Fourth, I assess applicability and exposure. I consider whether the affected component is used by the application, whether the vulnerable functionality is reachable, and whether the issue affects a production or externally exposed service.

Fifth, I identify ownership. I map the application, repository, build pipeline, and deployment environment to the responsible development or platform team. For a transitive dependency, the team may need to upgrade the parent dependency or apply an approved dependency override.

Finally, I communicate the evidence, risk, recommended fix, and remediation deadline, then track the issue until the fix is verified.

For example, if a CVE affects a logging library, I would use the SBOM and SCA results to find which application versions contain the vulnerable library, confirm the affected version, identify the responsible team, and recommend upgrading to a vendor-supported fixed version.

## Question 15

Question:

What is SQL injection, and how would you identify and remediate it?

Answer:

SQL injection is a vulnerability in which untrusted user input is incorporated into a database query in a way that changes the intended SQL statement. An attacker may exploit it to access unauthorized data, modify records, bypass authentication, or perform other database operations, depending on the application's permissions.

For example, if an application constructs a SQL query by concatenating user input directly into the query string, specially crafted input may alter the query's logic.

I would identify potential SQL injection through SAST, DAST, code review, and controlled security testing.

For remediation:

1. Use parameterized queries or prepared statements rather than concatenating user input into SQL statements.
2. Use safe ORM query methods where appropriate, ensuring they do not construct unsafe dynamic SQL.
3. Apply input validation as a secondary control; validation alone is not a substitute for parameterized queries.
4. Use least-privilege database accounts so the application has only the permissions it requires.
5. Avoid exposing detailed database errors to users, and log relevant security events safely.
6. Retest the affected functionality and run appropriate security scans to verify the fix.

For example, in a Java application, I would recommend using `PreparedStatement` with bound parameters rather than building a query through string concatenation.

The primary remediation is to ensure that user input is treated as data, not executable SQL.

## Question 16

Question:

What is the OWASP Top 10, and what significant changes were introduced in the latest edition?

Answer:

The OWASP Top 10 is a widely used awareness document highlighting major categories of web application security risks. It helps developers, architects, and security teams understand common weaknesses and prioritize secure development practices.

The latest published edition I can confidently identify is the OWASP Top 10: 2025.

Its categories include:

- Broken Access Control
- Security Misconfiguration
- Software Supply Chain Failures
- Cryptographic Failures
- Injection
- Insecure Design
- Authentication Failures
- Software or Data Integrity Failures
- Security Logging and Alerting Failures
- Mishandling of Exceptional Conditions

Compared with the 2021 edition, the 2025 edition gives greater prominence to software supply-chain failures, reflecting the risks associated with dependencies, build systems, development tooling, and third-party components. Security misconfiguration and mishandling exceptional conditions also receive updated emphasis.

In my DevSecOps role, the OWASP Top 10 helps guide secure coding awareness, SAST and DAST coverage, remediation discussions, and application security reviews.

I would not treat it as an exhaustive security checklist. It is a risk-awareness resource that should be combined with threat modeling, secure design, applicable security standards, and application-specific testing.

## Question 17

Question:

What is CISA KEV, and how do you use it alongside CVSS during vulnerability prioritization?

Answer:

CISA KEV stands for the Cybersecurity and Infrastructure Security Agency's Known Exploited Vulnerabilities catalog. It identifies vulnerabilities for which there is evidence of exploitation in the wild.

CVSS and KEV provide different types of information:

- CVSS communicates the technical severity of a vulnerability based on its characteristics and potential impact.
- KEV indicates that a vulnerability is known to have been exploited in real-world attacks.

During vulnerability triage, I would check whether a CVE appears in KEV, review the affected versions, and determine which applications and assets contain the vulnerable component.

If a vulnerable component is used in a critical, externally exposed application and its CVE appears in KEV, I would prioritize it urgently, even if other findings have similar CVSS scores.

I would also consider the availability of a patch, application exposure, business criticality, exploitability, and any applicable regulatory or organizational remediation deadlines.

For example, if an application contains a library affected by a KEV-listed vulnerability and a fixed version is available, I would coordinate an expedited upgrade, assess whether compensating controls are needed, and verify remediation through rescanning.

KEV should not be treated as the only prioritization criterion. Vulnerabilities absent from KEV can still present significant risk, and the appropriate response depends on the complete risk context and the organization's policies.

## Question 18

Question:

What are direct, recursive, and transitive dependencies? Can you explain transitive dependencies with an example?

Answer:

A direct dependency is a package that an application explicitly declares as a dependency. A transitive dependency is a package required by one of those direct dependencies or by another dependency further down the dependency tree.

The term recursive dependency resolution describes the process of following dependencies through multiple levels to identify the complete dependency tree.

For example, suppose a Java application directly depends on Library A. Library A depends on Library B, and Library B depends on Library C.

The dependency relationship is:

- Application → Library A: direct dependency.
- Library A → Library B: transitive dependency from the application's perspective.
- Library B → Library C: another transitive dependency from the application's perspective.

Even if the application team never explicitly added Library C, it may still be included in the built application through the dependency chain.

This matters in SCA because a vulnerable transitive dependency can introduce risk into an application even when developers are unaware of its presence.

I would use the dependency tree, lockfiles, SBOM, and SCA results to identify the component and understand how it was introduced. Remediation may involve upgrading the parent dependency, selecting a compatible version, excluding an unnecessary dependency, or applying a vendor-supported fix.

After the change, I would rebuild the application, rerun SCA, and verify that the vulnerable version is no longer included in the resulting artifact.

## Question 19

Question:

What hands-on CI/CD pipeline experience do you have, and how have you integrated security tools, policy enforcement, reporting, and quality gates?

Answer:

I have worked with Jenkins-based CI/CD pipelines and GitLab repositories, primarily supporting security integration and secure software delivery.

In my current project, development teams maintain application code in GitLab, and Jenkins executes the relevant build and security workflows. I support the integration and operation of security tools within those workflows.

A typical pipeline can include:

1. Source checkout: Retrieve the approved source-code revision.
2. Build and dependency resolution: Compile the application and resolve its dependencies.
3. Secret detection: Run Gitleaks to identify potentially exposed credentials.
4. SAST: Execute Fortify analysis to identify potential source-code vulnerabilities.
5. SCA: Use Sonatype Lifecycle to evaluate open-source dependencies against vulnerability and policy information.
6. Container scanning: Run Trivy against applicable container images.
7. Artifact and report handling: Publish approved build artifacts and make security results available to the relevant teams.
8. Policy enforcement: Apply the configured security gates and escalate findings that violate release criteria.

For DAST, the application must be deployed to an appropriate test environment before the scanner can assess its runtime behavior. Therefore, DAST may run in a separate downstream pipeline or pre-release stage rather than during the initial source-code build.

My work includes supporting tool onboarding, integration troubleshooting, scan operations, vulnerability reporting, and coordination with development teams. I also work with the shared security-library approach used in our Jenkins environment to help standardize security integration across applications.

For quality gates, I recommend using clearly defined policies rather than blocking every finding indiscriminately. Critical findings, known exploited vulnerabilities, and policy-defined high-risk issues should receive appropriate treatment. Exceptions must be documented and approved through the designated process.

The goal is to make security checks repeatable, visible, and consistent across application teams while minimizing unnecessary disruption to delivery.

## Question 20

Question:

Are you familiar with the job description, and what questions would you ask to understand the role and its responsibilities?

Answer:

Yes, I understand that the role focuses on DevSecOps and application security, particularly integrating security into the SDLC, managing vulnerabilities, supporting security tools, and working with engineering teams to improve remediation and compliance.

My experience with CI/CD security integration, SAST, SCA, DAST, container scanning, SBOMs, and vulnerability management is closely aligned with those responsibilities.

I would like to understand a few aspects of the role to see how I can contribute effectively:

1. Security tooling: Which tools are currently used for SAST, DAST, SCA, SBOM management, container security, and secret detection?
2. Responsibilities: Is the role primarily focused on security-tool administration and operations, vulnerability management, pipeline integration, or a combination of these?
3. Vulnerability governance: How are severity-based remediation SLAs, exceptions, and escalations managed across application teams?
4. Scale and coverage: Approximately how many applications and development teams are supported by the centralized DevSecOps function?
5. Success criteria: What are the key expectations for the person joining this role during the first three to six months?

## Question 21: Are you primarily focused on cloud or DevSecOps, and did you begin your career in core DevOps or DevSecOps?

I started my career in core DevOps, working on CI/CD pipelines, deployments, and infrastructure automation. Later, I moved more toward DevSecOps, focusing on integrating security into the software development lifecycle.

In my current ISG project, my primary focus is DevSecOps and application security tooling. I work with CI/CD pipelines, SAST, DAST, SCA, SBOM generation, container scanning, and vulnerability management. From the cloud perspective, I mainly work with AWS, along with hybrid cloud and on-premises environments.

## Question 22: Can you explain a real project where you implemented vulnerability management and DevSecOps practices?

In my current ISG project, we support fintech and payment gateway applications that serve multiple banking clients. Security and compliance are important because of the nature of the applications.

Our DevSecOps team integrates security tools into CI/CD pipelines using Jenkins, GitLab, and shared pipeline libraries. We use Fortify for SAST and DAST, Sonatype Lifecycle for SCA, Trivy for container scanning, and secret-detection tools such as GitLeaks.

When scans identify vulnerabilities, we review the findings, validate their severity and applicability, identify the affected application or dependency, and coordinate with the responsible development team for remediation. After fixes are implemented, we trigger rescans to verify the results.

Our objective is to identify vulnerabilities early, reduce security risks, and maintain security and compliance across application releases.

## Question 23: Who performs vulnerability triage, and which SAST, DAST, SCA, container-scanning, and secret-detection tools have you used?

Vulnerability triage is generally a collaborative process involving the DevSecOps team, application security team, and application development teams.

My role involves reviewing scan results, validating findings, understanding severity and applicability, identifying the affected application or dependency, and coordinating with the responsible team for remediation.

The tools I have worked with include:

- SAST: Fortify Static Code Analyzer.
- DAST: Fortify WebInspect and OWASP ZAP.
- SCA: Sonatype Lifecycle and OWASP Dependency-Check.
- Container scanning: Trivy.
- Secret detection: GitLeaks and GitGuardian.
- Code quality and additional security checks: SonarQube and Snyk.

The exact tools used depend on the application, pipeline, and security requirements.

## Question 24: Have you worked only on security-tool configuration, or have you also handled installation, maintenance, monitoring, upgrades, integrations, and console administration?

My experience includes both security-tool integration and operational support.

I have worked on integrating security tools with Jenkins and GitLab pipelines, configuring scan stages, managing scan parameters, reviewing results, troubleshooting pipeline and tool-related issues, and supporting reporting and remediation workflows.

I also work with security-tool consoles to review findings, manage scan-related configurations, and support teams using the tools.

For installation and upgrades, my involvement depends on the tool and project responsibility. In some cases, the central platform or vendor team handles the underlying installation, while our team supports integration, configuration, validation, and troubleshooting.

My main responsibility is to ensure that security tools are properly integrated, operational, and producing useful results within the SDLC.

## Question 25: How do you reduce false positives and determine whether a security finding is a true positive or a false positive?

I follow a structured validation process.

1. Review the finding: Understand the vulnerability description, severity, affected file or component, and supporting evidence.
2. Check applicability: Verify the affected version, dependency usage, vulnerable code path, and whether the vulnerable functionality is reachable.
3. Validate evidence: For SAST, inspect the code and data flow. For SCA, check the package version and dependency path. For DAST, examine the request, response, and reproducibility.
4. Correlate results: Compare findings with vendor advisories, vulnerability databases, SBOM data, and other scan results where appropriate.
5. Collaborate: Discuss uncertain findings with developers or application security analysts.
6. Document the outcome: Record the evidence and follow the approved process to suppress or mark a finding as a false positive when justified.

I don't suppress findings simply because they are inconvenient. Every suppression should have a technical justification and follow the organization's approval process.

## Question 26: If automated scanning identifies hundreds of vulnerabilities in an application that previously had few findings in manual VAPT, how would you investigate the discrepancy and convince the application owner to address the findings?

First, I would explain that automated scanning and manual VAPT have different coverage and objectives. A manual assessment may focus on selected attack scenarios, while automated tools can identify a large number of code-level, dependency, and container vulnerabilities.

I would investigate the discrepancy as follows:

- Verify the scan configuration, application scope, tool versions, and whether the findings are new.
- Group vulnerabilities by application, severity, vulnerability type, and affected component.
- Validate representative findings to identify false positives, duplicates, and vulnerabilities that are not applicable.
- Correlate SCA findings with dependency trees and SBOM data, and inspect code or runtime evidence where required.
- Prioritize actively exploited vulnerabilities, critical and high-risk issues, internet-exposed components, and vulnerabilities affecting sensitive functionality.
- Share a clear remediation report with the application owner, including evidence, business impact, recommended fixes, and target dates.
- Track remediation through closure and perform rescans to verify fixes.

I would avoid presenting hundreds of findings as equally urgent. Instead, I would provide a risk-based remediation plan so the application team can address the most important issues first.

## Question 27: When manual VAPT and automated scans produce different results, how do you validate the findings, inspect code and evidence, and involve developers and security analysts?

I would first compare the scope, environment, authentication, scan configuration, and testing methodology used by both assessments.

For example, an automated SAST scan might identify a potentially unsafe input flow in the source code, while manual VAPT might not reproduce an exploit in the tested environment. That does not automatically mean the finding is false.

My approach would be:

- For SAST, review the affected code, source-to-sink data flow, input validation, and sanitization.
- For SCA, verify the dependency version, transitive dependency path, vulnerability advisory, and actual usage.
- For DAST/VAPT, review the HTTP requests and responses, authentication context, reproduction steps, and potential impact.
- Check whether environmental controls or compensating controls affect exploitability.
- Discuss the technical evidence with developers and security analysts.
- Document the final decision, remediation action, or justified exception.

The goal is to establish the actual risk rather than automatically trusting or rejecting either assessment. Both automated scanning and manual VAPT provide complementary security coverage.

## Question 28: What are important HTTP security headers, and how do Content Security Policy (CSP) and Cross-Origin Resource Sharing (CORS) help secure web applications?

HTTP security headers help browsers enforce security policies and reduce common web application risks.

Important headers include:

- Content-Security-Policy (CSP): Restricts the sources from which scripts, styles, images, and other resources can load, helping mitigate cross-site scripting (XSS).
- Strict-Transport-Security (HSTS): Instructs browsers to use HTTPS for future connections.
- X-Content-Type-Options: With `nosniff`, helps prevent browsers from interpreting content as a different MIME type.
- X-Frame-Options: Helps prevent clickjacking by restricting framing; CSP's `frame-ancestors` is the more flexible modern alternative.
- Referrer-Policy: Controls how much referrer information the browser sends.
- Permissions-Policy: Controls access to selected browser features.

CSP vs. CORS:

CSP controls which sources a browser is allowed to load resources from. CORS controls whether browser-based JavaScript from one origin can access resources from another origin.

For example, CSP can restrict scripts to approved domains, while CORS can allow a frontend hosted at `https://app.example.com` to call an API hosted at `https://api.example.com`.

Both should be configured according to the application's requirements. CORS is not an authentication or authorization mechanism, and allowing every origin is generally inappropriate for sensitive APIs.

## Question 29: Who is responsible for SBOM generation and scanning in your project, and how do you generate, validate, publish, and maintain an SBOM?

In my current project, SBOM and software composition analysis activities involve the DevSecOps team, application teams, and the relevant security-tool/platform teams, depending on the workflow.

My role focuses on supporting the integration and operation of security tooling, reviewing scan results, and coordinating vulnerability remediation.

The typical SBOM workflow is:

1. Generate: Produce an SBOM from the application's dependencies or build artifacts using a supported tool. Common formats include SPDX and CycloneDX.
2. Validate: Check that the SBOM is valid, contains component names and versions, and includes package identifiers such as PURLs where available.
3. Scan: Use an SCA platform such as Sonatype Lifecycle to identify known vulnerabilities in the listed components.
4. Review: Analyze CVEs, severity, dependency paths, and applicability; prioritize findings based on risk and exposure.
5. Publish and store: Make the SBOM available in the approved repository or SBOM management platform, with appropriate access controls and version association.
6. Maintain: Regenerate the SBOM when dependencies or build artifacts change, rescan for newly disclosed vulnerabilities, and track remediation.

For regulated environments, I would also ensure the SBOM is traceable to the correct application, version, and release, and that required fields and retention practices follow the organization's compliance requirements.



