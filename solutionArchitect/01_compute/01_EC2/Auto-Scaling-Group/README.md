# Auto-Scaling Group 
An Auto Scaling Group contains a collection of EC2 instances that share similar characteristics and are treated as a logical grouping for the purpose of instance scaling and management. There are no additional fees with Auto Scaling.

AutoScaling is accessed using:
• AWS Command Line Interface (CLI)
• AutoScaling Command Line Interface (CLI) Tools
• AWS Tools for Windows PowerShell
• Launch Configurations from Console

The AutoScaling system can temporarily exceed the specified maximum capacity of a group by a 10 percent margin during a rebalancing activity. Because Auto Scaling attempts to launch new instances before terminating the old ones, being at or near the specified maximum capacity could impede or completely halt rebalancing activities. 

To avoid this problem, the system can temporarily exceed the specified maximum capacity of a group by a 10 percent margin during a rebalancing activity. The margin is extended only if the group is at or near maximum capacity and needs rebalancing, either because of user-requested rezoning or to compensate for zone availability issues. The extension lasts only as long as needed to rebalance the group typically 
a few minutes.

## Launch Configurations
A launch configuration is a template that an Auto Scaling group uses to launch EC2 instances. When you create a launch configuration, you specify information for the instances such as the ID of the Amazon Machine Image(AMI), the instance type, a key pair, one or more security groups, and a block device mapping. 

Keep in mind that whenever you creat an Auto Scaling group, you must specify a launch template, or and EC2 instance. When you create an Auto Scaling group using an EC2 instance, Amazon EC2 Auto Scaling automatically creates a launch configuration for you and associates it with the Auto Scaling group.

Note: Effective Setup for Auto Scaling on your EC2 inscances for a web-based application?  
Ans: ELB + Auto Scaling Group (feat. Launch Configuration)

## Changing the Launch Configuration for an Auto Scaling group
An Auto Scaling group is associated with one launch configuration at a time, and you can't modify a launch configuration after you've created it. To change the launch configuration for an Auto Scaling group, you can use an existing launch configuration as the basis for a new launch configuration and then update the Auto Scaling group to use the new launch configuration.

However, at any time, you can change the size of an existing Auto Scaling group. Update the desired capacity of the Auto Scaling group, or update the instances that are attached to the Auto Scaling group.

## Instance Health Status
By default, Amazon EC2 Auto Scaling health checks use the results of the EC2 status checks to determine the health of an instance. Amazon EC2 Auto Scaling marks an instance as unhealthy if its instance fails one or more of the status checks. Amazon EC2 Auto Scaling determines the health status of an instance using one or more of the following:

- Status checks provided by Amazon EC2
- Health checks provided by ELB
- Custom health checks

After a scaling activity is started, the policy must wait for the scaling activity or health check replacement to complete and the cooldown period to expire before it can respond to additional alarms. Cooldown periods help to prevent the initiation of additional scaling activities before the effects of previous activities are visible. You can use the default cooldown period associated with your Auto Scaling group, or you can override the default by specifying a cooldown period for your policy.


## Health Check Grace Periodically
Frequently, an Auto Scaling instance that has just come into service needs to warm up before it can pass the health check. Amazon EC2 Auto Scaling waits until the health check grace period ends before checking the health status of the instance. **While the EC2 status checks and ELB health checks can complete before the health check grace period expires, Amazon EC2 Auto Scaling does not act on them until the health check grace period expires.** 


## Auto Scaling Group Policy
An AutoScaling policy defines min and max EC2 instances. An autoscaling group defines the desired  number of EC2 instances. An autoscaling group includes an autoscaling policy.

**Simple and Step Policy**  
- ChangeInCapacity—Increase or decrease the current capacity of the group by the specified number of instances. A positive value increases the capacity and a negative adjustment value decreases the capacity. 

- ExactCapacity—Change the current capacity of the group to the specified number of instances. 

- PercentChangeInCapacity—Increment or decrement the current capacity of the group by the specified percentage. A positive value increases the capacity and a negative value decreases the capacity. If the resulting value is not an integer, it is rounded as follows:
    - Values greater than 1 are rounded down. 
    - Values between 0 and 1 are rounded to 1.
    - Values between 0 and -1 are rounded to -1. 
    - Values less than -1 are rounded up.

Default metric types available for Simple Policy and Step policy
- Average CPU utilization
- Average Network In (Bytes)
- Average Network Out (Bytes)

## Lifecycle Hooks 
Adding **Lifecycle Hooks** to Auto Scaling group puts the instance into **wait state** befor termination. During this wait state, you can perform custom activites to retrieve critical operational data from a statefull instance. **Default Wait period is 1 hour**.

**Termination Policy** 
- Default: The default termination policy is designed to help ensure that your network architecture spans Availability Zones evenly. With the default termination policy, the behavior of the Auto Scaling group is as follows:    
    1. Determine which Availability Zones have the most instances, and at least one instance that is not protected from scale in.
    2. Determine which instances to terminate so as to align the remaining instances to the allocation strategy for the On-Demand or Spot Instance that is terminating. This only applies to an Auto Scaling group that specifies allocation strategies.
    3. Determine whether any of the instances use the oldest launch template or configuration.
    4. If there are multiple unprotected instances to terminate, determine which instances are closest to the next billing hour. 

- OldestInstance: Terminate the oldest instance in the group. This option is useful when you're upgrading the instances in the Auto Scaling group to a new EC2 instacne type

- NewestInstance: Terminate the newest instance in the group. This policy is useful when you're testing a new launch configuration but don't want to keep it in produciton

- OldestLaunchConfiguration: Terminate instances that have the oldest launch configuration. This policy is useful when you're updating a group and phasing out the instances from a previous configuration.

- ClosestToNextInstanceHour: Terminate instances that are closest to the next billing hour. This policy helps you maximize the use of your instances and manage your Amazon EC2 costs.

- default: Terminate instances according to the default termination policy. This policy is useful when you have more than one scaling policy for the group.

## Target Health Status
Before the load balancer sends a health check request to a target, you must register it with a target group, specify its target group in a listener rule, and ensure that the Availability Zone of the target is enabled for the load balancer.

Possible reason for showing an unhealthy status: 
- A security group does not allow traffic.
- A network access control list(ACL) does not allow traffic. 
- The ping path does not exist.
- The connection times out.
- The target did not return a successful response code. 

## Target Group Types
When you create a target group, you specify its target type, which determines how you specify its target. After you create a target group, you cannot change its target type. You can

The following are the possible target types:

- instances: The targets are specified by instance ID.
- ip: The targets are specified by IP address. (cannot be a public IP address)
