# Amazon Cognito
**Amazon Cognito**: provides sign in and sign up capability for your web and mobile applications you can also integrate that signup process with external ouath providers such as Google and Facebook and also SAML 2 providers as well.

Sign-in through a third party (federation) is available in Amazon Cognito user pools. This feature is independent of federation through Amazon Cognito identity pools (federated identities).

Amazon Cognito Identity Pools can support unauthenticated identities by providing a unique identifier and AWS credentials for users who do not authenticate with an identity provider. Unauthenticated users can be associated with a role that has limited access to resources as compared to a role for authenticated users.

**OpenID Connect(OIDC) identity providers(IdPs)** are supported in Cognito, along with social and SAML based identity providers. You can add an OIDC IdP to your user pool in the AWS Management Console, with the AWS CLI, or by using the user pool API method CreateIdentityProvider.