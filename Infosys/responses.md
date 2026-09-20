# Round-1:

### 5. Terraform plan & Terraform apply
* Terraform plan command compares the desired state and current state and specifies what changes terraform is going to perform to meet the desired state. The output of `terraform plan` command can be stored separately by creating an execution plan using `-out` flag.
* Terraform apply command applies the changes specified by terraform plan command which can create, update or delete resources on a provider like AWS to meet the desired state. We could run terraform apply on an already created execution plan by specifying the name of the execution plan file at the end of terraform apply command.

### 6. Terraform vs Ansible
* Terraform is an Infrastructure as Code (IaC) tool used to provision and manage infrastructure resources like creating EC2 instances on AWS provider.
* Ansible is a configuration management tool that is used to install scripts and packages, configure systems, run commands and processes on the provisioned infrastructure.

### 7. Terraform provider
[Terraform Provider](https://github.com/iam-veeramalla/terraform-zero-to-hero/blob/main/Day-1/02-getting-started.md)

### 8. Terraform state file
[Terraform state file - Notion](https://app.notion.com/p/Terraform-2f431f57f13e8065984cf372a36f06a0?source=copy_link#33d31f57f13e80639177f1243e1008c6)
* It is important because Terraform uses the state file to: - track and maintain consistency between desired and existing resources, identify what changes need to be applied, and detect infrastructure drift.

### 9. Terraform drift
[Terraform Drift - Notion](https://app.notion.com/p/Terraform-2f431f57f13e8065984cf372a36f06a0?source=copy_link#35d31f57f13e8070b853d271b081a2e1)

### 11. Terraform Modules
[Terraform Modules - Notion](https://app.notion.com/p/Terraform-2f431f57f13e8065984cf372a36f06a0?source=copy_link#33831f57f13e80d7bdd8f12329724cb5)

### 12. Secure secrets in Terraform
* Avoid hardcoding or storing any sensitive value in terraform code files.
* Use secret management tools like HashiCorp Vault, AWS Secret Manager
* If we have to pass any sensitive value via variables then we should mark that variable as sensitive to avoid output of its value.
* Since state files do not mask the values, we should store state files in a remote backend and apply least privilege policy to avoid any unauthorized access.

### 13. Terraform architecture and internal working of Terraform
* Terraform follows a declarative approach where developers define the desired state in terraform code file written in HCL (HashiCorp Corporation Language), which terraform uses to perform actions.
* The different components involved are -
1. Terraform configuration file - which has `.tf` as extension and contains the desired state of infrastructure.
2. Terraform core - which is the terraform engine that reads configuration code, loads variables, compares desired and current state, create execution plan, communicate to platform to create resources and maintains the lifecycle of resources.
3. Terraform backend - which is used to store terraform state file remotely.
4. Terraform state file - which maintains the current state of infrastructure.
5. Providers - which are plugins through which terraform communicates to platforms like AWS or GitHub to create resources.
6. Dependency graph - which terraform uses to determine the order in which resources should be created, modified, or destroyed
   
* Internal Working of Terraform
```
1. Read configuration
          │
          ▼
2. Initialize providers
          │
          ▼
3. Read desired state
          │
          ▼
4. Compare desired vs current state
          │
          ▼
5. Build dependency graph
          │
          ▼
6. Generate execution plan
          │
          ▼
7. Execute changes
          │
          ▼
8. Update state file
```
