**What is CloudFront?**
1. Web servicec for high performance content delivery.
2. World-wide network data centres (edge locations).
3. Reduces number of hops for requests.

**CloudFront Origin Server**
1. Location of content to be delivered.
2. Origin server is either an S3 bucket or an HTTP server.
3. HTTP server can be on an EC2 instance.
4. Can also be on a web server you mangage (web only not RTMP)
5. CloudFront must have access to origin server.

**CloudFront Distrubution**
1. Distribution tells CloudFront which origin servers to get your files from and the TTL.
2. CloudFront assigns a domain name to your new distribution. (can be alternate domain CNAME)
3. If an edge location contains the requested file within TTL it is delivered. If not it is fetched from the origin server then delivered and cached at the edge location.
4. Distributions, or parts of, can be invalidated to force new content.

**Section: Getting Started with CloudFront**
If you are using Amazon S3 as the origin for your objects in CloudFront, it is recommended that you select Off for the value of Cookie Logging since Amazon S3 doesn't process cookies.
