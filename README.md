terraform-aws-security-group
============================

Terraform module for vpc security groups on AWS


Usage
-----

```hcl
module "security_group" {
  source = "Smartbrood/security-group/aws"
  name        = "my_security_group"
  description = "My security group"
  vpc_id      = "${module.vpc.vpc_id}"

  ingress_rules_from_any  = ["ssh-22-tcp", "http-80-tcp", "https-443-tcp"]

  egress_rules_to_any     = ["any"]

  tags = {
    Terraform = "true"
    Environment = "dev"
  }
}
```


```hcl
module "security_group" {
  source = "Smartbrood/security-group/aws"
  name        = "my_security_group"
  description = "My security group"
  vpc_id      = "${module.vpc.vpc_id}"

  ingress_cidr_blocks     = ["10.100.0.0/0"]
  ingress_rules           = ["ssh-22-tcp", "http-80-tcp", "https-443-tcp"]

  egress_cidr_blocks      = ["10.100.0.0/0"]
  egress_rules            = ["any"]

  tags = {
    Terraform = "true"
    Environment = "dev"
  }
}
```


Authors
-------

Module managed by [Smartbrood LLC](https://github.com/Smartbrood).


License
-------

Apache 2 Licensed. See LICENSE for full details.
