# terraform-issues

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

## Migrate Terraform state file from OLD AWS s3 bucket to New AWS S3 bucket
* 🤔  Migrate Terraform state file from OLD AWS s3 bucket to New AWS S3 bucket
* ❌ **error**: 
* 🎯 **solution**:
* 🙌🏼 **reference**: 
  * [https://stackoverflow.com/questions/60213404/error-with-subnet-id-while-creating-ec2-instaces-with-module](https://stackoverflow.com/questions/71048464/manually-moving-a-state-file-to-a-different-backend/71054509#71054509)https://stackoverflow.com/questions/71048464/manually-moving-a-state-file-to-a-different-backend/71054509#71054509
  * https://stackoverflow.com/questions/69735414/how-can-i-move-terraform-state-in-an-old-s3-bucket-to-a-new-s3-bucket
