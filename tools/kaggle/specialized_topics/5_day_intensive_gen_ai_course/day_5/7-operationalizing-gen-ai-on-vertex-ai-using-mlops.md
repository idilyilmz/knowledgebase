# Operationalizing Generative AI on Vertex AI using MLOps

https://youtu.be/Hbk8UXavHrk?si=kvaeioTLbz8i18WA

## 1. Introduction

- The rise of **foundation models** and **generative AI (gen AI)** has created new challenges for building AI systems, including model selection, data curation, prompt engineering, task-specific tuning, grounding outputs in real-world data and hardware optimization.
- This whitepaper explores how **MLOps practices** must adapt to meet the demands of gen AI and foundation models. 
- It also reviews **Vertex AI products** designed to support these requirements, showing how Vertex AI leverages its AI infrastructure and MLOps tools to provide a **comprehensive platform for developing, deploying and managing generative AI applications**.

### 1.1 What are DevOps and MLOps?

- **DevOps** is a methodology that connects software development and operations through collaboration, automation and continuous improvement, using practices like continuous integration and delivery. 
- **MLOps** extends DevOps to machine learning, addressing challenges such as data quality, model evaluation, monitoring in production and ensuring experiment tracking and reproducibility.

### 1.2 Lifecycle of a gen AI system

- The **lifecycle of a generative AI system** involves five key stages:
  1. **Discovery**: Selecting the most suitable model by evaluating strengths, weaknesses and costs.
  2. **Development & Experimentation**: Crafting prompts, using few-shot learning, fine-tuning and chaining models to achieve desired outputs.
  3. **Data Engineering**: Ensuring factual accuracy, incorporating up-to-date information and adapting data for specific tasks.
  4. **Deployment & Governance**: Managing artifacts like prompt templates, model adapters and embedding stores while aligning with infrastructure requirements.
  5. **Monitoring & Continuous Improvement**: Maintaining performance, safety, fairness and accountability; adapting foundation models through prompting, updates, or combining models, with occasional fine-tuning as needed.
- The lifecycle assumes pre-operational foundation models; the focus is on adapting and operationalizing these models for specific applications rather than training them from scratch.

## 2. Discover

- **Discovering the right foundation model** is a key MLOps practice because building models from scratch is costly and no single model fits all use cases. 
- The growing number of open-source and proprietary models requires systematic evaluation based on factors like **quality, latency, throughput, development effort, cost and compliance**. 
- Model discovery platforms, such as Vertex Model Garden, help practitioners efficiently identify and select suitable models for adaptation through fine-tuning or prompt engineering.

## 3. Develop and experiment

- **Development and experimentation** in generative AI is an iterative process involving **data refinement, model selection/adaptation and evaluation**. 
- Feedback from evaluation guides improvements, such as enhancing data, adjusting prompts, fine-tuning, or switching models, creating a continuous loop that optimizes the application—similar to traditional machine learning but tailored for foundation models.

### 3.1 The foundational model paradigm

- **Foundation models** differ from traditional predictive models because they are **multi-purpose**, trained on broad datasets and exhibit **emergent properties**—capabilities that arise from input without additional training. 
- Their outputs are highly sensitive to input, meaning tasks can be changed simply by modifying the input. 
- This creates a paradigm shift for generative AI, requiring **prompt templates** (structured instructions with placeholders) to guide the model and integrate it effectively into applications.

### 3.2 The core component of LLM Systems: A prompted model component

- In **LLM systems**, the combination of a foundation model and a prompt (called a **prompted model component**) is the core unit for generating content. 
- Effective development relies on **prompt engineering**, an iterative process of refining prompts and evaluating outputs. 
- Prompts are **hybrid artifacts**: some elements act as data (examples, knowledge bases) and others as code (templates, instructions, guardrails), requiring distinct MLOps practices. 
- Managing prompts alongside model versions enables efficient experimentation, tracking, evaluation, adaptation, deployment and overall artifact management in generative AI.

### 3.3 Chain & Augment

- **Chaining and augmenting gen AI models** addresses limitations like outdated knowledge and reasoning challenges by connecting multiple prompted models with external APIs and code. 
- Common patterns include **Retrieval-Augmented Generation (RAG)**, which grounds outputs with up-to-date data and **Agents**, which dynamically select tools or data sources to answer complex queries. 
- Unlike predictive AI, chains require **end-to-end evaluation, versioning, continuous monitoring and introspection**, since components are tightly coupled and harder to evaluate individually. 
- Platforms like Vertex AI and tools like LangChain support building, managing and monitoring these complex gen AI chains.

### 3.4 Tuning & training

- **Tuning and training gen AI models** goes beyond prompt engineering and chaining to optimize performance for specific tasks. 
- Common approaches include **supervised fine-tuning** (teaching the model correct outputs) and **RLHF** (guiding the model using human preferences). 
- MLOps practices for tuning include **tracking artifacts, evaluating model performance and comparing results**. 
- Platforms like **Vertex AI** support these needs with tools for artifact management, pipeline orchestration and data governance, providing unified capabilities for both predictive and generative AI workflows.

#### 3.4.1 Continuous Training & Tuning

- **Continuous training and tuning** in MLOps ensures models stay effective as real-world data changes. 
- For generative AI, **continuous tuning** (rather than full retraining) is often more practical due to high computational costs. 
- The frequency and method depend on the task, with dynamic applications like chatbots requiring frequent RLHF-based updates. 
- Hardware like **GPUs and TPUs** accelerates tuning and techniques such as **model quantization** help reduce compute and memory costs. 
- Platforms like **Vertex AI** provide tools to support these tuning workflows efficiently.

### 3.5 Data Practices

- **Data practices in generative AI** differ from traditional predictive AI because model behavior depends not just on training data but also on how the model is adapted using diverse inputs. 
- Applications can launch with minimal data through **foundation models, prompts, few-shot examples, grounding/augmentation data, task-specific datasets and human feedback datasets**. 
- Managing this variety requires careful **organization, versioning, tracking and lifecycle management**. 
- Synthetic data (generated, corrected, or augmented by large models) can supplement real-world data for fine-tuning and evaluation. 
- Robust evaluation datasets reflecting the specific use case are crucial, as foundation model training distributions are often unknown. 
- Overall, gen AI data pipelines focus on adaptability, reproducibility and governance across multiple data types rather than only extraction and transformation.

### 3.6 Evaluate

- **Automated evaluation in generative AI** accelerates development and improves reproducibility by handling complex prompts and outputs without human subjectivity. 
- Challenges include high-dimensional outputs, subjective quality metrics and lack of ground truth data. 
- Solutions involve **custom evaluation methods**, using other foundation models as judges (e.g., AutoSxS), generating synthetic data and aligning metrics with human judgment. 
- Comprehensive evaluation also protects against **adversarial attacks** through techniques like prompt fuzzing and testing for information leakage. 
- Overall, effective evaluation requires early metric definition, careful alignment with human preferences and ongoing adaptation as applications evolve.

## 4. Deploy

- **Deployment of generative AI systems** involves coordinating multiple components (prompts, models, adapter layers, databases and data pipelines) into a functioning production solution. 
- There are two main types: 
  - **system deployment**, which operationalizes a complete application for a specific use case and 
  - **foundational model deployment**, which makes open-weight or privately trained models accessible for multiple potential use cases. 
- Best practices are still evolving, but careful management of all components is essential for reliable production operation.

### 4.1 Deployment of gen AI systems

- **Deployment of gen AI systems** is similar to deploying other complex software. 
- Common components like databases and applications can be managed using standard **software engineering practices**, including **version control** and **CI/CD pipelines**.

#### 4.1.1 Version control

- **Version control in generative AI** is essential due to the iterative nature of development. 
- All modifiable components (including **prompt templates, chain definitions, external datasets and adapter models**) should be versioned using tools like Git or cloud storage solutions. 
- This ensures **reproducibility, traceability and easy rollback** during experimentation and deployment.

#### 4.1.2 Continuous integration of gen AI systems

- **Continuous Integration (CI) for gen AI systems** applies automated testing to all components (prompts, chains, embedding models and retrieval systems) to ensure quality, catch bugs early and reduce maintenance costs. 
- Challenges include **defining comprehensive test cases** due to open-ended outputs and **reproducibility issues** because of inherent randomness in generative models. 
- CI for gen AI relies on evaluation techniques adapted to handle these complexities and best practices are still evolving.

#### 4.1.3 Continuous delivery of gen AI systems

- **Continuous delivery (CD) for gen AI systems** moves tested code through pre-production environments before final deployment. 
- The key component is the **chain**, which serves users. 
- Delivery differs by use case: 
  - **batch applications** require scheduled pipeline testing and throughput validation, 
  - while **online applications** require API testing with low-latency performance checks, ensuring all components function correctly and non-functional requirements like scalability and reliability are met.

### 4.2 Deployment of foundation models

- **Deployment of foundation models** requires careful management of 
  - **compute resources** (GPUs or TPUs), 
  - **scalable data storage** (e.g., BigQuery, Cloud Storage) and 
  - **model optimization or compression techniques** to handle the large size and complexity of these models efficiently.

#### 4.2.1 Infrastructure validation

- **Infrastructure validation** ensures that gen AI models are compatible with the target hardware and serving configuration before deployment. 
- Tools like **TFX** can automate some checks, but engineers must still manually verify the availability of required compute resources to prevent deployment issues.

#### 4.2.2 Compression and optimization

- **Model compression and optimization** reduce compute, storage and latency requirements for gen AI systems. Key techniques include:
  - **Quantization**: 
    - Converts weights and activations to lower-precision formats (e.g., 8-bit) to save memory and computation.
  - **Pruning**: 
    - Removes unnecessary weights or subnetworks to reduce model size while maintaining accuracy.
  - **Distillation**: 
    - Trains a smaller “student” model to mimic a larger “teacher” model, often improving efficiency and sometimes performance, especially when combined with task-specific data. 
    - Techniques like **step-by-step distillation** further enhance results.
- These methods balance **resource efficiency** with **model performance**.

#### 4.2.3 Deployment, packaging and serving checklist

- **Deployment, packaging and serving of LLMs on Vertex AI** involves these key steps:
  1. **Version control**: Track changes and enable rollbacks.
  2. **Model optimization**: Apply distillation, quantization, or pruning.
  3. **Containerization**: Package the model into a container.
  4. **Define hardware requirements**: Ensure GPUs, TPUs, or accelerators meet performance needs.
  5. **Define model endpoint**: Configure container, I/O formats and other parameters.
  6. **Allocate resources**: Assign compute based on expected traffic and performance.
  7. **Access control**: Restrict endpoint access via authentication and authorization.
  8. **Create model endpoint**: Deploy the model as a REST API service.
  9. **Monitoring and logging**: Track performance, resource usage and errors.
  10. **Custom integrations**: Connect the model to applications or services via SDKs/APIs.
  11. **Real-time deployment**: Use Cloud Functions or Cloud Run for streaming, low-latency applications.

### 4.3 Logging and monitoring

- **Logging and monitoring in generative AI applications** require end-to-end tracking of both inputs and outputs at the **application and component levels** due to chained architectures. 
- Key practices include:

  - **Lineage tracking**: Log inputs, outputs and dependent artifacts for each component to diagnose errors or inaccuracies.
  - **Skew and drift detection**: Compare production input/output distributions with evaluation datasets using metrics like embeddings, token counts, vocabulary changes, or statistical measures (MMD, density differences).
  - **Multimodal and policy alignment**: Ensure outputs match prompts and organizational guidelines using techniques like **“LLM as a Judge”** or generative auto-raters.
  - **Continuous evaluation**: Capture production outputs, collect user feedback and compare to ground truth to track performance over time.
  - **Alerting**: Notify owners of drift, skew, or performance degradation for rapid intervention.
  - **Efficiency metrics**: Monitor resource utilization, latency and system performance.
  - **Tools**: Vertex AI Eval Service, Vertex Pipelines and OpenTelemetry for tracing and aggregating logs, enabling detailed analysis of complex, multi-step generative AI applications.

### 4.4 Govern

- **Governance in MLOps for generative AI** ensures **control, accountability and transparency** across the development, deployment and management of models, data and code. 
- In gen AI, the **chain and its components** are treated as governable assets, with lineage tracking extended to all elements—data, models, code and evaluation metrics—for auditing, debugging and improvement. 
- Traditional MLOps practices still apply, including governance of **data, tuned models and code**. 
- Tools like **Google Cloud Dataplex**, **Vertex ML Metadata** and **Vertex Experiments** help centralize governance, track experiments and manage assets.

## 5. Extend MLOps for genAI to Agents

- **Extending MLOps to gen AI Agents** involves managing complex workflows where agents interact with models, APIs and data sources to make decisions. 
- Agents introduce unique operational challenges, including **lifecycle management, tooling, observability, safety and continuous improvement**, requiring specialized MLOps practices beyond standard gen AI systems. 
- For deeper understanding, foundational resources like Google’s **Agent whitepaper** are recommended.

### 5.1 Agent Lifecycle

- **Core components and lifecycle of an agent system**:
  1. **Foundation Model** – Provides reasoning, language understanding and decision-making capabilities.
  2. **Instructions** – Define the agent’s goals or tasks, ranging from simple to complex multi-step objectives.
  3. **Tools** – Descriptions of available functions and their parameters, guiding the model on which function to call and how to use it.
- **Operational lifecycle**:
  1. **New Query** – User initiates interaction.
  2. **Function Identification** – Foundation model analyzes the query, instructions and available tools to determine needed function calls.
  3. **Function Call Preparation** – Model generates structured function call requests with parameters.
  4. **Function Call Execution** – Developer’s code (or advanced model) executes the function and retrieves results.
  5. **Intermediate Response** – Model processes function results to produce an intermediate response.
  6. **Iterative Context Update** – Conversation history (short-term memory) is updated and the model re-evaluates next steps.
  7. **Final Response** – Model generates the final output to the user after completing all necessary steps or reaching a maximum iteration limit.

### 5.2 Tool Orchestration

- **Tool orchestration in generative AI agents** emphasizes that tools are essential for agents to interact with the environment and perform complex tasks. 
- Tools differ in implementation, accessibility and capabilities, so understanding these distinctions is critical for designing effective and robust agent systems.

#### 5.2.1 Tool Types & Environments

- **Tool types and environments for generative AI agents**:
  * **Code Functions**: Implemented within the agent’s codebase, providing direct access to local resources. Cloud support includes **Artifact Registry** and **Cloud Code**.
  * **Private REST APIs**: Hosted in a VPC for secure access to internal services and data. Managed via **Cloud Run**, **API Gateway**, or **Apigee**.
  * **Public REST APIs**: Third-party services accessible over the internet, with secure outbound access via a **NAT Gateway**.
- Tools often reside in **distributed environments**—data lakes, production applications, or code repositories—creating challenges in management. 
- To address this, a **centralized Tool Registry** is essential for organizing, tracking and efficiently utilizing these diverse resources in production.

#### 5.2.2 Tool Registry

- **Tool Registry for generative AI agents** is a centralized catalog that standardizes the discovery, access and management of all tools. 
- Key benefits include **reusability, shareability, security, standardization, robustness and auditability**. 
- It stores detailed tool information (name, description, parameters, outputs), provides **version control**, enables **efficient search and discovery** and enforces **access permissions**. 
- Functionally, it mirrors a **Model Registry** in MLOps, serving as a critical component for operationalizing agent-based systems.

#### 5.2.3 Tool Selection Strategies at Scale

- **Tool Selection Strategies at Scale** focus on optimizing generative AI agent performance when managing large Tool Registries. 
- Providing access to all tools can overwhelm the model, reduce predictability and complicate testing. 
- Three strategies are commonly used:
  1. **Generalist Agent:** Access to the full Tool Registry; flexible but may reduce performance and predictability.
  2. **Specialist Agent:** Limited, curated tool subset; improves performance, predictability, security and simplifies testing but requires upfront design.
  3. **Dynamic Tool Selection:** Tools are selected at runtime based on task relevance; highly adaptable but harder to predict and ensure consistent behavior.
- The optimal approach depends on **task complexity, registry size, desired control and available design resources**, with ongoing research exploring quantitative comparisons, especially for dynamic tool selection.

### 5.3 Agent Evaluation & Optimization

- **Agent Evaluation** focuses on assessing an agent’s ability to reason, use tools effectively and operate reliably. It involves five key stages:
  1. **Tool Unit Testing & Refinement:** Validate individual tools and refine function descriptions and parameters to ensure reliable agent behavior.
  2. **Evaluation Dataset Creation:** Build representative datasets of multi-turn interactions, either manually or from real user sessions, for continuous evaluation.
  3. **Tool Selection Evaluation:** Assess the agent’s ability to choose and correctly use tools, including trajectory evaluation to detect hallucinations, wrong tool use, or dead-ends.
  4. **Reasoning & Groundedness Evaluation:** Evaluate the agent’s reasoning process, error recovery and context maintenance across multi-step interactions.
  5. **Operational Metric Evaluation:** Measure latency, cost and other production-related metrics to ensure practical viability and scalability.
- **Agent Optimization** is iterative, focusing on refining:
  * **Tools:** Curate appropriate tools and ensure clear function/parameter definitions.
  * **Foundation Model:** Select models optimized for reasoning and tool use.
  * **Instruction Prompts:** Craft prompts that guide the agent effectively through complex tasks.

### 5.4 Observability and Memory

- **Observability and Explainability** are critical for understanding agent behavior, building trust and ensuring proper operation. Observability captures insights into an agent’s internal workings and interactions, while explainability addresses the reasoning behind its decisions (e.g., why it chose a particular tool).
- **Memory plays a central role** in achieving both:
  * **Short-Term Memory (STM):** Stores ongoing session data—user queries, function calls and responses—allowing the agent to maintain context and coherence.
    - **Implementation options:**
      * Logs (simple, text-based)
      * Cloud storage/databases (structured for complex apps)
      * API session (client-side storage)
      * Hybrid approaches
* **Long-Term Memory (LTM):** Stores data across sessions—user preferences, past interactions—enabling personalization and insight into behavioral evolution.
  - **Implementation options:**
    * Vector databases (semantic search)
    * Metadata storage/graphs (session IDs, timestamps, relationships)
    * Cloud storage/databases (complete record)
    * Hybrid approaches
- **Benefits:** 
  - Proper memory design allows tracing of decision-making, 
  - identification of errors and continuous improvement, 
  - enhancing both **explainability** and 
  - **trustworthiness** of agent-based systems.

### 5.5 Deploying an Agent to Production

- **Deploying agents to production** requires a robust, automated and repeatable process to ensure **consistency, reliability and scalability**. 
- Leveraging a **standardized repository structure** and CI/CD pipelines enables streamlined deployment and automated tool registration.
- **Key pipeline stages:**
  1. **Repository validation:** Ensure the structure meets standards and required files are present.
  2. **Code validation:** Execute unit tests, static code analysis and quality checks.
  3. **Containerization:** Build custom container images if needed for consistent deployment.
  4. **Development deployment:** Deploy agent and tools to a dev environment for early integration testing. Manual approval ensures oversight.
  5. **Staging deployment:** Deploy to a staging environment mirroring production. Conduct automated and human testing, integration and stress tests. Test results are centrally stored for governance. Manual approval follows.
  6. **Production deployment:** Agent is deployed and metadata from the repository is **automatically registered in the Tool Registry**, ensuring consistency and eliminating manual effort.
- **Post-deployment:** Continuous monitoring tracks performance, errors and drift. Insights from monitoring feed back into improvements, forming a **continuous loop of evaluation, refinement and redeployment**.
- **Benefits:**
  * Ensures reproducibility and standardized deployment
  * Reduces manual effort with automated tool registration
  * Provides iterative improvement through monitoring and feedback
  * Supports scalability and governance for production-grade agent-based systems

## 6. Operations: People & Processes

- **Productionizing ML and gen AI** requires more than technology—it depends on **people, roles and standardized processes** working together efficiently.
- **Traditional ML teams** typically include:
  * **Cloud Platform Team:** Manages infrastructure, security and access control.
  * **Data Engineering Team:** Builds and maintains data pipelines, ensuring data quality and accessibility.
  * **Data Science & MLOps Team:** Develops, trains and deploys models using CI/CD pipelines.
  * **ML Governance:** Oversees the full ML lifecycle, ensuring transparency, compliance and auditability.
- **Gen AI introduces new specialized roles:**
  * **Prompt Engineers:** Craft and optimize prompts while applying domain expertise to elicit desired model behavior.
  * **AI Engineers:** Scale generative models into production, integrating evaluation, guardrails and backend systems.
  * **DevOps/App Developers:** Build front-end interfaces and integrate them with AI backends for seamless user experience.
- **Key points:**
  * These specialized roles form a **new operational layer** dedicated to gen AI solutions.
  * Team structure and role specialization scale with organizational size and GenAI maturity.
  * Effective coordination, clear processes and role alignment are critical for **robust production operations** and successful AI deployment.

## 7. The role of an AI platform for gen AI operations

- **AI platforms**, like Vertex AI, provide a **unified environment for managing the full AI lifecycle**, including:
  * **Data preparation**
  * **Model training, tuning and transfer learning**
  * **Deployment and CI/CD automation**
  * **Governance and monitoring**
- These platforms support both **predictive and generative AI**, enabling data scientists, model builders, application developers and agent creators to:
  * Use pre-trained models or fine-tune models for specific tasks
  * Connect models to internal/external data (e.g., via **RAG**)
  * Chain multiple models and components for complex workflows
  * Implement safety checks, caching and optimization for cost and performance
- **Key benefits of AI platforms:**
  * **Enterprise-ready:** secure, controlled and scalable deployment
  * **Efficiency & reproducibility:** standardized pipelines and CI/CD support
  * **Collaboration & innovation:** central access to models and observability tools
  * **Cost-effective:** optimizes compute and accelerates ROI

### 7.1 Key components fo Vertex AI for gen AI

- **Vertex AI** abstracts away the complexities of managing AI infrastructure, providing **on-demand access to compute, storage and services**. 
- This user-centric approach allows organizations to **focus on innovation and collaboration** rather than managing hardware or making upfront purchases. 
- For **generative AI development**, Vertex AI offers capabilities across **eight functional areas** that streamline the AI lifecycle.

### 7.2 Discover: Vertex Model Garden

- **Vertex AI Model Garden** is a curated repository of **150+ machine learning and generative AI models** from Google, partners and open-source communities. 
- It enables **easy discovery, customization and deployment** of models across modalities like **Language, Vision, Tabular, Document, Speech, Video and Multimodal**. 
- Models include Google proprietary foundational models (e.g., **Gemini, PaLM 2, Imagen**) and popular open-source models (e.g., **Llama 3, BERT, Stable Diffusion, Claude 3**).
- **Key features include:**
  * Task-specific models for generation, classification, extraction, recognition, segmentation and more.
  * **Model cards** describing use cases, deployment and tuning options.
  * **Vertex AI Studio** for experimentation with prompts and fine-tuning.
  * **One-click deployment** for some models and over 40 models available for fine-tuning.
  * Optimization options such as **vLLM** and **quantization** to reduce costs and improve efficiency.
- Model Garden **streamlines access** to foundational and open-source models, enabling organizations to leverage existing AI research rather than training models from scratch.

### 7.3 Prototype: Vertex AI Studio & Notebooks

- **Vertex AI Studio & Notebooks** provide a **flexible, inclusive environment for rapid prototyping and development** of generative AI applications. Key features include:
  * **Multiple development workflows**: console-driven, REST APIs and SDKs for Python, NodeJS and Java.
  * **Notebook support**: Vertex Colab Enterprise and Vertex Workbench for familiar coding environments.
  * **Model exploration and experimentation**: Access Google’s foundation models (PaLM 2, Gemini, Codey, Imagen, Universal Speech Model).
  * **Prompt testing and adaptation**: Built-in examples and tools for prompt tuning.
  * **Model customization**: Supports supervised fine-tuning, reinforcement learning and distillation.
  * **One-click deployment**: Quickly deploy gen AI applications.
- Overall, Vertex AI Studio **democratizes gen AI development**, enabling a wide range of users—from business analysts to ML engineers—to prototype, experiment and deploy applications efficiently.

### 7.4 Customize: Vertex AI Training & tuning

- **Vertex AI Training & Tuning** enables the customization and adaptation of generative AI models beyond prompt engineering. 
- The platform supports a spectrum of approaches, from fine-tuning existing models to training new models from scratch, allowing users to optimize performance for specific tasks and use cases.

#### 7.4.1 Train

- **High-performance infrastructure for LLM training:** GPUs and TPUs provide the processing power and memory required for large-scale models. 
- GPUs excel at parallel computation, while TPUs are optimized for ML workloads, offering faster and more energy-efficient training. 
- Google Cloud supports LLM development with options like TPU VMs, Cloud TPU Pods and Vertex AI, enabling scalable, high-performance training.

#### 7.4.2 Tune

- **Vertex AI LLM Tuning:** Vertex AI supports adapting pre-trained LLMs via multiple techniques:
  * **Prompt Engineering:** Crafting and testing prompts (including chains and examples) to guide outputs without retraining.
  * **Supervised Fine-Tuning (SFT):** Using labeled examples to adapt models to domain-specific tasks, extending few-shot learning efficiently.
  * **Reinforcement Learning with Human Feedback (RLHF):** Optimizing models based on human preferences for complex, sequence-level objectives.
  * **Step-by-Step Distillation:** Transferring knowledge from larger models to smaller task-specific models, reducing size, cost and latency while maintaining performance.

#### 7.4.3 Orchestrate

- **Vertex Pipelines:** A managed service for orchestrating, automating and scaling ML workflows, including training, tuning and evaluation of models. 
- It enables seamless transition from prototypes to production, supports complex pipelines and ensures consistency across managed services for Google Foundation Models. 
- Pipelines are defined using Python and the Kubeflow SDK.

### 7.5 Chain & Augment: Vertex AI Grounding, Extensions and RAG building blocks

- Vertex AI provides a comprehensive ecosystem for augmenting LLMs with factual grounding and retrieval capabilities. Key components include:
  * **LLM Function Calling & Structured Outputs:** Enables LLMs to propose structured function calls, return outputs in JSON or predefined schemas and interact with external systems.
  * **LLM Sandbox & Code Interpreter:** Allows models to execute code dynamically, building tools on the fly.
  * **Context Caching & Large Context Windows:** Improves efficiency and flexibility by storing session/task knowledge without consuming tokens repeatedly.
  * **RAG (Retrieval-Augmented Generation):** Enriches prompts with external or internal data via vector databases, ensuring accurate, up-to-date responses.
  * **Vertex AI Grounding & Extensions:** Connects LLMs to internal corpora or Google Search for verifiable outputs; manages tool lifecycle and automatic model-tool interactions.
  * **Vertex AI Search & RAG Engine:** Managed search and orchestration platforms for building agent knowledge bases and bespoke RAG pipelines.
  * **Vector Databases & Vertex Vector Search:** Store embeddings for high-dimensional semantic search at scale, enabling similarity search and hybrid retrieval.
  * **Vertex AI Feature Store:** Centralized repository for ML features and embeddings, integrated with BigQuery for governance and reuse.

### 7.6 Evaluate: Vertex AI Experiments, Tensorboard and evalyation pipelines

- Vertex AI supports continuous experimentation and evaluation for GenAI development. Key tools include:
  * **Vertex AI Experiments:** Track, compare and analyze model runs, tuning efforts and prompt variations.
  * **TensorBoard Integration:** Visualize metrics, losses, embeddings and model performance in real time.
  * **Evaluation Pipelines:** Automate recurring evaluation tasks, enabling consistent monitoring of model outputs and performance across experiments.
- Together, these tools streamline iterative development, allowing teams to efficiently optimize models, prompts and applications.

#### 7.6.1 Experiment

- Vertex AI enables structured experimentation and collaboration for ML and GenAI workflows:
  * **Workbench Instances:** Jupyter-based environments connected to Google Cloud services with GitHub integration.
  * **Colab Enterprise:** Collaborative coding with AI-assisted code completion and generation.
  * **Vertex AI Experiments:** Tracks experiments, hyperparameters, artifacts and metrics for reproducibility and optimal model selection.
  * **TensorBoard:** Visualizes training metrics, model graphs, embeddings and sample outputs, supporting detailed analysis of models, prompts and tuning strategies.

#### 7.6.2 Evaluation

- Vertex AI provides tools to assess GenAI model performance at scale:
  * **Ground Truth Metrics:** Automatic evaluation against labeled datasets for task-specific accuracy.
  * **LLM-based Evaluation:** Uses large models for pairwise or pointwise comparison of outputs, augmenting human evaluation.
  * **Pre-built Metrics & SDK Integration:** Supports rapid prototyping and flexible evaluation within notebooks using the Vertex AI Python SDK.
- These tools enable scalable, reproducible and automated assessment of models and applications.


### 7.7 Predict: Vertex AI endpoints & Monitoring

* **Vertex AI Endpoints:** Deploy trained or adapted models for online predictions with low latency. Provides access control, scaling and performance monitoring.
* **Citation Checks:** Ensures proper acknowledgment of sources, supports transparency, reproducibility and bias detection.
* **Safety Scores:** Evaluate content against harmful or sensitive categories to mitigate bias, misuse, or unsafe outputs.
* **Watermarking:** Digital watermarking for AI-generated images using SynthID to ensure provenance.
* **Content Moderation & Bias Detection:** Additional layer of checks on outputs to ensure fairness, appropriateness and responsible use.

### 7.8 Govern: Vertex AI Feature Store, Model Registry and Dataplex

* **Purpose:** Ensure lineage, observability, reproducibility, transparency and compliance across data, features, embeddings, models and artifacts in gen AI workflows.
* **Vertex AI Feature Store:** Central repository for features and embeddings; tracks versions, lineage, drift and formulas; supports feature discovery, selection and performance optimization.
* **Vertex AI Model Registry:** Centralized model lifecycle management (including LLMs); versioning, tuning history and artifact tracking; integrates with Vertex Pipelines, Experiments and Model Evaluation; enables monitoring, deployment and observability.
* **Google Cloud Dataplex:** Enterprise-wide data and model governance; provides unified lineage, metadata management and compliance; identifies champion models and golden datasets; enforces IAM-based security and cross-project management.

- **Impact:** These tools collectively enable responsible, transparent and reliable gen AI development, fostering trust, fairness and accuracy.
