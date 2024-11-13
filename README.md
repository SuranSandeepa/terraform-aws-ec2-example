# Terraform AWS EC2 Example

This is a simple Terraform project that provisions an AWS EC2 instance using the AWS provider. It demonstrates the basic steps to work with Terraform to deploy infrastructure to AWS.

Before running the project, make sure you have the following installed:

- [Terraform](https://www.terraform.io/downloads)
- [AWS CLI](https://aws.amazon.com/cli/)
- An AWS account with access to create resources.

### Setup Instructions

Follow these steps to get the project running on your machine:

1. **Install Terraform and AWS CLI**

   - Download and install **Terraform** from the [official website](https://www.terraform.io/downloads).
   - Download and install **AWS CLI** from the [official website](https://aws.amazon.com/cli/).

2. **Configure AWS CLI**

   - Open a terminal and run the following command to configure AWS CLI:
     ```bash
     aws configure
     ```
   - Provide your **AWS Access Key ID**, **Secret Access Key**, and **default region** (e.g., `us-east-1`).

3. **Create the Terraform Configuration**

   - Create a `main.tf` file with the following content:
     ```hcl
     provider "aws" {
       region = "us-east-1"
     }

     resource "aws_instance" "example" {
       ami             = "ami-0866a3c86853eaeeba"  # Update with the correct AMI ID
       instance_type   = "t2.micro"
     }
     ```

4. **Run Terraform Commands**

   - Initialize the Terraform project:
     ```bash
     terraform init
     ```

   - Review the Terraform plan:
     ```bash
     terraform plan
     ```

   - Apply the configuration to create the EC2 instance:
     ```bash
     terraform apply
     ```

   - Sometimes, you may encounter an error like **"no subnet found for default VPC"**. If that happens:
     - Go to the AWS Management Console.
     - Navigate to the **VPC Dashboard** > **Subnets**.
     - If there is no default subnet, create one and update your Terraform configuration with the correct subnet ID.

5. **(Optional) Add SSH Key**

   - To enable SSH access to your EC2 instance, go to **AWS EC2** > **Key Pairs** and create a key pair.
   - Add the key name to the Terraform code:
     ```hcl
     key_name = "your-key-name"
     ```

6. **Destroy the Resources**

   - Once you're done with the instance, you can destroy the created resources with the following command:
     ```bash
     terraform destroy
     ```

**Notes:**

- Be sure to update the AMI ID in the `main.tf` file with a valid one for the region you're deploying to.
- This is a basic example. You can customize it further with other AWS resources, networking configurations, and security groups.



### Key Points in the README:
- **Prerequisites**: Lists what the user needs to install (Terraform, AWS CLI, AWS account).
- **Setup Instructions**: Guides learners step-by-step from installing tools to running Terraform commands.
- **Troubleshooting**: Explains the potential error about subnets and how to resolve it.
- **Destroy**: Reminds users to clean up resources with `terraform destroy`.

---

