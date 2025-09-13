# IAC-template-related-to-cloud-computing-
IAC template 
main.tf 
provider "aws" {
  region = var.aws_region
}

resource "aws_instance" "web_server" {
  ami           = var.ami_id
  instance_type = var.instance_type

  tags = {
    Name = "MyWebServer"
  }
}

variables.tf 
variable "aws_region" {
  description = "AWS region to deploy resources in"
  default     = "us-east-1"
}

variable "ami_id" {
  description = "AMI ID for the EC2 instance"
  default     = "ami-0c94855ba95c71c99"  # Amazon Linux 2 in us-east-1
}

variable "instance_type" {
  description = "EC2 instance type"
  default     = "t2.micro"
}


output.tf 
output "instance_id" {
  description = "The ID of the EC2 instance"
  value       = aws_instance.web_server.id
}

output "public_ip" {
  description = "Public IP address of the EC2 instance"
  value       = aws_instance.web_server.public_ip
}



read.me 
# Simple AWS EC2 Terraform Deployment

This Terraform configuration deploys a single EC2 instance in AWS.

## Prerequisites

- Terraform installed: https://www.terraform.io/downloads.html
- AWS CLI configured with your credentials: https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html

## How to use

1. Clone this repo:
   ```bash
   git clone <your-repo-url>
   cd <repo-folder>
