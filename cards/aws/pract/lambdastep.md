#flashcards #aws

status:: 
count:: 25
[[Flashcards]]

<!-- Card Start -->
### Front 
What is AWS Lambda and what is its primary purpose?

### Back
AWS Lambda is a serverless compute service that runs code in response to events without requiring server management. Its primary purposes are:

- **Event-driven execution**: Runs code in response to triggers from AWS services or HTTP endpoints
- **Automatic scaling**: Scales automatically from a few requests per day to thousands per second
- **Pay-per-use**: Charges only for compute time consumed
- **Supports multiple languages**: Including Node.js, Python, Java, Go, Ruby, and .NET Core

<!-- Card End -->

<!-- Card Start -->
### Front
What are the maximum execution duration limits for AWS Lambda functions?

### Back
- **Maximum execution duration**: 15 minutes (900 seconds)
- **Default timeout**: 3 seconds
- **Minimum timeout**: 1 second
- **Configuration**: Timeout can be set at deployment or update time
- **Best practice**: Set the timeout value based on expected function execution time plus a buffer

<!-- Card End -->

<!-- Card Start -->
### Front
Compare AWS Lambda and AWS Step Functions

### Back
**AWS Lambda**:
- Single-purpose functions
- Short-lived executions
- Event-driven processing
- Standalone compute service

**AWS Step Functions**:
- Orchestrates multiple AWS services
- Long-running workflows
- Visual workflow designer
- State machine-based coordination
- Maintains workflow state

<!--- Card Link --->
<!-- Card End -->

<!-- Card Start -->
### Front 
What are the main state types in AWS Step Functions?

### Back
1. **Task States**: Execute work (Lambda, AWS services)
2. **Choice States**: Add branching logic
3. **Parallel States**: Execute branches simultaneously
4. **Map States**: Process items in arrays
5. **Wait States**: Pause execution
6. **Pass States**: Pass data without work
7. **Succeed States**: End execution successfully
8. **Fail States**: End execution with failure

<!-- Card End -->

<!-- Card Start -->
### Front  
How does memory allocation work in AWS Lambda?

### Back
- **Range**: 128 MB to 10,240 MB (10 GB)
- **Increments**: 1 MB steps
- **CPU Scaling**: CPU power scales linearly with memory
- **Pricing**: Charged based on memory-time (GB-seconds)
- **Best practice**: Test different memory configurations to optimize cost/performance

<!-- Card End -->

<!-- Card Start -->
### Front 
What are the two types of workflows in Step Functions?

### Back
**Standard Workflows**:
- Long-running executions (up to 1 year)
- At-least-once execution model
- Full execution history
- Higher price point

**Express Workflows**:
- Short-lived executions (up to 5 minutes)
- At-most-once or at-least-once execution
- Limited execution history
- Lower price point, higher throughput

<!-- Card End -->

<!-- Card Start -->
### Front
What is a cold start in AWS Lambda and how to minimize it?

### Back
A cold start occurs when a new Lambda container is initialized, causing additional latency:

**Minimization strategies**:
- Use Provisioned Concurrency
- Implement function warming
- Optimize code package size
- Choose runtimes with faster startup (Node.js, Python)
- Keep dependencies minimal

<!-- Card End -->

<!-- Card Start -->
### Front
How are environment variables handled in AWS Lambda?

### Back
- **Storage**: Key-value pairs stored in function configuration
- **Size limit**: 4 KB total for all environment variables
- **Encryption**: Can be encrypted using KMS
- **Runtime access**: Available through standard runtime interfaces
- **Best practice**: Use for configuration that changes between environments

<!-- Card End -->

<!-- Card Start -->
### Front 
How does Step Functions handle data input and output?

### Back
- Uses **JsonPath** syntax for data manipulation
- **InputPath**: Selects portion of input JSON
- **OutputPath**: Filters output JSON
- **ResultPath**: Specifies where to place result
- **Parameters**: Manipulates input data
- Maximum event size: 256 KB

<!-- Card End -->

<!-- Card Start -->
### Front 
What is the default concurrent execution limit for Lambda?

### Back
- **Default limit**: 1,000 concurrent executions per region
- **Reserved concurrency**: Can be set per function
- **Unreserved concurrency**: Shared pool for all functions
- **Burst concurrency**: Initial burst of 500-3000 based on region
- Can request limit increase via AWS Support

<!-- Card End -->

<!-- Card Start -->
### Front
What error handling features are available in Step Functions?

### Back
- **Retry**: Configure retry attempts with backoff
- **Catch**: Handle specific error types
- **TimeoutSeconds**: Set state execution timeout
- **HeartbeatSeconds**: Monitor long-running tasks
- **FallbackStates**: Define alternate execution paths
- Error types: States.ALL, States.Timeout, States.TaskFailed

<!-- Card End -->

<!-- Card Start -->
### Front 
Compare Lambda@Edge with regular Lambda functions

### Back
**Lambda@Edge**:
- Runs at CloudFront edge locations
- Lower memory limit (128MB)
- Shorter timeout (5-30 seconds)
- Limited runtime support
- No VPC access

**Regular Lambda**:
- Runs in single AWS region
- Up to 10GB memory
- Up to 15 minutes timeout
- Full runtime support
- VPC access available

<!-- Card End -->

<!-- Card Start -->
### Front 
What are key security best practices for Lambda?

### Back
1. **IAM Roles**: Use least privilege permissions
2. **VPC**: Run in VPC when accessing private resources
3. **Secrets**: Use Secrets Manager or Parameter Store
4. **Dependencies**: Regularly update runtime and dependencies
5. **Logging**: Enable CloudWatch logging
6. **API Security**: Use API Gateway with authorization
7. **Code Signing**: Enable code signing for functions

<!-- Card End -->

<!-- Card Start -->
### Front 
What is a Task Token in Step Functions and when to use it?

### Back
- **Purpose**: Enable callback pattern for long-running tasks
- **Usage**: External systems can signal task completion
- **Implementation**: Using .waitForTaskToken
- **Timeout**: Can be configured up to 1 year
- **Best for**: Human approval workflows, external processing

<!-- Card End -->

<!-- Card Start -->
### Front 
What are Lambda Layers and their benefits?

### Back
**Lambda Layers**:
- Shared code and dependencies across functions
- Up to 5 layers per function
- Maximum size: 250 MB unzipped
- Can include custom runtimes
- Versioning support
- Reduces deployment package size
- Promotes code reuse

<!-- Card End -->

<!-- Card Start -->
### Front 
Compare Step Functions and SQS for workflow management

### Back
**Step Functions**:
- Visual workflow management
- Complex orchestration
- Built-in error handling
- State tracking
- Higher cost

**SQS**:
- Simple message queue
- Decoupled components
- Message retention
- Lower cost
- No visual workflow

<!-- Card End -->

<!-- Card Start -->
### Front 
What are Lambda Function URLs and their features?

### Back
- **Dedicated HTTPS endpoint** for Lambda function
- **Built-in CORS** support
- **Authentication**: IAM or NONE
- **Dual stack**: Supports IPv4 and IPv6
- **Request context**: Includes HTTP context
- **No additional charge**: Pay only for Lambda invocations
- Alternative to API Gateway for simple HTTP APIs

<!-- Card End -->

<!-- Card Start -->
### Front 
What are Step Functions Activities and their use cases?

### Back
- **Poll-based tasks** executed by external workers
- Used for **legacy system integration**
- Workers can run **anywhere** (on-premises, cloud)
- Supports **long-polling** (up to 60 seconds)
- Requires **manual acknowledgment**
- Good for **hybrid cloud** scenarios
- Alternative to Lambda for specialized workloads

<!-- Card End -->

<!-- Card Start -->
### Front 
How does Lambda integrate with VPC resources?

### Back
- Requires **ENI** (Elastic Network Interface)
- Needs **subnet IDs** and **security groups**
- Access to private resources like **RDS**, **ElastiCache**
- **Cold start** impact when using VPC
- Requires **IAM permissions** for ENI management
- No direct internet access without **NAT Gateway**
- Best practice: Only enable if required

<!-- Card End -->

<!-- Card Start -->
### Front 
What are the integration patterns for Step Functions?

### Back
**Integration Patterns**:
1. **Request Response**: Synchronous tasks
2. **Run a Job**: Asynchronous operations
3. **Wait for Callback**: External completion signal
4. **Optimized Integrations**: Direct service integration

**Supported Services**:
- Lambda
- AWS Batch
- DynamoDB
- ECS/Fargate
- SNS/SQS
- and many more

<!-- Card End -->

<!-- Card Start -->
### Front 
How do Dead Letter Queues work with Lambda?

### Back
- **Purpose**: Capture failed event processing
- **Supported destinations**: SQS or SNS
- **Configuration**: Set at function level
- **Event retention**: Based on destination service
- **Async invocation only**: Not for synchronous calls
- **Alternative**: Use destination configuration
- **Best practice**: Monitor DLQ for troubleshooting

<!-- Card End -->

<!-- Card Start -->
### Front 
What are key Lambda performance optimization techniques?

### Back
1. **Code Optimization**:
   - Minimize initialization code
   - Reuse connections and clients
   - Implement caching

2. **Configuration**:
   - Right-size memory allocation
   - Use Provisioned Concurrency
   - Optimize deployment package

3. **Architecture**:
   - Use async patterns when possible
   - Implement fan-out patterns
   - Consider Step Functions for orchestration

<!-- Card End -->

<!-- Card Start -->
### Front 
Compare AWS Step Functions and EventBridge Rules

### Back
**Step Functions**:
- Complex workflow orchestration
- Visual workflow designer
- State management
- Error handling and retry logic
- Long-running processes

**EventBridge Rules**:
- Event routing and filtering
- Simple event-driven patterns
- Schedule-based execution
- Fan-out pattern support
- No state management

<!-- Card End -->

<!-- Card Start -->
### Front
What are the characteristics of Lambda Container Images?

### Back
- **Size limit**: Up to 10 GB
- **Base images**: AWS-provided or custom
- **Registry**: Store in Amazon ECR
- **Runtime API**: Must implement Lambda Runtime API
- **Benefits**:
  - Consistent build environment
  - Larger deployment packages
  - Container tooling compatibility
- **Limitations**:
  - Longer cold starts
  - More complex deployment

<!-- Card End -->