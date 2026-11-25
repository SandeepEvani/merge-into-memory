
Starting with the demo, we have a multi-account environment:
- The management account :: Used to manage billing, users and permissions and other accounts in an AWS Organization.

- The development account :: used for all the development and deployment activities, POCs, experiments and Labs.

- The test account :: used for project based testing for the deployed application for dev to test.

- The prod account :: release any application for user releases.

With these accounts, the AWS Organization is created by the management account and other accounts are either created or invited to this Organization

refer [[Account Heirarchy.canvas|Account Hierarchy]]

All IAM users are created in the management Account, and users switch roles from one account to another account based on the environment they would want to work in. This helps in centrally managing users in one environment.

