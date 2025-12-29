[[Terraform Language|Terraform Language]]

Provisioners are used to prepare the provisioned infrastructure using specific actions on the local or remote machine.

>[!Note]
>**Provisioners are to be used as a last resort** and if there is any direct provider functionality that fulfills the given requirement, it is recommended to use it over provisioners as:
>Terraform cannot include these provisioners in plans and state files as they could perform a wide range of operations

Provisioner blocks are added in the resource blocks.

### Connections
Most of the times, provisioners would require a connection to the remote system to provision it, hence the provisioners would require a connection block with required parameters to open a connection to the respective remote instance, for the same purpose, in the terraform configuration files along with the provisioner, we also define a connection block, which can be nested in the resource block which act as a global config for all the provisioners in the resource or can be defined in the respective provisioner to override the default connection block provided.

### The `self` object
For a provisioner to reference the parent object for attributes, using the `resource_type` and `resource_name` would cause a cyclic dependency, to avoid that, there is a `self` object which is created to output the attributes of the created instance.

### Arguments common across the provisioners
- `on_failure` : This argument specifies Terraform how to proceed if the provisioner failed, the default behavior which is `fail`  would taint the resource and return an error, setting this parameter to `continue` would continue the execution of the Terraform apply
- `when`: when this parameter is set to destroy, this will execute the provisioner during the destroy phase of the terraform apply

### Provisioner without a resource
When it is not logical to associate a provisioner to a specific resource, we can associate the provision with a `null_resource` or `terraform_data`, with these resources, we could provide a input and also trigger provisioners when ever there is a change in the mentioned resources n the triggers

There are 3 types of provisioners:
- `file`: copies files or directories from local machine where terraform is getting executed to the remote infrastructure
  arguments:
	- `source`: the source file/directory location which is to be copied
		- For sources ending with a /, Terraform copies all the files from the source to the destination, but if a / is not present in the end, then it copies the entire directory provided
	- `content`: provide content in a string format which should be written to the remote machine
	- `destination`: The location in the remote machine where the items must be written to.
- `local-exec`: 
- `remote-exec`: