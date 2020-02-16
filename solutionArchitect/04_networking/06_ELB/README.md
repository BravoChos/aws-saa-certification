# Elastic Load Balancer
Elastic Load Balancing automatically distributes incoming application traffic across multiple targets, such as Amazon EC2 instances, containers, IP addresses, and Lambda functions. It can handle the varying load of your application traffic in a single Availability Zone or across multiple Availability Zones. 

Elastic Load Balancing offers three types of load balancers that all feature the high availability, automatic scaling, and robust security necessary to make your applications fault tolerant.

- Application Load Balancer: is best suited for load balancing of HTTP and HTTPS traffic and provides advanced request routing targeted at the delivery of modern application architectures, including microservices and containers. With Application Load Balancers, cross-zone load balancing is always enabled.

- Nework Load Balancer: is best suited for load balancing of Transmission Control Protocol (TCP), User Datagram Protocol (UDP) and Transport Layer Security (TLS) traffic where extreme performance is required. 

- Classic Load Balancer: provides basic load balancing across multiple Amazon EC2 instances and operates at both the request level and connection level.

Elastic Load Balencers are AWS high-available and scalable components managed by AWS. Once you creat a load balancer, you will be given a internet-accessible hostname to connect. AWS manages the underlying IP addresses and you do not need to attach an eslatic IP address in order to connect from internet.

## Monitor Your Application Load Balancers
You can use the following features to monitor your application load balancers
- CloudWatch metrics
- Access logs
- Request tracing
- CloudTrail logs