# Amazon Redshift
**Amazon Redshift**: is a fast fully managed petabyte scale data warehouse that is based upon the postgre SQL database engine. 
If you're looking for a big data storage solution, redshift is perfect for this Amazon.

## Enhanced VPC Routing
Amazon Redshift Enhanced VPC Routing provides VPC resources access to Redshift. Redshift will not be able to access the S3 VPC endpoints without enabling Enhanced VPC routing. NAT instance cannot be reached by Redshift without enabling Enhanced VPC Routing.

When you use Amazon Redshift Enhanced VPC Routing, Amazon Redshift forces all COPY and UNLOAD traffic between your cluster and your data repositories through your Amazon VPC.