We should not commit:
- state files and their backup files :: terraform.tfstate and terraform.tfstate.*
- the .terraform.tfstate.lock.info file :: This file is automatically created and destroyed during the terraform apply
- .terraform directory, which contains all the providers and modules

and always commit files:
- All terraform configuration files (you can skip the override files if they are only meant for local or personal use).
- Your .terraform.lock.hcl file as this file consists of the information of the providers which are being used and terraform will use the same versions if the lock file is present over determining the versions of the providers to use at the runtime

