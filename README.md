# DevOps Combined Project — Terraform + Ansible Pipeline

Full infrastructure automation pipeline provisioning and configuring AWS EC2 instances.

## What This Project Does

1. **Terraform** provisions complete AWS infrastructure:
   - VPC, subnet, internet gateway, route tables
   - Security groups (SSH + HTTP)
   - 2 EC2 instances (Ubuntu 22.04)

2. **Ansible** configures both servers automatically:
   - Dynamic inventory (auto-discovers EC2 IPs from AWS)
   - Installs and starts nginx on both servers
   - No manual IP entry needed

## Project Structure
devops-project/
├── terraform/
│   ├── main.tf        # AWS infrastructure
│   └── outputs.tf     # EC2 public IPs
└── ansible/
    ├── aws_ec2.yml    # Dynamic inventory
    └── playbook.yml   # nginx configuration

## Usage

### Step 1 — Provision infrastructure
cd terraform
terraform init
terraform apply

### Step 2 — Configure servers
cd ansible
ansible-playbook -i aws_ec2.yml playbook.yml

### Step 3 — Verify
curl http://<public_ip>

### Cleanup
cd terraform
terraform destroy

## Author
Sindhu Shetty — Senior SRE
LinkedIn: linkedin.com/in/sindhu-shetty-76a035165
GitHub: github.com/sindhu-shetty
