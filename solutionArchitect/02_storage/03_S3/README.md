# Amazon S3

## Request Rate and Performance Guidelines
Amazon S3 automatically scales to high request rates. For example, your application can achieve at least 3,500 PUT/POST/DELETE and 5,500 GET requests per second per prefix in a bucket. There are no limits to the number of prefixes in a bucket.

## Uploading objects
Depending on the size of the data you are uploading, Amazon S3 offers the following options:
- Upload object in a single operation: with a single PUT operation, you can upload objects up to 5GB in size. 
- Upload objects in parts: using the multipart upload API, you can upload large objects. You can upload objects in parts. You can use a multipart upload for objects from 5 MB to 5TB in size.