# Infrastructure

Infrastructure
- Shared responsibility model 

Protecting your AWS resources
- Principal of least privilege
- Identities

# Principal of least privilege
- Persons (or processes) can perfrom all activities they need to perform, and no more.

# AWS IAM
- Centrally manage users and user permissions in AWS 

- Using AWS IAM, you can:
    - Create users, groups, roles and policies.
    - Define permissions to control which AWS resources users and access.
- IAM integrates with Microsoft Active Directory and AWS Directory Service using SAML identity federation.

# Identities 
- IAM users: Users created within the account
- Role: Temporary idenetities used by EC2 instances, lambdas, and external users.
- Federation: Users with Active Directory identities or other corporate credentials have role assigned in IAM.
- Web Identity Federation: Users with web identities from Amazon.com or other Open ID provider have role assigned using Security Token Service (STS).