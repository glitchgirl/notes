# AWS CCP training
- AWS has support plans, business plans have support.
- Trusted advisor: 7 checks for free, paid accounts get them all.
- TCO: total cost of ownership

## Resource groups and tagging
- words for organizing
- groups / words can be used for billing

## Quick starts
- Prebuilt templates that use cloud formations
- many guides use these

## AWS networking
- region
- AZ: availibilty zone
- VPC: virtual private cloud
- Internet gateway
- route tables
- NACLS (also called salt): subnet firewall
- security groups
- subnets

## Database services
 - Dynamo
 - DocumentDB
 - RDS(relational database service)
    - aurora
    - severless
- Neptune
- Redshift
- Elastic cache

## Provisioning
- beanstalk (feels like heroku)
- Ops work (chef)
- Quick starts (see above)
- Marketplace: user generated "quick starts"
- Cloud formation: infastructure as code

## Initialisms
- SES: "fancy" email html/gets email
- SNS: plain email
- SSM: Systems manager 
- WAF: web application firewall
- IDS/IPS: intrusion dectection/protection system
- HSM: hardware security module
- NACL: network access control list
- SQS: Simple Queue service = apps pull from queue using SDK

## Shared responsibility:
  - client:
    - data
    - config
  - AWS:
    - hardware
    - managed services
    - global

- aws shield: managed DDOS service

## Compliance
- Compliance programs: HIPAA, PCI
- artifact generates files to prove compliance

## Pen testing
- not all pen testing is permitted.
- permitted:
  - dns walking
  - ddos
  - flooding
