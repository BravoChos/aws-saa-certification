# Elastic Container Service

**ECS** or Amazon Elastic container service: is a highly scalable high-performance container management service for docker containers the containers. They will run on a managed cluster of ec2 instances

Following are the features for AWS ECS.

- Containers and Images
- Task Definition
- Tasks and Scheduling
- Clusters
- Container Agent

<img src="./diagram/ECS-Overview-Standard.png" >

## Service Definition

A service definition defines which task definition to use with your service, how many instantiations of that task to run, and which load balancer to accociate with your tasks.

Following are the parameters defined in Service Definition:

- Cluster on which to run the service
- Full ARN of the task definition to run in your service
- IAM Role that allows Amazon ECS to make calls to your load balancer on yout behalf.

## Task Definitions

To prepare your application to run on Amazon ECS, you create a task definition. The task definition is a textfile, in JSON format, that descirbes, that descirbes one or more containers, up to a maximum of ten, that form your application. It can be thought of as a blueprint for your application. A task definition is required to run Docker containers in Amazon ECS. Some of the parameters you can specify in a task definition include:

- The **Docker image** to use with each container in your task
- How much **CPU and memory** to use with each task or each container within a task
- The launch type to use, which determines the infrastructure on which your tasks are hosted
- The **Docker networking mode** to use for the containers in your task
- The logging configuration to use for your tasks
- Whether the task should continue to run if the container finishes or fails
- The command the container should run when it is started
- Any **data volumes** and environment variables that should be used with the containers in the task
- The IAM role that your tasks should use

## Security Configuration

You have root access to the operating system of your container instances, enabling you to take ownership of the operating system's security settings as well as load and configure additional software components for security capabilities such as monitoring, patch management, log management and host intrusion detection.

## Elastic Container Registry

ECR is a fully-managed Docker container registry that makes it easy for developers to store, manage, and deploy Docker continer images

## Amazon ECS Launch Types

An Amazon ECS launch type determines the type of infrastructure on which your tasks and services are hosted.

### 1. Fargte Launch Type

The Farget launch type allows you to run your containerized applications without the need to provision and manage the backend infrastructure. Just register your task definition and Fargte launches the container for you.

### 2. EC2 Launch Type

The EC2 launch type allows you to run your containerized applications on cluster of Amazon EC2 instances that you manage.

When you launch an Amazon ECS container instance, you have the option of passing user data to the instance. The data can be used to perform comon automated configuration tasks and even run scripts configuration information to the Docker daemon and the Amazon ECS container agent.

The Amazon ECS-optimized AMI looks for agent configuration dat in the /etc/ecs/ecs.config file when the container agent starts. You can specify this configuration data at launch with Amazon EC2 user data.

# Elastic Container Registry

Amazon Elastic Container Registry (Amazon ECR) is a managed AWS Docker registry service that is secure, scalable, and reliable. Amazon ECR supports private Docker repositories with resource-based permissions using AWS IAM so that specific users or Amazon EC2 instances can access repositories and images. Developers can use the Docker CLI to push, pull, and manage images.

## Components of Amazon ECR

### 1. Registry

An Amazon ECR registry is provided to each AWS account; you can create image repositories in your registry and store images in them. For more information, see Amazon ECR Registries.

### 2. Authorization token

Your Docker client must authenticate to Amazon ECR registries as an AWS user before it can push and pull images. The AWS CLI get-login command provides you with authentication credentials to pass to Docker. For more information, see Registry Authentication.

### 3. Repository

An Amazon ECR image repository contains your Docker or Open Container Initiative (OCI) images. For more information, see Amazon ECR Repositories.

### 4. Repository policy

You can control access to your repositories and the images within them with repository policies. For more information, see Amazon ECR Repository Policies.

### 5. Image

You can push and pull container images to your repositories. You can use these images locally on your development system, or you can use them in Amazon ECS task definitions. For more information, see Using Amazon ECR Images with Amazon ECS.
