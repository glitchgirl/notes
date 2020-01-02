Physical
Visual security
Access-based enumeration
Shoulder surfing 	

Ingress security

Egress security
USB port locks
Decommissioning devices
 
Login security (physical)

Logical
Authentication
Hard to fake, hard to steal, limited in time
Multifactor 

Authorization & Permission
Least privilege

Domain security
Central DB of users, computers, groups, resources. Like active directory. 
Groups are used to assign domain permissions
The domain is different than local
Enterprise admins- all permissions 
Domain admins- one domain, but not the whole enterprise (captain, not general)
Organizational Unit- sub-container for managing users and containers
OU admin- unit admin, can’t see into the domain (squad leader)
Local group policy (gets overwritten by network GPO (group policy)
➝Sites
➝Domain
		➝OU
Order of power: (OU(domain(site(local))))
	Last write wins

Communication 
Firewalls
	Bidirectional
	Block unused ports
MAC address filtering
(media access control)

Access restrictions

Encryption
IPsec can slow stuff down

Developers as tools: how your supply chain is getting owned
Traditional supply chain interdiction is the method of inserting a process into a supply chain to gain a competitive advantage 
Software interdiction is scalable in the software 
ShadowHammer - ASUS systems tiny malicious code injection into actual code flow
CCleaner- same in the actual codebase
SDLC-software development life cycle
Highest quality/lowest cost/shortest time (in real life its normally just two of these)
SSDLC (security added)
Best practices that red team can take advantage of:
Commit often
Write good commit messages
Use branches 
Once in a machine, it can be easy to just edit code
Security in the IDE
Scan code on commit/build process/apps on non-prod, apps to prod
Security needs to be baked into the start of the program, not slapped on the end
Intel prop checks

