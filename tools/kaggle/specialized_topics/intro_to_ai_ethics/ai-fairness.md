# (4) AI Fairness

https://www.kaggle.com/code/alexisbcook/ai-fairness

## 1. Introduction
- fairness in machine learning does not have a single definition
- different situations call for different fairness criteria
- for example, a credit approval model could be considered fair if approval rates are equal across genders, or if gender is completely removed from the data
- this tutorial introduces **four common fairness criteria** and shows how to analyze them in practice using trained models

## 2. Four Fairness Criteria
- these criteria apply to models that **select people for outcomes** (e.g., loans, jobs, admissions) - no single criterion is universally correct, and many others exist beyond these four

### a. Criteria 1 - Demographic parity / statistical parity
- a model satisfies demographic parity if the **proportion of selected individuals** matches the group proportions in the overall population
- **key idea**: equal selection rates across groups
- **example**: if 50% of applicants are women, then 50% of selected conference speakers should be women
- **limitation**: does not consider whether individuals were actually qualified

### b. Criteria 2 - Equal opportunity
- a model satisfies equal opportunity if the **true positive rate (TPR)** is the same across groups
- this means qualified individuals have an equal chance of being correctly selected, regardless of group membership
- **key idea**: equal chance of success for those who deserve the outcome
- **example**: a medical risk model identifies high-risk patients equally well across demographic groups

### c. Criteria 3 - Equal accuracy
- a model satisfies equal accuracy if it has the **same overall accuracy** across groups, meaning it makes correct decisions at the same rate for everyone
- **key idea**: equal correctness across groups
- **example**: a loan approval model is 98% accurate for all demographic groups

### d. Criteria 4 - Group unaware / "Fairness through unawareness"
- this approach removes **group membership information** (e.g., race, gender, age) from the dataset so the model cannot explicitly use it
- **key idea**: The model does not “see” group identity
- **challenges**:
    - proxy variables (e.g., zip code as a proxy for race) must also be removed
    - ineffective for addressing historical bias
    - cannot be evaluated using confusion matrices

## 3. Example Using Confusion Matrices
- confusion matrices help visualize model performance and compare fairness across groups
    - **demographic parity**: Equal number of selected individuals from each group
    - **equal opportunity**: Equal true positive rates across groups
    - **equal accuracy**: Equal accuracy across groups
    - **group unaware**: Not observable in confusion matrices
- each fairness criterion produces **different confusion matrices**

## 4. Tradeoffs and Limitations
- a model generally **cannot satisfy more than one fairness criterion at the same time**
- this is formalized in the **Impossibility Theorem of Machine Fairness**
- choosing a fairness definition requires careful discussion and depends on the context
- real-world models rarely achieve perfect fairness; “close enough” is often the practical goal

## 5. Key Takeaways
- fairness has **multiple, conflicting definitions**
- the “right” fairness metric depends on values, context, and stakeholders
- fairness decisions should involve the **entire team**, not just engineers
- confusion matrices remain useful tools for fairness analysis at scale