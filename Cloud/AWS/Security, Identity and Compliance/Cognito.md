[[Security, Identity and Compliance]]

> [!Definition] 
> Amazon Cognito is an identity platform for web and mobile apps. It’s a user directory, an authentication server, and an authorization service for OAuth 2.0 access tokens and AWS credentials. With Amazon Cognito, you can authenticate and authorize users from the built-in user directory, from your enterprise directory, and from consumer identity providers like Google and Facebook.

Amazon Cognito has two main features in it, they are 
- [[#Cognito User Pools]]
- Cognito Identity Pools

### Cognito User Pools

Generally, A user pool is used when we require an authentication system for a custom application we built, This custom application uses the Cognito User Pools to Authenticate and Authorize users using JSON Web Token (JWT). User pools support both independent directories and identity federation.

### Cognito Identity Pools

Set up an Amazon Cognito identity pool when you want to authorize authenticated or anonymous users to access your AWS resources. we can authenticate users either by the independent directory or an Identity Provider. Post authentication, The Cognito service exchanges the credentials to AWS temporary credentials by using the STS service to generate credentials after assuming a role.

You can authenticate users with a trusted identity provider, like a user pool or a SAML 2.0 service. It can also optionally issue credentials for guest users. Identity pools use both role-based and attribute-based access control to manage your users’ authorization to access your AWS resources.