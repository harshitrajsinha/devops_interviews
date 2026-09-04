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
