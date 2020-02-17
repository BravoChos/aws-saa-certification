# Amazon Route 53
**Amazon Route 53** is a highly available and scalable domain name system or DNS for short and it can handle direct traffic for your domain name and direct that traffic to your back-end web server. 

There are three main functions:
- Register Domain Names
- Route internet traffic to the resources for your domain
- Check the health of your resources

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

## Routing Policy
When you create a record, you choose a **routing policy**, which determines how Amazon Route 53 responds to queries:

- Simple routing policy – Use for a single resource that performs a given function for your domain, for example, a web server that serves content for the example.com website.
- Failover routing policy – Use when you want to configure active-passive failover.
- Geolocation routing policy – Use when you want to route traffic based on the location of your users.
- Geoproximity routing policy – Use when you want to route traffic based on the location of your resources and, optionally, shift traffic from resources in one location to resources in another.
- Latency routing policy – Use when you have resources in multiple locations and you want to route traffic to the resource that provides the best latency.
- Multivalue answer routing policy – Use when you want Route 53 to respond to DNS queries with up to eight healthy records selected at random.
- Weighted routing policy – Use to route traffic to multiple resources in proportions that you specify.

Route 53 **Weighted Routing Policy** can be used for managing risk with production application updates by releasing updates using staged increases in the percentage of users receiving the updates.

Weighted routing lets you **associate multiple resources with a single domain name** (example.com) or subdomain name (acme.example.com) and choose **how much traffic is routed to each resource**. This can be useful for a variety of purposes, including load balancing and testing new versions of software.

## DNS Record Types

Amazon Route 53 currently supports the following DNS record types:
- A (address record)
- AAAA (IPv6 address record)
- CNAME (canonical name record)
- ...

Amazon Route 53 also offers alias records, which are an Amazon Route 53-specific extension to DNS. You can create alias records to route traffic to selected AWS resources, including Amazon Elastic Load Balancing load balancers, Amazon CloudFront distributions, AWS Elastic Beanstalk environments, API Gateways, VPC interface endpoints, and Amazon S3 buckets that are configured as websites. 

Alias record typically have a type of A or AAAA, but they work like a CNAME record. Using an alias record, you can map your record name (example.com) to the DNS name for an AWS resource(elb1234.elb.amazonaws.com). Resolvers see the A or AAAA record and the IP address of the AWS resource.

## More About Alias Records

While ordinary Amazon Route 53 records are standard DNS records, **alias records** provide a Route 53–specific extension to DNS functionality. Instead of an IP address or a domain name, an alias record contains a **pointer to a CloudFront distribution, an Elastic Beanstalk environment, an ELB Classic, Application, or Network Load Balancer, an Amazon S3 bucket** that is configured as a static website, or another Route 53 record in the same hosted zone.  

Alias records can save your time because Route 53 automatically recognizes changes in the records that the alias record refers to. For example, suppose an alias record for example.com points to an ELB load balancer at lb1- 1234.us-east-2.elb.amazonaws.com. If the IP address of the load balancer changes, Route 53 will automatically reflect those changes in DNS answers for example.com without any changes to the hosted zone that contains records for example.com.

## CNAME vs Alias 
These are the main differences:

- The A record maps a name to one or more IP addresses when the IP are known and stable.
- The CNAME record maps a name to another name. It should only be used when there are no other records on that name.
- The ALIAS record maps a name to another name, but can coexist with other records on that name. The URL record redirects the name to the target name using the HTTP 301 status code.

### Important rules:

The **A**, **CNAME**, and **ALIAS** records cause a name to resolve to an IP. Conversely, the URL record redirects the name to a destination. The URL record is a simple and effective way to apply a redirect for one name to another name, for example redirecting **www.example.com** to **example.com**.

The **A** name must resolve to an IP. The **CNAME** and **ALIAS** records must point to **a** name.

## Which one to use?
Understanding the difference between A name and CNAME records will help you decide.

### General rules:

- Use an A record if you manage which IP addresses are assigned to a particular machine, or if the IP are fixed (this is the most common case).
- Use a CNAME record if you want to alias one name to another name, and you don’t need other records for the same name.
- Use an ALIAS record if you’re trying to alias the root domain (apex zone), or if you need other records for the same name.

## Working with Private Hosted Zones
In a private hosted zone, you can associate **Route 53 health checks only with failover, multivalue answer, and weighted records**. To use private hosted zones, you must set enableDnsHostnames and enableDnsSupport. You can use the Amazon Route 53 console to disassociate Amazon VPCs from a private hosted zone. 

## Health Checks and Configuring DNS Failover
Route 53 HTTPS health checks test **whether it’s possible to connect with the endpoint over SSL** and whether the endpoint returns a valid HTTP response code. However, they do not validate the SSL certificate returned by the endpoint.

Route 53 doesn't prevent you from deleting a health check even if the health check is associated with one or more records. If you delete a health check and you don't update the associated records, the future status of the health check can't be predicted and might change. This will affect the routing of DNS queries for your DNS failover configuration.

Route 53 health checks integrate with CloudWatch metrics so that you can do the following: 
1. Verify that a health check is properly configured.
2. Review the status of a health check over a specified period of time.
3. Configure CloudWatch to send an Amazon SNS alert when the status of a health check is unhealthy. 

## Types of Health Checks
- Health Checks that monitor an endpoint
- monitor CloudWatch alarms

## Configuring DNS Failover
Use an **active-passive failover configuration** when you want a primary resource or group of resources to be available the majority of the time and you want a secondary resource or group of resources to be on standby in case all the primary resources become unavailable. When responding to queries, Route 53 includes only the healthy primary resources. If all the primary resources are unhealthy, Route 53 begins to include only the healthy secondary resources in response to DNS queries. Having an S3 static website on standby for an EC2 instance is an example of Active-passive failover.

## Limits
As with other AWS products, there are no contracts or minimum commitments for using Amazon Route 53. You pay only for the hosted zones that you configure and the number of DNS queries that Route 53 answers.

Each new Amazon Route 53 account is limited to a maximum of **50 domains**. Complete an AWS request form for a higher limit and they will respond to your request within two business days. Route 53 supports health checks over HTTPS, HTTP or TCP. 

