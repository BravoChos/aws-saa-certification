# Vertical Scaling vs. Horizontal scaling
**Vertical scaling (Scale up and down)**  
Change in the specifications of instances (more CPU, memory)

<img src="./diagram/vertical_scaling.png" width="50%">

**Horizontal Scaling (Scale in and out)**  
Change in the number of instances (add and remove instances as needed)

<img src="./diagram/horizontal_scaling.png" width="50%">

# Auto Scaling
- Launch or terminates instances
- Automaticaly register new instances with load balancer
- can launch across Availability Zones

# Implement Elasticity
<img src="./diagram/elasticity.png" >

# Auto Scaling Components
Auto Scaling launch configuration
- specifies EC2 instance size and AMI name

Auto Scaling Group
- References the launch configuration
- specifies min, max, and desired size of the Auto Scaling group
- May reference an ELB instance
- Health Check Type

Auto Scaling Policy
- specifies how much to scale in or scale out the Auto Scaling
- one or more may be attached to Auto Scaling group