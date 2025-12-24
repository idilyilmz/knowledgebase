# (3) Identifying Bias in AI

https://www.kaggle.com/code/alexisbcook/identifying-bias-in-ai

## 1. Introduction
- machine learning can improve lives but can also cause harm, especially when systems discriminate against certain groups (e.g., by race, gender, religion, or socioeconomic status)
- this tutorial introduces **bias in ML**, defined as harmful or unfair outcomes (particularly those that disproportionately affect specific groups) and prepares learners to identify bias in real-world scenarios

## 2. Bias is complex
- bias is not limited to “bad data in, bad outcomes out.” While biased data can cause harm, bias can also arise from:
    - how data is collected or measured
    - how models are designed
    - how models are evaluated
    - how results are interpreted and used
- bias can appear at **any stage of the ML lifecycle**, and multiple types of bias can exist simultaneously

## 3. Six types of bias
- understanding different types of bias provides a shared vocabulary and helps practitioners detect and reduce unfairness in ML systems
- the tutorial follows a 2020 research paper that identifies **six key types of bias**

### a. Type 1 - Historical Bias
- historical bias occurs when the real-world context that generated the data is itself unfair
- models trained on such data learn and perpetuate existing inequalities, even if sensitive attributes are removed
- **example**: using past hiring data to train an AI hiring system can reinforce gender discrimination because historical hiring practices were biased

### b. Type 2 - Representation Bias
- representation bias happens when training data does not adequately represent the population the model will serve, leading to poor performance for underrepresented groups
- **example**: data collected from smartphone apps underrepresents older adults, making AI-driven city planning systems inaccessible to them

### c. Type 3 - Measurement Bias
- measurement bias arises when data quality or accuracy differs across groups, often due to flawed proxy variables
- **example**: using healthcare cost as a proxy for patient risk disadvantages Black patients, who may have lower costs due to systemic barriers rather than better health

### d. Type 4 - Aggregation Bias
- aggregation bias occurs when distinct groups are inappropriately combined into a single model, causing poor performance for some or all groups: often harming minority groups.
- **example**: a diabetes model that ignores ethnic differences may fail to detect higher risks in Hispanic populations

### e. Type 5 - Evaluation Bias
- evaluation bias occurs when benchmark or test datasets do not reflect the real population the model will serve, giving a false impression of model performance
- **example**: facial recognition systems performed well on benchmarks dominated by lighter-skinned individuals but failed more often on people of color

### f. Type 6 - Deployment Bias
- deployment bias happens when a model is used in a way that differs from its original purpose, leading to harmful or misleading outcomes
- **example**: risk prediction tools designed for post-conviction analysis are misused during sentencing decisions

## 4. Key takeaways
- bias can occur **throughout the ML pipeline**
- bias types are **not mutually exclusive**
- a single system can suffer from multiple biases at once
- recognizing bias is the first step toward mitigation