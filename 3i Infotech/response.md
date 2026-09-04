#### 1. Day-to-day activity as an aspiring DevOps engineer (looking for DevOps role)
- Starts with looking up and applying to any new job opportunities on the portals where I have set job alerts.
- Practice at-least one Bash scripting, or Linux commands, which keeps me familiar with the syntax of these tools and eventually improves my logic building.
- I alternatively schedule my day to revise a DevOps subject, such as Networking, Terraform concepts, or Kubernetes scenario-based problems, or work on building an end-to-end DevOps pipeline on a forked GitHub project.
- I dedicate the evening and nighttime to learn something new in the DevOps and AI domains, mostly through blogs on Medium or LinkedIn, or I try to build an AI pipeline using RAG or MCP. I am also upskilling in FastAPI, so at times I spend time building production-grade APIs.

<hr/>

### 2. Multi-node deployment using GitHub Actions
- I have used GitHub Actions for multi-node deployment. I usually have two different workflows one for continuous Integration and next is for continuous Delivery or Deployment.
- CI workflow on prod branch only gets triggered on a pull_request, either from a long-lived branch like dev or test or a short-lived branch like hotfix.
- The CI workflow starts with checking out the repository. I prefer to run the security checks like secret scan and vulnerability scan in parallel to unit test. This is because both jobs are independent of each other and either handled by separate teams like security and development (even if handled by one team it is better to give them feedback at once). Only after both the jobs succeed, the build job is run which builds the container image and pushes it to the image registry like DockerHub with a unique immutable tag.
- After the CI workflow, CD workflow is triggered. The CD workflow may contain an approval step as the very first thing so that even if we would have control over when to perform the deployment. Successful approval allows the CD workflow to download the container image. Since the CD depends on CI to succeed and gets triggered just after that, we get the same commit id or github sha value that was used to create the image tag.
- For multi-node deployment, I use Kubernetes which is deployed via Helm and reconciled using ArgoCD. CD workflow use the same image tag and updates the Helm manifest file as its last step.
- After this ArgoCD automatically picks up the changes and perform reconciliation process to update all the nodes.
- In case I would be performing manual deployment on multiple node, I would have a script that would perform deployment in rolling update fashion so that not all the nodes stop at once but rather one or a small group of nodes are first updated and once their health checks would pass, the next batch would then update.
 
<hr/>

### 3. Security scanning in pipeline
- I use different types of security scanning tools at different stages of pipeline. The goal is always to catch any vulnerability as soon as possible, adhering to "Shift Left" principle.
- The first type of security tool I use is "Static Code Analysis" that would detect any code related issues and vulnerabilities without running the the code. We could use tools like Gitleaks for secret scanning, OWASP dependency check or npm audit if it is a nodejs project in order to detect any package vulnerability. For code related issues to find out if there is possibility of SQL injection or insecure API we could use SonarQube.
- We may not use all the tools in same pipeline and rather be selective based on what depth the tool covers. For example, we should use tools that would perform basic checks to get faster CI pipeline in short-lived branches like feature and more detailed analysis in test and prod branch.
- We should also use security plugins and extensions in developer's IDE to catch it early. For example, a secret is leaked and committed, even if it gets caught by CI pipeline during pull request, it would be in commit history which then needs to be removed separately. This is where developer's IDE plugin and extensions could save us. Tool like "precommit" could be used.
- Next category of security scanning tool I use is "Dynamic Application Security Testing" that detects similar vulnerability like Static Code Analysis but at runtime. A tool that we can use here is OWASP ZAP.
- Once the container image is built, it is required to scan the image as well. For this I generally use Docker scout in development and Trivy Image scan in production is it gives more detailed report.
- It is also preferred to use SBOM to list all the packages that are going to be shipped in production and store it somewhere so that if any vulnerability is reported in community, we could check if our application is using that package or not.
- Finally, all the vulnerabilities that are generated, based on the severity level, we could fail the pipeline and report to the respective developer either through some external services like Slack or Gmail or maybe raise a ticket or comment on the the pull request that triggered the pipeline.
