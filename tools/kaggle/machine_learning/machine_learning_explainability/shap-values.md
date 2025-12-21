# (4) SHAP Values

https://www.kaggle.com/code/dansbecker/shap-values

## 1. Introduction
- SHAP values explain individual predictions by showing how each feature contributes to the final model output. While feature importance and partial dependence provide global insights, SHAP focuses on why a specific prediction was made.
- common use cases include:
    - explaining loan denials when legal justification is required
    - identifying patient-specific risk factors in healthcare
    - providing transparent, feature-level explanations for model decisions
- SHAP stands for **SH**apley **A**dditive ex**P**lanations, based on concepts from game theory.

## 2. How They Work
- SHAP values measure how much each feature contributes to a prediction **relative to a baseline value**.
- Key idea:
    - Compare the model’s prediction for a specific data point to a baseline prediction
    - Attribute the difference to individual features.
- SHAP values satisfy the property:

**Sum of SHAP values = Prediction − Baseline prediction**

- Interpretation:
    - Positive (pink) values increase the prediction.
    - Negative (blue) values decrease the prediction.
    - The magnitude shows the strength of each feature’s impact.
- This guarantees that all feature contributions add up exactly to explain why the prediction differs from the baseline

## 3. Code to Calculate SHAP Values
- SHAP values are computed using the **shap** library
- for tree-based models, `TreeExplainer` provides fast, exact SHAP values
- SHAP values are calculated for individual rows to explain single predictions
- visualizations such as **force plots** clearly show how each feature pushes the prediction higher or lower

### a. SHAP Explainers:
- **TreeExplainer**: Fast and exact for tree-based models
- **DeepExplainer**: For deep learning models
- **KernelExplainer**: Model-agnostic, slower, and approximate

## 4. Key Takeaway
SHAP values provide precise, consistent, and interpretable explanations for individual predictions, making them especially valuable in high-stakes and regulated applications where transparency is critical