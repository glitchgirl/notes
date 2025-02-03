# EC2 

## Types
- General purpose
- Compute optimized
- Memory optimized
- Accelrated computing
- Storage optimized

Set up billing before you start making things


# EBS 
- Elastic Block Store - these persist data even after their termination
- Can only be mounted to one instance at a time (at the CCP level), but you can link two or more volumes to an EC2 instance. You can also not attach it to an EC2 instance
- Uses the network to communicate
- Can be detached and then attached to another EC2
- Locked to an AZ
- You have to provison capacity
- Delete on termination attribute
- Any non root volume is not deleted by default, but the root is.
- Snapshot archive - takes time to restore
- Can use snapshots to copy them to new AZ
- Recycle bin 

## EBS Volume Types
- gp2/3 - general purpose
- io1/2 - highest performance for low latency high through put, can be multi attached
- stl - low cost frequently accessed throughput intensive workloads - can't be boot volumes
- scl - lowest cost for less frequently accessed workloads - can't be boot volumes
- provisioned IOPS
- can increase PIOPS independently from storage size
- Nitro for more IOPS

# EFS
- Elastic File System
- Managed NFS that can be mounted on many EC2
- Can be multi AZ
- This can be good for things like CMS
- Can only be ran on unix systems
- File system is pay per use
- Scale
- Performance mode: general versus max i/o
- Throughput mode: bursting versus provisioned versus elastic
- Storage Tiers
- Use a lifecycle policy to move things to lower cost storage
- Standard is better for prod (multi AZ), but backed up in one zone is fine for dev
- 
