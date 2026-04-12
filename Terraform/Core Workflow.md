[[Terraform/Terraform|Terraform]]

Contains Three stages:
- **Write**: Define the required resources in the configuration files ending with ```.tf``` or ```.tf.json``` .
- **Plan**: Execute the `terraform plan` to validate and check which resources Terraform is going to create, update or destroy.
- **Apply**: After reviewing the changes, execute `terraform apply` to build or destroy the required infrastructure