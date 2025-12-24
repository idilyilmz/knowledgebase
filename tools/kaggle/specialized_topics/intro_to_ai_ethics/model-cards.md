# (5) Model Cards

https://www.kaggle.com/code/var0101/model-cards

## 1. Introduction
- a model card is a short document that explains key details about a machine learning model
- its purpose is to improve transparency and accountability by clearly communicating how a model works, what it is intended for, and how it performs
- this tutorial explains who model cards are for and what sections they should include, followed by practical application examples

## 2. Model cards
- as AI systems become more widespread, many people affected by them do not understand how they work
- model cards, introduced in a **2019 research paper**, provide a standardized way to communicate essential model information to a broad audience, including users, researchers, and policymakers
- **key idea**: model cards are like **nutrition labels for ML models**, they summarize what’s inside, how it behaves, and where it may fall short

## 3. Examples of model cards
- real-world model cards help illustrate best practices
- examples include:
    - salesforce model cards
    - OpenAI’s GPT-3 model card
    - Google Cloud example model cards
- these examples show how organizations adapt the format to their needs

## 4. Audience of a Model Card
- model cards should balance **accessibility** and **technical depth**
- the intended audience depends on the model’s purpose
- **possible audiences include**:
    1. end users
    2. people affected by the model
    3. domain experts (e.g., doctors)
    4. researchers
    5. policymakers
    6. developers of similar systems
- **example**: a medical imaging model card may assume some knowledge of healthcare and AI because it will be read by clinicians and researchers.

## 5. Sections of a Model Card
- according to the original paper, model cards typically contain **nine sections** (organizations may adapt these)

### Section 1 - Model Details
- provides basic background information such as:
    - model name
    - version
    - developer or organization

### Section 2 - Intended Use
- clarifies:
    - in-scope use cases
    - intended users
    - out-of-scope or discouraged uses

### Section 3 - Factors
- describes variables that affect model performance, such as:
    - demographics (age, gender, ethnicity)
    - environmental conditions (lighting, weather)
    - hardware or instrumentation (camera type)

### Section 4 - Metrics
- explains:
    - which performance metrics are used
    - why those metrics were chosen
- **examples**:
    - classification metrics: false positives, false negatives, etc.
    - score-based outputs: performance comparisons across groups

### Section 5 - Evaluation Data
- details:
    - datasets used for evaluation
    - reasons for choosing them
    - how well they represent real-world and edge cases

### Section 6 - Training Data
- describes:
    - the data used to train the model
    - its source and scope (when possible)

### Section 7 - Quantitative Analyses
- reports:
    - model performance on selected metrics
    - performance breakdowns across key factors and group intersections

### Section 8 - Ethical Considerations
- discusses:
    - use of sensitive data
    - potential impacts on safety, health, or human rights
    - identified risks and mitigation strategies
    - known or possible harms

### Section 9 - Caveats and Recommentations
- includes:
    - important limitations
    - warnings
    - guidance for responsible use
    - information not covered elsewhere

## 6. How can you use model cards in your organization?
- organizations may hesitate to share details due to **privacy, proprietary data, or trade secrets**
- teams should still aim to make model cards useful without revealing sensitive information
- some organizations use alternative formats (e.g., **FactSheets**) to document and track model information internally.

## 7. Key takeaways
- model cards promote **transparency**, **trust**, and **accountability**
- they help diverse audiences understand model behavior and limitations
- a standardized structure supports responsible AI deployment
- model cards can be adapted to organizational constraints