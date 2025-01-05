[[Compute]]

EC2 :: Elastic Cloud Compute is a service in AWS that helps you launch virtual machines with desired OS. 
It's basically Infrastructure as a service (IaaS).

You can launch VMs of different sizes and use it for different use cases, running a website, using it as a bastion host etc.,

While running a EC2 instance, you can use the AWS CLI to access other resources with Access Key pair or a Role attached to EC2 instance.

EC2 user data script can also be used to run a script before the start of the instance with root privileges.

## Auto Scaling Groups
- Auto scaling groups allow the instances to be auto scaled based on an Cloud Watch metric usually CPU load to spin new instance/Instances based upon the load.
- There could be different types of Auto scaling policy attached to the Autoscaling group.
- We need to create a launch template before we actually create a autoscaling group.
- The launch is actually used to determine what kind of instance should be spun when needed.

## Load balancers
- There are many kind of load balancers, as their name suggest, these are used to balance the load between multiple instances.
- Before we create the load balancers, we need to create a target group. Target group is a logical group where the load balancer searches and locates instances to route requests to.
- There are SG configurations between load balancers and EC2 instances.

While we create Target groups, we must also edit the Autoscaling to launch new resources in this target group if autoscaling is enabled.


