# OpsWorks
**AWS Opsworks** provides managed instances of Chef and Puppet. Chef and Puppet can be used to configure and automate the deployment of AWS resources. 

An OpsWorks **Instance** represents a single computing resource.

Cloud-based computing usually involves groups of AWS resources, such as EC2 instances and Amazon Relational Database Service (RDS) instances. For example, a web application typically requires application servers, database servers, load balancers, and other resources.

An OpsWorks **layer** is basically a blueprint that specifies how to configure a set of Amazon EC2 instances for a particular purpose, such as serving applications or hosting a database server.

AWS OpsWorks Stacks, the original service, provides a simple and flexible way to create and manage stacks and applications. AWS OpsWorks Stacks lets you deploy and monitor applications in your stacks. You can create stacks that help you manage cloud resources in specialized groups called layers. A layer represents a set of EC2 instances that serve a particular purpose, such as serving applications or hosting a database server.

The **Stack** is the core AWS OpsWorks component. It is basically a container for AWS resources—Amazon EC2 instances, Amazon EBS volumes, Elastic IP addresses, and so on—that have a common purpose and would be logically managed together.

Cloud-based computing usually involves groups of AWS resources, such as EC2 instances and Amazon Relational Database Service (RDS) instances. For example, a web application typically requires application servers, database servers, load balancers, and other resources. This group of instances is typically called a stack.

Every stack contains one or more layers, each of which represents a stack component, such as a load balancer or a set of application servers. Each layer in a stack must have at least one instance and can optionally have multiple instances. Each instance in a stack must be a member of at least one layer, except for registered instances. Amazon EC2 instances can optionally be a member of multiple OpsWorks layers.

