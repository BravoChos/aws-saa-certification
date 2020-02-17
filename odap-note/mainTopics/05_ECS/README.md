## Security Configuration
You have root access to the operating system of your container instances, enabling you to take ownership of the operating system's security settings as well as load and configure additional software components for security capabilities such as monitoring, patch management, log management and host intrusion detection.

## ECS instances and its endpoint
The container agent runs on each infrastructure resource within an Amazon ECS cluster. It sends information about the resouce's current running tasks and resource utilization to Amazon ECS, and starts and stops taske whenever it recieves a request from Amazon ECS.

**Container instances need external network access to communicate with the Amazon ECS service endpoint**, so if your container instances do not have public IP address, then they must **use network access translation (NAT)** to provide this access.

## Fargte Launch Type
The Farget launch type allows you to run your containerized applications without the need to provision and manage the backend infrastructure. Just register your task definition and Fargte launches the container for you.

## ECS with AWS CloudTrail 
Amazon ECS is integrated with AWS CloudTrail, a service that provides a record of actions taken by a user, role, or an AWS service in Amazon ECS. CloudTrail captures all API calls for Amazon ECS as events, including calls from the Amazon ECS console and from code cals to the Amazon ECS APIs.

CloudWatch and logs are for monitoring the ECS resources, not for the API actions made on ECS. You can monitor your Amazon ECS resources using Amazon CloudWatch, which collects and processes raw data from Amazon ECS into readable, near real-time metrics.