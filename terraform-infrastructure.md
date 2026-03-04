# Terraform Infrastructure Provisioning Guide

This document describes the workflow used by the team to provision and manage infrastructure using Terraform.

Terraform allows infrastructure to be defined as code and deployed in a consistent and reproducible way across environments.

---

# Prerequisites

Before running Terraform, ensure the following tools are installed and configured.

Required tools:

- Terraform
- Cloud provider CLI (AWS CLI / Azure CLI / gcloud)
- Git
- Access to the infrastructure repository

Verify Terraform installation:
terraform version

Expected result:
Terraform v1.x.x

---

# Repository Structure

A typical Terraform project structure may look like the following:
terraform/
├── main.tf
├── variables.tf
├── outputs.tf
├── providers.tf
├── terraform.tfvars
└── modules/

Description of files:

| File | Purpose |
|-----|------|
| main.tf | Main infrastructure resources |
| variables.tf | Input variables |
| outputs.tf | Outputs returned after provisioning |
| providers.tf | Provider configuration |
| terraform.tfvars | Environment-specific values |

---

# Step 1 — Clone the Infrastructure Repository

Clone the repository containing Terraform configuration.
git clone https://github.com/company/infrastructure.git

Navigate to the Terraform directory:
cd infrastructure/terraform

---

# Step 2 — Initialize Terraform

Initialize Terraform to download required providers and modules.
terraform init

This command will:

- download required provider plugins
- configure the backend
- prepare the working directory

Expected output includes messages confirming provider installation.

---

# Step 3 — Validate Configuration

Validate the Terraform configuration before running a plan:
terraform validate

Expected output:
Success! The configuration is valid.

If validation fails, review syntax errors in Terraform files.

---

# Step 4 — Review Infrastructure Changes

Generate an execution plan to review pending infrastructure changes.
terraform plan

The plan will display:

- resources to be created
- resources to be modified
- resources to be destroyed

Example output summary:
Plan: 2 to add, 0 to change, 0 to destroy.

We should review the plan carefully before applying changes.

---

# Step 5 — Apply Infrastructure Changes

Apply the Terraform configuration to provision infrastructure:
terraform apply

Terraform will prompt for confirmation:
Do you want to perform these actions?
Type: yes
Terraform will then provision the defined infrastructure resources.

---

# Step 6 — Verify Deployment

After the apply step completes, verify the infrastructure.

Checks may include:

- confirming resources exist in the cloud provider console
- verifying network connectivity
- validating application deployment

Example checks:

- verify virtual machines are running
- confirm load balancer endpoints are reachable
- check database connectivity

---

# State Management

Terraform maintains a **state file** that tracks the current infrastructure state.

Best practices:

- store the state file in a remote backend
- restrict direct access to the state file
- enable state locking

Example remote backends:

- AWS S3 + DynamoDB
- Azure Storage
- Terraform Cloud

---

# Common Terraform Commands

| Command | Purpose |
|------|------|
| terraform init | Initialize Terraform environment |
| terraform validate | Validate configuration |
| terraform plan | Preview infrastructure changes |
| terraform apply | Apply configuration changes |
| terraform destroy | Remove infrastructure resources |

Please, use the command "destroy" with caution in production environments
