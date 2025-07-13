# AWS AI Practitioner Terms and Definitions

<!-- Card Start -->

### Front

What is model overfitting?

### Back

Model overfitting occurs when a machine learning model learns the training data too well, including its noise and random fluctuations, resulting in poor generalization to new data. An overfit model performs exceptionally well on training data but poorly on validation or test data.

**Task Reference**: This concept is covered in Task Statement 4.1 under effects of bias and variance in responsible AI implementation.

<!-- Card End -->

<!-- Card Start -->

### Front

What is model latent space?

### Back

Model latent space refers to the high-dimensional internal representation space where a model organizes and structures its learned concepts and patterns. In the context of foundation models, it's where semantic relationships and abstract features are encoded, enabling the model to understand and generate content.

**Task Reference**: This concept is referenced in Task Statement 3.2 under concepts of prompt engineering and model architecture.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Amazon SageMaker Feature Store?

### Back

Amazon SageMaker Feature Store is a centralized repository for storing, managing, and sharing machine learning features. It enables feature reuse across teams, ensures consistency in feature transformations, and provides both online and offline storage for training and inference.

Key capabilities:
- Feature versioning and tracking
- Real-time feature serving
- Point-in-time feature retrieval
- Feature sharing across teams

<!-- Card End -->

<!-- Card Start -->

### Front

What is Amazon SageMaker JumpStart?

### Back

Amazon SageMaker JumpStart is a capability that provides pre-built, solution-oriented machine learning models, algorithms, and example notebooks. It helps developers quickly get started with machine learning by providing:
- Pre-trained models for common use cases
- Solution templates
- Example notebooks and tutorials
- Built-in algorithms

**Task Reference**: This service is relevant to Task Statement 2.3 as it facilitates rapid development and deployment of AI solutions.

<!-- Card End -->

<!-- Card Start -->

### Front

What are Amazon SageMaker Model Cards?

### Back

Amazon SageMaker Model Cards are standardized model documentation templates that help document and track essential information about machine learning models, including:
- Model purpose and intended use
- Training data characteristics
- Performance metrics and evaluation results
- Model limitations and biases
- Deployment considerations

**Task Reference**: This feature is covered in Task Statement 4.2 as a tool for model transparency and documentation.

<!-- Card End -->

<!-- Card Start -->

### Front

What is in-context learning?

### Back

In-context learning is a technique where foundation models adapt their behavior based on examples or instructions provided in the prompt, without changing the model's weights. Key aspects include:

1. Types:
   - Zero-shot: Using only instructions
   - One-shot: Using one example
   - Few-shot: Using multiple examples

2. Benefits:
   - No additional training required
   - Quick adaptation to new tasks
   - Flexible implementation

**Task Reference**: This concept is covered in Task Statement 3.1 under foundation model customization approaches.

<!-- Card End -->

<!-- Card Start -->

### Front

What is AUC (Area Under the Curve)?

### Back

AUC (Area Under the Curve) is a performance metric that measures the area under the ROC (Receiver Operating Characteristic) curve. It indicates how well a model can distinguish between classes, with values ranging from 0 to 1, where:
- 1.0 represents perfect classification
- 0.5 represents random chance
- < 0.5 represents worse than random

**Task Reference**: This metric is mentioned in Task Statement 1.3 as one of the key model performance metrics.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the F1 score?

### Back

F1 score is a performance metric that combines precision and recall into a single value, providing a balanced measure of a model's accuracy. It is particularly useful when dealing with imbalanced datasets.

F1 = 2 * (Precision * Recall) / (Precision + Recall)

**Task Reference**: This is referenced in Task Statement 3.1 as a technical performance metric, distinct from business metrics.

<!-- Card End -->

<!-- Card Start -->

### Front

What is PartyRock?

### Back

PartyRock is Amazon's Bedrock Playground that provides a user-friendly environment for experimenting with and developing generative AI applications. It allows users to:
- Test different foundation models
- Experiment with prompts
- Prototype AI applications
- Share and collaborate on AI projects

**Task Reference**: Referenced in Task Statement 2.3 as a service for developing generative AI applications.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Reinforcement Learning?

### Back

Reinforcement Learning is a machine learning approach where an agent learns to make decisions by interacting with an environment. Key components include:
- Agent: The decision-maker
- Environment: The context in which the agent operates
- Actions: Choices the agent can make
- Rewards: Feedback signals that guide learning
- Policy: The strategy the agent learns

This type of learning is particularly useful for tasks involving sequential decision-making and optimization.

<!-- Card End -->

<!-- Card Start -->

### Front

What is AWS Audit Manager?

### Back

AWS Audit Manager helps continuously audit AWS usage to assess risk and compliance with various regulations and industry standards. In the context of AI/ML:
- Tracks model development and deployment
- Monitors compliance with AI governance policies
- Creates audit-ready reports
- Maintains audit trails for model lifecycles

**Task Reference**: This service is referenced in Task Statement 5.2 for governance and compliance monitoring.

<!-- Card End -->

<!-- Card Start -->

### Front

What is BERTScore?

### Back

BERTScore is an automatic evaluation metric for text generation that uses BERT embeddings to compute similarity scores between generated and reference texts. It provides a more nuanced evaluation than traditional metrics by considering:
- Semantic similarity
- Contextual understanding
- Word importance

**Task Reference**: This metric is mentioned in Task Statement 3.4 for evaluating foundation model outputs.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Transfer Learning?

### Back

Transfer Learning is a technique where knowledge learned in one domain is applied to a different but related domain. In the context of foundation models:
- Leverages pre-trained model knowledge
- Reduces training time and data requirements
- Improves performance on specialized tasks

**Task Reference**: This concept is covered in Task Statement 3.3 under model customization approaches.

<!-- Card End -->

<!-- Card Start -->

### Front

What is SageMaker Model Monitor?

### Back

Amazon SageMaker Model Monitor is a capability that automatically monitors machine learning models in production by:
- Detecting concept drift in data and model predictions
- Monitoring model quality
- Tracking bias drift
- Alerting when metrics deviate from baselines
- Providing detailed reports on model behavior

**Task Reference**: This capability is relevant to Task Statement 4.1 for monitoring model behavior and bias in production.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Conversion Rate in the context of AI applications?

### Back

Conversion Rate is a business metric that measures the percentage of users who complete a desired action. In AI applications, it helps evaluate the business impact of AI solutions by measuring:
- User engagement
- Action completion
- Business goal achievement

**Task Reference**: This metric is mentioned in Task Statement 2.2 as a business metric for evaluating AI solution effectiveness.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Continuous Pre-training?

### Back

Continuous Pre-training is a technique where foundation models are regularly updated with new data to maintain their relevance and performance. Key aspects include:
- Regular model updates with new data
- Preservation of existing knowledge
- Adaptation to changing patterns
- Maintenance of model performance

**Task Reference**: This concept is mentioned in Task Statement 3.3 as part of model maintenance and updating strategies.

<!-- Card End -->

<!-- Card Start -->

### Front

What is a Foundation Model?

### Back

A foundation model is a large-scale AI model trained on vast amounts of data that can be adapted for a wide variety of tasks. Key characteristics include:
- Pre-trained on broad datasets
- Can be fine-tuned for specific tasks
- Supports multiple modalities (text, images, etc.)
- Serves as a base for various applications

**Task Reference**: This concept is fundamental to Task Statement 2.1 and is central to understanding generative AI applications.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Prompt Engineering?

### Back

Prompt engineering is the process of designing and optimizing input instructions for AI models to generate desired outputs. Key aspects include:
- Crafting clear and specific instructions
- Using examples (few-shot learning)
- Managing context and constraints
- Implementing best practices for response quality

**Task Reference**: This is covered in Task Statement 2.1 as a foundational generative AI concept and detailed in Task Statement 3.2.

<!-- Card End -->

<!-- Card Start -->

### Front

What are Embeddings?

### Back

Embeddings are dense vector representations of data (text, images, etc.) that capture semantic relationships and meanings in a high-dimensional space. Key uses include:
- Semantic search
- Content similarity comparison
- Feature representation for ML models
- Knowledge retrieval in RAG applications

**Task Reference**: Referenced in Task Statement 2.1 as a foundational generative AI concept and important for Task Statement 3.1 regarding vector databases.

<!-- Card End -->

<!-- Card Start -->

### Front

What is MLOps?

### Back

MLOps (Machine Learning Operations) is a set of practices that combines ML, DevOps, and data engineering to deploy and maintain ML models in production. Key components include:
- Experimentation management
- Reproducible processes
- Scalable systems
- Model monitoring and retraining
- Version control for models and data

**Task Reference**: This concept is covered in Task Statement 1.3 under fundamental concepts of ML operations.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Hallucination in AI models?

### Back

Hallucination refers to when AI models generate false or unsupported information that appears plausible but isn't factual. It's a key limitation of generative AI that needs to be managed through:
- Proper prompt engineering
- Use of RAG to ground responses in facts
- Implementation of guardrails
- Output validation

**Task Reference**: Listed in Task Statement 2.2 as one of the disadvantages of generative AI solutions.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Fine-tuning in the context of Foundation Models?

### Back

Fine-tuning is the process of adapting a pre-trained model to a specific task or domain by training it on additional targeted data. Key aspects include:
- Preserving general knowledge while adding specific capabilities
- Requiring less data than full training
- Improving performance on domain-specific tasks
- Maintaining model architecture while updating weights

**Task Reference**: Detailed in Task Statement 3.3 as a key element of foundation model customization.

<!-- Card End -->

<!-- Card Start -->

### Front

What are Guardrails in Amazon Bedrock?

### Back

Guardrails are safety measures implemented in Amazon Bedrock to control and filter AI model outputs. They help:
- Block harmful or inappropriate content
- Protect sensitive information
- Enforce topic boundaries
- Maintain output quality and safety
- Ensure responsible AI use

**Task Reference**: Mentioned in Task Statement 4.1 as a tool for implementing responsible AI features.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Data Lineage?

### Back

Data lineage is the documentation and tracking of data's origin, movement, and transformations throughout its lifecycle. Key aspects include:
- Source documentation
- Data transformation tracking
- Usage history
- Compliance documentation
- Impact analysis capability

**Task Reference**: Referenced in Task Statement 5.1 under source citation and documenting data origins.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Model Drift?

### Back

Model drift occurs when a model's performance degrades over time due to changes in the real-world data patterns. Types include:
- Concept drift: Changes in the relationship between input and output
- Data drift: Changes in the distribution of input data
- Feature drift: Changes in the meaning or relevance of features

**Task Reference**: This concept is implicit in Task Statement 1.3 under model monitoring and Task Statement 4.1 under model behavior monitoring.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Human-Centered Design in AI?

### Back

Human-Centered Design in AI is an approach that prioritizes human needs, capabilities, and experiences in the development of AI systems. Key principles include:
- User needs first
- Transparency in AI decisions
- Intuitive interfaces
- Ethical considerations
- Accessibility and inclusivity

**Task Reference**: This concept is explicitly mentioned in Task Statement 4.2 under principles of human-centered design for explainable AI.

<!-- Card End -->
