# CloudFormation
**CloudFormation**: allows you to use a text file to define your infrastructure and, to use his text file to deploy resources on the AWS cloud. This allows for the defining of your infrastructure as code and you can manage your infrastructure with the same version control tools that you use to manage your code. An AWS CloudFormation template is a JSON or YAML formatted text file. You can save these files with any extension, such as .json, .yaml, .template, or .txt. AWS CloudFormation uses these templates as blueprints for building your AWS resources.

When you use AWS CloudFormation, you manage related resources as a single unit called a **stack**. In other words, you create, update, and delete a collection of resources by creating, updating, and deleting **stack**. All the resources in a stack are defined by the stack's AWS CloudFormation template. When you update a stack, you modify the original stack template then AWS CloudFormation: **updates only the resources that you modified.** When you delete a stack, you specify the stack to delete, and AWS CloudFormation: **deletes the stack and all the resources in that stack**. You can delete stacks by using the AWS CloudFormation console, API, or AWS CLI.

One of the greatest benefits of templates and AWS CloudFormation is the ability to create a set of resources that work together to create an application or solution. The name used for a resource within the template is a logical name. When AWS CloudFormation creates the resource, it generates a physical name that is based on the combination of the logical name, the stack name, and a unique ID.

You declare **parameters** in a CloudFormation template's **parameters** object.

For sensitive information, you can use the **NoEcho** attribute to prevent a parameter value from being displayed in the console, command line tools, or API.If you set the NoEcho attribute to true, the parameter value is returned as asterisks (*****).

**Mappings** enable you to use an input value as a condition that determines another value. Similar to a switch statement, a mapping associates one set of values with another.

CloudFormation Fn::Join function takes two parameters, a delimiter that separates the values you want to concatenate and an array of values in the order that you want them to appear. CloudFormation Fn::Join function allows you to construct values based on parameters, resource attributes, and other strings.

## Automatic Rollback on Error
By default, the “automatic rollback on error” feature is enabled. This will cause all AWS resources that AWS CloudFormation created successfully for a stack up to the point where an error occurred to be deleted. This is useful when, for example, you accidentally exceed your default limit of Elastic IP addresses, or you don’t have access to an EC2 AMI you’re trying to run. This feature enables you to rely on the fact that stacks are either fully created, or not at all, which simplifies system administration and layered solutions built on top of AWS CloudFormation.

# Limits
Each AWS CloudFormation account is limited to a maximum of **200** stacks.
Template, Parameter, Output, and Resource description fields are limited to **4096** characters.
You can include up to **60** parameters and **60** outputs in a template.

