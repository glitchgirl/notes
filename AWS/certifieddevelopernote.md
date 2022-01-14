General notes: 
- read the test carefully (lots of select twos/ NOTS)
- look for keywords: server, client, backend, cache, frontend, ELB, ALB, NLB

Knowledge notes:

- User Data is used to perform common automated config tasks and run scripts after the instance starts. Can pass two types of data, shell scripts and cloud-init directives as either plain text or file. 
- SSE-C is server side encrpytion with customer provided keys
- ALBs distribute traffic across multiple targets in multiple AZ. 
- To use an HTTPS listener you must deploy at least one SSL/TLS cert on LB. As the instances behind the ALB are under heavy load, the LB will use the server cert to teminate the front-end connection and then decrypt requests before sending them to the instances.
- Read capacity units (one strongly consistent read per second, or two eventually consistent reads per second, for an item up to 4KB in size) 
- Write capacity units (one write per second for an item up to 1KB in size) ((items rounded up))
- ECS - elastic container service (docker(and friends) management) 
- Max AWS KMS size is 4KB
- CloudFormation key words:
  - !ImportValue = returns value of an output from another stack
  - !Ref = returns value of a parameter or resource
  - !GetAtt = returns the value of an attribute from a resource in the template
  - !Sub = substitutes variables
 - SQS uses a visibility timeout to prevent other consumers from receiving and processing the same message
 - ARN (amazon resource Name)
PRE-TEST(take this on wednesday) 1)
Score : 46
Knowledge areas
  - Deployment - 33%
  - Security - 50%
  - Refactoring - 50 %
  - Development - 54 %
  - Monitoring/Troubleshooting - 33%
  
  Test review notes:
  Reducing latency with DynamoDB / OLTP should be done with global tables (if global users), and use eventually consistent reads instead of strongly consistent reads
  DAX is for read heavy, not write heavy. 
  User data features - run during boot cycle when first launched, and are executed with root user priv. 
  Pass through doesn't terminate instances/connections so it doesn't reduce load. 
  cloudformation reference = !ref 
  access key id / secret key only used by AWS CLI, other services use commands like get-login
  
  Youtube video Review notes(5:36:00):
  Elastic Beanstalk-
    - PaaS - platform as a service (not recommended for large production loads)
    - Powered by cloudformation 
    - EC2 instance preconfig
    - in place and blue/green
    - dockerized env
    - supported langs: ruby, python, php, tomcat, nodejs 
    - eb it's self is free, but services cost money
    - don't need to worry about underlying infrastructure
   Deployment Policies
    - All at once
      - fastest dangerous
      - deploy new app to all instances, out of service while deploying, comes up with new stuff
    - Rolling 
     - deploys new app a few at a time, takes a batch out, reattaches 
    - Rolling with additional batch
     - spin up new service, with new app, kill old apps
     - never has reduced capacity
    - Immutable
     - safest, might be expensive
     - new asg, deploy the updated version of the app to new EC2, point the ELB to the new ASG, then term the old one
  Web vs Worker
  - web(load balanced env): 
    - creates an ASG (auto scaling group)
    - creates and ELB (elastic load balancer)
    - designed to scale
  - Single Instance Env
    - uses an ASg set to one, no ELB, public IP
    - cannot do rolling / rolling with batch deployments
  - Worker:
   - creates ASG
   - SQS
   - Sqsd daemon on EC2
   - Creates cloudwatch alarms
  Configuration files
   - options, server config(can put commands that run before setup here), custom resources
   - .ebextensions
   - .config
  Environment manifest
   - env.yml
   CLI 
   - eb init (sets up default)
   - eb create first env
   - status, health, events, logs, config, deploy, terminate
   - eb open opens in browser
  Custom images
  - you can specify an AMI instead of the standard
  - describe-platform-version
  Database
  - inside 
    - generally for dev
    - when EB env is terminated the db will also be terminated 
  - outside
    - for prod
    - RDS sep from EB
    - when EB env is terminated, db will remain
    
 Fargate
 - can create empty ECS(elastic container service) cluster, then launch task as fargat
 - don't have to provison containers
 - define memory and vCPU
 - add containers and allocate memory and vCPU
 - choose VPC and submet
 - apply security group, IAM to TASK 
 - cold start
 - runs as long as you want
 - up to 30GB of memory
 - provide your own containers
 - more manual labour
 
 X-Ray
 - What is mirco-service architecture? - ach/org approach to soft dev where softwarte is composed of small independent service that communicate over well defined APIs
 - What is distributed tracing? method used to rpfoile and monitor apps, especially those with microservices, pinpoints failures and what causes poor performance.
 - not exactly performance monitoring, but falls under that umbrella 
 - console has visualization 
 - api is behind a daemon
 - there are x-ray sdks for language - interceptors, client handlers, http client
 - aws sdk and cli
 - Instrumenting - ability to monitor or measure the level of a product's performance, errors, and to write trace information
 - Daemon makes JSON segment documents to the process / queue - acts as a buffer for the api
 - it's installed already on serverless (lambda elastic beanstalk)
 - Concepts
  - segemnts = data from services, contains host, request, response, the work done, issues that occur
  - subsegments = granular timing information and details about downstream calls that your app made to fulfill the original request. additonal details too. Need to include sdk
  - traces = groups segments that have a common request, adds a trace id header
  - sampling = doesn't store every trace, this keeps the cost low.
  - filter expressions = narrow down specific paths/users 
  - groups = assign filter expression to a group so its gets its own service graph, trace, and cloudwatch. if you update the group, it won't retro the data

  - Annotations and Metadata - adds to the segment document 
    - ann = indexed, key-value, up to 50
    - key = UNIDEXED, key value, no limit
  - service graph = the client, front-end, and backend services helps with bottlenecks/lactency/errors
    
 ACM 
 - amazon cert manager
 - ssl/tls
 - public, private (400 a month)
 - multiple subdomains, *
 - terminating ssl at LB
 - ssl end to end, complicated, but better 
 
 Route 53
 - DNS
 - Record sets domains/subdomains
 - Alias lets us select direct aws resources instead of ips
 - routing policies (versioning)
   - simple
     - default
     - 1 record, multiple IP
     - random
   - weighted
     - splits up traffic based on different weights
     - good for testing featurs
   - latency based 
     - lowest network latency for your end user
     - requires a latency resource record to be set for resource that hosts your app
   - failover
     - active/passive setups
     - auto health-checks, if fails goes to secondary location
   - Geolocation
     - based on geographic location
   - Geoproximity
    - have to use traffic flow to build
    - use regions then create bias/boundaries 
   - Multi-value
     - same as simple, but with health checks
  - Health checks
   - every 30s by default
   - init a failover
   - chains
  - resolver
   - .2 resolver routes DNS queries between your VPCs and network
   - for hybrid envs
   
SDK/CLI 
- cloud9

KMS
- create, control, rotate encrpytion keys
- multi-tenant Hardware Security Module (HSM)
- cloud trail to audit access history
- cloud HSM is single tenant, stricter compliance
- customer master key
- aws kms
  - create0key
  - encrypt
  - decrypt
  - re-encrypt
  - enable-key-rotation (only for symmetric) 
 - doesn't store data keys
 
Cognito 
 - web identity federation
  - exchange identity and security info between an identity provider and an app
 - Identity Provider
  - something that provides a log in (saml, facebook)
 - user pools
  - allows users to sign in directly
  - JWTs to persist auth
 - identity pools
   - actual mechanism that authorizies access to services
 - Sync
   - SNS to sync user data and preferences accros user devices
  
 SNS
  - simple notification service
  - all stuff stored accross multiple AZs
  - only plain emails, if fancy emails needed, need SES
  - topics
     - logical access point, communication channel
     - allows you to group subscriptions together
     - able to deliver to multiple protocols
  - subscriptions
    - created to topics
    - only one protocol and one topic
  - Application as subscriber
    - send push notification messages directly to apps via mobile devices
  - publish/subscribe = messaging systems. doesn't send to end user, sends to bus, the groups, then the subs subscribe to groups
  - managed pub/sub messaging, decouples distributed systems and serverless apps
  - pub push to SNS topic
  - sub subsribed to have events to pushed to them
    
SQS
- simple queue system
- used to provide async communication and decouple processes via messages / events
- producer and consumer
- not real time
- not a stream
- application integration via aws sdk
- pull based
- default vis is 30 seconds

Kinesis
- collection, processing, and anlyzing streaming data
- real time
- data streams
  - 24 hr default persisant 
  - producers (make data)
  - shards
  - consumers (use data)
 - Firehose
  - producers
  - transform/compress/secure
  - immediately disappears
  - one consumer
  - only pay for what you consume
 - video streams
   - from camera
   - secures and retains
   - consumers / ML
 - data analytics
  - pass firehose or data streams as a an input and an output to do real time analytics. expensive   

SSM parameter store
- store data (passwords, license codes)
- creates hierarchies by using forwards slashes
- can't revert advanced to standard
- policies
  - making you update passwords
  - assign multiple policies    

Secerts manager
- db creds
- can manage other db too
- can manage other secrets in a key/value store
- enforees encrpytion at-rest
- expensive than store
- cloud trail
- Automatic rotation
- describe secret - version and access and such
- get-secert-value

Dynamo DB
- document no sql database
- not relation, doesn't use sql
- key value store
- fully maaged
- durable
- built-in secury
- eventual consistent reads (default), possible inconsistent, but faster
- strongly consistent reads, consistent, slower
- read capacity units
- write capacity
- items = rows
- attributes collumns
- keys = id
- have to set a primary key, can't be reset 
- only have partition key, internal hash function to decide where data gets partitioned
- should try to divide data evenly
- composite keys (partition and sort key) has to be unique in the comp. still is hashed, but is grouping data closer together
- values = data
- no date type in dynamo
- Partition - allocation of storage for a table, auto-created 
- for every 10GB, when you exceed the RCUs or the WCUS
- each partition has a max of 3000 RCUS, 1000WCUs
- Query
  - FIND ITEMS IN A TABLE BASED ON PRIMARY KE VALUES, ANY TABLE, OR SECONDARY INDEX THAT HAS A COMPOSITE id
  - eventually consistent
- Scan
  - through all items, return one or more items through filters
  - returns everything, so can be slow, use a lot of resources
- Provisioned throughput capacity max about of capacity or write per second 
- if you go beyond capacity, it will throw erros
- On-demand capacity, pay per request, good for new tables, unpredictable loads, default limits: 40,000 RCUs/WCUs. can be expensive 
- Calculating reads
  - one strongly consistent read pper second or two eventually consistent reada per seconds for an item 4kb in size
  - strong: round up to 4, divided by 4, times by number of reads
  - eventual: round up to 4, divide by 4, times by number of reads, divide by 2, round to nearest whole number
- Calculating writes 
 - one write per second, per an item up to 1kb
 - round data up to 1, times by number of writes
- Global tables
  - mutli0-region
  - KMS CMK
  - enable streams
  - steam type of new and old imaage      
 - Transaction 
   - represents a change that will occur to the database, transactions are ACID
   - will rollback as if the database changes never occurred. 
   - all or nothing, across table
   - transactWriteItems
   - TransactGetItems 
   - perpars, and commits 
   - conditionalcheck 
 - TTL, allows items to expire, good for temporary continous data
 - Streams capturs every modification to data items so you can react to those changes


Sample question review:
  
White Paper Review:
  Architecting for the cloud: aws best practives
  Practicing continous integration and continuous delivery on AWS acceleration software delivery with devops
  Blue/Green deployments on AWS
  Running containerized microservices on AWS 
  