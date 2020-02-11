Section: What Is Amazon VPC?

A **SUBNET** is a range of IP addresses in your VPC.
You can launch AWS resources into a specified subnet. Use a public subnet for resources that must be connected to the internet, and a private subnet for resources that won't be connected to the internet.

If you have a default VPC and don't specify a subnet when you launch an instance, **the instance is launched** into your default VPC.

A **internet gateway** enables your instances to connect to the Internet through the Amazon EC2 network edge. Your default VPC includes a **internet gateway**, and each default subnet is a public subnet. Each instance that you launch into a default subnet has a private IPv4 address and a public IPv4 address. These instances can communicate with the internet through the internet gateway. An internet gateway enables your instances to connect to the internet through the Amazon EC2 network edge.

You can enable Internet access for an instance launched into a nondefault subnet by attaching an Internet gateway to its VPC (if its VPC is not a default VPC) and associating a **Elastic IP address** with the instance.

To allow an instance in your VPC to initiate outbound connections to the Internet but prevent unsolicited inbound connections from the Internet, you can use a **NAT**. NAT maps multiple private IPv4 addresses to a single public IPv4 address. A NAT device has an Elastic IP address and is connected to the internet through an internet gateway. You can connect an instance in a private subnet to the internet through the NAT device, which routes traffic from the instance to the internet gateway, and routes any responses to the instance.
=> NAT instance and NAT Gateway are used when private resources are required to access the Internet.
=> VPN is used to create connection between the On-premises and AWS resources.
=> VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them privately.

**Primary private IP addresses** retained for the instance's or interface's lifetime. **Secondary private IP addresses** can be assigned, unassigned, or moved between interfaces or instances at any time.

**#Connecting to a VPC**
A **virtual private gateway** is the VPN concentrator on the Amazon side of the VPN connection. A VPN connection consists of a virtual private gateway attached to your VPC and a customer gateway located in your data center. A virtual private gateway is the VPN concentrator on the Amazon side of the VPN connection. A customer gateway is a physical device or software appliance on your side of the VPN connection.

Customer gateway is a physical device or software applicaion on you side of the VPN connection
Other options including AWS Direct Connect

#Main Requirement for Internet Connectivity

1) EC2 instance has a **Public IP address**.
2) VPC has an **Internet Gateway**.
3) **Route** defined in a route table from **subnet to IGW**.

**Pricing**
There are no additional charges for creating and using the VPC itself. Usage charges for other Amazon Web Services, including Amazon EC2, still apply at published rates for those resources, including data transfer charges. If you connect your VPC to your corporate datacenter using the optional hardware **VPN connection**, pricing is per VPN connection-hour (the amount of time you have a VPN connection in the "available" state.) Partial hours are billed as full hours. Data transferred over VPN connections will be charged at standard AWS Data Transfer rates.

