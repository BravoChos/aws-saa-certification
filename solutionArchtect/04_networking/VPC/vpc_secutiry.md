**VPC Security**

Security groups
- Firewall at the instance level
- Statefull

Network access control lists (ACLs)
- Firewall at the subnet level
- Network ACLs as a second layer of defense
- Stateless

Flow logs
- Capture inforamtion as CloudWatch logs

Security groups in a VPC specify which traffic is allowed to or from an Amazon EC2 instance. Network ACLs operate at the subnet level and evaluate traffic entering and exiting a subnet. Network ACLs can be used to set both Allow and Deny rules. Network ACLs do not filter traffic between instances in the same subnet. In addition, network ACLs perform stateless filtering while security groups perform stateful filtering.

