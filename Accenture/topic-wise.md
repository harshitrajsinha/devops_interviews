## Terraform

1. What are the best practices for designing reusable Terraform modules?<br/>
[Best practices for creating modules](https://app.notion.com/p/Terraform-2f431f57f13e8065984cf372a36f06a0?source=copy_link#35d31f57f13e804b997eff3bf15d88f6)

2. Versioning Terraform modules<br/>
We should store Terraform module code in a Git repository and use tags to version the modules in the form of: vX.Y.Z where X= Major version, Y = Minor version and Z = patch and then we can use Git releases to present that version to end users using documentation and distribution details.
```
Git Tags: Mark a specific commit in Git history. Git Releases: Package a version of software for distribution.
A tag identifies a version in Git; a release presents that version to users with documentation and distribution details.
```

3. Terraform count vs for_each loop<br/>
[Answer](https://app.notion.com/p/Terraform-2f431f57f13e8065984cf372a36f06a0?source=copy_link#3c631f57f13e808fa940d32dabffb7a8)

4. Managing secrets in Terraform
* Avoid hardcoding secrets in configuration file and scan the configuration files for any secret before committing it to remote repository like Git.
* Use secret manager like AWS Secrets Manager or Hashicorp Vault to pass secret values at runtime.
* For secrets at compile time that needs to be present while running terraform plan or apply command, we should pass the values through CLI using `-var` flags and mark the variables as sensitive so that its output is never displayed.
* State files should be stored in remote backend as they contain secrets in plain text and the remote backend should be secured with least-privilege policies.
* Finally, the secrets used should be timely rotated.
