## What is the difference between ElastiCache and CloudFront?

**1)-Elasticache:**   
ElastiCache is improving the performance of you application, where the data is retrieved from in memory data stores.
It means elastic cache is caching data from database. The request reaches the origin server.  

**2)-Cloudfront:**   
Cloudfront is caching the data on a remote edge location which means that the request is not even going to the origin server.

## Protecting Data in Amazon S3
Following options of protecting data at rest in Amazon S3:

- Server-Side Encryption: You request Amazon S3 to encrypt your object before saving it on disks in its data centers and decrypt it when you download the objects.
- Client-Side Encryption: You can encrypt data client-side and upload the encrypted data to Amazon S3. In this case, you manage the encryption process, the encryption keys, and related tools.

Data protection refers to protecting data while in-transit (as it travels to and from Amazon S3) and at rest (while it is stored on disks in Amazon S3 data centers).

You can protect data in transit by using SSL or by using client-side encryption. You have the following options of protecting data at rest in Amazon S3.

You use Server-Side Encryption with:

- Amazon S3-Managed Keys (SSE-S3)
- AWS KMS-Managed Keys (SSE-KMS)
- Customer-Provided Keys (SSE-C)

Server-side encryption is about data encryption at rest—that is, Amazon S3 encrypts your data at the object level as it writes it to disks in its data centers and decrypts it for you when you access it.

## MFA
You can optionally add another layer of security by configuring a bucket to enable **MFA** (Multi-Factor Authentication) Delete, which requires additional authentication for either of the following operations.
- Change the versioning state of your bucket
- Permanently delete an object version

MFA Delete requires two forms of authentication together:
- Your security credentials
- The concatenation of a valid serial number, a space, and the six-digit code displayed on an approved authentication device. 

MFA Delete thus provides added security in the event, for example, your security credentials are compromised.

## Delete Marker
When you DELETE an object, all versions remain in the bucket and Amazon S3 inserts a **delete marker**.
A delete marker is a placeholder (marker) for a versioned object that was named in a simple DELETE request. Because the object was in a versioning-enabled bucket, the object was not deleted. The delete marker, however, makes Amazon S3 behave as if it had been deleted.

To permanently delete versioned S3 objects, you must use DELETE Object versionId.

## CORS

Cross-origin resource sharing (CORS) defines a way for client web applications that are loaded in one domain to interact with resources in a different domain. With CORS support in Amazon S3, you can build rich client-side web applications with Amazon S3 and selectively allow cross-origin access to your Amazon S3 resources.

To configure your bucket to allow cross-origin requests, you create a CORS configuration, an **XML** document with rules that identify the origins that you will allow to access your bucket, the operations (HTTP methods) will support for each origin, and other operation-specific information. 