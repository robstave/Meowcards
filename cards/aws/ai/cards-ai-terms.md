# AWS AI Practitioner Terms and Definitions

<!-- Card Start -->

### Front

What is model overfitting?

### Back

Model overfitting occurs when a machine learning model learns the training data too well, including its noise and random fluctuations, resulting in poor generalization to new data. An overfit model performs exceptionally well on training data but poorly on validation or test data.

AWS-flavored intuition

The model memorized CloudWatch logs instead of learning system behavior.

**Task Reference**: This concept is covered in Task Statement 4.1 under effects of bias and variance in responsible AI implementation.

<!-- Card End -->

<!-- Card Start -->

### Front

What is model underfitting?

### Back

Model underfitting occurs when a machine learning model is too simple to capture the underlying patterns and relationships in the training data, resulting in poor performance on both training and test data. An underfit model fails to learn the essential structure of the data.

**Characteristics**:
- High training error
- High validation/test error
- Model is too simple for the data complexity
- Insufficient training time or features

**Solutions**:
- Increase model complexity
- Add more features
- Train longer
- Reduce regularization


AWS-flavored intuition

You picked the cheapest tool for the job, but it can’t do the job at all.


**Task Reference**: This concept is covered in Task Statement 4.1 under effects of bias and variance in responsible AI implementation.

<!-- Card End -->

<!-- Card Start -->

### Front

How do bias and variance relate to underfitting and overfitting?

### Back

**High bias → underfitting**

**High variance → overfitting**

The goal is to balance bias and variance to generalize well.

**Explanation**:
- **Bias** refers to errors from overly simplistic assumptions in the learning algorithm. High bias causes the model to miss relevant patterns (underfitting).
- **Variance** refers to errors from sensitivity to small fluctuations in the training set. High variance causes the model to model the noise in the data (overfitting).

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
**Research Link**: [Amazon SageMaker Feature Store](https://aws.amazon.com/sagemaker/feature-store/)

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
**Research Link**: [Amazon SageMaker JumpStart](https://aws.amazon.com/sagemaker/jumpstart/)

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
**Research Link**: [Amazon SageMaker Model Cards](https://aws.amazon.com/sagemaker/model-cards/)

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

basically you are maximizing the area under the curve.  if its a flat line at 0.5, you are doing no better than random guessing.

![OpenAI Generated Image](https://images.openai.com/thumbnails/url/IS6BgXicu5mVUVJSUGylr5-al1xUWVCSmqJbkpRnoJdeXJJYkpmsl5yfq5-Zm5ieWmxfaAuUsXL0S7F0Tw7KMtY1K4-Pd_GszHeLCPdKNs_2qkpyCXdyLdMtrPAvjjcs9jMsKnJLqgr1jjBPNAoNVisGAH2XJk8)

Exam trap

High accuracy but low AUC
This often means:

Data imbalance

Model predicting the majority class

AWS takeaway:

AUC evaluates ranking quality, not just correctness.




**Task Reference**: This metric is mentioned in Task Statement 1.3 as one of the key model performance metrics.

<!-- Card End -->

<!-- Card Start -->

### Front

What does an AUC-ROC curve represent in machine learning?

### Back

The **AUC-ROC curve** (Area Under the Receiver Operating Characteristic Curve) is a performance measurement for classification problems at various threshold settings. It plots the **True Positive Rate (TPR)** against the **False Positive Rate (FPR)** at different threshold values.

**Key Points**:
- **True Positive Rate (TPR)**: Sensitivity or recall, measures the proportion of actual positives correctly identified.
- **False Positive Rate (FPR)**: Measures the proportion of actual negatives incorrectly identified as positive.
- **AUC (Area Under Curve)**: Represents the degree of separability. A higher AUC indicates a better model at distinguishing between positive and negative classes.

**How it is created**:
1. The model outputs probabilities for each data point belonging to the positive class.
2. These probabilities are sorted, and thresholds are applied to classify data points as positive or negative.
3. For each threshold, the TPR and FPR are calculated and plotted on the graph.
4. The curve is formed by connecting these points, and the area under this curve is computed to evaluate the model's ranking quality.

**Why it evaluates ranking quality**:
- The AUC-ROC curve measures how well the model ranks positive instances higher than negative ones.
- A perfect model will have an AUC of 1, meaning it ranks all positive instances above all negative ones.
- A random model will have an AUC of 0.5, indicating no ability to distinguish between classes.

![AUC-ROC Curve](https://media.geeksforgeeks.org/wp-content/uploads/20230410164437/AUC-ROC-Curve.webp)

**Task Reference**: This concept is covered in Task Statement 4.3 under model evaluation metrics.

<!-- Card End -->

<!-- Card Start -->

### Front

A fraud detection model has 99% accuracy but an AUC of 0.55. What does this indicate?

### Back

The dataset is likely imbalanced, and the model is predicting the majority class well but is poor at distinguishing fraud cases.

**Explanation**:
- **99% accuracy** suggests the model is correct most of the time, but in fraud detection, legitimate transactions typically make up 99%+ of the data
- **AUC of 0.55** (close to 0.5 random guessing) indicates the model has almost no ability to rank fraudulent transactions higher than legitimate ones
- The model is likely just predicting "not fraud" for everything, achieving high accuracy by default

**Key insight**: With imbalanced datasets, accuracy is misleading. AUC, precision, recall, and F1 score are much better metrics.

**Task Reference**: This concept is covered in Task Statement 4.3 under model evaluation metrics and understanding appropriate metrics for different scenarios.

<!-- Card End -->

<!-- Card Start -->

### Front

Which metric is most appropriate for evaluating a binary classifier across multiple thresholds?

### Back

AUC (Area Under the ROC Curve), because it measures ranking quality independent of classification threshold.

**Key advantages**:
- **Threshold-independent**: Evaluates performance across all possible thresholds simultaneously
- **Ranking quality**: Measures how well the model ranks positive instances above negative ones
- **Robust to imbalance**: Unlike accuracy, AUC accounts for class imbalance
- **Single summary metric**: Provides one value (0 to 1) representing overall classifier performance

**Comparison**: Metrics like accuracy, precision, and recall depend on a specific threshold, making them less suitable for comparing classifiers when the optimal threshold is unknown.

**Task Reference**: This concept is covered in Task Statement 4.3 under model evaluation metrics.

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
**Research Link**: [AWS Audit Manager](https://aws.amazon.com/audit-manager/)

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

<!-- Card Start -->

### Front

What is model underfitting?

### Back

Model underfitting occurs when a machine learning model is too simple to capture the underlying patterns in the data, resulting in poor performance on both training and test data. Key characteristics include:
- High bias (strong assumptions about data)
- Low variance
- Poor performance on training data
- Similarly poor performance on validation/test data
- Inability to capture important relationships in the data

Common causes:
- Model is too simple for the complexity of the data
- Insufficient training time
- Not enough relevant features
- Too much regularization

**Task Reference**: This concept is covered in Task Statement 4.1 under effects of bias and variance in responsible AI implementation.

<!-- Card End -->

<!-- Card Start -->

### Front

What is Amazon Rekognition?

### Back

Amazon Rekognition is a computer vision service that enables you to analyze images and videos. Key capabilities include:
- Object and scene detection
- Face detection and analysis
- Text extraction from images
- Content moderation
- Custom labels for specific use cases
- Real-time video analysis  
**Research Link**: [Amazon Rekognition](https://aws.amazon.com/rekognition/)

**Task Reference**: This service is referenced in Task Statement 1.2 as one of AWS's managed AI services for computer vision applications.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the ROUGE score?

### Back

ROUGE (Recall-Oriented Understudy for Gisting Evaluation) is a set of metrics used to evaluate automatically generated summaries and translations. Key aspects include:
- Measures overlap between generated and reference texts
- Multiple variants (ROUGE-N, ROUGE-L, ROUGE-S)
- Focus on recall (how much of the reference appears in the generated text)
- Widely used for summarization tasks

**Task Reference**: This metric is mentioned in Task Statement 3.4 for evaluating foundation model performance, particularly for summarization tasks.

<!-- Card End -->

<!-- Card Start -->

### Front

A text summarization model has a low ROUGE score but users find the summaries helpful. Why?

### Back

ROUGE measures n-gram overlap, not semantic meaning or usefulness. Valid summaries can score poorly if worded differently.

**Key insights**:
- **ROUGE limitation**: Only counts exact word/phrase matches between generated and reference summaries
- **Semantic equivalence ignored**: "The company profits increased" vs "The firm saw revenue growth" = low ROUGE, same meaning
- **User value differs**: Clarity, brevity, and relevance matter more than matching reference text
- **Paraphrasing penalty**: Better vocabulary or alternative phrasing reduces ROUGE scores

**Implication**: Always complement automated metrics with human evaluation to capture actual quality and usefulness.

**Task Reference**: This relates to Task Statement 3.4 (model evaluation metrics) and Task Statement 4.1 (understanding limitations of metrics in responsible AI).

<!-- Card End -->

<!-- Card Start -->

### Front

What is Amazon Comprehend?

### Back

Amazon Comprehend is a natural language processing (NLP) service that uses machine learning to find insights and relationships in text. Key features include:
- Entity recognition
- Key phrase extraction
- Sentiment analysis
- Language detection
- Topic modeling
- Custom classification
- PII detection

**Task Reference**: This service is referenced in Task Statement 1.2 under AWS managed AI/ML services, particularly for NLP applications.  
**Research Link**: [Amazon Comprehend](https://aws.amazon.com/comprehend/)

<!-- Card End -->

<!-- Card Start -->

### Front

What is instruction-based fine-tuning?

### Back

Instruction-based fine-tuning is a technique for adapting foundation models to better follow specific instructions and commands. Key aspects include:
- Training on instruction-response pairs
- Improving task comprehension
- Enhancing model's ability to follow directions
- Better alignment with user intent
- Increased reliability in task execution

**Task Reference**: This concept is covered in Task Statement 3.3 under methods for fine-tuning foundation models.

<!-- Card End -->

<!-- Card Start -->

### Front

What is AWS Inspector?

### Back

AWS Inspector is an automated security assessment service that helps improve the security and compliance of applications. In the context of AI/ML:
- Vulnerability assessments
- Security best practice checks
- Compliance validation
- Continuous monitoring
- Risk scoring and prioritization

**Task Reference**: This service is mentioned in Task Statement 5.2 as a tool for governance and regulation compliance in AI systems.  
**Research Link**: [Amazon Inspector](https://aws.amazon.com/inspector/)

<!-- Card End -->

<!-- Card Start -->

### Front

What makes BERT different from earlier NLP models?

### Back

BERT uses a transformer architecture with bidirectional self-attention, allowing it to understand context from both left and right simultaneously.

**Key differences**:
- **Bidirectional**: Unlike earlier models (like GPT-1) that only read left-to-right, BERT processes text in both directions
- **Transformer-based**: Uses self-attention mechanisms instead of recurrent architectures (RNNs/LSTMs)
- **Pre-training approach**: Uses masked language modeling and next sentence prediction
- **Contextual embeddings**: Generates different embeddings for the same word based on context

**Task Reference**: This concept relates to Task Statement 3.2 under understanding foundation model architectures and their capabilities.

<!-- Card End -->

<!-- Card Start -->

### Front

When is using a BERT-based model not appropriate?

### Back

When latency, cost, or simplicity are critical and a simpler NLP approach meets requirements.

❗ AWS prefers right-sized solutions, not "biggest model wins."

**Situations where simpler alternatives are better**:
- **Real-time applications** requiring sub-millisecond latency
- **Resource-constrained environments** with limited compute/memory
- **Simple tasks** like keyword matching or basic sentiment analysis
- **Cost-sensitive deployments** where simpler models provide sufficient accuracy
- **High-throughput systems** processing millions of requests

**Better alternatives**:
- Rule-based systems for deterministic tasks
- Traditional ML (logistic regression, random forest) for structured features
- Smaller models (DistilBERT, TinyBERT) for reduced complexity
- AWS services like Amazon Comprehend for managed simplicity

**Task Reference**: This relates to Task Statement 2.1 (selecting appropriate model types) and Task Statement 2.3 (inferencing strategies and cost considerations).

<!-- Card End -->

<!-- Card Start -->

### Front

Which metric is most appropriate for evaluating text summarization?

### Back

ROUGE, because it compares generated summaries against reference summaries.

⚠️ Accuracy and AUC are incorrect but tempting answers.

**Why ROUGE**:
- Designed specifically for summarization tasks
- Measures overlap between generated and reference text
- Captures how well key content is preserved
- Standard metric in NLP summarization research

**Why not other metrics**:
- **Accuracy**: Used for classification, not generation tasks
- **AUC**: Used for binary classification ranking, not text generation
- **BLEU**: Better suited for translation than summarization

**Task Reference**: This concept is covered in Task Statement 3.4 under selecting appropriate metrics for different model types and tasks.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary goal of model evaluation in a production ML system?

### Back

To ensure the model generalizes well to unseen data and meets business requirements—not to maximize training accuracy.

**Key principles**:
- **Generalization over memorization**: The model must perform well on new data, not just training data
- **Business alignment**: Technical metrics must translate to business value (e.g., reduced fraud, improved customer satisfaction)
- **Real-world performance**: Validation on representative production-like data
- **Trade-offs**: Balance accuracy, latency, cost, and interpretability

**Common pitfall**: Overfitting to training data produces impressive training metrics but poor real-world performance.

**Task Reference**: This concept is foundational to Task Statement 4.1 (responsible AI) and Task Statement 4.3 (model evaluation and monitoring).

<!-- Card End -->


