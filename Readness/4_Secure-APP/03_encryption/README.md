# Data Tier
Data in transit 
- In and out of AWS 
- Within AWS

Data at rest 
- Amazon S3 
- Amazon EBS 

# Data in Transit
Transferring data in and out of your AWS infrastructure
- SSL over web
- VPN for IPsec
- IPsec over AWS Direct Connect
- Import/Export/Snowball

Data sent to the AWS API
- AWS API calls use HTTPS/SSL by default

# Data at Rest
Data stored in Amazon S3 is private by default, requires AWS credentials for access
- Access over HTTP or HTTPS
- Audit of access to all objects
- Supports ACL and policies
    - Buckets
    - Prefixes (directory/folder)
    - Objects

**Server-side encryption options** 
- Amazon S3-Managed keys (SSE-S3)
- KMS-Managed keys (SSE-KMS)
- Customer-Provided keys (SSE-C)

**Client-side encryption options**
- KMS-Managed master encryption keys (CSE-KMS)
- Customer managed master encryption keys (CSE-C)

# Managing Your Keys
Key Management Service 
- Customer software-based key management
- Integrated with many AWS services
- Use directly from application

# AWS CloudHSM
- Hardware-based key management
- Use directly from application
- FIPS 140-2 compliance

# Intergrating AWS KMS
Services integrated with AWS KMS
- Amazon EBS
- Amazon S3
- Amazon RDS
- Amazon Redshift
- Amazon Elastic Transcoder
- Amazon WorkMail
- Amazon EMR