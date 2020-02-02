**Section: Working with Records**

When you create a record, you choose a **routing policy**, which determines how Amazon Route 53 responds to queries:

1. Simple routing policy – Use for a single resource that performs a given function for your domain, for example, a web server that serves content for the example.com website.
2. Failover routing policy – Use when you want to configure active-passive failover.
3. Geolocation routing policy – Use when you want to route traffic based on the location of your users.
4. Geoproximity routing policy – Use when you want to route traffic based on the location of your resources and, optionally, shift traffic from resources in one location to resources in another.
5. Latency routing policy – Use when you have resources in multiple locations and you want to route traffic to the resource that provides the best latency.
6. Multivalue answer routing policy – Use when you want Route 53 to respond to DNS queries with up to eight healthy records selected at random.
8. Weighted routing policy – Use to route traffic to multiple resources in proportions that you specify.

Route 53 **Weighted Routing Policy** can be used for managing risk with production application updates by releasing updates using staged increases in the percentage of users receiving the updates.

Weighted routing lets you **associate multiple resources with a single domain name** (example.com) or subdomain name (acme.example.com) and choose **how much traffic is routed to each resource**. This can be useful for a variety of purposes, including load balancing and testing new versions of software.

**About Alias Records**

While ordinary Amazon Route 53 records are standard DNS records, **alias records** provide a Route 53–specific extension to DNS functionality. Instead of an IP address or a domain name, an alias record contains a **pointer to a CloudFront distribution, an Elastic Beanstalk environment, an ELB Classic, Application, or Network Load Balancer, an Amazon S3 bucket** that is configured as a static website, or another Route 53 record in the same hosted zone.
Alias records can save your time because Route 53 automatically recognizes changes in the records that the alias record refers to. For example, suppose an alias record for example.com points to an ELB load balancer at lb1- 1234.us-east-2.elb.amazonaws.com. If the IP address of the load balancer changes, Route 53 will automatically reflect those changes in DNS answers for example.com without any changes to the hosted zone that contains records for example.com.
