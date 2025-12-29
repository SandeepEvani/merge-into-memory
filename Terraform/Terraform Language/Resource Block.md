[[Terraform Language|Terraform Language]]

Resource Blocks are the direct mapping to the infrastructure that will create.

A resource block declares a resource of specific type with a specific name (2 Block Labels) and the block  body is encapsulated in the `{` and `}` 

Label 1: Resource Type (Can be any one from a set of values)
Label 2: Resource Local Name (arbitrary string which should be unique for a resource type and is used to store the state of the object, Terraform internally uses this particular name to manage the state. Outside Terraform this name does not have any meaning.)

## Removing resources

>[!Note]
 The `removed` block is available in Terraform v1.7 and later. For earlier Terraform versions, you can use the [`terraform state rm` CLI command](https://developer.hashicorp.com/terraform/cli/commands/state/rm) as a separate step.

To destroy a particular resource, we can remove the resource declaration for that object and execute `terraform apply` which will destroy the resource.

To remove a resource from Terraform configuration but would not want to delete the provisioned infrastructure, we would need to remove the object from terraform state. 
- To remove the object from the state file, we can execute the `terraform state rm` and comment/delete the resource declaration block
- Remove the resource declaration with a removed block
```
removed {
  from = aws_instance.example

  lifecycle {
    destroy = false
  }
}
```

## Meta Arguments

### `depends_on`

- `depends_on` is used to explicitly mention dependencies between resources which Terraform cannot implicitly infer.
- The `depends_on` meta argument instructs Terraform to complete all the actions on the dependency object before performing actions on the object which defined the dependency.
- It can be used in all module blocks and resource blocks

### `count`
- The count meta-argument is used to create the specified number of instances of that resource without redefining the resource multiple times
- It can be used with the modules and resource blocks
- In blocks where count is used, there is an additional object `count` made available which has one attribute `index`
- `count.index` - The distinct index number starting from 0
- Referring the block in which the count has been defined would be of the form `<resource_type>.<resource_local_name><count.index>`  and for modules `module.<module_local_name><count.index>`

### `for_each`
- `for_each` meta-argument can be defined in resources and modules and accepts a set or map of strings and creates multiple instances of that resource as per the elements in the `for_each` block
- the `for_each` block creates a object `each` which has 2 attributes::
  - `each.key` : corresponds to the key of the map object provided or the individual string if a set of strings is passed
  - `each.value` : corresponds to the value of the map object provided or the individual string if a set of string is passed
  - for set of strings, the `each.key` and `each.value` are identical
- It is chainable and can refer to other resources but some of the impure functions cannot be used in the `for_each` objects
- Referring the block in which the `for_each` has been defined would be of the form `<resource_type>.<resource_local_name><each.key>`  and for modules `module.<module_local_name><each.key>`

### `provider`
- The provider meta-argument is used to specify a provider for the resource or module to override the default provider.
- The argument reference to replace the default provider is `<PROVIDER>.<ALIAS>`

### `lifecycle`
- The `lifecycle` nested block argument is used to override the default resource behavior during creation, updation and deletion
- There are essentially 4 arguments supported by the `lifecycle` block :
	- `create_before_destroy`: For updates in a resource or an instance of the resource where a force-replacement is required, Terraform usually destroys the instance first and then creates the replacement with the new changes, setting this to `true` would make Terraform to create a resource first and then destroys the older instance later.
	  Terraform would propagate the `create_before_destroy` attribute to all the dependencies for the defined resource
	  Example: resource A has `create_before_destroy` set to true and it depends on resource B, the parameter `create_before_destroy` is also passed in to the resource B and cannot be overridden in the resource B's lifecycle argument
	- `prevent_destroy`: When this meta-argument is set to `true`, Terraform will raise an error while trying to destroy the object.
	- `ignore_changes`:For the list of given attributes, the `ignore_changes` block will enforce Terraform to ignore any changes for the mentioned attributes
	  The attributes in the `ignore_changes` are considered when there is a create operation but not when there is a update operation
	  Keyword `all` can be used to ignore all the attributes in the given resource instance
	- `replace_triggered_by`: This argument takes in a list of resources or attributes of resources and triggers a replace in the resource defined whenever any of the declared attributes are updated
- We can also add `precondition` and `postcondition` blocks with a lifecycle block to specify the assumptions and guarentees
- 