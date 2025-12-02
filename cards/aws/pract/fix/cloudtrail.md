#flashcards #aws

status:: 
count:: 
[[Flashcards]]

## Cloudetrail 20

<!-- Card Start -->
### Front
What is AWS CloudTrail and its primary purpose?

### Back
AWS CloudTrail is a service that provides:
- **Governance, compliance, and audit** capabilities
- Records all **API activity** and events in AWS account
- Creates **event history** of AWS account activity
- Supports **security analysis**
- Enables **resource change tracking**
- Facilitates **troubleshooting**

<!-- Card End -->
<!-- Card Start -->
### Front 
How does CloudTrail ensure log file integrity?

### Back
CloudTrail log file integrity validation:
- Uses industry-standard **SHA-256 hashing**
- Implements **SHA-256 with RSA** for digital signing
- Creates a **digest file** containing hashes
- Delivers digest files to specified **S3 bucket**
- Enables **detection of log file tampering**
- Provides **chain of custody** for log files

<!-- Card End -->
<!-- Card Start -->
### Front
Compare CloudTrail and CloudWatch Logs

### Back
**CloudTrail**:
- Records AWS API activity
- Focuses on who/what/when of changes
- Audit and compliance oriented
- Account-level activity tracking

**CloudWatch Logs**:
- Application and system logs
- Performance and error monitoring
- Operational insights
- Resource-level monitoring

<!-- Card End -->
<!-- Card Start -->
### Front  
What are the different types of events recorded by CloudTrail?

### Back
1. **Management Events**:
   - Control plane operations
   - Account management activities
   - Default enabled

2. **Data Events**:
   - Resource operations
   - High-volume activities
   - Disabled by default

3. **Insights Events**:
   - Unusual API activity
   - Requires separate enabling
   - Additional cost

<!-- Card End -->

<!-- Card Start -->
### Front  
What are key configuration options for a CloudTrail trail?

### Back
- **Name**: Unique within region
- **S3 bucket**: Log file destination
- **KMS encryption**: Optional encryption
- **Log file prefix**: Organization structure
- **SNS notification**: Activity alerts
- **CloudWatch Logs**: Log monitoring
- **Multi-region**: Global or regional tracking
- **Organization**: Multi-account logging

<!-- Card End -->

<!-- Card Start -->
### Front  
How does CloudTrail handle log retention and storage?

### Back
- **Event history**: 90 days by default
- **S3 storage**: Indefinite retention possible
- **Lifecycle policies**: Automated archival
- **Storage classes**: Support for S3 tiers
- **Compression**: Logs stored in compressed format
- **Organization**: Prefix-based structuring
- **Cost optimization**: Through lifecycle management

<!-- Card End -->

<!-- Card Start -->
### Front
What security features does CloudTrail provide?

### Back
- **IAM integration**: Access control
- **KMS encryption**: At-rest encryption
- **S3 bucket policies**: Storage security
- **Log file validation**: Integrity checking
- **Private endpoints**: VPC support
- **Service-linked roles**: Automated permissions
- **Organization trails**: Centralized security

<!-- Card End -->

<!-- Card Start -->
### Front 
What is CloudTrail Insights and its benefits?

### Back
CloudTrail Insights:
- **Automated analysis** of unusual API activity
- **Machine learning** based detection
- **Baseline determination** of normal activity
- **Anomaly detection** in real-time
- **Root cause analysis** capabilities
- **Proactive notification** of changes
- Additional cost for feature

<!-- Card End -->

<!-- Card Start -->
### Front
How do Organization trails work in CloudTrail?

### Back
Organization trails features:
- **Single trail** for multiple accounts
- **Centralized logging** in master account
- **Automatic enablement** for new accounts
- **Consolidated view** of activity
- **Simplified management** of audit logs
- **Cost efficiency** through sharing
- Requires AWS Organizations

<!-- Card End -->

<!-- Card Start -->
### Front 
What API activities does CloudTrail record?

### Back
Records:
- **AWS Management Console** actions
- **AWS CLI** commands
- **AWS SDK** operations
- **Other AWS service** APIs
- **IAM user/role** activity
- **Root account** activity
- **Resource-level** changes
- **Error responses** and denials

<!-- Card End -->

<!-- Card Start -->
### Front  
How to optimize CloudTrail costs?

### Back
Cost optimization strategies:
- **Selective event recording**
- **Log file compression**
- **S3 lifecycle policies**
- **Insights selective enabling**
- **Regional vs global trails**
- **Consolidation** of multiple trails
- **Storage class optimization**
- **Log retention period** management

<!-- Card End -->

<!-- Card Start -->
### Front 
What AWS services integrate with CloudTrail?

### Back
Key integrations:
- **S3** for log storage
- **CloudWatch Logs** for monitoring
- **EventBridge** for automation
- **SNS** for notifications
- **KMS** for encryption
- **IAM** for access control
- **Organizations** for multi-account
- **Athena** for log analysis

<!-- Card End -->

<!-- Card Start -->
### Front
What are CloudTrail implementation best practices?

### Back
1. **Security**:
   - Enable log file validation
   - Use KMS encryption
   - Implement least privilege
   
2. **Configuration**:
   - Enable multi-region trails
   - Configure CloudWatch integration
   - Set up SNS notifications

3. **Monitoring**:
   - Enable Insights
   - Regular log analysis
   - Alert on critical changes

<!-- Card End -->

<!-- Card Start -->
### Front
What are common CloudTrail troubleshooting scenarios?

### Back
Common issues and solutions:
- **Missing logs**: Check IAM permissions
- **Delivery delays**: Verify S3 policies
- **Integration failures**: Check service roles
- **Log validation errors**: Verify integrity
- **SNS notification issues**: Check topic policies
- **CloudWatch integration**: Validate role trust
- **Organization trail issues**: Check Organizations setup

<!-- Card End -->

<!-- Card Start -->
### Front
How are CloudTrail log files structured?

### Back
Log file components:
- **JSON format**
- **Event time** and source
- **User identity** information
- **Service name** and region
- **API details** and parameters
- **Resource information**
- **IP address** and user agent
- **Error codes** if applicable

<!-- Card End -->

<!-- Card Start -->
### Front  
Compare CloudTrail and AWS Config

### Back
**CloudTrail**:
- API activity logging
- Who made what changes
- Audit trail of actions
- Event-based tracking

**AWS Config**:
- Resource state tracking
- Configuration history
- Compliance monitoring
- Resource relationships
- State-based tracking

<!-- Card End -->

<!-- Card Start -->
### Front  
What are CloudTrail Data Events and their use?

### Back
Data Events characteristics:
- **High-volume** activities
- **Resource-level** operations
- **Separate pricing** structure
- Supported services:
  - S3 object-level API
  - Lambda function execution
  - DynamoDB item changes
  - S3 on Outposts
- **Selective enabling** recommended
- **Granular control** available

<!-- Card End -->

<!-- Card Start -->
### Front  
What is CloudTrail Lake and its features?

### Back
CloudTrail Lake provides:
- **Managed data lake** for logs
- **SQL-based querying**
- **Event aggregation**
- **Cross-account** analysis
- **Custom retention** periods
- **Integration events** support
- **Advanced analytics** capabilities
- **Region independent** storage

<!-- Card End -->

<!-- Card Start -->
### Front  
What are the key service limits in CloudTrail?

### Back
Important limits:
- **5 trails** per region
- **90 days** event history retention
- **Maximum event size**: 256KB
- **Management events**: Unlimited
- **Data events**: Volume-based pricing
- **Delivery time**: ~15 minutes
- **Organization trails**: 5 per organization
- **API rate**: 10 calls per second

<!-- Card End -->

<!-- Card Start -->
### Front  
What are alternative logging patterns to CloudTrail?

### Back
Alternative approaches:
- **CloudWatch Logs**: Application logging
- **VPC Flow Logs**: Network traffic
- **S3 Access Logs**: Bucket access
- **Load Balancer Logs**: Traffic patterns
- **AWS Config**: Resource tracking
- **GuardDuty**: Security monitoring
- **Security Hub**: Security posture
- **EventBridge**: Event routing

<!-- Card End -->