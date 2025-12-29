[[Management and Governance]]

>[!What is Organizations?]
>AWS Organizations is a account management service you can use to consolidate multiple AWS Accounts into an organization that you can create and centrally manage.

![[AWS Organizations.png|Organizational Structure]]

Using Organizations: 
- You can create multiple accounts with a designated responsibility
- Apply policies for governance
- Group accounts to organize workflows
- Simplify billing by using a single payment method and leverage advantages of the consolidated billing for qualifying services

## Features of AWS Organizations

### Manage Multiple AWS accounts
- AWS accounts are natural boundaries for permissions, costs, security and resources and using a multi-account environment is a recommended best practice when scaling your cloud environment. With organizations, we can programmatically create new accounts
### Define and manage your organization
- You can group the newly created or migrated accounts in an organizations under different OUs, apply relevant policies across the Organization on different levels like on the root level, or on a OU or on an individual account
### Secure and monitor your accounts
- You can centrally provide tools and access for your security team to manage the security needs on behalf of the organization.
### Control access and permissions
- Setup AWS IAM Identity Centre to provide access to AWS account and resources using your active directory
### Share resources across accounts
- Using RAM you can now share resources across the organization
### Centrally Audit your accounts
- Activate CloudTrail across accounts which creates a log of all activities
- Use Backups to automatically enforce backup resources
- Define recommended configurations for resources using AWS Config
### Centrally manage billing costs
- Manage all the billing and get consolidated costs based on volumetric usage across the Organization

### Feature Set
There are two available options for feature sets in the AWS Organizations
- **Consolidate Billing**
- **All Features** *(default)*
*Consolidated Billing* only allowed all the accounts in the organization generated a consolidated bill for the resources used in the [[#Management Account]]. No other management capabilities or functionality was allowed in the *Consolidated Billing* feature set.

*All Features* allows you to set central policies and configurations for an entire organization, delegate responsibilities to other accounts or services to define central organizational policies, security mechanisms, audit and resource sharing along with consolidated billing

### Policies
On a broader classification, there are two types of policies
- ***Authorization Policies*** :: Authorization policies are policies that can influence the permissions of a principal across the organization or a subset of the organization. They generally help you manage the security of the AWS accounts.
	***SCPs*** :: SCP or a Service Control Policy is a type of policy that offers control over the total permissions a IAM Identity can have.
	- SCP is very similar to a permissions boundary, but it is applied at the organization level and can also affect the root user of the account
	***RCPs*** :: RCP or a Resource Control Policy that defines control over the maximum available permissions for resources in the organization 
	- RCPs are similar to the resource policies and like SCPs are applied at the organization level.
- ***Management Policies*** :: Management policies are the policies that help you configure and manage certain resources at the organization level.
	- ***Declarative Policies*** :: A _declarative policy_ is a type of policy that allows you to centrally declare and enforce desired configurations for a given AWS service at scale across an organization.
	- ***Backup Policies*** :: A _backup policy_ is type of policy that allows you to centrally manage and apply backup plans to the AWS resources across an organization's accounts.
	- ***Tag policy*** :: A _tag policy_ is type of policy that allows you to standardize the tags attached to the AWS resources in an organization's accounts.
	- ***Chat applications policy*** :: A _chat applications policy_ is a type of policy that allows you to control access to an organization's accounts from chat applications
	- ***AI services opt-out policy*** :: An _AI services opt-out policy_ is a type of policy that allows you to control data collection for AWS AI services for all the accounts in an organization

>[!Note]
>Even though Authorization policies affect the root users in the member accounts, They do not affect any Identity in the management account
### Organizational Structure
An organization is a collection of AWS Accounts in a hierarchical structure with the [[#Root|root]] at the top that can be centrally managed by the management account.
We can create [[#Organizational Units]] (OUs) in the root or in another OU and can group multiple AWS Accounts using different OUs

Any Policies applied centrally by the management account or the delegated administrator account apply to all the elements falling under the specific hierarchy 
### Root
Root is the top-most container in your organizations hierarchy
### Organizational Units
An Organizational Units is a sub-group of the organizations containing AWS Account and other Organizational units
### Management Account
Management account is the account that is used to create the Organization, this account holds the admin activities for the organization
### Member Account
Member accounts are the accounts which either were created in the organization or have joined the organization via the invite from the management account
### Delegated Administrator for Organizations
Delegate the management account's powers and responsibilities to another account in the organization.
### Delegated Administrators for Supported AWS Services
You can assign particular set of services *trusted access* which makes the service a *trusted service*, Making a Service a trusted service allows the service to access the organization, the accounts in the organizations and create a service access role in all individual accounts and perform cumulative actions across all/subset of the accounts in the organization.

### Enable root access management and remove member account root credentials

We can enable root access management from the Management account into any member account and disable the existing root user credentials and not allow the credentials to be recovered using the forgot password. While the root user credentials are removed, the management account can assume a privileged session to perform following actions in the member account: 
- Remove a misconfigured bucket policy from a S3 bucket
- Remove a misconfigured SQS Queue policy from a SQS queue
- Allow the root user to recover his credentials

