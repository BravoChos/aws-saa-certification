# VPC
A VPC endpoint enables you to privately connect your VPC to supported AWS services and VPC endpoint services powered by AWS PrivateLink without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Instances in your VPC do not require public IP addresses to communicate with resources in the service. Traffic between your VPC and the other service does not leave the Amazon network.

## VPC Endpoints
### Interface Endpoint
**Interface Endpoint** (Powered by AWS PrivateLink): is an elastic network interface with a private IP address from the IP address range of your subnet that serves as an entry point for traffic destined to a supported service. The following services are supported:
- Amazon API Gateway
- Amazon EC2 Auto Scaling
- AWS CloudTrail
- AWS CloudWatch
- Amazon Kinesis
- Amazon SNS, SQS

### Gateway Endpoint
**Gateway Endpoint** is a gateway that you specify as a target for a route in your route table for traffic destined to a supported AWS service. The following AWS services are supported:
- S3
- DynamoDB

### Controlling the Use of VPC Endpoints
By default, IAM users do not have permission to work with endpoints. You can create an IAM user policy that grants users the permissions to create, modify, describe, and delete endpoints. 