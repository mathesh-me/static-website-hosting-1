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

### Step 2: Define Your Website Content

Prepare your static website files (HTML) in your particular directory where terraform configuration files are present and name it as index.html , if you want you can also add error.html file also, or you can also refer my repository for static website HTML file.

### Step 3: Create a Terraform Configuration File

Create a .tf file (e.g., main.tf) to define your infrastructure as code using terraform in your IDE.

### Step 4: Define your Configuration Files 
### Define the AWS provider and required resources like S3 buckets, IAM roles, and policies
1. Define ```provider.tf``` file using the below code :

```
provider "aws" {
    region = "ap-south-1"
}
```
2. In your IDE open the terminal and navigate to the directory where you create this configuration files.
3. And then run ``` terraform init``` command , It will install the necessary things required for connecting to AWS.<br>
4. And then define __resource.tf__ file for creating bucket using the below code :

```
resource "aws_s3_bucket" "bucket1" {
    bucket = "web-bucket-mathesh"
  
}
```
5. Use the below command for creating the bucket :

```
terraform apply -auto-approve
```
6. And then add the below codes in __resource.tf__ file :
```
resource "aws_s3_bucket_public_access_block" "bucket1" {
  bucket = aws_s3_bucket.bucket1.id

  block_public_acls       = false
  block_public_policy     = false
  ignore_public_acls      = false
  restrict_public_buckets = false
}

resource "aws_s3_object" "index" {
  bucket = "web-bucket-mathesh"
  key    = "index.html"
  source = "index.html"
  content_type = "text/html"
}

resource "aws_s3_object" "error" {
  bucket = "web-bucket-mathesh"
  key    = "error.html"
  source = "error.html"
  content_type = "text/html"
}


resource "aws_s3_bucket_website_configuration" "bucket1" {
  bucket = aws_s3_bucket.bucket1.id

  index_document {
    suffix = "index.html"
  }

  error_document {
    key = "error.html"
  }

}

resource "aws_s3_bucket_policy" "public_read_access" {
  bucket = aws_s3_bucket.bucket1.id
  policy = <<EOF
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
	  "Principal": "*",
      "Action": [ "s3:GetObject" ],
      "Resource": [
        "${aws_s3_bucket.bucket1.arn}",
        "${aws_s3_bucket.bucket1.arn}/*"
      ]
    }
  ]
}
EOF
}
```

7. And then again run the command :

```
terraform applyb -auto-approve
```
8. The above code will apply the neccessary configurations like static website hosting , bucket policies , public access block off in your bucket.
9. Remember that this codes are I got from terraform documentary page I changed it for my needs , Don't foget to change your bucket name , region and configurations as per your needs.

### Step 5: Define the Output file

1. We use Output file for get your webite link in your IDE , you don't have a need to go for link in AWS Console.
2. Define __output.tf__ file using the below terraform code :
```
output "websiteendpoint" {
    value = aws_s3_bucket.bucket1.website_endpoint
  
}
```
3. And then run the following command :

```
terraform apply -auto-approve
```
4. It will give your website link as output as shown below

![s3](https://github.com/mathesh-me/static-website-host-1/assets/144098846/90551cc8-ed1e-45c3-91b1-ffcce24666e1)

### Step 6: Verify your Work

Copy the link and paste it in your favourite browser.

![s4](https://github.com/mathesh-me/static-website-host-1/assets/144098846/f1908092-afeb-427b-a129-cc291275f4ae)



