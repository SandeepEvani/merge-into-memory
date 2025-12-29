[[Networking and Content Delivery]]

- _Amazon Virtual Private Cloud_ (VPC) is a service that lets you launch AWS resources in a logically isolated virtual network that you define.

- VPC creates a datacenter for an individual in the vast AWS public cloud offering  security, reliability and isolation.

- A region resilient service, which allows a restricted access to the resource within it where nothing goes in and out without explicit configuration

- Offers a similar networking model to that of home networks unlocking limitless potential for hybrid networking 


## How VPC works?


In Context with the EC2 machines, let's assume a huge server rack with multiple servers (indicated with IPs 192.168.xxx.xxx) running a suitable hypervisor, responsible for launching EC2s and below is a image for our imagination.

In the Image above, we see AWS servers running EC2 machines with a different IP prefixes (10.0.0.xxx), these EC2s are color coded as per the VPCs they belong to, i.e., the blue ones belong to a VPC, the green on to another and the grey one to another. So if the EC2 of the blue VPC on the left (10.0.0.2) wants to communicate with EC2 of the same VPC on the right (10.0.0.4), The traffic flowing from the first EC2 machine is included with a VPC header and there is a mapping service that essentially locates the destination server (192.168.1.3) which consists of the second EC2, while the packets reach the second server, the VPC header is verified and later stripped and then sent to the VM.

This is a brief description of how the VPC isolation works, for more detailed information [refer](https://www.youtube.com/watch?v=3qln2u1Vr2E&pp=ygUkYW5vdGhlciBkYXkgYW5vdGhlciBiaWxsaW9uIHBhY2tlcnRz)

We can also assume similar would be the communication with any of the services which use an network interface. 

## Creating a VPC

While creating a VPC, there are few considerations we need to plan before we create a VPC, they are:
- The IP version
- The Size of VPC
- The CIDR block

While the order may juggle based on other factors, we'll try to understand how each component is necessary ::
### - IP Version
- There are two IP versions we can use for a VPC, the IPv4 and IPv6, or the combination of both the versions, also known as the dual stack VPC.
- There is a shortage of IPv4 network addresses, which leads to an increasing cost factor per public IP procured, as well as other features like the NAT gateway, but IPv4 is used almost everywhere, so depending upon the feasibility of the external communication version choose the IP version
### - Size of VPC
- The next important component is the size of the VPC required, Size here is the number of IPs a VPC contains, which is proportional to the number of resources that could be launched in a VPC.
- Based upon your approximate requirement of resources, you can plan your VPC.
- This particular planning is not required if your choosing an IPv6 version, as there are too many IPs available for usage.
### - CIDR Block
- CIDR block is the block of IPs your resources are assigned with.


There are a few other factors we'll require before the creation of the VPC like, 
The desired AWS Region:
	Since VPC is a regional service, it only spans across an AWS region and is resilient to any Availability zone level failures.

## Components of VPC

### Subnets

Subnets are sub-network of the VPC CIDR, a part of the VPC Network having different routes based on the intended use case, The Scope of the Subnet is restricted only to an availability zone. Hence they are not resilient towards AZ level failures.

To launch any resources in a VPC, we need to create subnet(s) and point the subnets for launching the Subnets.

Similar to how we decide a CIDR range for VPCs we should also decide the CIDRs for the subnet.

> [!note]
> In every subnet, there are 5 IPs that are reserved and cannot be allocated to the resources (*assuming the subnet's CIDR to be 10.0.0.0/24*), they are the network address (10.0.0.0), the router's IP (10.0.0.1), the resolver service IP (10.0.0.2), the amazon reserved IP (10.0.0.3) for future purposes and the last IP of the subnet for the broadcast (10.0.0.255) which is not currently used in the AWS.

### Route Tables

Route tables contains the information of how the router should route the packets to various destinations, A route table's records essentially have the prefix, and the destination data for every record, based on the destination in the packets, the longest prefix match is determined and the packets are forwarded to the designated destination.

> [!Note]
> Each route table contains a default, un-removable route to the local of the VPC marked with the prefix of the VPC's CIDR.

Each subnet is associated to one route table, which implies that the communication across subnets could be different based upon the route tables and the routes attached to it. This brings the flexibility to use appropriate subnets for the appropriate use case and build a secure network topology.

### Firewalls in VPC

We have two kinds of firewalls available VPC namely,

1. [[Virtual Private Cloud#Network Access Control Lists|Network Access Control Lists]] (NACLs)
2. [[Virtual Private Cloud#Security Groups|Security Groups]]

#### Network Access Control Lists

NACLS are stateless firewalls acting on the [[Virtual Private Cloud#Subnets|Subnet(s)]], which means all the rules present in the NACL are applicable to the all the instances in the subnet to which the specific NACL is applied to.

NACLS allow us to impose rules on the packets source IP, Destination IP, source port and the destination port. while configuring the network ACL one should explicitly mention the ALLOW or DENY and the rules are also evaluated in a order till any of the ALLOW or DENY is met.

#### Security Groups

Security Groups are stateful firewalls acting om the interface, which means that different instances can have different security groups attached to it.

Security groups similar to NACLS impose rules on the same pairs and also include an additional parameter, the Protocol of the communication.

## Attachments to VPC

### NAT Gateway



