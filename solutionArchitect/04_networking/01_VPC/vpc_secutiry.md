**VPC Security**

Security groups
- Firewall at the instance level
- Statefull

Network access control lists (ACLs)
- Firewall at the subnet level
- Network ACLs as a second layer of defense
- Stateless

Flow logs
- Capture inforamtion about the IP traffic going to and from network interfaces in you VPC.
- Flow log data is stored using Amazon CloudWatch logs

Security groups in a VPC specify which traffic is allowed to or from an Amazon EC2 instance. Network ACLs operate at the subnet level and evaluate traffic entering and exiting a subnet. Network ACLs can be used to set both Allow and Deny rules. Network ACLs do not filter traffic between instances in the same subnet. In addition, network ACLs perform stateless filtering while security groups perform stateful filtering.

**Section: Security**

You can secure your VPC instances using only security groups; however, you can add network ACLs as a second layer of defense. A security group acts as a virtual firewall for your instance to control inbound and outbound traffic. When you launch an instance in a VPC, you can assign up to five security groups to the instance. Security groups act at the **instance** level, not the subnet level. Therefore, each instance in a subnet in your VPC could be assigned to a different set of security groups. If you don't specify a particular group at launch time, the instance is automatically assigned to the default security group for the VPC.

Network ACL operate at the **Subnet** level. A network access control list (ACL) is an optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets. You might set up network ACLs with rules similar to your security groups in order to add an additional layer of security to your VPC.

Network ACL **Is stateless: Return traffic must be explicitly allowed by rules** and responses to allowed inbound traffic are subject to the rules for outbound traffic (and vice versa).

Security Group **can specify allow rules, but not deny rules**. Security Group applies to an instance **only if someone specifies** the security group when launching the instance, or associates the security group with the instance later on. A security group acts as a virtual firewall for your instance to control inbound and outbound traffic. By default, a security group includes an outbound rule that allows all outbound traffic. You can remove the rule and add outbound rules that allow specific outbound traffic only. If your security group has no outbound rules, no outbound traffic originating from your instance is allowed. 

Security groups **are stateful** — if you send a request from your instance, the response traffic for that request is allowed to flow in regardless of inbound security group rules. **Responses to inbound traffic allowed by security group rules are allowed to flow outbound regardless of outbound rules**

When you specify a security group as the source for a rule, this allows instances associated with the source security group to access instances in the security group. This does not add rules from the source security group to this security group. Incoming traffic is allowed based on the private IP addresses of the instances that are associated with the source security group (and not the public IP or Elastic IP addresses). With EC-2 Classic you can reference security groups from other AWS accounts. 


Each subnet in your VPC must be associated with a network ACL. If you don't explicitly associate a subnet with a network ACL, the subnet is automatically associated with the default network ACL. 
You can add or remove rules from the default network ACL, or create additional network ACLs for your VPC. When you add or remove rules from a network ACL, the changes are automatically applied to the subnets it's associated with.
The default network ACL is configured to allow all traffic to flow in and out of the subnets to which it is associated. Each network ACL also includes a rule whose rule number is an **asterisk**. **This rule ensures that if a packet doesn't match any of the other numbered rules, it's denied. You can't modify or remove this rule**.

If you use a elastric load balancer in the same VPC as your backend instances, and your subnet has a network ACL with an inbound DENY rule for all traffic with a source of 0.0.0.0/0, then your load balancer cannot carry out health checks on instances in your subnet. 



