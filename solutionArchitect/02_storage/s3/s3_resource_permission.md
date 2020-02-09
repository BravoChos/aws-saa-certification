**Section: Managing Access Permissions to Your Amazon S3 Resources**
Section: Managing Access Permissions to Your Amazon S3 Resources

Q1.
Object policies and access control lists (ACLs) are resource-based because you attach them to your Amazon S3 resources. (F)
Bucket policies not object policies.
Amazon S3 offers access policy options broadly categorized as resource-based policies and user policies. Access policies you attach to your resources (buckets and objects) are referred to as resource-based policies. For example, bucket policies and access control lists (ACLs) are resource-based policies. You can also attach access policies to users in your account. These are called user policies. You may choose to use resource-based policies, user policies, or some combination of these to manage permissions to your Amazon S3 resources. The introductory topics provide general guidelines for managing permissions.

Q2.
Using IAM, you can create IAM users, groups, and roles in your account and attach access policies to them granting them access to AWS resources including Amazon S3.

Bucket policy and user policy are two of the access policy options available for you to grant permission to your Amazon S3 resources. Both use JSON-based access policy language.

Q3. 
To perform a specific operation on an object, an IAM user needs permission from the parent AWS account to which it belongs or the AWS account that owns the object. (F)

When Amazon S3 receives a request for an object operation, it converts all the relevant permissions—resource- based permissions (object access control list (ACL), bucket policy, bucket ACL) and IAM user policies—into a set of policies to be evaluated at run time. It then evaluates the resulting set of policies in a series of steps. In each step, it evaluates a subset of policies in three specific contexts—user context, bucket context, and object context.
User context – If the requester is an IAM user, the user must have permission from the parent AWS account to which it belongs.

Q4. An object ACL is preferred:
Answers
A. When you want to manage access to objects not owned by the bucket owner or when permissions vary by object and you need to manage permissions at the object level
B. When you want to manage cross-account permissions for all Amazon S3 permissions
C. When permission from the parent account to a user is required
D. When you want to grant write permission to the Amazon S3 Log Delivery group to write access log objects
to your bucket

Answer is A 
When to Use an Object ACL?
In addition to an object ACL, there are other ways an object owner can manage object permissions. For example:
If the AWS account that owns the object also owns the bucket, then it can write a bucket policy to manage the object permissions.
If the AWS account that owns the object wants to grant permission to a user in its account, it can use a user policy.
So when do you use object ACLs to manage object permissions? The following are the scenarios when you use object ACLs to manage object permissions:
• An object ACL is the only way to manage access to objects not owned by the bucket owner
• Permissions vary by object and you need to manage permissions at the object level
• Object ACLs control only object-level permissions

Q5.
A Bucket Policy is preferred:
Answers
A. When you want to manage access to objects not owned by the bucket owner
B. When you want to manage cross-account permissions for all Amazon S3 permissions
C. When permission from the parent account to a user is required
D. When you want to grant write permission to the Amazon S3 Log Delivery group to write access log objects
to your bucket
E. When permissions vary by object and you need to manage permissions at the object level
Answer
If an AWS account that owns a bucket wants to grant permission to users in its account, it can use either a bucket policy or a user policy. But in the following scenario, you will need to use a bucket policy.
You want to manage cross-account permissions for all Amazon S3 permissions

Q6.
A User Policy is preferred:
Answers
A. When you want to manage access to objects not owned by the bucket owner
B. When you want to manage cross-account permissions for all Amazon S3 permissions
C. When you want to grant write permission to the Amazon S3 Log Delivery group to write access log objects
to your bucket
D. When permission from the parent account to a user is required
E. When permissions vary by object and you need to manage permissions at the object level
Answer
D
WS Identity and Access Management (IAM) enables you to create multiple users within your AWS account and manage their permissions via user policies. An IAM user must have permissions from the parent account to which it belongs, and from the AWS account that owns the resource the user wants to access. The permissions can be granted as follows:
• Permission from the parent account – The parent account can grant permissions to its user by attaching a user policy.
• Permission from the resource owner – The resource owner can grant permission to either the IAM user (using a bucket policy) or the parent account (using a bucket policy, bucket ACL, or object ACL).

Q7.
A Bucket ACL is preferred:
Answers
A. When you want to manage access to objects not owned by the bucket owner
B. When you want to manage cross-account permissions for all Amazon S3 permissions
C. When you want to grant write permission to the Amazon S3 Log Delivery group to write access log objects
to your bucket
D. When permission from the parent account to a user is required
E. When permissions vary by object and you need to manage permissions at the object level
Answer C
The only recommended use case for the bucket ACL is to grant write permission to the Amazon S3 Log Delivery group to write access log objects to your bucket (see Server Access Logging). If you want Amazon S3 to deliver access logs to your bucket, you will need to grant write permission on the bucket to the Log Delivery group. The only way you can grant necessary permissions to the Log Delivery group is via a bucket ACL.

Q8.
In its most basic sense, a policy contains the following elements:
• Resources 
• Actions
• Effect
• Principal

Q9.
What is the resource arn:aws:s3:::mybucket/developers/${aws:username}/ ?
=> A folder in mybucket/developers with name the same as the user name.

Q10.
What does the following bucket policy do?
{
"Version": "2012-10-17", "Statement": [
{
"Sid": "statement1", "Effect": "Allow", "Principal": {
"AWS": "arn:aws:iam:: 123456789012:user/Bill" },
"Action": "s3:*",
"Resource": "arn:aws:s3:::examplebucket/*" }
] }

=>Grants all S3 action permissions to a user (Bill)

Q11.

The access policy language allows you to specify _______ when granting permissions. The _______element (or _______block) lets you specify _______for when a policy is in effect. In the _______element, which is optional, you build expressions in which you use Boolean operators (equal, less than, etc.) to match your _______against values in the request.
=>Conditions

Q12.
What does the following bucket policy do?
{
"Version": "2012-10-17", "Id": "S3PolicyId1", "Statement": [
{
"Sid": "IPAllow",
"Effect": "Allow",
"Principal": "*",
"Action": "s3:*",
"Resource": "arn:aws:s3:::examplebucket/*", "Condition": {
"IpAddress": {
"aws:SourceIp": "54.240.143.0/24" },
"NotIpAddress": {
"aws:SourceIp": "54.240.143.188/32" }
} }
] }

Grants permissions to any user to perform any Amazon S3 operations on objects in the examplebucket bucket. However, the request must originate from the range of IP addresses specified in 54.240.143.0/24 but excluding 54.240.143.188/32.

Q13.
The following policy denies any Amazon S3 operation on the /taxdocuments folder in the examplebucket bucket if the request is not MFA authenticated.?
{
"Version": "2012-10-17", "Id": "123", "Statement": [
{
"Sid": "",
"Effect": "Deny",
"Principal": "*",
"Action": "s3:*",
"Resource": "arn:aws:s3:::examplebucket/taxdocuments/*", "Condition": {
"Null": {
"aws:MultiFactorAuthAge": true }
} }
] }
Answer True



Amazon S3 supports the following destinations where it can publish events:
• Amazon Simple Notification Service (Amazon SNS) topic
• Amazon Simple Queue Service (Amazon SQS) queue
• AWS Lambda function
not AWS SES email

Q2.
Amazon S3 can publish events of the following types.
• s3:ObjectCreated:
• s3:ObjectCreated:Put
• s3:ObjectCreated:Copy
• s3:ReducedRedundancyLostObject
not s3:ObjectDeleted

Section: Performance Optimization
Q1.
If you anticipate that your workload will consistently exceed 100 requests per second, you should avoid sequential key names. (T)
=>If you must use sequential numbers or date and time patterns in key names, add a random prefix to the key name. The randomness of the prefix more evenly distributes key names across multiple index partitions.

Q2.
You can increase S3 performance by:
A. Add a hash string as prefix to the key name
B. Add more prefixes in your key name
C. Reverse the key name string
True

Q3.
If your workload is mainly sending GET requests, you should consider using Amazon Elasticache for performance optimization. (F)
=>Amazon CloudFront not Elasticache

What is the difference between ElastiCache and CloudFront?
Elasticache is improving the performance of you application, where the data is retrieved from in memory data stores.
It means elastic cache is caching data from database. The request reaches the origin server .
whereas cloudfront is caching the data on a remote edge location which means that the request is not even going to the origin server.