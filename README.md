# Ansible Playbook for Docker Deployment

## Overview

This Ansible playbook automates the deployment of Docker containers on AWS EC2 instances using Terraform for infrastructure provisioning and Ansible for configuration management. It sets up a VPC, subnets, security groups, and EC2 instances necessary for Docker deployment and then installs Docker, Docker Compose, and starts Docker containers.

## Prerequisites

- **Terraform**: Ensure Terraform is installed on your local machine.
- **Ansible**: Ansible must be installed on your local machine.
- **SSH Key Pair**: You should have an SSH key pair to access EC2 instances.
- **Docker Hub Account**: If using a private Docker registry, have credentials ready.

## Directory Structure

- **ansible-playbook-docker**: Contains Terraform configuration and Ansible playbooks.
  - **terraform-ec2**: Terraform configuration for provisioning AWS resources.
    - `main.tf`: Defines AWS resources such as VPC, subnets, security groups, and EC2 instances.
    - `terraform.tfvars`: Variables file containing configuration values.
  - **deploy-docker-ec2-user.yaml**: Ansible playbook for setting up Docker on EC2 instances and starting containers.
  - **deploy-docker-generic.yaml**: Ansible playbook for generic Docker server setup.
  - **deploy-docker-vars.yaml**: Variables file for Docker deployment configuration.
  - **hosts**: Inventory file containing IP addresses of target hosts.
- **manual-installation-docker.sh**: Bash script for manual Docker installation.

## Usage

1. **Update Configuration**:
   - Modify `terraform.tfvars` with appropriate values for your AWS environment.
   - Update Docker registry credentials in `deploy-docker-vars.yaml`.
   - Adjust any other configurations as needed.

2. **Run Terraform**:
   - Navigate to `terraform-ec2` directory.
   - Execute `terraform init` to initialize Terraform.
   - Run `terraform apply` to create AWS resources.

3. **Run Ansible Playbook**:
   - Ensure Ansible is installed and configured.
   - Execute Ansible playbooks:
     - `ansible-playbook deploy-docker-ec2-user.yaml` for EC2 user-based deployment.
     - `ansible-playbook deploy-docker-generic.yaml` for generic server setup.

4. **Manual Installation (Optional)**:
   - If needed, you can use `manual-installation-docker.sh` for manual Docker installation on servers.

## Notes

- Ensure proper IAM permissions are set for the AWS account used by Terraform.
- Modify security group rules according to your application requirements.
- Always follow security best practices when handling credentials and sensitive information.