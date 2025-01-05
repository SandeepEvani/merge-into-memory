[[Networking and Content Delivery]]
## AWS Site to Site VPN

AWS Site to site VPN also referred as S2S VPN offers the quickest way to enable private connectivity over internet between on-premises, datacenters or other clouds to an AWS network like AWS VPCs

- The VPN uses the IPSec protocol, which offers end to end encryption

We have some necessary components to configure an S2S VPN

- The VPC
- Virtual Private Gateway - used to connect Non AWS networks to AWS
- Customer gateway - A representation of customer router in the AWS Environment

We can have two types of configurations for the VPN, the static VPN and the dynamic VPN

The static VPN:
- In the static VPN, the routes are manually defined into the VPC route tables and we don't support the Route propagation in the Virtual Gateway.
- Easy for the initial setup.

The Dynamic VPN:
- In the Dynamic VPN, we allow the BGP to dynamically propagate routes between the VGW and the customer router.
- This setup unlocks many more features and can be collaborated with the Direct connect if present

## How VPN works

- The Virtual Private Gateway will have two Endpoints associated to it in two different availability zones in the AWS Public Zone.

- Each Endpoint connects with the CGW to form an IPSec tunnel.

- Communication is enabled between the VGW and the router with the help of tunnels

## VPN NAT Traversal

- Occurs on UDP port 4500 if the CGW is behind a NAT

## VPN Tunnels.

We can configure VPN tunnels in Active/Active mode and Active/Passive mode and the kind of VPN (Static or Dynamic)

When configured in static mode, we don't have the BGP session created between the routers and hence a couple of BGP routing options would not be available.

When the tunnel is configured in Active/Passive mode the routing between the VGW and CGW happens on the Active tunnel

- *Static routing + Active/Active configuration*: There could be a scenario where asymmetric routing might occur, the customer gateway side of the routing should be able to handle asymmetric routing.
- *Static routing + Active/Passive configuration*: Since only one tunnel is up at any given time, the communication is only done through one, while the traffic is originating from the customer gateway device and if the active tunnel fails, it's the responsibility of the customer gateway device to failover to the other tunnel and on the Virtual Gateway, AWS automatically performs this
- *Dynamic routing + Active/Active configuration:* using BGP parameters, we can choose specific tunnels when traffic is destined to specific CIDR range on the on prem.
	- Influence the tunnel selection also by using the ASPATH parameter
	- If ASPATH are also same, then you can use MED (Multi exit discriminator) to influence the tunnel selection, the one with the lowest MED is selected

## VPN Dead Peer Detection

Dead peer detection identifies the liveliness of the CGW and helps to switch to the other tunnel.

- The VGW will send acknowledgement message to the CGW and waits for a response, when there is no response for 3 consecutive times, the tunnel is taken down.
- DPD uses UDP 500 for the communication and UDP 4500 for NAT-Traversal communication


## S2S VPN with [[Transit Gateway]]

VPN Connections can be terminated on a virtual private gateway or an Transit gateway, Transit gateway provides more flexibility when it comes to attaching multiple VPC's to the VPN connections


## AWS VPN Cloud Hub

With the help of S2S VPN, we can connect different corporate datacenters to communicate with each other

With BGP enabled, all the connections will terminate on one VPN gateway


