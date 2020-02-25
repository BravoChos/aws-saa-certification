# VPC
**VPC** or Amazon virtual private cloud for short lets you provision a logically isolated section of the AWS cloud and you can launch AWS resources in that virtual network that you yourself define and this is your own personal private space within the AWS cloud and no one can enter it unless you allow them to enter it.

## VPC Endpoints
A VPC endpoint enables you to privately connect your VPC to supported AWS services and VPC endpoint services powered by AWS **PrivateLink** without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Instances in your VPC do not require public IP addresses to communicate with resources in the service. Traffic between your VPC and the other service does not leave the Amazon network.

### 1. Interface Endpoint
**Interface Endpoint** (Powered by AWS PrivateLink): is an elastic network interface with a private IP address from the IP address range of your subnet that serves as an entry point for traffic destined to a supported service. The following services are supported:
- Amazon API Gateway
- Amazon EC2 Auto Scaling
- AWS CloudTrail
- AWS CloudWatch
- Amazon Kinesis
- Amazon SNS, SQS

### 2. Gateway Endpoint
**Gateway Endpoint** is a gateway that you specify as a target for a route in your route table for traffic destined to a supported AWS service. The following AWS services are supported:
- S3
- DynamoDB

### 3. Controlling the Use of VPC Endpoints
By default, IAM users do not have permission to work with endpoints. You can create an IAM user policy that grants users the permissions to create, modify, describe, and delete endpoints. 


## VPC Peering
A VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them privately. Instances in either VPC can communicate with each other as if they are within the same network. You can create a VPC peering connection between your own VPCs, with a VPC in another AWS account, or with a VPC in a different AWS Region.

**To create a VPC peering connection**, first create a request to peer with another VPC. You can request a VPC peering connection with another VPC in your account, or with a VPC in a different AWS account. For an inter-region VPC peering connection where the VPCs are in different regions, the request must be made from the region of the requester VPC.  

**To activate the request**, the owner of the accepter VPC must accept the request. For an inter-region VPC peering connection, the request must be accepted in the region of the accepter VPC.

Do not accept VPC peering connections from unknown AWS accounts. A malicious user may have sent you a VPC peering connection request to gain unauthorized network access to your VPC. This is known as **peer phishing**. You can safely reject unwanted VPC peering connection requests without any risk of the requester gaining access to any information about your AWS account or your VPC. You can also ignore the request and let it expire; by default, requests expire after 7 days.

You cannot create a VPC peering connection between VPCs with matching or **overlapping IPv4 CIDR blocks**. This limitation also applies to VPCs that have non-overlapping IPv6 CIDR blocks.

## VPN Connections
You can create an IPsec VPN connection between your VPC and your remote network. On the AWS side of the VPN connection, a virtual private gateway **provides two VPN endpoints** (tunnels) for automatic failover. You configure your customer gateway on the remote side of the VPN connection.

AWS recommends that you use **BGP-capable** VPN devices when available, because the BGP protocol offers **robust liveness detection checks** that can assist failover to the second VPN tunnel if the first tunnel goes down. Devices that don't support BGP may also perform health checks to assist failover to the second tunnel when needed.

A VPN connection has two tunnels to help ensure connectivity in case one of the VPN connections becomes unavailable. To protect against a loss of connectivity in case your customer gateway becomes unavailable, you can set up a second VPN connection to your VPC by using a second customer gateway.

# Pricing
There are no additional charges for creating and using the VPC itself. Usage charges for other Amazon Web Services, including Amazon EC2, still apply at published rates for those resources, including data transfer charges. If you connect your VPC to your corporate datacenter using the optional hardware **VPN connection**, pricing is per VPN connection-hour (the amount of time you have a VPN connection in the "available" state.) Partial hours are billed as full hours. Data transferred over VPN connections will be charged at standard AWS Data Transfer rates.

## Amazon VPC Limits
Default maximum VPCs per region are **5**.
Maximum subnets per VPC are **200**.
Maximum VPN connections per region **50**