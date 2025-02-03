# RDS

- relational database service
- managed aws service
    - Advantages:
      - Automated provisioning
      - OS patching
      - Montioring
      - Read replicas
      - Scaling
      - Auto backups
    - Disadvatages:
      - can't ssh into it
  - Can make single AZ into multi AZ as a setting, doesn't need to turn off the DB
   
- stuff like postgres
- Aurora

Storage Auto Scaling
- set max

 Read replicas versus multi az
 Read replicas
- up to 15
- cross AZ, within or region
- these are async (eventually consisent)

  Multi
  - failover
  - sync
  - not for replicas
Can use read replicas for recovery

Aurora
- made for cloud
- 15 read replicias
- self healing
- reader endpoints
- writer endpoints

- RDS proxies
- Elasticache
      - not just something you can add on in the end
      - Cache evictions
      - Write through has longer writes but reads are quick
  - You can not create encrypted Read Replicas from an unencrypted RDS DB instance.
