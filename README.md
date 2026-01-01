<p align="center">
  <img src="https://img.shields.io/badge/LLM-Memory-blue?style=for-the-badge" alt="LLM Memory"/>
  <img src="https://img.shields.io/badge/Agents-Research-green?style=for-the-badge" alt="Agents Research"/>
  <img src="https://img.shields.io/github/stars/SuperMadee/MemoryIsAwesome?style=for-the-badge" alt="Stars"/>
  <img src="https://img.shields.io/github/forks/SuperMadee/MemoryIsAwesome?style=for-the-badge" alt="Forks"/>
  <img src="https://img.shields.io/github/license/SuperMadee/MemoryIsAwesome?style=for-the-badge" alt="License"/>
</p>

<h1 align="center">🧠 Memory is Awesome</h1>

<p align="center">
  <strong>A comprehensive resource on memory mechanisms for LLM-based agents</strong>
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
  - [Factual Memory](#factual-memory)
  - [Experiential Memory](#experiential-memory)
  - [Working Memory](#working-memory)
- [Benchmarks & Frameworks](#-benchmarks--frameworks)
- [Applications](#-applications)
- [Future Directions](#-future-directions)
- [References](#-references)
- [Contributing](#-contributing)
- [Citation](#-citation)

---

## 🎯 Introduction

Large Language Model (LLM) based agents have emerged as a transformative paradigm in AI research. Unlike vanilla LLMs, these agents possess **self-evolving capabilities** that enable them to solve real-world problems requiring long-term, complex interactions with their environment.

**Memory** is the cornerstone of foundation model-based agents—it's what makes an agent truly an *agent*. Memory underpins the ability to perform long-horizon reasoning, adapt continually, and interact effectively with complex environments.

This repository provides a comprehensive overview of memory mechanisms in LLM-based agents, synthesizing insights from two major surveys:

> **📄 Survey 1: A Survey on the Memory Mechanism of Large Language Model based Agents**  
> Zhang et al., April 2024  
> [[arXiv]](https://arxiv.org/abs/2404.13501) [[GitHub]](https://github.com/nuster1128/LLM_Agent_Memory_Survey)

> **📄 Survey 2: Memory in the Age of AI Agents**  
> Hu et al., December 2025  
> [[arXiv]](https://arxiv.org/abs/2512.13564) [[GitHub]](https://github.com/Shichun-Liu/Agent-Memory-Paper-List)

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

<p align="center">
  <img src="https://private-user-images.githubusercontent.com/46626936/373806238-11bf212b-b1fb-4057-ac69-4a59d46bfced.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjcyNDEzNTMsIm5iZiI6MTc2NzI0MTA1MywicGF0aCI6Ii80NjYyNjkzNi8zNzM4MDYyMzgtMTFiZjIxMmItYjFmYi00MDU3LWFjNjktNGE1OWQ0NmJmY2VkLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjAxMDElMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwMTAxVDA0MTczM1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTgzN2NjOWFiYzE1OTA1ZWYyYzI1MDA4NWYzMjhjY2Q1N2U1ZGU4OWJiMDk1Mzc4NjQzZjg3NDE0MGQ2OTkyOTUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.bJAsaVnh9QXEN129B8_PJ_aQrWm6FP5WrqfMNZdycS0" alt="Memory Framework" width="700"/>
</p>

---

## 🗂️ Unified Taxonomy

We organize agent memory research through three unified lenses: **Forms**, **Functions**, and **Dynamics**.

<p align="center">
  <img src="https://raw.githubusercontent.com/Shichun-Liu/Agent-Memory-Paper-List/main/assets/main.png" alt="Unified Taxonomy" width="800"/>
</p>

---

### 📦 Memory Forms (What Carries Memory?)

Memory forms categorize HOW information is stored and represented.

| Form | Description | Characteristics | Examples |
|------|-------------|-----------------|----------|
| **🔤 Token-level** | Explicit, discrete text/symbols stored externally | Human-readable, interpretable, easy to update | Knowledge graphs, text databases, conversation logs |
| **⚙️ Parametric** | Implicit knowledge encoded in model weights | Requires fine-tuning, can be permanent | LoRA adapters, model editing, knowledge injection |
| **🧬 Latent** | Compressed representations in hidden states | Efficient, compact, less interpretable | KV-cache, memory tokens, neural embeddings |

#### Token-level Memory

Information is explicitly retained using natural language or structured formats.

**Subtypes:**

| Type | Description | Use Case |
|------|-------------|----------|
| Complete Interactions | Store all past agent-environment interactions | Full audit trail, comprehensive history |
| Recent Interactions | Prioritize most recent, relevant data | Conversational agents, sliding window |
| Retrieved Interactions | Select memories based on relevance | Long-term personalization, large-scale memory |
| External Knowledge | Access to databases, APIs, documents | Domain expertise, factual grounding |

#### Parametric Memory

Knowledge encoded directly into model parameters.

| Method | Description |
|--------|-------------|
| **Fine-tuning** | Train on domain data to embed knowledge |
| **Knowledge Editing** | Surgically update specific facts in weights |
| **Adapter Methods** | Add trainable modules (LoRA, K-Adapter) |

#### Latent Memory

Compressed neural representations for efficient storage.

| Approach | Description |
|----------|-------------|
| **KV-Cache Compression** | Reduce key-value cache size |
| **Memory Tokens** | Learn special tokens for memory |
| **Hidden State Caching** | Store intermediate representations |

---

### 🎯 Memory Functions (Why Agents Need Memory?)

Memory functions categorize WHAT purpose the memory serves.

| Function | Description | Cognitive Parallel |
|----------|-------------|-------------------|
| **📚 Factual Memory** | Stores knowledge, facts, and user preferences | Semantic memory |
| **🎓 Experiential Memory** | Stores insights, skills, and learned procedures | Episodic + Procedural memory |
| **⚡ Working Memory** | Active context management during tasks | Working memory |

<p align="center">
  <img src="https://private-user-images.githubusercontent.com/46626936/373810852-d538cc3c-794f-417f-af66-50cfa62258b3.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjcyNDEzNTMsIm5iZiI6MTc2NzI0MTA1MywicGF0aCI6Ii80NjYyNjkzNi8zNzM4MTA4NTItZDUzOGNjM2MtNzk0Zi00MTdmLWFmNjYtNTBjZmE2MjI1OGIzLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjAxMDElMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwMTAxVDA0MTczM1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWZkZmI5ZTBkMDk0MWE5NjU2MzAwYWIzODdiZDkzZTc1NzBlY2VhZjliZTIyNTRiYTRlODUzOGVhOGM5MTA3OGImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.s2gbchDrhMj6dzztUgHNxChToV1EtcODdRIr0JObAtc" alt="Memory Sources" width="600"/>
</p>

---

### 🔄 Memory Dynamics (How Memory Evolves?)

Memory dynamics describe the operational lifecycle of memory.

<p align="center">
  <img src="https://private-user-images.githubusercontent.com/46626936/373806599-ed0136e6-9541-49a3-b428-e3bf3c719c5c.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjcyNDEzNTMsIm5iZiI6MTc2NzI0MTA1MywicGF0aCI6Ii80NjYyNjkzNi8zNzM4MDY1OTktZWQwMTM2ZTYtOTU0MS00OWEzLWI0MjgtZTNiZjNjNzE5YzVjLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjAxMDElMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwMTAxVDA0MTczM1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWM1ZTc3OTI4MzFlNGYyOWVlNjI5MjE0Mzk1OGRhMDExYzc5MjBiZTk4NWRhMDgzOTJjYmU4ZmE1MThjNDQwZmYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.FfIlVEAvnRiP0FORWkTZlH-jtqlWGVF5VFZnzKQlKtw" alt="Agent-Environment Interaction" width="700"/>
</p>

| Phase | Symbol | Description | Strategies |
|-------|--------|-------------|------------|
| **Formation** | W | How memories are created and stored | Direct storage, summarization, structured extraction |
| **Evolution** | P | How memories are maintained over time | Consolidation, forgetting, reflection, compression |
| **Retrieval** | R | How memories are accessed when needed | Recency-based, relevance-based, importance-based, hybrid |

---

## 📚 Paper Collection

### Factual Memory

Stores knowledge, facts, user preferences, and world knowledge.

#### Token-level Factual Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | O-Mem: Omni Memory System for Personalized, Long Horizon, Self-Evolving Agents | [arXiv](https://arxiv.org/abs/2511.13593) |
| 2025 | Zep: A Temporal Knowledge Graph Architecture for Agent Memory | [arXiv](https://arxiv.org/abs/2501.13956) |
| 2025 | A-MEM: Agentic Memory for LLM Agents | [arXiv](https://arxiv.org/abs/2502.12110) |
| 2025 | Mem0: Building production-ready AI agents with scalable long-term memory | [arXiv](https://arxiv.org/abs/2504.19413) |
| 2025 | Memory-R1: Enhancing LLM Agents to Manage and Utilize Memories via RL | [arXiv](https://arxiv.org/abs/2508.19828) |
| 2024 | HippoRAG: Neurobiologically Inspired Long-Term Memory for LLMs | [arXiv](https://arxiv.org/abs/2405.14831) |
| 2024 | From Local to Global: A Graph RAG Approach to Query-Focused Summarization | [arXiv](https://arxiv.org/abs/2404.16130) |
| 2024 | From Isolated Conversations to Hierarchical Schemas: Dynamic Tree Memory | [arXiv](https://arxiv.org/abs/2410.14052) |
| 2024 | OASIS: Open Agent Social Interaction Simulations with One Million Agents | [arXiv](https://arxiv.org/abs/2411.11581) |
| 2023 | MemGPT: Towards LLMs as Operating Systems | [arXiv](https://arxiv.org/abs/2310.08560) |
| 2023 | Generative Agents: Interactive Simulacra of Human Behavior | [arXiv](https://arxiv.org/abs/2304.03442) |
| 2023 | MemoryBank: Enhancing LLMs with Long-Term Memory | [arXiv](https://arxiv.org/abs/2305.10250) |
| 2023 | RET-LLM: Towards a General Read-Write Memory for LLMs | [arXiv](https://arxiv.org/abs/2305.14322) |
| 2023 | SCM: Enhancing LLMs with Self-Controlled Memory Framework | [arXiv](https://arxiv.org/abs/2304.13343) |
| 2023 | MemoChat: Tuning LLMs to Use Memos for Consistent Long-Range Conversation | [arXiv](https://arxiv.org/abs/2308.08239) |
| 2023 | MetaGPT: Meta Programming for Multi-Agent Collaborative Framework | [arXiv](https://arxiv.org/abs/2308.00352) |
| 2023 | S³: Social-network Simulation System with LLM-Empowered Agents | [arXiv](https://arxiv.org/abs/2307.14984) |

#### Parametric Factual Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | WISE: Rethinking Knowledge Memory for Lifelong Model Editing | [NeurIPS](http://papers.nips.cc/paper_files/paper/2024/hash/60960ad78868fce5c165295fbd895060-Abstract-Conference.html) |
| 2025 | ELDER: Enhancing Lifelong Model Editing with Mixture-of-LoRA | [AAAI](https://doi.org/10.1609/aaai.v39i23.34622) |
| 2025 | Online Adaptation of Language Models with a Memory of Amortized Contexts | [NeurIPS](http://papers.nips.cc/paper_files/paper/2024/hash/eaf956b52bae51fbf387b8be4cc3ce18-Abstract-Conference.html) |
| 2024 | AlphaEdit: Null-Space Constrained Knowledge Editing for LMs | [arXiv](https://arxiv.org/abs/2410.02355) |
| 2024 | Character-LLM: A Trainable Agent for Role-Playing | [EMNLP](https://doi.org/10.18653/v1/2023.emnlp-main.814) |
| 2023 | HuaTuo: Tuning LLaMA Model with Chinese Medical Knowledge | [arXiv](https://arxiv.org/pdf/2304.06975) |

#### Latent Factual Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | Memory³: Language Modeling with Explicit Memory | [arXiv](https://arxiv.org/abs/2407.01178) |
| 2025 | M+: Extending MemoryLLM with Scalable Long-Term Memory | [arXiv](https://arxiv.org/abs/2502.00592) |
| 2025 | R3Mem: Bridging Memory Retention and Retrieval via Reversible Compression | [arXiv](https://arxiv.org/abs/2502.15957) |

---

### Experiential Memory

Stores insights, learned skills, and procedural knowledge from past experiences.

#### Token-level Experiential Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | Agent Workflow Memory | [OpenReview](https://openreview.net/forum?id=NTAhi2JEEE) |
| 2025 | SkillWeaver: Web Agents can Self-Improve by Discovering and Honing Skills | [arXiv](https://arxiv.org/abs/2504.07079) |
| 2025 | Darwin Godel Machine: Open-Ended Evolution of Self-Improving Agents | [arXiv](https://arxiv.org/abs/2505.22954) |
| 2025 | Buffer of Thoughts: Thought-Augmented Reasoning with LLMs | [NeurIPS](http://papers.nips.cc/paper_files/paper/2024/hash/cde328b7bf6358f5ebb91fe9c539745e-Abstract-Conference.html) |
| 2025 | JARVIS-1: Open-World Multi-Task Agents With Memory-Augmented Multimodal LMs | [IEEE](https://doi.org/10.1109/TPAMI.2024.3511593) |
| 2025 | Memento: Fine-tuning LLM Agents without Fine-tuning LLMs | [arXiv](https://arxiv.org/abs/2508.16153) |
| 2024 | ExpeL: LLM Agents Are Experiential Learners | [AAAI](https://doi.org/10.1609/aaai.v38i17.29936) |
| 2023 | Reflexion: Language Agents with Verbal Reinforcement Learning | [arXiv](https://arxiv.org/abs/2303.11366) |
| 2023 | Voyager: An Open-Ended Embodied Agent with LLMs | [Website](https://voyager.minedojo.org/) |
| 2023 | Ghost in the Minecraft: Generally Capable Agents for Open-World Environments | [GitHub](https://github.com/OpenGVLab/GITM) |
| 2023 | ToolLLM: Facilitating LLMs to Master 16000+ Real-world APIs | [arXiv](https://arxiv.org/abs/2307.16789) |
| 2023 | RecMind: Large Language Model Powered Agent For Recommendation | [arXiv](https://arxiv.org/pdf/2308.14296) |

#### Parametric Experiential Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | AgentEvolver: Towards Efficient Self-Evolving Agent System | [arXiv](https://arxiv.org/abs/2511.10395) |
| 2024 | ToolGen: Unified Tool Retrieval and Calling via Generation | [arXiv](https://arxiv.org/abs/2410.03439) |
| 2023 | Retroformer: Retrospective Large Language Agents with Policy Gradient Optimization | [arXiv](https://arxiv.org/abs/2308.02151) |

---

### Working Memory

Manages active context during task execution.

#### Token-level Working Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | Memory as Action: Autonomous Context Curation for Long-Horizon Tasks | [arXiv](https://arxiv.org/abs/2510.12635) |
| 2025 | AgentFold: Long-Horizon Web Agents with Proactive Context Management | [arXiv](https://arxiv.org/abs/2510.24699) |
| 2025 | ACON: Optimizing Context Compression for Long-Horizon LLM Agents | [arXiv](https://arxiv.org/abs/2510.00615) |
| 2025 | MemSearcher: Training LLMs to Reason, Search and Manage Memory via RL | [arXiv](https://arxiv.org/abs/2511.02805) |
| 2024 | Agent S: An Open Agentic Framework That Uses Computers Like a Human | [arXiv](https://arxiv.org/abs/2410.08164) |

#### Latent Working Memory

| Year | Paper | Links |
|------|-------|-------|
| 2025 | Titans: Learning to Memorize at Test Time | [arXiv](https://arxiv.org/abs/2501.00663) |
| 2025 | MemoRAG: Boosting Long Context Processing with Global Memory-Enhanced RAG | [ACM](https://doi.org/10.1145/3696410.3714805) |
| 2025 | LM2: Large Memory Models | [arXiv](https://arxiv.org/abs/2502.06049) |
| 2025 | H2O: Heavy-Hitter Oracle for Efficient Generative Inference | [NeurIPS](http://papers.nips.cc/paper_files/paper/2023/hash/6ceefa7b15572587b78ecfcebb2827f8-Abstract-Conference.html) |
| 2024 | SnapKV: LLM Knows What You are Looking for Before Generation | [NeurIPS](http://papers.nips.cc/paper_files/paper/2024/hash/28ab418242603e0f7323e54185d19bde-Abstract-Conference.html) |
| 2024 | Adapting Language Models to Compress Contexts | [EMNLP](https://doi.org/10.18653/v1/2023.emnlp-main.232) |
| 2023 | In-Context Autoencoder for Context Compression in LLMs | [arXiv](https://arxiv.org/abs/2307.06945) |
| 2022 | Memorizing Transformers | [OpenReview](https://openreview.net/forum?id=TrjbxzRcnf-) |

---

## 🛠️ Benchmarks & Frameworks

### Open-Source Memory Frameworks

| Framework | Description | Links |
|-----------|-------------|-------|
| **Mem0** | Production-ready memory for AI agents | [GitHub](https://github.com/mem0ai/mem0) |
| **MemGPT/Letta** | LLMs as operating systems with memory management | [GitHub](https://github.com/cpacker/MemGPT) |
| **Zep** | Temporal knowledge graph for agent memory | [GitHub](https://github.com/getzep/zep) |
| **LangMem** | Long-term memory for LangChain agents | [Docs](https://langchain-ai.github.io/langmem/) |

### Evaluation Benchmarks

| Benchmark | Focus | Links |
|-----------|-------|-------|
| **LoCoMo** | Long-context memory in conversations | [Paper](https://arxiv.org/abs/2402.17753) |
| **LongMemEval** | Long-term memory evaluation | [Paper](https://arxiv.org/abs/2410.10813) |
| **LOCOMO** | Multi-session dialogue memory | [Paper](https://arxiv.org/abs/2402.17753) |

---

## 🎮 Applications

Memory mechanisms are crucial across various LLM agent applications:

| Domain | Description | Key Papers |
|--------|-------------|------------|
| **🎭 Role-Playing** | Maintaining consistent character personas | Character-LLM, ChatHaruhi, RoleLLM |
| **🌐 Social Simulation** | Simulating human social behaviors | Generative Agents, OASIS, S³ |
| **🤝 Personal Assistants** | Learning user preferences over time | MemoryBank, Mem0, A-MEM |
| **🎮 Open-World Games** | Accumulating skills and world knowledge | Voyager, GITM, JARVIS-1 |
| **💻 Code Generation** | Iterative debugging and improvement | ChatDev, MetaGPT, Reflexion |
| **📊 Recommendation** | Personalizing suggestions based on history | RecMind, InteRecAgent |
| **🏥 Expert Systems** | Domain-specific knowledge management | HuaTuo, InvestLM |
| **🌐 Web Agents** | Navigating and automating web tasks | Agent S, SkillWeaver, UFO2 |

---

## 🔮 Future Directions

Based on current research, promising future directions include:

| Direction | Description |
|-----------|-------------|
| **🤖 Memory Automation** | Reducing manual design of memory systems |
| **🎯 RL Integration** | Using reinforcement learning for memory optimization |
| **🖼️ Multimodal Memory** | Extending beyond text to images, audio, video |
| **👥 Multi-Agent Memory** | Shared and distributed memory across agent teams |
| **🔒 Trustworthiness** | Privacy, security, and reliability of agent memories |
| **⚡ Efficiency** | Scalable long-term memory for extended operations |
| **🧪 Benchmarking** | Standardized evaluation protocols |

---

## 📚 References

### Primary Surveys

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

### Survey Repositories

- [LLM_Agent_Memory_Survey](https://github.com/nuster1128/LLM_Agent_Memory_Survey) - Zhang et al.
- [Agent-Memory-Paper-List](https://github.com/Shichun-Liu/Agent-Memory-Paper-List) - Hu et al.

---

## 🤝 Contributing

Contributions are welcome! If you'd like to add new papers, fix errors, or suggest improvements:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/add-paper`)
3. Make your changes
4. Submit a pull request

Please ensure any added papers include:
- Full paper title with year
- Links to paper (arXiv/venue) and code (if available)
- Appropriate categorization by Form × Function

---

## 📄 Citation

If you find this resource helpful, please consider citing:

```bibtex
@misc{memoryisawesome2024,
  title={Memory is Awesome: A Comprehensive Resource on LLM-based Agent Memory},
  author={SuperMadee},
  year={2024},
  howpublished={\url{https://github.com/SuperMadee/MemoryIsAwesome}}
}
```

---

<p align="center">
  <strong>⭐ Star this repo if you find it helpful!</strong>
</p>

<p align="center">
  Made with ❤️ for the LLM Agent Research Community
</p>
