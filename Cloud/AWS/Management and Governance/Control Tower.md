[[Management and Governance]]

>[!Definition]
>AWS Control Tower offers a straight forward way to setup and govern a multi-account AWS environment, following all the prescriptive best practices

Basically, AWS Control Tower is a orchestrator of different AWS services like AWS Organizations, AWS Identity Centre, AWS Service Catalog, Guard Duty and many more, to build a Landing Zone with *drift* detection, which is divergence from the best practices.

**Landing Zone**: A Landing Zone is a well-architected multi-account environment, designed with best practices and industry standards.

**Controls**: Controls or Guardrails is a high level rule that provides ongoing governance of your overall AWS accounts

**Account Factory**: Account factory is a configurable account template which create a new AWS account with the required configurations.

### Structure of an AWS Control Tower

- **Root**: The root of the organization which contains all the OUs and AWS Accounts
- **Security OU**: This OU contains the Log Archive account and Audit accounts, we can create new accounts or bring existing accounts to the Security OU, but these accounts cannot be modified after their Initial Launch
- **Sandbox OU**: An Optional OU created in the Landing Zone
- **IAM Identity Center Directory**: Identity center is also enabled, when the Control Tower is created, By Default, we will have The service managed users, this can also be altered to point to external identities and groups.

### What Happens when we create an AWS Control Tower
- AWS Organizations creates 2 OUs :: The Security OU and the Sandbox OU in the Root OU
- Create or adds two AWS Accounts to the security OU, named the Log Archive Account and the Audit Account
- Creates the default Identity Center and Access Management where the users are managed by the service
- Applies preventive controls (SCPs)
- Applies detective controls (GuardDuty + AWS Config)

In AWS Control Tower preventive controls are implemented with service control policies (SCPs) and resource control policies (RCPs). Detective controls are implemented with AWS Config rules. Proactive controls are implemented with AWS CloudFormation hooks.



