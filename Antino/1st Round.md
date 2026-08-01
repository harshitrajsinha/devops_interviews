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




---

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

---

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

---

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

---

# Question 4

**Question:**

What is **SAST**? Where does it fit into your **CI/CD pipeline**?

**Answer:**

**SAST (Static Application Security Testing)** analyzes the application's source code or binaries without executing the application. It helps identify security vulnerabilities early in the development lifecycle, such as SQL Injection, Cross-Site Scripting, insecure coding practices, hardcoded credentials, and other OWASP Top 10 issues.

In our CI/CD pipeline, SAST runs immediately after the source code is checked out, typically before or immediately after the build stage depending on the tool.

Our pipeline generally follows this sequence:

Git Checkout → Secret Scan → SAST → SCA/SBOM → Build → Container Image Scan → Push Image → Deploy → DAST

Running SAST early allows developers to fix vulnerabilities before deployment, reducing remediation cost and improving overall software security.

---

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

---

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

---

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

---

# Question 8

**Question:**

How do you handle a **Merge Conflict** in a **shared Git branch**?

**Answer:**

First, I identify the conflicting files and understand why the conflict occurred by reviewing the Git history and recent commits.

Next, I pull the latest changes from the target branch, resolve the conflicts manually, verify that no functional changes are lost, and test the application locally.

If the conflict affects multiple developers, I coordinate with the respective team members to ensure the correct implementation is retained.

After successful validation, I commit the resolved changes and push them for review.

In production environments, good branching strategies, frequent rebasing or merging, and smaller pull requests significantly reduce merge conflicts.

---

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

---

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


