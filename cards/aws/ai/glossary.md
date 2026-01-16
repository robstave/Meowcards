# AWS AI Practitioner Glossary

A comprehensive glossary of AI, ML, and AWS-specific terms for the AWS Certified AI Practitioner exam.

---

## A

**Algorithm**
A set of rules or instructions that a computer follows to solve a problem or perform a task. In ML, algorithms learn patterns from data.

**Amazon A2I (Augmented AI)**
AWS service that makes it easy to build workflows for human review of ML predictions.

**Amazon Bedrock**
A fully managed service for building generative AI applications using foundation models from leading AI companies.

**Amazon Comprehend**
AWS NLP service that uses machine learning to find insights in text including sentiment, entities, key phrases, and language detection.

**Amazon Kendra**
Intelligent search service powered by machine learning for enterprise document search.

**Amazon Lex**
AWS service for building conversational interfaces (chatbots) using voice and text.

**Amazon Personalize**
AWS service for creating real-time personalized recommendations.

**Amazon Polly**
AWS text-to-speech service that turns text into lifelike speech.

**Amazon Q**
AWS generative AI-powered assistant for workplace productivity and software development.

**Amazon Rekognition**
AWS service for image and video analysis using deep learning.

**Amazon SageMaker**
Fully managed service for building, training, and deploying machine learning models at scale.

**Amazon Textract**
AWS service that automatically extracts text, handwriting, and data from scanned documents.

**Amazon Transcribe**
AWS automatic speech recognition (ASR) service for converting speech to text.

**Amazon Translate**
Neural machine translation service for translating text between languages.

**AUC (Area Under the Curve)**
A performance metric that measures the area under the ROC curve, indicating how well a model distinguishes between classes (0.5 = random, 1.0 = perfect).

---

## B

**Batch Inference**
Processing multiple inputs at once, typically used for high-throughput, non-time-sensitive predictions.

**BERT (Bidirectional Encoder Representations from Transformers)**
A pre-trained transformer model for NLP tasks that considers context from both directions.

**BERTScore**
An evaluation metric that uses BERT embeddings to compute similarity between generated and reference texts.

**Bias (in ML)**
Systematic errors in model predictions that can lead to unfair outcomes, often arising from skewed training data or flawed assumptions.

**BLEU (Bilingual Evaluation Understudy)**
A metric for evaluating machine-translated text quality by comparing it to reference translations.

---

## C

**Chain-of-Thought Prompting**
A prompt engineering technique that encourages the model to show step-by-step reasoning.

**Chunking**
Breaking down large inputs into smaller, manageable pieces for processing by AI models.

**Classification**
A supervised learning task that predicts which category an input belongs to.

**Clustering**
An unsupervised learning technique that groups similar data points together.

**Computer Vision**
AI field focused on enabling computers to interpret and understand visual information from images and videos.

**Concept Drift**
When the relationship between input data and target output changes over time, degrading model performance.

**Continuous Pre-training**
Regularly updating foundation models with new data to maintain relevance and performance.

---

## D

**Data Drift**
Changes in the distribution of input data over time that can affect model performance.

**Data Lineage**
Documentation tracking data's origin, movement, and transformations throughout its lifecycle.

**Deep Learning**
A subset of ML using neural networks with many layers to learn hierarchical representations of data.

**Diffusion Model**
A type of generative model that learns to create data by reversing a gradual noising process, commonly used for image generation.

---

## E

**Embeddings**
Dense vector representations of data (text, images) that capture semantic relationships in high-dimensional space.

**Exploratory Data Analysis (EDA)**
The process of analyzing datasets to understand their characteristics before model training.

---

## F

**F1 Score**
A performance metric combining precision and recall: F1 = 2 × (Precision × Recall) / (Precision + Recall).

**Feature Engineering**
Creating or transforming input features to improve model performance.

**Few-Shot Learning**
Providing a model with a few examples in the prompt to demonstrate the desired output format.

**Fine-Tuning**
Adapting a pre-trained model to a specific task by training on additional targeted data.

**Foundation Model**
A large-scale AI model trained on vast datasets that can be adapted for various downstream tasks.

---

## G

**Generative AI**
AI systems that can create new content (text, images, audio, code) based on learned patterns.

**Guardrails (Amazon Bedrock)**
Safety measures to control and filter AI model outputs, blocking harmful content and enforcing topic boundaries.

---

## H

**Hallucination**
When AI models generate false or unsupported information that appears plausible but isn't factual.

**Human-Centered Design**
An approach prioritizing human needs, capabilities, and experiences in AI system development.

**Hyperparameter Tuning**
The process of finding optimal configuration settings for a ML model.

---

## I

**In-Context Learning**
Technique where models adapt behavior based on examples in the prompt without changing model weights.

**Inference**
The process of using a trained model to make predictions on new data.

**Instruction Tuning**
Fine-tuning technique using instruction-response pairs to improve a model's ability to follow directions.

---

## L

**Large Language Model (LLM)**
A type of foundation model trained on vast text data, capable of understanding and generating human-like text.

**Latent Space**
The high-dimensional internal representation space where a model organizes learned concepts and patterns.

---

## M

**Machine Learning (ML)**
A subset of AI where systems learn patterns from data without being explicitly programmed.

**MLOps**
Practices combining ML, DevOps, and data engineering to deploy and maintain ML models in production.

**Model Cards (SageMaker)**
Standardized documentation templates for tracking information about ML models including purpose, performance, and limitations.

**Model Drift**
Performance degradation over time due to changes in real-world data patterns.

**Model Monitor (SageMaker)**
Capability for automatically monitoring ML models in production for drift and quality issues.

**Multi-Modal Model**
A model that can process and generate multiple types of data (text, images, audio) simultaneously.

---

## N

**Natural Language Processing (NLP)**
AI field focused on enabling computers to understand, interpret, and generate human language.

**Neural Network**
A computing system inspired by biological neurons, consisting of interconnected layers that process information.

**Nondeterminism**
The property of producing different outputs for the same input, common in generative AI models.

---

## O

**One-Shot Learning**
Providing a model with a single example to demonstrate the desired task or format.

**Overfitting**
When a model learns training data too well (including noise), resulting in poor generalization to new data.

---

## P

**PartyRock**
Amazon Bedrock Playground for experimenting with and prototyping generative AI applications.

**Precision**
The proportion of positive predictions that were actually correct: TP / (TP + FP).

**Pre-training**
Initial training of a model on large-scale data before task-specific fine-tuning.

**Prompt Engineering**
The process of designing and optimizing input instructions to guide AI model outputs.

**Prompt Injection**
A security attack where malicious instructions are inserted into prompts to manipulate model behavior.

---

## R

**RAG (Retrieval Augmented Generation)**
A technique combining retrieval of relevant documents with generation to ground AI responses in factual information.

**Real-Time Inference**
Processing individual inputs immediately as they arrive, for time-sensitive predictions.

**Recall**
The proportion of actual positives that were correctly identified: TP / (TP + FN).

**Regression**
A supervised learning task that predicts continuous numerical values.

**Reinforcement Learning**
ML approach where an agent learns by interacting with an environment and receiving feedback (rewards/penalties).

**RLHF (Reinforcement Learning from Human Feedback)**
Fine-tuning technique using human preferences to improve model outputs.

**ROUGE (Recall-Oriented Understudy for Gisting Evaluation)**
Metrics for evaluating text summarization by measuring overlap with reference summaries.

---

## S

**SageMaker Autopilot**
Automated ML capability that automatically builds, trains, and tunes models.

**SageMaker Clarify**
Tool for detecting bias and explaining model predictions using techniques like SHAP and LIME.

**SageMaker Feature Store**
Centralized repository for storing, sharing, and managing ML features.

**SageMaker JumpStart**
Provides pre-built solutions, pre-trained models, and example notebooks for quick ML development.

**Supervised Learning**
ML where models learn from labeled examples to predict outcomes.

---

## T

**Temperature**
A parameter controlling randomness in model outputs; higher values = more creative/diverse responses.

**Token**
A unit of text processed by a language model, typically a word or word fragment.

**Transfer Learning**
Applying knowledge learned in one domain to a different but related domain.

**Transformer**
A neural network architecture using attention mechanisms, foundational to modern LLMs.

---

## U

**Underfitting**
When a model is too simple to capture data patterns, resulting in poor performance on both training and test data.

**Unsupervised Learning**
ML where models find patterns in data without labeled examples (e.g., clustering).

---

## V

**Vector Database**
A database optimized for storing and querying high-dimensional vector embeddings (e.g., Amazon OpenSearch, Aurora with pgvector).

**Variance**
The sensitivity of model predictions to small changes in training data; high variance can lead to overfitting.

---

## Z

**Zero-Shot Learning**
Using only instructions (no examples) to get a model to perform a task it wasn't explicitly trained for.
