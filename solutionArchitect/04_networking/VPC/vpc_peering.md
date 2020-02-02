
**Section: VPC Peering**
A VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them privately. Instances in either VPC can communicate with each other as if they are within the same network. You can create a VPC peering connection between your own VPCs, with a VPC in another AWS account, or with a VPC in a different AWS Region.

**To create a VPC peering connection**, first create a request to peer with another VPC. You can request a VPC peering connection with another VPC in your account, or with a VPC in a different AWS account. For an inter-region VPC peering connection where the VPCs are in different regions, the request must be made from the region of the requester VPC.
**To activate the request**, the owner of the accepter VPC must accept the request. For an inter-region VPC peering connection, the request must be accepted in the region of the accepter VPC.

Do not accept VPC peering connections from unknown AWS accounts. A malicious user may have sent you a VPC peering connection request to gain unauthorized network access to your VPC. This is known as **peer phishing**. You can safely reject unwanted VPC peering connection requests without any risk of the requester gaining access to any information about your AWS account or your VPC. You can also ignore the request and let it expire; by default, requests expire after 7 days.

You cannot create a VPC peering connection between VPCs with matching or overlapping IPv4 CIDR blocks. This limitation also applies to VPCs that have non-overlapping IPv6 CIDR blocks.

