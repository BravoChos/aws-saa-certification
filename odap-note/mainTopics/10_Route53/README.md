## Routing Traffic to other resources
- CloudFront
- Amazon EC2
- AWS Elastic Beanstalk
- Elastic load balancer
- Amazon RDS
- Amazon S3

## Logging, Monitoring, and Tagging
- CloudTrail
- CloudWatch
- Route 53 Dashboard
- Tag Editors

## CloudTrail vs API Gateway
You have created a REST API using AWS API Gateway and deployed to production. Your organization requested the details on who is accessing the API for auditing purpose. How would you get the required information on who accessed your API?

**Answer: Enable access logging** 

CloudWatch loggging enables API requests logging which does not contain who access the API and how did they access.

CloudTrail logs the request information on AWS APIs, not the APIs generated through API gateway. You can use AWS CloudTrail to capture API Gateway REST API calls in your AWS account and deliver the log files to an Amazon S3 bucket you specify. Examples of these API calls include creating a new API, resource, or method in API Gateway.
