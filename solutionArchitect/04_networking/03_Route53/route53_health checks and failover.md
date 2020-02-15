
**Section: Working with Private Hosted Zones**
In a private hosted zone, you can associate **Route 53 health checks only with failover, multivalue answer, and weighted records**. To use private hosted zones, you must set enableDnsHostnames and enableDnsSupport. You can use the Amazon Route 53 console to disassociate Amazon VPCs from a private hosted zone. 

**Section: Creating Amazon Route 53 Health Checks and Configuring DNS Failover**
Use an **active-passive failover configuration** when you want a primary resource or group of resources to be available the majority of the time and you want a secondary resource or group of resources to be on standby in case all the primary resources become unavailable. When responding to queries, Route 53 includes only the healthy primary resources. If all the primary resources are unhealthy, Route 53 begins to include only the healthy secondary resources in response to DNS queries. Having an S3 static website on standby for an EC2 instance is an example of Active-passive failover.

Route 53 doesn't prevent you from deleting a health check even if the health check is associated with one or more records. If you delete a health check and you don't update the associated records, the future status of the health check can't be predicted and might change. This will affect the routing of DNS queries for your DNS failover configuration.

Route 53 health checks integrate with CloudWatch metrics so that you can do the following: 
1. Verify that a health check is properly configured.
2. Review the status of a health check over a specified period of time.
3. Configure CloudWatch to send an Amazon SNS alert when the status of a health check is unhealthy. 

**Note**
that several minutes might elapse between the time that a health check fails and the time that you receive the associated SNS notification.
CloudWatch metrics are retained for two weeks.









