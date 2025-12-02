#flashcards #aws


status:: 
count:: 
[[Flashcards]]

<!-- Card Start -->

### Front 

What is Amazon EBS?

### Back

Amazon Elastic Block Store (EBS) is:
- A fully managed persistent block storage service for EC2 instances
- Provides virtual hard drives that can be attached to EC2 instances
- Offers persistent storage that remains even after EC2 instance termination
- Designed for high availability and durability within an Availability Zone

<!-- Card End -->

<!-- Card Start -->

### Front 

EBS Volume Types

### Back

Amazon EBS offers six volume types:
1. General Purpose SSD (gp2 and gp3)
2. Provisioned IOPS SSD (io1 and io2)
3. Throughput Optimized HDD (st1)
4. Cold HDD (sc1)

Each type is optimized for specific use cases and priced accordingly[3].

<!-- Card End -->

<!-- Card Start -->

### Front 

What are IOPS?

### Back

IOPS (Input/Output Operations Per Second):
- A unit of measure for disk performance
- Represents the number of read/write operations per second
- Maximum size of an IOP:
  - 256 KiB for SSD volumes
  - 1 MiB for HDD volumes
- 1 GiB of storage typically provides 3 IOPS
- Used to measure and provision performance for EBS volumes[2][10]

<!-- Card End -->

<!-- Card Start -->

### Front 

EBS Key Features

### Back

Key features of Amazon EBS:
1. Elasticity: Dynamically resize volumes
2. Snapshots: Point-in-time backups
3. Availability and Durability: Replication within Availability Zone
4. Multiple volume types for different use cases
5. Scalability: Adjust capacity and performance
6. Backup and recovery options
7. Integration with other AWS services[1][5]

<!-- Card End -->

<!-- Card Start -->

### Front 

EBS Snapshots

### Back

EBS Snapshots:
- Point-in-time copies of EBS volumes
- Used for disaster recovery, data migration, and backup compliance
- Stored incrementally (only changed blocks)
- Can be copied across regions and accounts
- Integrate with Amazon Data Lifecycle Manager for automated management
- Enable fast data restoration with Fast Snapshot Restore feature[4]

<!-- Card End -->

<!-- Card Start -->

### Front 

EBS Performance Optimization

### Back

To optimize EBS Provisioned IOPS performance:
1. Ensure sufficient I/O requests (monitor VolumeQueueLength)
2. Use block sizes of 256 KB or less
3. Read blocks at least once before expecting full performance
4. Avoid pending EBS snapshots
5. Keep total read/write operations below 128MB/s per volume
6. Aim for VolumeQueueLength of 1 per 100 IOPS[6]

<!-- Card End -->

<!-- Card Start -->

### Front 

EBS Use Cases

### Back

Common use cases for Amazon EBS:
1. High-performance databases
2. Boot volumes for EC2 instances
3. Data storage for applications requiring consistent I/O performance
4. Big data analytics workloads
5. Backup and disaster recovery
6. Development and test environments
7. Enterprise applications requiring persistent storage

<!-- Card End -->

<!-- Card Start -->

### Front

EBS Encryption

### Back

EBS Encryption features:
- Data at rest encryption for volumes, snapshots, and instances
- Uses AWS Key Management Service (KMS) for key management
- Minimal impact on latency
- No additional cost for using encryption
- Simplifies compliance and data protection requirements
- Can be enabled by default for new EBS volumes and snapshots[9]

<!-- Card End -->

<!-- Card Start -->

### Front 

EBS vs Instance Store

### Back

EBS compared to EC2 Instance Store:
- EBS: Persistent storage, separate from instance lifecycle
- Instance Store: Ephemeral storage, tied to instance lifecycle
- EBS: Survives instance stops/terminations
- Instance Store: Data lost on instance stop/termination
- EBS: Can be detached and reattached to different instances
- Instance Store: Physically attached to the host computer

<!-- Card End -->

<!-- Card Start -->

### Front 

EBS Multi-Attach

### Back

EBS Multi-Attach:
- Allows attaching a single EBS volume to multiple EC2 instances
- Supported only for Provisioned IOPS SSD (io1/io2) volumes
- Instances must be in the same Availability Zone
- Useful for clustered applications requiring shared storage
- Requires cluster-aware file systems or applications

<!-- Card End -->

<!-- Card Start -->

### Front 

EBS Pricing Model

### Back

EBS pricing considerations:
- Pay for provisioned storage capacity
- Additional charges for Provisioned IOPS (if applicable)
- Snapshot storage charged based on actual data stored
- Data transfer fees for cross-region operations
- No charge for data transfer between EBS and EC2 in same AZ
- Pricing varies by region and volume type

<!-- Card End -->

<!-- Card Start -->

### Front

EBS Monitoring

### Back

Monitoring EBS volumes:
- Use Amazon CloudWatch for performance metrics
- Key metrics: VolumeReadOps, VolumeWriteOps, VolumeQueueLength
- Set up CloudWatch alarms for performance thresholds
- Use AWS Trusted Advisor for optimization recommendations
- Enable EBS-optimized instances for dedicated throughput
- Monitor I/O characteristics to choose appropriate volume types[10]

<!-- Card End -->

<!-- Card Start -->

### Front 

EBS Data Lifecycle Management

### Back

Managing EBS data lifecycle:
1. Use Amazon Data Lifecycle Manager (DLM) for automated snapshots
2. Create snapshot schedules based on tags or time intervals
3. Implement retention policies for snapshots
4. Use cross-region copy for disaster recovery
5. Automate snapshot deletion to manage costs
6. Integrate with AWS Backup for centralized backup management

<!-- Card End -->

<!-- Card Start -->

### Front EBS 

EBS Best Practices

### Back

Best practices for using EBS:
1. Right-size volumes based on application needs
2. Use appropriate volume types for workload characteristics
3. Implement regular snapshot backups
4. Enable encryption for sensitive data
5. Use EBS-optimized instances for consistent performance
6. Monitor and adjust IOPS and throughput as needed
7. Implement proper IAM policies for access control
8. Use tags for better resource management and cost allocation

<!-- Card End -->

Citations:
[1] https://docs.aws.amazon.com/ebs/latest/userguide/what-is-ebs.html
[2] https://handbook.vantage.sh/aws/concepts/io-operations/
[3] https://www.kerno.io/aws/ebs
[4] https://aws.amazon.com/ebs/snapshots/
[5] https://www.simplyblock.io/glossary/what-is-amazon-ebs/
[6] https://www.datadoghq.com/blog/aws-ebs-provisioned-iops-getting-optimal-performance/
[7] https://en.wikipedia.org/wiki/Amazon_Elastic_Block_Store
[8] https://bluexp.netapp.com/blog/aws-snapshots-a-complete-introduction-to-amazon-ebs-snapshots
[9] https://data-flair.training/blogs/aws-ebs/
[10] https://docs.aws.amazon.com/ebs/latest/userguide/ebs-io-characteristics.html
[11] https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volumes.html
[12] https://tutorialsdojo.com/streamlining-ebs-snapshot-management-with-amazon-data-lifecycle-manager-automation/
[13] https://www.amazonaws.cn/en/ebs/features/