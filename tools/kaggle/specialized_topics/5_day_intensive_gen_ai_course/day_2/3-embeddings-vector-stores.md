# 3. Embeddings & Vector Stores

https://www.youtube.com/watch?v=1CC39K76Nqs&list=PLqFaTIg4myu8GFXsSEicf6q_ExhfOr5ck&index=3

## 1. Introduction

- The whitepaper explains how embeddings convert diverse data—text, images, audio—into unified vector representations for easier use across applications. 
- It covers **understanding embeddings**, **mapping (embedding) techniques**, **efficient storage (management)** and **retrieval**, **vector databases** and **real-world use cases** with LLMs, illustrated with practical code examples.

## 2. Why embeddings are important

- **Embeddings** are *low-dimensional numerical representations of real-world data* (text, images, speech, videos) that capture semantic relationships. 
- Similar items are close in the embedding space, allowing *comparison*, *retrieval* and *recommendation* at scale. 
- Like latitude and longitude map locations, **embeddings map** complex data into vectors, enabling efficient search, recommendations and multimodal applications. 
- They can be *task-specific*, jointly representing multiple modalities and serve as compact, meaningful inputs for ML models and other downstream applications.

### 2.1 Evaluating Embedding Quality

- Embedding models are evaluated based on their ability to retrieve relevant items while excluding irrelevant ones, often using labeled datasets. 
- Key metrics include:
    - **Precision**: Fraction of retrieved documents that are relevant (e.g., precision@10 = relevant/total retrieved).
    - **Recall**: Fraction of relevant documents that are retrieved (e.g., recall@20 = relevant retrieved/total relevant).
    - **nDCG (Normalized Discounted Cumulative Gain)**: Measures ranking quality, rewarding highly relevant items appearing earlier in the results.
- Benchmarks like **BEIR** and **MTEB** provide standardized evaluation datasets, while tools like **trec_eval** or **pytrec_eval** help calculate metrics consistently. 
- Additional practical considerations include model size, embedding dimensions, latency and cost. 
- The guiding principle: similar items should be closer in the embedding space.

### 2.2 Search Example

- Embeddings are used in information retrieval and search applications. Key points include:
    - **Joint Embeddings for Search**:
        - Questions and documents are mapped into a shared embedding space. 
        - Dual encoders (separate networks for queries and documents) often outperform single “siamese” networks.
    - **RAG Workflow**: Retrieval-Augmented Generation (RAG) involves two phases:
        1. **Index Creation**: Documents are chunked, embedded and stored in a vector database for fast retrieval.
        2. **Query Phase**: User queries are embedded and matched with relevant document embeddings in milliseconds.
    - **Embedding Quality**: Embedding models (e.g., BERT and successors) have significantly improved retrieval performance over time (e.g., BEIR scores improving from 10.6 to 55.7).
    - **Implementation**: Example using Google Vertex APIs for embedding both documents and queries, storing embeddings in FAISS and evaluating retrieval with precision, recall and nDCG metrics.
    - **Dataset Considerations**: 
        - Labeled datasets like NFCorpus are needed for training and evaluation. 
        - Domain-specific datasets (e.g., medical or legal) are required for optimal performance.
    - **Scaling with LLMs**: Large language models can assist in generating synthetic question-document pairs for training and evaluation, reducing costs and improving model performance.
- In essence, embeddings combined with efficient vector search and RAG enable fast, accurate retrieval from large corpora, with continuous improvements in embedding quality and scalability through synthetic data generation.

### 2.3 Types of embeddings

- **Embeddings** convert data into low-dimensional representations that retain the most important information. 
- Different types of data, such as text or images, use *specific embedding techniques* tailored to their format.

### 2.3.1 Text embeddings

- Text embeddings in NLP represent the meaning of language for tasks like generation, classification and sentiment analysis. 
- The process begins with **tokenization**, which splits text into tokens (words, subwords, characters, numbers, punctuation). 
- Each token is then assigned a unique **token ID**, which can be used in sparse or one-hot encoded vectors. 
- However, these IDs lack semantic meaning, so **embeddings** are applied to capture relationships and meanings at the word or document level, enabling more effective downstream processing.

### 2.3.2 Word embeddings

- This section covers classic **word embedding techniques** that predate modern contextual embeddings. 
- Key methods include **Word2Vec**, **GloVe** and **SWIVEL**:
    - **Word2Vec**: Learns embeddings based on the principle that a word’s meaning is defined by its neighbors. 
    - It uses:
        - **CBOW**: Predicts a word from its surrounding context; faster and better for frequent words.
        - **Skip-gram**: Predicts surrounding words from a target word; slower but better for rare words.
        - Can be extended to sub-word embeddings (inspiring **FastText**).
    - **GloVe**: Captures both local and global word statistics using a co-occurrence matrix and factorization, producing embeddings suitable for various NLP tasks.
    - **SWIVEL**: Uses co-occurrence within local windows and accounts for unobserved co-occurrences via piecewise loss; slightly less accurate than GloVe but faster due to distributed training.
- These embeddings can be used directly in downstream NLP tasks like named entity recognition, topic modeling, or as pre-trained embeddings.

### 2.3.3 Document embeddings

- Document embeddings, which map paragraphs or entire documents into low-dimensional vectors, have been of interest since the 1980s. 
- They enable applications like **semantic search**, **topic discovery**, **classification** and **clustering**. 
- The evolution of document embeddings spans **two main stages**: traditional shallow **Bag-of-Words (BoW) models** and modern **pretrained large language models**.

#### 2.3.3.1 Shallow BoW models

- Early document embeddings relied on **Bag-of-Words (BoW) models**, such as **LSA**, **LDA** and **TF-IDF**, which represent documents based on word frequency or co-occurrence but ignore word order and semantics. 
- While TF-IDF can produce sparse or dense embeddings and remains a strong baseline (e.g., BM25), BoW models fail to capture sequential relationships between words. 
- Inspired by Word2Vec, **Doc2Vec** was introduced in 2014, adding a document-level embedding that combines with word embeddings to predict words, enabling more meaningful embeddings for downstream tasks, though new documents require extra inference to generate embeddings.

#### 2.3.3.2 Deeper pretrained large language models

- The evolution of embedding models has been driven by **deep neural networks**, large-scale **pretraining, subword tokenization** and fine-tuning. 
- BERT (2018) marked a breakthrough with bidirectional transformers and masked language modeling, becoming the foundation for models like **Sentence-BERT**, **SimCSE** and **E5**. 
- Subsequent **large language models** such as T5, PaLM, Gemini, GPT and LLaMA have further advanced embedding quality.
- Newer embedding approaches include:
    - **Multi-vector embeddings** (e.g., ColBERT, XTR) to enhance representational power.
    - **Task-specific dimension selection** (e.g., Matryoshka Embeddings) to optimize storage and indexing.
    - **Multimodal embeddings** combining text and images (e.g., ColPali).
- Deep neural network embeddings outperform traditional bag-of-words methods, capturing **contextual meanings** for words and documents. 
- Pretrained embeddings from platforms like TensorFlow Hub and Vertex AI can be integrated into workflows using Keras, LangChain and BigQuery for efficient downstream applications.

### 2.3.4 Image & multimodel embeddings

- Image embeddings can be generated using models like **CNNs** or **Vision Transformers**, taking the **penultimate layer** as a feature-rich representation of the image.
- **Multimodal embeddings** combine unimodal text and image embeddings into a **joint latent space** that captures semantic relationships. 
- These embeddings enable tasks like **retrieving images from text queries** without complex OCR or layout preprocessing, as demonstrated in approaches like **ColPali**. 
- They provide a fixed-size representation suitable for integration into models such as Keras.

### 2.3.5 Structured data embeddings

- Structured data has a defined schema, like database tables with known field types. 
- Unlike text or image data, embeddings for structured data usually need to be **custom-built** for each specific application.

#### 2.3.5.1 General structured data

- Embeddings can be created for each row of general structured data using techniques like PCA. 
- These embeddings are useful for **anomaly detection** and for **downstream ML tasks** like classification, often requiring less training data than using the original high-dimensional data.

#### 2.3.5.2 User/item structured data

- For recommendation systems, embeddings are created from user data, item/product data and their interactions (e.g., ratings) to map both entities into the same embedding space. 
- Custom embedding models are required and these can be combined with unstructured embeddings when items include text or images.

### 2.3.6 Graph embeddings

- **Graph embeddings** represent nodes in a graph by capturing both the node’s attributes and its relationships with neighbors. 
- They are useful for tasks like node/graph classification, link prediction, clustering, search and recommendations. 
- Popular algorithms include DeepWalk, Node2Vec, LINE and GraphSAGE.

## 2.4 Training Embeddings

- Modern embedding models often use a **dual-encoder (two-tower) architecture**, **encoding inputs** and **targets separately** (e.g., queries vs. documents, images vs. text). 
- They are trained using **contrastive loss**, bringing positive pairs closer and negative pairs further apart. 
- Training typically involves **pretraining on large datasets** and **fine-tuning for specific tasks**, using methods like human labeling, synthetic data, or hard negative mining. 
- **Embeddings** can be adapted for downstream tasks with additional layers and **models** can be frozen, trained from scratch, or fine-tuned. 
- **Platforms** like Vertex AI and TensorFlow Hub facilitate customization and fine-tuning of embeddings for various applications. 
- The next step involves efficiently storing and searching embeddings for production use.

## 3. Vector search

- Traditional full-text search relies on exact keyword matching, which struggles with misspellings or semantically similar queries. 
- **Vector search** overcomes this by using embeddings to represent the semantic meaning of documents, enabling searches across text, images, videos and other data types. 
- Queries and items are embedded in the same vector space and *matches are found using similarity metrics* like Euclidean distance, cosine similarity, or dot product. 
- Vector databases manage these embeddings efficiently, allowing scalable, semantically aware search beyond literal keyword matching.

### 3.1 Important vector search algorithms

- **Linear search** for finding the most similar vectors is simple but slow, scaling linearly with the **number of items (O(N))**, making it impractical for millions of documents. 
- **Approximate Nearest Neighbor (ANN)** search is a more efficient alternative, finding closest points with minimal error and significantly reduced computation **(O(logN))**. 
- ANN **uses** techniques like quantization, hashing, clustering and tree-based methods, offering trade-offs in speed, accuracy and scalability.

#### 3.1.1 Locality sensitive hashing & trees

- **Locality Sensitive Hashing (LSH)** speeds up similarity search by hashing similar items into the same buckets, reducing the search space and improving lookup speed, with a trade-off between recall and false positives depending on the number of hash functions. 
- **Tree-based approaches**, like Kd-trees and Ball-trees, partition data to speed up search, with Ball-trees better suited for high-dimensional vectors. 
- **Hashing and tree-based methods** can be combined to optimize search performance, as seen in libraries like *FAISS* (with *HNSW*) and ScaNN.

#### 3.1.2 Hierarchical navigable small worlds

- **FAISS** uses *Hierarchical Navigable Small World (HNSW)* graphs to perform vector similarity search efficiently in sub-linear time. 
- The graph has multiple layers with long links at the top and short links at the bottom. 
- The search starts at the top, greedily finds the closest node and moves down layer by layer until reaching the bottom, keeping track of traversed nodes to return the K-nearest neighbors. 
- Speed and memory efficiency can be further improved with quantization and vector indexing.

#### 3.1.3 ScaNN

- Google’s ScaNN is a scalable **approximate nearest neighbor (ANN)** search method used in Google Cloud products like Vertex AI Vector Search and databases. 
- It can optionally partition large datasets into clusters to prune the search space, improving speed. 
- At query time, ScaNN selects top partitions, computes distances (exact or approximate using product or anisotropic quantization) and optionally rescoring the top results for accuracy. 
- **ScaNN** provides a strong speed/accuracy tradeoff. 
- Along with FAISS, LSH, KD-Tree and Ball-tree, these ANN methods require production-ready vector databases for scalable and secure deployment.

## 4. Vector databases

- **Vector databases** are designed to efficiently store and query vector embeddings, combining semantic search with traditional database functionality. 
- The workflow involves embedding data using a trained model, augmenting vectors with metadata, indexing for efficient search and embedding queries to find semantically similar items. 
- Some databases support hybrid search, caching, pre- and post-filtering and reranking. 
- Examples include Google Vertex AI Vector Search (using ScaNN), AlloyDB & Cloud SQL Postgres (with pgvector and ScaNN extensions), Pinecone, Weaviate and ChromaDB, which provide fast ANN search and flexible integration with traditional query capabilities.

### 4.1 Operational considerations

- Vector databases address many challenges of storing and querying embeddings at scale, including scalability, consistency, real-time updates, backups and access control. 
- Key considerations include:
    1. **Embedding Updates**: 
        - Embeddings can change as models are retrained or updated, but frequent re-embedding of large datasets is costly. 
        - Automated processes are needed to manage updates efficiently.
    2. **Semantic vs Literal Representation**: 
        - Embeddings capture semantic meaning well but may miss literal or domain-specific values. 
        - Combining semantic search with full-text search can improve accuracy.
    3. **Workload Considerations**: The choice of vector database depends on workload type: operational databases (AlloyDB, Spanner, Postgres, CloudSQL) are better for OLTP, while analytical workloads benefit from systems like BigQuery.
    4. **Selection Factors**: Dataset type, business needs, budget, security, semantic and syntactic search requirements and integration with existing systems should guide the choice of vector database.
- Overall, vector databases are essential for scalable, accurate and production-ready embedding search systems.

## 5. Applications

- Embedding models, combined with vector stores using ANN search, are foundational tools for many applications. 
- They are widely used in Retrieval Augmented Generation (RAG) with LLMs, search, recommendation systems, anomaly detection and few-shot classification. 
- For ranking tasks like search or recommendations, embeddings are typically used in the first stage to efficiently retrieve semantically similar candidates from very large datasets, sometimes containing millions or billions of items. 
- ANN techniques, such as ScaNN, help scale this process, after which a more sophisticated model can refine the results. 
- This approach is particularly effective when integrating embeddings with LLMs for question-answering or RAG applications.

### 5.1 Q & A with sources (RAG)

- **Retrieval Augmented Generation (RAG)** for Q&A combines retrieval and generation by first fetching relevant documents from a knowledge base and then expanding the prompt with this information to produce more accurate and informative answers. 
- RAG addresses common LLM issues, such as hallucinations and outdated knowledge, by supplying up-to-date data via the prompt instead of retraining the model. 
- While it reduces hallucinations, it doesn’t fully eliminate them; including the sources and performing a coherence check (manually or with an LLM) further improves reliability. 
- RAG can be efficiently implemented using tools like Vertex AI text embeddings, Vertex AI Vector Search and libraries such as LangChain.