# Interview Questions 

1. **Introduce yourself** and explain your current **roles and responsibilities** in your project.

2. Can you explain the complete **deployment flow** from **developer commit** until **production deployment**? Also, draw a simple **CI/CD pipeline architecture** and explain all the stages involved.

3. Which **monitoring tools** are you using in your project?

4. How many **environments** are there in your project, and how does the **same build/image promotion** happen from Development to UAT and Production?

5. How do you securely manage **Secrets** inside **Jenkins**?

6. How do you **trigger Jenkins pipelines**? Do you use **Webhooks**, **Scheduler (Cron)**, or any other mechanism?

7. What **Git branching strategy** are you following in **GitLab**?

8. How are **artifacts/images** promoted from **Jenkins** to **Nexus**? What **quality gates** or **security validations** must pass before publishing them?

9. Have you worked on **Terraform**? What types of **cloud resources** have you provisioned using it?

10. What is the **Terraform State File**, and what information does it maintain?

11. If the **Terraform State File** gets **locked** due to concurrent changes or version mismatches, what issues can occur, and how would you resolve them?

12. What configuration details are typically present in a **Terraform Remote Backend** configuration (such as **S3** or **Azure Storage Account**)?

13. What are **Terraform Modules**, and why are they used?

14. What **AWS services** have you worked on?

15. Using **Terraform**, have you provisioned complete **network infrastructure** such as **VPC/VNet**, **Subnets**, and resource mappings, or have you mainly provisioned only **application resources**?

16. How many **Microservices** have you deployed in your **Kubernetes Cluster**, and what was your role in managing those deployments?

17. Have you configured or set up an **Ingress Controller**? What was your involvement in its implementation?

18. You mentioned **NGINX Gateway** and **DMZ** in your resume. Can you explain the complete architecture, including **Reverse Proxy**, **TLS/SSL Termination**, **Host-Based Routing**, **Path-Based Routing**, **Rate Limiting**, and how requests reach the backend **Microservices**?

19. If a **Jenkins Pipeline** suddenly hangs or fails, how would you **troubleshoot** and identify the **root cause**?

20. Suppose a **Production Deployment** fails midway. How would you perform a **rollback**, restore the service, investigate the **root cause**, and communicate the incident?

21. If the **Terraform State File** is accidentally **deleted**, how would you recover it?

22. Suppose your **Monitoring Tool** reports increasing **Application Latency**, but **CPU** and **Memory** utilization are normal. What other components would you investigate to identify the root cause?

23. Can you describe a recent **Production Issue** or **Security-related Incident** that you handled? What was the problem, how did you troubleshoot it, and what was the outcome?

---


# Answers


## Question 1

**Question:**

**Introduce yourself** and explain your current **roles and responsibilities** in your project.

**Answer:**

Sure. I'm a **DevSecOps Engineer with around 4.5 years of experience** in DevOps and DevSecOps, primarily working on secure CI/CD automation, cloud infrastructure, container platforms, and application security.

I started my career at **PREVIOUS COMPANY** as a DevOps Engineer, where I spent around **2.5 years** building Jenkins pipelines, automating deployments, managing cloud infrastructure, and supporting application releases. Later, I transitioned into a **DevSecOps Engineer** role at Talent Network.

Currently, I'm working for a **FinTech client** that provides payment gateway solutions for banking applications. My primary responsibility is integrating security throughout the Software Development Lifecycle while also supporting deployment automation.

Our environment consists of **Java, Python, Kotlin, Node.js, C, and C++** applications. We use **GitLab** for source code management, **Jenkins** as the CI/CD orchestrator, **Nexus** as the artifact repository, **Docker** and **Kubernetes** for containerized deployments, and a hybrid cloud environment across **AWS and Azure**.

From a security perspective, I have integrated tools such as **Fortify (SAST/DAST)**, **Sonatype (SCA)**, **GitLeaks** for secret scanning, and **Trivy** for container image scanning into the CI/CD pipeline.

My day-to-day responsibilities include:

* Designing and maintaining secure CI/CD pipelines.
* Onboarding new applications into the pipeline.
* Integrating security scanners into the SDLC.
* Supporting developers in resolving security vulnerabilities.
* Managing deployment automation for VM-based and Kubernetes applications.
* Collaborating with development, infrastructure, and security teams to ensure secure and reliable software delivery.



# Question 2

**Question:**

Can you explain the complete **deployment flow** from **developer commit** until **production deployment**? Also, draw a simple **CI/CD pipeline architecture** and explain all the stages involved.

**Answer:**

In our project, we use **GitLab** as the source code repository and **Jenkins** as the CI/CD orchestrator.

The deployment flow is as follows:

**Developer Commit / Merge Request**
→ Developer pushes code to GitLab, which triggers a Jenkins pipeline through a **Webhook**.

**Source Checkout**
→ Jenkins checks out the latest source code from the target branch.

**Build & Unit Testing**
→ The application is compiled and unit tests are executed.

**Code Quality & Security**
→ We perform:

* **SonarQube** for code quality and quality gates.
* **Fortify SAST** for static code analysis.
* **Sonatype** for Software Composition Analysis (SCA).
* **GitLeaks** for secret detection.

If any scanner reports vulnerabilities beyond the defined policy threshold, the pipeline fails immediately.

**Container Build**
→ A Docker image is built.

**Container Security**
→ The Docker image is scanned using **Trivy** for OS and package vulnerabilities.

**Artifact Publishing**
→ Only if all quality gates and security checks pass, the artifact or Docker image is pushed to **Nexus Repository**.

**Deployment**
→ The same approved artifact is promoted across **Development → UAT → Production** to maintain deployment consistency.

**Runtime Validation**
→ After deployment, we perform health checks and DAST scans where applicable.

**Monitoring**
→ Application monitoring is done using **Prometheus** and **Grafana**, while cloud resources are monitored using native cloud monitoring services.

This approach ensures the same tested artifact is promoted across environments while enforcing security at every stage of the SDLC.



# Question 3

**Question:**

Which **monitoring tools** are you using in your project?

**Answer:**

For application and infrastructure monitoring, we primarily use **Prometheus** and **Grafana**.

* **Prometheus** collects metrics such as CPU utilization, memory usage, request latency, pod health, and application-specific metrics.
* **Grafana** provides dashboards and alerting for real-time monitoring.

For cloud resources, we use native cloud monitoring services depending on the platform, such as Azure Monitor or AWS monitoring services, to track VM health, Kubernetes clusters, storage, and other infrastructure components.

During production support, these monitoring tools help us detect incidents proactively and reduce Mean Time to Detect (MTTD).



# Question 4

**Question:**

How many **environments** are there in your project, and how does the **same build/image promotion** happen from Development to UAT and Production?

**Answer:**

We primarily have three environments:

* **Development**
* **UAT**
* **Production**

The application is built only once in the Development pipeline. After all security scans, quality gates, and validations are successfully completed, the Docker image is pushed to **Nexus**.

The same immutable image is then promoted to UAT and later to Production without rebuilding it. This ensures consistency across environments and eliminates the risk of introducing differences due to multiple builds.

Each environment has its own deployment configuration, but the application artifact remains exactly the same throughout the promotion process.

This is considered a DevOps best practice because it guarantees that the artifact tested in lower environments is the exact one deployed to production.



# Question 5

**Question:**

How do you securely manage **Secrets** inside **Jenkins**?

**Answer:**

In our environment, we use the **Jenkins Credentials Store** to securely manage secrets.

Sensitive information such as API tokens, passwords, SSH keys, cloud credentials, and service account credentials are stored in the Jenkins Credentials Manager rather than hardcoded in pipeline scripts.

During pipeline execution, Jenkins injects these credentials securely into the required stages using credential bindings. This ensures the secrets are available only during runtime and are never exposed in the source code.

Additionally, we follow these best practices:

* Never store secrets in Git repositories.
* Restrict credential access based on job permissions.
* Mask sensitive values in Jenkins console logs.
* Rotate credentials periodically.
* Prefer short-lived credentials or IAM roles where possible instead of long-lived access keys.

This approach minimizes the risk of credential exposure while maintaining secure automated deployments.


## Question 6

**Question:**

How do you **trigger Jenkins pipelines**? Do you use **Webhooks**, **Scheduler (Cron)**, or any other mechanism?

**Answer:**

In our project, we primarily use **GitLab Webhooks** to trigger Jenkins pipelines.

Whenever a developer pushes code or creates a Merge Request in GitLab, the webhook automatically notifies Jenkins and triggers the corresponding pipeline. This enables immediate validation of the latest code changes and supports Continuous Integration.

Apart from webhook-based triggers, we also use **Scheduled (Cron) Triggers** for specific use cases such as:

* Nightly builds
* Periodic security scans
* Dependency validation
* Health-check or maintenance jobs

For production deployments, certain pipelines may also require **manual approval** before execution to ensure proper release governance.

Overall, webhook-based triggering is our primary mechanism, while scheduled and manual triggers are used based on the pipeline's purpose.



# Question 7

**Question:**

What **Git branching strategy** are you following in **GitLab**?

**Answer:**

We primarily follow the **GitFlow branching strategy**.

The common branches are:

* **main/master** – Production-ready code.
* **develop** – Integration branch for ongoing development.
* **feature/*** – Individual feature development.
* **release/*** – Release preparation and final testing.
* **hotfix/*** – Critical production fixes.

The typical workflow is:

* Developers create a **feature branch** from the **develop** branch.
* After development, they raise a **Merge Request**.
* Code undergoes peer review and automated CI/CD validation.
* Once approved, it is merged into **develop**.
* During a release, a **release branch** is created and promoted through Development, UAT, and finally merged into **main** for Production.
* If a production issue occurs, a **hotfix branch** is created from **main**, validated, deployed, and then merged back into both **main** and **develop**.

This strategy provides better release management, controlled production deployments, and easier parallel development.



# Question 8

**Question:**

How are **artifacts/images** promoted from **Jenkins** to **Nexus**? What **quality gates** or **security validations** must pass before publishing them?

**Answer:**

Once Jenkins builds the application, multiple quality and security validations are performed before publishing any artifact.

The pipeline flow is:

**Build**
→ **Unit Tests**
→ **SonarQube Quality Gate**
→ **Fortify SAST**
→ **Sonatype SCA**
→ **GitLeaks Secret Scan**
→ **Docker Image Build**
→ **Trivy Image Scan**
→ **Push to Nexus**

Each security tool has predefined policies and severity thresholds.

For example:

* If **Critical** or **High** vulnerabilities exceed the organization's policy, the pipeline fails immediately.
* Medium or Low findings are handled according to business and security policies.

Only after all quality gates and security validations are successfully completed does Jenkins authenticate with **Nexus** and publish the artifact or Docker image.

This ensures that only verified and secure artifacts are promoted to higher environments.



# Question 9

**Question:**

Have you worked on **Terraform**? What types of **cloud resources** have you provisioned using it?

**Answer:**

Yes, I have worked with Terraform for provisioning and managing cloud infrastructure using Infrastructure as Code.

In my project, I have primarily provisioned resources such as:

* **Virtual Machines (EC2/Azure VMs)**
* **Storage Services** (S3, Azure Storage)
* **Security Groups**
* **IAM-related resources** where required
* **Application-specific infrastructure**
* **Messaging services** such as **SNS** and **SQS** for specific use cases

I have also written reusable **Terraform Modules** to standardize infrastructure provisioning across multiple environments.

For networking components like **VPCs, VNets, and Subnets**, our organization has a dedicated cloud/network team. My primary responsibility was provisioning application infrastructure within the existing network architecture rather than designing the entire network from scratch.

Terraform helped us maintain infrastructure consistency, version control, automation, and repeatable deployments across environments.



# Question 10

**Question:**

What is the **Terraform State File**, and what information does it maintain?

**Answer:**

The **Terraform State File (`terraform.tfstate`)** is a JSON file that maintains the current state of the infrastructure managed by Terraform.

Its primary purpose is to map the infrastructure defined in Terraform code with the actual resources deployed in the cloud.

The state file stores information such as:

* Resource IDs
* Resource attributes and metadata
* Current configuration state
* Resource dependencies
* Outputs
* Provider-related information

Terraform uses this state file during **`terraform plan`** and **`terraform apply`** to determine what changes are required instead of recreating all resources.

In production environments, the state file is typically stored in a **Remote Backend**, such as an **AWS S3 Bucket** or **Azure Storage Account**, with **state locking** enabled (for example, using DynamoDB in AWS) to prevent concurrent modifications.

Storing the state remotely also enables collaboration, versioning, backup, and secure access for multiple team members while maintaining a single source of truth for the infrastructure.

## Question 11

**Question:**

If the **Terraform State File** gets **locked** due to concurrent changes or version mismatches, what issues can occur, and how would you resolve them?

**Answer:**

The Terraform State File is locked to prevent multiple users from modifying the infrastructure simultaneously. If the state file gets locked, Terraform operations such as **`terraform plan`** or **`terraform apply`** cannot proceed until the lock is released.

This can happen due to:

* Multiple users running Terraform on the same state simultaneously.
* An interrupted or failed Terraform execution that leaves a stale lock.
* Network interruptions during state updates.
* CI/CD pipeline failures while updating the state.

To resolve it, I would follow these steps:

1. First, verify whether another team member or CI/CD pipeline is currently running Terraform. If yes, I wait for it to complete.
2. If the lock is stale, I verify that no active Terraform operation is in progress.
3. I then safely remove the stale lock using **`terraform force-unlock <LOCK_ID>`** only after confirming that no other operation is using the state.
4. If the issue is due to backend connectivity, I verify access to the remote backend, such as the S3 bucket and DynamoDB table or Azure Storage Account.
5. After the lock is cleared, I run **`terraform plan`** to validate the infrastructure state before applying any changes.

To prevent such issues, we store the state in a **remote backend** with **state locking enabled**, ensure Terraform runs through CI/CD wherever possible, and avoid multiple users modifying the same state simultaneously.



# Question 12

**Question:**

What configuration details are typically present in a **Terraform Remote Backend** configuration (such as **S3** or **Azure Storage Account**)?

**Answer:**

A Terraform Remote Backend configuration defines where the Terraform State File is stored and how it is accessed.

For an **AWS S3 Backend**, the common configuration includes:

* **Bucket Name**
* **State File Key (Path)**
* **AWS Region**
* **DynamoDB Table** (for state locking)
* **Encryption** settings
* Optional AWS profile or role configuration

Example components:

* Bucket = Terraform state storage
* Key = Path of the state file
* Region = AWS region
* DynamoDB Table = State locking
* Encrypt = Server-side encryption

For an **Azure Storage Backend**, the configuration typically includes:

* Resource Group Name
* Storage Account Name
* Container Name
* State File Key
* Subscription/Tenant information (through authentication)

The purpose of the remote backend is to:

* Maintain a single source of truth.
* Enable team collaboration.
* Support state locking.
* Provide backup and versioning.
* Secure the Terraform State File.



# Question 13

**Question:**

What are **Terraform Modules**, and why are they used?

**Answer:**

Terraform Modules are reusable collections of Terraform configuration files that allow us to standardize infrastructure provisioning.

Instead of writing the same resource definitions repeatedly, we create a module once and reuse it across multiple environments or projects by passing different input variables.

For example, a single EC2 or Azure VM module can be reused for Development, UAT, and Production by changing parameters such as:

* Instance size
* Image ID
* Environment name
* Tags
* Network configuration

The benefits of Terraform Modules include:

* Code reusability
* Reduced duplication
* Easier maintenance
* Standardized infrastructure
* Better scalability
* Easier collaboration across teams

In my project, I have used Terraform Modules mainly for provisioning common infrastructure resources so that deployments remain consistent across environments.



# Question 14

**Question:**

What **AWS services** have you worked on?

**Answer:**

In my current and previous projects, I have worked with several AWS services, primarily from a DevOps and DevSecOps perspective.

Some of the services include:

* **EC2** for application hosting and virtual machines.
* **S3** for artifact storage, backups, and Terraform remote state.
* **IAM** for users, roles, policies, and least-privilege access management.
* **VPC** for networking concepts and resource connectivity.
* **Security Groups** for instance-level firewall rules.
* **Auto Scaling Groups** for scaling EC2 instances based on demand.
* **SNS** for notifications.
* **SQS** for asynchronous message queuing.
* **CloudWatch** for infrastructure monitoring, metrics, dashboards, and alerts.
* **EKS** exposure for Kubernetes-based deployments in cloud environments.

From a DevSecOps perspective, my work primarily involved provisioning resources, supporting deployments, managing IAM permissions, integrating monitoring, and automating infrastructure using Terraform.



# Question 15

**Question:**

Using **Terraform**, have you provisioned complete **network infrastructure** such as **VPC/VNet**, **Subnets**, and resource mappings, or have you mainly provisioned only **application resources**?

**Answer:**

In my project, my primary responsibility was provisioning **application infrastructure** rather than designing the complete network architecture.

I have provisioned resources such as:

* Virtual Machines
* Storage Accounts
* Application-specific infrastructure
* Security Groups
* Supporting cloud resources

For networking components like **VPCs, VNets, Subnets, Route Tables, and Network Gateways**, we had a dedicated cloud/network team responsible for their design and management.

However, I have worked with those existing network components by:

* Deploying resources into existing VPCs/VNets.
* Associating resources with appropriate Subnets.
* Configuring Security Groups where required.
* Referencing existing networking resources within Terraform.

So, while I understand the networking architecture and Terraform configuration for these components, my hands-on responsibility was primarily focused on provisioning application resources within the established network infrastructure.


## Question 16

**Question:**

How many **Microservices** have you deployed in your **Kubernetes Cluster**, and what was your role in managing those deployments?

**Answer:**

In our project, we have approximately **20–30 microservices** deployed in Kubernetes, depending on the application and release cycle.

My primary responsibilities included deploying and maintaining these microservices through our CI/CD pipelines. For each microservice, we typically managed the following Kubernetes resources:

* **Deployment** – To manage Pods, rolling updates, and replica count.
* **Service** – To expose the application internally within the cluster.
* **ConfigMaps** – To externalize application configuration.
* **Secrets** – To securely manage sensitive information such as credentials and API keys.
* **Ingress** – To expose applications externally and configure routing.
* **Namespaces** – To logically separate environments where applicable.

During deployments, I also verified:

* Pod health and rollout status.
* Readiness and liveness probes.
* Deployment strategies such as Rolling Updates.
* Resource requests and limits.
* Kubernetes events and pod logs for troubleshooting.

Most deployments were automated through Jenkins pipelines using Kubernetes manifests or Helm charts, ensuring consistent deployments across Development, UAT, and Production environments.



# Question 17

**Question:**

Have you configured or set up an **Ingress Controller**? What was your involvement in its implementation?

**Answer:**

I have a good understanding of Kubernetes Ingress and have worked extensively with **Ingress configuration**, although I was **not responsible for setting up the Ingress Controller from scratch**.

In our environment, the platform team initially installed and managed the NGINX Ingress Controller. My responsibilities included:

* Creating and maintaining **Ingress resources**.
* Configuring **host-based** and **path-based routing**.
* Managing **TLS/SSL certificates** for HTTPS.
* Mapping external requests to the appropriate Kubernetes Services.
* Coordinating with the infrastructure team whenever controller-level changes were required.

I was also involved in troubleshooting ingress-related issues such as:

* Incorrect routing.
* TLS certificate problems.
* 404 and 502 errors.
* Backend service connectivity.
* DNS configuration verification.

So, while I wasn't responsible for installing the controller itself, I regularly configured and managed Ingress resources for application deployments.



# Question 18

**Question:**

You mentioned **NGINX Gateway** and **DMZ** in your resume. Can you explain the complete architecture, including **Reverse Proxy**, **TLS/SSL Termination**, **Host-Based Routing**, **Path-Based Routing**, **Rate Limiting**, and how requests reach the backend **Microservices**?

**Answer:**

Certainly.

In our environment, **NGINX** acts as a **Reverse Proxy** and serves as the entry point for external client traffic. It is deployed within the **DMZ (Demilitarized Zone)**, which acts as a secure network boundary between the internet and the internal application network.

The request flow is as follows:

**Client → NGINX Reverse Proxy (DMZ) → Kubernetes Ingress → Service → Pod (Microservice)**

Here's how each component works:

* External clients send HTTPS requests to the public endpoint exposed through NGINX.
* NGINX performs **TLS/SSL termination**, decrypting HTTPS traffic before forwarding it securely to the internal Kubernetes environment.
* Based on the request, NGINX applies **Host-Based Routing** (using the domain name) and **Path-Based Routing** (using the URL path) to direct traffic to the appropriate backend service.
* The request is forwarded to the Kubernetes Ingress, which routes it to the corresponding Kubernetes Service and then to the target Pods.

From a security perspective, NGINX also provides:

* **Rate Limiting** to prevent abuse and reduce the impact of excessive requests.
* Basic request filtering and header management.
* SSL/TLS certificate management.
* Centralized logging for incoming traffic.

This architecture improves both **security** and **traffic management** by isolating internal services from direct internet access while providing controlled and secure request routing to backend microservices.



# Question 19

**Question:**

If a **Jenkins Pipeline** suddenly hangs or fails, how would you **troubleshoot** and identify the **root cause**?

**Answer:**

Whenever a Jenkins pipeline hangs or fails, my first priority is to identify **where** and **why** the failure occurred.

My troubleshooting approach is:

1. **Review the Jenkins Console Output**

   * Identify the stage where the failure occurred.
   * Note the exact error message or exception.

2. **Identify the Failure Category**

   * Source code issue.
   * Build or compilation failure.
   * Test failure.
   * Security scan failure.
   * Deployment failure.
   * Infrastructure issue.

3. **Verify Jenkins Infrastructure**

   * Check whether the Jenkins Controller and Agent are online.
   * Verify agent connectivity.
   * Check CPU, Memory, and Disk utilization.
   * Ensure sufficient workspace availability.

4. **Validate External Integrations**

   * GitLab connectivity.
   * Nexus availability.
   * Kubernetes cluster connectivity.
   * Security scanning tools such as Fortify, Sonatype, or Trivy.

5. **Review Recent Changes**

   * Recent pipeline modifications.
   * Plugin updates.
   * Credential changes.
   * Infrastructure changes.

6. **Take Corrective Action**

   * Fix configuration or infrastructure issues.
   * Restart failed agents if required.
   * Re-run the pipeline after resolving the issue.
   * Document the RCA for recurring problems.

In production, I always begin with the Jenkins logs because they usually pinpoint the exact stage where the pipeline stopped, allowing faster resolution and minimizing deployment delays.



# Question 20

**Question:**

Suppose a **Production Deployment** fails midway. How would you perform a **rollback**, restore the service, investigate the **root cause**, and communicate the incident?

**Answer:**

If a production deployment fails midway, my first priority is to **restore the service** and minimize customer impact.

My approach would be:

1. **Assess the Impact**

   * Verify which services are affected.
   * Check application health, Kubernetes events, and monitoring dashboards.

2. **Rollback Immediately**

   * Roll back to the last stable application version.
   * For Kubernetes deployments, use the previous ReplicaSet or Helm release if applicable.
   * Ensure traffic is restored to the stable version.

3. **Validate Service Recovery**

   * Verify application health endpoints.
   * Confirm Pods are healthy.
   * Monitor user traffic and error rates.
   * Ensure monitoring alerts return to normal.

4. **Perform Root Cause Analysis**

   * Review deployment logs.
   * Check application logs using `kubectl logs`.
   * Verify configuration changes, Helm values, Secrets, ConfigMaps, and infrastructure health.
   * Confirm whether the issue is application-related, configuration-related, or infrastructure-related.

5. **Communicate with Stakeholders**

   * Inform the incident manager, development team, and business stakeholders about the rollback and service status.
   * Provide regular updates until the issue is resolved.

6. **Post-Incident Activities**

   * Document the Root Cause Analysis.
   * Implement preventive measures.
   * Update deployment procedures if required.
   * Add monitoring or validation checks to prevent recurrence.

My overall approach is **Restore First, Investigate Next**, ensuring business continuity before conducting a detailed RCA.


## Question 21

**Question:**

If the **Terraform State File** is accidentally **deleted**, how would you recover it?

**Answer:**

If the Terraform State File is accidentally deleted, the recovery approach depends on how the remote backend is configured. In production, we always store the state in a **remote backend** with **versioning and backup enabled**, so recovery is usually straightforward.

My approach would be:

1. **Check the Remote Backend**

   * Verify whether the state file exists in the remote backend (such as an S3 bucket or Azure Storage Account).
   * Check if **versioning** is enabled.

2. **Restore from Previous Version or Backup**

   * If bucket versioning is enabled, restore the latest valid version of the state file.
   * If periodic backups or snapshots are configured, restore the most recent backup.

3. **Validate the Restored State**

   * Run **`terraform plan`** to verify that the restored state matches the actual infrastructure before making any changes.

4. **Rebuild the State (If No Backup Exists)**

   * If the state cannot be recovered, import the existing infrastructure into a new state using **`terraform import`**.
   * Import each resource into Terraform until the complete infrastructure is reconstructed.
   * Validate the rebuilt state using **`terraform plan`** to ensure there are no unintended changes.

5. **Prevent Future Incidents**

   * Store the state in a remote backend.
   * Enable **versioning**, **state locking**, and **encryption**.
   * Schedule regular backups.
   * Restrict access using IAM policies and avoid manual modifications.

In production, enabling **remote state storage with versioning and locking** is the most effective way to recover quickly and minimize operational risk.



# Question 22

**Question:**

Suppose your **Monitoring Tool** reports increasing **Application Latency**, but **CPU** and **Memory** utilization are normal. What other components would you investigate to identify the root cause?

**Answer:**

If CPU and memory utilization are normal but application latency is increasing, it usually indicates that the bottleneck lies elsewhere. I would troubleshoot the issue systematically.

First, I would check the **application logs** for exceptions, timeout errors, thread pool exhaustion, or slow request processing.

Next, I would verify the **database** by checking:

* Slow-running queries.
* Database connection pool utilization.
* Lock contention.
* High query execution time.

Then, I would examine the **network path**, including:

* Network latency between services.
* DNS resolution issues.
* Packet loss or connectivity problems.
* Service-to-service communication delays.

If the application is running on Kubernetes, I would inspect:

* Pod events.
* Pod restarts.
* Readiness and liveness probe failures.
* Resource throttling.
* Kubernetes Service and Endpoint health.

I would also verify the **Ingress Controller**, **Load Balancer**, or **NGINX** to check:

* Request queues.
* Backend health.
* Rate limiting.
* Upstream connection failures.
* Response time metrics.

Additionally, I would check:

* External API dependencies.
* Message queues, if used.
* Recent deployments or configuration changes.
* Application Performance Monitoring (APM) traces, if available.

Finally, I would correlate application logs, monitoring dashboards, and infrastructure metrics to isolate the root cause before implementing the appropriate fix.



# Question 23

**Question:**

Can you describe a recent **Production Issue** or **Security-related Incident** that you handled? What was the problem, how did you troubleshoot it, and what was the outcome?

**Answer:**

One production issue I recently handled was related to our **security scanning pipeline**.

Our Jenkins pipelines suddenly started failing across multiple applications because the **Fortify SAST scanning agent** became unreachable from the Jenkins server.

My troubleshooting approach was:

1. **Identify the Failure**

   * Reviewed the Jenkins console logs.
   * Confirmed that all failures were occurring during the SAST scanning stage.

2. **Isolate the Root Cause**

   * Verified network connectivity between Jenkins and the Fortify scanning agent.
   * Confirmed that the scanning service was unavailable, causing connection failures.

3. **Restore the Service**

   * Coordinated with the infrastructure team.
   * Restored connectivity between Jenkins and the Fortify scanning server.
   * Re-ran the affected pipelines successfully.

4. **Validate the Solution**

   * Verified that SAST scans completed successfully.
   * Confirmed that downstream stages such as SCA, image scanning, and deployments proceeded normally.

In another recurring scenario, we experienced a high number of security findings that created **alert fatigue** for developers. I worked with the security team to fine-tune scanning policies and adjust quality gate thresholds based on organizational guidelines. This reduced false positives, improved developer adoption of security practices, and allowed the team to focus on genuine high-risk vulnerabilities while maintaining the required security standards.

These incidents reinforced the importance of systematic troubleshooting, cross-team collaboration, and balancing security with developer productivity.
