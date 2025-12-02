
status:: 
count:: 21
[[Flashcards]]

create a few cards for study of cloudtrail vs cloudfront. But where the question is perhaps a use case and the question which is the right choice for the usecase. Other similar products I get mixed up are fargate/ECS redshift/kenisis waf vr firewall if there are others you can thing off. Create those too like a dozen or so cards

I understand you want flashcards comparing various AWS services, focusing on use cases and choosing the right service. I'll create cards for CloudTrail vs CloudFront, Fargate vs ECS, Redshift vs Kinesis, WAF vs Firewall, and a few others that are often confused. Here are the flashcards in the requested format: 

<!-- Card Start -->

## Front

You need to track API calls and user activity across your AWS account. Which service should you use?

## Back

**CloudTrail**

**CloudTrail** is designed for auditing and logging API activity, making it the ideal choice for tracking user actions and API calls across your AWS infrastructure [4](https://allcode.com/top-aws-services/). 

<!-- Card End --> 
<!-- Card Start -->

## Front

Your application needs to deliver content with low latency to users worldwide. Which service is best suited for this?

## Back

**CloudFront**

**CloudFront** is AWS's content delivery network (CDN) service, designed to distribute content globally with low latency, making it perfect for delivering web assets, dynamic content, or streaming video to users worldwide[4](https://allcode.com/top-aws-services/). 

<!-- Card End --> 
<!-- Card Start -->

## Front

You want to run containerized applications without managing the underlying infrastructure. Which service should you choose?

## Back

**AWS Fargate**

**Fargate** is a serverless compute engine for containers that works with both ECS and EKS. It allows you to run containers without managing servers or clusters, making it ideal for those who want to focus on application development rather than infrastructure management[1](https://blog.purestorage.com/purely-educational/fargate-vs-ecs/)[5](https://www.cloudzero.com/blog/ecs-vs-eks/). 

<!-- Card End --> 
<!-- Card Start -->

## Front

You need fine-grained control over your container orchestration and want to use Docker containers. Which service is more suitable?

## Back

**Amazon ECS (Elastic Container Service)**

ECS is a fully managed container orchestration service that supports Docker containers. It provides more control over the underlying infrastructure compared to Fargate, making it suitable for users who need specific instance types or configurations[1](https://blog.purestorage.com/purely-educational/fargate-vs-ecs/)[5](https://www.cloudzero.com/blog/ecs-vs-eks/). 

<!-- Card End --> 
<!-- Card Start -->

## Front

Your application needs to analyze large volumes of structured data for business intelligence. Which service should you use?

## Back

**Amazon Redshift**

Redshift is a fully managed data warehouse service optimized for analyzing large datasets using standard SQL queries. It's ideal for business intelligence and big data analytics[4](https://allcode.com/top-aws-services/). 

<!-- Card End --> 
<!-- Card Start -->

## Front

You need to process and analyze real-time streaming data. Which service is more appropriate?

## Back

Amazon Kinesis

Kinesis is designed for real-time processing of streaming data at scale. It's suitable for applications that need to ingest and process large amounts of data in real-time, such as log and event data collection, IoT device data telemetry, and real-time analytics[4](https://allcode.com/top-aws-services/). 
<!-- Card End --> <!-- Card Start -->

## Front

You want to protect your web applications from common web exploits. Which service should you use?

## Back

AWS WAF (Web Application Firewall)WAF operates at the application layer (Layer 7) and is specifically designed to protect web applications from common exploits like SQL injection and cross-site scripting. It's ideal for securing web applications exposed to the internet[3](https://www.tufin.com/blog/waf-vs-firewall-unraveling-web-application-network-firewalls-conundrum)[6](https://plainenglish.io/blog/difference-between-aws-waf-and-aws-network-firewall). 

<!-- Card End --> <!-- Card Start -->

## Front

You need to control traffic flow at the network level for your entire VPC. Which service is more suitable?

## Back

**AWS Network Firewall**

Network Firewall operates at the network layer (Layer 3-4) and provides broader protection for your entire VPC. It's suitable for controlling traffic flow, implementing security policies, and protecting a wide range of AWS resources beyond just web applications[3](https://www.tufin.com/blog/waf-vs-firewall-unraveling-web-application-network-firewalls-conundrum)[6](https://plainenglish.io/blog/difference-between-aws-waf-and-aws-network-firewall). 

<!-- Card End --> 
<!-- Card Start -->

## Front

You need a service for storing and retrieving any amount of data from anywhere on the web. Which AWS service should you use?

## Back

**Amazon S3 (Simple Storage Service)**

S3 is an object storage service offering industry-leading scalability, data availability, security, and performance. It's ideal for a wide range of use cases including websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics[4](https://allcode.com/top-aws-services/). 

<!-- Card End -->
<!-- Card Start -->

## Front

You want to run code without provisioning or managing servers. Which AWS service is best for this?

## Back

**AWS Lambda**

Lambda is a serverless compute service that lets you run code without provisioning or managing servers. It automatically scales your application by running code in response to each trigger, making it ideal for building serverless applications[4](https://allcode.com/top-aws-services/). 

<!-- Card End -->
<!-- Card Start -->

## Front

You need a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability. Which AWS service should you choose?

## Back

**Amazon DynamoDB**

DynamoDB is a key-value and document database that delivers single-digit millisecond performance at any scale. It's fully managed, multi-region, multi-active, durable database with built-in security, backup and restore, and in-memory caching for internet-scale applications[4](https://allcode.com/top-aws-services/). 

<!-- Card End --> 
<!-- Card Start -->

## Front

You want to easily deploy and scale a web application without worrying about the underlying infrastructure. Which AWS service is most suitable?

## Back

**AWS Elastic Beanstalk**

Elastic Beanstalk is an easy-to-use service for deploying and scaling web applications and services. It automatically handles the details of capacity provisioning, load balancing, scaling, and application health monitoring[4](https://allcode.com/top-aws-services/). 

<!-- Card End -->

Those are pretty good. Can you think of 5 or 6 for machine learning ai that is relevant to the aws cloud practitioner exam

<!-- Card Start -->

## Front

Which AWS service provides a fully managed environment for building, training, and deploying machine learning models?

## Back

**Amazon SageMaker**

Amazon SageMaker is a comprehensive service that simplifies the machine learning workflow, allowing developers and data scientists to prepare data, build models, train and tune them, and deploy them to production[1](https://www.restack.io/p/aws-ai-comparison-answer-2025)[3](https://www.ibm.com/think/topics/amazon-sagemaker). 
<!-- Card End -->
<!-- Card Start -->

## Front

You need a service to add image and video analysis capabilities to your application without deep learning expertise. Which AWS service should you use?

## Back

**Amazon Rekognition**

Amazon Rekognition provides pre-trained computer vision capabilities, allowing you to easily add image and video analysis to your applications without requiring machine learning expertise[1](https://www.restack.io/p/aws-ai-comparison-answer-2025).
<!-- Card End --> 
<!-- Card Start -->

## Front

Which AWS service allows you to add natural language processing (NLP) capabilities to your applications?

## Back

**Amazon Comprehend**

Amazon Comprehend is a natural language processing (NLP) service that uses machine learning to find insights and relationships in text, such as sentiment analysis, entity recognition, and language detection[1](https://www.restack.io/p/aws-ai-comparison-answer-2025). 
<!-- Card End -->
<!-- Card Start -->

## Front

You want to add text-to-speech capabilities to your application. Which AWS service should you use?

## Back

**Amazon Polly**

Amazon Polly is a service that turns text into lifelike speech, allowing you to create applications that talk and build entirely new categories of speech-enabled products[1](https://www.restack.io/p/aws-ai-comparison-answer-2025).

<!-- Card End -->
 
<!-- Card Start -->

## Front

What is the primary advantage of using AWS AI services for cloud practitioners?

## Back

**Ease of use and quick integration**

AWS AI services are designed to be easily integrated into applications without requiring deep machine learning expertise. This allows cloud practitioners to quickly add AI capabilities to their projects, reducing the time and complexity typically associated with implementing AI features[1](https://www.restack.io/p/aws-ai-comparison-answer-2025)[5](https://www.veritis.com/blog/top-15-aws-machine-learning-tools-in-the-cloud/). 

<!-- Card End -->