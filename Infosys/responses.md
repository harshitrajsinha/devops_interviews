# Round-1:

### 5. Terraform plan & Terraform apply
* Terraform plan command compares the desired state and current state and specifies what changes terraform is going to perform to meet the desired state. The output of `terraform plan` command can be stored separately by creating an execution plan using `-out` flag.
* Terraform apply command applies the changes specified by terraform plan command which can create, update or delete resources on a provider like AWS to meet the desired state. We could run terraform apply on an already created execution plan by specifying the name of the execution plan file at the end of terraform apply command.
