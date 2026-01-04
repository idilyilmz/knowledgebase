# Agents Companion

https://youtu.be/7rbSwt-7odQ?si=JmIL7VBdolKwpv39

## 1. Introduction

- Generative AI agents go beyond standalone language models by combining reasoning, tools and external information to autonomously achieve specific goals. 
- An agent is designed to perceive its environment, make decisions and take actions (often proactively) using a structured architecture made up of three core components:
    - **Model**: The language model that serves as the agent’s reasoning and decision-making engine.
    - **Tools**: Mechanisms (extensions, functions and data stores) that connect the agent to external systems and up-to-date information, enabling real-world interaction.
    - **Orchestration layer**: The control loop that manages memory, state, planning and reasoning using techniques like ReAct, Chain-of-Thought and Tree-of-Thoughts.
- This paper builds on foundational agent concepts as a “102” guide, focusing on advanced topics such as evaluation methods and practical use of Google’s agent products. 
- It grounds theory in real-world examples, especially automotive AI, which highlights how multi-agent systems operate under constraints like connectivity, safety and coordination across services. 
- Finally, it emphasizes that while building agent prototypes is easy, deploying reliable, high-quality agents in production is challenging, making **quality**, **reliability** and **AgentOps** essential for success.

## 2. AgentOps

- AgentOps is a specialized branch of GenAIOps focused on operationalizing **AI agents** in production. As enterprises move from prototypes to real-world GenAI systems, AgentOps addresses the added complexity agents introduce—such as tool use, orchestration, memory and task decomposition.
- AgentOps builds on existing operational disciplines rather than replacing them:
    - **DevOps** underpins everything by productionizing deterministic software.
    - **MLOps** extends DevOps to handle non-deterministic ML models.
    - **FMOps** focuses on deploying and managing foundation models.
    - **PromptOps** manages prompt versioning, evaluation and optimization.
    - **RAGOps** operationalizes retrieval-augmented generation pipelines.
    - **AgentOps** specifically manages agents’ tools, prompts (goals, profiles, instructions), orchestration logic, memory and decomposition of tasks.
- Like other Ops practices, AgentOps relies on **version control**, **CI/CD**, **testing**, **logging**, **security** and **(critically) metrics**. 
- Metrics-driven development, including A/B testing and experimentation, is central to improving agent performance and measuring business impact. 
- Traditional concerns such as authentication, privacy, scalability and API design remain essential because agents still interact with standard systems.
- Ultimately, AgentOps is not just about technology, it requires aligning people, processes and organizational structures to ensure agents integrate smoothly into real business workflows. 
- Measuring success means tracking both **agent-level performance** and **business outcomes** like,
    - goals achieved, 
    - user journey improvements, 
    - ROI
- which sets the stage for robust agent evaluation and continuous improvement.

### 2.1 Agent Success Metrics

- Agent success metrics are essential for building, monitoring and improving AI agents. 
- While **business metrics** like revenue or user engagement serve as the ultimate “north star,” most agent evaluation focuses on how well agents achieve their intended goals.
- Key metrics include:
    - **Goal completion rate**, since agents are typically designed around accomplishing specific objectives.
    - **Task- and interaction-level metrics**, where complex goals are broken into critical steps that are individually instrumented and measured.
    - **Operational metrics** such as latency, error rates and reliability, drawn from standard application telemetry. These are especially important for agents due to their non-deterministic behavior.
    - **Human feedback**, such as thumbs up/down or structured reviews from users, testers, or domain experts, which provides direct insight into agent quality and usefulness.
- Together, these serve as **KPIs** that enable high-level observability of agent performance in production. 
- For deeper understanding and debugging, agents should also generate **detailed traces** of internal reasoning and actions, which are examined when issues arise rather than continuously monitored as metrics.
- Finally, beyond manual testing, **automated testing** during development is critical for efficiently evaluating agent behavior, uncovering weaknesses and ensuring consistent improvements over time.

## 3. Agent Evaluation

- Agent evaluation is critical for moving AI agents from proof-of-concept to production. 
- Unlike standard generative model evaluation, which mainly focuses on final outputs, agent evaluation must also examine *how* decisions are made. 
- It consists of three main components:
    1. **Assessing agent capabilities**: Evaluating fundamental skills such as instruction understanding and logical reasoning.
    2. **Evaluating trajectory and tool use**: Analyzing the agent’s step-by-step behavior, including strategy selection, tool usage and efficiency in reaching a solution.
    3. **Evaluating the final response**: Judging the accuracy, relevance and overall quality of the agent’s final output.
- Together, these components provide a holistic view of agent performance, covering both reasoning processes and outcomes.

### 3.1 Assessing Agent Capabilities

- Assessing agent capabilities starts with leveraging public benchmarks and technical reports to understand core strengths and limitations, such as model performance, hallucinations, tool calling and planning. 
- Examples include BFCL and **τ-bench** for tool use, PlanBench for planning and reasoning and holistic benchmarks like AgentBench for end-to-end performance. 
- Specialized leaderboards can offer more targeted insights when aligned with a specific use case.
- However, benchmarks are only a starting point. 
- Agents inherit behaviors from their underlying LLMs and other components, as well as from established conversational and workflow systems. 
- Therefore, organizations must evaluate agents in simulated, use-case–specific scenarios, examining both the final responses and the trajectories (steps taken to reach outcomes).
- Investing in automated, agent-specific evaluation (similar to automated testing in software engineering) provides faster feedback and greater confidence. 
- The quality and representativeness of the evaluation dataset is especially critical, as it must closely reflect real-world interactions the agent will face.

### 3.2 Evaluating Trajectory and Tool Use

- Agents perform multiple internal actions (such as referencing context, searching knowledge bases, or calling APIs) before producing a response. 
- This sequence of actions is called a *trajectory*. 
- Comparing an expected trajectory with the agent’s actual trajectory helps developers debug errors, identify inefficiencies and improve agent performance.
- Trajectory and tool-use evaluation can be done using six main ground-truth–based metrics:
    1. **Exact match**: Requires the agent’s action sequence to perfectly match the ideal path.
    2. **In-order match**: Checks that required actions occur in the correct order, allowing extra steps.
    3. **Any-order match**: Verifies that all required actions occur, regardless of order and allows extras.
    4. **Precision**: Measures how many tool calls made by the agent are correct or relevant.
    5. **Recall**: Measures how many required tool calls were successfully included.
    6. **Single-tool use**: Checks whether the agent used a specific tool at least once.
- These metrics offer different perspectives and should be chosen based on the use case’s tolerance for flexibility. 
- A key limitation is the need for predefined reference trajectories, though emerging approaches like agent autoraters (like, *Agent* as a *Judge*) aim to reduce this dependency.

### 3.3 Evaluating the Final Response

- Evaluating an agent’s final response focuses on whether it successfully achieves its intended goals. 
- Success criteria should be customized to the use case, such as accuracy for a retail chatbot or clarity, tone and relevance for a research assistant. 
- This evaluation can be automated using an *autorater*, an LLM acting as a judge that assesses responses against predefined criteria. 
- Because there is often no single ground truth, clearly and precisely defining evaluation criteria is critical. 
- Prebuilt criteria from existing libraries can serve as a starting point but should be refined to reflect what “good” means for the specific application.

### 3.4 Human-in-the-Loop Evaluation

- Human-in-the-loop evaluation complements automated agent evaluation by addressing challenges such as subjective judgment, contextual understanding and bias mitigation. 
- Humans are especially valuable for assessing qualities that are hard to quantify, validating creative or nuanced behavior and ensuring automated metrics align with real preferences. 
- Human feedback also supports iterative improvement of agents and helps calibrate autoraters. 
- Common approaches include direct expert assessments, comparative evaluations across agents or versions and user studies where participants interact with the agent and provide feedback on its effectiveness and usability.

### 3.5 More about Agent Evaluation

- Agent evaluation is complex and still evolving. Practical methods only address part of the challenge, as evaluation data can be scarce and incomplete, even when using synthetic data or LLMs as judges. 
- Current approaches often overemphasize final outcomes while overlooking reasoning processes and intermediate actions. 
- Additional difficulties arise from multimodal agents (image, audio, video), multi-turn interactions and deployment in dynamic, real-world environments that are hard to simulate in controlled settings
- Looking forward, the field is moving toward **process-based evaluation** that emphasizes reasoning and decision paths, greater use of **AI-assisted evaluation** for scalability and stronger alignment with **real-world contexts**. 
- New standardized benchmarks, along with increased focus on **explainability and interpretability**, are emerging to enable fairer comparisons and deeper understanding of agent behavior. 
- Continuous refinement of evaluation methods is essential to ensure agents are deployed responsibly, effectively and ethically.

## 4. Multiple Agents & Their Evaluation

- AI systems are increasingly moving toward **multi-agent architectures**, where specialized agents collaborate to tackle complex tasks. 
- Each agent operates independently, possibly using a different LLM and focuses on a particular role or subtask. 
- Compared to single-agent systems, multi-agent setups offer several advantages:
    - **Enhanced Accuracy:** Agents cross-verify each other’s work for more reliable results.
    - **Improved Efficiency:** Parallel work allows faster task completion.
    - **Better Handling of Complexity:** Large tasks are broken into manageable subtasks.
    - **Increased Scalability:** Additional agents with specialized skills can be added easily.
    - **Improved Fault Tolerance:** Other agents can compensate if one fails.
    - **Reduced Hallucinations and Bias:** Diverse perspectives help produce more trustworthy outputs.
- Evaluation of multi-agent systems focuses on measuring their **effectiveness, reliability and adaptability**, taking into account the interactions, collaboration and performance of the team as a whole.

### 4.1 Understanding Multi-Agent Architectures

- Multi-agent architectures decompose complex problems into distinct tasks handled by specialized agents, enabling **structured reasoning, decentralized problem-solving and scalable automation**. 
- Key principles include **modularity, collaboration and hierarchy**, allowing agents to work together efficiently.
- Common agent roles include:
    - **Planner Agents:** Break down high-level goals into structured sub-tasks.
    - **Retriever Agents:** Fetch relevant data from external sources dynamically.
    - **Execution Agents:** Perform computations, generate outputs, or call APIs.
    - **Evaluator Agents:** Monitor and validate outputs for correctness and alignment.
- These architectures go beyond single-agent or simple prompt-based approaches, supporting **adaptive, explainable and efficient AI-driven workflows**.

### 4.2 Multi-Agent Design patterns and Their Business Impact
- Effective multi-agent architectures rely on **design patterns** that define how agents interact, delegate tasks and share roles. Key patterns include:

| Type              | Description                                                                       | Example                                                                               |
| ----------------- | --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| **Sequential**    | Agents perform tasks one after another, passing outputs to the next agent.        | An assembly line with each worker completing a step before passing the product along. |
| **Hierarchical**  | A “manager” agent oversees the workflow, delegating tasks to “worker” agents.     | A leader agent makes strategic decisions while followers execute them.                |
| **Collaborative** | Agents work together, sharing information and resources to achieve a common goal. | A research team where each member contributes expertise to a joint project.           |
| **Competitive**   | Agents compete to optimize individual performance while pursuing a shared goal.   | LLMs playing a game like Overcooked-AI, coordinating and competing simultaneously.    |

- **Benefits:**
    - Reduces operational bottlenecks
    - Improves knowledge retrieval
    - Enhances reliability and scalability of AI deployments
    - Supports agile decision-making and efficient workflow execution
- The choice of pattern depends on the **application context** and **desired level of interaction** between agents.

### 4.3 Important components of Agents
- LLM-based AI agents rely on several interrelated components that enable autonomous operation, intelligent interaction and collaboration in multi-agent systems:
    - **Interaction Wrapper:** Interfaces with the environment, managing diverse input/output modalities.
    - **Memory Management:** Handles short-term working memory (context, cache, sessions) and long-term memory (learned patterns, skills, user profiles). Includes reflection to decide which items to store or share.
    - **Cognitive Functionality:** Uses reasoning frameworks like Chain-of-Thought (CoT), ReAct and planners to decompose tasks, self-correct and refine user intent.
    - **Tool Integration:** Enables the use of external tools via dynamic registries and retrieval-augmented generation (Tool RAG).
    - **Flow / Routing:** Manages connections with other agents, supporting task delegation, handoffs and agent-as-tool interactions.
    - **Feedback Loops / Reinforcement Learning:** Incorporates past performance metrics to improve decision-making and adaptability.
    - **Agent Communication:** Structured protocols for agents to collaborate, achieve consensus and solve complex tasks.
    - **Remote Agent Communication:** Ensures durable asynchronous messaging, task updates and user integration across remote agents.
    - **Agent & Tool Registry (Mesh):** Centralized system for discovering, registering and selecting agents/tools based on ontology, capabilities and performance metrics, supporting autonomous planning and task execution.
- **Purpose:**
    - These components collectively provide a **robust foundation** for autonomous reasoning, tool use, learning and multi-agent collaboration in complex environments.

### 4.4 Challenges in Multi-Agent systems
- While multi-agent systems provide benefits like parallelism, specialization and improved reliability, they also introduce several challenges:
    - **Task Communication:** Most frameworks rely on message passing rather than structured asynchronous task management.
    - **Task Allocation:** Dividing complex tasks efficiently among agents is difficult, with feedback loops often left for developers to implement.
    - **Coordinating Reasoning:** Facilitating effective debate and collaborative reasoning between agents requires advanced coordination mechanisms.
    - **Managing Context:** Tracking all relevant information, tasks and interactions between agents can become overwhelming.
    - **Time and Cost:** Multi-agent operations can be computationally intensive, leading to higher runtime costs and increased user latency.
    - **System Complexity:** While each agent may remain simple, the overall system becomes more complex, similar to challenges in microservice architectures.
- **Implication:** Careful design and coordination are essential to build efficient, scalable and robust multi-agent systems.

### 4.5 Multi-Agent Evaluation
- Evaluating multi-agent systems builds on single-agent evaluation, but with additional considerations due to complexity and collaboration:
- **Core Metrics Remain:** Business metrics as the “north star,” goal completion, critical task success, telemetry metrics (latency, errors) and traces for debugging.
- **Trajectory and Final Response Evaluation:**
  - Trajectories now encompass multiple agents collaborating on tasks.
  - The final output can still be evaluated independently.
  - Stepwise evaluation allows assessment of each agent individually and the system as a whole.
- **Multi-Agent Specific Considerations:**
    - **Cooperation and Coordination:** Are agents effectively collaborating to reach shared objectives?
    - **Planning and Task Assignment:** Did agents follow the plan, or deviate into inefficiencies?
    - **Agent Utilization:** Are the right agents chosen for tasks, delegation, or handoff?
    - **Scalability:** Does adding more agents improve system performance, reduce latency, or enhance efficiency?
- **Implication:** Evaluation tools from single-agent systems apply, but analyses must account for interactions, dependencies and distributed reasoning across multiple agents.

## 5. Agent RAG: A Critical Evalution in Retrieval-Augmented Generation
- Agentic RAG represents a major evolution of traditional RAG in multi-agent systems by adding autonomous retrieval agents that refine queries and reasoning iteratively. 
- Key enhancements include:
    - **Context-Aware Query Expansion:** Agents generate multiple refined queries to retrieve more relevant information.
    - **Multi-Step Reasoning:** Complex queries are decomposed into logical steps for structured retrieval and response synthesis.
    - **Adaptive Source Selection:** Retrieval agents dynamically choose the most appropriate knowledge sources rather than relying on a single vector database.
    - **Validation and Correction:** Evaluator agents verify retrieved data for hallucinations or contradictions before integration.
- **Impact:** Agentic RAG improves accuracy, explainability and adaptability, making it essential for enterprise applications involving complex knowledge retrieval, such as legal research, scientific discovery and business intelligence.

### 5.1 Agentic RAG and its Importance
- Agentic RAG enhances traditional Retrieval-Augmented Generation by adding autonomous agents that orchestrate retrieval, evaluate sources and optimize the use of retrieved information.
- **Key Advantages:**
    - **Improved Accuracy:** Agents assess the reliability of sources, reducing errors and hallucinations.
    - **Enhanced Contextual Understanding:** Agents consider both the user query and retrieved information to generate relevant, meaningful responses.
    - **Increased Adaptability:** Agents dynamically adjust retrieval strategies to account for evolving information, ensuring up-to-date and precise outputs.
- **Impact:** This approach is especially valuable in dynamic, information-heavy domains such as healthcare, finance and legal research, helping professionals access accurate and comprehensive data efficiently.

### 5.2 Better Search, Better RAG
- High-quality search is critical for effective RAG systems, as it determines the relevance and recall of retrieved information. 
- Agentic RAG enhances search by allowing multiple queries, filtering, ranking and iterative refinement.
- **Key Techniques to Improve Search Performance Before Adding Agents:**
    - **Document Parsing & Chunking:** Break complex documents into semantically coherent chunks (tables, images, headings) for better indexing.
    - **Metadata Enrichment:** Add synonyms, keywords, authors, dates, tags and categories to improve search filtering, boosting and control.
    - **Embedding Optimization:** Fine-tune embeddings or use search adaptors to better represent domain-specific data.
    - **Faster Vector Databases:** Upgrade to high-speed vector search to improve both latency and accuracy.
    - **Ranking:** Use rankers to refine top results from approximate vector searches.
    - **Grounding Checks:** Verify that generated outputs are actually supported by retrieved chunks.
- **Tools:** Vertex AI Search provides all these capabilities out-of-the-box, while custom pipelines can be built using standalone APIs or RAG Engine with a Python interface.
- In short, improving search quality is foundational to effective RAG and Agentic RAG implementations.

## 6. Agents in the enterprice

### 6.1 Manager of agents 

- In 2025, AI agents are set to transform enterprises by assisting employees with tasks or autonomously running background automation. 
- Different teams can leverage agents in ways that streamline workflows and enhance productivity:
    - **Business analysts:** Generate insights, analyze trends and create data-driven presentations.
    - **HR teams:** Improve onboarding and manage complex processes like benefits selection.
    - **Software engineers:** Detect and fix bugs proactively, accelerating development cycles.
    - **Marketers:** Optimize campaigns, analyze performance and improve content recommendations.
- **Two emerging types of agents:**
    1. **Assistants:** Interact with users to execute tasks, either synchronously or asynchronously. They can be general-purpose or specialized, helping with tasks like scheduling, coding, research, sales, or marketing.
    2. **Automation Agents:** Operate in the background, monitoring systems or data, making decisions and taking actions—serving as the backbone of intelligent automation.

- **Future of Knowledge Work:**
    - Workers will increasingly become **managers of agents**, orchestrating multiple agents, monitoring long-running tasks, approving actions and chaining outputs to new tasks. 
    - Novel UIs will emerge for managing multi-agent systems effectively.

- **Google Agentspace:**
    - Create agents via low-code/no-code interfaces or full code.
    - Manage agent permissions and access.
    - Invoke appropriate agents when needed.
    - Monitor, manage and orchestrate multiple agents in a team-oriented interface.

- In essence, 2025 marks a shift where humans manage AI teams rather than performing every task manually.

### 6.2 Google Agentspace

- Google Agentspace is an enterprise AI platform designed to enhance productivity by providing streamlined access to information and automating complex workflows through intelligent agents. 
- It combines the reasoning capabilities of Gemini, Google’s search infrastructure and secure access to enterprise data across locations.
- **Key Features:**
    - **Enhanced Knowledge Access:** Consolidates disparate content sources, delivers personalized and grounded AI-generated answers and supports diverse data formats.
    - **Workflow Integration:** Embeds AI assistance and intelligent agents into operational workflows.
    - **Trust and Security:** Built-in security, explainability, governance, SSO authentication, user-level permissions, RBAC, VPC Service Controls and IAM integration ensure compliance and data protection.
    - **Intelligence and Personalization:** Uses machine learning, semantic understanding, knowledge graphs and LLMs to deliver highly relevant results. Supports user-level personalization and enterprise-level customization.
    - **Connectivity and Scalability:** Connects to multiple enterprise systems with automated data refreshes, eliminating silos and supporting growth across regions, languages and peak usage.
    - **Adaptive and Grounded AI:** Real-time feedback and Blended RAG enable AI applications grounded in enterprise data.
- In essence, Agentspace provides secure, intelligent and scalable AI-driven workflows that unify information access, enhance decision-making and automate enterprise tasks effectively.

#### 6.2.1 NotebookLM Enterprise

- NotebookLM is an AI-powered research and learning tool designed to help users consolidate, understand and synthesize complex information from various sources, such as documents and notes. 
- It functions as a dedicated research assistant, enabling deeper comprehension beyond mere information collection.
- **Versions and Features:**
    - **NotebookLM Plus:** Premium tier with increased storage, advanced summarization, enhanced question-answering and tools for identifying relationships between sources.
    - **NotebookLM Enterprise:** Enterprise-grade version offering the above capabilities for organizational use, plus AI-generated audio summaries for efficient knowledge absorption. It also includes enterprise-level security and privacy protections.
- **Technical Aspects:**
    - Uses LLMs to extract key concepts, summarize documents and process uploaded materials.
    - Audio summaries leverage advanced text-to-speech technology for natural, clear playback.
- In essence, NotebookLM streamlines research, improves comprehension and provides secure, scalable solutions for both individual and enterprise users.

#### 6.2.2 Google AgentSpace Enterprise

- **Google Agentspace** is a unified, company-branded AI platform that provides employees with conversational access to enterprise information. 
- It integrates Google’s search capabilities to answer complex queries, offer proactive recommendations and access both structured and unstructured data. 
- Features include translation, pre-built connectors to popular apps (e.g., Confluence, Jira, SharePoint), workflow management and real-world task execution.

- **Agentspace Enterprise Plus** allows organizations to create custom AI agents tailored to specific business functions, enabling research, content generation, task automation and multi-step workflows. 
- These agents can connect to internal and external systems, adhere to company policies and leverage proprietary data. 
- A centralized interface simplifies discovery, development, deployment and management of these specialized agents.

## 7. From agents to contractors
- Current AI agent interfaces are simple (typically defining goals, instructions, tools and examples) which works for prototypes but often leads to underspecified behavior and difficulties in moving to production. 
- To address this, the proposal is to evolve agents into **“contract-adhering agents”**, where agents operate under more explicit, structured contracts. 
- This approach is better suited for complex, high-stakes tasks and aims to improve reliability, clarity and production readiness.

### 7.1 Contracts

- The **contractor model** introduces standardized contracts between a requester and AI agents to reduce ambiguity and improve reliability for complex, high-stakes tasks. 
- Contracts precisely define expected outcomes, allow negotiation and clarification before execution and establish rules for creating subcontracts when tasks need to be broken down further.
- A contract includes required elements such as a clear task description, detailed deliverables and acceptance criteria, expected cost and duration and defined reporting and feedback mechanisms. 
- Optional fields cover scope boundaries and allowed input sources.
- During **contract iteration**, agents can flag underspecified requirements, negotiate cost, identify risks and request additional inputs. 
- This structured, negotiable approach enables agents to validate progress against explicit expectations and iteratively refine their work until the agreed objectives are met.

### 7.2 Contract Lifecycle

### 7.3 Contract execution

- Contract execution requires a runtime capable of fulfilling contracts by strictly adhering to defined specifications. 
- By prioritizing quality and completeness over low latency, the system can fully leverage LLM capabilities, generating multiple solution candidates, reviewing and scoring them and iteratively refining results. 
- The execution engine continuously self-validates outputs against objective criteria and self-corrects until all contract requirements are met. 
- This validation-driven, iterative approach (successfully demonstrated in systems like AlphaCode) enables more reliable and high-quality AI outcomes.

### 7.4 Contract Negotiation

- Contract negotiation enables automation agents to handle complex enterprise tasks using LLMs with fewer constraints on latency and cost, increasing reliability and business value. 
- To ensure trust, fair resource allocation and proper prioritization, contracts introduce a negotiable notion of cost and priority between the requester and the contractor. Beyond cost, agents can also negotiate specifications, deliverables and feedback requirements, helping clarify expectations and ensure each contract is resourced and defined appropriately.

### 7.5 Contract Feedback

- Contract feedback provides a structured way for agents to surface ambiguities and issues early, which is essential as tasks grow more complex. 
- Contractors can assess the contract immediately upon receipt and provide ongoing feedback at predefined intervals. 
- This feedback focuses on clarifying underspecified or conflicting requirements, identifying inconsistencies and resolving misunderstandings to ensure the task is correctly defined and executed.

### 7.6 Subcontracts

- Subcontracts enable contractors to break down complex tasks into smaller, more manageable subtasks. 
- When a task is too complex to handle directly, contractors generate standardized subcontracts and add them to the execution queue. 
- This capability is made possible by formalized contracts, allowing contractors to create, manage and coordinate multiple contracts in a consistent and structured way.

## 8. Automative AI: Real World Use of Multi-Agent Architecture

- Google’s AI Co-Scientist demonstrates how multi-agent LLM systems can accelerate scientific research. 
- It uses specialized agents with distinct roles—such as data processing, hypothesis generation, validation and collaboration—to mirror the scientific method through a “generate, debate and evolve” workflow. 
- By combining multiple LLMs, each optimized for different research tasks, the system can produce, critique and refine hypotheses iteratively. 
- In practice, this approach has generated novel insights, such as proposing new drug mechanisms and candidates for liver fibrosis, highlighting the power of dynamic, collaborative AI systems in complex domains like scientific discovery, enterprise automation and knowledge management.

### 8.1 Specialized Agents

#### 8.1.1 Conversation Navigation Agent

- The Conversational Navigation Agent assists users with location-based tasks such as finding places and navigating routes. 
- It understands natural language navigation requests, queries services like Google Places and Maps for relevant results, re-ranks options using user preferences and past behavior and integrates directly with a car’s navigation system to provide seamless, personalized guidance.

#### 8.1.2 Conversational Media Search Agent

- The Conversational Media Search Agent helps users discover and play music, audiobooks and podcasts through natural language voice commands. 
- It searches local libraries, streaming services and the web when needed, recommends content based on context such as mood, time, or environment and can identify similar artists or related content to match user preferences.

#### 8.1.3 Message Composition Agent

- The Message Composition Agent assists users in drafting, summarizing and sending messages or emails hands-free while driving. 
- It interprets voice commands, generates context-appropriate message drafts, allows users to review or modify them and integrates with messaging platforms such as SMS, WhatsApp and email.

#### 8.1.4 Car Manual Agent

- The Car Manual Agent helps users with car-related questions by using a RAG system to fetch relevant sections from the car manual. 
- It summarizes and contextualizes the information with an LLM and provides links to detailed documentation or instructional videos when needed.

#### 8.1.5 General Knowledge Agent

- The General Knowledge Agent answers factual questions on topics like history, science and culture. 
- It accesses a broad knowledge base, provides contextual explanations, stays grounded in facts and maintains context for follow-up questions.

### 8.2 Patterns in Use

#### 8.2.1 Hierarchical Pattern

- The Hierarchical Pattern uses a central **Orchestrator Agent** to classify user queries and route them to specialized agents. 
- It manages conversation flow, maintains context, directs requests to the right agent (like, Navigation Agent for location queries) and handles fallback strategies when needed.

#### 8.2.2 Diamond Pattern

- The **Diamond Pattern** adds a **moderation/rephraser step** to the hierarchical flow. 
- After specialized agents generate responses, a **Rephraser Agent** adjusts tone, style and presentation based on user preferences and context, ensuring responses are clear, personalized and suitable for situations like driving.

#### 8.2.3 Peer-to-Peer

- **Peer-to-Peer pattern** allows agents to **handoff queries to each other** if the central orchestrator misroutes a request. 
- Benefits include:
    1. **Resilience** – the system can recover from misclassifications.
    2. **Domain-aware routing** – specialized agents better judge which queries they can handle.
    3. **Simpler orchestration** – the central orchestrator doesn’t need perfect routing accuracy.

#### 8.2.4 Collaborative Pattern

- The **Collaborative Pattern** has multiple agents work together on different aspects of the same task. 
- A **Response Mixer Agent** synthesizes their outputs into a **comprehensive answer**. 
- Key points:
    1. Useful when queries require **different expertise**.
    2. No single agent has all the needed information.
    3. Provides **multiple perspectives** to the user.
    4. Leverages **distinct knowledge bases** of each agent.
- Unlike competitive systems, contributions are **complementary**, not redundant. 
- Example: handling hydroplaning—Car Manual Agent gives safety info, Driving Tips Agent provides techniques and General Knowledge Agent explains physics. 
- The mix produces a **complete, practical response**.

#### 8.2.5 Response Mixer Agent

- The **Response Mixer Agent** combines outputs from multiple specialized agents into a **single, accurate and helpful answer**. 
- It evaluates responses based on **accuracy and relevance**, removes errors and merges the most useful parts.
- **Example:** For a query on aquaplaning:
    - Car Manual Agent gives vehicle-specific safety systems.
    - General Knowledge Agent explains what aquaplaning is.
    - Safety Tips Agent provides practical driving advice.
- The Response Mixer merges these into one comprehensive response, ensuring **critical information is preserved** and the user receives the **best overall answer**. 
- This method also protects against misrouting or partial responses.

#### 8.2.6 Adaptive Loop Pattern

- The **Adaptive Loop Pattern** allows agents to **iteratively refine results** until they meet the desired criteria. 
- Instead of giving up when an initial query fails, the agent **reformulates and broadens searches progressively**.
- **Example:** A user asks for an Italian restaurant with vegan options:
    1. First search: "Italian restaurants with vegetarian options"
    2. Second search: "Italian restaurants" filtered for plant-based options
    3. Third search: "Vegan restaurants" filtered for Italian-influenced cuisine
- The agent then presents the **best matches**, adapting dynamically to context and availability, ensuring useful results even when exact matches are missing.

### 8.3 Advantages of Multi-Agent Architecture for Automotive AI

- Multi-agent architectures in automotive AI offer **specialization, efficiency, speed and resilience**:
    -  **Specialization:** Each agent focuses on a specific domain (e.g., Navigation, Media, Car Manual), improving expertise and performance in that area.
    -  **Efficiency:** Narrow tasks allow for optimized processing, delivering faster, higher-quality responses at lower computational cost.
    - **Speed:** Critical functions (climate control, windows) run on fast, on-device agents, while less urgent tasks (restaurant searches) use cloud-based agents.
    - **Resilience:** Essential functions continue even if connectivity drops, ensuring robust operation.
- This approach allows automotive AI to handle complex tasks reliably while prioritizing real-time responsiveness for safety and convenience.

## 9. Agent Builder

- **Vertex AI Agent Builder** is Google’s comprehensive platform for building, connecting and deploying AI agents. 
- It combines **Google Cloud’s engineering and security**, **DeepMind AI research** and **AgentOps best practices** to provide a full developer ecosystem.
- Key features include:
    - **Vertex AI Agent Engine:** Managed autoscaling runtime, integrations with open-source agent libraries and essential services like session management, examples, trace and evaluation.
    - **Vertex AI Eval Service:** Stable and scalable tools for evaluating LLMs, RAG and agents, with integrations for monitoring and experimentation.
    - **Extensive Agent Tools:**
        - Retrieval via Vertex AI Search or RAG Engine.
        - Database access via Gen AI Toolbox.
        - API integrations with enterprise ACLs and Apigee Hub for managed tools.
    - **LLM Support:** Access to Vertex AI Model Garden and Gemini models to power agentic workflows.
- This platform enables developers to safely and efficiently deploy high-quality, scalable agents across enterprise applications.
