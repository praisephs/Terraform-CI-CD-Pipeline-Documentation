# Building Infrastructure Using Terraform and GitHub CI/CD Pipeline

## Prerequisites:

1. ## Install Terraform:
Download and install Terraform from the official website: [Download Terraform](https://developer.hashicorp.com/terraform/install)

2. ## Install Git:
Install Git if you don't have it already. You can download it from [Git Download](https://git-scm.com/downloads)

3. ## GitHub Account:
Create a GitHub account if you don't have one: [GitHub](https://git-scm.com/book/en/v2/GitHub-Account-Setup-and-Configuration)

4. ## GitHub Repository:
Create a new repository on GitHub that will host your Terraform code

5. ## Access to Cloud Provider:
Have access credentials to the cloud provider (e.g., AWS, Azure, GCP) where you want to deploy infrastructure

## Setting up Terraform:

1. ## Initialize Terraform:
- Create a new directory for your Terraform configuration.
- Inside the directory, create a file named **main.tf** and add your Terraform configuration
  ![main](https://github.com/praisephs/basic_model/assets/129758959/dabb5700-104b-4923-9492-4088129e936c)
- Run **terraform init** to intialize your terraform configuration. This ensures that your Terraform environment is set up correctly and ready to interact with your infrastructure

2. ## Create Variables:
- Create a **variables.tf** file to define input variables
 ![var](https://github.com/praisephs/basic_model/assets/129758959/da03f33c-2836-4678-9084-e18c5aafc811) 

3. ## Create provider:
- Create a **provider.tf** file which acts as a centralized location for specifying the Terraform version and provider requirements, contributing to a well-structured and maintainable Terraform project
  
![provider](https://github.com/praisephs/basic_model/assets/129758959/37737ff9-8109-4467-94a0-0fea178268e0)

4. ## Configure Backend (Optional):
- Configure a backend for storing the Terraform state remotely (e.g., Azure Storage)
- Create a **backend.tf** file and configure the backend
![storage](https://github.com/praisephs/basic_model/assets/129758959/3ed9e08c-9083-448e-8b73-1e45daa4e23e)
- Initialize Terraform again with terraform init to apply the backend configuration.

## Setting up CI/CD with GitHub Actions:

1. ## Create GitHub Actions Workflow:
- Inside your GitHub repository, create a .github/workflows directory. Please ensure the directory is .github/workflows and not .github/workflow
- Create a YAML file (e.g., terraform.yaml) for your workflow
  
![pipelinedemo](https://github.com/praisephs/basic_model/assets/129758959/02b1b0ba-51ad-4040-8f94-b4281f4079d9)
- This workflow triggers on every push to the branch and executes Terraform apply

2. ## Add GitHub Secrets:
- In your GitHub repository, go to **"Settings"** > **"Secrets"** and add the necessary secrets (e.g.,ARM_CLIENT_ID, ARM_CLIENT_SECRET, ARM_SUBSCRIPTION_ID and ARM_TENANT_ID).

## Usage:
1. ## Local Testing:
- Test your Terraform configuration locally using terraform plan and terraform apply
  
2. ## Commit and Push
- Commit your changes to the created branch and push to GitHub
  
3. ## GitHub Actions:
- GitHub Actions will automatically trigger the workflow defined in the YAML file
  
4. ## Check Outputs:
- After successful execution, check the Terraform outputs or the cloud provider's console for the deployed resources.

