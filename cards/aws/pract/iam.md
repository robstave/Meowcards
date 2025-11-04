
#flashcards #aws 

status:: 
count:: 
[[Flashcards]]

<!-- Card Start -->

### Front

What does IAM stand for in AWS?

### Back

IAM stands for **Identity and Access Management**.

It is a web service that helps you securely control access to AWS resources.

<!-- Card End -->

<!-- Card Start -->

### Front

What are the main components of IAM?

### Back

The main components of IAM are:

- Users
- Groups
- Roles
- Policies

<!-- Card End -->

<!-- Card Start -->

### Front

What is an IAM User?

### Back

An IAM User is an entity that represents a person or service that interacts with AWS. It has a unique name and security credentials (password or access keys).

<!-- Card End -->

<!-- Card Start -->

### Front

What is an IAM Group?

### Back

An IAM Group is a collection of IAM users. Groups allow you to specify permissions for multiple users, making it easier to manage permissions.

<!-- Card End -->

<!-- Card Start -->

### Front

What is an IAM Role?

### Back

An IAM Role is an identity with specific permissions that can be assumed by AWS services, applications, or users. Roles do not have long-term credentials associated with them.

<!-- Card End -->

<!-- Card Start -->

### Front

What is an IAM Policy?

### Back

An IAM Policy is a JSON document that defines permissions. It specifies what actions are allowed or denied on which AWS resources.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the principle of least privilege in IAM?

### Back

The principle of least privilege means granting only the permissions required to perform a task. It's a best practice in IAM to minimize potential security risks.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Multi-Factor Authentication (MFA) in IAM?

### Back

MFA is an extra layer of security that requires users to provide a second form of authentication in addition to their password. It significantly enhances account security.

<!-- Card End -->

<!-- Card Start -->

### Front

What are IAM Security Tools?

### Back

IAM Security Tools include:

1. IAM Credentials Report
2. IAM Access Advisor

These tools help in auditing and managing IAM permissions.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the IAM Password Policy?

### Back

The IAM Password Policy is a set of rules that define the complexity requirements for IAM user passwords. It can enforce minimum length, specific character types, and password expiration.

<!-- Card End -->

<!-- Card Start -->

### Front

How can users access AWS?

### Back

Users can access AWS through:

1. AWS Management Console (web interface)
2. AWS Command Line Interface (CLI)
3. AWS Software Development Kits (SDKs)

<!-- Card End -->

<!-- Card Start -->

### Front

What is the AWS CLI?

### Back

The AWS CLI (Command Line Interface) is a unified tool to manage AWS services from the command line. It allows you to control multiple AWS services and automate them through scripts.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the AWS SDK?

### Back

The AWS SDK (Software Development Kit) provides language-specific APIs for interacting with AWS services programmatically. It's available for various programming languages like Python, Java, JavaScript, etc.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of IAM Roles for Services?

### Back

IAM Roles for Services allow AWS services to perform actions on your behalf. They provide a secure way for services to access resources without the need for long-term access keys.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the IAM Policy Simulator?

### Back

The IAM Policy Simulator is a tool that allows you to test and troubleshoot IAM policies. It helps you understand which actions are allowed or denied based on your current policies.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between AWS-managed and Customer-managed policies?

### Back

- AWS-managed policies: Created and managed by AWS, cannot be modified by customers.
- Customer-managed policies: Created and managed by the customer, offering more granular control.

<!-- Card End -->

<!-- Card Start -->

### Front

What is IAM Policy Inheritance?

### Back

IAM Policy Inheritance refers to how permissions are applied:

- Users inherit permissions from groups they belong to.
- Roles can inherit permissions from attached policies.
- Final permissions are a combination of all applicable policies.

<!-- Card End -->

<!-- Card Start -->

### Front

What are IAM Access Keys?

### Back

IAM Access Keys are long-term credentials for IAM users. They consist of:

1. Access Key ID
2. Secret Access Key

These are used to make programmatic requests to AWS services via the CLI or SDK.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the IAM root user?

### Back

The IAM root user is the account created when you first set up your AWS account. It has complete access to all AWS services and resources. Best practice is to avoid using the root user for everyday tasks.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the shared responsibility model for IAM?

### Back

In the shared responsibility model for IAM:

- AWS is responsible for infrastructure security and IAM service availability.
- Customers are responsible for managing users, groups, roles, and applying appropriate policies.

<!-- Card End -->


<!-- Card Start -->

### Front

What is the principle of least privilege in IAM?

### Back

The principle of least privilege means granting only the minimum permissions necessary for users or roles to perform their required tasks. This practice helps to reduce security risks by limiting potential damage from compromised credentials.

<!-- Card End -->

<!-- Card Start -->

### Front

What are IAM Access Keys used for?

### Back

IAM Access Keys are used for programmatic access to AWS services. They consist of:

1. Access Key ID
2. Secret Access Key

These credentials are used to authenticate requests made via the AWS CLI, SDKs, or direct API calls.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between inline and managed policies in IAM?

### Back

- **Inline policies**: Directly embedded into a single user, group, or role. They are unique to that entity.
- **Managed policies**: Standalone policies that can be attached to multiple users, groups, or roles. They come in two types:
  1. AWS managed policies: Created and managed by AWS
  2. Customer managed policies: Created and managed by the customer

<!-- Card End -->

<!-- Card Start -->

### Front

What is IAM Policy Evaluation Logic?

### Back

IAM Policy Evaluation Logic determines the final access decision:

1. By default, all requests are implicitly denied
2. An explicit allow overrides the default
3. An explicit deny overrides any allows

The most restrictive policy always wins.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of IAM Access Analyzer?

### Back

IAM Access Analyzer helps identify resources in your organization and accounts that are shared with an external entity. It:

- Analyzes policies for unintended access
- Generates findings for resources accessible from outside your AWS account
- Helps maintain least privilege by identifying unused permissions

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between authentication and authorization in IAM?

### Back

- **Authentication**: The process of verifying the identity of a user or service (who you are)
- **Authorization**: The process of determining what actions an authenticated entity is allowed to perform (what you can do)

IAM handles both processes for AWS services.

<!-- Card End -->

<!-- Card Start -->

### Front

What is IAM Identity Center (formerly AWS SSO)?

### Back

IAM Identity Center is a service that helps you securely create or connect your workforce identities and manage their access centrally across AWS accounts and applications. It provides:

- Single sign-on access to multiple AWS accounts
- Centralized permission management
- Integration with HR systems and identity providers

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of IAM instance profiles?

### Back

IAM instance profiles are containers for IAM roles that can be used to pass role information to an EC2 instance when it starts. They allow:

- EC2 instances to assume a role without storing long-term credentials
- Applications running on the instance to access AWS resources securely

<!-- Card End -->

<!-- Card Start -->

### Front

What is the AWS Security Token Service (STS)?

### Back

AWS Security Token Service (STS) is a web service that enables you to request temporary, limited-privilege credentials for IAM users or federated users. It's used for:

- Implementing temporary security credentials
- Supporting identity federation
- Cross-account access

<!-- Card End -->

<!-- Card Start -->

### Front

What is IAM role chaining?

### Back

IAM role chaining is the process of assuming a role from another assumed role. It allows:

- Complex permission delegation across accounts
- Temporary access across multiple AWS accounts
- Maximum session duration of 1 hour when chaining roles

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of IAM policy conditions?

### Back

IAM policy conditions add constraints to when a policy is in effect. They can be based on:

- Time of day or date
- IP address of the requester
- Use of SSL/TLS
- Multi-factor authentication (MFA) status
- AWS tags

Conditions provide more granular control over when policies are applied.

<!-- Card End -->

<!-- Card Start -->

### Front

What is IAM policy versioning?

### Back

IAM policy versioning allows you to keep multiple versions of a managed policy. Benefits include:

- Tracking changes to policies over time
- Reverting to previous policy versions if needed
- Maintaining up to five versions of a managed policy

The default version is the one currently in effect.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the IAM Policy Simulator?

### Back

The IAM Policy Simulator is a tool that helps you:

- Test and troubleshoot IAM policies
- Validate the effects of policies before committing them to production
- Determine which specific API actions are allowed or denied for specific resources

It's useful for debugging permission issues and understanding complex policies.

<!-- Card End -->

<!-- Card Start -->

### Front

What are IAM permission boundaries?

### Back

IAM permission boundaries are a feature that sets the maximum permissions an IAM entity can have. They:

- Define the maximum permissions a user or role can have
- Do not grant permissions by themselves
- Are useful for delegating permissions management while maintaining control

Permission boundaries can be used with identity-based policies for fine-grained access control.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between a root user and an IAM user?

### Back

- **Root user**: 
  - Created when the AWS account is created
  - Has complete, unrestricted access to all AWS services and resources
  - Should only be used for initial account setup and specific tasks

- **IAM user**:
  - Created within the AWS account
  - Has only the permissions explicitly granted to it
  - Used for day-to-day interactions with AWS services

Best practice is to avoid using the root user for everyday tasks.

<!-- Card End -->

<!-- Card Start -->

### Front

What is IAM Access Advisor?

### Back

IAM Access Advisor is a feature that shows the service permissions granted to a user and when those services were last accessed. It helps:

- Identify unused permissions
- Refine policies to align with actual usage
- Implement the principle of least privilege

Access Advisor data is updated within 4 hours of activity.

<!-- Card End -->

<!-- Card Start -->

### Front

What are IAM tags and how are they used?

### Back

IAM tags are key-value pairs that can be attached to IAM users, roles, and managed policies. They are used for:

- Organizing and categorizing IAM entities
- Controlling access based on tags (when used with IAM policies)
- Cost allocation and tracking
- Enhancing searchability and filtering of IAM resources

Tags can be used in IAM policies to grant or restrict access based on tag values.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of IAM Access Keys rotation?

### Back

IAM Access Keys rotation is the practice of regularly changing access keys. It:

- Enhances security by limiting the time an access key is active
- Reduces the impact of a compromised key
- Is recommended by AWS as a security best practice

AWS recommends rotating access keys every 90 days or sooner.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the IAM policy evaluation order when multiple policies apply?

### Back

When multiple policies apply, IAM evaluates them in this order:

1. Explicit Deny: If any policy has an explicit deny, the request is denied
2. Organizations SCPs: Evaluated next if the account is part of an AWS Organization
3. Resource-based Policies: Checked if applicable to the requested resource
4. Identity-based Policies: Policies attached to the IAM user, group, or role
5. IAM Permissions Boundaries: If set, these limit the maximum allowed permissions
6. Session Policies: If present, these apply to temporary credentials

The most restrictive set of permissions from this evaluation is applied.

<!-- Card End -->

<!-- Card Start -->

### Front

What is cross-account access in IAM and how is it implemented?
### Back

Cross-account access in IAM allows users from one AWS account to access resources in another AWS account. It's implemented using:

1. IAM roles in the target account
2. Trust relationships between accounts
3. AssumeRole API call to obtain temporary security credentials

This approach enhances security by avoiding the need to share long-term access keys between accounts.

<!-- Card End -->

Citations:
[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/15706698/cabfc564-7a9b-4ec8-9319-2c0379fe68a3/iam.md
[2] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/15706698/cabfc564-7a9b-4ec8-9319-2c0379fe68a3/iam.md