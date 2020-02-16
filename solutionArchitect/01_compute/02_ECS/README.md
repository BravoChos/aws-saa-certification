# Elastic Container Service
**ECS** or Amazon Elastic container service: is a highly scalable high-performance container management service for docker containers the containers. They will run on a managed cluster of ec2 instances 

Amazon EC2 provides the following features: 
- Instances & Instance types & Tags
- Amazon Machine Images (AMIs)
- Secure login information for your instances using key pairs
- Instance store & EBS volumes
- Hosting in Regions & Availability Zones
- Security groups
- Elastic IP addresses

## Amazon Machine Images

From an **AMI**, you launch an instance, which is a copy of the **AMI** running as a virtual server in the cloud. When you launch an instance, you must select an AMI that's in the same region. AMI are region specific but can be copied to another region.

To migrate an instance to another availability zone you must create an AMI from the original instance, launch an instance in the new Availability Zone, and update the configuration of the new instance. 

## Best Practices for Amazon EC2

It is best practice to use the instance store available for your instance to store temporary data. Use the instance store available for your instance to store temporary data. Remember that the data stored in instance store is deleted when you stop or terminate your instance. If you use instance store for database storage, ensure that you have a cluster with a replication factor that ensures fault tolerance.

It is best practice to use instance metadata and custom resource tags to track and identify your AWS resources. Use instance metadata and custom resource tags to track and identify your AWS resources.