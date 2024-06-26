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
* `terraform plan -var ec2_instance_type=t2.micro`
  * Problems:
    * Problem1: NO result
      * Solution: Update aws.version
* `terraform apply -var ec2_instance_type=t2.micro`
  * Problems
    * Problem1: 'Unsupported argument enable_classiclink  and enable_classiclink_dns_support '
    * Solution: Update modules.version
* `terraform apply -var='resource_tags={project="my-project",environment="development"}'`
  * Fail, because there is a variable's validation
* `terraform destroy`
  * clean up the infrastructure

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
    * `var.resource_tags["environment"]`
* ways to assign variables
  * via CL -- `terraform * -var VariableName=VariableValue` --
  * via file /
    * must be named
      * ‘terraform.tfvars’
      * ‘*.auto.tfvars’
      * `terraform … -var-file FileName`