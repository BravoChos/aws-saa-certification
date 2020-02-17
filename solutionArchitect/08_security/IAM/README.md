# IAM
**IAM** or AWS identity and access management allows you to manage user access to your AWS services and resources in your account. Users and groups of users have individual permissions that allow or deny access to your resources.

IAM credentials are used to:
- manage your AWS account credentials, such as your password, access keys (access key ID and secret access key).
- manage multi-factor authentication devices.
- create security credentials for your users as needed.
- allow users to access account billing pages.
- allow applications that run on Amazon EC2 to access to AWS resources 

You can use IAM features to securely give applications that run on EC2 instances the credentials that they need in order to access other AWS resources, like S3 buckets and RDS or DynamoDB databases.

IAM is global service so it will not have a region specified in the ARN.  
ex) arn:aws:iam::123456789012:instance-profile/Webserver

## IAM Role
A **Role** is an entity that has a set of permissions, and that another entity assumes to make calls to access your AWS resources.

An IAM role is similar to a user, in that it is an AWS identity with permission policies that determine what the identity can and cannot do in AWS. 

However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it. Also, a role does not have standard long-term credentials (password or access keys) associated with it. Instead, if a user assumes a role, temporary security credentials are created dynamically and provided to the user.

To create a role, you can use the AWS Management Console, the AWS CLI, the Tools for Windows PowerShell, or the IAM API.

Your users might already have identities outside of AWS, such as in your corporate directory. If those users need to work with AWS resources (or work with applications that access those resources), then those users also need AWS security credentials. You can use an IAM role to specify permissions for users whose identity is federated from your organization or a third-party identity provider (IdP).

## IAM Best Practices and Use Cases

- Use roles for applications that run on AWS EC2 instances  
- Keep a history of activity in your AWS account  
- Grant least privilege  

=> **Never** store AWS credentials inside application code!

## IAM Alias

Your AWS account can have only one alias. If you create a new alias for your AWS account, the new alias overwrites the old alias, and the URL containing the old alias stops working.

## IAM group
An IAM group is a collection of IAM users. Groups let you specify permissions for multiple users, which can make it easier to manage the permissions for those users. For example, you could have a group called Admins and give that group the types of permissions that administrators typically need. 

Any user in that group automatically has the permissions that are assigned to the group. If a new user joins your organization and needs administrator privileges, you can assign the appropriate permissions by adding the user to that group. Similarly, if a person changes jobs in your organization, instead of editing that user's permissions, you can remove him or her from the old groups and add him or her to the appropriate new groups.

**NOTE**  
You can only use ASCII characters for IAM entities.