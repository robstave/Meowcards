# AWS AI Practitioner - Additional Practice Cards

<!-- Card Start -->

### Front

What is Amazon Bedrock primarily used for?
- A. Hosting web applications
- B. Building generative AI applications using foundation models
- C. Managing database backups
- D. Monitoring network traffic

### Back

**Correct Answer**: B  
Explanation: Amazon Bedrock is a fully managed service that provides access to foundation models from leading AI companies for building generative AI applications. It's referenced in Task Statement 2.3.  
**Research Link**: [Amazon Bedrock](https://aws.amazon.com/bedrock/)

<!-- Card End -->
<!-- Card Start -->

### Front

Which AWS service would you use to implement human review of ML predictions?
- A. Amazon Rekognition
- B. Amazon Augmented AI (A2I)
- C. Amazon Polly
- D. AWS Lambda

### Back

**Correct Answer**: B  
Explanation: Amazon Augmented AI (A2I) makes it easy to build workflows for human review of ML predictions. This is particularly useful for high-stakes predictions or when model confidence is low.

**Task Reference**: Covered in Task Statement 4.1 as a tool for responsible AI implementation.  
**Research Link**: [Amazon A2I](https://aws.amazon.com/augmented-ai/)

<!-- Card End -->
<!-- Card Start -->

### Front

What is the primary purpose of Amazon SageMaker Clarify?
- A. Text-to-speech conversion
- B. Detecting bias and explaining model predictions
- C. Image classification
- D. Language translation

### Back

**Correct Answer**: B  
Explanation: Amazon SageMaker Clarify helps detect bias in ML models and explain predictions using techniques like SHAP (SHapley Additive exPlanations) and LIME (Local Interpretable Model-agnostic Explanations).

**Task Reference**: Referenced in Task Statement 4.1 for monitoring bias, trustworthiness, and truthfulness.  
**Research Link**: [Amazon SageMaker Clarify](https://aws.amazon.com/sagemaker/clarify/)

<!-- Card End -->
<!-- Card Start -->

### Front

What is a key characteristic of Retrieval Augmented Generation (RAG)?
- A. It requires no external data sources
- B. It combines document retrieval with generation to ground responses in facts
- C. It only works with image data
- D. It eliminates the need for embeddings

### Back

**Correct Answer**: B  
Explanation: RAG retrieves relevant documents from a knowledge base and uses them to augment the context for generation, helping ground AI responses in factual information and reduce hallucinations.

**Task Reference**: This is covered in Task Statement 3.1 under design considerations for foundation model applications.  
**Research Link**: [What is RAG?](https://aws.amazon.com/what-is/retrieval-augmented-generation/)

<!-- Card End -->
<!-- Card Start -->

### Front

Which AWS services can store embeddings for vector search? (Choose 2)
- A. Amazon S3
- B. Amazon OpenSearch Service
- C. Amazon Aurora with pgvector
- D. Amazon Route 53
- E. AWS CloudTrail

### Back

**Correct Answer**: B and C  
Explanation: Amazon OpenSearch Service and Amazon Aurora (with pgvector extension) are mentioned in Task Statement 3.1 as services that can store embeddings within vector databases for similarity search in RAG applications.

Other options that support vector embeddings (from the task statement):
- Amazon Neptune
- Amazon DocumentDB (with MongoDB compatibility)
- Amazon RDS for PostgreSQL  
**Research Link**: [Vector Databases on AWS](https://aws.amazon.com/nosql/vector-databases/)

<!-- Card End -->
<!-- Card Start -->

### Front

What is prompt injection in the context of AI security?
- A. A method to improve model accuracy
- B. A technique for faster inference
- C. A security attack where malicious instructions are inserted into prompts
- D. A way to reduce model bias

### Back

**Correct Answer**: C  
Explanation: Prompt injection is a security vulnerability where attackers insert malicious instructions into prompts to manipulate model behavior, potentially exposing sensitive data or bypassing safety controls.

**Task Reference**: Referenced in Task Statement 5.1 under security considerations for AI systems.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the role of agents in Amazon Bedrock?
- A. To monitor infrastructure costs
- B. To orchestrate multi-step tasks and workflows
- C. To train new foundation models
- D. To manage user authentication

### Back

**Correct Answer**: B  
Explanation: Agents for Amazon Bedrock can orchestrate multi-step tasks by breaking down user requests, calling external APIs, and combining multiple foundation model calls to complete complex workflows.

**Task Reference**: Referenced in Task Statement 3.1 under the role of agents in multi-step tasks.  
**Research Link**: [Agents for Amazon Bedrock](https://aws.amazon.com/bedrock/agents/)

<!-- Card End -->
<!-- Card Start -->

### Front

What is jailbreaking in the context of generative AI?
- A. Upgrading model hardware
- B. Attempting to bypass a model's safety guardrails through crafted prompts
- C. Optimizing model performance
- D. Reducing inference latency

### Back

**Correct Answer**: B  
Explanation: Jailbreaking refers to attempts to bypass or circumvent a model's built-in safety measures and content policies through specially crafted prompts.

**Task Reference**: Listed in Task Statement 3.2 as a potential risk of prompt engineering.

<!-- Card End -->
<!-- Card Start -->

### Front

What are SHAP and LIME used for in machine learning?
- A. Model training acceleration
- B. Data preprocessing
- C. Explaining individual model predictions
- D. Hyperparameter optimization

### Back

**Correct Answer**: C  
Explanation: SHAP (SHapley Additive exPlanations) and LIME (Local Interpretable Model-agnostic Explanations) are techniques used by Amazon SageMaker Clarify to explain why a model made specific predictions, enhancing model interpretability.

**Task Reference**: Related to Task Statement 4.2 on transparent and explainable models.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the purpose of Amazon Macie in the context of AI systems?
- A. Training computer vision models
- B. Discovering and protecting sensitive data
- C. Converting speech to text
- D. Generating images

### Back

**Correct Answer**: B  
Explanation: Amazon Macie uses machine learning to automatically discover, classify, and protect sensitive data stored in AWS. In AI contexts, it helps ensure that training data and model outputs don't expose sensitive information.

**Task Reference**: Listed in Task Statement 5.1 as a service for securing AI systems.  
**Research Link**: [Amazon Macie](https://aws.amazon.com/macie/)

<!-- Card End -->
<!-- Card Start -->

### Front

What is continuous pre-training in foundation models?
- A. Training a model from scratch
- B. Regularly updating models with new data while preserving existing knowledge
- C. One-time model deployment
- D. Reducing model size

### Back

**Correct Answer**: B  
Explanation: Continuous pre-training involves regularly updating foundation models with new data to maintain relevance and performance while preserving the knowledge they've already learned.

**Task Reference**: This concept is mentioned in Task Statement 3.3 as part of model maintenance strategies.

<!-- Card End -->
<!-- Card Start -->

### Front

What does temperature control in generative AI model settings?
- A. Server cooling requirements
- B. Training speed
- C. Randomness and creativity in outputs
- D. Model memory usage

### Back

**Correct Answer**: C  
Explanation: Temperature is an inference parameter that controls the randomness of model outputs. Lower values (e.g., 0.1) produce more deterministic, focused responses, while higher values (e.g., 1.0) produce more creative, diverse outputs.

**Task Reference**: Referenced in Task Statement 3.1 under the effect of inference parameters on model responses.

<!-- Card End -->
<!-- Card Start -->

### Front

Which of the following is NOT a feature of responsible AI?
- A. Fairness
- B. Transparency
- C. Maximizing data collection
- D. Safety

### Back

**Correct Answer**: C  
Explanation: Maximizing data collection is not a feature of responsible AI. Responsible AI emphasizes fairness, transparency, safety, inclusivity, robustness, and veracity—not indiscriminate data collection.

**Task Reference**: Task Statement 4.1 lists features of responsible AI including bias awareness, fairness, inclusivity, robustness, safety, and veracity.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the primary purpose of AWS Artifact in the context of AI governance?
- A. Storing AI models
- B. Providing access to AWS compliance reports and agreements
- C. Training foundation models
- D. Creating vector embeddings

### Back

**Correct Answer**: B  
Explanation: AWS Artifact provides on-demand access to AWS security and compliance reports and select online agreements, helping organizations demonstrate compliance for AI systems.

**Task Reference**: Listed in Task Statement 5.2 as a service for governance and compliance.  
**Research Link**: [AWS Artifact](https://aws.amazon.com/artifact/)

<!-- Card End -->
<!-- Card Start -->

### Front

What is data poisoning in the context of AI security?
- A. Encrypting training data
- B. Corrupting or manipulating training data to compromise model behavior
- C. Deleting unused datasets
- D. Compressing data for storage

### Back

**Correct Answer**: B  
Explanation: Data poisoning is an attack where training data is intentionally corrupted or manipulated to make the model learn incorrect patterns or exhibit malicious behavior.

**Task Reference**: Related to Task Statement 3.2 under risks of prompt engineering (poisoning).

<!-- Card End -->
<!-- Card Start -->

### Front

What is the purpose of Amazon SageMaker Ground Truth?
- A. Model deployment
- B. Creating high-quality labeled datasets
- C. Real-time inference
- D. Cost monitoring

### Back

**Correct Answer**: B  
Explanation: Amazon SageMaker Ground Truth helps create high-quality labeled datasets for training ML models by combining human labeling with active learning and automated labeling.

**Task Reference**: Related to Task Statement 1.3 regarding data collection and labeling for ML pipelines.  
**Research Link**: [Amazon SageMaker Ground Truth](https://aws.amazon.com/sagemaker/groundtruth/)

<!-- Card End -->
<!-- Card Start -->

### Front

What is the key difference between zero-shot and few-shot prompting?
- A. Zero-shot uses more examples than few-shot
- B. Zero-shot uses only instructions while few-shot includes examples
- C. They are the same technique
- D. Few-shot never uses examples

### Back

**Correct Answer**: B  
Explanation: Zero-shot prompting provides only instructions to the model without examples. Few-shot prompting includes one or more examples in the prompt to demonstrate the desired output format or behavior.

**Task Reference**: Referenced in Task Statement 3.2 under prompt engineering techniques.

<!-- Card End -->
<!-- Card Start -->

### Front

What AWS service helps continuously audit AWS usage for compliance?
- A. Amazon Rekognition
- B. AWS Audit Manager
- C. Amazon Polly
- D. AWS Lambda

### Back

**Correct Answer**: B  
Explanation: AWS Audit Manager helps continuously audit AWS usage to assess risk and compliance with regulations and industry standards, including for AI/ML workloads.

**Task Reference**: Listed in Task Statement 5.2 as a service for governance and compliance.  
**Research Link**: [AWS Audit Manager](https://aws.amazon.com/audit-manager/)

<!-- Card End -->
<!-- Card Start -->

### Front

What is the advantage of using managed API services for ML model deployment?
- A. No internet connection required
- B. Reduced operational overhead and automatic scaling
- C. Free unlimited usage
- D. Guaranteed 100% accuracy

### Back

**Correct Answer**: B  
Explanation: Managed API services for ML models reduce operational overhead by handling infrastructure, scaling, and maintenance, allowing teams to focus on application development.

**Task Reference**: Referenced in Task Statement 1.3 under methods to use a model in production.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the purpose of labeling in the context of fine-tuning foundation models?
- A. Organizing code files
- B. Creating training examples for the model to learn from
- C. Monitoring costs
- D. Managing user permissions

### Back

**Correct Answer**: B  
Explanation: Labeling creates structured training examples (input-output pairs) that the model learns from during fine-tuning, helping it adapt to specific tasks or domains.

**Task Reference**: Referenced in Task Statement 3.3 under preparing data for fine-tuning (labeling, representativeness).

<!-- Card End -->
<!-- Card Start -->

### Front

Which metric would you use to evaluate a text summarization model?
- A. Accuracy
- B. ROUGE score
- C. Mean Squared Error
- D. Conversion rate

### Back

**Correct Answer**: B  
Explanation: ROUGE (Recall-Oriented Understudy for Gisting Evaluation) measures overlap between generated and reference summaries, making it ideal for evaluating summarization tasks.

**Task Reference**: Listed in Task Statement 3.4 as a metric for evaluating foundation model performance.  
**Research Link**: [Model Evaluation in Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/model-evaluation.html)

<!-- Card End -->
