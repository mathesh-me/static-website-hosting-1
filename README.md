#  Terraform AWS S3 Static Website Hosting

## Project Description:
In this project, I developed a streamlined infrastructure for hosting a static website using Terraform and Amazon Web Services (AWS) S3. The primary goal of this project is to demonstrate the automated provisioning and deployment of a web hosting solution for static websites.

## Key Components and Features:

### Terraform Infrastructure as Code (IaC):
I utilized Terraform, an IaC tool, to define and provision the AWS resources required for our static website hosting solution. This allows for version-controlled, repeatable infrastructure deployments.

### AWS S3 Bucket:
I created an S3 bucket to store and serve the static website files. This bucket is configured for website hosting, allowing for easy content delivery.

### Content Upload and Management: 
I provided instructions and scripts for uploading and managing your website content within the S3 bucket.

## Prerequisites:

1. Basic knowledge of AWS services and concepts.
2. Familiarity with Terraform and infrastructure as code principles.
3. An AWS account with appropriate permissions.
4. An IDE of your Choice.
5. This project serves as an excellent foundation for hosting various types of static websites, including personal blogs, portfolio sites, or small business websites.


## Steps :

### Step 1: Set Up Your Development Environment

Install Terraform and the AWS Command Line Interface (CLI) on your local machine.
Configure your AWS credentials by running ```aws configure``` and providing your AWS access key and secret key.

### Step 2: Create a Terraform Configuration File

Create a .tf file (e.g., main.tf) to define your infrastructure as code using terraform in your IDE.

### Step 3: Define your Files 
### Define the AWS provider and required resources like S3 buckets, IAM roles, and policies
1. Define ```provider.tf``` file , you can refer from my repository and make changes as per your needs.
2. And then run ``` terraform init``` command , It will install the necessary things required for connecting to AWS.
3. And then define __resource.tf__ file and __output.tf__ file , You can also refer these two files from my repository.
4. Remember that , first run the code for creating the bucket after bucket creation you can add the remaining code.

### Step 4: Define Your Website Content

Prepare your static website files (HTML, CSS, JavaScript, etc.) locally on your computer.
