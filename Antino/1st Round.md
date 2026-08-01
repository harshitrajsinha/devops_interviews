# Int Que

1. Introduce yourself.

2. Suppose you are designing a **highly available three-tier application** on any **cloud** platform. How would you design it? Walk me through the architecture and explain the key considerations.

3. What is the difference between **Horizontal Scaling** and **Vertical Scaling**? How would you implement **Auto Scaling** in the cloud?

4. What is **SAST**? Where does it fit into your **CI/CD pipeline**?

5. How is **DAST** different from **SAST**? Where would you execute **DAST** in the **CI/CD pipeline**?

6. How does **Pod-to-Pod communication** happen in **Kubernetes**?

7. How do you scan **Container Images** for vulnerabilities in a **CI/CD pipeline**? Explain where the image scanning stage fits and what happens if vulnerabilities are found.

8. How do you handle a **Merge Conflict** in a **shared Git branch**?

9. How would you undo a **bad commit** that has already been pushed to a **shared branch**? Which **Git command** would you use?

10. What are the **Three Pillars of Observability**? Name them and explain each one along with a tool used for it.

11. Suppose your **Production** environment is down. Walk me through how you would handle the **first 15 minutes** of the incident.

12. How do you enforce the **Principle of Least Privilege** using **IAM** in a **Cloud Environment** at scale?

13. How would you securely manage **Secrets** and **Credentials** used by **CI/CD Pipelines** to access **Cloud Resources**?

14. How do you tune a **SAST Tool** to reduce **False Positives** without missing real vulnerabilities? Also explain how you handle **Suppressions**.

15. Compare **SonarQube**, **Checkmarx**, and **Semgrep**. Explain their differences, strengths, limitations, and use cases.

16. What are the **limitations of DAST**, and how do you compensate for those limitations?

17. Walk me through your **End-to-End Vulnerability Management Lifecycle**. Also explain your **role and responsibilities** throughout the process.

18. How would you secure a **Kubernetes Cluster** against common **Attack Vectors**?

19. What are the **Image Security Best Practices** you enforce for **Docker/Container Images**?

20. What is **Terraform State Drift**?

21. How do you **detect**, **prevent**, and **fix Terraform State Drift**?

22. How would you design **DDoS Protection** for a **Public-facing API** across **Layer 3 (L3)**, **Layer 4 (L4)**, and **Layer 7 (L7)**?






# Ans

## Question 1

**Question:**

Introduce yourself.

**Answer:**

Sure. I'm a **DevSecOps Engineer with around 4+ years of experience** in building secure CI/CD pipelines, cloud infrastructure, and DevSecOps automation.

I started my career as a **DevOps Engineer at TCS**, where I primarily worked on CI/CD pipeline development, AWS infrastructure, deployment automation, and operational support. Later, I transitioned into a **DevSecOps Engineer** role, where my focus shifted towards integrating security throughout the Software Development Lifecycle.

In my recent project for a **FinTech client**, I was responsible for implementing DevSecOps practices to support **PCI-DSS compliance**. I worked on integrating **SAST, SCA, SBOM, Secret Scanning, Container Image Scanning, and DAST** into Jenkins-based CI/CD pipelines. We also used **GitLab CI** and **Azure DevOps** for specific workloads.

My technical stack includes **AWS, Azure, Docker, Kubernetes, Terraform, Jenkins, SonarQube, Fortify, Trivy, Nexus, Prometheus, Grafana, and Linux**. I have experience supporting both **VM-based** and **Kubernetes-based** deployments in hybrid cloud environments.

Overall, my role has been to automate secure deployments, improve developer experience through DevSecOps automation, and ensure applications are deployed securely while meeting compliance requirements.



# Question 2

**Question:**

Suppose you are designing a **highly available three-tier application** on any **cloud** platform. How would you design it? Walk me through the architecture and explain the key considerations.

**Answer:**

Before designing the architecture, I would first gather the business requirements such as expected traffic, availability targets, compliance requirements, disaster recovery objectives, and whether any components need to remain on-premises.

For an AWS-based three-tier application, my architecture would be:

* **Presentation Layer:** Deploy the web application behind an **Application Load Balancer (ALB)** across multiple Availability Zones with Auto Scaling enabled.
* **Application Layer:** Deploy application services on **EKS** or EC2 Auto Scaling Groups across multiple Availability Zones to ensure high availability.
* **Database Layer:** Use **Amazon RDS Multi-AZ** for relational databases or another managed database service depending on the workload. For highly sensitive workloads, the database could remain on-premises if required by compliance.

For infrastructure provisioning, I would use **Terraform** to maintain Infrastructure as Code.

For networking:

* Deploy resources inside a **VPC**.
* Place public components in **Public Subnets** and application/database components in **Private Subnets**.
* Control access using **Security Groups** and **Network ACLs**.

For security:

* Store secrets in **AWS Secrets Manager** or **Azure Key Vault**.
* Apply least privilege using **IAM Roles**.
* Enable encryption for data at rest and in transit.

For observability:

* Use **Prometheus** and **Grafana** for monitoring.
* Configure centralized logging and alerting.

For CI/CD:

* Build and deploy using **Jenkins**.
* Integrate **SonarQube, SAST, SCA, Trivy, and Secret Scanning** before deployment.

This design provides high availability, scalability, security, and operational visibility while supporting production workloads.



# Question 3

**Question:**

What is the difference between **Horizontal Scaling** and **Vertical Scaling**? How would you implement **Auto Scaling** in the cloud?

**Answer:**

**Vertical Scaling** means increasing the resources of an existing instance, such as adding more CPU, memory, or storage. It is simple to implement but has hardware limits and may require downtime.

**Horizontal Scaling** means adding or removing multiple application instances based on workload. It provides better availability, fault tolerance, and scalability, making it the preferred approach for cloud-native applications.

For Auto Scaling, I would configure scaling policies based on metrics such as:

* CPU utilization
* Memory utilization
* Request count
* Network traffic
* Custom CloudWatch metrics

In AWS, I would use **Auto Scaling Groups** with an **Application Load Balancer** for EC2 workloads.

For Kubernetes, I would configure:

* **Horizontal Pod Autoscaler (HPA)** for scaling pods.
* **Cluster Autoscaler** for scaling worker nodes when required.

This ensures the application automatically scales during traffic spikes and scales down during low utilization, optimizing both availability and infrastructure cost.



# Question 4

**Question:**

What is **SAST**? Where does it fit into your **CI/CD pipeline**?

**Answer:**

**SAST (Static Application Security Testing)** analyzes the application's source code or binaries without executing the application. It helps identify security vulnerabilities early in the development lifecycle, such as SQL Injection, Cross-Site Scripting, insecure coding practices, hardcoded credentials, and other OWASP Top 10 issues.

In our CI/CD pipeline, SAST runs immediately after the source code is checked out, typically before or immediately after the build stage depending on the tool.

Our pipeline generally follows this sequence:

Git Checkout → Secret Scan → SAST → SCA/SBOM → Build → Container Image Scan → Push Image → Deploy → DAST

Running SAST early allows developers to fix vulnerabilities before deployment, reducing remediation cost and improving overall software security.



# Question 5

**Question:**

How is **DAST** different from **SAST**? Where would you execute **DAST** in the **CI/CD pipeline**?

**Answer:**

The primary difference is that **SAST** analyzes the application code without executing it, whereas **DAST** tests a running application from the outside by simulating real-world attacks.

SAST is used during development to identify coding vulnerabilities.

DAST is performed after the application has been deployed to a testing environment such as UAT or QA because it requires a running application.

DAST can identify issues such as:

* Authentication and authorization flaws
* Security misconfigurations
* Session management issues
* Missing security headers
* Runtime vulnerabilities

In our pipeline, DAST runs after deployment to the test environment and before production release using tools like **OWASP ZAP**. This complements SAST because some runtime vulnerabilities cannot be detected through static code analysis alone.



# Question 6

**Question:**

How does **Pod-to-Pod communication** happen in **Kubernetes**?

**Answer:**

In Kubernetes, every Pod receives its own unique IP address, allowing Pods to communicate directly without NAT.

Pod networking is provided by the **Container Network Interface (CNI)** plugin such as Calico, Flannel, or Cilium. These plugins ensure network connectivity across worker nodes.

By default, Pods can communicate with each other unless restricted.

To control communication, Kubernetes provides **Network Policies**, which define which Pods are allowed to send or receive traffic.

For application communication, we generally expose Pods using **Services** such as ClusterIP instead of directly accessing Pod IPs because Pod IPs can change during restarts or rescheduling.

This architecture provides reliable service discovery while allowing fine-grained network security.



# Question 7

**Question:**

How do you scan **Container Images** for vulnerabilities in a **CI/CD pipeline**? Explain where the image scanning stage fits and what happens if vulnerabilities are found.

**Answer:**

In our project, we use **Trivy** for container image scanning.

The image scanning stage is executed after the Docker image is built but before it is pushed to the container registry.

The pipeline flow is:

Source Code → Secret Scan → SAST → SCA → Build Docker Image → **Trivy Image Scan** → Push to Nexus → Deploy

Trivy scans:

* Base image vulnerabilities
* OS packages
* Installed libraries
* Application dependencies
* Misconfigurations (if enabled)

We define severity thresholds in the pipeline.

If **Critical** or **High** vulnerabilities exceed the allowed threshold, the pipeline fails, preventing vulnerable images from reaching the registry or production.

Only images that pass the security policy are pushed to **Nexus** and deployed.

This approach ensures vulnerable container images are blocked early in the deployment process.



# Question 8

**Question:**

How do you handle a **Merge Conflict** in a **shared Git branch**?

**Answer:**

First, I identify the conflicting files and understand why the conflict occurred by reviewing the Git history and recent commits.

Next, I pull the latest changes from the target branch, resolve the conflicts manually, verify that no functional changes are lost, and test the application locally.

If the conflict affects multiple developers, I coordinate with the respective team members to ensure the correct implementation is retained.

After successful validation, I commit the resolved changes and push them for review.

In production environments, good branching strategies, frequent rebasing or merging, and smaller pull requests significantly reduce merge conflicts.



# Question 9

**Question:**

How would you undo a **bad commit** that has already been pushed to a **shared branch**? Which **Git command** would you use?

**Answer:**

If the commit has already been pushed to a shared branch, I prefer using **`git revert`** because it safely creates a new commit that reverses the previous changes without rewriting Git history.

This is the recommended approach for shared branches since other team members may already have pulled the commit.

I would identify the commit hash and execute:

```bash
git revert <commit-id>
```

If the commit has **not** been shared with others, commands like **`git reset`** can be used, but for production or collaborative branches, **`git revert`** is the safer and industry-standard approach.



# Question 10

**Question:**

What are the **Three Pillars of Observability**? Name them and explain each one along with a tool used for it.

**Answer:**

The three pillars of observability are:

**1. Metrics**
These are numerical measurements collected over time, such as CPU usage, memory utilization, request latency, and error rates. Metrics help identify trends and trigger alerts.

**Tool:** Prometheus

**2. Logs**
Logs provide detailed records of application and system events. They help investigate failures, exceptions, and operational issues.

**Tool:** ELK Stack (Elasticsearch, Logstash, Kibana)

**3. Traces**
Distributed tracing follows a request as it travels across multiple microservices, helping identify latency bottlenecks and service dependencies.

**Tool:** Jaeger or OpenTelemetry

In production, these three pillars work together. Metrics alert us that an issue exists, logs help determine what happened, and traces identify exactly where the request failed across distributed services. This combination enables faster troubleshooting and root cause analysis.


## Question 11

**Question:**

Suppose your **Production** environment is down. Walk me through how you would handle the **first 15 minutes** of the incident.

**Answer:**

My first priority is **service restoration**, followed by root cause analysis.

First, I would verify the scope of the incident—whether it affects all users or only specific services—and acknowledge the incident through the appropriate communication channel.

Next, I would quickly determine whether the issue is related to the **application, infrastructure, Kubernetes, database, or network**.

Based on the findings:

* Check monitoring dashboards like **Prometheus** and **Grafana** for alerts.
* Review application and infrastructure logs.
* If it's Kubernetes, use commands like `kubectl get pods`, `kubectl describe pod`, and `kubectl logs`.
* If it's infrastructure-related, verify VM or cloud resource health and check whether any recent infrastructure changes or Terraform drift occurred.
* If a recent deployment caused the issue, consider a rollback to restore service quickly.

Once the service is restored, I would perform a detailed **Root Cause Analysis (RCA)**, document the incident, identify preventive actions, and communicate updates to stakeholders throughout the process.

The priority is always **Restore Service → RCA → Prevent Recurrence**.



# Question 12

**Question:**

How do you enforce the **Principle of Least Privilege** using **IAM** in a **Cloud Environment** at scale?

**Answer:**

The Principle of Least Privilege means every user, application, or service should receive only the permissions required to perform its task—nothing more.

At scale, I enforce this by:

* Using **IAM Roles** instead of long-term user credentials wherever possible.
* Implementing **Role-Based Access Control (RBAC)** so permissions are assigned based on job responsibilities.
* Following a **default deny** approach and granting only the minimum required permissions.
* Using temporary credentials through role assumption instead of permanent access keys.
* Regularly reviewing and removing unused or excessive permissions.
* Granting elevated privileges only for a limited duration and revoking them immediately after the activity is completed.
* Storing permissions as code wherever possible for better auditing and consistency.

This approach minimizes the attack surface while maintaining operational efficiency.



# Question 13

**Question:**

How would you securely manage **Secrets** and **Credentials** used by **CI/CD Pipelines** to access **Cloud Resources**?

**Answer:**

Sensitive credentials should never be hardcoded in source code or pipeline scripts.

In our environment, we use **Jenkins Credentials** for securely storing pipeline secrets and **HashiCorp Vault** for centralized secret management. Cloud-native secret managers like **AWS Secrets Manager** or **Azure Key Vault** are also excellent options.

The pipeline retrieves secrets dynamically during execution rather than storing them in the repository.

Some security best practices include:

* Encrypt secrets at rest.
* Rotate credentials regularly.
* Use IAM Roles instead of static access keys wherever possible.
* Restrict access using least privilege.
* Mask secrets in pipeline logs.
* Audit secret access through logging.

This ensures credentials remain secure while allowing automated deployments.



# Question 14

**Question:**

How do you tune a **SAST Tool** to reduce **False Positives** without missing real vulnerabilities? Also explain how you handle **Suppressions**.

**Answer:**

Fine-tuning a SAST tool starts with aligning its policies to the organization's security and compliance requirements.

For example, in our project, we prioritize rules relevant to **PCI-DSS** and **OWASP Top 10**, rather than enabling every available rule.

To reduce false positives:

* Enable only relevant rule sets.
* Customize severity thresholds.
* Update scan configurations based on application technology.
* Validate findings before marking them as false positives.

When a finding is confirmed as a false positive, we suppress it with proper justification and maintain suppression records in the security platform. These suppressions are reused in future scans so the same false positives do not repeatedly appear.

However, suppressions are periodically reviewed to ensure genuine vulnerabilities are not accidentally ignored.

This balances security effectiveness with developer productivity.



# Question 15

**Question:**

Compare **SonarQube**, **Checkmarx**, and **Semgrep**. Explain their differences, strengths, limitations, and use cases.

**Answer:**

These tools have different strengths.

**SonarQube**

* Focuses on **code quality** and basic security analysis.
* Detects bugs, vulnerabilities, and code smells.
* Integrates easily with CI/CD pipelines.
* Available in both Community and Enterprise editions.
* Best suited for continuous code quality monitoring.

**Checkmarx**

* Enterprise-grade **SAST** solution.
* Performs deeper security analysis than SonarQube.
* Supports compliance reporting, governance, and advanced vulnerability management.
* Commonly used in organizations with strict security requirements.

**Semgrep**

* Lightweight and fast static analysis tool.
* Uses customizable rules.
* Easy to integrate into CI/CD.
* Excellent for custom security policies and developer workflows.

In practice:

* **SonarQube** is ideal for improving overall code quality.
* **Checkmarx** is preferred for enterprise security scanning and compliance.
* **Semgrep** is useful for fast scans and organization-specific security rules.

The choice depends on the organization's security maturity, compliance needs, and budget.



# Question 16

**Question:**

What are the **limitations of DAST**, and how do you compensate for those limitations?

**Answer:**

DAST is effective for identifying runtime vulnerabilities, but it has several limitations.

Some common limitations are:

* It requires a running application.
* It cannot analyze source code.
* It may miss vulnerabilities hidden behind complex authentication or business workflows.
* It provides limited visibility into the exact vulnerable code.
* Scans may take longer than static analysis.

To compensate for these limitations, we combine DAST with other security practices:

* **SAST** for source code analysis.
* **SCA** for third-party dependency vulnerabilities.
* **Container Image Scanning** for container security.
* **Secret Scanning** for exposed credentials.
* Manual security reviews and penetration testing for complex scenarios.

Using multiple security controls provides comprehensive coverage throughout the SDLC.



# Question 17

**Question:**

Walk me through your **End-to-End Vulnerability Management Lifecycle**. Also explain your **role and responsibilities** throughout the process.

**Answer:**

Our vulnerability management process starts with integrating security scanners into the CI/CD pipeline.

The lifecycle is:

**Identify → Assess → Prioritize → Remediate → Validate → Report → Continuous Monitoring**

Different scanners identify different vulnerability types:

* SAST for source code.
* SCA for third-party dependencies.
* Container scanners for Docker images.
* DAST for runtime vulnerabilities.

My responsibilities include:

* Integrating scanners into Jenkins pipelines.
* Supporting development teams in understanding findings.
* Providing evidence for reported vulnerabilities.
* Assisting with remediation recommendations.
* Handling false-positive validation where applicable.
* Re-running scans after fixes.
* Supporting compliance activities such as PCI-DSS by generating security reports and evidence.

For image-related vulnerabilities, I help update vulnerable base images or dependencies. For SCA findings, I assist teams in identifying where vulnerable libraries are being used so they can upgrade or replace them.



# Question 18

**Question:**

How would you secure a **Kubernetes Cluster** against common **Attack Vectors**?

**Answer:**

Securing Kubernetes requires multiple layers of protection.

Some key security controls include:

* Implement **RBAC** with least privilege.
* Enforce **Network Policies** to restrict Pod-to-Pod communication.
* Use **Namespaces** for workload isolation.
* Store secrets securely using Kubernetes Secrets integrated with external secret managers where possible.
* Scan container images before deployment.
* Avoid running containers as the **root user**.
* Use trusted and signed container images.
* Keep Kubernetes and worker nodes regularly patched.
* Enable audit logging and continuous monitoring.
* Restrict API Server access and use strong authentication mechanisms.

These controls significantly reduce the attack surface while maintaining operational flexibility.



# Question 19

**Question:**

What are the **Image Security Best Practices** you enforce for **Docker/Container Images**?

**Answer:**

Some important image security best practices are:

* Use **minimal and trusted base images**.
* Pin image versions instead of using the `latest` tag.
* Run containers as a **non-root user**.
* Remove unnecessary packages and dependencies.
* Scan images using tools like **Trivy** before pushing them to the registry.
* Block deployment if High or Critical vulnerabilities exceed the defined threshold.
* Sign container images to ensure integrity.
* Store images only in trusted registries such as Nexus.
* Regularly rebuild images to include security patches.
* Avoid embedding secrets inside images.
* Follow multi-stage builds to reduce image size and attack surface.

These practices help produce secure, lightweight, and maintainable container images.



# Question 20

**Question:**

What is **Terraform State Drift**?

**Answer:**

Terraform State Drift occurs when the actual infrastructure no longer matches the infrastructure recorded in the Terraform state file.

This usually happens when someone manually modifies cloud resources outside Terraform, such as through the AWS or Azure console.

For example, if an EC2 instance type is changed manually in AWS, Terraform's state file will still contain the previous configuration. During the next `terraform plan`, Terraform detects this difference and reports the drift.

State drift can lead to unexpected infrastructure changes, so all infrastructure modifications should ideally be performed through Terraform.

## Question 21

**Question:**

How do you **detect**, **prevent**, and **fix Terraform State Drift**?

**Answer:**

Terraform state drift is detected by regularly running **`terraform plan`**, which compares the actual infrastructure with the Terraform state file and highlights any differences. Periodic drift detection can also be automated through CI/CD pipelines.

To **prevent** state drift, I follow these best practices:

* Store the Terraform state in a **remote backend** such as an S3 bucket with proper access control.
* Enable **state locking** (for example, using DynamoDB with an S3 backend) to prevent multiple users from modifying the state simultaneously.
* Restrict direct access to cloud resources using **IAM** and **RBAC**, so infrastructure changes are made only through Terraform.
* Follow Infrastructure as Code practices and avoid manual changes from the cloud console.
* Use code reviews and CI/CD pipelines for infrastructure changes.

To **fix** state drift:

* Run **`terraform plan`** to identify the drift.
* If the manual change is valid, update the Terraform code to match the actual infrastructure and apply it.
* If the manual change is unauthorized, run **`terraform apply`** to restore the infrastructure to the desired state.
* In specific cases where resources already exist but are not tracked, use **`terraform import`** to bring them under Terraform management.

This approach keeps the infrastructure consistent, auditable, and manageable.



# Question 22

**Question:**

How would you design **DDoS Protection** for a **Public-facing API** across **Layer 3 (L3)**, **Layer 4 (L4)**, and **Layer 7 (L7)**?

**Answer:**

DDoS protection should follow a **defense-in-depth** approach by securing the application across multiple network layers.

### **Layer 3 & Layer 4 (Network and Transport Layer)**

At these layers, the goal is to absorb or block large volumes of malicious traffic.

* Use cloud-native DDoS protection services such as **AWS Shield** or equivalent cloud services.
* Deploy **Load Balancers** to distribute incoming traffic.
* Enable **Auto Scaling** so the application can handle legitimate traffic spikes.
* Apply **Security Groups**, **Network ACLs**, and firewall rules to restrict unnecessary traffic.
* Continuously monitor traffic patterns using **CloudWatch**, **Prometheus**, or similar monitoring tools.

### **Layer 7 (Application Layer)**

At the application layer, the focus is on protecting APIs from malicious requests.

* Place the API behind an **API Gateway** or **Application Load Balancer**.
* Configure **Rate Limiting** and **Request Throttling** to limit requests from individual clients.
* Use a **Web Application Firewall (WAF)** to block malicious requests such as SQL Injection, XSS, bot traffic, and known attack signatures.
* Maintain **IP allowlists/blocklists** where appropriate.
* Validate authentication and authorization before processing requests.
* Configure logging, monitoring, and alerts for abnormal traffic patterns.

In production, these controls work together. Network-level protection mitigates volumetric attacks, while application-level controls prevent abuse of API endpoints. This layered approach provides resilient and secure protection for public-facing APIs.

