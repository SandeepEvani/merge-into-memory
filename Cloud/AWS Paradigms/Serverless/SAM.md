[[AWS Serverless]]

> [!Definition] 
> AWS SAM stands for the Serverless Application Model is an open-source framework for building serverless applications using Infrastructure as Code (IaC)

SAM is an open-source framework for building serverless applications. It provides shorthand syntax to express functions, APIs, databases, and event source mappings. With just a few lines per resource, you can define the application you want and model it using YAML.

we provide SAM with simplified instructions for your environment and during deployment SAM transforms and expands the SAM syntax into AWS CloudFormation syntax (a fully detailed CloudFormation template). All CloudFormation options are still available within SAM. SAM just makes it easier to set up the resources commonly needed for serverless applications.

SAM also offers CLI which can be used to validate, build, test and deploy the serverless application, and can also be integrated with the CICD pipeline

SAM is an abstraction built on [[CloudFormation]] which involves the two main components : 
- SAM templates
- SAM CLI

### SAM Templates

SAM provides us 7 specific resource types to transform from a SAM template to a CloudFormation Template, they are :

- AWS::Serverless::Function :: Create a Lambda Function
- AWS::Serverless::Api
- AWS::Serverless::HttpApi
- AWS::Serverless::SimpleTable
- AWS::Serverless::LayerVersion
- AWS::Serverless::Application
- AWS::Serverless::StateMachine











