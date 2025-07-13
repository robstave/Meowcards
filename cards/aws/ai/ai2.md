# AWS AI Practitioner Exam Flashcards - Set 2

<!-- Card Start -->

### Front

Which AWS services can be used to build a complete chatbot solution? (Choose 2)
- A. Amazon Lex
- B. Amazon Polly
- C. Amazon Transcribe
- D. Amazon Kendra
- E. Amazon Textract

### Back

**Correct Answers**: A and D  
**Explanation**: Amazon Lex provides the conversational interface for building chatbots with automatic speech recognition (ASR) and natural language understanding (NLU) capabilities. Amazon Kendra provides intelligent search functionality using semantic search to help chatbots retrieve relevant information from enterprise data sources. 

**Amazon Polly** converts text to speech but doesn't handle the conversational aspects, 
**Transcribe** converts speech to text but doesn't understand intent, and 
**Textract** is for extracting text from documents.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary difference between Amazon SageMaker and Amazon Bedrock?
- A. SageMaker is only for traditional ML, Bedrock is only for generative AI
- B. SageMaker is a comprehensive ML platform for custom models, Bedrock provides managed access to foundation models
- C. SageMaker is cheaper than Bedrock for all use cases
- D. SageMaker and Bedrock serve completely different purposes with no overlap

### Back

**Correct Answer**: B  
**Explanation**: Amazon SageMaker is a comprehensive ML platform for the entire ML lifecycle (data prep, training, deployment, monitoring) including both traditional ML and generative AI capabilities.

 Amazon Bedrock specifically provides serverless access to pre-trained foundation models from multiple providers (Anthropic Claude, AI21 Jurassic, Amazon Titan, etc.) with built-in features like Guardrails and Agents. While SageMaker can work with foundation models, Bedrock is purpose-built for easy consumption of large language models.

<!-- Card End -->

<!-- Card Start -->

### Front

Which of the following are key considerations when implementing responsible AI? (Choose 2)
- A. Maximizing model accuracy at all costs
- B. Ensuring fairness across different demographic groups
- C. Implementing transparency and explainability
- D. Using the largest possible dataset
- E. Minimizing computational costs

### Back

**Correct Answers**: B and C  
**Explanation**: Responsible AI implementation requires ensuring fairness (option B) by preventing/mitigating bias and discrimination across demographic groups. It also requires transparency and explainability (option C) so stakeholders can understand how models make decisions and trust the systems.

 Options A, D, and E focus solely on technical or business considerations without addressing ethical concerns. The AWS Responsible AI approach emphasizes human agency, fairness, governance, privacy, robustness, and transparency.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary purpose of Amazon SageMaker Ground Truth?
- A. To train foundation models
- B. To create high-quality labeled datasets
- C. To deploy models to production
- D. To monitor model performance

### Back

**Correct Answer**: B  
**Explanation**: Amazon SageMaker Ground Truth is a data labeling service that helps create high-quality training datasets by providing tools for human annotators. It includes features like automated data labeling with active learning that reduces labeling costs by up to 70%. Ground Truth supports various labeling types including text classification, image classification, object detection, semantic segmentation, and can use private workforces, Amazon Mechanical Turk, or AWS Marketplace vendor workforces to complete labeling tasks.

<!-- Card End -->

<!-- Card Start -->

### Front

Which Amazon Bedrock features help ensure responsible AI deployment? (Choose 2)
- A. Guardrails
- B. Model customization
- C. Agents
- D. Model evaluation
- E. Knowledge bases

### Back

**Correct Answers**: A and D  
**Explanation**: Amazon Bedrock Guardrails (A) allow you to implement content filtering policies that block harmful content in both inputs and outputs, enforce topics to avoid, and protect personally identifiable information (PII). Model evaluation (D) helps you assess foundation models based on key metrics and custom evaluation criteria to ensure they meet quality, safety, and fairness standards before deployment. 

Model customization (B) adapts models to specific use cases, Agents (C) orchestrate tasks, and Knowledge bases (E) connect external information, but these don't specifically target responsible AI practices.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between fine-tuning and prompt engineering in generative AI?
- A. Fine-tuning is cheaper than prompt engineering
- B. Fine-tuning modifies model weights, prompt engineering modifies inputs
- C. Fine-tuning is faster than prompt engineering
- D. Fine-tuning requires less data than prompt engineering

### Back

**Correct Answer**: B  
**Explanation**: Fine-tuning modifies a model's internal weights through additional training on domain-specific data, requiring computational resources but creating a customized model that better understands your specific domain. Prompt engineering involves carefully crafting input text to guide the model's response without modifying the model itself—it's more immediate but requires experimentation to achieve optimal results. In Amazon Bedrock, fine-tuning is available for models like Claude, while prompt engineering can be done with any foundation model using techniques like few-shot learning and specific formatting.

<!-- Card End -->

#fix
this seems kinda weird.  I mean, you can run 
what you want on EC2...can you refine this 
to be a bit more in task

<!-- Card Start -->

### Front

Which AWS services are commonly used for real-time ML inference? (Choose 2)
- A. Amazon SageMaker Real-time Endpoints
- B. Amazon S3
- C. AWS Lambda
- D. Amazon CloudWatch
- E. Amazon EC2

### Back

**Correct Answers**: A and C  
**Explanation**: Amazon SageMaker Real-time Endpoints (A) are purpose-built for ML inference with automatic scaling, model monitoring, and support for various instance types including GPU and Inferentia. AWS Lambda (C) enables serverless inference for lightweight models with low latency requirements and automatic scaling with a pay-per-invocation pricing model. Amazon S3 (B) is a storage service not designed for inference, CloudWatch (D) is for monitoring, and while EC2 (E) can run inference workloads, it requires manual setup and management of infrastructure unlike the specialized services.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Retrieval Augmented Generation (RAG) primarily used for?
- A. Training new foundation models from scratch
- B. Combining retrieved information with generative AI responses
- C. Compressing large language models
- D. Converting text to images

### Back

**Correct Answer**: B  
**Explanation**: Retrieval Augmented Generation (RAG) enhances foundation models by retrieving relevant information from external data sources and incorporating it into the generation process. This achieves several key benefits: (1) access to information beyond the model's training cutoff date, (2) improved factual accuracy by grounding responses in authoritative sources, (3) reduced hallucinations since the model can reference actual data instead of fabricating responses, and (4) ability to incorporate domain-specific or proprietary information. In AWS, this is implemented using Amazon Bedrock Knowledge Bases, which combine vector search with foundation models.

<!-- Card End -->

<!-- Card Start -->

### Front

Which factors should be considered when selecting a foundation model? (Choose 2)
- A. Model size and computational requirements
- B. The company that created the model
- C. Task-specific performance metrics
- D. The programming language used to build the model
- E. The year the model was created

### Back

**Correct Answers**: A and C  
**Explanation**: When selecting a foundation model in Amazon Bedrock or other platforms, model size and computational requirements (A) directly impact inference latency, throughput, and costs—larger models generally provide better quality but with higher resource demands. 
Task-specific performance metrics (C) evaluate how well models perform on specific tasks like text generation, summarization, or code completion, helping match capabilities to business requirements.

 The creator company (B), programming language (D), and creation year (E) are less relevant than actual performance metrics. AWS recommends evaluating models using both automated benchmarks and human evaluation for your specific use cases.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary benefit of using Amazon SageMaker Model Registry?
- A. To train models faster
- B. To manage model versions and metadata
- C. To reduce model inference costs
- D. To automatically deploy models

### Back

**Correct Answer**: B  
**Explanation**: Amazon SageMaker Model Registry provides a centralized repository for model catalog management with versioning, lineage tracking, and approval workflows. It maintains metadata like training metrics, datasets used, hyperparameters, and approval status for each model version. Model Registry integrates with CI/CD pipelines and enables organizations to implement governance processes with model approval workflows. It also facilitates model deployment by allowing you to select specific approved versions for deployment to production, supporting regulatory compliance and model governance requirements by maintaining comprehensive audit trails.

<!-- Card End -->

<!-- Card Start -->

### Front

Which Amazon Bedrock capabilities support building AI agents? (Choose 2)
- A. Agents for Amazon Bedrock
- B. Knowledge bases for Amazon Bedrock
- C. Guardrails for Amazon Bedrock
- D. Custom model import
- E. Model evaluation

### Back

**Correct Answers**: A and B  
**Explanation**: **Agents for Amazon Bedrock** (A) provides a fully managed capability to build autonomous AI agents that can understand user requests, break them down into steps, and execute multi-step tasks by calling external APIs and business systems. It includes an orchestration layer that manages conversation context, action planning, and execution flow. 

**Knowledge bases for Amazon Bedrock** (B) enhances agents with RAG capabilities by connecting to external data sources (S3, SharePoint, Confluence, etc.), creating vectorized representations, and enabling semantic search—allowing agents to retrieve and incorporate enterprise information in responses. 

Guardrails (C) focuses on content filtering, 

custom model import (D) allows for using your own models, and 

model evaluation (E) is for assessing model performance, but these don't directly enable agent functionality.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of temperature parameter in generative AI models?
- A. To control the physical temperature of the GPU
- B. To adjust the randomness and creativity of outputs
- C. To set the speed of model inference
- D. To determine the model size

### Back

**Correct Answer**: B  
**Explanation**: Temperature is a hyperparameter that controls randomness in token selection during text generation. Lower temperature settings (e.g., 0-0.3) make outputs more deterministic, focused, and predictable—ideal for factual responses, specific instructions, or code generation. Higher temperature settings (e.g., 0.7-1.0) introduce more randomness, creating more diverse, creative, and varied responses—better for brainstorming, creative writing, or generating multiple alternatives. In Amazon Bedrock, temperature can be adjusted in the API's inferenceConfig parameter, allowing developers to fine-tune model behavior for different use cases without changing the model itself. This parameter has nothing to do with hardware temperature (A), inference speed (C), or model size (D).

<!-- Card End -->

<!-- Card Start -->

### Front

Which AWS services help detect bias in ML models? (Choose 2)
- A. Amazon SageMaker Clarify
- B. Amazon Textract
- C. Amazon SageMaker Model Monitor
- D. Amazon Polly
- E. Amazon Translate

### Back

**Correct Answers**: A and C  
**Explanation**: Amazon SageMaker Clarify (A) provides bias detection capabilities at multiple stages of the ML lifecycle. It calculates pre-training bias metrics to identify issues in training data, post-training bias metrics to detect if models have learned biased patterns, and offers feature attribution capabilities to explain which features contribute most to predictions. Amazon SageMaker Model Monitor (C) extends bias detection to production by monitoring for bias drift, automatically analyzing predictions for emerging bias patterns over time, and sending alerts when metrics deviate from baselines. 

Textract (B) is for document processing, 
Polly (D) is for text-to-speech, and 
Translate (E) is for language translation—none provide bias detection functionality.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary difference between supervised and unsupervised learning?
- A. Supervised learning is faster than unsupervised learning
- B. Supervised learning uses labeled data, unsupervised learning uses unlabeled data
- C. Supervised learning is more accurate than unsupervised learning
- D. Supervised learning requires more computational power

### Back

**Correct Answer**: B  
**Explanation**: Supervised learning algorithms learn from labeled training data (input-output pairs), while unsupervised learning algorithms find patterns in unlabeled data without explicit target outputs.

<!-- Card End -->

<!-- Card Start -->

### Front

Which security measures are important for AI/ML workloads on AWS? (Choose 2)
- A. Encryption at rest and in transit
- B. Using only public datasets
- C. IAM roles and policies for access control
- D. Storing all data in a single region
- E. Disabling all logging

### Back

**Correct Answers**: A and C  
**Explanation**: Encryption protects data confidentiality, while proper IAM controls ensure only authorized users and services can access ML resources. These are fundamental security practices for AI/ML workloads.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of Amazon SageMaker Pipelines?
- A. To create data visualization dashboards
- B. To orchestrate and automate ML workflows
- C. To serve models for real-time inference
- D. To store large datasets

### Back

**Correct Answer**: B  
**Explanation**: SageMaker Pipelines enables you to create, automate, and manage end-to-end ML workflows, including data preparation, training, evaluation, and deployment steps.

<!-- Card End -->

<!-- Card Start -->

### Front

Which techniques can help reduce hallucinations in generative AI models? (Choose 2)
- A. Increasing model temperature
- B. Using Retrieval Augmented Generation (RAG)
- C. Implementing proper prompt engineering
- D. Reducing model size
- E. Using only synthetic training data

### Back

**Correct Answers**: B and C  
**Explanation**: RAG provides factual information from reliable sources, while proper prompt engineering can guide models to be more accurate and honest about their limitations, both helping reduce false or fabricated outputs.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary purpose of Amazon SageMaker Feature Store?
- A. To train ML models
- B. To serve ML models
- C. To store and manage ML features
- D. To monitor ML models

### Back

**Correct Answer**: C  
**Explanation**: SageMaker Feature Store is a centralized repository for storing, sharing, and managing ML features, enabling feature reuse across different models and teams while ensuring consistency.

<!-- Card End -->

#fix
more context
ask if likely
<!-- Card Start -->

### Front

Which Amazon Bedrock models are best suited for code generation tasks? (Choose 2)
- A. Amazon Titan Text models
- B. Anthropic Claude models
- C. Amazon Titan Embeddings models
- D. AI21 Labs Jurassic models
- E. Cohere Command models

### Back

**Correct Answers**: B and E  
**Explanation**: Anthropic Claude models and Cohere Command models have strong capabilities for code generation and understanding programming tasks. Titan Text is more general-purpose, while Titan Embeddings and Jurassic have other specialties.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between batch and real-time inference?
- A. Batch inference is more accurate than real-time inference
- B. Batch inference processes multiple requests together, real-time processes individual requests
- C. Batch inference is only for image data, real-time is only for text data
- D. Batch inference requires GPU, real-time requires CPU

### Back

**Correct Answer**: B  
**Explanation**: Batch inference processes multiple data points together in scheduled jobs, optimizing for throughput, while real-time inference processes individual requests immediately, optimizing for low latency.

<!-- Card End -->

<!-- Card Start -->

### Front

Which AWS services support vector databases for embedding storage? (Choose 2)
- A. Amazon OpenSearch Service
- B. Amazon RDS
- C. Amazon Aurora with pgvector
- D. Amazon DynamoDB
- E. Amazon S3

### Back

**Correct Answers**: A and C  
**Explanation**: 

Amazon OpenSearch Service (A) provides native vector database capabilities with approximate k-nearest neighbor (k-NN) search using algorithms like HNSW and IVF for efficient high-dimensional vector searches with filtering capabilities. It scales to billions of vectors while maintaining sub-second query performance. 

Amazon Aurora PostgreSQL (C) supports the pgvector extension, enabling vector storage and similarity search operations directly within PostgreSQL using SQL syntax. This integration allows developers to store embeddings alongside structured data in the same database. 

Standard RDS (B) doesn't support vector operations natively, DynamoDB (D) is for key-value NoSQL without vector search capabilities, and S3 (E) is object storage without query capabilities for vector similarity.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of prompt templates in generative AI applications?
- A. To reduce model training time
- B. To create reusable prompt structures for consistent outputs
- C. To compress model size
- D. To encrypt sensitive data

### Back

**Correct Answer**: B  
**Explanation**: Prompt templates provide standardized structures that can be reused across different inputs, ensuring consistent formatting and improving the reliability and quality of model outputs.

<!-- Card End -->

<!-- Card Start -->

### Front

Which factors affect the cost of using Amazon Bedrock? (Choose 2)
- A. Number of input and output tokens
- B. Model selection and size
- C. AWS region where you deploy
- D. Time of day when making requests
- E. Number of AWS accounts in your organization

### Back

**Correct Answers**: A and B  
**Explanation**: Bedrock pricing is primarily based on token consumption (input and output tokens) and the specific model used, as different models have different pricing structures based on their capabilities and computational requirements.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary purpose of Amazon SageMaker Autopilot?
- A. To automatically deploy models to production
- B. To automatically build, train, and tune ML models
- C. To automatically label training data
- D. To automatically monitor model performance

### Back

**Correct Answer**: B  
**Explanation**: Amazon SageMaker Autopilot automates the machine learning process by analyzing your data, selecting appropriate algorithms, performing hyperparameter optimization, feature engineering, and model tuning. It supports classification and regression tasks, and creates up to 50 different pipeline candidates to identify the best model. Autopilot provides full transparency by generating Python notebooks with the code used to create models, enabling you to understand, customize, and reproduce the process. It can be used with minimal ML expertise through the Studio interface or programmatically via APIs, making ML accessible to developers without specialized ML knowledge while still providing control to experts.

<!-- Card End -->

<!-- Card Start -->

### Front

Which techniques are commonly used for model interpretability and explainability? (Choose 2)
- A. SHAP (SHapley Additive exPlanations)
- B. Increasing model complexity
- C. LIME (Local Interpretable Model-agnostic Explanations)
- D. Using larger datasets
- E. Adding more layers to neural networks

### Back

**Correct Answers**: A and C  
**Explanation**: SHAP (SHapley Additive exPlanations) (A) assigns importance values to each feature for specific predictions based on game theory principles. It provides consistent attribution values with mathematical backing and works across various model types. 

LIME (Local Interpretable Model-agnostic Explanations) (C) creates simplified interpretable models that approximate the behavior of complex models for individual predictions, showing how input features affect specific outputs. 

Both techniques are implemented in Amazon SageMaker Clarify for model explainability. 


Options B, D, and E actually make models less interpretable by increasing complexity. AWS emphasizes explainability as a key pillar of responsible AI to help build trust with users and meet regulatory requirements.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between zero-shot, one-shot, and few-shot learning in generative AI?
- A. They refer to different model architectures
- B. They refer to the number of examples provided in the prompt
- C. They refer to different training datasets
- D. They refer to different inference speeds

### Back

**Correct Answer**: B  
**Explanation**: These terms describe different prompt engineering techniques that vary by the number of examples included:
- Zero-shot learning: The prompt contains only instructions without any examples, relying on the model's pre-existing knowledge (e.g., "Classify this review as positive or negative: I really enjoyed this product.")
- One-shot learning: The prompt includes exactly one example to guide the model (e.g., "Classify these reviews. Positive: This was great! Negative: ?")
- Few-shot learning: The prompt includes multiple examples (typically 3-5) to establish a pattern for the model to follow.

These techniques are particularly important when using Amazon Bedrock or other foundation model services, allowing users to achieve different results without modifying the underlying model weights.

<!-- Card End -->

<!-- Card Start -->

### Front

Which AWS services can be used for document analysis and information extraction? (Choose 2)
- A. Amazon Textract
- B. Amazon Comprehend
- C. Amazon Polly
- D. Amazon Translate
- E. Amazon Transcribe

### Back

**Correct Answers**: A and B  
**Explanation**: Amazon Textract extracts text and data from documents (OCR and form understanding), while Amazon Comprehend analyzes text for entities, sentiment, and other insights. Together they provide comprehensive document analysis capabilities.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of Amazon SageMaker Model Monitor?
- A. To train models faster
- B. To detect data drift and model performance degradation
- C. To serve models for inference
- D. To create training datasets

### Back

**Correct Answer**: B  
**Explanation**: SageMaker Model Monitor continuously monitors deployed models to detect data drift, model drift, bias drift, and feature attribution drift, alerting when model performance may be degrading.

<!-- Card End -->

<!-- Card Start -->

### Front

Which considerations are important when designing prompts for generative AI? (Choose 2)
- A. Providing clear context and instructions
- B. Using as many words as possible
- C. Including relevant examples when helpful
- D. Always using technical jargon
- E. Making prompts as vague as possible

### Back

**Correct Answers**: A and C  
**Explanation**: Clear context and instructions help the model understand what's expected, while relevant examples (few-shot learning) can guide the model toward the desired output format and style.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary benefit of using Amazon SageMaker JumpStart?
- A. To reduce inference costs
- B. To access pre-trained models and solutions
- C. To automatically label data
- D. To monitor model performance

### Back

**Correct Answer**: B  
**Explanation**: SageMaker JumpStart provides access to hundreds of pre-trained models, built-in algorithms, and end-to-end ML solutions, enabling faster time-to-market for ML projects.

<!-- Card End -->

<!-- Card Start -->

### Front

Which factors should be considered when implementing MLOps practices? (Choose 2)
- A. Model versioning and reproducibility
- B. Automated testing and validation
- C. Using only cloud-based services
- D. Minimizing documentation
- E. Avoiding monitoring in production

### Back

**Correct Answers**: A and B  
**Explanation**: Model versioning ensures reproducibility and enables rollbacks, while automated testing validates models before deployment. These are core MLOps practices for reliable ML systems.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of embeddings in machine learning?
- A. To compress images
- B. To represent data as dense numerical vectors
- C. To encrypt sensitive information
- D. To reduce training time

### Back

**Correct Answer**: B  
**Explanation**: Embeddings convert discrete data (like words, images, or categorical features) into dense numerical vectors that capture semantic relationships and can be processed by ML algorithms.

<!-- Card End -->

#fix

<!-- Card Start -->

### Front

Which Amazon Bedrock features help with content filtering and safety? (Choose 2)
- A. Guardrails for content filtering
- B. Model customization options
- C. Prompt management capabilities
- D. Watermark detection for AI-generated content
- E. Knowledge base integration

### Back

**Correct Answers**: A and D  
**Explanation**: Guardrails filter harmful, inappropriate, or unwanted content in both inputs and outputs, while watermark detection helps identify AI-generated content, both contributing to safer AI deployments.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between discriminative and generative AI models?
- A. Discriminative models are faster than generative models
- B. Discriminative models classify/predict, generative models create new content
- C. Discriminative models are more accurate than generative models
- D. Discriminative models require more data than generative models

### Back

**Correct Answer**: B  
**Explanation**: Discriminative models learn to distinguish between different classes or predict outcomes (classification/regression), while generative models learn to create new content similar to their training data.

<!-- Card End -->

#fix  verify
<!-- Card Start -->

### Front

Which metrics are commonly used to evaluate generative AI model performance? (Choose 2)
- A. BLEU score for translation quality
- B. CPU utilization
- C. ROUGE score for summarization quality
- D. Network latency
- E. Storage capacity

### Back

**Correct Answers**: A and C  
**Explanation**: BLEU (Bilingual Evaluation Understudy) score (A) is the standard metric for evaluating machine translation quality. It measures the precision of n-grams (word sequences) in machine translations compared to reference human translations, with scores ranging from 0 to 1 (higher is better). ROUGE (Recall-Oriented Understudy for Gisting Evaluation) (C) evaluates summarization quality by measuring the overlap between generated summaries and reference summaries, focusing on recall (how much of the reference appears in the generated summary). In AWS, you can implement these metrics in custom evaluation tests within Amazon Bedrock Model Evaluation or SageMaker. 

Options B, D, and E are system performance metrics unrelated to output quality.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary purpose of Amazon Q for Business?
- A. To train custom ML models
- B. To provide AI-powered business intelligence and assistance
- C. To store large datasets
- D. To monitor infrastructure

### Back

**Correct Answer**: B  
**Explanation**: Amazon Q for Business is an enterprise-grade, generative AI-powered assistant specifically designed for business use. It integrates with enterprise systems, applications, and data repositories to provide contextual assistance to employees. Key capabilities include: answering questions about company data and policies, generating content like emails and documents based on internal knowledge, providing summaries of documents and meetings, troubleshooting issues and offering solutions, assisting with software development tasks, all while respecting company security policies and access controls. Unlike general AI assistants, Q for Business is specifically trained on your organization's internal information and maintains privacy and security requirements, making it different from both standard ML training tools (A) and basic data storage (C) or monitoring (D) solutions.

<!-- Card End -->
