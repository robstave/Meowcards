#flashcards #aws

status:: 
count:: 11
[[Flashcards]]

<!-- Card Start -->
### Front 
What is AWS CloudFormation and its core purpose?

### Back

AWS CloudFormation is an Infrastructure as Code (IaC) service that:
- **Automates** infrastructure deployment
- Creates resources in a **consistent, repeatable** manner
- Manages AWS resources through **templates**
- Handles **dependencies** automatically
- Treats infrastructure as **version-controlled code**
- Provides **rollback** capabilities
- Enables **stack** based resource management

<!-- Card End -->

<!-- Card Start -->
### Front

What is AWS CloudFormation and what are its main functions?
### Back

AWS CloudFormation is a service that:

- Allows users to model and provision their entire cloud infrastructure using configuration files
- Functions as an Infrastructure as Code (IaC) tool
- Enables creation, updating, and deletion of AWS resources in an automated way
- Uses JSON or YAML templates to define required AWS resources
- Manages resources as a single unit called a "stack"
- Supports provisioning across multiple AWS regions and accounts

<!-- Card End -->

<!-- Card Start -->
### Front

What are the main sections of a CloudFormation template?
### Back
A CloudFormation template consists of:

1. **Format Version**: Template version identifier
2. **Description**: Template documentation
3. **Parameters**: Input values
4. **Mappings**: Key-value lookups
5. **Conditions**: Conditional resource creation
6. **Resources** (Required): AWS resources to create
7. **Outputs**: Return values
8. **Metadata**: Template additional information
9. **Transform**: Include serverless transforms or macros

<!-- Card End -->
<!-- Card Start -->
### Front

How does CloudFormation handle stack updates?
### Back
CloudFormation stack updates involve:

- **Change Sets**: Preview of changes before execution
- **Update Behaviors**:
  - No interruption
  - Some interruption
  - Replacement
- **Rolling Updates**: Staged resource updates
- **Stack Policies**: Protect resources from updates
- **Rollback Triggers**: Automatic failure detection
- **Drift Detection**: Identify manual changes

<!-- Card End -->
<!-- Card Start -->
### Front 
Compare CloudFormation with Terraform

### Back
**CloudFormation**:
- Native AWS integration
- AWS-specific features
- JSON/YAML templates
- Stack-based management
- Free service (pay for resources)

**Terraform**:
- Multi-cloud support
- HCL syntax
- State file management
- Provider-based architecture
- Larger community modules
- More flexible state management

<!-- Card End -->
<!-- Card Start -->
### Front 

What are Nested Stacks and their benefits?
### Back
**Nested Stacks**:
- Reuse common template patterns
- Break down complex templates
- Maximum resources limit workaround
- Hierarchical stack management
- Modular infrastructure design

**Implementation**:
- Uses AWS::CloudFormation::Stack resource
- Supports parameters passing
- Enables template reuse
- Manages dependencies between stacks

<!-- Card End -->
<!-- Card Start -->
### Front 
What are key CloudFormation best practices?
### Back
1. **Template Structure**:
   - Use YAML for readability
   - Implement proper version control
   - Include comprehensive descriptions

2. **Security**:
   - Use stack policies
   - Implement least privilege
   - Encrypt sensitive parameters

3. **Operations**:
   - Test templates in dev environment
   - Use change sets
   - Implement proper tagging
   - Document dependencies

4. **Cost**:
   - Estimate costs before deployment
   - Use parameters for flexibility
   - Clean up unused resources

<!-- Card End -->
<!-- Card Start -->
### Front 
How to implement deletion protection in CloudFormation?

### Back
Multiple protection layers:

1. **Stack-level**:
   - EnableTerminationProtection flag
   - Stack policies

2. **Resource-level**:
   - DeletionPolicy attribute
   - RetentionPolicy settings
   - Termination protection

3. **Additional Measures**:
   - IAM policies
   - Resource lock settings
   - Service-specific protection

<!-- Card End -->
<!-- Card Start -->
### Front
What are CloudFormation Custom Resources?
### Back
Custom Resources allow:

- **Integration** with external resources
- **Custom provisioning** logic
- **Third-party service** management
- **Gap filling** for unsupported resources

**Implementation**:
- Lambda function backing
- SNS topic integration
- Response handling
- Lifecycle management
- Custom logic execution

<!-- Card End -->
<!-- Card Start -->
### Front 
How does CloudFormation Drift Detection work?

### Back
Drift Detection:

- **Purpose**: Identify unmanaged changes
- **Process**:
  1. Scan resource configuration
  2. Compare with template
  3. Report differences
  
- **Supported Operations**:
  - Stack level detection
  - Resource level detection
  - Drift status reporting
  
- **Limitations**:
  - Not all resources supported
  - Point-in-time detection
  - Manual initiation required

<!-- Card End -->
<!-- Card Start -->
### Front 

What are CloudFormation StackSets and their use cases?
### Back
**StackSets enable**:
- Deploy stacks across multiple accounts
- Regional deployment management
- Centralized operations
- Organizational unit deployment

**Features**:
- Concurrent deployment
- Automatic deployment ordering
- Failed operation handling
- Permission management
- Drift detection support
- Automatic retries

<!-- Card End -->
<!-- Card Start -->
### Front 
How to validate CloudFormation templates?
### Back
Validation methods:

1. **AWS Console**:
   - Template designer
   - Validate template option
   
2. **AWS CLI**:
   - validate-template command
   - describe-stack-events

3. **Best Practices**:
   - Linting tools
   - Static code analysis
   - Test deployments
   - Change set review
   - Parameter validation
   - Resource configuration checks

<!-- Card End -->

<!-- Card Start -->

### Front

What are the key components of an AWS CloudFormation template?

### Back

An AWS CloudFormation template typically includes:

1. Parameters: For user input and customization
2. Mappings: Key-value pairs for conditional resource definition
3. Conditions: For creating or modifying resources based on specific criteria
4. Resources: The only mandatory section, declaring all AWS resources
5. Outputs: For exporting information about created resources
6. Metadata: To organize parameters logically

<!-- Card End --> 
<!-- Card Start -->
### Front

What are some real-world use cases for AWS CloudFormation?

### Back

Real-world use cases for AWS CloudFormation include:

1. Infrastructure management with DevOps: Automating testing and deployment
2. Production stack scaling: From single EC2 instances to complex multi-region applications
3. Defining subnets and services: Easy provisioning of VPCs, ECS, or OpsWorks
4. Replicating environments: Creating identical dev, test, and production setups
5. Version control for infrastructure: Tracking changes and facilitating rollbacks
6. Multi-region deployments: Consistent resource provisioning across different regions
7. Access control: Managing permissions and security configurations
8. Application deployment: Automating the setup of entire application stacks

<!-- Card End -->

