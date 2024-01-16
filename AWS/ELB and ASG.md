# ELB

Elastic Load Balancer
- vertical scaliabily means making one instance smaller or larger
- horizontal scalibably means adding or removing instances
- classic load balancers are retired
- Only Network Load Balancer provides both static DNS name and static IP.
-  Application Load Balancer provides a static DNS name but it does NOT provide a static IP. The reason being that AWS wants your Elastic Load Balancer to be accessible using a static endpoint, even if the underlying infrastructure that AWS manages changes.
  
# ALB 
Application Load balancer
- route traffic to different Target Groups based on URL Path, Hostname, HTTP Headers, and Query Strings.
- The following cookie names are reserved by the ELB (AWSALB, AWSALBAPP, AWSALBTG)
- Server Name Indication (SNI) allows you to expose multiple HTTPS applications each with its own SSL certificate on the same listener
- Cooldown Period after each scaling activity. In this period, the ASG doesn't launch or terminate EC2 instances. 

# GLB
Gateway load balancer
- firewalls, intrusion dection etc
- Operates at layer 3
- GENEVE port 6081

# NLB
- Network Load Balancer provides the highest performance and lowest latency
- support both TCP and UDP protocols.
- https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API

Sticky Sessions
- same user to same instance

Connection Draining
- for handling when an instance is un-healthy or de-registering

# Auto Scaling Group
- scales in and out, and can do health checks (ELB does it, but asg can handle taking down / up stuff)
- 
