## Interview Questions: Client 2nd Round | Client Name: Thermo Fisher

1. Have you designed an end-to-end CI/CD pipeline using Jenkins?
2. Can you briefly explain your approach to designing the CI/CD pipeline?
3. Did you have deployments across multiple environments or just a single environment?
4. What different environments did you use?
5. What is the difference between the lower environments and the production environment?
6. What additional guardrails did you have for production?
7. What tools did you use for application monitoring?
8. What is your experience with vulnerability management?
9. How did you handle false positives when developers claimed a vulnerability was a false positive?
10. What did you do to validate whether a vulnerability was a true positive or a false positive?
11. You mentioned a separate vulnerability management team. Do you know what exactly they do?
12. How comfortable are you relocating to Bangalore?
13. Do you have any questions for me?


# Answers:

## Question 1: Have you designed an end-to-end CI/CD pipeline using Jenkins?

Answer:

Yes, I have worked on designing, maintaining, and enhancing end-to-end CI/CD pipelines using Jenkins and GitLab in my current CLIENT project. My primary responsibility is integrating security checks, standardizing pipelines, onboarding applications, and improving pipeline reliability.

The pipeline starts when a developer pushes code to GitLab. Jenkins checks out the code, builds the application using the appropriate build tool, runs unit tests and code-quality checks, and integrates security scans such as Fortify SAST, Sonatype SCA/SBOM, secrets scanning, and Trivy container image scanning.

We configure quality gates to identify security vulnerabilities and other issues. After successful validation and the required approvals, the build artifact is published to Nexus, and the application proceeds through the deployment process to the appropriate environment.

We also use Jenkins Shared Libraries to standardize reusable pipeline stages across applications. After deployment, we perform health checks and monitor application behavior using Prometheus, Grafana, and centralized logs.

My main focus has been on CI/CD pipeline automation, security integration, vulnerability gates, and troubleshooting, while coordinating with the development and platform teams for deployment-related activities.

## Question 2: Can you briefly explain your approach to designing the CI/CD pipeline?

Answer:

My approach is to make the pipeline automated, repeatable, secure, and easy to troubleshoot.

I generally divide it into these stages:

1. Source code management: Developers commit code to GitLab, following the agreed branching and review strategy.
2. Build and testing: Jenkins checks out the code, builds the application using Maven, Gradle, or the relevant build tool, and runs unit tests.
3. Code quality and security: Integrate SonarQube, Fortify SAST, Sonatype SCA, SBOM generation, secrets scanning, and container image scanning where applicable.
4. Quality gates: Fail the pipeline or block promotion when policy-defined security or quality thresholds are not met.
5. Artifact management: Publish versioned build artifacts to Nexus and maintain traceability between the source commit, artifact, and deployment.
6. Approvals and deployment: Deploy to the appropriate environment after required validations and approvals.
7. Post-deployment validation: Check application health, logs, and service availability, and notify the relevant teams if something fails.

I also prefer using Jenkins Shared Libraries for common stages, externalizing environment-specific configurations, securely managing credentials, and ensuring that the same versioned artifact is promoted across environments rather than rebuilding it separately for production.

## Question 3: Did you have deployments across multiple environments or just a single environment?

Answer:

We worked with multiple environments, not just a single environment. The application lifecycle included development, system integration testing, user acceptance testing, and production.

The purpose was to validate the application progressively before exposing it to production traffic. We performed builds, functional and integration testing, and security validation in the appropriate stages, followed by the required approvals before promoting the release.

We also ensured that environment-specific configurations and access permissions were handled appropriately, while keeping the application artifact consistent across environments.

## Question 4: What different environments did you use?

Answer:

We primarily worked with four environments:

- DEV — Development: Developers integrate their changes, and initial builds and basic validations take place.
- SIT — System Integration Testing: We validate integrations between the application and its dependent services, APIs, and databases.
- UAT — User Acceptance Testing: Business or client stakeholders validate that the application meets the expected functional requirements.
- PROD — Production: The approved application version is released to the live environment serving actual users or business transactions.

The pipeline uses environment-specific configurations and access controls. Movement between environments follows the defined validation and approval process, with stricter controls for production.

## Question 5: What is the difference between the lower environments and the production environment?

Answer:

The main differences are purpose, data sensitivity, access, traffic, availability requirements, and change controls.

In lower environments such as DEV, SIT, and UAT, the focus is on development, testing, integration, and validating new changes. These environments generally have lower traffic and more flexibility for debugging and troubleshooting.

Production handles actual business transactions, so stability, security, availability, and data protection are critical. Changes are controlled through approvals, release procedures, and appropriate access restrictions.

From a CI/CD perspective, lower environments allow us to validate builds, tests, and security scans before release. Production requires stronger deployment safeguards, such as restricted permissions, approval gates, health checks, monitoring, and a rollback or recovery plan.

For a fintech application, we also need to consider sensitive data, auditability, and applicable security and compliance requirements. We should never assume that production data can be freely copied into lower environments; test data should be appropriately masked or synthetic.

## Question 6: What additional guardrails did you have for production?

Answer:

Production had stricter guardrails because any failed deployment or security issue could affect business transactions.

The main guardrails included:

- Approval gates: Required authorization before production deployment.
- Security gates: Review of SAST, SCA, secrets-scanning, and other applicable security results, with policy-defined thresholds for blocking releases.
- Access control: Restricted production permissions based on roles and least privilege.
- Artifact traceability: Deploying approved, versioned artifacts from the artifact repository instead of using unverified builds.
- Configuration and secrets management: Avoiding hardcoded credentials and ensuring that environment-specific secrets are handled securely.
- Deployment validation: Checking application health and service availability after deployment.
- Monitoring and logging: Observing application metrics, errors, and logs after release.
- Rollback and recovery: Maintaining a documented recovery approach if a release causes problems.
- Auditability: Maintaining relevant pipeline logs, approvals, and deployment records.

For higher-risk releases, a rolling or controlled rollout can reduce the impact of a failure. The exact strategy depends on the application architecture and the deployment process.

My contribution was mainly around pipeline security integration, enforcing security checks, standardization, and troubleshooting, in coordination with the teams responsible for production deployment and infrastructure.

## Question 7: What tools did you use for application monitoring?

Answer:

We primarily used Prometheus and Grafana for metrics and dashboards, along with the ELK Stack for centralized logging.

Prometheus collects metrics such as CPU and memory utilization, request rates, error rates, and application or infrastructure health metrics, depending on the configured exporters and instrumentation.

Grafana helps us visualize those metrics through dashboards and identify trends or abnormal behavior. Alerting can notify the responsible team when configured thresholds or alert conditions are triggered.

The ELK Stack — Elasticsearch, Logstash, and Kibana — helps centralize, search, and analyze application and infrastructure logs.

For example, if an application becomes slow or starts returning errors after a deployment, I would check the Grafana dashboards for resource utilization and error trends, then correlate the issue with application logs in Kibana. I would also check the relevant pod or service status, recent deployment changes, and dependencies such as databases or downstream APIs.

This helps us narrow down whether the issue is related to the application, infrastructure, configuration, or a dependent service.

## Question 8: What is your experience with vulnerability management?

Answer:

I have hands-on experience integrating security scanning into CI/CD pipelines and coordinating vulnerability remediation with development and security teams.

In my current project, we use tools such as Fortify for SAST, Sonatype for SCA and SBOM-related analysis, and Trivy for container image scanning, along with other security tools depending on the application and scanning requirements.

The process starts with scanning source code, dependencies, or container images. We review the findings based on severity, exploitability, affected components, and the relevant security policy.

When a valid vulnerability is identified, I coordinate with the development team to understand the affected component and determine the appropriate remediation, such as upgrading a vulnerable dependency, fixing insecure code, or rebuilding an image with a patched base image.

After remediation, we rerun the relevant scans to verify that the issue is resolved and that the pipeline meets the required security gates.

I also help investigate disputed findings, support vulnerability triage, and ensure that security checks are integrated into the development lifecycle rather than being performed only before production releases.

## Question 9: How did you handle false positives when developers claimed a vulnerability was a false positive?

Answer:

I would not dismiss the finding immediately or accept that it was a false positive just because the developer disputed it. I would first review the scan evidence and validate the finding.

I would check the affected file or dependency, the vulnerability details, the affected version, the relevant code path, and the scanner's explanation. For dependency vulnerabilities, I would verify whether the application actually uses the affected component and whether the installed version falls within the vulnerable range.

I would then discuss the evidence with the developer and, when necessary, involve the application security or vulnerability management team.

If the finding is confirmed as a false positive, we follow the approved process to document the justification and apply a suppression or exception in the appropriate tool. If it is a true positive, we coordinate remediation and rerun the scan.

The important point is that a false-positive decision must be evidence-based, documented, and approved according to the team's security policy. We should not simply suppress a finding to make the pipeline pass.

## Question 10: What did you do to validate whether a vulnerability was a true positive or a false positive?

Answer:

I validate the finding using the scanner report, the affected code or component, and the application's actual implementation.

For a SAST finding, I review the affected source-code location, the data flow, the input source, and whether the potentially vulnerable operation can actually be reached. For example, with a possible injection vulnerability, I check whether untrusted input can reach a database query or command without appropriate validation or parameterization.

For an SCA finding, I verify the dependency name and version, compare it with the vulnerable version range, and check whether the affected component or functionality is present in the application.

For a container image finding, I check the image, operating-system package or library, installed version, and whether a fixed version is available.

I also review the scanner's supporting evidence, relevant vendor advisories, and any applicable compensating controls. If the technical evidence is insufficient or the impact is unclear, I consult the application security team rather than making an unsupported decision.

If the vulnerability is genuine, we prioritize remediation based on severity, exploitability, exposure, and business impact. If it is a false positive, we document the evidence and follow the approved exception process.

## Question 11: You mentioned a separate vulnerability management team. Do you know what exactly they do?

Answer:

Yes. A vulnerability management team generally coordinates the lifecycle of vulnerabilities across applications, infrastructure, and other technology assets.

Their responsibilities typically include:

- Vulnerability identification: Collecting findings from security scanners, penetration tests, infrastructure assessments, and other sources.
- Triage and prioritization: Assessing severity, exploitability, exposure, business impact, and remediation urgency.
- Ownership and tracking: Assigning findings to the responsible application, infrastructure, or security teams and tracking them through closure.
- Remediation coordination: Following up with owners, agreeing on remediation timelines, and escalating overdue or high-risk findings.
- Validation and closure: Reviewing remediation evidence or rescanning to confirm that the vulnerability has been addressed.
- False-positive and exception management: Coordinating technical validation, documenting justifications, and ensuring exceptions follow the approved risk-acceptance process.
- Reporting and compliance: Maintaining vulnerability dashboards, reporting remediation status, and providing evidence for audits or applicable compliance requirements.

In my role, I primarily work on the CI/CD and application security side: integrating scanners, reviewing findings, coordinating with developers, helping validate disputed results, and ensuring that remediation is reflected in subsequent scans.

The vulnerability management team provides broader governance, prioritization, tracking, and reporting. The exact division of responsibilities depends on the organization's operating model.

## Question 12: How comfortable are you relocating to Bangalore?

Answer:

Yes, I am comfortable relocating to Bangalore for the right opportunity. My priority is to take up a role where I can contribute my DevSecOps experience, work on challenging technical projects, and continue growing professionally.

I am open to discussing the work arrangement, joining timeline, and relocation expectations based on the project requirements.

## Question 13: Do you have any questions for me?

Answer:

Yes, thank you. I have a couple of questions.

First, could you tell me more about the project, the current CI/CD and DevSecOps setup, and the main challenges the team is looking to address?

Second, I would like to understand the team's responsibilities and how the role works with development, platform engineering, and vulnerability management teams.

Finally, what would you expect the person joining this role to accomplish during the first three months?
