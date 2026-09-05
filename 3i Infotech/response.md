#### 1. Day-to-day activity as an aspiring DevOps engineer (looking for DevOps role)
- Starts with looking up and applying to any new job opportunities on the portals where I have set job alerts.
- Practice at-least one Bash scripting, or Linux commands, which keeps me familiar with the syntax of these tools and eventually improves my logic building.
- I alternatively schedule my day to revise a DevOps subject, such as Networking, Terraform concepts, or Kubernetes scenario-based problems, or work on building an end-to-end DevOps pipeline on a forked GitHub project.
- I dedicate the evening and nighttime to learn something new in the DevOps and AI domains, mostly through blogs on Medium or LinkedIn, or I try to build an AI pipeline using RAG or MCP. I am also upskilling in FastAPI, so at times I spend time building production-grade APIs.

<hr/>

### 2. Multi-node deployment using GitHub Actions
- I have used GitHub Actions for multi-node deployment. For multi-node deployment, I use Kubernetes which is deployed via Helm and reconciled using ArgoCD which automatically deploys in rolling update fashion by default to achieve near zero-downtime deployment. CD workflow, in GitHub Actions, is used to update image tag in Helm manifest file.
- This CD workflow is run immediately after the CI workflow in prod branch as a result of which the GitHub SHA value used to tag container image in CI workflow is passed onto the CD workflow to download the same image. CD workflow requires an approval as the first step which not only adds security but also allows to schedule deployment some time later.
- In case I would be performing manual deployment on multiple node, I would have a script that would perform deployment in rolling update fashion so that not all the nodes are stopped at once but rather one or a small group of nodes would be updated first and once their health checks would pass, the next batch would get the update.
- If I talk about CI workflow on prod branch, it will only get triggered on a pull_request, either from a long-lived branch like dev and test or a short-lived branch like hotfix. The CI workflow would start with checking out the repository. I prefer to run the security checks like secret scan and vulnerability scan in parallel to unit test. This is because both jobs are independent of each other and handled by separate teams like security and development. Only after both the jobs succeed, the build job is run which builds the container image and pushes it to the image registry like DockerHub with a unique immutable tag.
 
<hr/>

### 3. Security scanning in pipeline
- I use different types of security scanning tools at different stages of pipeline. The goal is always to catch any vulnerability as soon as possible, adhering to "Shift Left" principle.
- The first type of security tool I use is "Static Code Analysis" that would detect any code related issues and vulnerabilities without running the the code. We could use tools like Gitleaks for secret scanning, OWASP dependency check or npm audit if it is a nodejs project in order to detect any package vulnerability. For code related issues such as possibility of SQL injection or insecure API we could use SonarQube.
- We may not use all the tools in same pipeline and rather be selective based on what depth the tool covers. For example, we should use tools that would perform basic checks in short-lived branches like feature branch to get faster CI pipeline and tools that would do more detailed analysis in test and prod branch.
- We should also use security plugins and extensions in developer's IDE to catch problems early. For example, if a secret gets leaked and committed to a remote branch, then even if a CI pipeline catches it, it would be in commit history of that branch and we would need to remove the secret separately. Tool like "precommit" could be used.
- Next category of security scanning tool I use is "Dynamic Application Security Testing" that detects similar vulnerability like Static Code Analysis but at runtime. A tool that we can use here is OWASP ZAP.
- Once the container image is built, it is required to scan the image as well. For this I generally use Docker scout in development and Trivy Image scan in production as it gives more detailed report.
- It is also preferred to use SBOM to list all the packages that are going to be shipped in production and store it somewhere so that if any vulnerability is reported in community, we could check if our application is using that package or not.
- Finally, based on the severity level of the vulnerabilities, we could fail the pipeline and report to the respective developer either through some external services like Slack or Gmail or may raise a ticket or comment on the the pull request that triggered the pipeline.

<hr />

- TAR file can be loaded using `docker load -i <tar-file.tar>`
- Kubernetes `cordon` command marks a node as Unschedulable. New pods won't start on it, but existing pods keep running. Used for maintenance.
```bash
| Command            | What it does                                                   |
| ------------------ | -------------------------------------------------------------- |
| `kubectl cordon`   | Stops **new Pods** from being scheduled                        |
| `kubectl drain`    | Evicts **existing Pods** and also makes the node unschedulable |
| `kubectl uncordon` | Allows Pods to be scheduled on the node again                  |
```
