# 1. Introduction To Building AI Applications With Foundation Models

I asked chatGPT to summarize the most important parts for me.

## 1.1 Why AI engineering exists now

Three major shifts created the rise of **AI engineering**:

**1. Model scale**

* Modern AI models (ChatGPT, Gemini, etc.) are extremely large and powerful.
* Training them requires huge **data, compute, and expert talent**.
* Only a few organizations can train them.

**2. Model-as-a-Service**

* Companies provide these models through **APIs**.
* Developers can build AI applications **without training their own models**.

**3. Lower barrier to entry**

* Developers can build AI apps by **using existing models instead of training them**.
* This dramatically speeds up development and reduces cost.

➡️ Result:
Demand for AI apps increased **while the difficulty of building them decreased**.

This led to **AI engineering** — building applications on top of powerful pretrained models.

---

## 1.2 What changed vs traditional ML

Traditional ML and modern AI engineering differ in key ways.

### Traditional ML

Typical workflow:

1. Collect data
2. Label data
3. Train a task-specific model
4. Deploy it

Example models:

* Fraud detection
* Recommendation systems
* Churn prediction

Each model is usually built for **one specific task**.

---

### AI Engineering (with foundation models)

Workflow changes:

1. Use a **pretrained foundation model**
2. Adapt it using techniques like:

   * Prompt engineering
   * RAG
   * Fine-tuning

Instead of training a model from scratch.

Key benefits:

* Faster development
* Less data required
* Lower infrastructure cost

---

## 1.3 Language models → Large language models

### What is a language model?

A **language model** predicts the probability of the next word or token in a sequence.

Example:

Prompt

```
My favorite color is ___
```

Prediction

```
blue
```

Language models work by learning **statistical patterns in text**.

---

### Tokens

Models don’t process words directly — they process **tokens**.

A token can be:

* a word
* part of a word
* a character

Example:

Sentence

```
I can’t wait to build AI applications
```

might become tokens like:

```
I | can | ’t | wait | to | build | AI | applications
```

Important facts:

* ~1 token ≈ ¾ of a word
* Models have a **vocabulary of tokens**

Example vocabulary sizes:

* Mixtral: ~32k tokens
* GPT-4: ~100k tokens

---

### Two types of language models

#### 1. Masked Language Models (MLM)

Predict **missing tokens anywhere in the sentence**.

Example:

```
My favorite ___ is blue
```

Predict → `color`

Example model:

* BERT

Used for:

* classification
* sentiment analysis
* code understanding

---

#### 2. Autoregressive Language Models

Predict **the next token based on previous tokens**.

Example:

```
My favorite color is
```

Predict → `blue`

These models **generate text sequentially**, making them ideal for:

* chatbots
* writing
* coding
* translation

Examples:

* GPT models
* Claude
* Gemini

Most generative AI today uses **autoregressive models**.

---

### Generative AI

Because language models can generate open-ended outputs, they are called **generative models**.

A language model essentially acts like a **completion machine**:

Example:

Prompt

```
To be or not to be
```

Completion

```
that is the question
```

Many tasks can be framed as **text completion**:

* translation
* summarization
* question answering
* classification
* coding

---

## 1.4 Self-supervised learning (why LLMs can scale)

Traditional ML needs **labeled data**.

Example:

```
Transaction → fraud / not fraud
```

Labeling data is:

* expensive
* slow
* hard to scale

---

### Self-supervision

Language models avoid this problem using **self-supervised learning**.

The **text itself becomes the label**.

Example sentence:

```
I love street food.
```

Training examples:

```
Input → Output
<BOS> → I
<BOS> I → love
<BOS> I love → street
<BOS> I love street → food
```

This means:

* no manual labeling required
* huge datasets can be used

Because the internet contains massive text data:

* books
* articles
* blogs
* Reddit

LLMs can scale to **hundreds of billions of parameters**.

---

## 1.5 Large Language Models → Foundation Models

LLMs originally handled **only text**.

But modern models handle **multiple data types**.

Examples:

* text
* images
* audio
* video
* code

These are called **foundation models**.

---

### Multimodal models

A **multimodal model** processes multiple types of input.

Example:

Input:

* text
* image

Output:

* text
* image description

Examples:

* GPT-4V
* Gemini
* Claude 3

---

### From task-specific → general-purpose models

Old ML:

* One model per task.

Example:

* translation model
* sentiment model
* spam model

Foundation models:

* One model can do **many tasks**.

Examples:

* translation
* summarization
* classification
* coding
* reasoning

---

## 1.6 Adapting foundation models

Instead of training new models, developers adapt existing ones using:

### Prompt engineering

Writing better prompts to guide model behavior.

Example:
Provide instructions + examples.

---

### Retrieval-Augmented Generation (RAG)

Provide external knowledge from a database.

Example:

* company docs
* product info
* user data

The model retrieves relevant info before generating.

---

### Fine-tuning

Further train the model on **task-specific data**.

Example:

* brand-style product descriptions
* legal documents
* medical text

---

## 1.7 Why AI engineering is exploding

Three main factors:

### 1. General-purpose AI

AI can now automate many communication tasks:

* writing emails
* coding
* customer support
* marketing content
* image generation

---

### 2. Massive investment

AI investment is rapidly increasing:

* billions of dollars globally
* companies racing to add AI features

---

### 3. Extremely low entry barrier

Developers can use AI models through:

* APIs
* SDKs
* simple prompts

This means **any developer can build AI applications quickly**.

---

## Core Idea of the Chapter

The entire chapter can be summarized in one concept:

**AI engineering = building applications on top of foundation models instead of training models from scratch.**

Key enablers:

* large language models
* self-supervised learning
* multimodal foundation models
* API access to powerful models

Here’s a **clean, structured summary in the same format** as before so you can quickly review the chapter.

---

# 2. Foundation Model Use Cases

## 2.1 Why foundation models have so many applications

Foundation models are **general-purpose**, meaning they can solve many different tasks.

Reasons the use cases are so broad:

* They understand **natural language**
* They generate **open-ended outputs**
* They can work across **multiple modalities (text, image, video, etc.)**

Because of this, the number of possible AI applications is **almost unlimited**.

Organizations categorize AI use cases differently, for example:

**AWS**

* Customer experience
* Employee productivity
* Process optimization

**O’Reilly survey**

* Programming
* Data analysis
* Customer support
* Marketing copy
* Research
* Web design
* Art

Another way to categorize them is by **business value**:

* Cost reduction
* Efficiency
* Growth
* Innovation

---

## 2.2 Jobs most exposed to AI

Researchers studied how much AI could reduce the time needed for certain tasks.

A job is **“exposed to AI”** if AI can reduce task time by **50% or more**.

Highly exposed occupations include:

* Translators
* Writers
* Web designers
* Tax preparers
* Quantitative analysts
* Mathematicians

These jobs involve **language, analysis, or digital content**, which AI handles well.

Low exposure jobs include:

* Cooks
* Stonemasons
* Athletes

These rely heavily on **physical skills**.

---

# 2.3 Major Categories of AI Applications

The chapter groups common AI applications into **eight major categories**.

---

# 2.3.1 Coding

Coding is **the most popular AI use case**.

Examples:

* Code completion
* Code generation
* Code translation
* Debugging
* Documentation

Example tools:

* GitHub Copilot
* gpt-engineer
* screenshot-to-code

AI can help developers with:

* generating code
* refactoring
* documentation
* testing
* commit messages

Productivity impact (McKinsey research):

| Task                  | Productivity Gain |
| --------------------- | ----------------- |
| Documentation         | ~2x               |
| Code generation       | 25–50%            |
| Complex system design | small improvement |

AI currently performs **better at simpler tasks**, especially frontend work.

Key takeaway:
AI likely **augments developers rather than fully replacing them**.

---

# 2.3.2 Image and Video Production

AI is very good at **creative generation**.

Popular tools:

* Midjourney
* Adobe Firefly
* Runway
* Pika Labs
* Sora

Common uses:

**Consumer**

* profile pictures
* photo editing
* video creation
* art generation

**Enterprise**

* marketing visuals
* ad generation
* concept art
* campaign variations

Example:
AI can automatically generate seasonal ad variations:

* winter (snow)
* fall (orange leaves)

---

# 2.3.3 Writing

Writing is a natural use case because language models are trained for **text completion**.

Examples:

**Consumer**

* emails
* blog posts
* essays
* books
* social media posts

**Enterprise**

* marketing copy
* product descriptions
* internal reports
* outreach emails
* SEO content

Research findings:

* AI reduced writing time by **40%**
* Output quality improved by **18%**

AI is especially helpful for people who struggle with writing.

---

### Downsides

AI writing can also create problems:

* spam content
* SEO content farms
* AI-generated fake books
* misinformation

Example:
Some websites produce **1000+ AI articles per day**.

---

# 2.3.4 Education

AI can act as a **personalized tutor**.

Use cases:

* textbook summarization
* practice questions
* essay feedback
* tutoring
* language learning

Advantages:

* personalized lessons
* adaptive explanations
* interactive learning

Example uses:

* AI debate partner
* AI roleplay for language practice
* personalized quizzes

Some schools initially **banned ChatGPT**, but later reversed the bans.

---

# 2.3.5 Conversational Bots

Conversational AI is one of the **most visible AI applications**.

Examples:

**Consumer**

* chatbots
* AI companions
* therapy bots
* virtual characters

**Enterprise**

* customer support
* product assistants
* onboarding assistants

Benefits:

* faster response times
* reduced support costs
* improved customer experience

---

### Advanced conversational agents

New developments include:

* **voice assistants**

  * Siri
  * Alexa
  * Google Assistant

* **3D AI characters**

  * game NPCs
  * retail assistants
  * virtual brand representatives

AI can make **video game NPCs much more realistic and dynamic**.

---

# 2.3.6 Information Aggregation

People struggle with **information overload**.

AI helps by:

* summarizing documents
* extracting insights
* comparing research
* generating reports

Example applications:

* summarizing emails and Slack messages
* research summaries
* talk-to-your-docs systems

Example enterprise use:
AI summarizing meeting notes into:

* key facts
* open questions
* action items

These can automatically update **project management tools**.

---

# 2.3.7 Data Organization

A huge amount of data is **unstructured**:

* images
* videos
* PDFs
* contracts
* logs

AI helps by:

* extracting structured information
* labeling content
* enabling search

Examples:

Consumer:

* photo search in Google Photos
* image tagging

Enterprise:

* extracting info from receipts
* extracting data from contracts
* financial document processing

This industry is called **Intelligent Document Processing (IDP)**.

Expected growth:

* ~$12.8B market by 2030

---

# 2.3.8 Workflow Automation

AI can automate repetitive tasks.

Examples:

**Consumer**

* trip planning
* booking restaurants
* refund requests
* form filling

**Enterprise**

* lead generation
* invoice processing
* data entry
* reimbursements
* customer request handling

---

### AI Agents

Advanced automation requires **AI agents**.

Agents can:

* plan tasks
* call external tools
* execute multi-step workflows

Example workflow:

```
User request → plan steps → use tools → complete task
```

Example tasks:

* booking travel
* scheduling meetings
* searching the web
* updating databases

Agents could significantly **increase productivity**.

---

# Core Idea of This Section

Foundation models enable a **wide range of applications across industries**.

Most common categories:

1. Coding
2. Image/video generation
3. Writing
4. Education
5. Conversational bots
6. Information aggregation
7. Data organization
8. Workflow automation

Key insight:

AI is best at tasks involving:

* language
* digital content
* information processing

AI is weaker at tasks involving:

* physical skills
* complex real-world actions.

Here is the **same style structured summary** for the final section so it’s easy to review with the others.

---

# 3. Planning AI Applications

## 3.1 Why planning matters

Because foundation models are powerful, it’s easy to build **cool demos quickly**.

However:

* Building a **demo** is easy
* Building a **profitable product** is hard

Before building an AI application, companies should evaluate:

* why they need it
* whether they should build or buy it
* how success will be measured
* how the system will evolve over time

---

# 3.2 Use Case Evaluation

The first step is understanding **why the AI application should exist**.

Companies typically adopt AI for three reasons.

### 1. Existential risk (highest urgency)

If competitors use AI and you don’t, your business may become obsolete.

Examples of high-risk industries:

* financial analysis
* insurance
* document processing
* advertising
* web design

In these industries, AI adoption is necessary for **business survival**.

---

### 2. Profit and productivity opportunity

Most companies adopt AI to improve efficiency.

AI can help with:

* marketing copy
* customer support
* sales lead generation
* internal communication
* market research
* user personalization

Benefits include:

* lower costs
* higher productivity
* better user experience

---

### 3. Exploration (don’t fall behind)

Some companies experiment with AI even if they’re unsure how it fits.

Reason:
Companies that ignore new technologies often fail.

Examples of companies that missed technology shifts:

* Kodak
* Blockbuster
* BlackBerry

---

### Build vs Buy Decision

After identifying a use case, decide whether to:

**Build AI internally**

* more control
* better competitive advantage

**Buy existing solutions**

* faster
* cheaper
* less engineering effort

---

# 3.3 Role of AI in the Product

How AI fits into a product affects its **design and reliability requirements**.

Three key design dimensions:

---

## Critical vs Complementary

**Critical AI**
The product cannot function without AI.

Example:

* Face ID

These require:

* high accuracy
* strong reliability

---

**Complementary AI**
AI improves the product but isn’t essential.

Example:

* Gmail Smart Compose

Users tolerate more mistakes when AI is **nonessential**.

---

## Reactive vs Proactive

**Reactive AI**

Responds only when users ask.

Example:

* chatbots

Characteristics:

* requires fast responses
* user-initiated

---

**Proactive AI**

Suggests things without being asked.

Example:

* traffic alerts in maps

Characteristics:

* can be precomputed
* must be higher quality (users didn’t ask for it)

---

## Dynamic vs Static

**Dynamic systems**

Continuously update based on user behavior.

Example:

* personalized AI assistants
* recommendation systems

---

**Static systems**

Updated only when the model is updated.

Example:

* object detection in Google Photos

---

# 3.4 Role of Humans in AI Systems

Many AI systems include **human-in-the-loop** workflows.

Possible setups:

### AI-assisted humans

AI suggests responses, but humans decide.

Example:
Customer support agents using AI suggestions.

---

### AI handles simple tasks

AI answers easy questions, humans handle complex ones.

---

### Fully automated AI

AI handles everything without human intervention.

---

### Crawl–Walk–Run Automation Strategy

A common adoption model:

**Crawl**
Humans must review AI outputs.

**Walk**
AI interacts internally with employees.

**Run**
AI interacts directly with customers.

Automation increases as the system improves.

---

# 3.5 AI Product Defensibility

AI applications often have **low entry barriers**.

If you can build it easily, competitors can too.

Companies must create **defensible advantages (moats)**.

Three main AI advantages:

### 1. Technology

Unique algorithms or infrastructure.

Hard to maintain because many companies use the same models.

---

### 2. Data

Exclusive datasets can improve AI performance.

Startups can gain a data advantage if they:

* launch early
* collect user interactions
* improve models with feedback

---

### 3. Distribution

Ability to reach users.

Big companies have an advantage here.

Examples:

* Google
* Microsoft
* Apple

---

Even small startups can succeed if they:

* move fast
* focus on a specific niche

Examples of small startups beating big companies:

* Calendly
* Mailchimp
* Photoroom

---

# 3.6 Setting Expectations

Once the decision to build is made, define **success metrics**.

Example: customer support chatbot metrics

Business metrics:

* % of tickets automated
* faster response times
* reduced support cost
* higher throughput

---

### Important technical metrics

#### Quality metrics

Measure accuracy and usefulness of responses.

---

#### Latency metrics

Important metrics include:

* **TTFT** – time to first token
* **TPOT** – time per output token
* **Total latency**

Acceptable latency depends on the use case.

Example:
If humans respond in 1 hour, even a 30-second AI response is good.

---

#### Cost metrics

Cost per inference request.

---

#### Other metrics

* fairness
* interpretability
* reliability

---

# 3.7 Milestone Planning

After defining metrics, plan how to achieve them.

Steps:

1. Evaluate existing models
2. Estimate how much improvement is needed
3. Determine required effort

Example:

Goal:
Automate **60% of support tickets**

If base model already handles **30%**, development becomes easier.

---

### The “Last Mile Problem”

AI demos often look impressive quickly.

But improvement slows dramatically later.

Example findings:

* first **60–80% performance** is relatively easy
* improving from **80% → 95%** can take months

This happens due to:

* edge cases
* hallucinations
* reliability issues

---

# 3.8 Maintenance

AI systems require continuous maintenance.

Reasons:

### Rapid technology changes

Models constantly improve:

* better accuracy
* longer context windows
* cheaper inference

But switching models can break systems.

---

### Changing regulations

AI laws can affect:

* data usage
* compute availability
* intellectual property

Example:
GDPR compliance cost companies billions.

---

### Infrastructure risks

Dependencies can change suddenly.

Examples:

* GPU supply restrictions
* model providers shutting down
* API changes

---

# 3.9 The AI Engineering Stack

AI applications consist of **three layers**.

---

## 1. Application Development (top layer)

Focuses on building the product.

Key tasks:

* prompt engineering
* evaluation
* user interface design

This layer has grown **the fastest** since ChatGPT.

---

## 2. Model Development

Tools for building and adapting models.

Responsibilities:

* training
* finetuning
* dataset engineering
* inference optimization

Examples of tools:

* PyTorch
* TensorFlow
* Hugging Face

---

## 3. Infrastructure (bottom layer)

Provides system resources.

Responsibilities:

* model serving
* compute management
* data storage
* monitoring

---

# 3.10 AI Engineering vs Traditional ML Engineering

Building with foundation models changes the workflow.

### Traditional ML Engineering

Steps:

1. collect data
2. train model
3. build product

Model development is the main challenge.

---

### AI Engineering

Steps:

1. build product first
2. use existing models
3. adapt models if necessary

The focus shifts from **training models** to **adapting models**.

---

## Key differences

### 1. Model training

Traditional ML:
Train models from scratch.

AI engineering:
Use pretrained models.

---

### 2. Compute requirements

Foundation models:

* larger
* slower
* more expensive

This makes **inference optimization critical**.

---

### 3. Evaluation difficulty

Traditional ML outputs:

* fixed answers

Example:
spam / not spam

LLMs outputs:

* open-ended

This makes evaluation **much harder**.

---

# 3.11 Model Adaptation Methods

There are two main ways to adapt foundation models.

---

### Prompt-based techniques

Do not change model weights.

Examples:

* prompt engineering
* context construction

Advantages:

* easy
* requires little data

Limitations:

* less powerful for complex tasks

---

### Finetuning

Updates model weights.

Advantages:

* higher performance
* task specialization

Requirements:

* more data
* more compute

---

# 3.12 Application Development Components

Three main parts of AI application development.

---

## Evaluation

Evaluation is critical for:

* model selection
* benchmarking
* deployment readiness
* monitoring in production

Because LLMs generate open-ended responses, evaluation is harder.

---

## Prompt Engineering

Design prompts that guide model behavior.

Includes:

* instructions
* examples
* context
* memory management

Good prompts can dramatically improve performance.

---

## AI Interfaces

Interfaces through which users interact with AI.

Examples:

* web apps
* mobile apps
* browser extensions
* chatbots
* voice assistants

Popular integrations include:

* Slack bots
* Discord bots
* VSCode plugins
* browser assistants

---

# 3.13 AI Engineering vs Full-Stack Engineering

AI engineering is increasingly similar to **full-stack development**.

Reasons:

* strong focus on product interfaces
* rapid prototyping
* fast iteration cycles

Many AI engineers now come from:

* web development
* full-stack engineering

---

### New development workflow

Traditional ML workflow:

```
data → model → product
```

AI engineering workflow:

```
product → experiment → improve model
```

Developers can build **products first**, then optimize models later.

---

# Core Idea of This Section

Building AI applications requires more than using powerful models.

Successful AI products require:

* strong use case evaluation
* careful planning
* human-AI collaboration
* continuous evaluation and maintenance

The biggest shift from traditional ML:

**AI engineering focuses more on adapting models and building products than training models from scratch.**
