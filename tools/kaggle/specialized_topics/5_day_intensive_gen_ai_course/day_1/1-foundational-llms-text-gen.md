# 1. Foundational LLMs & Text Generation

https://youtu.be/Na3O4Pkbp-U?si=77ZHyDZKbBvwE5oK

## 1. Introduction
- LLMs have an ability to process, generate and understand user intent.
- LLMs are advanced AI systems that are specialized in the abilities listed above.
- They're also specialized in processing, understanding, and generating human-like text.
- The Deep Neural Network and the amount of text data allows them to learn intricate patterns of language

## 2. Why LMs are important
- LLMs are able to outperform previous Natural Language Processing (NLP) models in various complex tasks.
- Enabling new applications such as language translation, code generation, text generation, classification and question-answering.
- Foundational LLMs demonstrated strong capabilities and emergent behaviors from extensive training on diverse tasks, they can be fine-tuned for specific tasks to improve performance.
- This fine-tuning process requires less data and fewer resources than building an LLM from scratch.
- Prompt engineering plays a crucial role in guiding LLMs towards desired outcomes by crafting effective prompts and adjusting model parameters.

## 3. LLMs
- Language models predict the probability of words that are yet to come in an input sentence.
- **Recurrent Neural Networks (RNNSs)**
- **Long Short-Term Memory (LSTM)**
- **Gated Recurrent Unit (GRU)**
- A **Transformer** is a type of Neural Network that can process sequences of tokens in parallel thanks to the **self-attention mechanism**
    - This means they can model long-term contexts more effectively and are easier to parallelize than RNNs. This makes them smarter to train and more powerful than RNNS for handling long-term dependencies in long sequence tasks.

### 3.1 Transformer

- **Transformer Architecture** has an encoder part and a decoder part
- **Transformer** has multiple layers.
    - **Encoder** converts the input text into a representation, which is then passed to the decoder
    - **Decoder** uses this representation to generate the output text autoregressively
- **Layer** a layer in neural network comprises a set of parameters that perform a specific tranformation on the data.
- **Multi-head Attention** (look at 3.3)
- **Add & Norm**
- **Feed-Forward** (look at 3.2.2)
- **Linear**
- **Softmax**
- **Input Layer** could be input embeddings and/or output embeddings.
    - **Input Embeddings** are used to represent the input tokens to the model.
    - **Output embeddings** are used to represent the output tokens that the model predicts.
- **Output Layer** (like, *Softmax*) is the final later that produces the output of the network.
- **Hidden Layers** (like, *Multi-Head Attention*) are between the input and the output layers. The magic happens here! 
- **Sequence-to-sequence (Seq2Seq) model** 
- **Autoregressive generation** is a sequential AI process where models create output one piece (token) at a time, with each new piece predicted based on all previously generated tokens.
- **Representation (encoded representation)**

#### 3.1.1 Input preperation and embedding
- **Embedding** 
- Generating an input embedding involves the following steps: 
    1. **Normalization** (Optional): Standardizes text by removing redundant whitespace, accents, etc.
    2. **Tokenization**: Breaks the sentence into words or subwords and maps them to integer tokens IDs from a vocabulary.
    3. **Embedding**: Converts each token ID to its corresponding high-dimensional vector, typically using a lookup table. These can be learned during the training process.
    4. **Positional Encoding**: Adds information about the position of each token in the sequence to help the transformer understand word order.


#### 3.1.2 Multi-head attention
- **Self-attention**: a crucial machanism in transformers: it enables them to focus on specific parts of the input sequence relevant to the task at hand and to capture long-range dependencies within sequences more effectively than traditional RNNs.
- IN OTHER WORDS: *Self-attention* is like a high-powered spotlight. Instead of just looking at the word its currently processing, the AI shines a light on all the other relevant words in the sentence to get the full picture. 

### 3.2 Understanding self-attention
- *Self-attention* helps to determine relationships between different words and phrases in sentences. 
- It achieves this through the following steps:
1. **Create Vectors**: Each word is turned into three vectors:
    - **Query (Q)**: "What am I looking for?"
    - **Key (K)**: "What do I offer?"
    - **Value (V)**: The actual content.
2. **Calculate Scores**: Multiply **Q** of one word by **K** of all others (dot product) to see how much they relate.
3. **Normalize**: Scale the scores and use **Softmax** to turn them into weights (0 to 1).
4. **Weighted Values**: Multiply the weights by **V** and sum them up to get a final, context-aware version of the word.

### 3.3 Multi-head attention: power in diversity
- **Multi-head attention** uses multiple parallel attention heads to focus on different relationships in the input, then combines their outputs into a richer representation. 
- This allows transformers to better capture complex language patterns and long-range dependencies, improving performance on tasks like translation, summarization, and question answering.

#### 3.3.1 Layer normalization and residual connections
- **Transformers** use residual connections and layer normalization in each layer to stabilize and speed up training. 
- **Layer normalization** normalizes activations to improve gradient flow and convergence, while residual connections pass inputs directly to later layers to ease optimization and prevent vanishing or exploding gradients.

#### 3.3.2 Feed-Forward layer
- The **feed-forward layer** in a transformer, processes the output of the attention mechanism at each position in the sequence **independently**, meaning it treats each token separately rather than looking across tokens. 
- Its purpose is to add **non-linearity** and increase the model's ability to learn complex patterns.
- This layer usually consists of **two linear transformations** (simple matrix multiplications) with a **non-linear activation function**, such as **ReLU** (Rectified Linear Unit) or **GELU** (Gaussian Error Linear Unit), in between. 
- These activation functions allow the model to learn more complex relationships than linear operations alone.
- After the feedforward computation, the result passes through another **Add and Norm** step:
    - **Residual connection (Add)**: adds the original input back to the output to help training and preserve information.
    - **Layer normalization (Norm)**: normalizes activations to improve training stability and performance.
- Together, the feedforward layer and Add & Norm step enhance the transformer’s representational power while keeping deep models stable and effective.

#### 3.3.3 Encoder and decoder
- The original **transformer architecture** is made up of two main parts: an **encoder** and a **decoder**, each built from repeated layers that include **multi-head attention**, **feedforward networks**, **layer normalization**, and **residual connections**.
- The **encoder** processes the input sequence and converts it into contextualized representations. 
- The input text is **tokenized** (split into tokens), turned into **embeddings** (numerical vectors), and combined with **positional encodings** so the model knows the order of tokens
- Using **self-attention**, each token can attend to all others in the sequence, allowing the model to capture context and relationships. 
- The encoder outputs a set of vectors (**Z**) that represent the entire input sequence with context.
- The **decoder** generates the output sequence one token at a time using the encoder’s output. 
- It uses:
    - **Masked self-attention**, which prevents the model from seeing future tokens and ensures correct sequential generation.
    - **Encoder–decoder (cross) attention**, which lets the decoder focus on relevant parts of the input representation produced by the encoder.
- This process continues until an **end-of-sequence token** is produced.
- Many modern **large language models (LLMs)** use a **decoder-only architecture**, which removes the separate encoder. 
- In this setup, the input is embedded and positionally encoded, then passed directly into the decoder, which relies solely on **masked self-attention** to predict the next token. 
- This simplifies the architecture while remaining effective for text generation tasks.

#### 3.3.4 Mixture of Experts (MoE)
- A **Mixture of Experts (MoE)** is an architecture that improves performance on complex tasks by using multiple specialized sub-models, called **experts**, rather than a single model. 
- Instead of combining all experts equally, an MoE uses a **gating network (router)** to decide which experts are most relevant for a given input and how much each should contribute. 
- The selected experts process the input, and their outputs are **weighted and combined** to produce the final prediction. 
- This approach allows experts to specialize in different sub-tasks and can reduce computation through **sparse activation**, where only a subset of experts is used for each input.

#### 3.3.5 Large Reasoning Models
- Large Reasoning Models achieve strong reasoning ability through a combination of **architecture**, **training**, and **inference strategies**. 
- Transformer-based models provide the foundation, but advanced reasoning requires additional techniques beyond standard self-attention.

- **Prompting methods** such as *Chain-of-Thought*, *Tree-of-Thoughts*, and *Least-to-Most prompting* guide models to break complex problems into smaller steps, explore multiple reasoning paths, and solve tasks progressively, improving multi-step inference.

- **Training approaches** like fine-tuning on reasoning-focused datasets, **instruction tuning**, and **Reinforcement Learning from Human Feedback (RLHF)** further enhance logical coherence, helpfulness, and reasoning quality.

- To improve efficiency, **knowledge distillation** transfers reasoning skills from large models to smaller ones. 
- During inference, techniques such as **beam search** and **temperature scaling** help explore better reasoning paths. 
- Finally, **external knowledge integration**, including **retrieval-augmented generation**, supplies relevant information to support more accurate and informed reasoning. 
- Together, these methods produce highly capable reasoning-focused large language models.

#### 3.3.6 Training the transformer
- In machine learning, **training** and **inference** are distinct phases. 
- **Training** involves updating a model’s parameters using loss functions and backpropagation, while **inference** uses the trained model to generate predictions with fixed parameters.

### 3.4 Data preparation
- Data preparation is the first step in training a model and includes cleaning the data through filtering, deduplication, and normalization. 
- The text is then **tokenized** using methods like Byte-Pair Encoding or Unigram tokenization to create a **vocabulary** the model uses to understand language. 
- Finally, the data is split into training and test sets for model training and performance evaluation.

### 3.5 Training and loss function
- Training a transformer involves feeding batches of input sequences into the model, comparing its predicted outputs to target sequences using a **loss function** (commonly cross-entropy), and updating the model’s parameters via gradient-based optimization. 
- This loop repeats until the model reaches the desired performance.
- The training objective depends on the transformer architecture:
    - **Decoder-only models** are trained with language modeling, predicting the next token from previous tokens.
    - **Encoder-only models** (e.g., BERT) use tasks like **masked language modeling**, where the model reconstructs corrupted input.
    - **Encoder–decoder models** are trained on sequence-to-sequence tasks such as translation, summarization, and question answering, either supervised or adapted from unsupervised data.
- Another key consideration is **context length**, which determines how many previous tokens the model can use. Longer contexts capture richer dependencies but increase computational and memory costs, requiring a trade-off between performance and efficiency.

## 4. The evaluation of transformers
- These include encoder-only, encoder-decoder, as well as decoder-only transformers.

### 4.1 GPT-1 (novelist)
- **GPT-1** was a decoder-only transformer model introduced by OpenAI in 2018 and trained on the **BooksCorpus**, a large unlabeled dataset of long-form text. 
- Its key innovation was demonstrating the effectiveness of **unsupervised pre-training** on large text corpora followed by **supervised fine-tuning**, which improved generalization and reduced reliance on labeled data.
- Another important contribution was **task-aware input transformations**, where different NLP tasks (such as textual entailment and question answering) were reformulated into a single text input format, allowing GPT-1 to handle multiple tasks without task-specific architectures.
- GPT-1 achieved strong benchmark results and showed the power of transformer-based language models, but it had limitations, including repetitive text generation, weak multi-turn reasoning, and difficulty maintaining coherence over long passages. 
- Despite this, it laid the groundwork for later, more capable GPT models.

### 4.2 BERT (puzzle master)
- **BERT** is an **encoder-only transformer** that focuses on understanding context rather than generating text. 
- It is trained using **masked language modeling** (predicting randomly masked words from surrounding context) and **next sentence prediction** (determining if one sentence logically follows another). 
- These training objectives allow BERT to capture deep contextual relationships and sentence-level dependencies.
- Making it highly effective for natural language understanding tasks like question answering, sentiment analysis, and inference. 
- However, BERT cannot generate text.

### 4.3 GPT-2
- **GPT-2**, released in 2019, was a scaled-up successor to GPT-1, with **1.5 billion parameters** and trained on a large 40GB **WebText** dataset of high-quality webpages. 
- The increase in parameters and data allowed GPT-2 to generate more coherent, human-like text and capture long-range dependencies and commonsense reasoning better than GPT-1.
- A major advancement of GPT-2 was its **zero-shot learning** ability, meaning it could perform tasks like translation, summarization, and reading comprehension without task-specific training, simply by understanding instructions in the input. 
- Performance on these tasks improved as **model size increased**, demonstrating the benefits of scaling both data and parameters for generalization.

### 4.4 GPT-3/3.5/4
- **GPT-3** is a massive evolution from GPT-2, featuring **175 billion parameters**, enabling it to generate more coherent, contextually relevant text and understand nuanced instructions over longer passages. 
- Uses **Few-shot learning**
- Unlike GPT-2, GPT-3 can perform tasks with few or no examples, reducing the need for task-specific fine-tuning.
- **InstructGPT**, a fine-tuned version of GPT-3 using **human demonstrations and reinforcement learning from feedback**, improved instruction-following, truthfulness, and safety. 
- **GPT-3.5** enhanced dialogue capabilities, code understanding, and expanded context windows.
- GPT-4 further extends GPT-3.5 as a **multimodal model** that handles *text and images*, with extremely large context windows, advanced reasoning, and broad domain knowledge. 
- It excels in complex tasks across fields like mathematics, coding, law, medicine, and psychology, often matching or surpassing human performance and significantly outperforming earlier models.

### 4.5 LaMDA
- **Google’s LaMDA** is a large language model designed specifically for **open-ended conversations**. 
- Trained on dialogue-focused data, it emphasizes natural, flowing exchanges across a wide range of topics. 
- Unlike GPT models, which excel at diverse tasks and long-form content generation, LaMDA focuses on **maintaining conversational depth and progression**, aiming to mimic the richness and unpredictability of human dialogue.

### 4.6 Gopher
- **Gopher**, developed by DeepMind in 2021, is a **280 billion parameter decoder-only transformer** trained to generate text, translate, create content, and answer questions. 
- It was trained on a high-quality, filtered dataset called **MassiveText**, and optimized with careful learning rate schedules, batch sizing, and gradient clipping to stabilize training.
- Gopher excelled on **knowledge-intensive tasks** like general knowledge and reading comprehension, outperforming previous models on 81% of evaluated tasks, but struggled on reasoning-heavy tasks such as abstract algebra. 
- Increasing model size significantly improved performance on logical reasoning and comprehension tasks, while gains on general knowledge tasks plateaued.

### 4.7 GLaM
- **GLaM** is a **sparsely-activated mixture-of-experts language model** with 1.2 trillion parameters. 
- It improves computational efficiency by activating only a subset of experts for each input. 
- As a result, GLaM uses one-third of the energy for training and half the FLOPs for inference compared to GPT-3, while achieving better overall performance.

### 4.8 Chinchilla
- Until 2022, large language models (LLMs) were scaled mainly by increasing **model size** with relatively small datasets. 
- The Kaplan et al. study suggested increasing model size more than dataset size for higher compute budgets. 
- However, the **Chinchilla paper** showed that **balanced scaling**, increasing both model parameters and dataset size proportionally, yields better performance.
- DeepMind’s **Chinchilla** (70B parameters) trained with the same compute as Gopher (280B) outperformed larger models while being more efficient in memory and inference cost. 
- These findings shifted LLM development toward **scaling dataset size alongside model size**, with new research exploring limits under data-constrained conditions.

### 4.9 PaLM 
- **PaLM** is a **540-billion parameter transformer** developed by Google AI, trained on a massive text and code dataset. 
- It excels at a wide range of tasks, including reasoning, code generation, translation, and joke explanation, achieving state-of-the-art results on benchmarks like GLUE and SuperGLUE. 
- Its efficiency comes from the **Pathways system**, which enables scalable training across multiple TPU v4 Pods.

#### 4.9.1 PaLM 2
- **PaLM 2**, announced in May 2023, is the successor to PaLM with improved architecture and training, offering higher capabilities despite having fewer parameters. 
- It excels at reasoning, code generation, math, classification, question answering, and translation, and is more efficient than PaLM. 
- PaLM 2 also serves as the foundation for Google Cloud’s commercial generative AI models.

### 4.10 Gemini
- **Gemini** is Google’s state-of-the-art **multimodal language model family**, capable of processing text, images, audio, and video. 
- Built on **transformer decoders** with architectural optimizations, it supports extremely large context windows, up to **millions of tokens** in Gemini 1.5 Pro, and employs **Mixture-of-Experts** for efficiency.
- The family includes models optimized for different purposes:
    - **Gemini Ultra**: handles highly complex tasks, achieving state-of-the-art results.
    - **Gemini Pro**: scalable deployment.
    - **Gemini Nano**: on-device applications using distillation for efficiency.
    - **Gemini Flash**: fast, cost-efficient, high-volume tasks with a 1 million token context.
- **Gemini 1.5 Pro** excels in code understanding, language learning, multimodal reasoning, and video comprehension, with near-perfect recall even for documents up to 10 million tokens. 
- It also demonstrates strong multi-step instruction following.
- **Gemini 2.0** builds on this with enhanced multimodal understanding, efficiency, and new capabilities:
    - **Gemini 2.0 Flash**: faster, efficient, with improved spatial reasoning and multimodal performance.
    - **Gemini 2.0 Pro**: high capability across tasks.
    - **Gemini 2.0 Nano**: optimized for on-device use.
    - **Gemini 2.0 Flash Thinking Experimental**: advanced reasoning with explainability, large input/output context, code execution, and text + image support, aimed at complex tasks.
- Overall, the Gemini family showcases Google’s advances in **scalable**, **multimodal**, and **instruction-following LLMs**.

### 4.11 Gemma
- **Gemma** is Google’s family of **lightweight, open large language models** built on the same technology as the Gemini models.
    - The first Gemma model has a **256K vocabulary** and was trained on **6 trillion tokens**, with a **2B parameter version** that can run efficiently on a single GPU.
    - **Gemma 2** is a **27B parameter model** that achieves performance comparable to much larger models like LLaMA 3 70B, offering **efficient architecture**, strong benchmark performance, and compatibility with diverse tuning toolchains for broad developer accessibility.
    - **Gemma 3** introduces **multimodality**, processing text and image inputs with text outputs, a **128K token context window**, and support for **140+ languages**. It comes in multiple sizes (1B, 4B, 12B, 27B) to suit different hardware and application needs, making it highly versatile for both resource-constrained and high-performance environments.
- Overall, the Gemma family advances **open**, **efficient**, and **accessible LLMs**, providing powerful tools for developers and researchers.

### 4.12 LLaMA
- **LLaMA** models are **decoder-only transformers** designed to predict the next token in a sequence. Meta has released several generations:
    - **LLaMA 1**: 7B–65B parameters, strong performance among open-source models.
    - **LLaMA 2**: 7B–70B parameters, fine-tuned for chat (**LLaMA 2-Chat**), doubled context length (4096 tokens), 40% larger dataset, grouped-query attention, and released with a **commercial license**.
    - **LLaMA 3**: Builds on LLaMA 2 with enhanced reasoning, coding, and general knowledge capabilities, improved safety and alignment, and includes multilingual text-only and vision LLMs in LLaMA 3.2, featuring quantized versions for on-device deployment, grouped-query attention, and a **128K token vocabulary**.
- Overall, the LLaMA family emphasizes **scalability**, **chat performance**, **multilingual support**, and **safe deployment**.

### 4.13 Mixtral
- **Mixtral 8x7B**, developed by **Mistral AI**, is a **Sparse Mixture of Experts (SMoE)** model with 47B total parameters but only **12B active parameters per token**, making inference faster and more efficient.
- It performs particularly well in **mathematics**, **code generation**, and **multilingual tasks**, often outperforming **LLaMA 2 70B**, and supports a **32k token context length**.
- The **instruction-tuned version** excels on human evaluation benchmarks, and Mistral emphasizes **open access** by releasing models under the **Apache 2.0 license** while also offering models via an API for flexible use.

### 4.14 OpenAI 01
- OpenAI's **o1 model series** is designed for **advanced reasoning**, using RL and an internal **chain-of-thought-style deliberation** process to solve complex problems.
- This approach leads to outstanding performance on dificult scientific and technical benchmarks, including top-tier results in competitive programming, mathematics, and science, often surpassing human expert levels.
- The series includes **o1**, optimized for broad, complex readoning tasks, and **o1-mini**, a faster and more cost-efficient variant focused on coding, math and scientitic problem-solving.

### 4.15 DeepSeek
- **DeepSeek** showed that strong reasoning performance comparable to OpenAI's **o1** models can be achieved using a **pure RL** approach with minimal labeled data.
- Their ket innovation, **Group Relative Policy Optimization (GPRO)**, removes the need for a critic model by scoring outputs using predefined rules (coherence, completeness, fluency) and learning though **self-comparison** across multiple outputs.
- The initial **DeepSeek-R1-Zero**model, trained purely with RL, achieved high reasoning scores (mathcing o1 on AIME 2024) but suffered from poor readability.
- To address this, DeepSeek introduced a **multi-stake training pipeline** for **DeepSeek-R1**:
    1. **Supervised fine-tuning (SFT)** on a small dataset to establish basic language skills.
    2. **Pure RL with GRPO** to develop strong reasoning abilities.
    3. **Rejection sampling** to create high-quality synthetic training data.
    4. **Final SFT and RL** combining synthetic and supervised data to improve fluency, generalization, and overall quality.
- This approach produces a well-rounded model that matches or exceeds o1 in many areas, with **chain-of-thought reasoning** emerging naturally from the RL training process. 
- Although model weights are released, limited transparency around training data and methods makes the models effectively **closed-source**.

### 4.16 Other open models
- The **open LLM ecosystem** is rapidly expanding, with many models releasing both **code and pretrained weights**. Notable examples include:
    - **Qwen 1.5 (Alibaba)**: Models from 0.5B to 72B parameters, all supporting **32k context**, with strong benchmark performance, **Qwen 1.5-72B** surpasses LLaMA2-70B across evaluated tasks.
    - **Yi (01.AI)**: 6B and 34B models trained on **3.1T tokens** of high-quality English and Chinese data, achieving performance comparable to **GPT-3.5**, with variants supporting long context, vision-language tasks, and efficient deployment.
    - **Grok 3 (xAI)**: Reinforcement-learning–trained models with advanced reasoning and **1M token context windows**, released in standard and lightweight versions.
- Beyond these, many academic and commercial efforts contribute to the fast-paced innovation in LLMs, including projects like **GPT-NeoX, Alpaca, Vicuna, Falcon, PHI, NVLM, DBRX, and LLaMA**, as well as companies such as **Anthropic, Cohere, xAI, and AI21**. 
- Given the diversity of models and licenses, users must carefully review **licensing terms** to ensure suitability for their use cases.

### 4.17 Comparison
- Transformer-based language models have evolved from **encoder–decoder architectures** with millions of parameters to large decoder-only models with billions of parameters trained on trillions of tokens. 
- Scaling model size and data has greatly improved performance, leading to **emergent abilities** and **zero- or few-shot generalization**. 
- However, despite these advances, LLMs still face limitations in areas like natural conversation, mathematical reasoning, and ethical alignment, motivating ongoing research to address these challenges.

## 5. Fine-tuning large language models
- Large language models are trained in multiple stages. 
- The first stage, **pre-training**, teaches the model general language understanding by predicting the next token on large, unlabeled text datasets. 
- This stage is the most computationally expensive but enables strong zero-shot and few-shot performance across tasks.
- After pre-training, models are refined through **fine-tuning** (**supervised or instruction tuning**), which adapts them to specific tasks and behaviors. 
- Fine-tuning can improve **instruction following**, **multi-turn dialogue**, and **safety**, often using methods like **reinforcement learning from human feedback (RLHF)**. 
- Compared to pre-training, fine-tuning is more efficient and significantly less costly while enabling targeted improvements in model performance and alignment.

### 5.1 Supervised fine-tuning
- **Supervised fine-tuning (SFT)** improves an LLM’s performance by training it on **small**, **high-quality**, **human-curated labeled datasets** tailored to specific tasks. 
- Each training example pairs a **prompt** with a **target response**, such as question–answer pairs, translations, or summaries. 
- Beyond task performance, SFT is also used to improve **instruction following**, **conversational ability**, and **safety**, helping reduce toxic or harmful outputs.

### 5.2 Reinforcement learning from human feedback
- After supervised fine-tuning (SFT), LLMs are often further refined using **reinforcement learning from human feedback (RLHF)** to better align outputs with human preferences such as helpfulness, truthfulness, and safety.
- Unlike SFT, RLHF uses both **positive and negative examples**, penalizing undesirable responses. 
- This process involves training a **reward model (RM)** on human preference data (e.g., choosing the better of two responses), which then guides reinforcement learning to fine-tune the LLM. 
- To scale this approach, **reinforcement learning from AI feedback (RLAIF)** replaces human labels with AI-generated feedback, while methods like **direct preference optimization (DPO)** aim to achieve alignment without full RLHF training.

### 5.3 Parameter Efficient Fine-Tuning
- Full fine-tuning of LLMs is **computationally expensive**, but **parameter-efficient fine-tuning (PEFT)** techniques allow adapting models with far fewer trainable parameters. 
- PEFT methods “perturb” the pre-trained weights with a smaller set of parameters to specialize the model for new tasks. 
- Common approaches include:
    - **Adapter-based fine-tuning**: Small modules (adapters) are added and trained, leaving most weights frozen.
    - **Low-Rank Adaptation (LoRA)**: Trains small matrices to approximate weight updates, keeping original weights frozen; variants like QLoRA use quantization for further efficiency.
    - **Soft prompting**: Uses learnable vectors instead of textual prompts to condition frozen models efficiently.
- PEFT methods reduce memory and compute requirements, achieve comparable performance to full fine-tuning, and enable flexible task adaptation.

## 6. Using Large Language Models
- Prompt engineering and sampling techniques significantly affect LLM performance. 
- **Prompt engineering** involves designing and refining inputs to elicit desired outputs, while **sampling techniques** control how output tokens are selected, impacting correctness, creativity, and diversity. 
- Both areas, along with key parameters, play a critical role in shaping the quality of LLM responses.

### 6.1 Prompt Engineering
- Prompt engineering is key to guiding LLMs to produce accurate, creative, or task-specific outputs. 
- Techniques include providing clear instructions, examples, keywords, formatting, and context. 
- Common strategies are:
    - **Zero-shot prompting**: The model receives only instructions, relying on prior knowledge.
    - **Few-shot prompting**: The model is given a few examples to guide its response.
    - **Chain-of-thought prompting**: The model is prompted to reason step-by-step for complex tasks.
- This area remains an active field of research to optimize LLM performance.

### 6.2 Sampling Techniques and Parameters
- Sampling techniques control how an LLM selects the next token, affecting creativity, diversity, and quality of output:
    - **Greedy search**: Always picks the highest-probability token; simple but can be repetitive.
    - **Random sampling**: Picks tokens according to their probability distribution; more creative but can be nonsensical.
    - **Temperature sampling**: Adjusts probabilities; higher temperature = more diversity, lower = more predictable.
    - **Top-K sampling**: Randomly selects from the top K tokens; K sets the randomness level.
    - **Top-P (nucleus) sampling**: Samples from tokens whose cumulative probability is P; adapts to model confidence.
    - **Best-of-N sampling**: Generates N outputs and chooses the best based on a metric; useful for reasoning-focused tasks.
- Combining these with prompt engineering allows fine control over the relevance, creativity, and consistency of LLM responses.

### 6.3 Task-based Evaluation
- Moving LLMs from prototype to production requires careful evaluation, tailored to the specific application. Key considerations include:
    - Evaluation Data: Use datasets that reflect expected production traffic, enriched with real user interactions, logs, and synthetic examples.
    - Development Context: Evaluate the entire system, including data augmentation (e.g., RAG) and agentic workflows, not just model outputs.
    - Definition of “Good”: Move beyond matching a single correct answer; define performance based on desired business outcomes or rubrics reflecting key output qualities.
- Evaluation Methods:
    1. **Traditional Metrics**: Quantitative measures comparing outputs to reference answers; may penalize creative or unexpected solutions.
    2. **Human Evaluation**: Gold standard, offering nuanced judgment for complex generative tasks.
    3. **LLM-Powered Autoraters**: Scalable, mimic human judgment, can provide rationales. Require **meta-evaluation** to ensure alignment with human preferences.
- Advanced setups break tasks into subtasks for interpretable metrics and allow specialized models for better reliability. 
- Aggregated results provide overall or axis-specific scores, particularly useful in media generation where multiple skills (e.g., text vs image) are needed.
- This approach ensures performance, reliability, and actionable insights in production LLM applications.

## 7. Accelerating inference
- LLMs have grown consistently in size, improving quality and accuracy, but this also increases computational and memory demands. 
- Optimizing efficiency, balancing cost, speed, and energy use, is crucial for practical deployment. 
- As models scale from millions to billions of parameters, inference performance becomes a key challenge. 
- Research now focuses on techniques to accelerate inference while managing trade-offs between memory, computation, and latency for large-scale, low-latency applications.

### 7.1 Trade offs
- **Inference optimization** often involves trade-offs, such as between latency, quality, and cost. 
- These **trade-offs** can be adjusted depending on the specific use case. 
- Accepting a small reduction in one factor can lead to significant improvements in another, enabling tailored and balanced optimization strategies.

#### 7.1.1 The Quality vs Latency/Cost Tradeoff
- **Inference speed** and **cost** can be improved with minimal impact on accuracy by using smaller models or quantizing parameters. 
- The actual effect on performance depends on the task, often, simpler tasks can be handled effectively even with reduced model size or precision, meaning quality loss isn’t always significant.

#### 7.1.2 The Latency vs Cost Tradeoff
- This passage discusses the **latency** vs **throughput tradeoff** in LLM inference: higher throughput reduces cost but may affect latency, and vice versa. 
- Optimizing this balance is crucial depending on the use case, for example, offline batch tasks prioritize cost, while chatbots prioritize low latency. 
- Inference acceleration methods are categorized as **output-approximating** (may slightly affect output) or **output-preserving** (maintain output quality). 
- Gemini 2.0 Flash Thinking exemplifies an effective balance of high-quality reasoning and low cost, highlighting rapid advancements in AI capabilities.

### 7.2 Ouput-approximating methods
#### 7.2.1 Quantization
- LLMs rely on large numerical matrices (weights) for inference, and **quantization** reduces the numerical precision of weights and activations (e.g., from 32-bit floats to 8- or 4-bit integers). 
- This reduces memory usage, speeds up communication across chips, and enables faster arithmetic operations on hardware like GPUs/TPUs. 
- Quality impact is often minimal, making it an **effective quality vs latency/cost tradeoff**. 
- Quantization can be applied post-training or during **Quantization Aware Training (QAT)**, which helps the model recover potential accuracy losses. 
- Strategies like varying precision for weights vs activations and applying quantization at different granularities optimize this tradeoff.

#### 7.2.2 Distillation
- Using smaller models can improve inference efficiency but usually at the cost of quality. 
- **Distillation** techniques help smaller “student” models learn from larger “teacher” models to close this quality gap.
    - **Data distillation/model compression**: The teacher generates synthetic data to train the student, improving performance beyond the original dataset. Quality of synthetic data is critical.
    - **Knowledge distillation**: Aligns the student’s output token distribution with the teacher’s, making training more sample-efficient.
    - **On-policy distillation**: Uses teacher feedback on sequences generated by the student, often in a reinforcement learning setup, to further improve performance.
- These techniques allow smaller models to achieve better quality while retaining efficiency gains.

### 7.3 Output-preserving methods
- These inference optimization methods are **quality-neutral**, meaning they don’t alter the model’s outputs. 
- They are typically the first choice for improving efficiency before considering methods that involve trade-offs in output quality.

#### 7.3.1 Flash Attention
- Scaled Dot-Product Attention, a core transformer operation, is quadratic in input length and can be a performance bottleneck. 
- **Flash Attention** optimizes this by minimizing data movement between memory tiers and fusing operations, achieving **2–4× faster attention computation** without changing the output, providing significant latency and cost benefits.

#### 7.3.2 Prefix Caching
- Calculating attention key and value scores (KV) during LLM inference, called prefill, is compute-intensive. 
- **Prefix caching** stores the KV cache from previous inputs, allowing reuse in subsequent requests, which reduces latency and computation. 
- It is especially useful for **multi-turn conversations** or **large document/code uploads**. 
- Caches can be stored in memory or on disk, but the input structure must remain consistent to avoid invalidating the cache. 
- Google AI Studio and Vertex AI provide this as **Context Caching**.

#### 7.3.3 Speculative Decoding
- LLM inference has two phases: **prefill** (compute-bound, parallel matrix operations) and decode (memory-bound, serial token generation). 
- **Speculative decoding** speeds up decoding by using a smaller “drafter” model to predict tokens ahead of the main model. 
- The main model then verifies these predictions in parallel, reducing latency significantly without affecting output quality. 
- Effective speculative decoding requires the drafter to be well-aligned with the main model.

### 7.4 Batching and Parallelization
- LLM inference can be further optimized using **batching** and **parallelization**, techniques common in general software systems. 
- **Batching** combines multiple requests during the decode phase to better utilize spare compute, though memory limits must be considered. 
- **Parallelization** distributes computation across inputs (sequence parallelism), layers (pipeline parallelism), or within layers (tensor parallelism), but communication overhead between hardware shards must be managed carefully. 
- Properly applied, these methods significantly improve throughput and reduce latency.

## 8. Applications
- Large language models are transforming how we create and interact with text, code, images, audio, and video. 
- While many applications exist, the field is rapidly evolving with new use cases emerging constantly. 
- Tools like Google Cloud Vertex AI SDK and AI Studio make it easy to generate text-based responses using models like Gemini, with multimodal capabilities discussed in dedicated resources.

### 8.1 Code and mathematics
- Generative models enhance software development by assisting with code generation, completion, refactoring, debugging, translation, test case creation, and documentation. 
- They save time, improve quality, and facilitate understanding. 
- Advanced LLM-based systems like **AlphaCode 2**, **FunSearch**, and **AlphaGeometry** extend these capabilities to competitive coding, mathematics, and geometric theorem proving, achieving performance comparable to top human coders and solving previously open problems efficiently.

### 8.2 Machine translation
- LLMs excel at producing fluent, context-aware translations by understanding linguistic nuances, idioms, and culture. 
- Real-world applications include instant messaging for natural cross-language communication, e-commerce platforms for accurate product translations, and travel apps for smooth real-time spoken translations.

### 8.3 Text summarization
- LLMs excel at text summarization, which can be applied to news aggregation, research databases, and chat platforms. 
- They can generate concise summaries that capture key points, sentiment, and tone, helping users quickly understand content, prioritize responses, and grasp core findings in research papers.

### 8.4 Question-answering
- LLMs greatly improve **question-answering** (QA) by *understanding context and user intent*, unlike older keyword-based systems. 
- They enhance applications such as virtual assistants, customer support, and academic platforms by providing personalized, context-aware, and accurate responses. 
- Performance can be further improved with advanced techniques like **Retrieval-Augmented Generation (RAG)**, chain-of-thought prompting, careful prompt engineering, and tuning parameters like temperature.

### 8.5 Chatbots
- LLMs enable **chatbots** to have dynamic, human-like conversations by understanding sentiment, context, and humor. 
- Applications include customer service, where chatbots provide personalized advice and support, and entertainment, where they interact dynamically with users, moderate chats, and respond to live events.

### 8.6 Content generation
- LLMs excel at generating human-like, contextually rich text across diverse styles and tones. 
- They maintain coherence over long passages and blend factuality with creativity. 
- **Key applications** include **content creation**, where they generate targeted marketing messages, and scriptwriting, where they assist with dialogues or scene suggestions. 
- The balance between correctness and creativity can be tuned via sampling methods and parameters like temperature.

### 8.7 Natural Language Inference
- LLMs excel at **Natural Language Inference (NLI)**, determining if a hypothesis logically follows from a premise. Their deep understanding of context and semantics enables near-human accuracy. Applications include:
    - **Sentiment analysis**: Extracting nuanced emotions from customer reviews.
    - **Legal document review**: Identifying contradictions or risks in contracts.
    - **Medical diagnoses**: Inferring potential health risks from patient descriptions.
- Domain-specific LLMs and prompt engineering further enhance these capabilities

### 8.8 Text Classification
- LLMs enhance **Text Classification** by accurately categorizing text, even with ambiguous or overlapping categories. Applications include:
    - **Spam detection**: Context-aware identification of spam vs legitimate emails.
    - **News categorization**: Sorting articles into topics like technology, politics, or sports.
    - **Customer feedback sorting**: Classifying feedback into categories like product, service, or pricing.
    - **LLM evaluation**: Using LLMs to rate, compare, and rank outputs from other LLMs.

### 8.9 Text Analysis
- LLMs provide **deep text analysis**, uncovering patterns, themes, and actionable insights from large text datasets. Applications include:
    - **Market research**: Analyzing social media conversations to identify trends, preferences, and emerging needs.
    - **Literary analysis**: Examining themes, motifs, and character development in literature for new insights.

### 8.10 Multimodal Applications
- **Multimodal LLMs**, which process and generate text, images, audio, and video, enable a wide range of innovative applications:
    - **Creative content**: Storytelling from visuals, targeted advertising.
    - **Education & accessibility**: Personalized learning, assistive tools for visually or hearing-impaired users.
    - **Business & industry**: Document understanding, multimodal customer service.
    - **Science & research**: Medical diagnosis from scans and reports, bioinformatics, and drug discovery.
- These models build on text-based LLM methods and are expected to expand the scope of human–machine interaction across sectors.