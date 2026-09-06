# Chapter 1 — What Is Deep Learning? (Study Notes)

## 1. AI vs. Machine Learning vs. Deep Learning
Nested relationship: **AI ⊃ ML ⊃ DL**

| Term | Definition | Era it took off |
|---|---|---|
| **AI** | Effort to automate intellectual tasks normally done by humans. Includes approaches with NO learning at all (e.g. hardcoded chess rules). | Born 1950s |
| **Symbolic AI** | Programmers handcraft explicit rules to manipulate knowledge in databases. Good for well-defined logical problems (chess), bad for fuzzy problems (image/speech). | Dominant 1950s–late 1980s, peaked in the 1980s "expert systems boom" |
| **Machine Learning (ML)** | System is *trained*, not explicitly programmed. Finds statistical rules from examples. | Started to flourish in the **1990s** |
| **Deep Learning (DL)** | Subfield of ML. Learns **successive layers** of increasingly meaningful representations via neural networks. | Recent decade(s) |

**Key exam trap:** "Deep" does NOT mean "deeper understanding" — it refers to the number of **layers** (the *depth* of the model).

### Key historical facts / names (classic MC bait)
- **1956** — John McCarthy organizes the **Dartmouth workshop**; "AI" crystallizes as a field.
- **Ada Lovelace** — worked with Charles Babbage on the **Analytical Engine** (1830s–40s). Her 1843 remark ("It can do whatever we know how to order it to perform...") = **"Lady Lovelace's objection."**
- **Blaise Pascal** — built the **Pascaline** in 1642 (age 19), first mechanical calculator.
- **Alan Turing** — 1950 paper *"Computing Machinery and Intelligence"* introduced the **Turing test** and quoted Lady Lovelace's objection.

---

## 2. Classical Programming vs. Machine Learning (Fig 1.2)
- **Classical programming:** Rules + Data → Answers
- **Machine learning:** Data + Answers → Rules

ML is related to statistics but differs because it handles **large, complex datasets** where classical statistical methods (e.g. Bayesian analysis) are impractical. ML is described as **fundamentally an engineering discipline**, hands-on and empirical (not much theory).

## 3. Three Things Needed to Do Machine Learning
1. **Input data points**
2. **Examples of the expected output**
3. **A way to measure whether the algorithm is doing a good job** (feedback signal → this measurement/adjustment step = **"learning"**)

## 4. Representations & Hypothesis Space
- A **representation** = a different way to encode/look at data (e.g. RGB vs. HSV for images).
- ML = searching for a **useful representation** + simple rule that solves the task.
- **Hypothesis space** = the predefined set of possible transformations the algorithm searches through (e.g., "all possible coordinate changes").
- ML algorithms are **not creative** — they only search within this predefined space.
- Example in the book: classifying black/white points via a **coordinate change** so the rule becomes simple ("black if x > 0").

**Definition to memorize:** *Learning* = an automatic search process for data transformations that produce useful representations, guided by a feedback signal.

## 5. The "Deep" in Deep Learning
- Learned via **neural networks**, structured in literal stacked layers.
- **Depth** = number of layers in the model.
- **Shallow learning** = other ML approaches using only 1–2 layers of representation (e.g. pixel histogram + classification rule).
- **Important myth-buster:** Neural networks are **NOT models of the brain**. The term is inspired by neurobiology, but there's no evidence the brain works the same way. For this book's purposes: DL = **"a mathematical framework for learning representations from data."**
- Analogy: a deep network = a **multistage information-distillation process**.

## 6. How Learning Actually Happens (Figures 1.7–1.9)
| Component | Role |
|---|---|
| **Weights** | Numbers that parameterize what each layer does to its input. Also called *parameters*. |
| **Loss function** (a.k.a. objective/cost function) | Compares predictions (Y') to true targets (Y) → produces a **distance/loss score**. |
| **Optimizer** | Adjusts the weights to lower the loss score. Implements **Backpropagation** — "the central algorithm in deep learning." |
| **Training loop** | Repeated adjustment over many examples until loss is minimized → a **trained network**. |

Sequence: Input X → Layers (weights) → Predictions Y' → compared with True targets Y via Loss function → Loss score → Optimizer → updates Weights → repeat.

## 7. What Makes Deep Learning Different (3 Properties)
1. **Simplicity** — Automates **feature engineering** (the old, manual, crucial step). Shallow learning needed humans to hand-craft representations; DL learns all features in one end-to-end pass.
2. **Scalability** — Highly parallelizable on GPUs; trained via small batches → works on datasets of arbitrary size.
3. **Versatility & reusability** — Can be trained on additional data without restarting (continuous/online learning); trained models are **repurposable/reusable** → basis of **"foundation models."**

## 8. The Age of Generative AI
- Powered by large **foundation models** trained via **self-supervised learning**: targets are taken from the input itself (e.g., predict the next word, reconstruct a noisy image).
- Self-supervised learning lets models use **vast amounts of unlabeled data** — removes the manual-annotation bottleneck.
- Generative AI became mainstream in **2022**, but text generation experiments go back to the **1990s**.

## 9. Achievements of Deep Learning (know the rough timeline)
- **2013–2017:** perceptual tasks (image classification, speech transcription, handwriting transcription)
- **2017–2022:** NLP progress
- **2022–now:** generative AI wave
- Also: machine translation, text-to-speech, autonomous driving (deployed in Phoenix, SF, LA, Austin as of 2025), recommender systems, superhuman Go/Chess/Poker, AlphaFold protein structure prediction.

## 10. Hype, AGI, and AI Winters — Be Careful with MC Nuance Here
- Book's stance: today's AI = **"cognitive automation,"** not true intelligence (**"cognitive autonomy"**). Analogy: **AI is like a cartoon character; intelligence is like a living being** — a cartoon can only act out scenes it was drawn for; a living being adapts to the unexpected.
- Key distinguishing concept: **adaptability** — intelligence handles the unknown; automation only handles what it was trained/programmed for.
- **Two past AI winters:**
  1. **1960s–70s (symbolic AI):** Marvin Minsky claimed (1967) AI would "substantially be solved" within a generation; in 1970 predicted human-level general intelligence within 3–8 years. Didn't happen → funding dried up → **first AI winter**.
  2. **1980s (expert systems):** Companies spent **>$1 billion/year** around 1985; systems proved expensive/hard to scale → **second AI winter** in early 1990s.
- **OpenAI history nugget:** Founded **2015**, originally intended as an open-source counterweight to DeepMind, partly motivated by fears (as early as 2013) that AGI was near. In 2016 recruiting pitch claimed AGI by 2020.
- Author's take: unlikely to see a full AI winter like the 1990s again, but expects the **2023–2024 AI bubble** to deflate somewhat. AI investment (>$100B/year, mostly data centers/GPUs) currently **outpaces revenue** (~$10B/year).

---

## Quick-Fire Definitions Table (great for last-minute MC review)

| Term | One-line definition |
|---|---|
| Symbolic AI | Explicit handcrafted rules on explicit databases |
| Machine Learning | Learns rules from data + answers via training |
| Deep Learning | ML using many stacked layers of representations |
| Representation | A way of encoding/looking at data |
| Hypothesis space | Predefined set of transformations an algorithm searches |
| Weights/Parameters | Numbers that define what a layer does |
| Loss function | Measures distance between prediction and target |
| Optimizer / Backpropagation | Adjusts weights to reduce loss |
| Training loop | Repeated weight adjustment until loss is minimized |
| Feature engineering | Manually designing good input representations (needed in shallow learning, automated away by DL) |
| Foundation model | Large model, trained on huge data, reusable across many tasks |
| Self-supervised learning | Targets derived from the input data itself |
| Cognitive automation | Author's preferred, more modest term for what today's "AI" actually is |