

# AWS AI Practitioner Multiple Choice Questions - Set 3

<!-- Card Start -->

### Front

Which capabilities of Amazon OpenSearch Service are most relevant for AI/ML workloads? (Choose 2)
- A. Vector similarity search with k-NN
- B. Website hosting
- C. Vector database functionality
- D. Email processing
- E. Log analysis

### Back

**Correct Answers**: A and C  
**Explanation**: Amazon OpenSearch Service provides essential capabilities for AI/ML workloads through:
- Vector similarity search (k-NN) for efficient similarity-based queries
- Vector database functionality for storing and querying embeddings

**Task Reference**: This is covered in Task Statement 3.1 regarding services for storing embeddings within vector databases.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary advantage of using Amazon Aurora with pgvector for AI applications?
- A. It provides serverless computing capabilities
- B. It enables vector similarity search within a relational database
- C. It automatically generates AI models
- D. It provides pre-trained language models

### Back

**Correct Answer**: B  
**Explanation**: Amazon Aurora with pgvector enables vector similarity search operations within a relational database, allowing organizations to:
- Store embeddings alongside structured data
- Perform vector similarity searches using SQL
- Maintain ACID compliance while working with vector data
- Scale vector operations efficiently

**Task Reference**: Referenced in Task Statement 3.1 as one of the AWS services that help store embeddings within databases.

<!-- Card End -->

<!-- Card Start -->

### Front

Which features make Amazon Kendra most valuable for enterprise search applications? (Choose 2)
- A. Natural language understanding
- B. Website hosting capabilities
- C. Semantic search functionality
- D. Email server functionality
- E. Network monitoring

### Back

**Correct Answers**: A and C  
**Explanation**: Amazon Kendra provides advanced search capabilities through:
- Natural language understanding that interprets user intent
- Semantic search that understands context and meaning
- Integration with enterprise data sources
- Learning from user interactions and feedback

**Task Reference**: This service is mentioned in Task Statement 1.2 under AWS managed AI services, particularly for intelligent search applications.

<!-- Card End -->

<!-- Card Start -->

### Front

Which parameters are commonly used for controlling the output diversity in generative AI models? (Choose 2)
- A. Top-k sampling
- B. Model size
- C. Top-p (nucleus) sampling
- D. Training dataset size
- E. Hardware configuration

### Back

**Correct Answers**: A and C  
**Explanation**: Top-k and Top-p sampling are key parameters for controlling output generation:
- Top-k limits token selection to the k most likely next tokens
- Top-p (nucleus) sampling selects from tokens that sum to probability p
Both help balance between diversity and quality of generated content.

**Task Reference**: These concepts relate to Task Statement 3.1 regarding inference parameters' effects on model responses.

<!-- Card End -->

<!-- Card Start -->

### Front

Which statements about model latent space are correct? (Choose 2)
- A. It represents the model's internal understanding of relationships
- B. It is only used for image processing
- C. It enables semantic similarities between different inputs
- D. It requires human supervision to maintain
- E. It must be stored in a specific database type

### Back

**Correct Answers**: A and C  
**Explanation**: Model latent space:
- Represents the model's internal understanding and organization of concepts
- Enables computation of semantic similarities between different inputs
- Facilitates transfer learning and generalization
- Supports various types of data representations

**Task Reference**: This concept is referenced in Task Statement 3.2 under concepts of prompt engineering and model architecture.

<!-- Card End -->

<!-- Card Start -->

### Front

What are the primary use cases for storing embeddings in a vector database like Amazon OpenSearch Service? (Choose 2)
- A. Semantic search implementation
- B. Website content management
- C. Similarity-based recommendations
- D. Email routing
- E. Network traffic analysis

### Back

**Correct Answers**: A and C  
**Explanation**: Vector databases are essential for:
- Implementing semantic search by finding similar vectors
- Building recommendation systems based on content similarity
- Supporting RAG (Retrieval Augmented Generation)
- Enabling efficient nearest neighbor search at scale

**Task Reference**: This aligns with Task Statement 3.1 regarding vector database applications and RAG implementations.

<!-- Card End -->

<!-- Card Start -->

### Front

How does top-p (nucleus) sampling differ from traditional temperature-based sampling?
- A. It samples from the smallest possible token set
- B. It selectively samples from tokens that sum to probability p
- C. It always produces deterministic output
- D. It only works with specific model architectures

### Back

**Correct Answer**: B  
**Explanation**: Top-p (nucleus) sampling:
- Dynamically selects tokens based on cumulative probability
- More adaptive than fixed temperature or top-k approaches
- Balances quality and diversity
- Helps prevent unlikely token combinations

**Task Reference**: This relates to Task Statement 3.1 regarding inference parameters and their effects on model outputs.

<!-- Card End -->

<!-- Card Start -->

### Front

Which features of Amazon Aurora with pgvector are most important for AI applications? (Choose 2)
- A. Vector similarity search capabilities
- B. Traditional SQL operations
- C. Integration with structured data
- D. Web hosting features
- E. Email processing

### Back

**Correct Answers**: A and C  
**Explanation**: Key features include:
- Vector similarity search for finding related content
- Ability to combine traditional structured data with vector operations
- SQL interface for vector operations
- Scalable vector storage and querying

**Task Reference**: This relates to Task Statement 3.1 regarding storage and querying of embeddings in databases.

<!-- Card End -->
