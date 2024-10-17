# Terraform-AWS-Demo

Welcome to the **Terraform-AWS-Demo** repository! This repository contains Terraform code designed to automate the setup of basic AWS infrastructure components. This setup includes creating a VPC, an Internet Gateway, a custom route table, a subnet, a security group, a network interface, an Elastic IP, and an Ubuntu server with Apache2 installed.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Directory Structure](#directory-structure)
- [Usage](#usage)
  - [Initialization](#initialization)
  - [Execution](#execution)
- [Resources Created](#resources-created)
- [Configuration](#configuration)
- [Notes](#notes)
- [License](#license)

## Prerequisites

Before using this Terraform configuration, make sure you have:

1. **Terraform:** Install Terraform from [Terraform's official website](https://www.terraform.io/downloads.html).
2. **AWS CLI:** Configure your AWS CLI with the necessary credentials. Install it from the [AWS CLI installation page](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html).
3. **An AWS Account:** Ensure you have access to an AWS account with the appropriate permissions to create the resources defined in this configuration.

## Directory Structure

The repository contains the following main files:

- `main.tf`: The primary Terraform configuration file. It includes code to create the VPC, Internet Gateway, Route Table, Subnet, Security Group, Network Interface, and Ubuntu server.
- `variables.tf`: Defines the variables used in `main.tf`.
- `outputs.tf`: Specifies the output values to retrieve information about the created resources.

## Usage

### Initialization

1. Clone the repository:

   ```bash
   git clone https://github.com/your-repo/Terraform-AWS-Demo.git
   cd Terraform-AWS-Demo
   ```

2. Initialize Terraform:

   ```bash
   terraform init
   ```

   This command will download the necessary Terraform providers and set up the working directory.

### Execution

1. Review the configuration:

   ```bash
   terraform plan
   ```

   This command will show you the resources that will be created or modified.

2. Apply the configuration:

   ```bash
   terraform apply
   ```

   Confirm the prompt to proceed with the creation of resources.

3. To destroy the created resources:

   ```bash
   terraform destroy
   ```

   Confirm the prompt to delete the resources.

## Resources Created

The Terraform code in this repository performs the following tasks:

1. **Create a VPC:** A Virtual Private Cloud (VPC) to isolate resources.
2. **Create an Internet Gateway:** An Internet Gateway attached to the VPC for external internet access.
3. **Create a Custom Route Table:** A route table to manage routing within the VPC.
4. **Create a Subnet:** A subnet within the VPC for placing resources.
5. **Associate Subnet with Route Table:** The subnet is associated with the custom route table.
6. **Create a Security Group:** A security group that allows inbound traffic on ports 22 (SSH), 80 (HTTP), and 443 (HTTPS).
7. **Create a Network Interface:** A network interface with an IP address in the created subnet.
8. **Assign an Elastic IP:** An Elastic IP associated with the network interface for stable IP addressing.
9. **Create an Ubuntu Server:** An Ubuntu server with Apache2 installed and enabled.

## Configuration

The following variables can be configured in `variables.tf`:

- `region`: The AWS region where resources will be created.
- `vpc_cidr`: The CIDR block for the VPC.
- `subnet_cidr`: The CIDR block for the subnet.
- `instance_type`: The type of EC2 instance for the Ubuntu server.
- `ami_id`: The AMI ID for the Ubuntu server.

Update these variables as needed to meet your requirements.

## Notes

- Ensure your AWS user has sufficient permissions to create and manage the specified resources.
- Be mindful of resource limits and quotas in your AWS account to avoid hitting limits during creation.
- Review the Terraform state files to keep track of your infrastructure's state.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

If you have any questions or need further assistance, feel free to reach out. Happy Terraforming!
