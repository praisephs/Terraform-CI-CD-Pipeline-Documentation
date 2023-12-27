# Building Infrastructure Using Terraform and GitHub CI/CD Pipeline

## Building Cloud Infrastructure
Building infrastructure on the cloud refers to the process of creating and configuring computing resources and services in a cloud environment to support the needs of applications and workloads. Traditional infrastructure involves physical servers, networking hardware, and storage devices located in on-premises data centers. In contrast, cloud infrastructure leverages virtualization and cloud services provided by third-party vendors.

## Key aspects of building infrastructure on the cloud include:

1. ## Virtualization
Cloud infrastructure relies heavily on virtualization technologies, allowing users to create virtual instances of servers, storage, and network resources. Virtualization enables the efficient use of physical hardware and provides flexibility in scaling resources up or down based on demand.

2. ## On-Demand Resources
Cloud providers offer a range of services that can be provisioned on-demand. Users can quickly allocate and de-allocate resources, paying only for what they use. This elasticity is a fundamental characteristic of cloud infrastructure

3. ## Service Models
Cloud infrastructure is typically categorized into three service models:

## Infrastructure as a Service (IaaS)
Provides virtualized computing resources over the internet, such as virtual machines, storage, and networking.
Use cases or examples of Infrastructure as a Service (IaaS) are:

**Amazon EC2 (Elastic Compute Cloud):**
- Provider: Amazon Web Services (AWS)
- Description: EC2 provides resizable compute capacity in the cloud. Users can launch virtual servers (instances) and scale them up or down based on demand
  
**Google Compute Engine:**
- Provider: Google Cloud Platform (GCP)
- Description: Compute Engine offers virtual machines that run on Google's infrastructure. Users have control over the VMs' configuration, including choice of instance type and operating system
  
**Microsoft Azure Virtual Machines:**
- Provider: Microsoft Azure
- Description: Azure VMs provide on-demand scalable computing resources. Users can deploy virtual machines running Windows or Linux and customize them as needed

## Platform as a Service (PaaS)
Offers a platform with development and deployment tools to build and manage applications without dealing with the underlying infrastructure.
Use cases of Platform as a Service (PaaS) are:

**Heroku:**
- Provider: Salesforce (Heroku)
- Description: Heroku is a cloud platform that allows developers to build, deploy, and scale applications without managing the underlying infrastructure. It supports multiple programming languages and frameworks

**Google App Engine:**
- Provider: Google Cloud Platform (GCP)
- Description: App Engine is a fully managed platform that automatically scales applications based on demand. It supports multiple languages and allows developers to focus on building code without managing infrastructure
  
**Azure App Service:**
- Provider: Microsoft Azure
- Description: Azure App Service is a fully managed platform for building, deploying, and scaling web apps. It supports multiple programming languages and provides features like automatic scaling and continuous integration

## Software as a Service (SaaS)
Delivers software applications over the internet, eliminating the need for users to install, manage, and maintain the software.
Examples of Software as a Service (SaaS) are:

**Salesforce:**
- Description: Salesforce is a customer relationship management (CRM) platform delivered as a service. Users access Salesforce applications through a web browser without needing to install or maintain software
  
**Microsoft 365 (formerly Office 365):**
- Description: Microsoft 365 is a suite of cloud-based productivity tools that includes applications like Word, Excel, PowerPoint, and collaboration services like Microsoft Teams. Users can access these tools online
  
**Google Workspace (formerly G Suite):**
- Description: Google Workspace is a set of cloud-based collaboration and productivity tools, including Gmail, Google Drive, Google Docs, and more. It enables real-time collaboration and communication.

4. ## Scalability
Cloud infrastructure allows for easy scaling of resources to accommodate changes in workload. Scaling can be done vertically (increasing the power of individual resources) or horizontally (adding more instances of resources)

5. ## Managed Services
Cloud providers offer managed services that handle specific aspects of infrastructure management, such as databases, machine learning, or content delivery networks. These services reduce the operational burden on users, allowing them to focus more on application development and less on infrastructure management

6. ## Global Reach
Cloud providers have data centers distributed globally. This allows users to deploy applications closer to end-users, improving performance and reducing latency.

7. ## Automation and Infrastructure as Code (IaC)
Cloud infrastructure is often provisioned and managed through automation tools and IaC frameworks like Terraform or AWS CloudFormation. This enables the creation and maintenance of infrastructure using code, making it reproducible and version-controlled.

8. ## Security and Compliance
Cloud providers invest heavily in security measures to protect infrastructure. Users can leverage built-in security features and compliance certifications to ensure that their infrastructure meets industry standards.

# GitHub CI/CD Pipeline: Streamlining Software Delivery
Continuous Integration and Continuous Delivery (CI/CD) is a software development practice that aims to automate the building, testing, and deployment of code changes. GitHub provides a robust CI/CD platform that integrates seamlessly with version control, enabling developers to maintain a rapid and reliable software delivery pipeline

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

