# ELB

Elastic Load Balancer

classic load balancers are retired

# ALB 
Application Load balancer

# GLB
Gateway load balancer
- firewalls, intrusion dection etc
- Operates at layer 3
- GENEVE port 6081

Sticky Sessions
- same user to same instance

Connection Draining
- for handling when an instance is un-healthy or de-registering

# Auto Scaling Group
- scales in and out, and can do health checks (ELB does it, but asg can handle taking down / up stuff)
- 
