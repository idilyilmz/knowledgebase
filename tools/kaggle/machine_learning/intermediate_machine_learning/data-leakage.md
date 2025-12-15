# (7) Data Leakage

https://www.kaggle.com/code/alexisbcook/data-leakage

## 1. Introduction
- **data leakage** occurs when training data contains information that wouldn't be available at prediction time
- this leads to models that perform extremely well during training or validation but fail badly in real-world use
- leakage is dangerous because it is often subte and hard to detect
- there are two main types
    - **target leakage**: using information created after the target outcome occurs
    - **train-rest contamination**: allowing validation data to influence training or preprocessing

## 2. Example
- a credit card approval dataset initially showed very high cross-validation accuracy (~98%), which raised suspicion
- some features (like, **expenditure**, **share**) were strongly linked to whether a credit card was approved, but were likely recorded *after* approval
- data exploration confirmed that nearly all rejected applicants had zero expenditure, indicating **target leakage**
- after removing leaky features and retraining the model, accuracy dropped to ~83%
- although lower, this score is far more realistic and reliable for real-world predictions

## 3. Conclusion
- data leakage can lead to severely misleading model performance and costly real-world mistakes
- to prevent leakage: 
    - exclude features that depend on future information
    - keep training and validation data strictly seperate
    - use **pipelines** to ensure preprocessing doesn't leak information
- careful data inspection, domain knowledge and cautious feature selection are essential for building trustworthy models