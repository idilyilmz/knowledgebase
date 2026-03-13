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

