# ⚔️ Terraform Issues and Troubleshooting 💡

## Error with passing Subnet ID/IDS 
* 🤔  Try to pass Subnet ID to from module ID
  ```
  endpoint_subnets           = ["${module.vpc.private_subnets}"]
  ```
* ❌ **error**: `The given "for_each" argument value is unsuitable: "for_each" supports maps and sets of strings, but you have provided a set │ containing type tuple.`
* 🎯 **solution**: If need to use list of subnet remove bracits
  ```
  endpoint_subnets           = "${module.vpc.private_subnets}"
  ```
  if need to use single subnet then use
    ```
  endpoint_subnets           = ["${module.vpc.private_subnets[0]}"]
  ```
* 🙌🏼 **reference**: https://stackoverflow.com/questions/60213404/error-with-subnet-id-while-creating-ec2-instaces-with-module


## How to get all CIDR's of a existing VPC
* 🤔  How to get all CIDR's of a existing VPC
  ```
  cidr_blocks       = data.aws_vpc.example.cidr_block[0]
  ```
* ❌ **error**: Unable to fetch the values of all the CIDR
* 🎯 **solution**: `data.aws_vpc.example.cidr_block_associations[*].cidr_block`
  ```
  data "aws_vpc" "example" {
    id = "vpc-0f67a3b2exxxxxx"
  }
  
  resource "aws_security_group_rule" "example" {
    type              = "ingress"
    from_port         = 22
    to_port           = 22
    protocol          = "tcp"
    cidr_blocks       = data.aws_vpc.example.cidr_block_associations[*].cidr_block
    security_group_id = "sg-0e40fe769816xxxxx"
  }
  ```
* 🙌🏼 **reference**: [https://stackoverflow.com/questions/60213404/error-with-subnet-id-while-creating-ec2-instaces-with-module](https://stackoverflow.com/questions/75690181/how-to-get-all-cidrs-of-a-existing-vpc-and-add-them-to-security-group-as-inboun)https://stackoverflow.com/questions/75690181/how-to-get-all-cidrs-of-a-existing-vpc-and-add-them-to-security-group-as-inboun

## Terraform Import successful but state file not updated
* 🤔  Try to import some AWS resources on terraform 
* ❌ **error**: But it show import is successful but the terraform plan and terraform state file not showing resources
* 🎯 **solution**: if you are using manual import command for terraform import make sure **not** to use terraform version **1.5** use any <1.5 version
