# Learn Terraform variables
Follow along with this [Learn Terraform variables](https://developer.hashicorp.com/terraform/tutorials/configuration-language/variables) tutorial.


# Goal
* Deploy on AWS
  *  Web application + VPC + load balancer + EC2 instances
* About input variables
  * to parameterize the configuration
  * -- interpolated into -- strings
  * with functions
  * validations

# Prerequisites
* Terraform v1.2+
* [AWS CLI installed locally](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
* AWS account with [associated credentials](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#authentication-and-configuration)

# How to run?
* `terraform init`
* `terraform plan`
  * Problems:
    * Problem1: NO result
      * Solution: Update aws.version
* `terraform apply`
  * Problems
    * Problem1: 'Unsupported argument enable_classiclink  and enable_classiclink_dns_support '
    * Solution: Update modules.version

# Notes
* Where to locate input variables?
  * anywhere
  * 'variables.tf' -- recommended --
* `terraform console`
  * best way to inspect a variable
  * _Example:_ 
    * `var.public_subnet_cidr_blocks`
    * `var.public_subnet_cidr_blocks[1]`
    * `slice(var.private_subnet_cidr_blocks, 0, 3)`