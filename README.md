<h1 align="center">🧠 Memory is Awesome</h1>

<p align="center">
  <strong>Your Guide to Memory in Foundation Model Agents</strong>
</p>

<p align="center">
  <em>"Without memory, there is no culture. Without memory, there would be no civilization, no society, no future."</em><br/>
  — Elie Wiesel
</p>

---

## 📖 Table of Contents

- [Introduction](#-introduction)
- [What is Agent Memory?](#-what-is-agent-memory)
- [Unified Taxonomy](#-unified-taxonomy)
  - [Memory Forms](#-memory-forms-what-carries-memory)
  - [Memory Functions](#-memory-functions-why-agents-need-memory)
  - [Memory Dynamics](#-memory-dynamics-how-memory-evolves)
- [Paper Collection](#-paper-collection)
  - [Factual Memory](#-factual-memory)
  - [Experiential Memory](#-experiential-memory)
  - [Working Memory](#-working-memory)
- [Benchmarks & Evaluation](#-benchmarks--evaluation)
- [Open-Source Frameworks](#-open-source-frameworks)
- [Applications](#-applications)
- [Future Directions](#-future-directions)
- [Citation](#-citation)
- [Contributing](#-contributing)

---

## 🎯 Introduction

Large Language Model (LLM) based agents have emerged as a transformative paradigm in AI research. Unlike vanilla LLMs, these agents possess **self-evolving capabilities** that enable them to solve real-world problems requiring long-term, complex interactions with their environment.

**Memory** is the cornerstone of foundation model-based agents—it's what makes an agent truly an *agent*. Memory underpins the ability to perform long-horizon reasoning, adapt continually, and interact effectively with complex environments.

This repository synthesizes insights from major surveys on agent memory:

| Survey | Year | Links |
|--------|------|-------|
| A Survey on the Memory Mechanism of Large Language Model based Agents | 2024 | [[arXiv]](https://arxiv.org/abs/2404.13501) [[GitHub]](https://github.com/nuster1128/LLM_Agent_Memory_Survey) |
| Memory in the Age of AI Agents | 2025 | [[arXiv]](https://arxiv.org/abs/2512.13564) [[GitHub]](https://github.com/Shichun-Liu/Agent-Memory-Paper-List) |

---

## 🧩 What is Agent Memory?

### Conceptual Distinction

Agent Memory is distinct from related concepts:

| Concept | Description | Key Difference |
|---------|-------------|----------------|
| **LLM Memory** | Knowledge encoded in model weights during pre-training | Static, not updated during deployment |
| **RAG** | Retrieval from external knowledge bases | Typically for single-task QA, static corpus |
| **Context Engineering** | Managing prompt context windows | Focus on immediate context, not persistence |
| **Agent Memory** | Dynamic, persistent storage for agent experiences | Supports long-horizon tasks, self-evolution |

### Definition Perspectives

| Perspective | Definition |
|-------------|------------|
| **Narrow** | The actions and observations within a single trial (complete agent-environment interaction sequence) |
| **Broad** | Information from current trial, past trials, AND external knowledge sources |

<!-- 
📌 FIGURE RECOMMENDATION #1: Use this figure to illustrate the conceptual comparison
Source: https://github.com/Shichun-Liu/Agent-Memory-Paper-List/blob/main/assets/concept.png
This figure clearly shows the distinction between Agent Memory, LLM Memory, RAG, and Context Engineering
-->

---

## 🗂️ Unified Taxonomy

We organize agent memory research through three unified lenses: **Forms**, **Functions**, and **Dynamics**.

<!-- 
📌 FIGURE RECOMMENDATION #2: Use this main taxonomy figure
Source: https://github.com/Shichun-Liu/Agent-Memory-Paper-List/blob/main/assets/main.png
This is the central figure showing Forms × Functions × Dynamics framework
-->

---

### 📦 Memory Forms (What Carries Memory?)

Memory forms categorize HOW information is stored and represented.

| Form | Description | Characteristics |
|------|-------------|-----------------|
| **🔤 Token-level** | Explicit, discrete text/symbols stored externally | Human-readable, interpretable, easy to update |
| **⚙️ Parametric** | Implicit knowledge encoded in model weights | Requires fine-tuning, permanent storage |
| **🧬 Latent** | Compressed representations in hidden states | Efficient, compact, less interpretable |

#### 🔤 Token-level Memory

> 💡 **Why use it?** Token-level memory is human-readable and interpretable, making it easy to debug, update, and audit. It allows for flexible retrieval strategies and can be shared across different models without retraining.

**Subtypes:**

| Type | Description | Use Case |
|------|-------------|----------|
| **Complete Interactions** | Store all past agent-environment interactions | Full audit trail, comprehensive history |
| **Recent Interactions** | Prioritize most recent, relevant data | Conversational agents, sliding window |
| **Retrieved Interactions** | Select memories based on relevance | Long-term personalization, large-scale memory |
| **External Knowledge** | Access to databases, APIs, documents | Domain expertise, factual grounding |

#### ⚙️ Parametric Memory

> 💡 **Why use it?** Parametric memory enables permanent knowledge storage that doesn't require retrieval at inference time. It's ideal for domain-specific adaptation and can capture nuanced patterns that are difficult to express in text.

| Method | Description |
|--------|-------------|
| **Fine-tuning** | Train on domain data to embed knowledge |
| **Knowledge Editing** | Surgically update specific facts in weights |
| **Adapter Methods** | Add trainable modules (LoRA, K-Adapter) |

#### 🧬 Latent Memory

> 💡 **Why use it?** Latent memory provides highly efficient storage with minimal overhead. It's particularly effective for working memory scenarios where information needs to be quickly accessed and doesn't need to be human-interpretable.

| Approach | Description |
|----------|-------------|
| **KV-Cache Compression** | Reduce key-value cache size for efficiency |
| **Memory Tokens** | Learn special tokens for memory representation |
| **Hidden State Caching** | Store intermediate representations |

---

### 🎯 Memory Functions (Why Agents Need Memory?)

Memory functions categorize WHAT purpose the memory serves.

| Function | Description | Cognitive Parallel |
|----------|-------------|-------------------|
| **📚 Factual Memory** | Stores knowledge, facts, and user preferences | Semantic memory |
| **🎓 Experiential Memory** | Stores insights, skills, and learned procedures | Episodic + Procedural memory |
| **⚡ Working Memory** | Active context management during tasks | Working memory |

<!-- 
📌 FIGURE RECOMMENDATION #3: Use this figure for memory sources
Source: Your existing figure showing Inside-trial, Cross-trial, and External Knowledge
This illustrates the three sources of memory information
-->

---

### 🔄 Memory Dynamics (How Memory Evolves?)

Memory dynamics describe the operational lifecycle of memory.

<!-- 
📌 FIGURE RECOMMENDATION #4: Use this figure for agent-environment interaction
Source: Your existing figure showing the W (Write), P (Process), R (Read) cycle
This shows how agents interact with memory during task execution
-->

| Phase | Symbol | Description | Strategies |
|-------|--------|-------------|------------|
| **Formation (Writing)** | W | How memories are created and stored | Direct storage, summarization, structured extraction |
| **Evolution (Management)** | P | How memories are maintained over time | Consolidation, forgetting, reflection, compression |
| **Retrieval (Reading)** | R | How memories are accessed when needed | Recency-based, relevance-based, importance-based, hybrid |

---

## 📚 Paper Collection

### 📚 Factual Memory

Stores knowledge, facts, user preferences, and world knowledge.

> 💡 **Why use Factual Memory?** Factual memory allows agents to maintain consistent knowledge about users, domains, and the world. It enables personalization, reduces repetitive queries, and ensures agents can provide accurate, up-to-date information across sessions.

#### Token-level Factual Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | O-Mem: Omni Memory System for Personalized, Long Horizon, Self-Evolving Agents | [[arXiv]](https://arxiv.org/abs/2511.13593) |
| 2025 | Zep: A Temporal Knowledge Graph Architecture for Agent Memory | [[arXiv]](https://arxiv.org/abs/2501.13956) |
| 2025 | A-MEM: Agentic Memory for LLM Agents | [[arXiv]](https://arxiv.org/abs/2502.12110) |
| 2025 | Mem0: Building Production-Ready AI Agents with Scalable Long-Term Memory | [[arXiv]](https://arxiv.org/abs/2504.19413) [[GitHub]](https://github.com/mem0ai/mem0) |
| 2025 | Memory-R1: Enhancing LLM Agents to Manage and Utilize Memories via RL | [[arXiv]](https://arxiv.org/abs/2508.19828) |
| 2025 | From RAG to Memory: Non-Parametric Continual Learning for LLMs | [[arXiv]](https://arxiv.org/abs/2502.14802) |
| 2025 | ENGRAM: Effective, Lightweight Memory Orchestration for Conversational Agents | [[arXiv]](https://arxiv.org/abs/2511.12960) |
| 2025 | SGMem: Sentence Graph Memory for Long-Term Conversational Agents | [[arXiv]](https://arxiv.org/abs/2509.21212) |
| 2025 | Nemori: Self-Organizing Agent Memory Inspired by Cognitive Science | [[arXiv]](https://arxiv.org/abs/2508.03341) |
| 2024 | HippoRAG: Neurobiologically Inspired Long-Term Memory for LLMs | [[arXiv]](https://arxiv.org/abs/2405.14831) [[GitHub]](https://github.com/OSU-NLP-Group/HippoRAG) |
| 2024 | From Local to Global: A Graph RAG Approach to Query-Focused Summarization | [[arXiv]](https://arxiv.org/abs/2404.16130) |
| 2024 | From Isolated Conversations to Hierarchical Schemas: Dynamic Tree Memory | [[arXiv]](https://arxiv.org/abs/2410.14052) |
| 2024 | OASIS: Open Agent Social Interaction Simulations with One Million Agents | [[arXiv]](https://arxiv.org/abs/2411.11581) |
| 2024 | Crafting Personalized Agents through RAG on Editable Memory Graphs | [[arXiv]](https://arxiv.org/abs/2409.19401) |
| 2024 | AriGraph: Learning Knowledge Graph World Models with Episodic Memory | [[arXiv]](https://arxiv.org/abs/2407.04363) |
| 2024 | Toward Conversational Agents with Context and Time Sensitive Long-term Memory | [[arXiv]](https://arxiv.org/abs/2406.00057) |
| 2024 | Enhancing Long-Term Memory using Hierarchical Aggregate Tree for RAG | [[arXiv]](https://arxiv.org/abs/2406.06124) |
| 2024 | Towards Lifelong Dialogue Agents via Timeline-based Memory Management | [[arXiv]](https://arxiv.org/abs/2406.10996) |
| 2024 | Memory Sharing for Large Language Model based Agents | [[arXiv]](https://arxiv.org/abs/2404.09982) |
| 2024 | Knowledge Graph Tuning: Real-time LLM Personalization based on Human Feedback | [[arXiv]](https://arxiv.org/abs/2405.19686) |
| 2024 | AI PERSONA: Towards Life-long Personalization of LLMs | [[arXiv]](https://arxiv.org/abs/2412.13103) |
| 2023 | MemGPT: Towards LLMs as Operating Systems | [[arXiv]](https://arxiv.org/abs/2310.08560) [[GitHub]](https://github.com/cpacker/MemGPT) |
| 2023 | Generative Agents: Interactive Simulacra of Human Behavior | [[arXiv]](https://arxiv.org/abs/2304.03442) [[GitHub]](https://github.com/joonspk-research/generative_agents) |
| 2023 | MemoryBank: Enhancing LLMs with Long-Term Memory | [[arXiv]](https://arxiv.org/abs/2305.10250) [[GitHub]](https://github.com/zhongwanjun/MemoryBank-SiliconFriend) |
| 2023 | RET-LLM: Towards a General Read-Write Memory for LLMs | [[arXiv]](https://arxiv.org/abs/2305.14322) |
| 2023 | SCM: Enhancing LLMs with Self-Controlled Memory Framework | [[arXiv]](https://arxiv.org/abs/2304.13343) [[GitHub]](https://github.com/wbbeyourself/scm4llms) |
| 2023 | MemoChat: Tuning LLMs to Use Memos for Consistent Long-Range Conversation | [[arXiv]](https://arxiv.org/abs/2308.08239) [[GitHub]](https://github.com/LuJunru/MemoChat) |
| 2023 | Prompted LLMs as Chatbot Modules for Long Open-domain Conversation | [[GitHub]](https://github.com/krafton-ai/MPC) |
| 2023 | MetaGPT: Meta Programming for Multi-Agent Collaborative Framework | [[arXiv]](https://arxiv.org/abs/2308.00352) |
| 2023 | S³: Social-network Simulation System with LLM-Empowered Agents | [[arXiv]](https://arxiv.org/abs/2307.14984) |
| 2023 | Think-in-Memory: Recalling and Post-thinking enable LLMs with Long-term Memory | [[arXiv]](https://arxiv.org/abs/2311.08719) |
| 2023 | RecurrentGPT: Interactive Generation of (Arbitrarily) Long Text | [[arXiv]](https://arxiv.org/abs/2305.13304) |
| 2023 | ChatDB: Augmenting LLMs with Databases as Their Symbolic Memory | [[Website]](https://chatdatabase.github.io/) |
| 2023 | Recursively Summarizing Enables Long-Term Dialogue Memory in LLMs | [[arXiv]](https://arxiv.org/abs/2308.15022) |

#### Parametric Factual Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | WISE: Rethinking Knowledge Memory for Lifelong Model Editing | [[arXiv]](https://arxiv.org/abs/2405.14768) |
| 2025 | ELDER: Enhancing Lifelong Model Editing with Mixture-of-LoRA | [[arXiv]](https://arxiv.org/abs/2408.11869) |
| 2025 | Online Adaptation of Language Models with a Memory of Amortized Contexts | [[arXiv]](https://arxiv.org/abs/2403.04317) |
| 2024 | AlphaEdit: Null-Space Constrained Knowledge Editing for LMs | [[arXiv]](https://arxiv.org/abs/2410.02355) |
| 2024 | Character-LLM: A Trainable Agent for Role-Playing | [[arXiv]](https://arxiv.org/abs/2310.10158) [[GitHub]](https://github.com/choosewhatulike/trainable-agents) |
| 2023 | HuaTuo: Tuning LLaMA Model with Chinese Medical Knowledge | [[arXiv]](https://arxiv.org/abs/2304.06975) |
| 2023 | K-Adapter: Infusing Knowledge into Pre-Trained Models with Adapters | [[arXiv]](https://arxiv.org/abs/2002.01808) |
| 2022 | Fast Model Editing at Scale (MEND) | [[arXiv]](https://arxiv.org/abs/2110.11309) |
| 2021 | Editing Factual Knowledge in Language Models (ROME) | [[arXiv]](https://arxiv.org/abs/2104.08164) |

#### Latent Factual Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | Memory³: Language Modeling with Explicit Memory | [[arXiv]](https://arxiv.org/abs/2407.01178) |
| 2025 | M+: Extending MemoryLLM with Scalable Long-Term Memory | [[arXiv]](https://arxiv.org/abs/2502.00592) |
| 2025 | R3Mem: Bridging Memory Retention and Retrieval via Reversible Compression | [[arXiv]](https://arxiv.org/abs/2502.15957) |
| 2024 | Efficient Episodic Memory Utilization of Cooperative Multi-Agent RL | [[arXiv]](https://arxiv.org/abs/2403.01911) |

---

### 🎓 Experiential Memory

Stores insights, learned skills, and procedural knowledge from past experiences.

> 💡 **Why use Experiential Memory?** Experiential memory enables agents to learn from successes and failures, accumulate reusable skills, and improve performance over time. It transforms agents from stateless responders into continuously evolving systems that get better with experience.

#### Token-level Experiential Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | Agent Workflow Memory | [[arXiv]](https://arxiv.org/abs/2409.07429) |
| 2025 | SkillWeaver: Web Agents can Self-Improve by Discovering and Honing Skills | [[arXiv]](https://arxiv.org/abs/2504.07079) |
| 2025 | Darwin Godel Machine: Open-Ended Evolution of Self-Improving Agents | [[arXiv]](https://arxiv.org/abs/2505.22954) |
| 2025 | Buffer of Thoughts: Thought-Augmented Reasoning with LLMs | [[arXiv]](https://arxiv.org/abs/2406.04271) |
| 2025 | JARVIS-1: Open-World Multi-Task Agents With Memory-Augmented Multimodal LMs | [[arXiv]](https://arxiv.org/abs/2311.05997) |
| 2025 | Memento: Fine-tuning LLM Agents without Fine-tuning LLMs | [[arXiv]](https://arxiv.org/abs/2508.16153) |
| 2025 | Agent KB: Leveraging Cross-Domain Experience for Agentic Problem Solving | [[arXiv]](https://arxiv.org/abs/2507.06229) |
| 2025 | Memp: Exploring Agent Procedural Memory | [[arXiv]](https://arxiv.org/abs/2508.06433) |
| 2025 | SEAgent: Self-Evolving Computer Use Agent with Autonomous Learning | [[arXiv]](https://arxiv.org/abs/2508.04700) |
| 2025 | FLEX: Continuous Agent Evolution via Forward Learning from Experience | [[arXiv]](https://arxiv.org/abs/2511.06449) |
| 2025 | Scaling Agent Learning via Experience Synthesis | [[arXiv]](https://arxiv.org/abs/2511.03773) |
| 2025 | LEGOMem: Modular Procedural Memory for Multi-agent LLM Systems | [[arXiv]](https://arxiv.org/abs/2510.04851) |
| 2025 | ReasoningBank: Scaling Agent Self-Evolving with Reasoning Memory | [[arXiv]](https://arxiv.org/abs/2509.25140) |
| 2025 | Dynamic Cheatsheet: Test-Time Learning with Adaptive Memory | [[arXiv]](https://arxiv.org/abs/2504.07952) |
| 2025 | From Exploration to Mastery: Enabling LLMs to Master Tools via Self-Driven Interactions | [[arXiv]](https://arxiv.org/abs/2410.08197) |
| 2024 | ExpeL: LLM Agents Are Experiential Learners | [[arXiv]](https://arxiv.org/abs/2308.10144) [[GitHub]](https://github.com/LeapLabTHU/ExpeL) |
| 2024 | RepairAgent: An Autonomous, LLM-Based Agent for Program Repair | [[arXiv]](https://arxiv.org/abs/2403.17134) |
| 2024 | Fincon: A Synthesized LLM Multi-Agent System for Financial Decision Making | [[arXiv]](https://arxiv.org/abs/2407.06567) |
| 2023 | Reflexion: Language Agents with Verbal Reinforcement Learning | [[arXiv]](https://arxiv.org/abs/2303.11366) [[GitHub]](https://github.com/noahshinn/reflexion) |
| 2023 | Voyager: An Open-Ended Embodied Agent with LLMs | [[arXiv]](https://arxiv.org/abs/2305.16291) [[Website]](https://voyager.minedojo.org/) |
| 2023 | Ghost in the Minecraft: Generally Capable Agents for Open-World Environments | [[arXiv]](https://arxiv.org/abs/2305.17144) [[GitHub]](https://github.com/OpenGVLab/GITM) |
| 2023 | ToolLLM: Facilitating LLMs to Master 16000+ Real-world APIs | [[arXiv]](https://arxiv.org/abs/2307.16789) |
| 2023 | RecMind: Large Language Model Powered Agent For Recommendation | [[arXiv]](https://arxiv.org/abs/2308.14296) |
| 2023 | CREATOR: Tool Creation for Disentangling Abstract and Concrete Reasoning | [[arXiv]](https://arxiv.org/abs/2305.14318) |
| 2023 | Toolformer: Language Models Can Teach Themselves to Use Tools | [[arXiv]](https://arxiv.org/abs/2302.04761) |
| 2023 | Synapse: Trajectory-as-Exemplar Prompting with Memory for Computer Control | [[Website]](https://ltzheng.github.io/Synapse/) |

#### Parametric Experiential Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | AgentEvolver: Towards Efficient Self-Evolving Agent System | [[arXiv]](https://arxiv.org/abs/2511.10395) |
| 2025 | Agent Learning via Early Experience | [[arXiv]](https://arxiv.org/abs/2510.08558) |
| 2025 | Scaling Agents via Continual Pre-training | [[arXiv]](https://arxiv.org/abs/2509.13310) |
| 2024 | ToolGen: Unified Tool Retrieval and Calling via Generation | [[arXiv]](https://arxiv.org/abs/2410.03439) |
| 2023 | Retroformer: Retrospective Large Language Agents with Policy Gradient Optimization | [[arXiv]](https://arxiv.org/abs/2308.02151) [[GitHub]](https://github.com/weirayao/Retroformer) |
| 2023 | A Machine with Short-Term, Episodic, and Semantic Memory Systems | [[arXiv]](https://arxiv.org/abs/2212.02098) |

#### Latent Experiential Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | Auto-scaling Continuous Memory for GUI Agent | [[arXiv]](https://arxiv.org/abs/2510.09038) |

---

### ⚡ Working Memory

Manages active context during task execution.

> 💡 **Why use Working Memory?** Working memory enables agents to handle long-horizon tasks by maintaining relevant context without overwhelming the context window. It's essential for complex reasoning, multi-step planning, and tasks that exceed the model's native context length.

#### Token-level Working Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | Memory as Action: Autonomous Context Curation for Long-Horizon Tasks | [[arXiv]](https://arxiv.org/abs/2510.12635) |
| 2025 | AgentFold: Long-Horizon Web Agents with Proactive Context Management | [[arXiv]](https://arxiv.org/abs/2510.24699) |
| 2025 | ACON: Optimizing Context Compression for Long-Horizon LLM Agents | [[arXiv]](https://arxiv.org/abs/2510.00615) |
| 2025 | MemSearcher: Training LLMs to Reason, Search and Manage Memory via RL | [[arXiv]](https://arxiv.org/abs/2511.02805) |
| 2025 | IterResearch: Rethinking Long-Horizon Agents via Markovian State Reconstruction | [[arXiv]](https://arxiv.org/abs/2511.07327) |
| 2025 | PRIME: Planning and Retrieval-Integrated Memory for Enhanced Reasoning | [[arXiv]](https://arxiv.org/abs/2509.22315) |
| 2025 | DeepAgent: A General Reasoning Agent with Scalable Toolsets | [[arXiv]](https://arxiv.org/abs/2510.21618) |
| 2025 | ReSum: Unlocking Long-Horizon Search Intelligence via Context Summarization | [[arXiv]](https://arxiv.org/abs/2509.13313) |
| 2025 | MemAgent: Reshaping Long-Context LLM with Multi-Conv RL-based Memory Agent | [[arXiv]](https://arxiv.org/abs/2507.02259) |
| 2024 | Agent S: An Open Agentic Framework That Uses Computers Like a Human | [[arXiv]](https://arxiv.org/abs/2410.08164) |

#### Parametric Working Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | Various Lengths, Constant Speed: Efficient Language Modeling with Lightning Attention | [[arXiv]](https://arxiv.org/abs/2405.17381) |
| 2024 | Efficient Streaming Language Models with Attention Sinks | [[arXiv]](https://arxiv.org/abs/2309.17453) |

#### Latent Working Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | Titans: Learning to Memorize at Test Time | [[arXiv]](https://arxiv.org/abs/2501.00663) |
| 2025 | MemoRAG: Boosting Long Context Processing with Global Memory-Enhanced RAG | [[arXiv]](https://arxiv.org/abs/2409.05591) |
| 2025 | LM2: Large Memory Models | [[arXiv]](https://arxiv.org/abs/2502.06049) |
| 2025 | MemGen: Weaving Generative Latent Memory for Self-Evolving Agents | [[arXiv]](https://arxiv.org/abs/2509.24704) |
| 2025 | MEM1: Learning to Synergize Memory and Reasoning for Efficient Long-Horizon Agents | [[arXiv]](https://arxiv.org/abs/2506.15841) |
| 2025 | MemoryVLA: Perceptual-Cognitive Memory in Vision-Language-Action Models | [[arXiv]](https://arxiv.org/abs/2508.19236) |
| 2024 | H2O: Heavy-Hitter Oracle for Efficient Generative Inference | [[arXiv]](https://arxiv.org/abs/2306.14048) |
| 2024 | SnapKV: LLM Knows What You are Looking for Before Generation | [[arXiv]](https://arxiv.org/abs/2404.14469) |
| 2024 | RazorAttention: Efficient KV Cache Compression Through Retrieval Heads | [[arXiv]](https://arxiv.org/abs/2407.15891) |
| 2024 | Adapting Language Models to Compress Contexts | [[arXiv]](https://arxiv.org/abs/2305.14788) |
| 2024 | Focused Transformer: Contrastive Training for Context Scaling | [[arXiv]](https://arxiv.org/abs/2307.03170) |
| 2023 | Learning to Compress Prompts with Gist Tokens | [[arXiv]](https://arxiv.org/abs/2304.08467) |
| 2023 | In-Context Autoencoder for Context Compression in LLMs | [[arXiv]](https://arxiv.org/abs/2307.06945) |
| 2023 | Scissorhands: Exploiting the Persistence of Importance Hypothesis for LLM KV Cache Compression | [[arXiv]](https://arxiv.org/abs/2305.17118) |
| 2023 | Augmenting Language Models with Long-Term Memory | [[arXiv]](https://arxiv.org/abs/2306.07174) |
| 2022 | Memorizing Transformers | [[arXiv]](https://arxiv.org/abs/2203.08913) |

---

## 📊 Benchmarks & Evaluation

### Memory Evaluation Benchmarks

| Benchmark | Focus | Context Length | Links |
|-----------|-------|----------------|-------|
| **LoCoMo** | Very long-term conversational memory | ~9K tokens, 35 sessions | [[arXiv]](https://arxiv.org/abs/2402.17753) [[Website]](https://snap-research.github.io/locomo/) |
| **LongMemEval** | Long-term interactive memory | ~115K-1.5M tokens | [[arXiv]](https://arxiv.org/abs/2410.10813) [[GitHub]](https://github.com/xiaowu0162/LongMemEval) |
| **MemoryBench** | Memory and continual learning | Various | [[arXiv]](https://arxiv.org/abs/2510.17281) |
| **MemoryAgentBench** | Incremental multi-turn interactions | Various | [[arXiv]](https://arxiv.org/abs/2507.05257) |

### Evaluation Metrics

| Metric | Description |
|--------|-------------|
| **F1 Score** | Token-level overlap between predicted and ground-truth answers |
| **BLEU** | N-gram lexical similarity |
| **LLM-as-a-Judge** | Semantic correctness evaluation via LLM |
| **Retrieval Accuracy** | Correctness of retrieved memories |
| **Memory Efficiency** | Storage and retrieval speed |

---

## 🛠️ Open-Source Frameworks

| Framework | Description | Links |
|-----------|-------------|-------|
| **Mem0** | Production-ready memory for AI agents with graph-based storage | [[GitHub]](https://github.com/mem0ai/mem0) [[arXiv]](https://arxiv.org/abs/2504.19413) |
| **MemGPT/Letta** | LLMs as operating systems with hierarchical memory management | [[GitHub]](https://github.com/cpacker/MemGPT) [[arXiv]](https://arxiv.org/abs/2310.08560) |
| **Zep** | Temporal knowledge graph for agent memory | [[GitHub]](https://github.com/getzep/zep) [[arXiv]](https://arxiv.org/abs/2501.13956) |
| **HippoRAG** | Neurobiologically inspired long-term memory with knowledge graphs | [[GitHub]](https://github.com/OSU-NLP-Group/HippoRAG) [[arXiv]](https://arxiv.org/abs/2405.14831) |
| **A-MEM** | Agentic memory with Zettelkasten-inspired organization | [[GitHub]](https://github.com/agiresearch/A-mem) [[arXiv]](https://arxiv.org/abs/2502.12110) |
| **LangMem** | Long-term memory for LangChain agents | [[Docs]](https://langchain-ai.github.io/langmem/) |

---

## 🎮 Applications

Memory mechanisms are crucial across various LLM agent applications:

| Domain | Description | Key Papers |
|--------|-------------|------------|
| **🎭 Role-Playing** | Maintaining consistent character personas over extended interactions | Character-LLM, ChatHaruhi, RoleLLM |
| **🌐 Social Simulation** | Simulating human social behaviors at scale | Generative Agents, OASIS, S³ |
| **🤝 Personal Assistants** | Learning user preferences and providing personalized responses | MemoryBank, Mem0, A-MEM |
| **🎮 Open-World Games** | Accumulating skills and world knowledge for exploration | Voyager, GITM, JARVIS-1 |
| **💻 Code Generation** | Iterative debugging and cross-project learning | ChatDev, MetaGPT, Reflexion |
| **📊 Recommendation** | Personalizing suggestions based on interaction history | RecMind, InteRecAgent |
| **🏥 Expert Systems** | Domain-specific knowledge management | HuaTuo, InvestLM |
| **🌐 Web Agents** | Navigating and automating web tasks | Agent S, SkillWeaver, UFO2 |
| **🔬 Scientific Research** | Managing research context and hypotheses | JARVIS-1, Darwin Godel Machine |

---

## 🔮 Future Directions

Based on current research, promising future directions include:

| Direction | Description |
|-----------|-------------|
| **🤖 Memory Automation** | Reducing manual design through learned memory operations |
| **🎯 RL Integration** | Using reinforcement learning for memory optimization (Memory-R1) |
| **🖼️ Multimodal Memory** | Extending beyond text to images, audio, and video |
| **👥 Multi-Agent Memory** | Shared and distributed memory across agent teams |
| **🔒 Trustworthiness** | Privacy, security, and reliability of agent memories |
| **⚡ Efficiency** | Scalable long-term memory for extended operations |
| **🧪 Standardized Benchmarks** | Unified evaluation protocols (LoCoMo, LongMemEval) |
| **🧠 Cognitive Inspiration** | Drawing from neuroscience (HippoRAG, episodic memory) |

---

## 📌 Recommended Figures

For your README, I recommend including these figures (in order of importance):

1. **Main Taxonomy Figure** — Shows the Forms × Functions × Dynamics framework
   - Source: `https://github.com/Shichun-Liu/Agent-Memory-Paper-List/blob/main/assets/main.png`
   - Use: Central visual explaining the unified taxonomy

2. **Conceptual Comparison Figure** — Distinguishes Agent Memory from LLM Memory, RAG, and Context Engineering
   - Source: `https://github.com/Shichun-Liu/Agent-Memory-Paper-List/blob/main/assets/concept.png`
   - Use: In the "What is Agent Memory?" section

3. **Agent-Environment Interaction Figure** — Shows the W (Write), P (Process), R (Read) cycle
   - Source: Your existing figure showing Task A/B interaction
   - Use: In the "Memory Dynamics" section

4. **Memory Sources Figure** — Shows Inside-trial, Cross-trial, and External Knowledge
   - Source: Your existing figure
   - Use: In the "Memory Functions" section

---

## 📄 Citation

If you find this resource helpful, please cite the reference surveys:

```bibtex
@article{zhang2024survey,
  title={A Survey on the Memory Mechanism of Large Language Model based Agents},
  author={Zhang, Zeyu and Bo, Xiaohe and Ma, Chen and Li, Rui and Chen, Xu and Dai, Quanyu and Zhu, Jieming and Dong, Zhenhua and Wen, Ji-Rong},
  journal={arXiv preprint arXiv:2404.13501},
  year={2024}
}

@article{hu2025memory,
  title={Memory in the Age of AI Agents},
  author={Hu, Yuyang and Liu, Shichun and Yue, Yanwei and Zhang, Guibin and Liu, Boyang and others},
  journal={arXiv preprint arXiv:2512.13564},
  year={2025}
}
```

---

## 🤝 Contributing

Contributions are welcome! If you'd like to add new papers, fix errors, or suggest improvements:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/add-paper`)
3. Make your changes
4. Submit a pull request

Please ensure any added papers include:
- Full paper title with year
- Links to arXiv paper AND GitHub (if available)
- Appropriate categorization by Form × Function

---

<p align="center">
  <strong>⭐ Star this repo if you find it helpful!</strong>
</p>

<p align="center">
  Made with ❤️ for the LLM Agent Research Community
</p>
