[[Security, Identity and Compliance]]

> [!Definition]
> IAM is a globally available and globally resilient service where we can centrally manage permissions that control which AWS resources users can access. You use IAM to control who is [[Authentication|authenticated]] and [[Authorization|authorized]] to use resources.

When an AWS Account is created, there is one Identity that is created automatically by AWS with is called the Account's root user.
This _account root user_ has an unrestricted access over all the resources in that particular AWS account. No policy can restrict an root user.

## The Control and Data Plane of IAM.

**The Control plane** is the management plane of IAM, where we create and manage different IAM resources and assign permissions to different resources. In Short, This handles all the moving parts in IAM.
The Creates, deletes and updates of the IAM is the control plane

**The Data plane** is where all the information regarding the resources is retained. The data plane operates at a much higher scale than the control plane. All the IAM resources and their configurations together make up the Data plane. This Data Plane is replicated across all AWS regions* (Regions before the Hong-Kong region was introduced, post that we need to opt-in to other regions, after we opt-in the data is propagated into those specific regions).
The state of the IAM Identities and resources is the Data Plane, also known as the Auth Data Plane.

The IAM's data plane is internal to the AWS. Any time an request is made by an Identity to an Specific AWS service, the service in-turn makes an API call to the IAM to authenticate and authorize the request.
Therefore, the use of IAM's data plane is to authenticate and authorize the requests from different services.
## How IAM Works

As we have learnt above that each service, whenever a request is received it forwards the authentication headers to IAM data plane. The Auth data plane validates the signature and if the signature is not valid, then the request is errored immediately. For the other case where the signature is valid, we have IAM return a bunch of parameters related to the principal or the caller. Till this point, we have successfully completed the _Authentication_ of the request.

What's coming next is the Authorization of the request, i.e., is the caller at all is privileged enough to make a specific request to the specific service? The answer to this question is deduced by the service in itself, the job of the Auth data plane concludes at verifying the request and returning back the caller metadata with all other IAM metadata (Policies, Groups, Organizations) to the service.

Now, the service with all the required data pieces, starts to evaluate the different policies (based on string matching) against the [[#Request Context]] and proceeds if there is any policy providing an ***explicit allow*** without an ***explicit deny***.

## AWS SigV4

AWS SigV4 is request signing process that is performed either by the user or the AWS SDKs. it's a signing algorithm that actually performs a series of hashes called the HMACs. So we sign the request body and the secret access key together with the region and the service we would like to access. This helps in fast and safe authentication of requests by AWS. For more information refer [AWS re:Invent 2022 - A day in the life of a billion requests (SEC404)](https://www.youtube.com/watch?v=tPr1AgGkvc4)****


## Components of IAM

IAM consists of 4 different Components
- User
	- An IAM user is an identity within your AWS account that has specific permissions for a single person or application.
- Groups
	- An IAM group is an identity that specifies a collection of IAM users.
- Role
	- An IAM role is an identity within your AWS account that has specific permissions. It is similar to an IAM user, but is not associated with a specific person.
		- **Trust policy** – Defines which principals can assume the role, and under which conditions. A trust policy is a specific type of resource-based policy for IAM roles. A role can have only one trust policy.
		    
		- **Identity-based policies (inline and managed)** – These policies define the permissions that the user of the role is able to perform (or is denied from performing), and on which resources.
- Policy
	- You grant permissions to an Identity by creating a policy, which is a document that lists the actions that an Identity can perform and the resources those actions can affect.

![[Classification of different IAM Components.png]]




## AWS IAM Identity Centre

AWS service for SSO.

## IAM Access Analyzer

## Attribute based Access Control (ABAC)

ABAC is an authorization strategy that defines permissions based on attributes, and in AWS there attributes are called as _tags_.
### ABAC vs RBAC

- ABAC scales better when a user/group with an ABAC policy needs access to another set of resources and not in this set.
- ABAC falls short when you need access to both sets as the attributes with the same key will be overwritten.

## Request Context

When a principal tries to use the AWS Management Console, the AWS API, or the AWS CLI, that principal sends a _request_ to AWS. The request includes the following information:

- **Actions or operations** – The actions or operations that the principal wants to perform. This can be an action in the AWS Management Console, or an operation in the AWS CLI or AWS API.
    
- **Resources** – The AWS resource object upon which the actions or operations are performed.
    
- **Principal** – The person or application that used an entity (user or role) to send the request. ***Information about the principal includes the policies that are associated with the entity that the principal used to sign in.***
    
- **Environment data** – Information about the IP address, user agent, SSL enabled status, or the time of day.
    
- **Resource data** – Data related to the resource that is being requested. This can include information such as a DynamoDB table name or a tag on an Amazon EC2 instance.







## References

- [AWS re:Inforce 2022 - AWS Identity and Access Management (IAM) deep dive (IAM301)](https://www.youtube.com/watch?v=YMj33ToS8cI)
- [AWS re:Invent 2022 - A day in the life of a billion requests (SEC404)](https://www.youtube.com/watch?v=tPr1AgGkvc4)

## Extras

- IAM Roles Anywhere




