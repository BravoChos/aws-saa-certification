# CloudFront
**Amazon CloudFront**: is a global content delivery network or CDN for short that securely delivers your frequently requested content to over 100 edge locations across the globe and by doing this it achieves low latency and high transfer speeds for your end-users. It also provides protection against DDoS attacks. In short, 

- Web service for high performance content delivery.
- World-wide network data centres (edge locations).
- Reduces number of hops for requests.

## CloudFront Origin Server
- Location of content to be delivered.
- Origin server is either an S3 bucket or an HTTP server.
- HTTP server can be on an EC2 instance.
- Can also be on a web server you mangage (web only not RTMP)
- CloudFront must have access to origin server.

## CloudFront Distrubution
- Distribution tells CloudFront which origin servers to get your files from and the TTL.
- CloudFront assigns a domain name to your new distribution. (can be alternate domain CNAME)
- If an edge location contains the requested file within TTL it is delivered. If not it is fetched from the origin server then delivered and cached at the edge location.
- Distributions, or parts of, can be invalidated to force new content.

## Troubleshooting
If you can't view the files in your CloudFront web distribution. Possible causes are:
1. Incorrect S3 bucket and object permissions
2. You haven’t signed up for both CloudFront and Amazon S3, separately.
3. Old CNAME record for your domain name is not updated or not replaced with the new one.
4. CNAME record points to your Amazon S3 bucket, not your distribution's domain name.