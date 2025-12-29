[[Terraform/Terraform|Terraform]]
The main purpose of Terraform language is to define resources, other features in the language make it flexible and convenient to define the resources
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

### Blocks
Blocks are containers which usually represent configuration of some kind of object, like a resource
- A block can have 0 or more labels and can contain any number of arguments or nested blocks

The ordering of the blocks and the files they are organized into are usually not significant, Terraform considers the implicit and explicit references between the resources when determining the order of operations
### Arguments

Arguments assign value to a particular name. These are always present inside a block and the context of block decides the validity of the argument, whether the particular argument is valid, or the type is valid.

