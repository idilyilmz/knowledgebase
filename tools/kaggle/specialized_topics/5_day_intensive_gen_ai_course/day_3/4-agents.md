# 4. Agents

https://youtu.be/H4gZd4BCrDQ?si=7W8k3mIZN2QRj2vq

## 1. Introduction

- Generative AI models, like humans, can enhance their capabilities by using external tools to access real-time information or take actions. 
- By combining reasoning, planning and tool use—such as database retrieval or API calls—these models can perform complex, self-directed tasks. 
- This integrated system is known as an agent, which extends AI beyond standalone text generation into practical, decision-driven applications.

## 2. What is an agent?

- Generative AI can go beyond text generation by reasoning, planning and using external tools (like databases or APIs) to access real-time information and take actions. 
- When these capabilities are combined, the system functions as an agent, enabling autonomous, practical and decision-oriented applications.

### 2.1 The model

- In an agent system, the model is the language model that serves as the central decision-maker. 
- It may consist of one or multiple LMs (small or large) capable of instruction-following and structured reasoning 
    - ReAct
    - Chain-of-Thought
    - Tree-of-Thoughts
- Models can be general, multimodal, or task-specific and should be chosen to best fit the agent’s application and the tools it will use. 
- While the model is usually not trained on the agent’s exact configuration, it can be refined with examples that demonstrate the agent’s reasoning processes and tool usage.

### 2.2 The tools

- Foundational models are powerful but limited because they cannot directly interact with the external world. 
- Tools overcome this limitation by allowing agents to access external data and services through APIs 
    - GET
    - POST
    - PATCH
    - DELETE 
- By using tools, agents can perform real-world actions, retrieve up-to-date information and support advanced systems like RAG, significantly expanding their capabilities beyond standalone model generation.

### 2.3 The orchestration layer

- The **orchestration layer** defines the iterative loop an agent follows to process inputs, reason internally and decide on actions. 
- This cycle continues until the agent reaches a goal or stopping condition. 
- Its complexity can range from simple rule-based decisions to advanced chained logic, machine learning, or probabilistic reasoning, depending on the task and agent design.

### 2.4 Agents vs. models

- Models and agents differ in scope and capability. 
- Models rely only on their training data, perform single-turn predictions, lack native tool use and have no built-in logic or session management. 
- Agents extend model knowledge through external tools, maintain session history for multi-turn interactions, natively integrate tools and use a cognitive architecture with reasoning frameworks (e.g., CoT, ReAct) to plan and act toward goals.

### 2.5 Cognitive architecture: How agents operate

- Agent cognitive architectures mirror how humans plan and act, using an iterative cycle of information intake, reasoning, action and adjustment to reach goals. 
- At the core is the orchestration layer, which manages memory, state, planning and reasoning. 
- Agents rely on prompt-engineering frameworks, such as ReAct, Chain-of-Thought (CoT) and Tree-of-Thoughts (ToT), to structure reasoning and decide next actions.
- For example, with ReAct, an agent repeatedly reasons (“thought”), selects an action (often choosing a tool), observes results and refines its plan until producing a final answer. 
- By combining models, tools and orchestration, agents ground responses in real data rather than guessing, improving accuracy, trustworthiness and task effectiveness.

## 3. Tools: Our keys to the outside world

- Language models cannot directly interact with the real world and are limited to their training data. 
- Tools, such as functions, extensions, data stores and plugins, bridge this gap by connecting models to external systems and real-time data. 
- By using tools, agents can perform actions like querying databases, sending emails, updating calendars, or controlling smart devices. 
- Google models primarily support three tool types: 
    - **Extensions**, 
    - **Functions**,
    - **Data Stores**,
- which together enable agents to move beyond understanding information to reliably acting on it in real-world applications.

### 3.1 Extensions

- Extensions provide a standardized, scalable way for agents to interact with APIs without relying on fragile custom code. 
- Instead of manually parsing user input and handling edge cases, Extensions teach the agent **how to use an API** and **what parameters it requires**, using examples. 
- At runtime, the agent dynamically selects the most appropriate Extension based on the user’s request, similar to how a developer chooses the right API for a task. 
- This makes agents more resilient, flexible and easier to maintain, enabling reliable interactions such as booking flights or finding locations.

### 3.2 Sample Extensions

- Google offers ready-made Extensions that can be easily added to projects with minimal setup, such as the Code Interpreter, which lets agents generate and run Python code from natural language. 
- Overall, Extensions enable agents to perceive, interact with and affect the external world, with their selection and use guided by examples defined in each Extension’s configuration.

### 3.3 Functions

- In agent systems, functions mirror traditional software functions: reusable code units with defined inputs and outputs. 
- Instead of a developer deciding when to call them, the model selects which function to use and supplies the required arguments based on their specifications. 
- Unlike Extensions, functions do not make live API calls; they are executed on the client side, with the actual API interaction handled by the application rather than the agent.
- This approach gives developers greater control over data flow, security, timing and transformations. 
- Functions are especially useful when APIs can’t be directly accessed by agents, when calls must occur in specific layers or batches, when extra processing is required, or when developers want to iterate without deploying new infrastructure. 
- Overall, function calling offers a more decoupled and flexible alternative to Extensions.

#### 3.3.1 Use cases

- Function calling lets a model generate structured outputs (such as JSON) that drive complex client-side workflows without the agent directly executing APIs. 
- Instead of returning free-form text that’s hard to parse, the model fills in well-defined parameters, which the client application then uses to make API calls 
    - fetching images or data from Google Places.
- This approach gives developers greater control over execution, security and data flow. 
- It’s especially useful when credentials shouldn’t be exposed, operations are asynchronous or long-running, functions must run on different systems, or when developers want flexibility in how API results are handled. 
- Ultimately, function calling allows the model to assist with reasoning and formatting, while developers decide how and when external actions are executed and whether results should feed back into the agent’s future reasoning.

#### 3.3.2 Function sample code

- This example demonstrates how to implement function calling with a model (like `gemini-2.0-flash-001`) for the ski vacation scenario.
- By defining a Python function (`display_cities`) and linking it as a Tool for the model, the model can generate structured output for the client application to use. 
- Functions provide developers precise control over execution and data flow, while still leveraging the model for generating key inputs. 
- Developers can decide whether the agent sees the external data or not, depending on their application needs.

### 3.4 Data stores

- Data Stores allow a language model to access dynamic, up-to-date information beyond its static training data. 
- They enable developers to provide additional data (like spreadsheets or PDFs) without retraining the model. 
- The Data Store converts this data into embeddings, which the agent can then use to retrieve relevant information and enhance its responses or actions.

#### 3.4.1 Implementation and application

- In Generative AI agents, Data Stores are often implemented as vector databases that store information as embeddings.
- This allows agents to access knowledge beyond their training data in formats like web content, PDFs, CSVs, or text.
- In **Retrieval Augmented Generation (RAG)** applications, a user query is converted into embeddings, matched against the vector database (e.g., using ScaNN) and relevant content is retrieved. 
- The agent then uses this content along with the query to generate a response or take an action, enabling real-time, context-aware and factually grounded interactions.

### 3.5 Tools recap

- Agents have three main types of tools, **Extensions**, **Function Calling** and **Data Stores**, each serving different purposes:
    - **Extensions**: Executed on the agent side; ideal for letting the agent directly interact with APIs, perform multi-step actions, or leverage pre-built integrations (e.g., Vertex Search, Code Interpreter).
    - **Function Calling**: Executed on the client side; used when API calls require security/authentication constraints, timing/order restrictions, or when the API isn’t directly accessible to the agent.
    - **Data Stores**: Executed on the agent side; used to provide agents access to external knowledge for Retrieval Augmented Generation (RAG), including structured data (PDF, CSV, spreadsheets), unstructured data (HTML, text) and relational or non-relational databases.
- These tools can be used independently or together, depending on the agent’s requirements.

## 4. Enhancing model performance with targeted learning

- Enhancing model performance for specific tasks often requires **targeted learning**, beyond general pretraining. There are three main approaches:
    1. **In-Context Learning**: The model learns on the fly using prompts, tools and few-shot examples during inference (like a chef improvising a dish with limited ingredients and a recipe).
    2. **Retrieval-Based In-Context Learning**: The model dynamically retrieves relevant information, tools and examples from external memory or data stores to inform its outputs (like a chef using a well-stocked pantry and cookbooks).
    3. **Fine-Tuning**: The model is trained on a larger dataset of specific examples beforehand, allowing it to handle similar tasks more effectively in the future (like a chef learning an entirely new cuisine).
- Combining these methods within an agent framework balances speed, cost and accuracy, creating a robust, adaptable system for real-world tasks.

## 5. Agent quick start with LangChain

- A real-world agent prototype can be built using **LangChain** and **LangGraph**, which chain together reasoning, logic and tool calls to handle multi-step user queries. 
- Using the **gemini-2.0-flash-001 model** along with tools like **SerpAPI** (Google Search) and **Google Places API**, the prototype demonstrates how the three core components (**Model**, **Orchestration** and **Tools**) work together to achieve a goal. 
- This example illustrates the foundation behind more advanced, managed solutions like **Vertex AI agents** and **Generative Playbooks**.

## 6. Production applications with Vetrex AI agents

- Building production-grade agents goes beyond core components, requiring integration with **user interfaces**, **evaluation frameworks** and **continuous improvement** tools. Google’s Vertex AI platform provides a fully managed environment where developers can define agent goals, tasks, tools, sub-agents and examples through a natural language interface. It also offers tools for testing, evaluation, debugging and performance measurement, allowing developers to focus on agent design while the platform handles infrastructure, deployment and maintenance. Vertex AI supports features like Agent Builder, Extensions, Function Calling and Example Store to enable production-ready agent architectures.
