## Terraform

1. Do you create Terraform modules for the team so that others can execute them?
2. Do you also design the Terraform CI/CD pipeline?
3. Can you explain how you designed your Terraform CI/CD pipeline?
4. How do you secure Terraform resources/modules that will be used in production?
5. How do you prevent production resources from being accidentally destroyed by an entry-level engineer?
6. If prevent_destroy = true is configured but the resource still gets destroyed, is that possible? If yes, where do you think it went wrong?
7. Suppose you have prevent_destroy = true, but now you receive a request to decommission that production resource (for example, an Azure DB or AWS RDS). How would you decommission it?
8. Suppose an AKS cluster has two node pools. One node pool was initially provisioned with two nodes using Terraform, but autoscaling increased it to ten nodes. Now you're upgrading Kubernetes or adding tags, and Terraform wants to scale it back to two. How would you avoid that?
9. Where would you configure the ignore_changes lifecycle setting? Is it possible to put it in the resource block?

