## Changing the Launch Configuration for an Auto Scaling group
An Auto Scaling group is associated with one launch configuration at a time, and you can't modify a launch configuration after you've created it. To change the launch configuration for an Auto Scaling group, you can use an existing launch configuration as the basis for a new launch configuration and then update the Auto Scaling group to use the new launch configuration.

## Auto Scaling Group Policy
**Simple and Step Policy**  
Default metric types available for Simple Policy and Step policy
- Average CPU utilization
- Average Network In (Bytes)
- Average Network Out (Bytes)

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

## Health Check Grace Periodically
Frequently, an Auto Scaling instance that has just come into service needs to warm up before it can pass the health check. Amazon EC2 Auto Scaling waits until the health check grace period ends before checking the health status of the instance. **While the EC2 status checks and ELB health checks can complete before the health check grace period expires, Amazon EC2 Auto Scaling does not act on them until the health check grace period expires.** 