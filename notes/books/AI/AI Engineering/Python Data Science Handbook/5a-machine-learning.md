# Chapter 5 — Machine Learning (Python Data Science Handbook) — Study Notes
*(Covers everything up to "In-Depth: Decision Trees and Random Forests" — that section is intentionally left out for now.)*

---

## 1. What Is Machine Learning?

**Definition:** ML = building mathematical models to understand data, where "learning" = giving models tunable parameters that adapt to observed data.

### Two main categories
| Type | Description | Subtypes |
|---|---|---|
| **Supervised learning** | Models the relationship between measured **features** and a **label**; once determined, applies labels to new data. | **Classification** (discrete labels) & **Regression** (continuous labels) |
| **Unsupervised learning** | Models the features of data **without reference to any label** ("letting the dataset speak for itself"). | **Clustering** (find groups) & **Dimensionality reduction** (find compact representation) |
| **Semi-supervised learning** | Falls between the two — useful when only **incomplete labels** are available. | — |

### Qualitative examples (know these definitions!)
- **Classification:** predicting discrete labels. Model = e.g. a line separating two classes. Training = finding parameter values from data; applying the model to new data = **prediction**. Example: spam detection.
- **Regression:** predicting continuous labels. E.g. fitting a plane to 3D data (2 features + 1 continuous label). Example: **photometric redshift** problem in astronomy (predict galaxy distance from brightness features).
- **Clustering:** unsupervised, assigns data to discrete groups based on intrinsic structure. Example: **k-means** — fits **k cluster centers**, minimizing distance of each point to its assigned center.
- **Dimensionality reduction:** unsupervised, pulls out a lower-dimensional representation that preserves relevant structure. Example: **Isomap** (a manifold learning algorithm) unrolling a spiral into 1D.

### Summary table (potential MC fill-in-the-blank)
- Supervised learning → predicts labels from labeled training data
- Classification → predicts labels as discrete categories
- Regression → predicts continuous labels
- Unsupervised learning → identifies structure in unlabeled data
- Clustering → detects distinct groups
- Dimensionality reduction → detects lower-dimensional structure

---

## 2. Introducing Scikit-Learn

### Data representation
- Data thought of as a **table**: rows = **samples** (`n_samples`), columns = **features** (`n_features`).
- **Features matrix `X`**: 2D, shape `[n_samples, n_features]` — usually a NumPy array or Pandas DataFrame.
- **Target array `y`**: usually 1D, length `n_samples` — the **dependent variable** (what you want to predict). Can hold continuous or discrete values.
- Classic example dataset: the **Iris dataset** (Ronald Fisher, 1936) — 150 samples, 4 features (sepal/petal length & width), target = species.

### Scikit-Learn API design principles
1. **Consistency** — common interface, consistent docs
2. **Inspection** — parameters exposed as public attributes
3. **Limited object hierarchy** — only algorithms are classes; data uses standard formats
4. **Composition** — complex tasks = sequences of simpler algorithms
5. **Sensible defaults**

### The 5-step Estimator API recipe (MEMORIZE — very testable)
1. Choose a **class of model** (import estimator)
2. Choose **model hyperparameters** (set at instantiation, *before* fitting)
3. Arrange data into features matrix `X` and target array `y`
4. **Fit** the model to data: `model.fit(X, y)`
5. **Apply** to new data: `model.predict()` (supervised) or `model.transform()`/`predict()` (unsupervised)

**Key facts:**
- **Hyperparameters** = parameters set before fitting (chosen at instantiation), e.g. `fit_intercept`.
- After `fit()`, learned parameters are stored with a **trailing underscore** (e.g. `model.coef_`, `model.intercept_`).
- Instantiating a model only stores hyperparameters — it does **not** touch any data yet.
- **`train_test_split`** splits data into training/testing sets.
- **`accuracy_score`** = fraction of correctly predicted labels.

### Worked examples recap
- **Simple linear regression** — `LinearRegression`, learns `coef_` (slope) and `intercept_`.
- **Iris classification** — used **Gaussian naive Bayes** (`GaussianNB`), no hyperparameters, good simple baseline; achieved ~97% accuracy on a train/test split.
- **Iris dimensionality reduction** — used **PCA** (`n_components=2`) to visualize the 4D iris data in 2D; note `y` (target) is **not** used when fitting PCA (unsupervised!).
- **Iris clustering** — used a **Gaussian Mixture Model (GMM)**, models data as a collection of Gaussian blobs; recovered species clusters without ever seeing the labels.
- **Handwritten digits application:**
  - Data: 1,797 samples, 8×8 pixel images → flattened to 64 features.
  - Used **Isomap** to reduce to 2D for visualization.
  - Used **Gaussian naive Bayes** for classification → ~80% accuracy.
  - **Confusion matrix**: shows which classes get mixed up (e.g., 2's misclassified as 1's or 8's).

---

## 3. Hyperparameters and Model Validation

### Model validation — the WRONG way
- Training and evaluating on the **same data** → misleadingly high (even 100%) accuracy. Example: 1-nearest-neighbor classifier gets 100% on training data trivially, because it just memorizes points.

### The RIGHT ways
| Method | How it works | Downside |
|---|---|---|
| **Holdout set** | Split data into train/test once (`train_test_split`) | Loses a chunk of data from training |
| **Cross-validation** | Multiple train/validate splits, using different folds each time, then combine (e.g. average) the scores | More compute, but uses all data |
| **k-fold cross-validation** | Data split into *k* groups; each is used once as validation, trained on remaining k-1 | e.g. 2-fold, 5-fold |
| **Leave-one-out CV** | Extreme case: number of folds = number of data points (train on all but one each time) | Very expensive for large datasets |

`cross_val_score(model, X, y, cv=5)` → returns an array of scores, one per fold.

### The Bias–Variance trade-off (HIGH-YIELD for MC!)
| Concept | Description | Symptom |
|---|---|---|
| **Underfitting** | Model too simple/not flexible enough (e.g. straight line on curved data) | = **high bias** |
| **Overfitting** | Model too flexible, fits noise instead of signal | = **high variance** |

- **High-bias models:** performance on validation set ≈ performance on training set (both mediocre).
- **High-variance models:** performance on validation set is **much worse** than on training set (training score very high, validation score low).
- **R² score (coefficient of determination):** R²=1 → perfect match; R²=0 → model does no better than the mean; negative → worse than the mean.

### Validation curves
- Plots **training score** vs. **validation score** as a function of **model complexity** (e.g. polynomial degree).
- Training score is *always* ≥ validation score.
- Low complexity → both scores low (underfitting/high bias).
- High complexity → training score high, validation score drops (overfitting/high variance).
- The complexity at the **peak of the validation curve** = the sweet spot / best bias-variance trade-off.

### Learning curves
- Plots training/validation score as a function of **training set size** (not model complexity).
- General behavior:
  - Small dataset + fixed complexity → model **overfits**: high training score, low validation score.
  - Large dataset + fixed complexity → model **underfits** more: training score decreases, validation score increases.
  - Curves converge but (except by chance) **training score never falls below validation score.**
- **Key insight:** Once a learning curve has **converged** (training and validation curves are close), **adding more training data will NOT help.** The only way to improve further is to use a **more complex model.**

### Grid search
- `GridSearchCV` automates searching over a **grid of hyperparameter combinations**, evaluating each via cross-validation, and reports `best_params_` / `best_estimator_`.
- Used when there is more than one hyperparameter "knob" to tune simultaneously.

### If a model underperforms, possible fixes:
- Use a more complicated/flexible model
- Use a simpler/less flexible model
- Gather more training samples
- Gather more features
> **Important nuance:** more data or a more complex model does NOT always help — it depends on whether you're dealing with high bias or high variance!

---

## 4. Feature Engineering

Feature engineering = turning arbitrary/raw information into numeric features (a.k.a. **vectorization**).

### Categorical features
- Don't map categories to arbitrary integers (implies false ordering, e.g. "Wallingford - Queen Anne = Fremont" makes no sense).
- Use **one-hot encoding**: creates one binary (0/1) column per category.
- Scikit-Learn tool: `DictVectorizer` (also `OneHotEncoder`, `FeatureHasher`).
- Downside: many categories → much larger (but sparse) dataset.

### Text features
- **Word counts**: `CountVectorizer` — counts occurrences of each word.
- Problem: raw counts overweight frequent (but often uninformative) words.
- **TF–IDF (term frequency–inverse document frequency)**: `TfidfVectorizer` — weights word counts by how often they appear across documents, downweighting very common words.

### Image features
- Simplest approach: use raw **pixel values** as features (as with the digits example).
- More advanced techniques found in Scikit-Image.

### Derived features
- Features **mathematically derived** from input features, e.g. **polynomial features** (`PolynomialFeatures`) — turning a linear regression into a polynomial regression by transforming the *input*, not changing the model.
- Also called **basis function regression** — motivates **kernel methods** (used later in SVMs).

### Imputation of missing data
- Missing values (`NaN`) must be filled in (**imputed**) before fitting most models.
- Simple approach: replace with **mean/median/most frequent value** of the column — Scikit-Learn's `Imputer` class.
- Sophisticated approaches: matrix completion, robust models (application-specific).

### Feature pipelines
- `make_pipeline()` chains multiple steps (e.g. impute → transform to polynomial → fit linear regression) into a single object that behaves like a normal estimator (`fit`/`predict`).

---

## 5. In Depth: Naive Bayes Classification

- **Naive Bayes** = fast, simple classification algorithms, good for **high-dimensional data**, often used as a **quick baseline**.
- Built on **Bayes's theorem**: relates the probability of a label given features, `P(label | features)`, to quantities we can compute more directly.
- Requires a **generative model**: specifies the hypothetical random process that generates data for each label. The **"naive"** part = making simplifying (naive) assumptions about this generative model.

### Gaussian Naive Bayes
- Assumes data for each label is drawn from a simple **Gaussian (normal) distribution** with **no covariance between dimensions**.
- Fit by finding the **mean and standard deviation** of points within each label.
- Decision boundary in Gaussian NB is generally **quadratic** (curved).
- Supports **probabilistic classification** via `predict_proba()`.

### Multinomial Naive Bayes
- Assumes features are generated from a **multinomial distribution** — appropriate for **count-based features** (e.g. word counts).
- Classic use case: **text classification** (e.g. the 20 Newsgroups example — classifying documents using TF-IDF + `MultinomialNB` in a pipeline).
- Confusion often occurs between **semantically related categories** (e.g. religion vs. Christianity topics).

### When to use Naive Bayes — advantages
- Extremely **fast** for training and prediction
- Provides **straightforward probabilistic prediction**
- Often **very interpretable**
- **Very few tunable parameters**

### Naive Bayes performs especially well when:
1. The naive assumptions actually match the data (rare in practice)
2. Categories are **very well separated** (model complexity less important)
3. Data is **very high-dimensional** (model complexity less important)

**Why high dimensions help:** in high dimensions, points must be close in *every* dimension to be considered close overall, so clusters tend to be more separated — simple models like NB can perform as well as complex ones once you have enough data.

---

## 6. In Depth: Linear Regression

### Simple linear regression
- Straight-line fit: `y = ax + b` — `a` = **slope**, `b` = **intercept**.
- Scikit-Learn: `LinearRegression`. Learned params: `model.coef_` (slope(s)), `model.intercept_`.
- Generalizes to **multidimensional** linear models: `y = a₀ + a₁x₁ + a₂x₂ + ...` — geometrically fitting a plane/hyperplane.

### Basis function regression
- Trick to fit **nonlinear relationships** with a linear model: transform inputs via **basis functions** before fitting.
- If the basis functions are polynomials (`x, x², x³, ...`) → **polynomial regression**. Still technically a "linear model" because the *coefficients* are combined linearly (they never multiply each other).
- Implemented in Scikit-Learn via `PolynomialFeatures` (+ pipeline).
- **Gaussian basis functions** are another option (not built-in, need a custom transformer) — sum of Gaussian "bumps" fit to the data.

### Regularization (HIGH-YIELD)
Basis functions add flexibility → risk of **overfitting** (huge/oscillating coefficients, especially where basis functions overlap). **Regularization** penalizes large coefficient values.

| Type | Aka | Penalty | Effect | Scikit-Learn class |
|---|---|---|---|---|
| **Ridge regression** | L2 regularization / Tikhonov regularization | Sum of **squares** of coefficients | Shrinks coefficients smoothly; α→0 recovers standard linear regression, α→∞ suppresses all coefficients | `Ridge` |
| **Lasso regularization** | L1 regularization | Sum of **absolute values** of coefficients | Tends to produce **sparse models** — sets many coefficients to exactly **zero** | `Lasso` |

- Both have a tunable strength parameter (`alpha`), best chosen via **cross-validation**.
- **Ridge (L2)** = smooth shrinkage; **Lasso (L1)** = feature selection via sparsity — this contrast is a classic exam distinction.

### Example application mentioned
- **Predicting Bicycle Traffic** — a real-world case study applying linear regression with multiple features (weather, day of week, etc.) — used to illustrate that a simple linear model may still be "missing relevant information."

---

## 7. In-Depth: Support Vector Machines (SVM)

- SVMs = powerful, flexible **supervised** algorithms for both classification and regression.
- This is an example of **discriminative classification** (finds a dividing line/curve/manifold) as opposed to **generative classification** (like Naive Bayes, which models each class's distribution).

### Maximizing the margin
- Problem: many possible lines can perfectly separate two classes — which is best?
- SVM idea: draw a **margin** around the dividing line, up to the nearest point(s), and choose the line that **maximizes this margin**.
- SVMs are called **maximum margin estimators**.
- The points that touch/define the margin = **support vectors** (gives the algorithm its name) — stored in `model.support_vectors_`.
- **Key property:** only the position of the support vectors affects the fit — points farther from the margin (on the correct side) do NOT affect the model at all, even if more of them are added.

### Kernel SVM (nonlinear boundaries)
- For data that is **not linearly separable** (e.g. concentric circles), project into a higher dimension using a **kernel transformation** (basis function based on similarity/"kernel" between point pairs) so that a linear separator becomes possible.
- Doing this for every point would be computationally expensive — solved via the **kernel trick**: fits kernel-transformed data **implicitly**, without ever explicitly building the high-dimensional representation.
- Common kernel: **RBF (radial basis function)** kernel — set via `kernel='rbf'` in `SVC`.

### Softening the margin (the `C` parameter)
- Real data often overlaps between classes — SVM allows a **soft margin**, letting some points creep into the margin.
- Controlled by parameter **`C`**:
  - **Large `C`** → **hard margin** (little/no tolerance for points inside the margin)
  - **Small `C`** → **soft margin** (more tolerance, margin can grow to include more points)
- Optimal `C` should be tuned via cross-validation.

### Example: Face Recognition
- Used the **Labeled Faces in the Wild** dataset.
- Pipeline: **PCA** (dimensionality reduction, e.g. to 150 components) → **SVC** (`kernel='rbf'`).
- Hyperparameters tuned via **grid search**: `C` (margin hardness) and `gamma` (RBF kernel size/width).
- Evaluated with **classification report** (precision/recall/f1-score per class) and **confusion matrix**.

### SVM Summary — Advantages
- Compact models (depend on relatively few support vectors) → low memory
- Fast prediction once trained
- Work well in **high-dimensional data**, even when there are more dimensions than samples
- Versatile via kernel methods — adapt to many data types

### SVM Summary — Disadvantages
- Scaling with number of samples `N` is poor (worst case ~O(N³), or O(N²) for efficient implementations) → expensive for large datasets
- Results depend heavily on a well-chosen softening parameter `C` — must be cross-validated (costly)
- No direct probabilistic interpretation (can be estimated via internal cross-validation, but that's costly too)
- **Rule of thumb from the author:** use SVMs only after simpler/faster methods have proven insufficient.

---

## Quick-Fire Definitions Table (fast review before the test)

| Term | One-line definition |
|---|---|
| Features matrix (X) | 2D array, shape [n_samples, n_features] |
| Target array (y) | 1D array of labels/values to predict (the dependent variable) |
| Hyperparameter | A parameter set **before** fitting (at model instantiation) |
| `fit()` / `predict()` / `transform()` | Train the model / predict labels (supervised) / infer or reduce structure (unsupervised) |
| Holdout set | Data reserved from training, used only for evaluation |
| Cross-validation | Repeated train/validate splits across different folds |
| Underfitting / high bias | Model too simple; poor fit on both train & validation |
| Overfitting / high variance | Model too flexible; great fit on train, poor on validation |
| Validation curve | Score vs. model complexity |
| Learning curve | Score vs. training set size; converges — more data ≠ always better |
| Grid search | Automated search over combinations of hyperparameters |
| One-hot encoding | Binary column per category, avoids false numeric ordering |
| TF–IDF | Weights word counts by how distinctive they are across documents |
| Naive Bayes | Fast generative classifier; "naive" = features assumed (conditionally) independent given the label |
| Gaussian NB | Assumes Gaussian-distributed features per class; quadratic boundary |
| Multinomial NB | Assumes multinomial (count-based) distribution; used for text |
| Ridge (L2) regularization | Penalizes sum of squared coefficients; shrinks smoothly |
| Lasso (L1) regularization | Penalizes sum of absolute coefficients; produces sparse (zeroed-out) models |
| Support vector | A training point that lies exactly on the margin; defines the SVM decision boundary |
| Maximum margin | The SVM's optimal separating boundary maximizes distance to nearest points |
| Kernel trick | Implicitly computes high-dimensional kernel transformations without building them explicitly |
| C parameter (SVM) | Controls margin hardness: large C = hard margin, small C = soft margin |

---
*Note: "In-Depth: Decision Trees and Random Forests" and everything after it was intentionally skipped, as requested.*