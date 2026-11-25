[[Terraform/Terraform|Terraform]]

All the files ending with `.tf` or `.tf.json` are the configuration files which we use to declare resources in.

A _module_ is a collection of such configuration files together in a directory, nested directories are again considered as separate modules.

Terraform evaluates all the configuration files in the module including the root module hence treating all the configuration files as a single document

Root Module == The collection of configuration files in the working directory
## Override files

Terraform loads all the `.tf` and `.tf.json` files together and expects a distinct combination of block type and block name, if two files define the same object twice, Terraform returns an error.

For convenience, Terraform has special handling for files with suffix `_override.tf` or `_override.tf.json` and this also applies to files `override.tf` and `override.tf.json`

Terraform initially skips the override files and then later processes these files each one in alphabetical order. For each top level block defined in the override file Terraform attempts to find the already defined object in the configuration and then merges the override block contents into it.

Merging behavior is different for different block types, please refer the official documentation for more information

## Dependency Lock file

There are two types of external dependencies apart from the Terraform binary.
- Providers
- Modules

Both these dependencies can be individually published and updated, Hence, Terraform must determine which versions of those must be used.

Version constraints within the configuration itself determine which versions can be used, but after selecting a particular version for each dependency, Terraform remembers the decision by storing the version details in a lock file, so that it can make the same decisions in the future.

>[!Note]
>At present, Terraform only keeps track of the provider versions and not the modules versions, hence module versions need to be exactly pinned

Lock file :: .terraform.lock.hcl is stored in the root module or the working directory and is supposed to be committed to the VCS for collaboration

## Dependency installation behavior

When `terraform init` is executed, Terraform will consider both the version constraints provided in the configuration files and the version selections recorded in the lock file.

If a particular provider has no recorded selection, Terraform will select the latest version with respect to the version constraints provided in the configurations

If a particular provider has a recorded selection, Terraform will re-select the same version even if there is a new version available and it is verified against the provided configurations
- If there is a change in the configurations and the selected version is no longer valid as per the provided configurations, Terraform will return an error. You would need to run `terraform init -upgrade` to override the selection in the lock file and re-determine the provider version. This will in turn update the lock file after determining and installing a suitable version.

## Test Files

We can execute tests on the defined Terraform configurations with test files present as `.tftest` or `.tftest.json`
