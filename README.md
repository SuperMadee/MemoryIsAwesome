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
- [References](#-references)
- [Citation](#-citation)
- [Contributing](#-contributing)

---

## 🎯 Introduction

Foundation model-based agents have emerged as a transformative paradigm in AI research. Unlike vanilla foundation models, these agents possess **self-evolving capabilities** that enable them to solve real-world problems requiring long-term, complex interactions with their environment.

**Memory** is the cornerstone of these agents—it's what makes an agent truly an *agent*. Memory underpins the ability to perform long-horizon reasoning, adapt continually, and interact effectively with complex environments.

This repository synthesizes insights from major surveys on agent memory (see [References](#-references)).

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

### What Counts as Memory?

| Perspective | Definition |
|-------------|------------|
| **Narrow** | The actions and observations within a single trial (complete agent-environment interaction sequence) |
| **Broad** | Information from current trial, past trials, AND external knowledge sources |

---

## 🗂️ Unified Taxonomy

We organize agent memory research through three unified lenses: **Forms**, **Functions**, and **Dynamics**.

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

---

### 🔄 Memory Dynamics (How Memory Evolves?)

Memory dynamics describe the operational lifecycle of memory.

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

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| O-Mem | 2025 | Omni memory system for personalized, long horizon, self-evolving agents | [[arXiv]](https://arxiv.org/abs/2511.13593) |
| In Prospect and Retrospect | 2025 | Reflective memory management for long-term personalized dialogue agents | [[ACL]](https://aclanthology.org/2025.acl-long.413/) |
| Memoro | 2025 | Using LLMs to realize a concise interface for real-time memory augmentation | [[ACM]](https://doi.org/10.1145/3613904.3642450) |
| RCR-Router | 2025 | Efficient role-aware context routing for multi-agent LLM systems with structured memory | [[arXiv]](https://arxiv.org/abs/2508.04903) |
| Livia | 2025 | Emotion-aware AR companion powered by modular AI agents and progressive memory compression | [[arXiv]](https://arxiv.org/abs/2509.05298) |
| D-SMART | 2025 | Enhancing LLM dialogue consistency via dynamic structured memory and reasoning tree | [[arXiv]](https://arxiv.org/abs/2510.13363) |
| WebWeaver | 2025 | Structuring web-scale evidence with dynamic outlines for open-ended deep research | [[arXiv]](https://arxiv.org/abs/2509.13312) |
| CAM | 2025 | A constructivist view of agentic memory for LLM-based reading comprehension | [[arXiv]](https://arxiv.org/abs/2510.05520) |
| MovieChat | 2025 | From dense token to sparse memory for long video understanding | [[CVPR]](https://doi.org/10.1109/CVPR52733.2024.01725) |
| Pre-Storage Reasoning | 2025 | Shifting inference burden to memory for personalized dialogue | [[arXiv]](https://arxiv.org/abs/2509.10852) |
| LightMem | 2025 | Lightweight and efficient memory-augmented generation | [[arXiv]](https://arxiv.org/abs/2510.18866) |
| Mem-α | 2025 | Learning memory construction via reinforcement learning | [[arXiv]](https://arxiv.org/abs/2509.25911) |
| SGMem | 2025 | Sentence graph memory for long-term conversational agents | [[arXiv]](https://arxiv.org/abs/2509.21212) |
| Nemori | 2025 | Self-organizing agent memory inspired by cognitive science | [[arXiv]](https://arxiv.org/abs/2508.03341) |
| MOOM | 2025 | Maintenance, organization and optimization of memory in ultra-long role-playing dialogues | [[arXiv]](https://arxiv.org/abs/2509.11860) |
| Multiple Memory Systems | 2025 | Enhancing the long-term memory of agents | [[arXiv]](https://arxiv.org/abs/2508.15294) |
| Semantic Anchoring | 2025 | Leveraging linguistic structures for persistent conversational context | [[arXiv]](https://arxiv.org/abs/2508.12630) |
| Recommender AI Agent | 2025 | Integrating LLMs for interactive recommendations | [[ACM]](https://doi.org/10.1145/3731446) |
| ComoRAG | 2025 | Cognitive-inspired memory-organized RAG for stateful long narrative reasoning | [[arXiv]](https://arxiv.org/abs/2508.10419) |
| Seeing, Listening, Remembering | 2025 | A multimodal agent with long-term memory | [[arXiv]](https://arxiv.org/abs/2508.09736) |
| RoleLLM | 2025 | Benchmarking, eliciting, and enhancing role-playing abilities of LLMs | [[ACL]](https://doi.org/10.18653/v1/2024.findings-acl.878) |
| Memory-R1 | 2025 | Enhancing LLM agents to manage and utilize memories via RL | [[arXiv]](https://arxiv.org/abs/2508.19828) |
| Intrinsic Memory Agents | 2025 | Heterogeneous multi-agent LLM systems through structured contextual memory | [[arXiv]](https://arxiv.org/abs/2508.08997) |
| MIRIX | 2025 | Multi-agent memory system for LLM-based agents | [[arXiv]](https://arxiv.org/abs/2507.07957) |
| Hierarchical Memory | 2025 | High-efficiency long-term reasoning in LLM agents | [[arXiv]](https://arxiv.org/abs/2507.22925) |
| G-Memory | 2025 | Tracing hierarchical memory for multi-agent systems | [[arXiv]](https://arxiv.org/abs/2506.07398) |
| Embodied Agents Meet Personalization | 2025 | Exploring memory utilization for personalized assistance | [[arXiv]](https://arxiv.org/abs/2505.16348) |
| MemGuide | 2025 | Intent-driven memory selection for goal-oriented multi-session LLM agents | [[arXiv]](https://arxiv.org/abs/2505.20231) |
| SeCom | 2025 | Memory construction and retrieval for personalized conversational agents | [[OpenReview]](https://openreview.net/forum?id=xKDZAW0He3) |
| Embodied VideoAgent | 2025 | Persistent memory from egocentric videos and embodied sensors | [[arXiv]](https://arxiv.org/abs/2501.00358) |
| Human-inspired Episodic Memory | 2025 | Episodic memory for infinite context LLMs | [[OpenReview]](https://openreview.net/forum?id=BI2int5SAC) |
| Zep | 2025 | A temporal knowledge graph architecture for agent memory | [[arXiv]](https://arxiv.org/abs/2501.13956) |
| A-MEM | 2025 | Agentic memory for LLM agents | [[arXiv]](https://arxiv.org/abs/2502.12110) |
| Unveiling Privacy Risks | 2025 | Privacy risks in LLM agent memory | [[arXiv]](https://arxiv.org/abs/2502.13172) |
| Mem2Ego | 2025 | Empowering VLMs with global-to-ego memory for long-horizon embodied navigation | [[arXiv]](https://arxiv.org/abs/2502.14254) |
| Mem0 | 2025 | Building production-ready AI agents with scalable long-term memory | [[arXiv]](https://arxiv.org/abs/2504.19413) [[GitHub]](https://github.com/mem0ai/mem0) |
| From RAG to Memory | 2025 | Non-parametric continual learning for LLMs | [[arXiv]](https://arxiv.org/abs/2502.14802) |
| ENGRAM | 2025 | Effective, lightweight memory orchestration for conversational agents | [[arXiv]](https://arxiv.org/abs/2511.12960) |
| SimpleDoc | 2025 | Multi-modal document understanding with dual-cue page retrieval | [[arXiv]](https://arxiv.org/abs/2506.14035) [[GitHub]](https://github.com/ag2ai/SimpleDoc) |
| Zero-RAG | 2025 | Retrieval-augmented generation with zero redundant knowledge | [[arXiv]](https://arxiv.org/abs/2511.00505) |
| RAG with Hierarchical Knowledge | 2025 | Retrieval-augmented generation with hierarchical knowledge | [[arXiv]](https://arxiv.org/abs/2503.10150) |
| RoboMemory | 2025 | Brain-inspired multi-memory agentic framework for interactive environmental learning | [[arXiv]](https://arxiv.org/abs/2508.01415) |
| Graph2Nav | 2025 | 3D object-relation graph generation for robot navigation | [[arXiv]](https://arxiv.org/abs/2504.16782) |
| Episodic Memory for Video | 2025 | Episodic memory representation for long-form video understanding | [[arXiv]](https://arxiv.org/abs/2508.09486) |
| AI PERSONA | 2024 | Towards life-long personalization of LLMs | [[arXiv]](https://arxiv.org/abs/2412.13103) |
| OASIS | 2024 | Open agent social interaction simulations with one million agents | [[arXiv]](https://arxiv.org/abs/2411.11581) |
| Memolet | 2024 | Reifying the reuse of user-AI conversational memories | [[ACM]](https://doi.org/10.1145/3654777.3676388) |
| Dynamic Tree Memory | 2024 | From isolated conversations to hierarchical schemas | [[arXiv]](https://arxiv.org/abs/2410.14052) |
| Inner Loop Query | 2024 | Enhancing long context performance in LLMs | [[arXiv]](https://arxiv.org/abs/2410.12859) |
| Editable Memory Graphs | 2024 | Crafting personalized agents through RAG on editable memory graphs | [[arXiv]](https://arxiv.org/abs/2409.19401) |
| AriGraph | 2024 | Learning knowledge graph world models with episodic memory for LLM agents | [[arXiv]](https://arxiv.org/abs/2407.04363) |
| ChatHaruhi | 2024 | Reviving anime character in reality via LLM | [[arXiv]](https://arxiv.org/abs/2308.09597) |
| Context and Time Sensitive Memory | 2024 | Toward conversational agents with context and time sensitive long-term memory | [[arXiv]](https://arxiv.org/abs/2406.00057) |
| Hierarchical Aggregate Tree | 2024 | Enhancing long-term memory using hierarchical aggregate tree for RAG | [[arXiv]](https://arxiv.org/abs/2406.06124) |
| Timeline-based Memory | 2024 | Towards lifelong dialogue agents via timeline-based memory management | [[arXiv]](https://arxiv.org/abs/2406.10996) |
| HippoRAG | 2024 | Neurobiologically inspired long-term memory for LLMs | [[arXiv]](https://arxiv.org/abs/2405.14831) [[GitHub]](https://github.com/OSU-NLP-Group/HippoRAG) |
| Memory Sharing | 2024 | Memory sharing for LLM-based agents | [[arXiv]](https://arxiv.org/abs/2404.09982) |
| Knowledge Graph Tuning | 2024 | Real-time LLM personalization based on human feedback | [[arXiv]](https://arxiv.org/abs/2405.19686) |
| Graph RAG | 2024 | From local to global: a graph RAG approach to query-focused summarization | [[arXiv]](https://arxiv.org/abs/2404.16130) |
| User Behavior Simulation | 2024 | User behavior simulation with LLM-based agents | [[arXiv]](https://arxiv.org/abs/2306.02552) [[GitHub]](https://github.com/RUC-GSAI/YuLan-Rec) |
| ReMEmbR | 2024 | Building and reasoning over long-horizon spatio-temporal memory for robot navigation | [[arXiv]](https://arxiv.org/abs/2409.13682) |
| Episodic Memory Verbalization | 2024 | Hierarchical representations of life-long robot experience | [[arXiv]](https://arxiv.org/abs/2409.17702) |
| Mobility VLA | 2024 | Multimodal instruction navigation with long-context VLMs and topological graphs | [[arXiv]](https://arxiv.org/abs/2407.07775) |
| MemGPT | 2023 | Towards LLMs as operating systems | [[arXiv]](https://arxiv.org/abs/2310.08560) [[GitHub]](https://github.com/cpacker/MemGPT) |
| GameGPT | 2023 | Multi-agent collaborative framework for game development | [[arXiv]](https://arxiv.org/abs/2310.08067) |
| CALYPSO | 2023 | LLMs as dungeon masters' assistants | [[AIIDE]](https://doi.org/10.1609/aiide.v19i1.27534) |
| Lyfe Agents | 2023 | Generative agents for low-cost real-time social interactions | [[arXiv]](https://arxiv.org/abs/2310.02172) |
| MetaGPT | 2023 | Meta programming for multi-agent collaborative framework | [[arXiv]](https://arxiv.org/abs/2308.00352) |
| MemoChat | 2023 | Tuning LLMs to use memos for consistent long-range conversation | [[arXiv]](https://arxiv.org/abs/2308.08239) [[GitHub]](https://github.com/LuJunru/MemoChat) |
| MPC | 2023 | Prompted LLMs as chatbot modules for long open-domain conversation | [[ACL]](https://doi.org/10.18653/v1/2023.findings-acl.277) [[GitHub]](https://github.com/krafton-ai/MPC) |
| Recursive Summarization | 2023 | Recursively summarizing enables long-term dialogue memory in LLMs | [[arXiv]](https://arxiv.org/abs/2308.15022) |
| S³ | 2023 | Social-network simulation system with LLM-empowered agents | [[arXiv]](https://arxiv.org/abs/2307.14984) |
| RecurrentGPT | 2023 | Interactive generation of (arbitrarily) long text | [[arXiv]](https://arxiv.org/abs/2305.13304) |
| MemoryBank | 2023 | Enhancing LLMs with long-term memory | [[arXiv]](https://arxiv.org/abs/2305.10250) [[GitHub]](https://github.com/zhongwanjun/MemoryBank-SiliconFriend) |
| RET-LLM | 2023 | Towards a general read-write memory for LLMs | [[arXiv]](https://arxiv.org/abs/2305.14322) |
| Generative Agents | 2023 | Interactive simulacra of human behavior | [[arXiv]](https://arxiv.org/abs/2304.03442) [[GitHub]](https://github.com/joonspk-research/generative_agents) |
| HuaTuo | 2023 | Tuning LLaMA model with Chinese medical knowledge | [[arXiv]](https://arxiv.org/abs/2304.06975) |
| SCM | 2023 | Enhancing LLMs with self-controlled memory framework | [[arXiv]](https://arxiv.org/abs/2304.13343) [[GitHub]](https://github.com/wbbeyourself/scm4llms) |
| Think-in-Memory | 2023 | Recalling and post-thinking enable LLMs with long-term memory | [[arXiv]](https://arxiv.org/abs/2311.08719) |
| ChatDB | 2023 | Augmenting LLMs with databases as their symbolic memory | [[Website]](https://chatdatabase.github.io/) |
| RoboVQA | 2023 | Multimodal long-horizon reasoning for robotics | [[arXiv]](https://arxiv.org/abs/2311.00899) [[Website]](https://robovqa.github.io/) |
| CLIP-Fields | 2022 | Weakly supervised semantic fields for robotic memory | [[arXiv]](https://arxiv.org/abs/2210.05663) [[GitHub]](https://github.com/notmahi/clip-fields) |
| LM-Nav | 2022 | Robotic navigation with large pre-trained models of language, vision, and action | [[arXiv]](https://arxiv.org/abs/2207.04429) |
| Scene Memory Transformer | 2019 | Scene memory transformer for embodied agents in long-horizon tasks | [[arXiv]](https://arxiv.org/abs/1903.03878) |

#### Parametric Factual Memory

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| Pretraining with Hierarchical Memories | 2025 | Separating long-tail and common knowledge | [[arXiv]](https://arxiv.org/abs/2510.02375) |
| MLP Memory | 2025 | Language modeling with retriever-pretrained external memory | [[arXiv]](https://arxiv.org/abs/2508.01832) |
| Self-Updatable LLMs | 2025 | Integrating context into model parameters | [[OpenReview]](https://openreview.net/forum?id=aCPFCDL9QY) |
| WISE | 2025 | Rethinking knowledge memory for lifelong model editing | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2024/hash/60960ad78868fce5c165295fbd895060-Abstract-Conference.html) |
| CharacterGLM | 2025 | Customizing social characters with LLMs | [[EMNLP]](https://doi.org/10.18653/v1/2024.emnlp-industry.107) |
| ELDER | 2025 | Enhancing lifelong model editing with mixture-of-LoRA | [[AAAI]](https://doi.org/10.1609/aaai.v39i23.34622) |
| Online Adaptation (MAC) | 2025 | Online adaptation of language models with a memory of amortized contexts | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2024/hash/eaf956b52bae51fbf387b8be4cc3ce18-Abstract-Conference.html) [[GitHub]](https://github.com/jihoontack/MAC) |
| AlphaEdit | 2024 | Null-space constrained knowledge editing for LMs | [[arXiv]](https://arxiv.org/abs/2410.02355) |
| Neighboring Perturbations | 2024 | Neighboring perturbations of knowledge editing on LLMs | [[OpenReview]](https://openreview.net/forum?id=K9NTPRvVRI) |
| Character-LLM | 2024 | A trainable agent for role-playing | [[EMNLP]](https://doi.org/10.18653/v1/2023.emnlp-main.814) [[GitHub]](https://github.com/choosewhatulike/trainable-agents) |
| Memory Layers at Scale | 2024 | Scaling memory layers for LLMs | [[arXiv]](https://arxiv.org/abs/2412.09764) [[GitHub]](https://github.com/facebookresearch/memory) |
| MoExtend | 2024 | Tuning new experts for modality and task extension | [[arXiv]](https://arxiv.org/abs/2408.03511) [[GitHub]](https://github.com/zhongshsh/MoExtend) |
| K-Adapter | 2023 | Infusing knowledge into pre-trained models with adapters | [[ACL]](https://doi.org/10.18653/v1/2021.findings-acl.121) |
| MEND | 2022 | Fast model editing at scale | [[ICLR]](https://openreview.net/forum?id=0DcZxeWfOPt) |
| ROME | 2021 | Editing factual knowledge in language models | [[arXiv]](https://arxiv.org/abs/2104.08164) |
| ELLA | 2013 | An efficient lifelong learning algorithm | [[ICML]](https://proceedings.mlr.press/v28/ruvolo13.html) |

#### Latent Factual Memory

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| Memory³ | 2025 | Language modeling with explicit memory | [[arXiv]](https://arxiv.org/abs/2407.01178) |
| General Continuous Memory | 2025 | Towards general continuous memory for vision-language models | [[arXiv]](https://arxiv.org/abs/2505.17670) |
| M+ | 2025 | Extending MemoryLLM with scalable long-term memory | [[arXiv]](https://arxiv.org/abs/2502.00592) |
| R3Mem | 2025 | Bridging memory retention and retrieval via reversible compression | [[arXiv]](https://arxiv.org/abs/2502.15957) |
| NAMM | 2025 | An evolved universal transformer memory | [[arXiv]](https://arxiv.org/abs/2410.13166) [[GitHub]](https://github.com/SakanaAI/evo-memory) |
| Thinker | 2025 | Learning to think fast and slow | [[arXiv]](https://arxiv.org/abs/2505.21097) |
| Hierarchical Reasoning Model | 2025 | Hierarchical reasoning model for complex tasks | [[arXiv]](https://arxiv.org/abs/2506.21734) [[GitHub]](https://github.com/sapientinc/HRM/) |
| Efficient Episodic Memory | 2024 | Efficient episodic memory utilization of cooperative multi-agent RL | [[OpenReview]](https://openreview.net/forum?id=LjivA1SLZ6) |

---

### 🎓 Experiential Memory

Stores insights, learned skills, and procedural knowledge from past experiences.

> 💡 **Why use Experiential Memory?** Experiential memory enables agents to learn from successes and failures, accumulate reusable skills, and improve performance over time. It transforms agents from stateless responders into continuously evolving systems that get better with experience.

#### Token-level Experiential Memory

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| Agentic Context Engineering | 2025 | Evolving contexts for self-improving language models | [[arXiv]](https://arxiv.org/abs/2510.04618) |
| FLEX | 2025 | Continuous agent evolution via forward learning from experience | [[arXiv]](https://arxiv.org/abs/2511.06449) |
| Scaling Agent Learning | 2025 | Scaling agent learning via experience synthesis | [[arXiv]](https://arxiv.org/abs/2511.03773) |
| UFO2 | 2025 | The desktop AgentOS | [[arXiv]](https://arxiv.org/abs/2504.14603) |
| PRINCIPLES | 2025 | Synthetic strategy memory for proactive dialogue agents | [[arXiv]](https://arxiv.org/abs/2509.17459) |
| Training-Free GRPO | 2025 | Training-free group relative policy optimization | [[arXiv]](https://arxiv.org/abs/2510.08191) |
| ToolMem | 2025 | Enhancing multimodal agents with learnable tool capability memory | [[arXiv]](https://arxiv.org/abs/2510.06664) |
| H²R | 2025 | Hierarchical hindsight reflection for multi-task LLM agents | [[arXiv]](https://arxiv.org/abs/2509.12810) |
| BrowserAgent | 2025 | Building web agents with human-inspired web browsing actions | [[arXiv]](https://arxiv.org/abs/2510.10666) |
| LEGOMem | 2025 | Modular procedural memory for multi-agent LLM systems | [[arXiv]](https://arxiv.org/abs/2510.04851) |
| Alita-G | 2025 | Self-evolving generative agent for agent generation | [[arXiv]](https://arxiv.org/abs/2510.23601) |
| SAGE | 2025 | Self-evolving agents with reflective and memory-augmented abilities | [[Neurocomputing]](https://doi.org/10.1016/j.neucom.2025.130470) |
| ReasoningBank | 2025 | Scaling agent self-evolving with reasoning memory | [[arXiv]](https://arxiv.org/abs/2509.25140) |
| Memento | 2025 | Fine-tuning LLM agents without fine-tuning LLMs | [[arXiv]](https://arxiv.org/abs/2508.16153) |
| Memp | 2025 | Exploring agent procedural memory | [[arXiv]](https://arxiv.org/abs/2508.06433) |
| SEAgent | 2025 | Self-evolving computer use agent with autonomous learning from experience | [[arXiv]](https://arxiv.org/abs/2508.04700) |
| Agent KB | 2025 | Leveraging cross-domain experience for agentic problem solving | [[arXiv]](https://arxiv.org/abs/2507.06229) |
| MemTool | 2025 | Optimizing short-term memory management for dynamic tool calling | [[arXiv]](https://arxiv.org/abs/2507.21428) |
| JARVIS-1 | 2025 | Open-world multi-task agents with memory-augmented multimodal LMs | [[TPAMI]](https://doi.org/10.1109/TPAMI.2024.3511593) |
| Agent Workflow Memory | 2025 | Agent workflow memory for task automation | [[OpenReview]](https://openreview.net/forum?id=NTAhi2JEEE) |
| Darwin Godel Machine | 2025 | Open-ended evolution of self-improving agents | [[arXiv]](https://arxiv.org/abs/2505.22954) |
| Alita | 2025 | Generalist agent enabling scalable agentic reasoning with minimal predefinition | [[arXiv]](https://arxiv.org/abs/2505.20286) |
| SkillWeaver | 2025 | Web agents can self-improve by discovering and honing skills | [[arXiv]](https://arxiv.org/abs/2504.07079) |
| LearnAct | 2025 | Few-shot mobile GUI agent with a unified demonstration benchmark | [[arXiv]](https://arxiv.org/abs/2504.13805) |
| Tool Retrieval Benchmark | 2025 | Retrieval models aren't tool-savvy: benchmarking tool retrieval for LLMs | [[arXiv]](https://arxiv.org/abs/2503.01763) |
| Dynamic Cheatsheet | 2025 | Test-time learning with adaptive memory | [[arXiv]](https://arxiv.org/abs/2504.07952) |
| Inducing Programmatic Skills | 2025 | Inducing programmatic skills for agentic tasks | [[arXiv]](https://arxiv.org/abs/2504.06821) |
| COLA | 2025 | A scalable multi-agent framework for Windows UI task automation | [[arXiv]](https://arxiv.org/abs/2503.09263) |
| Memory-augmented Query | 2025 | Memory-augmented query reconstruction for LLM-based knowledge graph reasoning | [[arXiv]](https://arxiv.org/abs/2503.05193) |
| Buffer of Thoughts | 2025 | Thought-augmented reasoning with LLMs | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2024/hash/cde328b7bf6358f5ebb91fe9c539745e-Abstract-Conference.html) |
| From Exploration to Mastery | 2025 | Enabling LLMs to master tools via self-driven interactions | [[arXiv]](https://arxiv.org/abs/2410.08197) |
| REFLECT | 2025 | Summarizing robot experiences for failure explanation and correction | [[arXiv]](https://arxiv.org/abs/2306.15724) [[Website]](https://robot-reflect.github.io/) |
| Planning from Imagination | 2024 | Episodic simulation and episodic memory for vision-and-language navigation | [[arXiv]](https://arxiv.org/abs/2412.01857) |
| ExpeL | 2024 | LLM agents are experiential learners | [[AAAI]](https://doi.org/10.1609/aaai.v38i17.29936) [[GitHub]](https://github.com/LeapLabTHU/ExpeL) |
| RepairAgent | 2024 | An autonomous, LLM-based agent for program repair | [[arXiv]](https://arxiv.org/abs/2403.17134) |
| Fincon | 2024 | Synthesized LLM multi-agent system for enhanced financial decision making | [[arXiv]](https://arxiv.org/abs/2407.06567) |
| COLT | 2024 | Towards completeness-oriented tool retrieval for LLMs | [[arXiv]](https://arxiv.org/abs/2405.16089) |
| ChatDev | 2024 | Communicative agents for software development | [[arXiv]](https://arxiv.org/abs/2307.07924) [[GitHub]](https://github.com/OpenBMB/ChatDev) |
| LOTUS | 2024 | Continual imitation learning for robot manipulation through unsupervised skill discovery | [[arXiv]](https://arxiv.org/abs/2311.02058) |
| RecMind | 2023 | Large language model powered agent for recommendation | [[NAACL]](https://doi.org/10.18653/v1/2024.findings-naacl.271) |
| ToolLLM | 2023 | Facilitating LLMs to master 16000+ real-world APIs | [[arXiv]](https://arxiv.org/abs/2307.16789) |
| CREATOR | 2023 | Tool creation for disentangling abstract and concrete reasoning | [[EMNLP]](https://doi.org/10.18653/v1/2023.findings-emnlp.462) |
| Reflexion | 2023 | Language agents with verbal reinforcement learning | [[arXiv]](https://arxiv.org/abs/2303.11366) [[GitHub]](https://github.com/noahshinn/reflexion) |
| Toolformer | 2023 | Language models can teach themselves to use tools | [[arXiv]](https://arxiv.org/abs/2302.04761) |
| Voyager | 2023 | An open-ended embodied agent with LLMs | [[arXiv]](https://arxiv.org/abs/2305.16291) [[Website]](https://voyager.minedojo.org/) |
| GITM | 2023 | Ghost in the Minecraft: generally capable agents for open-world environments | [[arXiv]](https://arxiv.org/abs/2305.17144) [[GitHub]](https://github.com/OpenGVLab/GITM) |
| Synapse | 2023 | Trajectory-as-exemplar prompting with memory for computer control | [[Website]](https://ltzheng.github.io/Synapse/) |
| ReAct | 2023 | Synergizing reasoning and acting in language models | [[arXiv]](https://arxiv.org/abs/2210.03629) [[GitHub]](https://github.com/ysymyth/ReAct) |
| TPTU | 2023 | Large language model-based AI agents for task planning and tool usage | [[arXiv]](https://arxiv.org/abs/2308.03427) |
| TPTU-v2 | 2023 | Boosting task planning and tool usage in real-world systems | [[arXiv]](https://arxiv.org/abs/2311.11315) [[GitHub]](https://github.com/OPS-KK2024/TPTU-v2) |
| CLIN | 2023 | A continually learning language agent for rapid task adaptation | [[arXiv]](https://arxiv.org/abs/2310.10134) [[GitHub]](https://github.com/allenai/clin) |
| MetaAgents | 2023 | Simulating interactions of human behaviors for LLM-based task-oriented coordination | [[arXiv]](https://arxiv.org/abs/2310.06500) |
| Episodic Memory for Robotics | 2021 | Episodic memory model for learning robotic manipulation tasks | [[arXiv]](https://arxiv.org/abs/2104.10218) |
| Generalizable Episodic Memory | 2021 | Generalizable episodic memory for deep reinforcement learning | [[arXiv]](https://arxiv.org/abs/2103.06469) |

#### Parametric Experiential Memory

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| AgentEvolver | 2025 | Towards efficient self-evolving agent system | [[arXiv]](https://arxiv.org/abs/2511.10395) |
| Agent Learning via Early Experience | 2025 | Agent learning via early experience | [[arXiv]](https://arxiv.org/abs/2510.08558) |
| Scaling Agents via Continual Pre-training | 2025 | Scaling agents via continual pre-training | [[arXiv]](https://arxiv.org/abs/2509.13310) |
| ToolGen | 2024 | Unified tool retrieval and calling via generation | [[arXiv]](https://arxiv.org/abs/2410.03439) |
| Interactive Continual Learning | 2024 | Interactive continual learning: fast and slow thinking | [[arXiv]](https://arxiv.org/abs/2403.02628) [[GitHub]](https://github.com/BiqingQi/Interactive-continual-Learning-Fast-and-Slow-Thinking) |
| Dynamic Gradient Calibration | 2024 | An effective dynamic gradient calibration method for continual learning | [[arXiv]](https://arxiv.org/abs/2407.20956) |
| A Machine with Memory | 2023 | A machine with short-term, episodic, and semantic memory systems | [[AAAI]](https://doi.org/10.1609/aaai.v37i1.25075) |
| Retroformer | 2023 | Retrospective LLM agents with policy gradient optimization | [[arXiv]](https://arxiv.org/abs/2308.02151) [[GitHub]](https://github.com/weirayao/Retroformer) |
| DualPrompt | 2022 | Complementary prompting for rehearsal-free continual learning | [[arXiv]](https://arxiv.org/abs/2204.04799) [[GitHub]](https://github.com/JH-LEE-KR/dualprompt-pytorch) |
| L2P | 2022 | Learning to prompt for continual learning | [[arXiv]](https://arxiv.org/abs/2112.08654) [[GitHub]](https://github.com/google-research/l2p) |
| DualNet | 2021 | Continual learning, fast and slow | [[arXiv]](https://arxiv.org/abs/2110.00175) [[GitHub]](https://github.com/phquang/DualNet) |

#### Latent Experiential Memory

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| Auto-scaling Continuous Memory | 2025 | Auto-scaling continuous memory for GUI agent | [[arXiv]](https://arxiv.org/abs/2510.09038) |

---

### ⚡ Working Memory

Manages active context during task execution.

> 💡 **Why use Working Memory?** Working memory enables agents to handle long-horizon tasks by maintaining relevant context without overwhelming the context window. It's essential for complex reasoning, multi-step planning, and tasks that exceed the model's native context length.

#### Token-level Working Memory

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| Memory as Action | 2025 | Autonomous context curation for long-horizon agentic tasks | [[arXiv]](https://arxiv.org/abs/2510.12635) |
| IterResearch | 2025 | Rethinking long-horizon agents via Markovian state reconstruction | [[arXiv]](https://arxiv.org/abs/2511.07327) |
| MemSearcher | 2025 | Training LLMs to reason, search and manage memory via end-to-end RL | [[arXiv]](https://arxiv.org/abs/2511.02805) |
| AgentFold | 2025 | Long-horizon web agents with proactive context management | [[arXiv]](https://arxiv.org/abs/2510.24699) |
| PRIME | 2025 | Planning and retrieval-integrated memory for enhanced reasoning | [[arXiv]](https://arxiv.org/abs/2509.22315) |
| Context as Memory | 2025 | Scene-consistent interactive long video generation with memory retrieval | [[arXiv]](https://arxiv.org/abs/2506.03141) |
| DeepAgent | 2025 | A general reasoning agent with scalable toolsets | [[arXiv]](https://arxiv.org/abs/2510.21618) |
| ACON | 2025 | Optimizing context compression for long-horizon LLM agents | [[arXiv]](https://arxiv.org/abs/2510.00615) |
| ReSum | 2025 | Unlocking long-horizon search intelligence via context summarization | [[arXiv]](https://arxiv.org/abs/2509.13313) |
| MemAgent | 2025 | Reshaping long-context LLM with multi-conv RL-based memory agent | [[arXiv]](https://arxiv.org/abs/2507.02259) |
| Agent S | 2024 | An open agentic framework that uses computers like a human | [[arXiv]](https://arxiv.org/abs/2410.08164) |

#### Parametric Working Memory

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| Lightning Attention | 2025 | Various lengths, constant speed: efficient language modeling | [[OpenReview]](https://openreview.net/forum?id=Lwm6TiUP4X) |
| Attention Sinks | 2024 | Efficient streaming language models with attention sinks | [[OpenReview]](https://openreview.net/forum?id=NG7sS51zVF) |

#### Latent Working Memory

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| Time-VLM | 2025 | Exploring multimodal VLMs for augmented time series forecasting | [[arXiv]](https://arxiv.org/abs/2502.04395) |
| SoftCoT | 2025 | Soft chain-of-thought for efficient reasoning with LLMs | [[ACL]](https://aclanthology.org/2025.acl-long.1137/) |
| MemoRAG | 2025 | Boosting long context processing with global memory-enhanced retrieval | [[ACM]](https://doi.org/10.1145/3696410.3714805) |
| MemGen | 2025 | Weaving generative latent memory for self-evolving agents | [[arXiv]](https://arxiv.org/abs/2509.24704) |
| Conflict-Aware Soft Prompting | 2025 | Conflict-aware soft prompting for retrieval-augmented generation | [[arXiv]](https://arxiv.org/abs/2508.15253) |
| MemoryVLA | 2025 | Perceptual-cognitive memory in VLA models for robotic manipulation | [[arXiv]](https://arxiv.org/abs/2508.19236) |
| MEM1 | 2025 | Learning to synergize memory and reasoning for efficient long-horizon agents | [[arXiv]](https://arxiv.org/abs/2506.15841) |
| Sentinel Tokens | 2025 | Taking a deep breath: enhancing language modeling with sentinel tokens | [[EMNLP]](https://doi.org/10.18653/v1/2024.findings-emnlp.233) |
| H2O | 2025 | Heavy-hitter oracle for efficient generative inference of LLMs | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/6ceefa7b15572587b78ecfcebb2827f8-Abstract-Conference.html) |
| RazorAttention | 2025 | Efficient KV cache compression through retrieval heads | [[OpenReview]](https://openreview.net/forum?id=tkiZQlL04w) |
| SnapKV | 2025 | LLM knows what you are looking for before generation | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2024/hash/28ab418242603e0f7323e54185d19bde-Abstract-Conference.html) |
| LM2 | 2025 | Large memory models | [[arXiv]](https://arxiv.org/abs/2502.06049) |
| Titans | 2025 | Learning to memorize at test time | [[arXiv]](https://arxiv.org/abs/2501.00663) [[GitHub]](https://github.com/ai-inpm/Titans---Learning-to-Memorize-at-Test-Time) |
| TTT | 2025 | Learning to (learn at test time): RNNs with expressive hidden states | [[arXiv]](https://arxiv.org/abs/2407.04620) [[GitHub]](https://github.com/test-time-training/ttt-lm-pytorch) |
| Adacc | 2025 | Adaptive compression and activation checkpointing for LLM memory management | [[arXiv]](https://arxiv.org/abs/2508.00806) |
| EdgeInfinite | 2025 | A memory-efficient infinite-context transformer for edge devices | [[arXiv]](https://arxiv.org/abs/2503.22196) |
| Augmenting LLMs with Long-Term Memory | 2024 | Augmenting language models with long-term memory | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/ebd82705f44793b6f9ade5a669d0f0bf-Abstract-Conference.html) |
| Context Compression | 2024 | Adapting language models to compress contexts | [[EMNLP]](https://doi.org/10.18653/v1/2023.emnlp-main.232) |
| Gist Tokens | 2024 | Learning to compress prompts with gist tokens | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/3d77c6dcc7f143aa2154e7f4d5e22d68-Abstract-Conference.html) |
| Scissorhands | 2024 | Exploiting the persistence of importance hypothesis for LLM KV cache compression | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/a452a7c6c463e4ae8fbdc614c6e983e6-Abstract-Conference.html) |
| Focused Transformer | 2024 | Contrastive training for context scaling | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/8511d06d5590f4bda24d42087802cc81-Abstract-Conference.html) |
| In-Context Autoencoder | 2023 | Context compression in a large language model | [[arXiv]](https://arxiv.org/abs/2307.06945) |
| Memorizing Transformers | 2022 | Memorizing transformers for long-range attention | [[OpenReview]](https://openreview.net/forum?id=TrjbxzRcnf-) |
| XMem | 2022 | Long-term video object segmentation with an Atkinson-Shiffrin memory model | [[arXiv]](https://arxiv.org/abs/2207.07115) |

---

## 📊 Benchmarks & Evaluation

### Memory Evaluation Benchmarks

| Benchmark | Year | Focus | Context Length | Links |
|-----------|------|-------|----------------|-------|
| **FindingDory** | 2025 | Memory evaluation in embodied agents | Various | [[arXiv]](https://arxiv.org/abs/2506.15635) [[HuggingFace]](https://huggingface.co/yali30/findingdory-qwen2.5-VL-3B-finetuned) |
| **MemoryBench** | 2025 | Memory and continual learning | Various | [[arXiv]](https://arxiv.org/abs/2510.17281) |
| **MemoryAgentBench** | 2025 | Incremental multi-turn interactions | Various | [[arXiv]](https://arxiv.org/abs/2507.05257) |
| **HaluMem** | 2025 | Evaluating hallucinations in memory systems | Various | [[arXiv]](https://arxiv.org/abs/2505.00000) |
| **LoCoMo** | 2024 | Very long-term conversational memory | ~9K tokens, 35 sessions | [[arXiv]](https://arxiv.org/abs/2402.17753) [[Website]](https://snap-research.github.io/locomo/) |
| **LongMemEval** | 2024 | Long-term interactive memory | ~115K-1.5M tokens | [[arXiv]](https://arxiv.org/abs/2410.10813) [[GitHub]](https://github.com/xiaowu0162/LongMemEval) |

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

| Framework | Year | Description | Links |
|-----------|------|-------------|-------|
| **Mem0** | 2025 | Production-ready memory for AI agents with graph-based storage | [[GitHub]](https://github.com/mem0ai/mem0) [[arXiv]](https://arxiv.org/abs/2504.19413) |
| **A-MEM** | 2025 | Agentic memory with Zettelkasten-inspired organization | [[GitHub]](https://github.com/agiresearch/A-mem) [[arXiv]](https://arxiv.org/abs/2502.12110) |
| **Zep** | 2025 | Temporal knowledge graph for agent memory | [[GitHub]](https://github.com/getzep/zep) [[arXiv]](https://arxiv.org/abs/2501.13956) |
| **MemOS** | 2025 | Operating system for memory-augmented generation in LLMs | [[GitHub]](https://github.com/MemoryAgent/MemOS) |
| **PowerMem** | 2025 | Agent-powered long-term memory with Ebbinghaus forgetting curve | [[GitHub]](https://github.com/Teingi/PowerMem) |
| **HippoRAG** | 2024 | Neurobiologically inspired long-term memory with knowledge graphs | [[GitHub]](https://github.com/OSU-NLP-Group/HippoRAG) [[arXiv]](https://arxiv.org/abs/2405.14831) |
| **LangMem** | 2024 | Long-term memory for LangChain agents | [[Docs]](https://langchain-ai.github.io/langmem/) |
| **MemGPT/Letta** | 2023 | LLMs as operating systems with hierarchical memory management | [[GitHub]](https://github.com/cpacker/MemGPT) [[arXiv]](https://arxiv.org/abs/2310.08560) |

---

## 🎮 Applications

Memory mechanisms are crucial across various LLM agent applications:

| Domain | Description | Key Papers |
|--------|-------------|------------|
| **🎭 Role-Playing** | Maintaining consistent character personas over extended interactions | Character-LLM, ChatHaruhi, RoleLLM, CharacterGLM, MOOM |
| **🌐 Social Simulation** | Simulating human social behaviors at scale | Generative Agents, OASIS, S³, Lyfe Agents |
| **🤝 Personal Assistants** | Learning user preferences and providing personalized responses | MemoryBank, Mem0, A-MEM, AI PERSONA, Livia |
| **🎮 Open-World Games** | Accumulating skills and world knowledge for exploration | Voyager, GITM, JARVIS-1, Minecraft agents |
| **💻 Code Generation** | Iterative debugging and cross-project learning | ChatDev, MetaGPT, Reflexion, RepairAgent |
| **📊 Recommendation** | Personalizing suggestions based on interaction history | RecMind, InteRecAgent, Recommender AI Agent |
| **🏥 Expert Systems** | Domain-specific knowledge management | HuaTuo, InvestLM, medical/legal agents |
| **🌐 Web Agents** | Navigating and automating web tasks | Agent S, SkillWeaver, UFO2, BrowserAgent |
| **🔬 Scientific Research** | Managing research context and hypotheses | JARVIS-1, Darwin Godel Machine |
| **🤖 Embodied Agents** | Persistent memory for physical world interaction | Mem2Ego, Embodied VideoAgent, MemoryVLA |
| **📹 Video Understanding** | Long-term video comprehension | MovieChat, XMem, Context as Memory |

---

## 🔮 Future Directions

Based on current research, promising future directions include:

| Direction | Description |
|-----------|-------------|
| **🤖 Memory Automation** | Reducing manual design through learned memory operations (Mem-α, Memory-R1) |
| **🎯 RL Integration** | Using reinforcement learning for memory optimization |
| **🖼️ Multimodal Memory** | Extending beyond text to images, audio, and video |
| **👥 Multi-Agent Memory** | Shared and distributed memory across agent teams (G-Memory) |
| **🔒 Trustworthiness** | Privacy, security, and reliability of agent memories |
| **⚡ Efficiency** | Scalable long-term memory for extended operations |
| **🧪 Standardized Benchmarks** | Unified evaluation protocols (LoCoMo, LongMemEval, MemoryBench) |
| **🧠 Cognitive Inspiration** | Drawing from neuroscience (HippoRAG, episodic memory) |
| **🔄 Self-Evolution** | Agents that continuously improve their own memory systems |

---

## 📚 References

This repository synthesizes insights from the following surveys:

| Survey | Year | Links |
|--------|------|-------|
| From Human Memory to AI Memory: A Survey on Memory Mechanisms in the Era of LLMs | 2025 | [[arXiv]](https://arxiv.org/abs/2504.15965) |
| Retrieval-Augmented Generation for Natural Language Processing: A Survey | 2025 | [[arXiv]](https://arxiv.org/abs/2407.13193) |
| A Survey of Robotic Navigation and Manipulation with Physics Simulators in the Era of Embodied AI | 2025 | [[arXiv]](https://arxiv.org/abs/2505.01458) |
| Memory in the Age of AI Agents: A Survey | 2025 | [[arXiv]](https://arxiv.org/abs/2512.13564) [[GitHub]](https://github.com/Shichun-Liu/Agent-Memory-Paper-List) |
| A Comprehensive Survey of Continual Learning: Theory, Method and Application | 2024 | [[arXiv]](https://arxiv.org/abs/2302.00487) [[GitHub]](https://github.com/Wang-ML-Lab/llm-continual-learning-survey) |
| Retrieval-Augmented Generation for Large Language Models: A Survey | 2024 | [[arXiv]](https://arxiv.org/abs/2312.10997) |
| A Survey on the Memory Mechanism of Large Language Model based Agents | 2024 | [[arXiv]](https://arxiv.org/abs/2404.13501) [[GitHub]](https://github.com/nuster1128/LLM_Agent_Memory_Survey) |
| Robot Learning in the Era of Foundation Models: A Survey | 2023 | [[arXiv]](https://arxiv.org/abs/2311.14379) |

---

## 📄 Citation

If you find this repository helpful, please cite:

```bibtex
@misc{memoryisawesome,
  title={Memory is Awesome: Your Guide to Memory in Foundation Model Agents},
  author={SuperMadee},
  year={2024},
  howpublished={\url{https://github.com/SuperMadee/MemoryIsAwesome}}
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
  Made with ❤️ for the Agent Research Community
</p>
