[[Compute]]

> [!Definition]
> AWS Lambda is a compute service. You can use it to run code without provisioning or managing servers.


The code you run on AWS Lambda is called a _Lambda function_. Each function includes your code as well as some associated configuration information, including the function name and resource requirements. 

Lambda functions are _stateless_, with no affinity to the underlying infrastructure. Lambda can rapidly launch as many copies of the function as needed to scale to the rate of incoming events.

### Features of Lambda

- **Environment Variables** : We can use environment variables to adjust the functions behavior without modifying the code, environment variables cannot be used as parameters while using a Lambda Function i.e. we cannot use update environment variables for a specific invocation rather we would need to update the function and use the environment variables
- **Versions and Aliases** : We can publish a version of a Lambda function and the published version is immutable, ideal for deploying functions in production environments, Aliases are pointers to Lambda versions, we can use aliases to point to a specific version or two versions with a weighted distribution policy very useful for Canary and Linear deployments
- **Container Images** : Create a container image for a Lambda function by using an AWS provided base image or an alternative base image so that you can reuse your existing container tooling or deploy larger workloads that rely on sizable dependencies, such as machine learning.
- **Layers** : Package libraries and other dependencies to reduce the size of deployment archives and makes it faster to deploy your code.
- **Lambda extensions**: Augment your Lambda functions with tools for monitoring, observability, security, and governance.
- **Function URLs** : Add a dedicated HTTP(S) endpoint to your Lambda function.
- **Response streaming** : Configure your Lambda function URLs to stream response payloads back to clients to improve time to first byte (TTFB) performance or to return larger payloads.
- **Concurrency and scaling controls** : Apply fine-grained control over the scaling and responsiveness of your production applications.
- **File system access** : Configure a function to mount an Amazon Elastic File System (Amazon EFS) to a local directory, so that your function code can access and modify shared resources safely and at high concurrency.














## How AWS Lambda Works

As we have already seen about Lambda, we understand that Lambda runs a piece of defined code, without us provisioning and maintaining the backend instances and the runtimes. *What actually makes lambda a key serverless service is the integration with multiple other AWS services facilitating the Event Driven Architectures.*

>[!Note]
>In this section, we'll closely be looking about how lambda can be invoked differently by different services and then the execution environment of the lambda

### Invocation models for running Lambda functions

Event sources can invoke a Lambda function in three general patterns. These patterns are called invocation models.

- **Synchronous invocation** : When you invoke a function synchronously, Lambda runs the function and waits for a response. When the function completes, Lambda returns the response from the function's code with additional data, such as the version of the function that was invoked. Synchronous events expect an immediate response from the function invocation.

- **Asynchronous invocation** : When you invoke a function asynchronously, events are queued and the requestor doesn't wait for the function to complete. This model is appropriate when the client doesn't need an immediate response. With the asynchronous model, you can make use of destinations. Use destinations to send records of asynchronous invocations to other services.

- **Polling invocation** : This invocation model is designed to integrate with AWS streaming and queuing based services with no code or server management. Lambda will poll these services, retrieve any matching events, and invoke your functions.


### Lambda execution environment  

- **Init Phase** : Lambda creates or unfreezes an execution environment with the configured resources, downloads the code for the function and all layers, initializes any extensions, initializes the runtime, and then runs the function’s initialization code (the code outside the main handler).
- **Invoke Phase** : Lambda invokes the function handler. After the function runs to completion, Lambda prepares to handle another function invocation.
- **Shutdown phase** : If the Lambda function does not receive any invocations for a period of time, this phase initiates. In the Shutdown phase, Lambda shuts down the runtime, alerts the extensions to let them stop cleanly, and then removes the environment

### Lambda with IAM

- Lambda functions takes resource based policies for other AWS Services/AWS Accounts to invoke the function.
- Lambda functions also allows an Execution Role for the function to access other AWS Services, the Role must have _AssumeRole_ action with the principle being Lambda, and the user must have the pass role permissions to pass a role to Lambda 
- For your Lambda Function to launch and access resources within a VPC, like the subnets, security groups and elastic network interfaces, for this we can use a managed role _AWSLambdaVPCAccessExecutionRole_

### Lambda programming model

#### The Lambda Handler

The Lambda function handler is the method in your function code that processes events. When your function is invoked, Lambda runs the handler method. When the handler exits or returns a response, it becomes available to handle another event. The handler method takes two objects – the event object and the context object.

- **Event** : The contents of the event parameter include all of the data and metadata your Lambda function needs to drive its logic. Basically this relates to the all-round data which caused the lambda to trigger 
- **Context** : The context object allows your function code to interact with the Lambda execution environment. This basically is the function gets the metadata of itself, like the runtime, request Id, resources provisioned etc..

### Configuring Your Lambda Functions

#### Memory
You can allocate up to 10 GB of memory to a Lambda function. Lambda allocates CPU and other resources linearly in proportion to the amount of memory configured.

#### Timeout
The AWS Lambda timeout value dictates how long a function can run before Lambda terminates the Lambda function.

**The balance between power and duration**

Depending on the function, you might find that the higher memory level might actually cost less because the function can complete much more quickly than at a lower memory configuration.

-  You can use an open-source tool called Lambda Power Tuning to find the best configuration for a function.

#### Concurrency

Concurrency is the number of invocations your function runs at any given moment. When your function is invoked, Lambda launches an instance of the function to process the event. When the function code finishes running, it can handle another request. If the function is invoked again while the first request is still being processed, another instance is allocated.

**Concurrency types**

- Unreserved concurrency : The amount of concurrency that is not allocated to any specific set of functions. (100)
- Reserved concurrency : Guarantees the maximum number of concurrent instances for the function. no other function can use that concurrency. No charge is incurred for configuring reserved concurrency for a function.
- provisioned concurrency : Initializes a requested number of runtime environments so that they are prepared to respond immediately to your function's invocations. This option is used when you need high performance and low latency.


