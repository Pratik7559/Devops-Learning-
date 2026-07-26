# 🌍 Terraform Notes for DevOps

Welcome to my Terraform learning journey. This repository contains detailed notes for learning Terraform from beginner to advanced.

## Table of Contents
1. Introduction
2. Why Terraform
3. Infrastructure as Code
4. Architecture
5. Installation
6. Workflow
7. Configuration Files
8. Providers
9. Resources
10. Variables
11. Outputs
12. Locals
13. Data Sources
14. State File
15. Backend
16. Remote State
17. Modules
18. Provisioners
19. Lifecycle
20. Workspaces
21. Commands
22. Best Practices
23. AWS with Terraform
24. Interview Questions
25. Mini Projects

---

## Introduction

Terraform is an Infrastructure as Code (IaC) tool developed by HashiCorp that allows you to provision and manage infrastructure using code.

## Why Terraform?

- Open Source
- Multi Cloud Support
- Automation
- Version Control
- Reusable Infrastructure
- Consistent Deployments

## Terraform Workflow

```
terraform init
terraform validate
terraform plan
terraform apply
terraform destroy
```

## Configuration Files

- main.tf
- provider.tf
- variables.tf
- outputs.tf
- terraform.tfvars
- versions.tf

## Providers

- AWS
- Azure
- Google Cloud
- Docker
- Kubernetes
- GitHub

## Resources

Resources define infrastructure such as EC2, VPC, S3, IAM and RDS.

## Variables

Input variables make your code reusable.

## Outputs

Display values like Instance ID, Public IP and DNS Name.

## Locals

Store reusable local values.

## Data Sources

Read existing infrastructure.

## Terraform State

- terraform.tfstate
- State Locking
- Drift Detection

## Backend

- Local
- S3
- Azure Storage
- Google Cloud Storage

## Modules

Reusable Terraform code.

## Provisioners

- local-exec
- remote-exec
- file

## Lifecycle

- create_before_destroy
- prevent_destroy
- ignore_changes

## Workspaces

Manage dev, test and production environments.

## Common Commands

```bash
terraform init
terraform fmt
terraform validate
terraform plan
terraform apply
terraform destroy
terraform output
terraform state list
terraform workspace list
terraform workspace new dev
```

## Best Practices

- Use modules
- Store state remotely
- Never hardcode secrets
- Use variables
- Use Git
- Keep code modular

## AWS Services

- EC2
- VPC
- Subnets
- IAM
- S3
- RDS
- Route53
- Load Balancer

## Interview Questions

- What is Terraform?
- What is IaC?
- What is a provider?
- What is a resource?
- What is a state file?
- What are modules?
- Difference between plan and apply?
- What is backend?
- What are workspaces?

## Mini Projects

- EC2 Deployment
- S3 Bucket
- Custom VPC
- IAM User
- Three Tier Architecture

## Checklist

- [ ] Basics
- [ ] Providers
- [ ] Resources
- [ ] Variables
- [ ] Outputs
- [ ] State
- [ ] Backend
- [ ] Modules
- [ ] Workspaces
- [ ] AWS Projects

⭐ Happy Learning!
