# Extra

## VPC Peering:
	- A connection between two VPCs that enables you to route traffic between the using private IP addresses. Instances in either VPC can communicate with each other as if they are within the same network. You can create a VPC peering connection between your own VPCs, or with a VPC in another AWS account within a single region.
	- AWS uses the existing infra of a VPC to create a VPC peering connection; it is neither a gateway nor a VPN connection, and does not rely on a separate piece of physical hardware. There is no single point of failure for communication or a bandwidth bottleneck.
	- Cannot have overlapping CIDR blocks
	- No transitive Peering. A cannot connect to C.
	- Cannot create peering across different regions

## Direct Connect:
	- Makes it easy to establish a dedicated network connection from your premises to AWS. Using Direct connect, you can establish private connectivity between AWS and your DC, office, or colocation env, which in many cases can reduce your network costs, increase bandwidth throughput, and provide a more consistent network xp than internet-based connections.
	- VPN connections can be configured in minutes and are a good solution if you have an immediate need, have low to modest bandwidth requirements, and can tolerate the inherent variability in Internet-based connectivity.
	- AWS Direct Connect does not involve the internet; instead it uses dedicated, private network connections between your intranet and Amazon VPC.

