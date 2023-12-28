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
