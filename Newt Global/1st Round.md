# Interview Questions 

1. **Introduce yourself** and briefly explain your **profile** and **experience**.

2. Can you share your **GCP experience**? Which **GCP services** have you worked on, and do you have **production experience**?

3. Which **cloud platform** do you primarily have experience with?

4. Can you explain the **AWS services** you have worked on?

5. You mentioned working on **Java** and **Node.js** applications. Can you explain your complete **CI/CD pipeline**, **GitOps workflow**, and how you **deploy applications** from source code to the cloud/Kubernetes environment?

6. Suppose someone tries to deploy an application **outside the CI/CD pipeline**. How would you ensure that **only authorized images** are deployed to the cluster, even if someone bypasses the pipeline? Explain how you would enforce **image authorization**, **image signing**, and **image verification**, and how you would **configure** this mechanism.

7. Suppose the application is deployed, but the container keeps restarting (**CrashLoopBackOff**). How would you **troubleshoot** the issue and ensure the correct application is deployed?

8. Can you **prevent CrashLoopBackOff** errors **before deployment** instead of troubleshooting them later?

9. Suppose users are already accessing your application. If someone deploys a faulty version that results in **CrashLoopBackOff**, how would you ensure users **never experience downtime** or a **Service Unavailable** error? How would you prevent unhealthy pods from serving traffic?

10. You mentioned **health checks**. Can you explain what those checks are, how they work, and **how you configure them**?

11. You mentioned **rollback**. How do you actually **configure rollback** in Kubernetes? What needs to be configured to enable rollback?

12. What **deployment strategy** do you configure in Kubernetes? Explain **Rolling Update**, how it works, and what other strategies such as **Canary** are available for safer deployments and rollbacks.

13. Have you worked on **Terraform**?

14. What exactly have you implemented using **Terraform**? Explain the **reusable modules** you created and the type of **infrastructure** you provisioned.

15. Which **AWS resources** have you provisioned using Terraform (for example **EC2, S3, VPC, Subnets, IAM, Kubernetes Clusters**)?

16. Suppose you need to provision an **EC2/Compute Engine** instance inside a **VPC**, but the VPC itself is **not yet created**. Since Terraform provisions everything together, how would you ensure the instance is deployed into the correct VPC? Explain how you handle **resource dependencies**, **outputs**, and **inputs**.

17. Have you worked on **Logging and Monitoring**?

18. Suppose you have multiple **GCP Projects** (Project A, Project B, Project C) and want to **centralize logs** from multiple projects. How would you implement **centralized logging**? Where would you configure it, how would you configure it, and what **log collectors/forwarders/plugins** would you use?

19. Do you have any **questions for me**?

---

# Answers



# Question 1

### **Question:**

**Introduce yourself** and briefly explain your **profile** and **experience**.

### **Answer:**

Sure.

  My name is **NAME**, and I have around **4.5 years of experience** in **DevOps and DevSecOps**.

I started my career as a **DevOps Engineer at PREVIOUS COMPANY**, where I worked on CI/CD automation, infrastructure provisioning, containerization, and cloud deployments. Later, I transitioned into a **DevSecOps Engineer** role at PRESENT COMPANY, supporting a **FinTech client** that provides payment gateway solutions for banking applications.

My primary responsibility is to **design, implement, and maintain secure CI/CD pipelines** while integrating security throughout the Software Development Life Cycle.

I have worked with applications built on **Java, Node.js, Python, and Kotlin**, using **GitLab**, **Jenkins**, **Docker**, **Kubernetes**, **Helm**, **Terraform**, and **Argo CD**.

From a security perspective, I have integrated tools such as **Fortify (SAST)**, **OWASP Dependency-Check (SCA)**, **Trivy (Container Security)**, **SBOM generation**, and **Secret Scanning** into CI/CD pipelines. I also implement Kubernetes and Docker security best practices, enforce quality gates, and automate secure deployments.

On the cloud side, I have hands-on experience with **AWS**, exposure to **Azure**, and foundational knowledge of **GCP**, particularly around compute, storage, IAM, Kubernetes, and monitoring services.

Overall, my focus is on building **secure, automated, scalable, and reliable DevSecOps platforms**.



# Question 2

### **Question:**

Can you share your **GCP experience**? Which **GCP services** have you worked on, and do you have **production experience**?

### **Answer:**

Yes.

I would like to be transparent here. I **don't have hands-on production experience in GCP**, but I have a solid understanding of its core services through learning, labs, and certification.

The services I'm familiar with include:

* **Compute Engine** for virtual machines.
* **Google Kubernetes Engine (GKE)** for container orchestration.
* **Cloud Storage** for object storage.
* **IAM** for identity and access management.
* **Cloud Monitoring** and **Cloud Logging** for observability.
* **Secret Manager** for securely storing application secrets.
* **Artifact Registry** for storing container images.
* Basic networking concepts such as **VPC**, **Subnets**, and **Firewall Rules**.

Since my production experience is primarily on AWS and Kubernetes, I usually correlate GCP services with equivalent AWS services, which helps me understand the platform quickly.

Although I haven't worked on GCP in production yet, I'm confident in adapting because the core DevOps and Kubernetes concepts remain the same across cloud providers.



# Question 3

### **Question:**

Which **cloud platform** do you primarily have experience with?

### **Answer:**

My primary hands-on experience is with **AWS**.

I have worked on provisioning and managing infrastructure, deploying containerized applications, integrating CI/CD pipelines, and implementing DevSecOps practices on AWS.

The AWS services I've worked with include:

* **EC2**
* **EKS**
* **ECR**
* **S3**
* **VPC**
* **Subnets**
* **Security Groups**
* **IAM**
* **CloudWatch**
* **Application Load Balancer**
* **Route 53** (basic exposure)

I also have working knowledge of **Azure** services such as AKS and Key Vault, along with foundational knowledge of **GCP**.



# Question 4

### **Question:**

Can you explain the **AWS services** you have worked on?

### **Answer:**

Certainly.

Some of the AWS services I've worked with include:

* **EC2** – Hosting virtual machines and supporting application deployments.
* **EKS** – Running Kubernetes workloads and deploying containerized applications.
* **ECR** – Storing Docker images securely.
* **S3** – Artifact storage, backups, and pipeline-related files.
* **IAM** – Managing users, roles, policies, and least-privilege access.
* **VPC** – Configuring networking, subnets, route tables, Internet Gateways, and security boundaries.
* **Security Groups** and **NACLs** – Controlling inbound and outbound traffic.
* **CloudWatch** – Monitoring infrastructure, collecting metrics, and creating alerts.
* **Terraform** – Provisioning AWS infrastructure as code.
* **Load Balancers** – Distributing application traffic across multiple instances.

My role mainly involved automating infrastructure deployment, integrating AWS resources into CI/CD pipelines, securing workloads, and supporting Kubernetes-based application deployments.



# Question 5

### **Question:**

You mentioned working on **Java** and **Node.js** applications. Can you explain your complete **CI/CD pipeline**, **GitOps workflow**, and how you **deploy applications** from source code to the cloud/Kubernetes environment?

### **Answer:**

Sure.

We follow a **GitOps-based CI/CD approach** with security integrated throughout the pipeline.

**Step 1 – Source Code Management**

* Developers commit code to **GitLab** using a GitFlow branching strategy.
* A **Merge Request (MR)** is created and reviewed before merging into the main branch.

**Step 2 – CI Pipeline**
Once the merge request is approved, Jenkins triggers the CI pipeline.

The pipeline performs:

* Source code checkout.
* Application build using **Maven**, **Gradle**, or **npm**, depending on the technology stack.
* Unit testing.
* **SonarQube** analysis for code quality.
* **Fortify SAST** for static code security scanning.
* **OWASP Dependency-Check** to identify vulnerable third-party libraries.
* **SBOM generation** for software component inventory.
* **Secret scanning** to detect hardcoded credentials.

Quality gates are enforced after each critical stage. If any gate fails, the pipeline stops immediately.

**Step 3 – Container Security**

* Build the Docker image.
* Scan the image using **Trivy** for OS and package vulnerabilities.
* Only approved images are pushed to **Nexus**.

**Step 4 – GitOps Deployment**

* Update the image tag in the Helm values repository.
* **Argo CD** continuously monitors the Git repository.
* Once it detects a new image version, it synchronizes the changes to the Kubernetes cluster automatically.

**Step 5 – Post-Deployment Validation**
After deployment:

* Kubernetes **Readiness** and **Liveness Probes** validate application health.
* Verify rollout status.
* Monitor application logs.
* Monitor infrastructure and application metrics through **Prometheus** and **Grafana**.

**Infrastructure Provisioning**
Infrastructure is provisioned separately using **Terraform**, including Kubernetes clusters, networking, IAM resources, and other cloud infrastructure. Infrastructure changes are also validated through CI pipelines before deployment.

This approach ensures deployments are **automated, secure, auditable, and fully version-controlled**, with Git serving as the **single source of truth**.




# Question 6

### **Question:**

Suppose someone tries to deploy an application **outside the CI/CD pipeline**. How would you ensure that **only authorized images** are deployed to the cluster, even if someone bypasses the pipeline? Explain how you would enforce **image authorization**, **image signing**, and **image verification**, and how you would **configure** this mechanism.

### **Answer:**

This is an **image trust** problem rather than an authentication problem. The goal is to ensure that only trusted images built by our CI/CD pipeline are allowed to run.

Our approach would be:

1. **Image Signing**

   * Every Docker image built by the CI/CD pipeline is digitally signed using **Cosign**.
   * The signing key is securely stored in a KMS or managed securely within the organization.

2. **Image Scanning**

   * Before signing, the image is scanned using **Trivy** (or another vulnerability scanner).
   * Only images that pass the defined vulnerability thresholds are approved.

3. **Private Artifact Registry**

   * Only images stored in the organization's **trusted private registry** (Nexus, Artifact Registry, or ECR) are considered valid.
   * Deployments from public registries are restricted.

4. **Admission Policy**

   * On Kubernetes, we enforce an admission policy using **OPA Gatekeeper**, **Kyverno**, or **GKE Binary Authorization**.
   * During deployment, the admission controller verifies:

     * The image originates from the trusted registry.
     * The image signature is valid.
     * The image satisfies organizational security policies.

5. **Reject Unauthorized Images**

   * If the image is unsigned, tampered with, or not built through the approved CI/CD pipeline, Kubernetes rejects the deployment before the pod is created.

This ensures that even if someone manually executes a `kubectl apply`, only trusted and verified container images can run inside the cluster.



# Question 7

### **Question:**

Suppose the application is deployed, but the container keeps restarting (**CrashLoopBackOff**). How would you **troubleshoot** the issue and ensure the correct application is deployed?

### **Answer:**

My troubleshooting approach is systematic.

**Step 1 – Verify Pod Status**

```bash
kubectl get pods
```

Confirm whether the pod is in **CrashLoopBackOff**, **Error**, or **ImagePullBackOff**.



**Step 2 – Check Pod Events**

```bash
kubectl describe pod <pod-name>
```

Review Kubernetes events for scheduling failures, probe failures, image pull errors, or resource issues.



**Step 3 – Review Container Logs**

```bash
kubectl logs <pod-name>
```

Identify application startup errors such as:

* Missing configuration
* Database connection failures
* Missing Secrets or ConfigMaps
* Dependency failures
* Runtime exceptions



**Step 4 – Validate Configuration**

Verify:

* Environment variables
* Secrets
* ConfigMaps
* Mounted volumes
* Image version
* Image tag



**Step 5 – Verify Health Probes**

Ensure **Readiness**, **Liveness**, and **Startup Probes** are correctly configured and not causing unnecessary restarts.



**Step 6 – Check Resource Constraints**

Verify whether the container is:

* **OOMKilled**
* CPU throttled
* Hitting resource limits



**Step 7 – Validate External Dependencies**

Ensure required services such as databases, APIs, message queues, or caches are reachable.

After identifying the root cause, I fix the issue, rebuild the image if required, redeploy, and verify that all pods reach the **Running** and **Ready** state.



# Question 8

### **Question:**

Can you **prevent CrashLoopBackOff** errors **before deployment** instead of troubleshooting them later?

### **Answer:**

Yes. While not every runtime issue can be prevented, we can significantly reduce the chances of **CrashLoopBackOff** by introducing validation gates before deployment.

Our pipeline includes:

* Running **unit and integration tests**.
* Validating Kubernetes manifests using **Helm lint** and dry-run validation.
* Verifying required **Secrets**, **ConfigMaps**, and environment variables.
* Building and testing the Docker image before deployment.
* Performing vulnerability scans and security validation.
* Deploying first to **Dev/UAT** environments and executing smoke tests.
* Validating application startup before promoting the release.

However, some issues such as unavailable databases, third-party API failures, or unexpected runtime bugs can only be detected after deployment. That's why runtime health checks and monitoring are equally important.



# Question 9

### **Question:**

Suppose users are already accessing your application. If someone deploys a faulty version that results in **CrashLoopBackOff**, how would you ensure users **never experience downtime** or a **Service Unavailable** error? How would you prevent unhealthy pods from serving traffic?

### **Answer:**

The key is to ensure Kubernetes never routes user traffic to unhealthy pods.

We achieve this through:

### **1. Readiness Probes**

A pod only receives production traffic after it successfully passes the readiness check.

If the application fails to start or enters **CrashLoopBackOff**, Kubernetes never adds it to the Service endpoints.



### **2. Rolling Update Strategy**

We configure deployments using:

* `maxUnavailable: 0`
* `maxSurge: 1`

This ensures existing healthy pods continue serving users while new pods are being created.



### **3. Progressive Deployment**

For critical applications, we prefer **Blue-Green** or **Canary Deployments**.

* Deploy the new version.
* Validate health.
* Gradually shift traffic.
* Roll back immediately if issues are detected.



### **4. Automatic Rollback**

If rollout health checks fail, tools like **Argo CD**, **Helm**, or Kubernetes rollout mechanisms automatically revert to the previous stable version.



### **5. Continuous Monitoring**

During deployment, we monitor:

* Pod health
* Application logs
* Prometheus metrics
* Error rates
* Response latency

This approach ensures users continue accessing healthy application instances throughout the deployment process.



# Question 10

### **Question:**

You mentioned **health checks**. Can you explain what those checks are, how they work, and **how you configure them**?

### **Answer:**

Kubernetes provides three types of health checks.

### **1. Startup Probe**

* Used for applications with long startup times.
* Kubernetes waits until the application has started successfully before performing other health checks.
* Prevents premature container restarts during initialization.



### **2. Readiness Probe**

* Determines whether the application is ready to receive traffic.
* Until the readiness probe succeeds, Kubernetes does **not** route requests to that pod.
* This helps prevent users from accessing partially initialized applications.



### **3. Liveness Probe**

* Checks whether the application is still running correctly after startup.
* If the probe repeatedly fails, Kubernetes automatically restarts the container.



### **Configuration**

These probes are configured in the Kubernetes Deployment manifest.

Typically, we define:

* HTTP endpoint (for example `/health` or `/ready`)
* Port
* `initialDelaySeconds`
* `periodSeconds`
* `timeoutSeconds`
* `failureThreshold`

For example:

* **Startup Probe** waits for the application to initialize.
* **Readiness Probe** ensures dependencies such as database connectivity are established before serving traffic.
* **Liveness Probe** continuously checks application health and automatically recovers failed containers.

Properly configured probes improve application availability, prevent unnecessary restarts, and ensure users are served only by healthy application instances.




# Question 11

### **Question:**

You mentioned **rollback**. How do you actually **configure rollback** in Kubernetes? What needs to be configured to enable rollback?

### **Answer:**

Rollback is achieved by combining **deployment strategies**, **health checks**, and **deployment automation**.

**1. Configure Deployment Strategy**

* In the Kubernetes Deployment manifest, define the update strategy:

  * **RollingUpdate**
  * **Blue-Green**
  * **Canary** (using Argo Rollouts or a service mesh)



**2. Configure Health Checks**

* **Startup Probe**
* **Readiness Probe**
* **Liveness Probe**

These ensure Kubernetes only routes traffic to healthy pods.



**3. Monitor Rollout Status**

After deployment, the CI/CD pipeline waits for the rollout to complete.

```bash
kubectl rollout status deployment/<deployment-name>
```

If the rollout fails or pods remain unhealthy, the deployment is marked as failed.



**4. Roll Back**

Rollback can be performed using:

```bash
kubectl rollout undo deployment/<deployment-name>
```

If using **Helm**:

```bash
helm rollback <release-name> <revision>
```

If using **Argo CD**, rollback can be performed by syncing the previous Git revision or using the rollback option.



**5. GitOps Approach**

Since Git is the source of truth, reverting the Git commit automatically restores the previous stable version.

This approach enables safe, repeatable, and automated recovery with minimal downtime.



# Question 12

### **Question:**

What **deployment strategy** do you configure in Kubernetes? Explain **Rolling Update**, how it works, and what other strategies such as **Canary** are available for safer deployments and rollbacks.

### **Answer:**

The deployment strategy depends on the application's criticality.

### **1. Rolling Update (Default)**

This is the most commonly used strategy.

* Kubernetes gradually replaces old pods with new ones.
* New pods are created before old ones are terminated.
* Traffic is shifted only after the **Readiness Probe** succeeds.

Typical configuration:

* **maxUnavailable: 0**
* **maxSurge: 1**

This minimizes downtime during upgrades.



### **2. Blue-Green Deployment**

* Maintain two identical environments:

  * **Blue** (Current Production)
  * **Green** (New Version)
* Validate the Green environment completely.
* Switch traffic after successful validation.
* Roll back instantly by directing traffic back to Blue.

Suitable for business-critical applications.



### **3. Canary Deployment**

* Deploy the new version to a small percentage of users (5–10%).
* Monitor:

  * Error rate
  * Latency
  * Resource utilization
* Gradually increase traffic if everything is healthy.
* Roll back immediately if issues are detected.

Often implemented using **Argo Rollouts**, **Istio**, or **NGINX Ingress**.



**In production, Rolling Update is sufficient for many applications, while Blue-Green and Canary are preferred for high-availability and customer-facing services where minimizing deployment risk is critical.**



# Question 13

### **Question:**

Have you worked on **Terraform**?

### **Answer:**

Yes.

I have hands-on experience with **Terraform** for provisioning and managing cloud infrastructure using Infrastructure as Code (IaC).

My responsibilities include:

* Developing reusable **Terraform modules**
* Managing multiple environments using variables and remote state
* Provisioning cloud infrastructure on AWS
* Integrating Terraform execution into Jenkins CI/CD pipelines
* Reviewing execution plans before deployment
* Managing infrastructure updates through version-controlled code

Terraform helped us standardize infrastructure provisioning, reduce manual effort, and ensure consistent deployments across environments.



# Question 14

### **Question:**

What exactly have you implemented using **Terraform**? Explain the **reusable modules** you created and the type of **infrastructure** you provisioned.

### **Answer:**

In our project, we followed a **modular Terraform architecture** to promote reusability and consistency.

I created and maintained reusable modules for:

* **VPC**
* **Subnets**
* **Security Groups**
* **EC2**
* **IAM Roles and Policies**
* **S3 Buckets**
* **Load Balancers**
* **EKS Clusters**
* **Node Groups**

For each environment (Dev, QA, UAT, Production), we reused the same modules while changing only variables such as:

* Environment name
* CIDR ranges
* Instance types
* Desired node count
* Tags

Our Terraform workflow included:

* `terraform fmt`
* `terraform validate`
* `terraform plan`
* Manual approval
* `terraform apply`

We stored the Terraform state remotely to support team collaboration and state locking.

Using reusable modules significantly reduced code duplication and ensured consistent infrastructure across all environments.



# Question 15

### **Question:**

Which **AWS resources** have you provisioned using Terraform (**EC2, S3, VPC, Subnets, IAM, Kubernetes Clusters**)?

### **Answer:**

Using Terraform, I have provisioned and managed several AWS resources, including:

* **VPC**
* **Public and Private Subnets**
* **Internet Gateway**
* **NAT Gateway**
* **Route Tables**
* **Security Groups**
* **Network ACLs**
* **EC2 Instances**
* **IAM Users, Roles, and Policies**
* **S3 Buckets**
* **Application Load Balancers**
* **Auto Scaling Groups**
* **EKS Clusters**
* **Managed Node Groups**
* **CloudWatch Log Groups** (where required)

I also configured resource dependencies using Terraform references so infrastructure was created in the correct order.

For example:

* VPC → Subnets → Security Groups → Load Balancer → EKS/EC2

Terraform automatically determines this dependency graph based on resource references, allowing the complete infrastructure to be provisioned in a single `terraform apply` execution.



# Question 16

### **Question:**

Suppose you need to provision an **EC2/Compute Engine** instance inside a **VPC**, but the VPC itself is **not yet created**. Since Terraform provisions everything together, how would you ensure the instance is deployed into the correct VPC? Explain how you handle **resource dependencies**, **outputs**, and **inputs**.

### **Answer:**

Terraform automatically manages resource dependencies through **resource references**, so we don't have to manually control the execution order.

Our approach is:

### **1. Create the Network Infrastructure**

First, define:

* VPC
* Public/Private Subnets
* Internet Gateway
* Route Tables
* Security Groups

### **2. Reference the Resources**

When creating the EC2 instance (or GCP Compute Engine), I reference the subnet and security group created earlier.

For example:

* EC2 references the **Subnet ID**
* Security Group references the **VPC ID**

Because of these references, Terraform understands the dependency graph automatically.

### **3. Modular Design**

If using modules:

* The **VPC module** exports outputs such as:

  * `vpc_id`
  * `private_subnet_ids`
* The **EC2 module** accepts these values as input variables.

### **4. Single Deployment**

When executing:

```bash
terraform apply
```

Terraform creates resources in the correct sequence:

* VPC
* Subnets
* Route Tables
* Security Groups
* EC2 Instance

No manual sequencing is required because Terraform builds the dependency graph internally.

This modular approach improves reusability, maintainability, and consistency across environments.



# Question 17

### **Question:**

Have you worked on **Logging and Monitoring**?

### **Answer:**

Yes.

Monitoring and observability are an important part of my responsibilities.

For **Infrastructure and Kubernetes Monitoring**, I have worked with:

* **Prometheus** for metrics collection
* **Grafana** for dashboards and visualization
* **Node Exporter** for server metrics
* **Kube State Metrics** for Kubernetes object metrics

For **Logging**, I have worked with:

* **ELK Stack (Elasticsearch, Logstash, Kibana)**
* **Fluent Bit** for collecting container logs
* Kubernetes application logs using `kubectl logs`
* Centralized log analysis for troubleshooting production issues

Typical metrics we monitor include:

* CPU utilization
* Memory utilization
* Disk usage
* Pod health
* Container restarts
* Application latency
* Request throughput
* Error rates

We also configure alerts so that critical issues are detected proactively before impacting users.



# Question 18

### **Question:**

Suppose you have multiple **GCP Projects** (Project A, Project B, Project C) and want to **centralize logs** from multiple projects. How would you implement **centralized logging**? Where would you configure it, how would you configure it, and what **log collectors/forwarders/plugins** would you use?

### **Answer:**

To centralize logs across multiple GCP projects, I would implement a centralized logging architecture.

### **Step 1 – Create a Central Logging Project**

Create a dedicated GCP project to act as the centralized logging destination.



### **Step 2 – Configure Log Collection**

If running Kubernetes workloads, deploy **Fluent Bit** (or Fluentd) as a **DaemonSet** in each cluster.

Fluent Bit automatically collects:

* Container logs
* Node logs
* System logs

from every Kubernetes node.



### **Step 3 – Forward Logs**

Configure Fluent Bit or the **Cloud Logging Agent** to forward logs to:

* **Google Cloud Logging**
* or **Elasticsearch/Loki**, depending on organizational architecture.



### **Step 4 – Configure Log Router**

Use **Cloud Logging Log Sinks** to export logs from Project A, Project B, and Project C into the centralized logging project.

Grant the required IAM permissions for the sink service accounts.



### **Step 5 – Visualization**

Use:

* **Cloud Logging**
* **Grafana**
* **Kibana**
* or **BigQuery** (for advanced analytics)

to search, visualize, and analyze logs from all projects through a single interface.

This architecture provides centralized monitoring, easier troubleshooting, compliance, and long-term log retention.



# Question 19

### **Question:**

Do you have any **questions for me**?

### **Answer:**

Yes, thank you.

I have a few questions:

1. Could you briefly explain the **current DevSecOps architecture** and technology stack used by the team?

2. What are the primary responsibilities for this role during the first three to six months?

3. Which **GCP services**, security tools, and CI/CD platforms are primarily used in your environment?

4. How is success measured for this role, and what are the key expectations from the person joining the team?

5. Finally, what would be the next steps in the interview process?

Thank you for your time. It was a great discussion, and I enjoyed learning more about the role and your team's work.


