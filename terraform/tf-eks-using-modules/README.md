# AWS EKS Cluster with Terraform

A sample repository to create an EKS cluster on AWS using Terraform.

## Prerequisites

1. **Install the AWS Toolkit Extension in VS Code**  
   Instead of using AWS CLI, we will configure AWS credentials using the **AWS Toolkit extension** in VS Code. This simplifies the process and avoids manual command-line configuration. You can install the AWS Toolkit extension directly from the VS Code extensions marketplace.

2. **Install Terraform**  
   Install Terraform to provision infrastructure as code. Use the following link to install Terraform:  
   👉 https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli

---

## Steps to Set Up EKS

### 1. Configure AWS Credentials in VS Code

- **Install the AWS Toolkit Extension** from the VS Code marketplace if you haven’t done so already.
- Open the **AWS Toolkit** in the VS Code sidebar.
- Click on **"Credentials"** and then **"Create new AWS Profile"**.
- In the profile creation wizard, provide a profile name (e.g., `default`, `dev-profile`, etc.).
- Enter your **Access Key ID** and **Secret Access Key** when prompted. You can obtain these keys from the AWS Management Console under **IAM > Users > Security Credentials**.
- Once the profile is created, it will be listed in the AWS Toolkit sidebar, and this profile will be available for use by Terraform.

  **For more details**, you can refer to the [AWS Toolkit Documentation](https://docs.aws.amazon.com/toolkit-for-vscode/latest/userguide/welcome.html).

This method integrates the credential management directly within your IDE, eliminating the need for manual AWS CLI configuration.

### 2. Initialize Terraform

- Clone this repository using:

  ```bash
  git clone https://github.com/your-repository/terraform-eks.git
  ```

- Navigate to the repository directory and run:

  ```bash
  terraform init
  ```

  This command initializes the Terraform environment, downloading the necessary modules, providers, and other configurations.

### 3. Optionally Review the Terraform Configuration

- Run the following command to see what infrastructure will be created:

  ```bash
  terraform plan
  ```

  This will show the planned infrastructure setup based on your configuration.

### 4. Apply Terraform Configuration to Create the EKS Cluster

- Finally, apply the Terraform configuration to create the EKS cluster and VPC:

  ```bash
  terraform apply
  ```

  Confirm the changes, and Terraform will begin provisioning your infrastructure on AWS.

---

## Summary

This repository utilizes **Terraform modules** to create an EKS cluster and its supporting infrastructure, such as the VPC. By using the **AWS Toolkit extension in VS Code**, we eliminate the need for the AWS CLI, integrating AWS credentials directly within the IDE for a smoother setup process.
