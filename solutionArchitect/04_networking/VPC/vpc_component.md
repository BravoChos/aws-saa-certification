

Section: VPC Networking Components

Every **subnet**: that you create is automatically associated with the main route table for the VPC. Each subnet must be associated with a route table, which controls the routing for the subnet. If you don't explicitly associate a subnet with a particular route table, the subnet is implicitly associated with the main route table. AWS provides the network ACLs and security groups that you can use to increase security in your VPC.

**Private IP addresses**: are the IP addresses that are within the CIDR range of the VPC. You can assign additional private IP addresses, known as **secondary private IP addresses**, to instances that are running in a VPC. Unlike a primary private IP address, you **can reassign a secondary private IP address** from one network interface to another. A private IP address remains associated with the network interface when the instance is stopped and restarted, and is released when the instance is terminated.

You cannot manually associate or disassociate a public IP address from your instance. Instead, in certain cases, we release the public IP address from your instance, or assign it a new one:

• We release the public IP address for your instance when it's stopped or terminated. Your stopped instance receives a new public IP address when it's restarted.

• We release the public IP address for your instance when you associate an Elastic IP address with your instance, or when you associate an Elastic IP address with the primary network interface (eth0) of your instance in a VPC. When you disassociate the Elastic IP address from your instance, it receives a new public IP address.

• If the public IP address of your instance in a VPC has been released, it will not receive a new one if there is more than one network interface attached to your instance.

All subnets have an attribute that determines whether a network interface created in the subnet automatically receives a public IPv4 address (also referred to as a public IP address in this topic). Therefore, when you launch an instance into a subnet that has this attribute enabled, a public IP address is assigned to the primary network interface (eth0) that's created for the instance. A public IP address is mapped to the primary private IP address through network address translation (NAT).

Whether or not you assign a public IPv4 address to your instance during launch, you can associate an **Elastic IP address** with your instance after it's launched. The advantage of associating the Elastic IP address with the network interface instead of directly with the instance is that you can move all the attributes of the network interface from one instance to another in a single step. 

A network interface's attributes follow it as it is attached or detached from an instance and reattached to another instance. When you move a network interface from one instance to another, network traffic is redirected to the new instance.

To apply route table routes to a particular subnet, you must associate the route table with the subnet. When you add a new subnet, it automatically uses the routes specified in the main route table and **a route table can be associated with multiple subnets; however, a subnet can only be associated with one route table at a time**. Any subnet not explicitly associated with a table is implicitly associated with the main route table by default.

**ClassicLink** allows you to link your EC2-Classic instance to a VPC in your account, within the same region. This allows you to associate the VPC security groups with the EC2-Classic instance, enabling communication between your EC2-Classic instance and instances in your VPC using private IPv4 addresses. ClassicLink removes the need to make use of public IPv4 addresses or Elastic IP addresses to enable communication between instances in these platforms.

To enable access to or from the Internet for instances in a VPC subnet, you must:

1. attach an Internet gateway to your VPC
2. ensure that your subnet's route table points to the Internet gateway
3. ensure that instances in your subnet have public IP addresses or Elastic IP addresses
4. ensure that your network access control and security group rules allow the relevant traffic to flow to and from your instance.

**Dynamic Host Configuration Protocol** (DHCP) provides a standard for passing configuration information to hosts on a TCP/IP network.
The options field of a DHCP message contains the configuration parameters. Some of those parameters are the domain name, domain name server, and the netbios-node-type. DHCP options sets are associated with your AWS account so that you can use them across all of your virtual private clouds (VPC). After you create a set of DHCP options, you can't modify them. If you want your VPC to use a different set of DHCP options, you must create a new set and associate them with your VPC. You can also set up your VPC to use no DHCP options at all.

The Amazon EC2 instances you launch into a nondefault VPC are private by default; they're not assigned a public IPv4 address unless you specifically assign one during launch, or you modify the subnet's public IPv4 address attribute. By default, all instances in a nondefault VPC receive an **unresolvable host name** that AWS assigns (for example, ip-10-0-0-202). You can assign your own domain name to your instances, and use up to four of your own DNS servers. To do that, you must specify a special set of DHCP options to use with the VPC.

You can assign your own domain name to your instances, and use up to **four** of your own DNS servers.
