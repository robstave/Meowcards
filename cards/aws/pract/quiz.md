#flashcards #aws

status:: 
count:: 
[[Flashcards]]

<!-- Card Start -->
### Front 

 A user has an AWS account with a Business-level AWS Support plan and needs assistance with handling a production service disruption.  
  
Which action should the user take?

- A. Contact the dedicated AWS technical account manager (TAM).
- B. Contact the dedicated AWS Concierge Support team.
- C. Open a business-critical system down support case.
- D. Open a production system down support case.
### Back

 D. As I've checked with document the highest severity that Business-level AWS Support plan can open is "Production system down"

https://aws.amazon.com/premiumsupport/plans/

<!-- Card End --> 
 
<!-- Card Start -->
### Front 

Which of the following are AWS Cloud design principles? (Choose two.)

- A. Pay for compute resources in advance
- B. Make data driven decisions to determine cloud architectural design
- C. Emphasize manual processes to allow for changes
- D. Test systems at production scale
- E. Refine operational procedures infrequently

### Back

B. Make data driven decisions to determine cloud architectural design 
D. Test systems at production scale 

"Drive architectures using data: In the cloud, you can collect data on how your architectural choices affect the behavior of your workload. This lets you make fact-based decisions on how to improve your workload. Your cloud infrastructure is code, so you can use that data to inform your architecture choices and improvements over time." 

"Test systems at production scale: In the cloud, you can create a production-scale test environment on demand, complete your testing, and then decommission the resources. Because you only pay for the test environment when it's running, you can simulate your live environment for a fraction of the cost of testing on premises." 

https://wa.aws.amazon.com/wat.design_principles.wa-dp.en.html

<!-- Card End --> 
<!-- Card Start -->
### Front 

Which of the following are user authentication services managed by AWS? (Choose two.)

- A. Amazon Cognito
- B. AWS Lambda
- C. AWS License Manager
- D. AWS Identity and Access Management (1AM)
- E. AWS CodeStar

### Back

A. Amazon Cognito 
D. AWS Identity and Access Management (IAM) 

"Amazon Cognito helps you implement customer identity and access management (CIAM) into your web and mobile applications. You can quickly add user authentication and access control to your applications in minutes."

<!-- Card End --> 
<!-- Card Start -->
### Front 

A company is designing its AWS workloads so that components can be updated regularly and so that changes can be made in small, reversible increments.  
  
Which pillar of the AWS Well-Architected Framework does this design support?

- A. Security
- B. Performance efficiency
- C. Operational excellence
- D. Reliability

### Back

C. Operational Excellence

Operational excellence in the AWS Well-Architected Framework focuses on designing and operating workloads to deliver business value, with a strong emphasis on continuous improvement, responding to events, and automation. Making regular updates in small, reversible increments supports the goal of achieving operational excellence by promoting agility and efficiency in the development and deployment processes.

<!-- Card End --> 
<!-- Card Start -->
### Front 

Which actions can a system administrator take to connect to the EC2 instance? (Choose two.)

- A. Use Amazon EC2 Instance Connect.
- B. Use a Remote Desktop Protocol (RDP) connection.
- C. Use AWS Batch.
- D. Use AWS Systems Manager Session Manager.
- E. Use Amazon Connect.
### Back

A. Use Amazon EC2 Instance Connect. 
D. Use AWS Systems Manager Session Manager

There many nuanced differences between these services but the basic idea is that EC2 Instance Connect allows for a convenient and secure native SSH connection using short-lived keys while Session Manager permits an SSH connection tunneled over a proxy connection.

[discussion](https://repost.aws/questions/QUnV4R9EoeSdW0GT3cKBUR7w/what-is-the-difference-between-ec2-instance-connect-and-session-manager-ssh-connections)

<!-- Card End --> 
<!-- Card Start -->
### Front 

A company needs to analyze its AWS Cloud environment to determine whether the company is following security best practices. The company wants recommendations about how to close security gaps.  
  
Which AWS service should the company use to obtain these recommendations?

- A. AWS WAF
- B. AWS Systems Manager
- C. AWS Trusted Advisor
- D. AWS Shield
### Back

C **AWS Trusted Advisor**  

**AWS Trusted Advisor**   is an online tool that acts like a customized cloud expert, helping you to configure your resources to follow best practices. Trusted Advisor inspects your AWS environment to help close security gaps, and finds opportunities to save money, improve system performance, and increase reliability.
<!-- Card End --> 


<!-- Card Start -->

### Front 
A company is planning to migrate to the AWS Cloud. The company is conducting organizational transformation and wants to become more responsive to customer inquiries and feedback.  
  
Which task should the company perform to meet these requirements, according to the AWS Cloud Adoption Framework (AWS CAF)?

- A. Realign teams to focus on products and value streams.
- B. Create new value propositions with new products and services.
- C. Use a new data and analytics platform to create actionable insights.
- D. Migrate and modernize legacy infrastructure.
### Back

A. Realign teams to focus on products and value streams.

According to the AWS Cloud Adoption Framework (AWS CAF), an organization undergoing cloud migration should focus on optimizing people, processes, and technology to enhance customer responsiveness. The People Perspective of the AWS CAF emphasizes that aligning teams to focus on products and value streams is essential for increasing agility, reducing time-to-market, and improving customer responsiveness. By organizing teams around customer-focused products or services, the company can respond more effectively to customer inquiries and feedback.

so...C is something you want, but if your people are not ready for it, it aint happening


<!-- Card End --> 











<!-- Card Start -->

### Front 

### Back


<!-- Card End --> 

<!-- Card Start -->

### Front 

### Back


<!-- Card End --> 


<!-- Card Start -->

### Front 

### Back


<!-- Card End --> 


<!-- Card Start -->

### Front 

### Back


<!-- Card End --> 


<!-- Card Start -->

### Front 

### Back


<!-- Card End --> 


<!-- Card Start -->

### Front 

### Back


<!-- Card End --> 


<!-- Card Start -->

### Front 

### Back


<!-- Card End --> 


<!-- Card Start -->

### Front 

### Back


<!-- Card End --> 




#flashcards #aws 
file:: quiz2
status:: 
count:: 
[[Flashcards]]

site:www.examtopics.com "AWS Certified Cloud Practitioner"

https://www.examtopics.com/discussions/amazon/

## Stuff

<!-- Card Start -->

### Front 

A company wants to enhance security by launching a third-party ISP intrusion detection system from its AWS account.  
  
Which AWS service or resource should the company use to meet this requirement?

- A. AWS Security Hub
- B. AWS Marketplace
- C. AWS Quick Starts
- D. AWS Security Center
- 
### Back

B. AWS Marketplace   - Third party apps
 

<!-- Card End --> 
<!-- Card Start -->

### Front 
Which duties are the responsibility of a company that is using AWS Lambda? (Choose two.)  

- A. Security inside of code
- B. Selection of CPU resources
- C. Patching of operating system
- D. Writing and updating of code
- E. Security of underlying infrastructure

### Back

 A and D

A. **Security inside of code:** It is the company's responsibility to ensure the security of the code running within the Lambda functions. This includes implementing proper security measures, such as input validation, encryption, and access controls, to protect the code and the data it processes. 

D. **Writing and updating of code:** The company is responsible for developing and maintaining the code that runs within the Lambda functions. This involves writing the code, testing it, and making any necessary updates or modifications over time.


<!-- Card End --> 
<!-- Card Start -->
### Front 
A company is planning to replace its physical on-premises compute servers with AWS serverless compute services. The company wants to be able to take advantage of advanced technologies quickly after the migration.  
Which pillar of the AWS Well-Architected Framework does this plan represent?  

- A. Security
- B. Performance efficiency
- C. Operational excellence
- D. Reliability
### Back

 B **Performance efficiency**: 
 
 The performance efficiency pillar focuses on the efficient use of computing resources to meet requirements, and how to maintain efficiency as demand changes and technologies evolve. 
 
 **Operational Excellence:** The operational excellence pillar includes how your organization supports your business objectives, your ability to run workloads effectively, gain insight into their operations, and to continuously improve supporting processes and procedures to deliver business value. I understand why you could think it is C, but I believe the correct answer is B (key part: as demand changes and technologies evolve)

<!-- Card End -->
 
# Group 1

<!-- Card Start -->
### Front

Which AWS service is used to temporarily provide federated security credentials to access AWS resources?

- A. Amazon GuardDuty
- B. AWS Simple Token Service (AWS STS)
- C. AWS Secrets Manager
- D. AWS Certificate Manager

### Back

B) AWS Simple Token Service (AWS STS)

<!-- Card End -->


https://www.examtopics.com/discussions/amazon/view/106645-exam-aws-certified-cloud-practitioner-topic-1-question-703/

<!-- Card Start -->

### Front

A company has acquired several other companies. All the companies host their IT infrastructure in the AWS Cloud.  
  
Which AWS service should the acquiring company use to centralize the account management?

- A. AWS Systems Manager
- B. AWS Organizations
- C. AWS Security Hub
- D. Amazon Workspaces
### Back
B. AWS Organizations

AWS Organizations is an account management service that enables you to consolidate multiple AWS accounts into an organization that you create and centrally manage. AWS Organizations includes account management and consolidated billing capabilities that enable you to better meet the budgetary, security, and compliance needs of your business. As an administrator of an organization, you can create accounts in your organization and invite existing accounts to join the organization.


<!-- Card End -->
https://www.examtopics.com/discussions/amazon/view/96553-exam-aws-certified-cloud-practitioner-topic-1-question-378/


---
<!-- Card Start -->
### Front


A company wants to set up a secure network connection from on premises to the AWS Cloud within 1 week.  
  
Which solution will meet these requirements?

- A. AWS Direct Connect
- B. Amazon VPC
- C. AWS Site-to-Site VPN
- D. Edge location

### Back

C) AWS Site-to-Site VPN

The key word here is "1 week". The Direct Connect needs more times as it involves multiple parties and configurations...

<!-- Card End -->


<!-- Card Start -->
### Front

A company wants an Amazon S3 solution that provides access to object storage within single-digit milliseconds.  
  
Which solution will meet these requirements?

- A. S3 Express One Zone
- B. S3 Standard
- C. S3 Glacier Flexible Retrieval
- D. S3 Glacier Instant Retrieval
### Back
A
Amazon S3 Express One Zone is a high-performance, single-Availability Zone storage class purpose-built to deliver consistent single-digit millisecond data access for your most frequently accessed data and latency-sensitive applications. S3 Express One Zone delivers data access speed up to 10x faster and request costs up to 50% lower than S3 Standard. While you have always been able to choose a specific AWS Region to store your S3 data, with S3 Express One Zone you can select a specific AWS Availability Zone within an AWS Region to store your data.


<!-- Card End -->
<!-- Card Start -->
### Front

Which AWS service or feature enables users to block the incoming or outgoing traffic associated with specific IP addresses flowing through a VPC?

- A. Network ACLs
- B. Security groups
- C. AWS Identity and Access Management (IAM)
- D. AWS WAF

### Back

- A. Network ACLs

<!-- Card End -->
# Group pillars


<!-- Card Start -->

### Front

What is the AWS Well-Architected Framework?

### Back

The AWS Well-Architected Framework is a set of best practices for designing and operating reliable, secure, efficient, and cost-effective systems in the cloud. It consists of six pillars:

1. Operational Excellence
2. Security
3. Reliability
4. Performance Efficiency
5. Cost Optimization
6. Sustainability

It provides a consistent approach for customers and partners to evaluate architectures and implement scalable designs.

<!-- Card End -->

<!-- Card Start -->

### Front

What are the six pillars of the AWS Well-Architected Framework?

### Back

The six pillars of the AWS Well-Architected Framework are:

1. Operational Excellence
2. Security
3. Reliability
4. Performance Efficiency
5. Cost Optimization
6. Sustainability

Each pillar focuses on a specific set of best practices and design principles for cloud architecture.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of the Operational Excellence pillar?

### Back

The Operational Excellence pillar focuses on:

- Running and monitoring systems to deliver business value
- Continuously improving processes and procedures
- Automating changes to infrastructure and applications
- Defining and maintaining standards for operations
- Managing and automating changes through the use of version control

It aims to streamline operations and enhance the ability to run workloads effectively.

<!-- Card End -->

<!-- Card Start -->

### Front

What does the Security pillar of the AWS Well-Architected Framework address?

### Back

The Security pillar addresses:

- Protecting information, systems, and assets
- Implementing a strong identity foundation
- Enabling traceability
- Applying security at all layers
- Automating security best practices
- Protecting data in transit and at rest
- Preparing for security events

It focuses on ensuring the confidentiality, integrity, and availability of data and systems.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the focus of the Reliability pillar in the AWS Well-Architected Framework?

### Back

The Reliability pillar focuses on:

- Ensuring a workload performs its intended function correctly and consistently
- Recovering quickly from failures to meet business and customer demand
- Automatically recovering from infrastructure or service disruptions
- Scaling horizontally to increase aggregate system availability
- Managing change in automation

It aims to build systems that are resilient and can quickly recover from issues.

<!-- Card End -->

<!-- Card Start -->

### Front

What does the Performance Efficiency pillar emphasize?

### Back

The Performance Efficiency pillar emphasizes:

- Selecting the right resource types and sizes based on workload requirements
- Monitoring performance and making informed decisions to maintain efficiency
- Using serverless architectures to reduce the need for managing servers
- Experimenting more easily with different resource types
- Considering mechanical sympathy (understanding how cloud services are consumed)

It focuses on using computing resources efficiently to meet system requirements and maintain efficiency as demand changes.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the main goal of the Cost Optimization pillar?

### Back

The main goal of the Cost Optimization pillar is to:

- Avoid unnecessary costs
- Understand and control where money is being spent
- Select the most appropriate and right number of resource types
- Analyze spend over time
- Scaling to meet business needs without overspending

It aims to help organizations run systems to deliver business value at the lowest price point.

<!-- Card End -->

<!-- Card Start -->

### Front

What does the Sustainability pillar address in the AWS Well-Architected Framework?

### Back

The Sustainability pillar addresses:

- Understanding the impact of cloud services on the environment
- Selecting efficient hardware and software offerings
- Maximizing utilization of resources
- Reducing the downstream impact of cloud workloads
- Adopting practices that reduce energy consumption

It focuses on minimizing the environmental impacts of running cloud workloads.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the AWS Well-Architected Tool?

### Back

The AWS Well-Architected Tool is:

- A service provided at no additional cost in the AWS Management Console
- A mechanism for regularly evaluating workloads against current AWS best practices
- A tool that helps identify high-risk issues in your workloads
- A way to record improvements and track changes in your architectural decisions over time

It helps customers apply the principles of the Well-Architected Framework to their specific workloads.

<!-- Card End -->

<!-- Card Start -->

### Front

What are AWS Well-Architected Lenses?

### Back

AWS Well-Architected Lenses are:

- Extensions of the Well-Architected Framework
- Focused on specific industry or technology domains
- Provide additional best practices for particular types of workloads
- Include questions and guidance tailored to specific use cases

Examples include the Serverless Lens, Container Lens, and SaaS Lens.

<!-- Card End -->

<!-- Card Start -->

### Front

How does the AWS Well-Architected Framework help in cloud architecture design?

### Back

The AWS Well-Architected Framework helps in cloud architecture design by:

- Providing a consistent approach to evaluate architectures
- Offering design principles for each pillar to guide decision-making
- Helping identify and address potential issues in workload designs
- Encouraging continuous improvement of architectures
- Aligning architecture decisions with AWS best practices and latest innovations

It serves as a guide for building efficient, secure, and high-performing infrastructure for various applications and workloads.

<!-- Card End -->

<!-- Card Start -->

### Front

What are some benefits of using the AWS Well-Architected Framework?

### Back

Benefits of using the AWS Well-Architected Framework include:

- Improved overall quality of cloud architectures
- Reduced risk of critical issues in production
- Increased efficiency and cost-effectiveness of workloads
- Enhanced security and reliability of systems
- Better alignment with AWS best practices and latest innovations
- Consistent approach to evaluating and improving architectures
- Facilitation of important discussions about architectural decisions

It helps organizations build and maintain cloud systems that are secure, reliable, efficient, and cost-effective.

<!-- Card End -->
 
<!-- Card Start -->

### Front

What are the main categories of EC2 instance types?

### Back

EC2 instance types are grouped into categories based on their optimized use cases:

1. General purpose
2. Compute optimized
3. Memory optimized
4. Storage optimized
5. Accelerated computing
6. High-performance computing
7. Burstable performance (T instance family)

Each category is designed for specific workload requirements, offering different combinations of CPU, memory, storage, and networking capacity[1][7].

<!-- Card End -->

<!-- Card Start -->

### Front

How does EC2 provide elasticity?

### Back

EC2 offers elasticity through:

- Ability to scale computing capacity up or down quickly
- Option to commission thousands of server instances simultaneously
- Web service APIs that can automatically scale servers based on demand
- Rapid provisioning and de-provisioning of resources
- Pay-as-you-go model allowing flexible resource allocation

This elasticity enables businesses to adapt to changing workloads efficiently and cost-effectively[4][6].

<!-- Card End -->

<!-- Card Start -->

### Front

How does EC2 integrate with other AWS services?

### Back

EC2 seamlessly integrates with various AWS services, including:

- Amazon RDS for managed databases
- Amazon S3 for object storage
- Amazon DynamoDB for NoSQL databases
- Amazon SQS for message queuing
- Amazon EKS for container orchestration
- AWS IAM for access management
- Amazon VPC for network isolation

This integration allows for building comprehensive, end-to-end solutions in the cloud, enhancing overall functionality and efficiency[4].

<!-- Card End -->

<!-- Card Start -->

### Front

What are key considerations when selecting EC2 instance types?

### Back

When choosing EC2 instance types, consider:

1. CPU requirements (number of vCPUs, processor family)
2. Memory needs (RAM capacity)
3. Storage requirements (type, capacity, IOPS)
4. Network performance
5. GPU requirements (for accelerated computing)
6. Operating system compatibility
7. Region availability
8. Cost and pricing model (On-Demand, Reserved, Spot)

Use the EC2 instance type finder to match requirements with available options[3][8].

<!-- Card End -->

<!-- Card Start -->

### Front

How can you optimize costs with EC2?

### Back

To optimize EC2 costs:

1. Choose appropriate instance types for workloads
2. Utilize Auto Scaling to adjust capacity based on demand
3. Use Spot Instances for flexible, fault-tolerant applications
4. Leverage Reserved Instances for predictable workloads
5. Monitor and rightsize instances using AWS Cost Explorer
6. Implement proper tagging for cost allocation
7. Use EC2 Fleet for a mix of instance types and purchase options
8. Terminate unused or idle instances promptly

These strategies help maximize resource utilization and minimize unnecessary expenses[2][4].

<!-- Card End -->

# efs ebs s3 (15)


 Here are the 15 AWS storage-focused flashcards in the requested Markdown format:

<!-- Card Start -->

### Front

What type of AWS storage is best suited for persistent block storage for EC2 instances?

### Back

Amazon Elastic Block Store (EBS) provides persistent block storage for EC2 instances.

<!-- Card End --> <!-- Card Start -->

### Front

Which AWS storage service offers highly available object storage with scalability?

### Back

Amazon S3 (Simple Storage Service) provides highly available, scalable object storage.

<!-- Card End --> <!-- Card Start -->

### Front

What is the primary difference between EBS and S3?

### Back

EBS is block storage for EC2 instances, while S3 is object storage for scalable and accessible data.

<!-- Card End --> <!-- Card Start -->

### Front

Which AWS storage service allows for mounting a file system across multiple EC2 instances?

### Back

Amazon Elastic File System (EFS) allows you to mount a file system across multiple EC2 instances.

<!-- Card End --> <!-- Card Start -->

### Front

What type of storage would you use for data that needs high-speed access and low latency?

### Back

Amazon EBS provides high-speed access and low-latency block storage for EC2 instances.

<!-- Card End --> <!-- Card Start -->

### Front

Which storage service is best for storing large numbers of files with varying access patterns?

### Back

Amazon S3 is ideal for storing large numbers of files with different access patterns.

<!-- Card End --> <!-- Card Start -->

### Front

How does Amazon S3 ensure durability of your data?

### Back

Amazon S3 ensures durability by replicating data across multiple Availability Zones (AZs).

<!-- Card End --> <!-- Card Start -->

### Front

Which storage service supports NFS-based file systems?

### Back

Amazon EFS supports NFS-based file systems.

<!-- Card End --> <!-- Card Start -->

### Front

What is a key advantage of using Amazon EFS over EBS?

### Back

Amazon EFS can be mounted by multiple instances simultaneously, whereas EBS can only be attached to one instance at a time.

<!-- Card End --> <!-- Card Start -->

### Front

Which type of Amazon EBS volume provides the highest performance for I/O-intensive workloads?

### Back

Provisioned IOPS SSD (io2) volumes provide the highest performance for I/O-intensive workloads.

<!-- Card End --> <!-- Card Start -->

### Front

Which AWS storage service offers lifecycle policies to transition objects to different storage classes?

### Back

Amazon S3 offers lifecycle policies for transitioning objects to different storage classes (e.g., Standard, Infrequent Access, Glacier).

<!-- Card End --> <!-- Card Start -->

### Front

What is the benefit of Amazon S3 Intelligent-Tiering?

### Back

Amazon S3 Intelligent-Tiering automatically moves objects between storage classes based on access patterns to optimize costs.

<!-- Card End --> <!-- Card Start -->

### Front

Which Amazon storage service is best suited for storing backups of EC2 instances?

### Back

Amazon EBS Snapshots are ideal for backing up EC2 instances.

<!-- Card End --> <!-- Card Start -->

### Front

How can you access Amazon EFS from on-premises data centers?

### Back

You can access Amazon EFS from on-premises using AWS Direct Connect or a VPN.

<!-- Card End --> <!-- Card Start -->

### Front

What AWS service would you use for data archiving with long retrieval times?

### Back

Amazon S3 Glacier is ideal for data archiving with long retrieval times.

<!-- Card End -->


[#flashcards #aws

https://www.examtopics.com/discussions/amazon/view/147745-exam-aws-certified-cloud-practitioner-clf-c02-topic-1/

file::quizcards1
status:: 
count:: 
[[Flashcards]]

site:www.examtopics.com "AWS Certified Cloud Practitioner"

https://www.examtopics.com/discussions/amazon/>)


<!-- Card Start -->
### Front
Which responsibility belongs to AWS when a company hosts its databases on Amazon EC2 instances?

- A. Database backups
- B. Database software patches
- C. Operating system patches
- D. Operating system installations

### Back

D) Operating system installations

AWS provides the infrastructure and services (like EC2) that include a range of Amazon Machine Images (AMIs) with pre-installed operating systems. This means AWS is responsible for ensuring that these AMIs are available and that the underlying infrastructure to run these instances is secure and reliable.



<!-- Card End -->

---
<!-- Card Start -->

### Front

A company wants to monitor its workload performance. The company wants to ensure that the cloud services are delivered at a level that meets its business needs.  
  
Which AWS Cloud Adoption Framework (AWS CAF) perspective will meet these requirements?

- A. Business
- B. Governance
- C. Platform
- D. Operations

### Back

 D. Operations

The Operations perspective in AWS CAF focuses on managing and optimizing workloads, ensuring operational excellence, and monitoring performance to meet business requirements. It includes practices related to workload monitoring, performance optimization, incident management, and continuous improvement to ensure that cloud services are delivered effectively and efficiently.



<!-- Card End -->

---
<!-- Card Start -->
### Front


A company wants to continuously improve processes and procedures to deliver business value.  
  
Which pillar of the AWS Well-Architected Framework does this goal represent?

- A. Performance efficiency
- B. Operational excellence
- C. Reliability
- D. Sustainability

### Back
B. Operational excellence "The Operational Excellence pillar includes the ability to support development and run workloads effectively, gain insight into their operations, and to continuously improve supporting processes and procedures to deliver business value."



<!-- Card End -->

---
<!-- Card Start -->

### Front

A company has been storing monthly reports in an Amazon S3 bucket. The company exports the report data into comma-separated values (.csv) files. A developer wants to write a simple query that can read all of these files and generate a summary report.  
  
Which AWS service or feature should the developer use to meet these requirements with the LEAST amount of operational overhead?

- A. Amazon S3 Select
- B. Amazon Athena
- C. Amazon Redshift
- D. Amazon EC2

### Back
B Amazon Athena

Amazon Athena is an interactive query service that makes it simple to analyze data directly in Amazon S3 using standard SQL. Athena is serverless, so there is no infrastructure to setup or manage, and you can choose to pay based on the queries you run or compute needed by your queries. Use Athena to process logs, perform data analytics, and run interactive queries. Athena scales automatically – executing queries in parallel – so results are fast, even with large datasets and complex queries.

<!-- Card End -->

---
<!-- Card Start -->

### Front

Which AWS service can a company use to manage encryption keys in the cloud?

- A. AWS License Manager
- B. AWS Certificate Manager (ACM)
- C. AWS CloudHSM
- D. AWS Directory Service

### Back

C AWS CloudHSM
Hardware Security Module

<!-- Card End -->

---
<!-- Card Start -->

### Front
A company is migrating an application that includes an Oracle database to AWS. The company cannot rewrite the application.  
  
To which AWS service could the company migrate the database?

- A. Amazon Athena
- B. Amazon DynamoDB
- C. Amazon RDS
- D. Amazon DocumentDB (with MongoDB compatibility)

### Back

C. Amazon RDS 

Amazon Relational Database Service (Amazon RDS) is a collection of managed services that makes it simple to set up, operate, and scale databases in the cloud. Choose from seven popular engines — Amazon Aurora with MySQL compatibility, Amazon Aurora with PostgreSQL compatibility, MySQL, MariaDB, PostgreSQL, Oracle, and SQL Server — and deploy on-premises with Amazon RDS on AWS Outposts.


<!-- Card End -->

---
<!-- Card Start -->

### Front
Which AWS service helps users plan and track their server and application inventory migration data to AWS?

- A. Amazon CloudWatch
- B. AWS DataSync
- C. AWS Migration Hub
- D. AWS Application Migration Service

### Back
C. AWS Migration Hub - AWS service designed to help users plan, track, and manage their server and application inventory during the migration process to AWS.


<!-- Card End -->
<!-- Card Start -->
### Front

A company has applications that control on-premises factory equipment.  
  
Which AWS service should the company use to run these applications with the LEAST latency?

- A. AWS Outposts
- B. Amazon EC2
- C. AWS Lambda
- D. AWS Fargate

### Back


A. AWS Outposts supports workloads and devices requiring low latency access to on-premises systems, local data processing, data residency, and application migration with local system interdependencies.

<!-- Card End -->

<!-- Card Start -->

### Front  
A company is planning to run a global marketing application in the AWS Cloud. The application will feature videos that can be viewed by users. The company must ensure that all users can view these videos with low latency.  
Which AWS service should the company use to meet this requirement?  

- A. AWS Auto Scaling
- B. Amazon Kinesis Video Streams
- C. Elastic Load Balancing
- D. Amazon CloudFront

### Back

D. Amazon CloudFront


<!-- Card End --> 


<!-- Card Start -->

### Front

The ability to horizontally scale Amazon EC2 instances based on demand is an example of which concept?

- A. Economy of Scale
- B. Elasticity
- C. High availability
- D. Agility

### Back

Correct Answer: **B**

<!-- Card End -->
<!-- Card Start -->
### Front

A company requires a dashboard for reporting when using a business intelligence solution. Which AWS service can a Cloud Practitioner use?

- A. Amazon Redshift
- B. Amazon Kinesis
- C. Amazon Athena
- D. Amazon QuickSight

### Back

Correct Answer: **D** Amazon QuickSight.

**Amazon QuickSight** is the most appropriate AWS service for creating dashboards and reports in a business intelligence solution. It is a fully managed, cloud-based business intelligence service that allows users to create interactive visualizations, perform ad-hoc analysis, and quickly get business insights from their data [1](https://aws.amazon.com/quicksight/?tag=bizzopedia)[5](https://www.techtarget.com/searchaws/definition/Amazon-QuickSight). Key features of Amazon QuickSight that make it suitable for this scenario include:

1. Interactive dashboards: QuickSight enables the creation of dynamic visual dashboards for reporting purposes[8](https://aws.amazon.com/quicksight/q/).
2. Easy setup and use: It requires no complex server setups or data models, allowing users to get started quickly
3. Natural language querying: QuickSight Q allows users to ask questions about their data in plain English, making it accessible to users with varying technical expertise[3](https://www.uneecops.com/blog/what-amazon-quicksight-have-in-store-lets-explore/).
4. Machine learning insights: QuickSight incorporates ML capabilities to help users discover hidden trends and outliers in their data[9](https://aws.amazon.com/quicksight/features-ml/).
5. Scalability: It can support thousands of users without additional infrastructure management[5](https://www.techtarget.com/searchaws/definition/Amazon-QuickSight).

<!-- Card End -->
<!-- Card Start -->

### Front

According to the shared responsibility model, which security-related task is the responsibility of the customer?

- A. Maintaining server-side encryption.
- B. Securing servers and racks at AWS data centers.
- C. Maintaining firewall configurations at a hardware level.
- D. Maintaining physical networking configuration.

### Back

Correct Answer: **A**

<!-- Card End -->

---
 
<!-- Card Start -->

### Front

Which AWS service or feature can be used to restrict the individual API actions that users and roles in each member account can access?

- A. Amazon Macie
- B. AWS Organizations
- C. AWS Shield
- D. AWS IAM

### Back

Correct Answer: **B**

The correct answer is: B. AWS Organizations AWS Organizations can be used to restrict the individual API actions that users and roles in each member account can access. Here's why:

1. AWS Organizations provides Service Control Policies (SCPs) which allow you to control permissions for accounts in your organization[1](https://docs.aws.amazon.com/en_us/organizations/latest/userguide/orgs_manage_accounts_access.html).
2. SCPs can be used to restrict API actions across all users and roles in member accounts, including the root user[4](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_permissions_overview.html).
3. These policies can be attached to the organization root, an individual member account, or an organizational unit (OU) to control permissions[4](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_permissions_overview.html).
4. SCPs act as a permissions boundary, limiting what actions are allowed within an account regardless of what IAM policies are set within that account[1](https://docs.aws.amazon.com/en_us/organizations/latest/userguide/orgs_manage_accounts_access.html)[4](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_permissions_overview.html).

While AWS IAM (option D) is used for managing permissions within individual accounts, AWS Organizations provides a higher-level control across multiple accounts in an organization. Amazon Macie (option A) is for data security and privacy, and AWS Shield (option C) is for DDoS protection, neither of which are used for API action restrictions across accounts.

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS managed service provides protection from distributed denial of service (DDoS) attacks and assistance during such events?

- A. AWS Shield Advanced
- B. AWS Firewall Manager
- C. AWS Web Application Firewall
- D. Amazon GuardDuty

### Back

Correct Answer: **A**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS service allows publishing messages to thousands of subscribers simultaneously using a push mechanism?

- A. AWS Step Functions
- B. Amazon Simple Workflow Service (SWF)
- C. Amazon Simple Notification Service (Amazon SNS)
- D. Amazon Simple Queue Service (SQS)

### Back

Correct Answer: **C**

<!-- Card End -->

---

<!-- Card Start -->

### Front

How can a company separate costs for storage, Amazon EC2, Amazon S3, and other AWS services by department?

- A. Add department-specific tags to each resource
- B. Create a separate VPC for each department
- C. Create a separate AWS account for each department
- D. Use AWS Organizations

### Back

Correct Answer: **A**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS Support plan provides access to architectural and operational reviews, as well as 24/7 access to Cloud Support Engineers through email, online chat, and phone?

- A. Basic
- B. Business
- C. Developer
- D. Enterprise

### Back

Correct Answer: **D**

<!-- Card End -->
<!-- Card Start -->
### Front

Who is responsible for configuring backups when point-in-time recovery (PITR) is required for an Amazon DynamoDB table?

- A. The customer configures PITR, and AWS performs the backups.
- B. AWS automatically configures and performs backups.
- C. AWS performs the backups and configuration.
- D. The customer is responsible for both configuration and backups.
### Back

Correct Answer: **A**

The customer configures PITR, and AWS performs the backups. Point-in-time recovery (PITR) for Amazon DynamoDB is a feature that provides automatic continuous backups of table data. Here's a breakdown of the responsibilities:

1. Customer's role:
    
    - The customer is responsible for enabling PITR on their DynamoDB tables[1](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/PointInTimeRecovery_Howitworks.html)[3](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Point-in-time-recovery.html).
    - This can be done through the AWS Management Console, AWS CLI, AWS CloudFormation, or the DynamoDB API[1](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/PointInTimeRecovery_Howitworks.html).
    
2. AWS's role:
    
    - Once PITR is enabled, AWS automatically manages and performs the backups[3](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Point-in-time-recovery.html).
    - DynamoDB provides continuous backups for up to 35 days at a per-second granularity[3](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Point-in-time-recovery.html).
    

It's important to note that while the customer initiates the PITR setup, they don't need to worry about creating, maintaining, or scheduling the actual backups once it's enabled  This division of responsibilities ensures that customers have control over which tables are protected by PITR, while AWS handles the complex task of continuous backup management.

<!-- Card End -->
<!-- Card Start -->

### Front

What action should a user take when experiencing a production service disruption under the Business-level AWS Support plan?

- A. Contact the Technical Account Manager.
- B. Contact the AWS Concierge Support Team.
- C. Open a business-critical system down support case.
- D. Open a production system down support case.

### Back

Correct Answer: **D**

<!-- Card End -->
<!-- Card Start -->

### Front

What are advantages for companies running workloads in the AWS Cloud? (Select TWO.)

- A. Less staff time required to launch new workloads.
- B. Increased time to market for new application features.
- C. Higher acquisition costs to support elastic workloads.
- D. Lower overall utilization of server and storage systems.
- E. Increased productivity for application development teams.

### Back

Correct Answers: **A, E**

<!-- Card End -->
<!-- Card Start -->
### Front

Under the AWS shared responsibility model, which is an example of security in the AWS Cloud?

- A. Managing edge locations
- B. Physical security
- C. Firewall configuration
- D. Global infrastructure

### Back

Correct Answer: **C**

<!-- Card End -->
<!-- Card Start -->

### Front

Which statement about Amazon S3 cross-region replication is correct?

- A. Both source and destination S3 buckets must have versioning disabled.
- B. The source and destination S3 buckets cannot be in different AWS Regions.
- C. S3 buckets configured for cross-region replication can be owned by a single AWS account or by different accounts.
- D. The source S3 bucket owner must have the source and destination AWS Regions disabled for their account.
### Back

Correct Answer: **C**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which tasks can a user complete using AWS Cost Management tools?

- A. Delete all AWS resources with a single click.
- B. Create budgets and receive notifications if usage exceeds budgets.
- C. Launch EC2 Spot or On-Demand instances based on pricing.
- D. Move data stored in Amazon S3 to a cheaper storage class.

### Back

Correct Answer: **B**

<!-- Card End -->
<!-- Card Start -->
### Front

Which AWS service delivers static content stored in Amazon S3 to users worldwide with low latency?

- A. AWS Lambda
- B. Amazon CloudFront
- C. AWS Elastic Beanstalk
- D. AWS Global Accelerator

### Back

Correct Answer: **B**

<!-- Card End -->
<!-- Card Start -->

### Front

Which AWS services are infrastructure automation tools? (Select TWO.)

- A. AWS CloudFormation
- B. Amazon CloudFront
- C. AWS Batch
- D. AWS OpsWorks
- E. Amazon QuickSight

### Back

Correct Answers: **A, D**

<!-- Card End -->

---

<!-- Card Start -->
### Front

What advantage does Amazon RDS provide to database administrators?

- A. 99.99999999999% reliability and durability.
- B. Databases automatically scale based on load.
- C. Dynamically adjust CPU and RAM resources.
- D. Simplifies relational database administration tasks.
### Back

Correct Answer: **D**

<!-- Card End -->

<!-- Card Start -->

### Front

Which AWS hosting model provides physical isolation for workloads?

- A. Dedicated Hosts
- B. Reserved Instances
- C. On-Demand Instances
- D. Spot Instances

### Back

Correct Answer: **A**

<!-- Card End -->

<!-- Card Start -->

### Front

Which cloud design principles improve workload operations? (Select TWO.)

- A. Minimize platform design
- B. Loose coupling
- C. Customized hardware
- D. Remove single points of failure
- E. Minimum viable product

### Back

Correct Answers: **B, D**

<!-- Card End -->

<!-- Card Start -->

### Front

What is required to make an EC2 deployment highly available using an Elastic Load Balancer?

- A. Launch instances across multiple Availability Zones in a single AWS Region.
- B. Launch EC2 Spot Instances in the same AZ.
- C. Launch instances in multiple AWS Regions using Elastic IPs.
- D. Use Reserved Instances in the same AWS Region but different AZs.

### Back

Correct Answer: **A**

<!-- Card End -->
<!-- Card Start -->
### Front

What is the main benefit of AWS Elasticity?

- A. Minimize storage needs by reducing logs.
- B. Scale systems to meet demand.
- C. Enable AWS to optimize costs.
- D. Automate recovery and testing.
### Back

Correct Answer: **B**

<!-- Card End -->

<!-- Card Start -->

### Front

Which tool forecasts AWS spending?

- A. AWS Organizations
- B. Amazon Dev Pay
- C. AWS Trusted Advisor
- D. AWS Cost Explorer

### Back

Correct Answer: **D**

<!-- Card End -->
<!-- Card Start -->

### Front

Which AWS service creates interactive dashboards for business intelligence?

- A. Amazon QuickSight
- B. Amazon Redshift
- C. CloudWatch Dashboards
- D. Amazon Athena

### Back

Correct Answer: **A**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS feature accelerates file transfers over long distances to Amazon S3 buckets?

- A. File Transfer
- B. HTTP Transfer
- C. Amazon S3 Transfer Acceleration
- D. S3 Acceleration

### Back

Correct Answer: **C**

<!-- Card End -->
<!-- Card Start -->

### Front

Which AWS service manages SSL/TLS certificates, including renewal and updates?

- A. AWS Data Lifecycle Manager
- B. AWS License Manager
- C. AWS Firewall Manager
- D. AWS Certificate Manager

### Back

Correct Answer: **D**

<!-- Card End -->

---

<!-- Card Start -->
### Front

Who is responsible for ensuring availability and backup of EBS volumes?

- A. Delete the data and create a new EBS volume.
- B. Create EBS snapshots.
- C. Attach new volumes to EC2 Instances.
- D. Create copies of EBS Volumes.
### Back

Correct Answer: **B**

<!-- Card End -->
<!-- Card Start -->

### Front

Which AWS service acts as a web application firewall?

- A. AWS Snowball
- B. AWS WAF
- C. AWS Firewall
- D. AWS Protection

### Back

Correct Answer: **B**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which design principle reduces interdependencies so failures don’t affect other components?

- A. Integration
- B. Decoupling
- C. Aggregation
- D. Segregation

### Back

Correct Answer: **B**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS service alerts about scheduled maintenance impacting EC2 instances?

- A. AWS Organizations
- B. AWS Personal Health Dashboard
- C. AWS Trusted Advisor
- D. AWS Service Health Dashboard

### Back

Correct Answer: **B**

<!-- Card End -->

<!-- Card Start -->

### Front

Can security groups be changed for EC2 instances while running?

- A. Yes, security groups can be changed in running or stopped state.
- B. Yes, but only in hibernation state.
- C. No, security groups cannot be changed.
- D. Only default security groups can be changed.

### Back

Correct Answer: **A**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which Amazon RDS feature improves database availability?

- A. VPC Peering
- B. Multi-AZ
- C. Read Replicas
- D. Data Encryption

### Back

Correct Answer: **B**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS service facilitates database migration to the cloud?

- A. AWS Database Migration Service
- B. AWS VM Migration Service
- C. AWS Inspector
- D. AWS Trusted Advisor

### Back

Correct Answer: **A**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS service analyzes EC2 instances for security vulnerabilities?

- A. AWS Trusted Advisor
- B. AWS Inspector
- C. AWS WAF
- D. AWS Shield

### Back

Correct Answer: **B**

<!-- Card End -->
<!-- Card Start -->

### Front

Which AWS service provides location-based web personalization?

- A. Amazon CloudFront
- B. Amazon EC2
- C. Amazon Lightsail
- D. Amazon Route 53

### Back

Correct Answer: **A**

<!-- Card End -->
<!-- Card Start -->

### Front

Which AWS services protect against DDoS attacks? (Select TWO.)

- A. AWS EC2
- B. AWS RDS
- C. AWS Shield
- D. AWS Shield Advanced

### Back

Correct Answers: **C, D**

<!-- Card End -->

---
## zoot 

<!-- Card Start -->

### Front

Which resource is recommended to be deployed in a VPC private subnet?

- A. NAT Gateways
- B. Bastion Hosts
- C. Database Servers
- D. Internet Gateways

### Back

Correct Answer: **C**

Database servers are recommended to be deployed in a VPC private subnet for the following reasons:

1. Security: Private subnets provide an additional layer of security by isolating sensitive resources like databases from direct internet access[1](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-example-private-subnets-nat.html)[3](https://aws.github.io/aws-eks-best-practices/networking/subnets/).
2. Best practices: AWS recommends placing database servers in private subnets as part of a secure architecture design[2](https://www.reddit.com/r/aws/comments/qasrtd/is_there_a_such_thing_as_a_private_vpc/)[7](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-example-web-database-servers.html).
3. Access control: Resources in private subnets can still be accessed by other resources within the VPC, allowing controlled communication between application tiers[4](https://stackoverflow.com/questions/28542000/access-database-server-hosted-in-aws-private-subnet).
4. Protection: Deploying databases in private subnets helps protect them from unauthorized external access while still allowing necessary internal communications[5](https://docs.aws.amazon.com/vpc/latest/userguide/configure-subnets.html).

The other options are not typically deployed in private subnets:

- A. NAT Gateways are usually placed in public subnets to provide internet access for resources in private subnets.
- B. Bastion Hosts are typically deployed in public subnets to allow secure access to private resources.
- D. Internet Gateways are attached to the VPC itself, not deployed within subnets.

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS storage service is best for long-term data storage with retrieval times of 12-48 hours?

- A. Amazon S3 Glacier
- B. S3 Glacier Deep Archive
- C. Amazon EBS volumes
- D. AWS CloudFront

### Back

Correct Answer: **B**

<!-- Card End -->

<!-- Card Start -->

### Front

Which AWS service provides a fully managed NoSQL database with fast performance and scalability?

- A. AWS RDS
- B. Amazon DynamoDB
- C. Oracle RDS
- D. Elastic Map Reduce

### Back

Correct Answer: **B**

<!-- Card End -->
 
<!-- Card Start -->

### Front

Which AWS service provides detailed cost and usage reports?

- A. AWS Trusted Advisor
- B. AWS Cost Explorer
- C. AWS CloudTrail
- D. AWS Organizations

### Back

Correct Answer: **B**

<!-- Card End -->

---
# Drp
<!-- Card Start -->

### Front

Which AWS feature ensures encryption at rest for data stored in Amazon S3?

- A. AWS KMS
- B. Amazon Macie
- C. Server-Side Encryption (SSE)
- D. IAM Roles

### Back

Correct Answer: **C**


- AWS KMS (A) is a service for managing encryption keys, which can be used with SSE-KMS, but it's not the primary feature for S3 encryption.
- Amazon Macie (B) is a data security service that uses machine learning to discover and protect sensitive data, but it doesn't handle encryption.
- IAM Roles (D) are used for access management and don't directly provide encryption capabilities.
<!-- Card End -->
 
<!-- Card Start -->

### Front

Which AWS service is designed for monitoring and logging resource activities?

- A. AWS CloudTrail
- B. Amazon CloudWatch
- C. AWS Config
- D. AWS Inspector

### Back

Correct Answer: **B  Amazon CloudWatch.**

Amazon CloudWatch is the AWS service specifically designed for monitoring and logging resource activities. Here's why CloudWatch is the most appropriate choice:

1. Comprehensive monitoring: CloudWatch monitors AWS resources and applications running on AWS, providing real-time monitoring of metrics, logs, and events[1](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html).
2. Log management: It allows you to collect, store, and analyze log files from various AWS services, EC2 instances, and custom sources[1](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html)[3](https://www.amazonaws.cn/en/cloudwatch/features/).
3. Metrics and alarms: CloudWatch enables you to track metrics, set alarms, and automatically respond to changes in your AWS resources[6](https://www.simplilearn.com/tutorials/aws-tutorial/what-is-amazon-cloudwatch).
4. Visualization: It provides dashboards and graphs for visualizing your cloud data and application performance[2](https://www.techtarget.com/searchaws/definition/CloudWatch).
5. Real-time analysis: CloudWatch performs real-time analysis of logs and metrics, allowing for quick troubleshooting and operational insights[4](https://www.geeksforgeeks.org/introduction-to-amazon-cloudwatch/).

While the other options are related to AWS services, they serve different primary purposes:

- AWS CloudTrail (A) focuses on recording API calls and account activity for governance and compliance.
- AWS Config (C) is used for assessing, auditing, and evaluating configurations of AWS resources.
- AWS Inspector (D) is an automated security assessment service for applications deployed on AWS.

CloudWatch's extensive features for monitoring, logging, and analyzing resource activities make it the most suitable answer for this question.

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS feature automatically adjusts EC2 instance capacity based on demand?

- A. Elastic Load Balancer
- B. Reserved Instances
- C. Placement Groups
- D. Auto Scaling

### Back

Correct Answer: **D**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS service facilitates identity federation with third-party providers?

- A. AWS IAM
- B. AWS Cognito
- C. AWS Directory Service
- D. AWS Secrets Manager

### Back

Correct Answer: **B**

<!-- Card End -->

---

<!-- Card Start -->

### Front

What AWS service is used to manage encryption keys for securing data?

- A. AWS KMS
- B. AWS WAF
- C. AWS Certificate Manager
- D. AWS CloudHSM

### Back

Correct Answer: **A**

<!-- Card End -->

---
# Drp
<!-- Card Start -->

### Front

Which AWS service provides a serverless computing platform?

- A. Amazon EC2
- B. AWS Fargate
- C. AWS Lambda
- D. AWS CloudFormation

### Back

Correct Answer: **C**

note  fargate is kinda serverless container orchestration.  but B is THE serverless golden boy of AWS

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS storage class provides the lowest cost for long-term data archival?

- A. S3 Glacier Deep Archive
- B. S3 Standard-IA
- C. Amazon EBS
- D. Amazon RDS

### Back

Correct Answer: **A**

<!-- Card End -->
 

---

<!-- Card Start -->

### Front

Which AWS service protects against SQL injection and cross-site scripting attacks?

- A. AWS WAF
- B. AWS Shield
- C. AWS Firewall Manager
- D. AWS Inspector

### Back

Correct Answer: **A**

WEB Exploits

AWS WAF (Web Application Firewall) is a managed security service that protects web applications against common web exploits that could affect application availability, compromise security, or consume excessive resources.

Key aspects:

- Protects web apps and APIs from common attacks like SQL injection and cross-site scripting (XSS)
- Works with Amazon CloudFront, Application Load Balancer, API Gateway, and AppSync
- Lets you create rules to filter web traffic based on conditions like IP addresses, HTTP headers, and custom URI strings
- Can block or allow traffic based on your rules
- Includes managed rules for common threats and vulnerabilities
- Provides real-time metrics and sampled web requests

Think of it as a security guard that inspects and filters traffic before it reaches your application, blocking malicious requests while allowing legitimate traffic through.


<!-- Card End -->

<!-- Card Start -->

### Front

Which AWS service offers distributed denial-of-service (DDoS) protection?

- A. AWS CloudTrail
- B. AWS Shield
- C. AWS Security Hub
- D. AWS Config

### Back

Correct Answer: **B**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS service provides managed virtual desktops for remote access?

- A. Amazon WorkSpaces
- B. AWS AppStream 2.0
- C. AWS WorkLink
- D. Amazon Connect

### Back

Correct Answer: **A**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS service provides automatic backups and point-in-time recovery for DynamoDB?

- A. AWS CloudTrail
- B. AWS Backup
- C. DynamoDB PITR
- D. AWS Config

### Back

Correct Answer: **C**

<!-- Card End -->

<!-- Card Start -->

### Front

Which AWS service is used to set budgets and track usage costs?

- A. AWS Organizations
- B. AWS Budgets
- C. AWS Trusted Advisor
- D. AWS CloudTrail

### Back

Correct Answer: **B**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS service is ideal for storing frequently accessed data with millisecond latency?

- A. Amazon S3 Standard
- B. Amazon S3 Glacier
- C. Amazon S3 Intelligent-Tiering
- D. Amazon S3 Glacier Deep Archive

### Back

Correct Answer: **A**

<!-- Card End -->
 
<!-- Card Start -->

### Front

Which AWS service is designed for archiving data at the lowest cost?

- A. Amazon S3 Glacier
- B. Amazon S3 Glacier Deep Archive
- C. Amazon EFS
- D. Amazon S3 Intelligent-Tiering

### Back

Correct Answer: **B**

<!-- Card End -->

---

<!-- Card Start -->

### Front

What AWS feature supports fault tolerance by replicating resources across Availability Zones?

- A. Multi-AZ Deployments
- B. Elastic Load Balancer
- C. AWS Auto Scaling
- D. AWS Shield

### Back

Correct Answer: **A**

<!-- Card End -->
 

---

<!-- Card Start -->

### Front

Which AWS service provides a managed Kubernetes environment?

- A. Amazon EKS
- B. AWS Elastic Beanstalk
- C. Amazon ECS
- D. AWS Lambda

### Back

Correct Answer: **A**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS service is used to detect security threats using machine learning?

- A. AWS WAF
- B. Amazon GuardDuty
- C. AWS Inspector
- D. AWS CloudTrail

### Back

Correct Answer: **B**

<!-- Card End -->

---

 

---

<!-- Card Start -->

### Front

Which AWS service enables automated code deployment?

- A. AWS CodeDeploy
- B. AWS CodePipeline
- C. AWS CodeCommit
- D. AWS CloudFormation

### Back

Correct Answer: **A**

 **Explanation:**

- **A. AWS CodeDeploy** – Enables **automated code deployment** to Amazon EC2 instances, Lambda functions, and on-premises servers. It helps streamline the deployment process, minimizes downtime, and supports both rolling updates and blue-green deployments.
    
- **B. AWS CodePipeline** – An **orchestration tool** that automates the build, test, and deployment process as part of a CI/CD pipeline, but it relies on services like **CodeDeploy** for the actual deployment step.
    
- **C. AWS CodeCommit** – A **source control service** for hosting Git repositories but does not handle deployments.
    
- **D. AWS CloudFormation** – Used for **infrastructure-as-code** to provision AWS resources but does not handle application code deployment.
- 
<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS service can scale compute resources automatically based on usage?

- A. Elastic Load Balancer
- B. AWS Auto Scaling
- C. AWS CloudFormation
- D. Amazon CloudFront

### Back

Correct Answer: **B**

<!-- Card End -->

---
 

<!-- Card Start -->

### Front

Which AWS service provides an object storage solution with scalability, security, and performance?

- A. Amazon S3
- B. Amazon EFS
- C. Amazon Glacier
- D. AWS Storage Gateway

### Back

Correct Answer: **A**

<!-- Card End -->

---

<!-- Card Start -->

### Front

Which AWS service offers a managed solution for hosting relational databases?

- **A. Amazon RDS**
- B. Amazon DynamoDB
- C. Amazon Redshift
- D. AWS Aurora

### Back

Correct Answer: **A**

- **A. Amazon RDS (Relational Database Service)** – A **fully managed service** for hosting and scaling **relational databases** such as MySQL, PostgreSQL, MariaDB, Oracle, and SQL Server. It simplifies database administration tasks like backups, patching, and monitoring.
    
- **B. Amazon DynamoDB** – A **NoSQL database** service designed for key-value and document-based storage, not relational databases.
    
- **C. Amazon Redshift** – A **data warehousing service** optimized for **analytical processing** (OLAP) rather than transactional relational databases.
    
- **D. AWS Aurora** – A **relational database** engine compatible with MySQL and PostgreSQL, but it is a **specific engine** within **Amazon RDS** rather than a standalone service.
- 

<!-- Card End -->

---
# dd

<!-- Card Start -->

### Front

Which AWS service allows monitoring of AWS resources and applications in real-time?

- A. AWS Config
- B. AWS CloudTrail
- C. Amazon CloudWatch
- D. AWS X-Ray

### Back

Correct Answer: **C**

<!-- Card End -->

---

 

---

<!-- Card Start -->

### Front

Which AWS service provides a virtual private cloud to isolate resources?

- A. Amazon VPC
- B. AWS Direct Connect
- C. AWS VPN
- D. AWS Transit Gateway

### Back

Correct Answer: **A**

<!-- Card End -->
<!-- Card Start -->

### Front

Which AWS service provides a fully managed data warehouse solution?

- A. Amazon RDS
- B. Amazon Athena
- C. Amazon Redshift
- D. Amazon DynamoDB

### Back

Correct Answer: **C**

<!-- Card End -->

---

 

---

<!-- Card Start -->

### Front

Which AWS service provides a centralized platform for automating workflows?

- A. AWS Lambda
- B. AWS Step Functions
- C. AWS CodePipeline
- D. AWS Glue

### Back

Correct Answer: **B**

<!-- Card End -->
 
<!-- Card Start -->

### Front

Which AWS service helps in tracking configuration changes of AWS resources?

- A. AWS CloudTrail
- B. AWS Config
- C. AWS Inspector
- D. AWS CloudWatch

### Back

Correct Answer: **B**

<!-- Card End -->

---

  

---

<!-- Card Start -->

### Front

Which AWS service is used to securely store and manage access keys and secrets?

- A. AWS Secrets Manager
- B. AWS Identity and Access Management (IAM)
- C. AWS Certificate Manager
- D. AWS Key Management Service (KMS)

### Back

Correct Answer: **A
weak question
KMS manages too...but secret manager does secrets

Think of it as:

- Secrets Manager = Password Manager
- KMS = Key Locker
- HSM = Bank Vault ( crazy strong)

<!-- Card End -->


<!-- Card Start -->

### Front 
A company purchased Amazon EC2 Standard Reserved Instances (RIs) for a workload in the AWS Cloud. The company needs to move part of the workload to an instance family that does not match the instance family of these Standard RIs.  
  
How can the company take advantage of the Standard RIs that it no longer needs?

- A. Contact the AWS Support team, and ask the team to sell the Standard RIs
- B. Sell the Standard RIs on the Amazon EC2 Reserved Instance Marketplace
- C. Sell the Standard RIs as a third-party seller on the AWS Marketplace
- D. Convert the Standard RIs to Savings Plans
### Back
B. Sell the Standard RIs on the Amazon EC2 Reserved Instance Marketplace


Correct Answer: B. Sell the Standard RIs on the Amazon EC2 Reserved Instance Marketplace

This is correct because:

- The EC2 Reserved Instance Marketplace is specifically designed for customers to sell their unused Standard RIs to other AWS customers
- Sellers can list their unused RI time and set their own price
- This provides flexibility when business needs change and you no longer need your RIs
- 
<!-- Card End --> 


 

<!-- Card Start -->

### Front 
A company needs to run some of its workloads on premises to comply with regulatory guidelines. The company wants to use the AWS Cloud to run workloads that are not required to be on premises. The company also wants to be able to use the same API calls for the on-premises workloads and the cloud workloads.  
  
Which AWS service or feature should the company use to meet these requirements?

- A. Dedicated Hosts
- B. AWS Outposts
- C. Availability Zones
- D. AWS Wavelength
### Back
AWS Outposts

The correct answer is B. AWS Outposts because:

- It's specifically designed for hybrid cloud scenarios
- Provides consistent AWS APIs across cloud and on-premises
- Allows you to run AWS services on-premises
- Maintains regulatory compliance by keeping specific workloads on-premises
- Enables seamless integration between on-premises and cloud environments
- 

<!-- Card End --> 



<!-- Card Start -->

### Front 

A company runs an uninterruptible Amazon EC2 workload on AWS 24 hours a day, 7 days a week. The company will require the same instance family and instance type to run the workload for the next 12 months.  
  
Which combination of purchasing options should the company choose to MOST optimize costs? (Choose two.)

- A. Standard Reserved Instance
- B. Convertible Reserved Instance
- C. Compute Savings Plan
- D. Spot Instance
- E. All Upfront payment

### Back

- A. **Standard Reserved Instance:** Standard Reserved Instances (RIs) are ideal for workloads that run 24/7 and are predictable over a long period (e.g., 12 months). By committing to a specific instance family and type, the company can get significant discounts compared to On-Demand pricing. 

- E. **All Upfront payment:** Choosing the All Upfront payment option for Reserved Instances provides the maximum discount. This option allows the company to pay for the entire 12-month commitment upfront, further reducing costs compared to monthly payments or partial upfront payments.

note: Convertable is less discount but gives you the option of converting up ( the question says nothing changed)

<!-- Card End --> 


<!-- Card Start -->

### Front 
A company plans to perform a one-time migration of a large dataset with millions of files from its on-premises data center to the AWS Cloud.  
  
Which AWS service should the company use for the migration?

- A. AWS Database Migration Service (AWS DMS)
- B. AWS DataSync
- C. AWS Migration Hub
- D. AWS Application Migration Service
### Back
B. AWS DataSync

AWS DataSync is designed for transferring large amounts of data quickly and securely between on-premises storage and AWS. It is well-suited for one-time migrations of large datasets and can handle millions of files efficiently.

<!-- Card End --> 


<!-- Card Start -->

### Front 
A company wants to define a central data protection policy that works across AWS services for compute, storage, and database resources.  
  
Which AWS service will meet this requirement?

- A. AWS Batch
- B. AWS Elastic Disaster Recovery
- C. AWS Backup  
- D. Amazon FSx
### Back

- C. AWS Backup  

AWS Backup is a fully managed backup service that makes it easy to centralize and automate the back up of data across AWS services in the cloud as well as on-premises. With AWS Backup, you can configure backup policies and monitor backup activity for AWS resources in one place. This includes compute resources like EC2 instances, storage resources like EBS volumes, and database resources like RDS databases.


<!-- Card End --> 
 
 