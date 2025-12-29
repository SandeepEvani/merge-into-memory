
>[!What is Terraform?]
Terraform is an open-source tool developed by HashiCorp for declaring Infrastructure as code ([[IaC]]) using the HashiCorp Configuration Language.
> Terraform is a IaC tool that lets you build, change and version infrastructure safely and efficiently
### Terraform' s Plugin based architecture

Terraform uses a plugin based architecture, which is there is a terraform core binary, which is the terraform binary we manually download from terraform official website.

We also have different plugins or providers for terraform to interact with different APIs. These providers are specified in the terraform config files and are downloaded into the working directory when the 'terraform init' is executed.

The Terraform Core, communicates to the respective backends through the providers.

>[!Important]
>Terraform can determine and install the required provider based upon the terraform configurations written in the directory. This is called as the implicit identification but this is not considered as a best practice in production environment as version mismatches might cause errors while building the infrastructure. 
### Hashicorp Configuration Language

All the Terraform configurations are written in a explicit language called the Hashicorp Configuration language.

Here is a sample how the HCL is written ::
```HCL
# block tempate
<BLOCK_TYPE> "<BLOCK_LABEL>" "<BLOCK_LABEL>" {
	#block configurations
	<IDENTIFIER> = <EXPRESSION>

}
```

#### Terraform Resource block
 Each resource block describes one or more infrastructure objects, such as virtual networks, compute instances, or higher-level components such as DNS records.
 
 ```HCL
 # syntax for resource block
 resource "resource_type" "resource_local_label"{
	 # resource arguments
	 identifier = "argument"
 
 }
```
#### Terraform Provider block

#### Terraform Data block
Terraform Data block is used to retrieve data from the respective API via terraform

#### Terraform Input block
Input variables let you customize aspects of Terraform modules without altering the module's own source code. This functionality allows you to share modules across different Terraform configurations, making your module composable and reusable.

#### Terraform Output block

#### Terraform Local block
Locals block are defined values in Terraform that are used to reduce repetitive references to expressions and values
#### Terraform Module block







