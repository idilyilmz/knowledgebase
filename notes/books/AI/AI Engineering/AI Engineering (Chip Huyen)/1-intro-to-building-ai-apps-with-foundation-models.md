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

# Core Idea of the Chapter

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
