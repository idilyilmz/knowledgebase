# 2. Prompt Engineering

https://youtu.be/CFtX0ZyLSAY?si=q9pj9yIUPLdZs9WU

## 1. Introduction

- **Prompts** are the inputs LLMs use to generate outputs and while anyone can write them, creating *effective* prompts is challenging. 
- Prompt quality depends on many factors, including the model, its training data, configuration settings (like temperature), wording, structure, tone and context. 
- As a result, prompt engineering is an **iterative process** and poorly designed prompts can lead to vague or inaccurate responses.
- This whitepaper focuses on **prompting the Gemini model via Vertex AI or APIs**, where users have more control over model configurations. 
- It introduces prompt engineering techniques, best practices and common challenges to help users become more effective at crafting prompts.

## 2. Prompt Engineering

- LLMs work by **predicting the next token** in a sequence based on prior text and patterns learned during training. 
- Prompt engineering aims to set up the input text so the model predicts the *desired* sequence of tokens. 
- It involves iteratively refining prompts, adjusting length, wording, structure and style, to guide the model toward accurate outputs.
- Prompts enable many tasks, including summarization, extraction, Q&A, classification, translation and code-related tasks. 
- Because different models behave differently, prompts often need to be **tailored to the chosen model** (e.g., Gemini, GPT, Claude, or open-source models). 
- In addition to prompt design, **model configuration settings** also play an important role in achieving optimal results.

## 3. LLM output configuration

- After selecting an LLM, you must configure its settings, as these options directly influence the model’s output. 
- Effective prompt engineering involves tuning these configurations appropriately to match the specific task and achieve the best results.

### 3.1 Output length

- The maximum number of generated tokens is a key LLM configuration because longer outputs require more computation, increasing latency, energy use and cost. 
- Limiting tokens only stops generation, it does not make responses more concise, so prompts may need to be engineered to enforce brevity. 
- Output length limits are especially important for techniques like ReAct, where the model may otherwise continue generating unnecessary tokens.

### 3.2 Sampling controls

- LLMs generate text by assigning probabilities to all possible next tokens and then sampling from them. 
- Configuration settings like **temperature**, **top-K** and **top-P** control how these probabilities are sampled, influencing how deterministic or creative the final output is.

#### 3.2.1 Temperature

- **Temperature** controls randomness in LLM outputs. 
- Low temperatures produce more deterministic and predictable responses, while higher temperatures increase diversity and randomness. 
- At very high temperatures, all tokens become nearly equally likely. Conceptually, temperature works like the softmax temperature: low values sharpen probability differences, while high values flatten them, making the model more flexible and creative.

#### 3.2.2 Top-K and top-P

- Top-K and top-P (nucleus sampling) limit which tokens an LLM can choose from, controlling randomness and output diversity. 
- Top-K restricts selection to the K most likely tokens (lower K = more deterministic; K=1 equals greedy decoding). 
- Top-P selects tokens whose cumulative probability is below a threshold P (lower P = more focused; P=1 allows all tokens). 
- Both can be used individually or together and the best choice depends on experimentation for the desired balance of creativity and accuracy.

#### 3.2.3 Putting it all together

- Choosing temperature, top-K, top-P and output length depends on the task, as these settings interact closely. 
- Typically, top-K and top-P first filter candidate tokens, then temperature controls how randomly one is selected. 
- Extreme values in any setting can override the others (e.g., temperature = 0 or top-K = 1 makes output deterministic).
- General starting points are moderate settings (e.g., temperature 0.2, top-P 0.95, top-K 30) for balanced creativity and coherence, higher values for creative tasks and lower or zero temperature for tasks with a single correct answer. 
- However, higher freedom can reduce relevance and may cause issues like repetition loops, where poor parameter choices lead the model to repeat filler text. 
- Careful tuning is needed to balance creativity, accuracy and stability.

## 4. Prompt Techniques

- LLMs are trained to follow instructions and generate responses from prompts, but their outputs improve significantly with clear, well-structured prompts. 
- Because LLMs are not perfect, effective prompt engineering, using techniques aligned with how models are trained and operate, helps produce more accurate and relevant results. 
- This sets the stage for exploring key prompting techniques.

### 4.1 General prompting / zero shot

- Zero-shot prompting is the simplest prompting method, where the model is given only a task description and input text, with no examples. 
- It’s useful for straightforward tasks like classification and is typically paired with low temperature settings to reduce randomness. 
- Using structured documentation (such as tables) helps track prompt iterations during development. 
- If zero-shot prompts fail to produce reliable results, adding examples leads to one-shot or few-shot prompting.

### 4.2 One-shot & few-shot

- Using examples in prompts helps guide AI models toward desired outputs.
    - **One-shot prompting**: Provides a single example for the model to imitate.
    - **Few-shot prompting**: Provides multiple examples (typically 3–5) to show a pattern, increasing the likelihood the model follows it.
- Example quality matters—use relevant, diverse and well-written examples. Including edge cases ensures the model can handle unusual or unexpected inputs. Task complexity and model input limits influence the number of examples needed.

### 4.3 System, contextual and role prompting 

- LLMs can be guided using three main types of prompts, each with a distinct focus:
    - **System prompting**: Sets the overall purpose or capabilities of the model (the “big picture”), e.g., translating or classifying text.
    - **Contextual prompting**: Provides task-specific details or background relevant to the current input, helping the model tailor its response.
    - **Role prompting**: Assigns a character or identity for the model to adopt, shaping the style, voice and behavior of its output.
- These prompts can overlap, but understanding their differences helps design prompts with clear intent and analyze their influence on the model’s output.

#### 4.3.1 System prompting

- **System prompts** provide clear, overarching instructions to the LLM, helping ensure outputs meet specific requirements. They can:
    - Specify output structure (e.g., JSON) to reduce errors and hallucinations.
    - Control style, formatting, or compatibility (e.g., generating code in a certain language).
    - Enhance safety or limit toxicity by adding instructions like “be respectful.”
    
        Even with higher creativity (temperature) or longer outputs, clear system instructions help the model stay on task.

#### 4.3.2 Role propmting

- **Role prompting** assigns a specific role to the AI model, guiding it to generate outputs consistent with that role’s expertise, tone and style. 
- Examples include making the model act as a teacher, travel guide, or motivational speaker. 
- Role prompts improve relevance and effectiveness of responses and can be combined with styles like humorous, formal, descriptive, or inspirational to shape the output further.

#### 4.3.3 Contextual

- **Contextual prompting** provides specific background or task-related details to the AI, helping it understand requests more quickly and generate more accurate, relevant responses.

### 4.4 Step-back prompting

- **Step-back prompting** improves LLM performance by first asking a broader, related question to activate relevant knowledge, then using that answer to inform the specific task. 
- This approach encourages critical thinking, reduces biases and generates more accurate and insightful responses.

### 4.5 Chain of Thought (CoT)

- **Chain of Thought (CoT) prompting** improves LLM reasoning by explicitly generating **intermediate steps** before the final answer. 
- It enhances accuracy, interpretability and robustness across LLM versions and works well with zero-shot, one-shot, or few-shot setups. 
- CoT is particularly useful for tasks like math, code generation, or structured problem solving, though it increases output length, cost and latency.

### 4.6 Self-Consistency

- **Self-consistency prompting** enhances LLM reasoning by generating multiple reasoning paths for the same prompt and selecting the most common answer. 
- Unlike simple Chain of Thought (CoT) prompting, this approach uses higher temperature sampling to explore diverse solutions, improving accuracy and coherence. 
- While effective, it comes with higher computational costs.

### 4.7 Tree of Thoughts (ToT)

- **Tree of Thoughts (ToT)** extends Chain of Thought prompting by allowing LLMs to explore multiple reasoning paths simultaneously instead of a single linear chain. 
- Each node in the tree represents an intermediate thought, enabling the model to branch out and consider alternative solutions. 
- This makes ToT especially effective for complex tasks that require exploration and multiple possibilities.

### 4.8 ReAct (Reason & Act)

- **ReAct (Reason and Act)** prompting enables LLMs to solve complex tasks by combining natural language reasoning with actions, such as interacting with external tools or APIs. 
- It operates in a thought–action loop: the LLM reasons about a problem, executes actions, observes results and updates its reasoning iteratively until a solution is reached. 
- This approach mimics human problem-solving and is effective across domains. 
- In practice, it requires managing previous prompts/responses, trimming extra content and providing appropriate examples or instructions.

### 4.9 Automatic Prompt Engineering

- Automatic Prompt Engineering (APE) automates the creation of prompts by having an LLM generate candidate prompts, which are then evaluated and refined. 
- The process involves: 
    1) prompting the model to produce multiple prompt variations, 
    2) scoring these candidates using metrics like BLEU or ROUGE and 
    3) selecting or tweaking the best-performing prompt for use in applications such as chatbots. 
- This iterative approach reduces human effort and can improve task performance.

### 4.10 Code Prompting

- Gemini specializes in text-based prompts, including those for generating code. 
- Users can test and experiment with these prompts in Vertex AI Studio to see practical coding examples.

#### 4.10.1 Prompt for writing code

- Gemini can act as a coding assistant, helping you quickly write scripts in any programming language. 
- For example, you can create a Bash script to rename hundreds of files in a folder. 
- By writing a prompt in Gemini or Vertex AI Studio, the model generates the code, which you can test on a small folder first. 
- Following the instructions, the script successfully renames all files as intended.

#### 4.10.2 Prompts for explaining code

- Gemini can assist developers in understanding existing code. 
- By providing the model with a script (e.g., from Table 16) and removing comments, you can prompt Gemini to explain the code’s functionality, making it easier to read and comprehend someone else’s work.

#### 4.10.3 Prompts for translating code

- The Bash file-renaming script works, but for reusability and better UI integration, Python is preferable. 
- LLMs can help translate Bash scripts into Python. 
- After generating the Python code (e.g., Table 18), you can save it as `file_renamer.py` and test it via the terminal. 
- In Vertex AI Language Studio, using the Markdown mode preserves Python indentation, which is crucial for proper execution.

#### 4.10.4 Prompts for debugging and reviewing code

- After manually modifying the Python script to prompt for a filename prefix in uppercase, errors occured. 
- Using an LLM to debug and review the code helped identify the bugs, provided fixes and offered addictional suggestions for improving the code overall.

#### 4.10.5 What about multimodal prompting?

- Multimodal prompting extends regular LLM prompting by using multiple input types, such as text, images, audio, or code, rather than just text. 
- It leverages the model’s ability to process different formats for more versatile and context-aware outputs.

## 5. Best Practices

- Finding effective prompts requires experimentation. 
- Vertex AI’s Language Studio provides a convenient environment to test prompts across different models, helping you refine and optimize them. 
- Best practices can guide you toward expert-level prompt engineering.

### 5.1 Provide examples

- A key best practice in prompt engineering is including one-shot or few-shot examples within your prompt. 
- These examples serve as references for the model, guiding it to produce outputs that better match the desired style, tone and accuracy.

### 5.2 Design with simplicity

- Prompts should be clear, concise and easy for both you and the model to understand. 
- Avoid unnecessary information or complex language. 
- Using action-oriented verbs (like *Act*, *Analyze*, *Describe*, *Generate*, *Summarize*) helps guide the model toward producing precise and relevant outputs.

### 5.3 Be specific about the output

- Be explicit about the desired output in your prompt. 
- Including specific instructions (e.g., length, style, tone, or focus) helps the LLM generate accurate and relevant responses, while vague or generic prompts can lead to less useful results.

### 5.4 Use Instructions over Constraints

- In prompts, **instructions** tell the LLM what to do (desired format, style, or content), while **constraints** set limits on what the model should avoid. 
- Positive instructions (focusing on what to do) are usually more effective than negative constraints, which can confuse the model. 
- Use constraints selectively (for safety, strict formats, or specific restrictions) and always prioritize clear instructions. 
- Iteration and documentation help refine prompts for the best results.

### 5.5 Control the max token length

- You can control an LLM’s response length.
- By setting a maximum token limit or by explicitly requesting a specific length in the prompt
- like, asking for a tweet-length explanation.

### 5.6 Use variables in prompts

- Using variables in prompts makes them reusable and dynamic. 
- Instead of hardcoding values (like a city name), variables allow the same prompt to adapt to different inputs, saving time, reducing repetition.
- And making prompts easier to integrate into applications.

### 5.7 Experiment with input formats and wiritng styles

- LLM outputs can vary based on the model, settings, prompt style, wording and prompt type. 
- Experimenting with different prompt formats (e.g., questions, statements, instructions; zero-shot vs. few-shot) helps achieve the desired results, as each formulation can lead to different responses even for the same topic.

### 5.8 For few-shot prompting with classification tasks, mix up the classes

- In few-shot prompting, example order usually doesn’t matter, but for classification tasks you should mix response classes to avoid overfitting to example order. 
- This helps the model learn true class features rather than memorizing patterns, leading to better generalization. 
- A good starting point is around six few-shot examples, then evaluate accuracy.

### 5.9 Adapt to model updates

- Stay up to date with model updates, new capabilities and data changes. 
- Regularly test newer model versions and refine your prompts to take advantage of improvements. 
- Tools like Vertex AI Studio help you store, test and document different prompt versions.

### 5.10 Experiment with output formats

- For non-creative tasks, experimenting with structured output formats like JSON or XML can improve reliability. 
- Using JSON enforces a consistent structure, reduces hallucinations, focuses the model on the required data, preserves relationships and data types and enables sorting. 
- This makes outputs easier to use directly in real-world applications.

### 5.11 JSON Repair

- Returning data in JSON is useful for structure and parsing, but it increases token usage, cost and the risk of hitting output limits. 
- When responses are truncated, the JSON may become invalid and unusable. 
- Tools like the json-repair library can help by automatically fixing incomplete or malformed JSON generated by LLMs.

### 5.12 Working with Schemas

- While JSON is commonly used for structured LLM output, it is also powerful for structuring input. 
- Using JSON Schemas defines expected fields, data types and relationships, helping the model better understand and focus on relevant information, reduce misinterpretation and even become time-aware through dates or timestamps. 
- Providing both a schema and schema-compliant data improves accuracy and relevance, especially for large datasets and complex applications.

### 5.13 Experiment together with other prompt engineers

- When designing a good prompt, having multiple people create prompts using best practices helps reveal performance differences and identify the most effective prompt through comparison.

### 5.14 CoT Best Practices

- In Chain of Thought (CoT) prompting, the reasoning must precede the final answer because the generated reasoning affects token prediction. 
- The final answer should be clearly extractable from the reasoning. 
- Since CoT uses greedy decoding and typically aims for a single correct answer, the temperature should always be set to 0.

### 5.15 Document the various prompt attempts

- Thoroughly documenting all prompt attempts is crucial, as outputs can vary across models, versions and even repeated runs. 
- Using a structured record—like a Google Sheet or Vertex AI Studio links—helps track iterations, results and feedback. 
- For RAG systems, include details about queries and content insertion. 
- Once prompts are refined, store them separately in your codebase and integrate automated testing. 
- Prompt engineering is iterative: continuously craft, test, document and refine prompts to achieve optimal results and adapt to model changes.
