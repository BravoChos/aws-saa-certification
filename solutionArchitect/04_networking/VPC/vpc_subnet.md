**Section: VPCs and Subnets**

AWS reserves both the first four IP addresses and the last IP address in each subnet CIDR block. They're not available for you to use.

If your VPC is too small to meet your needs, you must terminate all the instances in the VPC, delete the VPC, and then create a new, larger VPC or You can associate a **secondary IPv4 CIDR block in order to increase the VPC size**. However, you **cannot change the CIDR block size** using the AWS console, CLI or API tools.

You can optionally set up a connection between your VPC and your corporate or home network. If you have an IPv4 address prefix in your VPC that overlaps with one of your networks' prefixes, any traffic to the network's prefix is dropped. We therefore recommend that you create a VPC with a CIDR range large enough for expected future growth, but not one that overlaps with current or expected future subnets anywhere in your corporate or home network, or that overlaps with current or future VPCs.

If a subnet doesn't have a route to the Internet gateway, but has its traffic routed to a **virtual private gateway**, the subnet is known as a **VPN-only subnet**.

When we create a **default VPC**, aws... :
A. Create a VPC with a size /16 IPv4 CIDR block (**172.31.0.0/16**). This provides up to **65,536 private IPv4 addresses**.
B. Create a size **/20 default subnet** in each Availability Zone. This provides up to **4,096 addresses per subnet**, a few of which are reserved for our use.
C. Create an internet gateway and connect it to your default VPC.
D. Create a main route table for your default VPC with a rule that sends all IPv4 traffic destined for the internet to the internet gateway.
E. Create a default security group and associate it with your default VPC.
F. Create a default network access control list (ACL) and associate it with your default VPC.
G. Associate the default DHCP options set for your AWS account with your default VPC.

