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
