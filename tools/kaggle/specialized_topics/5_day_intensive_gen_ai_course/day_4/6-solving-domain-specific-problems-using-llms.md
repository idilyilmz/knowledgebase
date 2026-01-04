# Solving Domain-Specific Problems Using LLMs

https://youtu.be/b1a4ZOQ8XdI?si=TcVsB-71E6Rmn2Dq

## 1. Introduction

- Large language models (LLMs) are increasingly being fine-tuned for **domain-specific applications**. 
- In **cybersecurity**, challenges like limited public data, technical complexity and rapidly changing threats require specialized models and techniques for tasks such as threat detection and risk analysis. 
- In **medicine**, the vast and evolving knowledge base demands context-aware reasoning for accurate diagnosis and treatment. 
- Domain-specific LLMs, such as **SecLM** for cybersecurity and **Med-PaLM** for medical applications, demonstrate the ability to enhance workflows, answer complex questions and provide actionable insights, highlighting the transformative potential of LLMs in specialized fields.

## 2. SecLM and the future of cybersecurity

- SecLM and specialized Generative AI can help cybersecurity professionals by 
    - **automating repetitive tasks**, 
    - reducing operational burden, 
    - and providing **faster access to knowledge**, 
- allowing practitioners to focus on strategic work amid evolving threats and talent shortages.

### 2.1 Challenges in cybersecurity

- Real-world cybersecurity faces three major challenges:
    1. **New and evolving threats**: Attackers constantly adopt sophisticated techniques, making it hard for defenders to stay current.
    2. **Operational toil**: Security professionals spend excessive time on repetitive, manual tasks, limiting their focus on strategic defenses.
    3. **Talent shortage**: There is a scarcity of skilled cybersecurity experts, leaving many roles undertrained or overburdened.
- These factors make it difficult for defenders to effectively protect complex systems against modern attacks.

### 2.2 How GenAI can tackle the challendes in cybersecurity

- Generative AI (GenAI), particularly large language models (LLMs), can help address key cybersecurity challenges across various roles by reducing repetitive work, assisting with complex tasks and providing actionable knowledge:
    - **Security Analysts:** Translate natural-language queries into security-specific languages, autonomously investigate and triage alerts and plan personalized remediation steps.
    - **Threat Researchers / SysAdmins:** Automate analysis of unknown artifacts through code de-obfuscation, reverse engineering and classification.
    - **CISO Teams:** Generate readable reports and slide decks summarizing threats using latest intelligence.
    - **IT Admins / Security Teams:** Identify potential attack paths and propose remediations.
    - **Application Developers:** Highlight where to fuzz-test code and generate test scripts.
    - **Administrators & Users:** Maintain least-privilege access configurations and receive authoritative guidance contextualized to their environment.
- A **multi-layered approach** enhances effectiveness:
    1. **Top layer:** Existing security tools for context-aware actions.
    2. **Middle layer:** Security-specialized LLM API with reasoning, planning and tool use.
    3. **Bottom layer:** Datastores of authoritative security intelligence.
- The **SecLM API** integrates these layers, combining reasoning, Retrieval-Augmented Generation (RAG) to ground outputs in verified data and tool use to act or retrieve information, providing a holistic solution to complex cybersecurity challenges.

### 2.3 SecLM: An API for cubersecurity tasks

- The **SecLM API** is designed as a comprehensive, “one-stop” solution for cybersecurity tasks, allowing engineers and analysts to ask complex security questions in natural language and receive high-quality, actionable responses. Key design goals include:
    - **Freshness**: Access to up-to-date threat and vulnerability information without needing constant retraining.
    - **User-specific data**: Secure handling of sensitive data within the user’s environment, avoiding exposure to others or centralized systems.
    - **Security expertise**: Understanding and decomposition of high-level security concepts (e.g., attack strategies) into actionable components.
    - **Multi-step reasoning**: Combining multiple data sources, tools and specialized models to solve complex security problems.
- SecLM achieves this by integrating **security-specialized LLMs**, traditional ML models and a **flexible planning framework** that enables dynamic tool use and collaboration between domain-specialized agents, ensuring accurate and context-aware cybersecurity solutions.

#### 2.3.1 Security-focused large language models

- General-purpose LLMs struggle with cybersecurity tasks due to:
    1. **Limited security data**: Most security data is sensitive or proprietary, with little publicly available information for training.
    2. **Technical depth**: Security requires knowledge spanning low-level CS concepts to high-level policy and intelligence analysis.
    3. **Sensitive use cases**: Tasks like malware or phishing analysis are avoided by general-purpose LLMs but are critical for defenders.
- To address these, **security-specialized LLMs** are developed with targeted training:
    - **Pre-training**: Start with a robust foundational model on broad general text, code and structured data for multilingual support and general capabilities.
    - **Continued pre-training**: Incorporate open-source and licensed cybersecurity content (blogs, threat intelligence, IT books) to develop domain-specific language understanding.
    - **Fine-tuning**: Supervised training on task-specific datasets mirroring real-world security work (malware analysis, command-line interpretation, security event summarization, threat intelligence query generation). Proprietary data is isolated for security-sensitive tasks.
- **Evaluation**:
    - Classification metrics for quantifiable tasks (e.g., malware detection).
    - Similarity metrics (ROUGE, BLEU, BERTScore) and automated side-by-side comparisons for less structured tasks.
    - Expert human evaluation for accuracy and relevance.
- **Post-training enhancements**:
    - **In-context learning**: Helps the model generalize to unseen security platforms.
    - **Parameter-efficient tuning (PET)**: Integrates user-specific or sensitive data without retraining the core model.
    - **Retrieval-augmented generation (RAG)**: Provides the model with the latest threat intelligence in real-time.
- This approach produces LLMs capable of performing core security tasks with expert-level reasoning, while remaining adaptable to new platforms, threats and user environments. 

#### 2.3.2 A flexible planning and reasoning framework

- SecLM’s framework orchestrates complex, multi-step cybersecurity tasks by combining specialized LLMs, authoritative data and user-specific information. Key points:
    - **Multi-step planning**: For example, answering questions about an APT group like “APT41” involves retrieving threat intelligence, extracting TTPs and indicators, translating them into SIEM queries and aggregating results for the analyst.
    - **Automation**: SecLM automates repetitive, time-consuming tasks across multiple systems, freeing analysts to focus on follow-up investigations or remediation.
    - **Tool and model integration**: The framework leverages retrieval-augmented generation, code execution, specialized models (fine-tuned with PET) and long-term memory to handle complex operations.
    - **Real-world validation**: Side-by-side comparisons with general-purpose LLMs showed SecLM outperforms on cybersecurity tasks such as attack path analysis, alert summarization and script analysis, with win rates of 53–79%.
    - **Holistic platform**: By combining LLM reasoning, authoritative data and flexible orchestration, SecLM provides a comprehensive platform that supports experts, junior analysts and system administrators, reducing toil while improving accuracy and efficiency.
- In essence, SecLM acts as an intelligent, autonomous assistant for cybersecurity, turning complex multi-system processes into streamlined, actionable insights.

## 3. MedLM and the future of health tech

- MedLM represents a family of foundation models specifically fine-tuned for healthcare applications. 
- Building on advances in AI and NLP, these models, starting with Med-PaLM, aim to tackle the unique challenges of the medical field, including complex, context-dependent knowledge, rapidly evolving information and the need for precise, reliable guidance. 
- MedLM solutions support clinicians, researchers and patients by providing domain-specialized insights, improving workflows and enabling new possibilities in health technology.

### 3.1 The potential for GenAI in medical Q & A

- Medical question-answering (QA) is a complex AI challenge due to the vast, evolving and nuanced nature of medical knowledge. 
- Large language models (LLMs) trained on extensive datasets have shown strong performance on medical QA benchmarks, demonstrating an ability to understand and apply intricate medical concepts. 
- With growing access to medical data (from textbooks and research papers to patient records) models like Med-PaLM (fine-tuned from the PaLM family) can leverage these resources to provide accurate, context-aware answers, supporting clinicians, researchers and other healthcare stakeholders in improving health outcomes.

### 3.2 The opportunities

- Generative AI offers transformative potential in healthcare across diagnostic and non-diagnostic tasks. Key opportunities include:
    - **Personalized guidance**: Answering patient questions in the context of their medical history.
    - **Message triage**: Categorizing and prioritizing incoming patient communications for clinicians.
    - **Adaptive patient intake**: Dynamically adjusting questions based on patient responses for more comprehensive data collection.
    - **Real-time feedback**: Monitoring patient-clinician interactions to provide actionable insights for both parties.
    - **Clinical support**: Offering on-demand consults or reference material to help clinicians handle unfamiliar cases or diseases.
- Due to patient safety concerns, these innovations require careful, phased validation (from retrospective studies using de-identified data to prospective studies) before integration into clinical practice.

### 3.3 The scientific starting point

- Traditional AI in medicine often produces rigid outputs like “yes/no” or numbers, limiting flexibility and slowing innovation. Google’s approach emphasizes **human-centric**, **interactive AI** that can assist across diverse medical scenarios while incorporating context, empathy and expertise.
    - **Goal**: Enhance AI effectiveness, helpfulness and safety in medicine using natural language interaction for clinicians, researchers and patients.
    - **Approach**: Use foundation models (LLMs) to create flexible, domain-adaptable systems.
    - **Med-PaLM Development**:
        - **Med-PaLM (2022)**: First AI to exceed passing scores on USMLE-style questions; evaluated on reasoning and long-form answers.
        - **Med-PaLM 2 (2023)**: Significant improvement, 86.5% accuracy on USMLE-style questions, 19% higher than the previous version; long-form answers assessed by physicians showed substantial quality gains.
- These advances illustrate that **domain-specific fine-tuning of LLMs** enables robust, interactive medical AI capable of providing authoritative, nuanced answers.

#### 3.3.1 How to evaluate: wyantative and qualitative

- Evaluating medical AI systems like Med-PaLM requires both **quantitative** and **qualitative** methods to measure performance and real-world utility.
- **Quantitative Evaluation**:
    - **USMLE-style questions** serve as a benchmark, requiring comprehension of patient data, reasoning and selection of correct answers.
    - **Performance milestones**: Med-PaLM first exceeded the passing mark at 67%, while Med-PaLM 2 reached 86.5%, reflecting expert-level performance.
    - **Advantages**: Standardized, programmatically scorable and widely accepted in the medical community.
- **Qualitative Evaluation**:
    - Focuses on **long-form answers** assessing factuality, reasoning, helpfulness, equity and potential harm.
    - Expert clinicians evaluate outputs using a detailed rubric, including comprehension, recall, reasoning correctness, relevance, omissions and applicability to specific medical demographics.
    - Evaluation procedure:
        - AI and physicians independently answer questions.
        - Responses are presented in a **blinded fashion** for side-by-side comparison.
        - Emphasis is on substance over style.
- **Insights**:
    - Human evaluation is resource-intensive but critical for assessing real-world clinical utility.
    - Med-PaLM outputs compare favorably with physician responses across multiple axes, though certain areas still require improvement.
    - Combining quantitative benchmarks with qualitative expert review provides a robust framework to guide future model improvements while ensuring safety and clinical relevance.

### 3.4 Evaluation in real clinical environments

- Validating AI technologies like Med-PaLM in real clinical settings is critical, as strong performance on retrospective datasets does not guarantee real-world effectiveness. Key evaluation steps include:
    1. **Retrospective evaluation**: Testing the technology on historical patient data to gauge baseline performance.
    2. **Prospective observational (non-interventional)**: Evaluating the AI on newly collected data without impacting patient care, often with expert review of outputs.
    3. **Prospective interventional**: Deploying the technology in live clinical workflows with patient consent, under IRB-approved protocols, to assess actual impact on care and outcomes.
- These steps ensure robustness, safety and practical integration, highlighting that real-world deployment may require workflow adjustments to maximize the benefits of AI in clinical practice.

### 3.5 Task- vs. domain-specific models

- Med-PaLM and Med-PaLM 2 demonstrate the value of domain-specific models in medicine, achieving much higher reasoning accuracy compared to general-purpose models. However, success on one medical task does not automatically translate to other tasks—each task, such as mental health assessments, requires validation and possibly adaptation.
- Medicine is inherently multimodal, involving not just text but also images, EHRs, sensors, wearables and genomics. 
- Early multimodal MedLM approaches are being researched with the same principles of validation and workflow integration.
- Specialized medical models are useful beyond direct patient care, including applications like scientific discovery (e.g., gene-trait associations). 
- With MedLM, a suite of healthcare-focused models built on Med-PaLM 2, organizations can safely and responsibly deploy GenAI solutions tailored to clinical and research workflows.

### 3.6 Training strategies for Med-PaLM 2

- Med-PaLM 2 is a medical-specialized variant of Google’s PaLM 2 LLM, fine-tuned using medical QA datasets such as MultiMedQA (MedQA, MedMCQA, HealthSearchQA, LiveQA, MedicationQA). 
- Empirical dataset mixture ratios were used to optimize training.
- To improve reasoning and performance on multiple-choice questions, several prompting strategies were applied:
    - **Few-shot prompting**: providing examples in the prompt.
    - **Chain-of-Thought (CoT) prompting**: including step-by-step reasoning in examples for multi-step problem solving.
    - **Self-consistency**: sampling multiple model outputs and selecting the majority-vote answer.
- Additionally, Ensemble Refinement (ER) was introduced: the model generates multiple answers in the first stage, then reconditions on those outputs to produce a refined final answer. 
- This enhances performance, particularly on complex queries without a fixed answer set.
- The research emphasizes that achieving expert-level performance in medical QA is only the first step. 
- Success relies on careful evaluation, collaboration with clinicians and consideration of real-world clinical applications, patient privacy and workflow integration. 
- Domain-specific models like Med-PaLM 2 are expected to continue outperforming general-purpose models in specialized tasks.