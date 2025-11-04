#flashcards #aws

status:: 
count:: 29
[[Flashcards]]



<!-- Card Start -->

### Front

** Amazon QuickSight** 
### Back

Amazon QuickSight is a cloud-native, fully managed business intelligence (BI) service that enables organizations to create interactive dashboards, visualize data, and gain insights through machine learning capabilities.


<!-- Card End -->

<!-- Card Start -->

### Front

** S3 Express One Zone** Use cases
### Back

- Machine learning and artificial intelligence training
- Interactive data analytics 
- High performance computing (HPC)
- Data streaming
- Real-time advertising
- Media content workloads


<!-- Card End -->

# AWS EC2 Instance Connect

<!-- Card Start -->


### Front 

What is AWS EC2 Instance Connect?

### Back

AWS EC2 Instance Connect is a simple and secure way to connect to your Amazon EC2 instances using Secure Shell (SSH). It provides:

- Browser-based SSH access
- No need to manage SSH keys
- Integration with IAM for access control
- Support for Linux-based EC2 instances

<!-- Card End -->

<!-- Card Start -->

### Front

What are the main benefits of using EC2 Instance Connect?

### Back

The main benefits of EC2 Instance Connect include:

1. **Enhanced security**: No need to store or manage SSH keys
2. **Simplified access**: Connect directly from the AWS Management Console
3. **Fine-grained control**: Use IAM policies to manage access
4. **Audit trail**: All connection attempts are logged in AWS CloudTrail
5. **No additional cost**: Free feature included with EC2

<!-- Card End -->

<!-- Card Start -->

### Front

How does EC2 Instance Connect work?

### Back

EC2 Instance Connect works as follows:

1. User initiates a connection request
2. AWS generates a one-time SSH key pair
3. The public key is pushed to the instance metadata
4. The private key is used to establish the SSH connection
5. The key pair is automatically deleted after use

This process ensures secure, temporary access without long-term key management.

<!-- Card End -->

<!-- Card Start -->

### Front

What are the prerequisites for using EC2 Instance Connect?

### Back

Prerequisites for using EC2 Instance Connect:

1. EC2 instance running a supported Amazon Linux or Ubuntu AMI
2. Instance in a VPC with internet access (or VPC endpoints for EC2 and EC2 Instance Connect)
3. Security group allowing inbound traffic on port 22 (SSH)
4. IAM permissions to use EC2 Instance Connect
5. EC2 Instance Connect CLI (optional, for command-line access)

<!-- Card End -->

<!-- Card Start -->

### Front

What are the security best practices for EC2 Instance Connect?

### Back

Security best practices for EC2 Instance Connect:

1. Use IAM policies to restrict access to specific instances or users
2. Enable AWS CloudTrail to audit connection attempts
3. Use VPC endpoints to access EC2 Instance Connect without internet
4. Regularly review and update security group rules
5. Implement the principle of least privilege for IAM permissions
6. Use Multi-Factor Authentication (MFA) for IAM users
7. Monitor and analyze EC2 Instance Connect usage patterns

<!-- Card End -->

<!-- Card Start -->

### Front 

How does EC2 Instance Connect compare to Systems Manager Session Manager?

### Back

EC2 Instance Connect vs Systems Manager Session Manager:

| Feature | EC2 Instance Connect | Session Manager |
|---------|----------------------|-----------------|
| Protocol | SSH only | Multiple (SSH, RDP, CLI) |
| OS Support | Linux only | Linux, Windows, macOS |
| Bastion Host | Not required | Not required |
| Logging | CloudTrail | CloudTrail, S3, CloudWatch Logs |
| Port 22 | Required | Not required |
| IAM Integration | Yes | Yes |
| Additional Cost | No | No (but may incur data transfer costs) |

Choose based on specific requirements and use cases.

There many nuanced differences between these services but the basic idea is that EC2 Instance Connect allows for a convenient and secure native SSH connection using short-lived keys while Session Manager permits an SSH connection tunneled over a proxy connection.

<!-- Card End -->

<!-- Card Start -->

### Front

What are the limitations of EC2 Instance Connect?

### Back

Limitations of EC2 Instance Connect:

1. Only supports Linux-based instances (not Windows)
2. Requires internet access or VPC endpoints
3. Limited to SSH protocol
4. Not available for all instance types or regions
5. Requires specific AMIs or manual configuration
6. No support for custom SSH key management
7. May not be suitable for compliance requirements that mandate long-term key storage
8. Cannot be used with instances in EC2-Classic

Consider these limitations when deciding on remote access solutions.

<!-- Card End -->
## Questions

<!-- Card Start -->

### Front

What are some open-source alternatives to AWS Kinesis Data Streams?

### Back

Several open-source alternatives to AWS Kinesis Data Streams include:

1. **Apache Kafka**: A distributed streaming platform for high-throughput, fault-tolerant real-time data feeds.
2. **Apache Flink**: A stream processing framework for distributed, high-performing applications.
3. **Apache Storm**: A real-time computation system for processing large volumes of data.
4. **Spark Streaming**: Part of Apache Spark, it enables scalable, high-throughput stream processing.
5. **Apache NiFi**: A platform for automating data flow between software systems.

These tools offer similar capabilities for real-time data streaming and processing. 

<!-- Card End -->


<!-- Card Start -->

### Front

What are the main pricing tiers for AWS Support plans?

### Back

AWS offers four main support pricing tiers:

1. **Developer**: Minimum $29/month or 3% of monthly AWS charges
2. **Business**: Minimum $100/month or tiered percentage (10% for first $0-$10K, 7% for $10K-$80K, 5% for $80K-$250K, 3% over $250K)
3. **Enterprise On-Ramp**: Minimum $5,500/month or 10% of monthly AWS charges
4. **Enterprise**: Minimum $15,000/month or tiered percentage (10% for first $0-$150K, 7% for $150K-$500K, 5% for $500K-$1M, 3% over $1M)

Charges are based on the higher of the minimum or calculated percentage[1][7].

<!-- Card End -->

<!-- Card Start -->

### Front

How is the Developer Support plan fee calculated?

### Back

The Developer Support plan fee is calculated as follows:

- Minimum charge: $29/month
- If monthly AWS charges exceed $967 (3% of which is more than $29):
  - 3% of total monthly AWS charges

Example:
For $2,000 in monthly AWS charges:
$2,000 x 3% = $60

The higher amount ($60) would be charged as the support fee[5][7].

<!-- Card End -->

<!-- Card Start -->

## Enterprise Support Plan Benefits
### Front 

What are the key benefits of the Enterprise Support plan?

### Back

The Enterprise Support plan offers:

1. All features of Business Support
2. Dedicated Technical Account Manager (TAM)
3. Concierge Support Team
4. Support for use case reviews
5. Architectural guidance
6. Custom training options
7. Option to consolidate support across multiple AWS accounts within an organization
8. Simplified billing with a single invoice for the entire organization

Minimum fee: $15,000 per month (excludes additional AWS service usage charges)[2][7].

<!-- Card End -->


<!-- Card Start -->

## operational excellence
### Front 

What are the five design principles for operational excellence

### Back

 There are five design principles for operational excellence in the cloud: 
 
 - Perform operations as code 
 - Make frequent, small, reversible changes 
 - Refine operations procedures frequently 
 - Anticipate failure 
 - Learn from all operational failures

<!-- Card End -->

## AMI 

<!-- Card Start -->

### Front

What is an Amazon Machine Image (AMI)?
### Back

An Amazon Machine Image (AMI) is:

- A template for creating virtual servers (EC2 instances) in AWS
- Contains a pre-configured operating system and software stack
- Specific to region, OS, processor architecture, and virtualization type
- Used to launch multiple instances with the same configuration
- Can be created, acquired, or purchased from AWS Marketplace

AMIs include:
- A root volume template (OS, applications, etc.)
- Launch permissions
- Block device mapping for attached volumes

[1][5][7]

<!-- Card End -->

<!-- Card Start -->

### Front

What are the Types and Sources of AMIs
### Back

AMI types include:

1. Public AMIs: Provided by AWS, free to use
2. Paid AMIs: Available on AWS Marketplace, involve fees
3. Shared AMIs: Created and shared by other AWS users
4. Custom AMIs: Created by users for specific requirements

Sources of AMIs:
- AWS-provided
- AWS Marketplace
- Community AMIs
- Self-created custom AMIs

[2][8]

<!-- Card End -->

<!-- Card Start -->

### Front

Benefits of Using AMIs
### Back

Key benefits of using Amazon Machine Images:

1. Speed and efficiency in deployment
2. Consistency across multiple instances
3. Pre-configured software and permissions
4. Cost-effective scaling
5. Flexibility in OS and service options
6. Simplified software procurement (via AWS Marketplace)
7. Centralized policy enforcement
8. Version control for easy revision management
9. Integration with AWS services (e.g., Resource Access Manager, Organizations)
10. Reduced manual configuration and potential errors

[1][2]

<!-- Card End -->

<!-- Card Start -->

### Front

Creating a Custom AMI
### Back

Steps to create a custom AMI from an EC2 instance:

1. In AWS Management Console, go to EC2 Instances
2. Right-click the desired instance
3. Select "Create Image"
4. Provide a name and description for the AMI
5. Configure additional options if needed
6. Click "Create Image"
7. AWS will create a snapshot and register the AMI
8. The new AMI will appear in the AMIs list (may need to refresh)

Note: Creating an AMI may briefly stop the instance unless "No reboot" option is selected

[4][6]

<!-- Card End -->

## ETL

<!-- Card Start -->

### Front 
What is ETL?
 
### Back
 Extract, transform, and load (ETL) is the process of combining data from multiple sources into a large, central repository called a data warehouse. ETL uses a set of business rules to clean and organize raw data and prepare it for [storage](https://aws.amazon.com/what-is/cloud-storage/), [data analytics](https://aws.amazon.com/what-is/data-analytics/), and [machine learning (ML)](https://aws.amazon.com/what-is/machine-learning/). You can address specific business intelligence needs through data analytics (such as predicting the outcome of business decisions, generating reports and dashboards, reducing operational inefficiency, and more).

<!-- Card End -->

 

<!-- Card Start -->

### Front 

 Difference between data lake and data Warehouse
### Back
 
**Data warehouses**

A [data warehouse](https://aws.amazon.com/what-is/data-warehouse/) is a central repository that can store multiple databases. Within each database, you can organize your data into tables and columns that describe the data types in the table. The data warehouse software works across multiple types of storage hardware—such as solid state drives (SSDs), hard drives, and other cloud storage—to optimize your data processing.

**Data lakes**

With a [data lake](https://aws.amazon.com/what-is/data-lake/), you can store your structured and unstructured data in one centralized repository and at any scale. You can store data as is without having to first structure it based on questions you might have in the future. Data lakes also allow you to run different types of analytics on your data, like SQL queries, big data analytics, full-text search, real-time analytics, and machine learning (ML) to guide better decisions.

<!-- Card End -->

## Glue

<!-- Card Start -->

### Front 

What does ETL stand for and what is its purpose?

### Back

ETL stands for Extract, Transform, Load. It is a process used to:

- Move data from various sources to a unified repository
- Prepare data for analysis and business intelligence
- Consolidate data from multiple databases into a single repository
- Ensure data is properly formatted and qualified for analysis

ETL enables businesses to create a single source of truth for enterprise data, ensuring consistency and up-to-date information[1].

<!-- Card End -->

<!-- Card Start -->

### Front ETL Process Steps

What are the three main steps in the ETL process?

### Back

The three main steps in the ETL process are:

1. **Extract**: Pull raw data from multiple sources (e.g., CRM, ERP, IoT sensors)
2. **Transform**: Update data to match organizational needs and storage requirements
   - Standardize data types
   - Cleanse and resolve inconsistencies
   - Apply rules and functions
3. **Load**: Deliver and secure data for sharing within the organization

This process ensures data is ready for analysis and business intelligence purposes[1].

<!-- Card End -->

<!-- Card Start -->

### Front AWS Glue Overview

What is AWS Glue and what are its main features?

### Back

AWS Glue is a serverless data integration service that offers:

- Data discovery and organization
- Data transformation and preparation
- Building and monitoring of data pipelines
- Automatic ETL code generation
- Integration with other AWS services
- Support for various data sources and formats

AWS Glue simplifies the process of extracting, transforming, and loading data for analytics and data warehousing[2][6].

<!-- Card End -->

<!-- Card Start -->

### Front AWS Glue Benefits

What are the key advantages of using AWS Glue?

### Back

Key benefits of AWS Glue include:

1. Serverless architecture (no infrastructure management)
2. Automatic scaling based on data volume and complexity
3. Pay-only-for-what-you-use pricing model
4. Integration with other AWS services
5. Automated ETL code generation
6. Support for multiple data sources and formats
7. Built-in job scheduling and monitoring
8. Reduced time for data analysis
9. Collaboration features for teams[4][6][8]

<!-- Card End -->

<!-- Card Start -->

### Front AWS Glue Data Catalog

What is the AWS Glue Data Catalog and its purpose?

### Back

The AWS Glue Data Catalog is:

- A centralized metadata repository
- Used to store and manage information about data sources and stores
- Helps in unifying and searching across multiple data stores
- Allows for automatic data discovery using crawlers
- Enables schema management and permission control
- Increases data visibility across the organization

It serves as a foundation for data governance and discovery in AWS Glue[2][8].

<!-- Card End -->

<!-- Card Start -->

### Front ETL vs ELT

How does ETL differ from ELT?

### Back

ETL (Extract, Transform, Load) and ELT (Extract, Load, Transform) differ in the order of operations:

- ETL: Data is transformed before loading into the destination
- ELT: Data is loaded into the destination before transformation

ELT is more common in cloud-based data warehouses due to their scalable processing capabilities. It allows for:

- Preloading of raw data
- More flexibility for data scientists
- Faster processing by leveraging modern data processing engines
- Reduced data movement[1]

<!-- Card End -->

<!-- Card Start -->

### Front AWS Glue ETL Jobs

How does AWS Glue handle ETL jobs?

### Back

AWS Glue handles ETL jobs by:

1. Automatically generating ETL code in Scala or Python
2. Providing both visual and code-based interfaces
3. Offering job scheduling based on events or time
4. Supporting on-demand job execution
5. Automating logging, monitoring, and alerting
6. Facilitating job restarts in case of failures
7. Enabling parallel processing for heavy workloads
8. Allowing customization of generated ETL scripts

This approach simplifies ETL processes and improves efficiency[4][6][8].

<!-- Card End -->

<!-- Card Start -->

### Front AWS Glue Limitations

What are some limitations of AWS Glue?

### Back

While AWS Glue offers many benefits, it has some limitations:

1. Limited control over the underlying infrastructure
2. Potential higher costs for large-scale, continuous processing
3. Learning curve for those new to AWS services
4. Less flexibility compared to custom-built ETL solutions
5. Dependency on AWS ecosystem
6. Potential performance issues with very complex transformations
7. Limited support for real-time streaming data processing

Consider these factors when deciding to use AWS Glue for your ETL needs[6][10].

<!-- Card End -->

<!-- Card Start -->

### Front ETL Tools

What are some popular ETL tools besides AWS Glue?

### Back

Popular ETL tools include:

1. Informatica PowerCenter
2. Talend
3. IBM DataStage
4. Microsoft SQL Server Integration Services (SSIS)
5. Oracle Data Integrator
6. Pentaho Data Integration
7. Apache NiFi
8. Stitch
9. Fivetran
10. Matillion

These tools offer various features for data extraction, transformation, and loading, catering to different organizational needs and technical requirements[1][3].

<!-- Card End -->

<!-- Card Start -->

### Front ETL Best Practices

What are some best practices for implementing ETL processes?

### Back

Best practices for ETL implementation include:

1. Clearly define data quality standards and rules
2. Implement data profiling and cleansing
3. Use incremental loading when possible
4. Optimize for performance (e.g., parallel processing)
5. Implement error handling and logging
6. Version control your ETL code
7. Schedule regular maintenance and updates
8. Monitor and alert on job failures
9. Document data lineage and transformations
10. Ensure compliance with data governance policies

Following these practices can improve the reliability and efficiency of your ETL processes[1][3][7].

<!-- Card End -->

## more

<!-- Card Start -->

### Front  
Which of the following are pillars of the AWS Well-Architected Framework? **(Choose two.**)

- A. High availability
- B. Performance efficiency
- C. Cost optimization
- D. Going global in minutes
- E. Continuous development
 
### Back

B. Performance efficiency 
C. Cost optimization

<!-- Card End -->

<!-- Card Start -->

### Front  
A company wants to migrate unstructured data to AWS. The data needs to be securely moved with inflight encryption and end-to-end data validation.  
  
Which AWS service will meet these requirements?

- A. AWS Application Migration Service
- B. Amazon Elastic File System (Amazon EFS)
- C. AWS DataSync
- D. AWS Migration Hub
 
### Back

C. AWS DataSync

AWS DataSync is a service designed for securely transferring large amounts of data between on-premises storage and Amazon S3, Amazon EFS, or Amazon FSx for Windows File Server. It supports in-flight encryption and end-to-end data validation during the transfer process. In the context of the question, AWS DataSync is a suitable choice for securely moving unstructured data to AWS while ensuring encryption and data integrity throughout the migration process. Therefore, option C, AWS DataSync, would meet the specified requirements.

<!-- Card End -->