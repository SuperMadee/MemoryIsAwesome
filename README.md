<h1 align="center">🧠 Memory is Awesome</h1>

<p align="center">
  <strong>Your Guide to Memory in Foundation Model Agents</strong>
</p>

<p align="center">
  <em>"Without memory, there is no culture. Without memory, there would be no civilization, no society, no future."</em><br/>
  — Elie Wiesel
</p>

<p align="center">
  <a href="#-paper-collection"><img src="https://img.shields.io/badge/Papers-520+-blue" alt="Papers"></a>
  <a href="#-benchmarks--evaluation"><img src="https://img.shields.io/badge/Benchmarks-110+-green" alt="Benchmarks"></a>
  <a href="#datasets"><img src="https://img.shields.io/badge/Datasets-60+-teal" alt="Datasets"></a>
  <a href="#%EF%B8%8F-open-source-frameworks"><img src="https://img.shields.io/badge/Frameworks-30+-orange" alt="Frameworks"></a>
  <a href="#-references"><img src="https://img.shields.io/badge/References-25+-purple" alt="References"></a>
</p>

---

## 📖 Table of Contents

- [Introduction](#-introduction)
- [What is Agent Memory?](#-what-is-agent-memory)
- [Unified Taxonomy](#%EF%B8%8F-unified-taxonomy)
  - [Memory Forms](#-memory-forms-what-carries-memory)
  - [Memory Functions](#-memory-functions-why-agents-need-memory)
  - [Memory Dynamics](#-memory-dynamics-how-memory-evolves)
- [Paper Collection](#-paper-collection)
  - [Factual Memory](#-factual-memory)
  - [Experiential Memory](#-experiential-memory)
  - [Working Memory](#-working-memory)
- [Spatial Memory for Mobile Robots](#-spatial-memory-for-mobile-robots)
  - [Spatial Memory Representations](#spatial-memory-representations)
  - [Metric-Semantic and Open-Vocabulary Maps](#metric-semantic-and-open-vocabulary-maps)
  - [3D Scene Graphs and Hierarchical Memory](#3d-scene-graphs-and-hierarchical-memory)
  - [Topological, Episodic and Spatio-Temporal Memory](#topological-episodic-and-spatio-temporal-memory)
  - [Memory in Navigation Foundation Models](#memory-in-navigation-foundation-models)
  - [Neuro-Inspired and Classical Spatial Memory](#neuro-inspired-and-classical-spatial-memory)
  - [Spatial Memory Benchmarks](#spatial-memory-benchmarks)
  - [Spatial Memory Datasets](#spatial-memory-datasets)
- [Benchmarks & Evaluation](#-benchmarks--evaluation)
  - [Datasets](#datasets)
- [Open-Source Frameworks](#%EF%B8%8F-open-source-frameworks)
- [Applications](#-applications)
- [Future Directions](#-future-directions)
- [References](#-references)
- [Citation](#-citation)
- [Contributing](#-contributing)

---

## 🎯 Introduction

Foundation model-based agents have emerged as a transformative paradigm in AI research. Unlike vanilla foundation models, these agents possess **self-evolving capabilities** that enable them to solve real-world problems requiring long-term, complex interactions with their environment.

**Memory** is the cornerstone of these agents—it's what makes an agent truly an *agent*. Memory underpins the ability to perform long-horizon reasoning, adapt continually, and interact effectively with complex environments.

### 📊 Repository Highlights

This repository collects agent memory research, featuring:

- **520+ papers** spanning from foundational works (Neural Turing Machines, 2014) to recent research (October 2026)
- **Unified taxonomy** organizing research by Forms × Functions × Dynamics
- **Spatial memory for mobile robots**: 112+ papers on maps, 3D scene graphs, topological/episodic memory and navigation foundation models, with 43+ benchmarks and 48+ datasets
- **110+ benchmarks** for evaluating memory capabilities (LoCoMo, LongMemEval-V2, MemoryArena, BEAM, OpenEQA, GOAT-Bench, etc.)
- **60+ datasets** for training and evaluating memory (MSC, Conversation Chronicles, Ego4D, HM3D, ScanNet++, etc.)
- **30+ open-source frameworks** (Mem0, Letta, Zep/Graphiti, MemOS, Cognee, HippoRAG, etc.)
- **25+ references** including surveys synthesizing the field's evolution

### 🔬 Coverage Areas

| Category | Description | Key Topics |
|----------|-------------|------------|
| **🔤 Token-level Memory** | Explicit, discrete text/symbols | RAG (Self-RAG, CRAG, DPR), knowledge graphs, episodic stores, conversation history |
| **⚙️ Parametric Memory** | Knowledge encoded in weights | Model editing (ROME, MEMIT, SERAC), LoRA adapters, continual learning (EWC, iCaRL) |
| **🧬 Latent Memory** | Compressed hidden states | KV cache (StreamingLLM, SnapKV), state space models (Mamba, H3, Hyena, Griffin), memory tokens |
| **🤖 Multi-Agent Memory** | Shared knowledge across agents | G-Memory, collaborative memory, AgentVerse, AutoGen, memory-as-a-service |
| **🧭 Spatial Memory** | Maps, graphs and implicit memory for mobile robots | Open-vocabulary maps (VLMaps, ConceptFusion), 3D scene graphs (Hydra, ConceptGraphs, HOV-SG), topological/episodic memory (ReMEmbR, Embodied-RAG), navigation foundation models (NaVid, StreamVLN) |
| **🏠 Embodied Memory** | Physical world interaction | Spatial memory, RT-1/RT-2, PaLM-E, SayCan, robotic manipulation |
| **👤 Personalization** | User preference learning | Long-term dialogue, LaMP/LongLaMP benchmarks, affective memory, user profiles |

This repository synthesizes insights from surveys on agent memory (see [References](#-references)).

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

This repository organizes agent memory research through three unified lenses: **Forms**, **Functions**, and **Dynamics**.

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
| **Complete Interactions** | Store all past agent-environment interactions | Full audit trail, full history |
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

> **Factual Memory** (also called Semantic Memory) stores general world knowledge, facts, and information about entities and their relationships. It answers "what do I know?" and provides the knowledge base that agents draw upon for reasoning and question-answering.

#### 🔤 **Token-level Factual Memory**

> **Token-level Factual Memory** stores world knowledge, facts, and semantic information as explicit text or structured data (e.g., knowledge graphs, databases, retrieved documents). This is the most common form of external memory in RAG systems, where facts are retrieved as text chunks and injected into the context window.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| MemAgent (Provider Routing) | 2026 | Treats memory as a routing problem, using content-aware probing to choose among 13 memory methods (trajectories, reflections, skills, structured knowledge); reports a 10.0% average accuracy gain across three benchmarks. Distinct from the 2025 MemAgent. | [[arXiv]](https://arxiv.org/abs/2609.32521) |
| JitMem | 2026 | Just-in-time memory that moves curation from write time to read time: raw trajectories are retained and task-adaptive summaries are synthesized on demand by a learned curator, avoiding information loss at ingestion. | [[arXiv]](https://arxiv.org/abs/2609.27334) |
| CoMem | 2026 | Separates private agent memory from a curated collective pool in evolutionary multi-agent systems, with promotion gates and parallel dual-stream retrieval to avoid memory pollution; reports gains on ALFWorld and PDDL. | [[arXiv]](https://arxiv.org/abs/2609.15009) |
| Agent Zero Memory | 2026 | Provenance-aware memory combining an episodic timeline, an entity-event graph and curated documentary memory, queried by concurrent agentic hybrid search with citation-locked answers; reports 95.60% on LongMemEval and 93.60% on LoCoMo. | [[arXiv]](https://arxiv.org/abs/2608.29606) |
| LycheeMemory V2 | 2026 | Consolidates memory at the level of semantically coherent dialogue segments using embedding-based boundary detection, with single-step query planning over structured indexes; reports 86% fewer construction tokens than A-MEM. | [[arXiv]](https://arxiv.org/abs/2608.12990) |
| Filesystem-Based Memory | 2026 | Formalizes filesystem-hierarchy agent memory with separate management, search and execution roles over one store; finds organized stores cut retrieval cost, but organization degrades over time unless the managing agent is the strongest model. | [[arXiv]](https://arxiv.org/abs/2607.26637) |
| SPORE | 2026 | Persistence-based memory extraction attack via compromised tool responses: injects persistent commands into short-term memory and frames extraction as embedding-space coverage optimization, extracting up to 80% of stored records. | [[arXiv]](https://arxiv.org/abs/2607.23444) |
| LazyMem | 2026 | Defers memory construction to query time: retrieves a broad candidate pool, then a trained lightweight model selectively compresses query-relevant content, reaching strong LongMemEval accuracy with 21x fewer context tokens than the strongest baseline. | [[arXiv]](https://arxiv.org/abs/2607.22690) [[GitHub]](https://github.com/allacnobug/LazyMem) |
| MOSAIC | 2026 | Typed entity-graph memory with conflict detection at ingestion and hash-accelerated lookup instead of LLM-based retrieval; reports 89.35% on LoCoMo and detection of 66% of injected clinical conflicts. | [[arXiv]](https://arxiv.org/abs/2607.16211) |
| MemCon | 2026 | Formulates memory access as an MDP and wraps existing memory backends with a lightweight contextual-bandit policy deciding when, what and how much to retrieve; reports up to 15.2-point task-success gains with fewer tokens. | [[arXiv]](https://arxiv.org/abs/2607.13591) [[GitHub]](https://github.com/ericjiang18/MemCon/) |
| SelfMem | 2026 | Lets agents discover their own memory strategies through exploration and feedback instead of following fixed protocols; reports large improvements over baselines at 100K, 500K and 1M-token conversation scales on BEAM. | [[arXiv]](https://arxiv.org/abs/2607.03726) |
| A-MemGuard | 2026 | Proactive defense for agent memory using consensus-based validation across multiple retrieved memories and a dual-memory structure that stores detected failures as lessons; reports over 95% reduction in attack success while preserving utility. | [[ICML]](https://icml.cc/virtual/2026/poster/61006) [[GitHub]](https://github.com/TangciuYueng/AMemGuard/) |
| MemClaw | 2026 | Systems-level primitives for governed multi-agent shared memory: scoped retrieval, temporal supersession, provenance tracking and policy-governed propagation, with full derivation-chain reconstruction and zero cross-fleet leakage reported. | [[arXiv]](https://arxiv.org/abs/2606.24535) |
| MRAgent | 2026 | Graph memory that treats recall as active reconstruction: a Cue-Tag-Content graph is traversed and adapted during LLM reasoning instead of one-shot retrieval; reports up to 23% improvement at reduced cost (ICML 2026). | [[arXiv]](https://arxiv.org/abs/2606.06036) |
| MemPoison | 2026 | Trojan attack that plants triggerable backdoors in agent memory through ordinary conversation, by semantically binding trigger and payload and mimicking named entities to survive memory rewriting; attack success reaches 0.95. | [[arXiv]](https://arxiv.org/abs/2605.29960) |
| MAGIC-Video | 2026 | Multimodal memory graph unifying episodic, semantic and visual content plus narrative chains for entity biographies and recurring events in ultra-long video; reports a 10.1-point gain over agentic baselines on EgoLifeQA. | [[arXiv]](https://arxiv.org/abs/2605.08271) [[GitHub]](https://github.com/lijiazheng0917/MAGIC-video) |
| Memanto | 2026 | Typed semantic memory with information-theoretic retrieval that replaces knowledge-graph pipelines, using single-query retrieval with zero ingestion overhead on long-term memory benchmarks. | [[arXiv]](https://arxiv.org/abs/2604.22085) |
| HiGMem | 2026 | Two-level event-turn memory in which the LLM uses event summaries as anchors to select relevant dialogue turns; retrieves far fewer turns and raises adversarial F1 on LoCoMo10 from 0.54 to 0.78. | [[arXiv]](https://arxiv.org/abs/2604.18349) [[GitHub]](https://github.com/ZeroLoss-Lab/HiGMem) |
| StreamMeCo | 2026 | Compresses graph-structured memory of streaming-video agents via edge-free minmax sampling, edge-aware weight pruning and time-decay retrieval; 1.87x faster retrieval at 70% graph compression (ACL 2026 Findings). | [[arXiv]](https://arxiv.org/abs/2604.09000) [[GitHub]](https://github.com/Celina-love-sweet/StreamMeCo) |
| FileGram | 2026 | Grounds personalization in file-system behavioural traces: FileGramEngine simulates workflows, FileGramBench tests profile reconstruction, and FileGramOS builds user profiles from atomic actions across procedural, semantic and episodic channels. | [[arXiv]](https://arxiv.org/abs/2604.04901) |
| MemMachine | 2026 | Ground-truth-preserving memory that stores complete conversational episodes alongside short-term and profile memory, with contextualized retrieval expanding around matched turns; reports 93.0% on LongMemEval-S with about 80% fewer tokens. | [[arXiv]](https://arxiv.org/abs/2604.04853) |
| MIA | 2026 | Memory Intelligence Agent coupling a non-parametric Memory Manager storing compressed trajectories with a parametric Planner-Executor, trained by alternating RL with test-time learning, bidirectional memory conversion and reflection. | [[arXiv]](https://arxiv.org/abs/2604.04503) |
| MemSkill | 2026 | Recasts memory operations as learnable, evolvable skills: a controller selects memory skills, an LLM executor writes memories, and a designer evolves the skill set from hard cases; improves LoCoMo, LongMemEval, HotpotQA and ALFWorld. | [[arXiv]](https://arxiv.org/abs/2602.02474) [[GitHub]](https://github.com/ViktorAxelsen/MemSkill) |
| Mem-T | 2026 | Autonomous memory agent over a hierarchical memory database, trained with MoT-GRPO, a tree-guided RL scheme that densifies sparse rewards into step-wise supervision; reports up to 14.92% gains with fewer inference tokens. | [[arXiv]](https://arxiv.org/abs/2601.23014) |
| SimpleMem | 2026 | Three-stage pipeline of semantic structured compression, online semantic synthesis to remove redundancy, and intent-aware retrieval planning; reports a 26.4% F1 gain on LoCoMo with up to 30x fewer inference tokens. | [[arXiv]](https://arxiv.org/abs/2601.02553) [[GitHub]](https://github.com/aiming-lab/SimpleMem) |
| EverMemOS | 2026 | Self-organizing memory operating system that converts dialogue into MemCells, consolidates them into thematic MemScenes, and retrieves reconstructed context for reasoning, with user profiling on long-term memory benchmarks. | [[arXiv]](https://arxiv.org/abs/2601.02163) [[GitHub]](https://github.com/EverMind-AI/EverOS) |
| Multi-Layered Memory | 2026 | Decomposes dialogue history into working, episodic, and semantic layers with adaptive retrieval gating and retention regularization, controlling cross-session drift while maintaining bounded context growth. | [[arXiv]](https://arxiv.org/abs/2603.29194) |
| Anatomy of Agentic Memory | 2026 | Taxonomy and empirical analysis of evaluation and system limitations for agentic memory, identifying gaps between current benchmarks and real-world agentic requirements. | [[arXiv]](https://arxiv.org/abs/2602.19320) |
| LRAgent | 2026 | KV cache sharing framework for multi-LoRA agents that decomposes cache into shared base and adapter-dependent components with Flash-LoRA-Attention kernel, reducing memory overhead for multi-agent systems. | [[arXiv]](https://arxiv.org/abs/2602.01053) |
| Agent Memory Below the Prompt | 2026 | Persists each agent's KV cache to disk in 4-bit quantized format for multi-agent LLM inference on edge devices, eliminating redundant prefill computation via direct cache restoration. | [[arXiv]](https://arxiv.org/abs/2603.04428) [[GitHub]](https://github.com/yshk-mxim/agent-memory) |
| AgeMem | 2026 | Unified LTM/STM management integrated into the agent's policy as tool-based actions, enabling autonomous decisions on when to store, retrieve, update, summarize, or discard information. | [[arXiv]](https://arxiv.org/abs/2601.01885) |
| MAGMA | 2026 | Represents each memory item across orthogonal semantic, temporal, causal, and entity graphs with policy-guided traversal, achieving up to 45.5% higher reasoning accuracy while reducing tokens by 95%. | [[arXiv]](https://arxiv.org/abs/2601.03236) [[GitHub]](https://github.com/FredJiang0324/MAMGA) |
| MemMA | 2026 | Plug-and-play multi-agent framework with a Meta-Thinker that steers memory construction and retrieval, plus a backward path that synthesizes probe QA pairs to self-repair the memory bank. | [[arXiv]](https://arxiv.org/abs/2603.18718) [[GitHub]](https://github.com/ventr1c/memma) |
| Memory as Asset | 2026 | Proposes "Memory-as-Asset" paradigm with EvoMap for decentralized knowledge propagation across agents, defining three pillars: Memory in Hand, Memory Group, and Collective Memory Evolution. | [[arXiv]](https://arxiv.org/abs/2603.14212) |
| Multi-Agent Memory (CompArch) | 2026 | Frames multi-agent memory as a computer architecture problem, distinguishing shared vs. distributed memory paradigms and proposing a three-layer memory hierarchy with coherence protocols. | [[arXiv]](https://arxiv.org/abs/2603.10062) |
| A-MAC | 2026 | Decomposes memory value into five interpretable factors (future utility, factual confidence, semantic novelty, temporal recency, content type prior) and uses linear weighted scoring for admission decisions. | [[arXiv]](https://arxiv.org/abs/2603.04549) [[GitHub]](https://github.com/GuilinDev/Adaptive_Memory_Admission_Control_LLM_Agents) |
| ARM | 2026 | Replaces static vector index with dynamic memory governed by consolidation and decay, where frequently retrieved items are protected and rarely used items gradually forgotten. | [[arXiv]](https://arxiv.org/abs/2601.02428) |
| A-RAG | 2026 | Scales agentic RAG via hierarchical retrieval interfaces exposing three levels (keyword_search, semantic_search, chunk_read) directly to the model for adaptive multi-granularity search. | [[arXiv]](https://arxiv.org/abs/2602.03442) [[GitHub]](https://github.com/Ayanami0730/arag) |
| GAM-RAG | 2026 | Gain-adaptive memory mechanism for RAG that adjusts retrieval strategy based on evolving information needs during generation. | [[arXiv]](https://arxiv.org/abs/2603.01783) |
| Structured Linked Data Memory | 2026 | Uses Schema.org markup and dereferenceable entity pages as structured memory layer to improve retrieval accuracy in both standard and agentic RAG systems. | [[arXiv]](https://arxiv.org/abs/2603.10700) |
| RF-Mem | 2026 | Dual-path memory retriever inspired by cognitive dual-process theory combining fast Familiarity recognition with deliberate Recollection chain reconstruction. | [[OpenReview]](https://openreview.net/forum?id=f7p0F2X6XN) [[GitHub]](https://github.com/Zhang-Yingyi/ICLR2026_RF-Mem) |
| GAM | 2025 | General Agentic Memory via just-in-time compilation: a Memorizer keeps lightweight highlights while full history sits in a page-store, and a Researcher agent performs deep-research-style retrieval at query time. | [[arXiv]](https://arxiv.org/abs/2511.18423) |
| O-Mem | 2025 | Introduces a three-component memory framework (Persona Memory, Working Memory, Topical Memory) that dynamically extracts and updates user characteristics through active profiling, enabling hierarchical retrieval of persona attributes and topic-related context for adaptive personalized responses in long-horizon interactions. | [[arXiv]](https://arxiv.org/abs/2511.13593) |
| In Prospect and Retrospect | 2025 | Proposes a dual-phase memory management approach where agents prospectively anticipate future information needs while retrospectively reflecting on past interactions, enabling more coherent and personalized long-term dialogue through selective memory retention and retrieval. | [[ACL]](https://aclanthology.org/2025.acl-long.413/) |
| RCR-Router | 2025 | Addresses context management in multi-agent systems by routing relevant memory segments to appropriate agent roles, reducing redundant context processing while maintaining coherent inter-agent communication through structured memory organization. | [[arXiv]](https://arxiv.org/abs/2508.04903) |
| Livia | 2025 | Creates an augmented reality companion that combines emotion detection with progressive memory compression, allowing the AR agent to maintain long-term emotional context while adapting its responses to user affect states in real-time. | [[arXiv]](https://arxiv.org/abs/2509.05298) |
| D-SMART | 2025 | Combines a Dynamic Structured Memory (DSM) that incrementally builds an OWL-compliant knowledge graph with a Reasoning Tree (RT) for explicit multi-step inference, achieving 48% improvement in dialogue consistency by enabling traceable reasoning over evolving conversational context. | [[arXiv]](https://arxiv.org/abs/2510.13363) |
| WebWeaver | 2025 | Organizes web-scale information into dynamically evolving outline structures during research tasks, enabling LLMs to systematically gather, organize, and synthesize evidence across multiple sources for comprehensive open-ended inquiry. | [[arXiv]](https://arxiv.org/abs/2509.13312) |
| CAM | 2025 | Proposes a constructivist memory framework where agents actively construct understanding by integrating new information with existing knowledge structures, improving reading comprehension through schema-based memory organization rather than passive information storage. | [[arXiv]](https://arxiv.org/abs/2510.05520) |
| Pre-Storage Reasoning | 2025 | Pre-computes and stores reasoning chains about user information at memory write time rather than query time, reducing inference latency while maintaining personalization quality by front-loading computational work to the memory formation phase. | [[arXiv]](https://arxiv.org/abs/2509.10852) |
| LightMem | 2025 | Proposes a parameter-efficient memory augmentation approach that adds minimal computational overhead to base LLMs while enabling effective long-term information retention through compressed memory representations. | [[arXiv]](https://arxiv.org/abs/2510.18866) |
| Mem-α | 2025 | Uses reinforcement learning to train agents to construct optimal memory representations, learning when and what to store through interaction feedback rather than relying on hand-crafted memory formation heuristics. | [[arXiv]](https://arxiv.org/abs/2509.25911) |
| SGMem | 2025 | Structures conversational memory as sentence-level graphs where nodes represent utterances and edges capture semantic relationships, enabling more precise retrieval of relevant dialogue history for context-aware response generation. | [[arXiv]](https://arxiv.org/abs/2509.21212) |
| Nemori | 2025 | Implements self-organizing memory maps inspired by cognitive neuroscience, where memories automatically cluster and reorganize based on semantic similarity and usage patterns without explicit indexing. | [[arXiv]](https://arxiv.org/abs/2508.03341) |
| MOOM | 2025 | Addresses the unique challenges of maintaining character consistency in extended role-playing scenarios through specialized memory maintenance routines that preserve character traits, plot points, and relationship dynamics across hundreds of dialogue turns. | [[arXiv]](https://arxiv.org/abs/2509.11860) |
| Multiple Memory Systems | 2025 | Proposes a multi-system memory architecture inspired by human cognitive models, separating episodic, semantic, and procedural memories with distinct storage and retrieval mechanisms for improved long-term agent performance. | [[arXiv]](https://arxiv.org/abs/2508.15294) |
| Semantic Anchoring | 2025 | Uses linguistic dependency structures and semantic roles as anchors for organizing conversational memory, enabling more precise context retrieval by matching query semantics to stored discourse structures. | [[arXiv]](https://arxiv.org/abs/2508.12630) |
| Memento 2 | 2025 | Learning by stateful reflective memory with continual experiential updates, extending the original Memento framework with structured memory states. | [[arXiv]](https://arxiv.org/abs/2512.22716) |
| Recommender AI Agent | 2025 | Combines LLM reasoning with user interaction history to provide contextually-aware recommendations, maintaining memory of user preferences, past interactions, and feedback to improve recommendation relevance over time. | [[ACM]](https://doi.org/10.1145/3731446) |
| ComoRAG | 2025 | Organizes retrieved information using cognitive memory principles (episodic, semantic, working memory) to maintain narrative state across complex multi-turn reasoning tasks, improving coherence in story understanding and question answering. | [[arXiv]](https://arxiv.org/abs/2508.10419) |
| Seeing, Listening, Remembering | 2025 | Extends agent memory to handle multimodal inputs (vision, audio, text), creating unified memory representations that enable cross-modal retrieval and reasoning for more comprehensive environmental understanding. | [[arXiv]](https://arxiv.org/abs/2508.09736) |
| Memory-R1 | 2025 | Trains agents to autonomously decide when to read, write, or forget memories using reinforcement learning, optimizing memory operations for downstream task performance rather than relying on fixed heuristics. | [[arXiv]](https://arxiv.org/abs/2508.19828) |
| Intrinsic Memory Agents | 2025 | Designs agents with built-in memory capabilities that don't require external databases, using structured internal representations to maintain context across heterogeneous multi-agent interactions. | [[arXiv]](https://arxiv.org/abs/2508.08997) |
| MIRIX | 2025 | Designs a shared memory infrastructure for multi-agent systems that enables agents to selectively share, query, and update collective knowledge while maintaining individual agent memory boundaries. | [[arXiv]](https://arxiv.org/abs/2507.07957) |
| G-Memory | 2025 | Introduces hierarchical memory tracing for multi-agent coordination, where shared memories are organized at multiple abstraction levels to enable both individual agent reasoning and collective knowledge aggregation across agent teams. | [[arXiv]](https://arxiv.org/abs/2506.07398) |
| H-MEM | 2025 | Implements multi-level memory abstraction where lower levels store raw experiences and higher levels contain progressively summarized knowledge, balancing storage efficiency with retrieval precision. | [[arXiv]](https://arxiv.org/abs/2507.22925) |
| Embodied Agents Meet Personalization | 2025 | Investigates how embodied agents can leverage memory to provide personalized assistance in physical environments, tracking user preferences, routines, and environmental context for proactive help. | [[arXiv]](https://arxiv.org/abs/2505.16348) |
| MemGuide | 2025 | Introduces intent-aware memory retrieval that considers the agent's current goals when selecting relevant memories, improving task completion by prioritizing goal-relevant historical information. | [[arXiv]](https://arxiv.org/abs/2505.20231) |
| SeCom | 2025 | Proposes semantic compression techniques for memory construction that preserve essential user information while reducing storage requirements, combined with retrieval methods optimized for conversational coherence. | [[OpenReview]](https://openreview.net/forum?id=xKDZAW0He3) |
| Embodied VideoAgent | 2025 | Processes continuous egocentric video streams to build persistent environmental memory, enabling embodied agents to recall spatial layouts, object locations, and past observations for navigation and manipulation tasks. | [[arXiv]](https://arxiv.org/abs/2501.00358) |
| Human-inspired Episodic Memory | 2025 | Models episodic memory formation and retrieval after human cognitive processes, enabling LLMs to handle effectively infinite context by selectively encoding and retrieving experience-based memories. | [[OpenReview]](https://openreview.net/forum?id=BI2int5SAC) |
| Zep | 2025 | Presents Graphiti, a temporal knowledge graph architecture that models agent memory as evolving entity-relationship graphs with temporal annotations, enabling complex temporal reasoning and outperforming MemGPT on the LongMemEval benchmark for enterprise use cases. | [[arXiv]](https://arxiv.org/abs/2501.13956) |
| MemR3 | 2025 | Introduces a three-stage retrieval process (Retrieve-Reflect-Refine) where agents reflect on initial retrieval results to identify gaps and iteratively improve memory selection for complex reasoning tasks. | [[arXiv]](https://arxiv.org/abs/2512.20237) |
| Memoria | 2025 | Combines vector embeddings with knowledge graph structures to create a scalable memory framework that captures both semantic similarity and explicit relational knowledge for personalized AI interactions across extended user sessions. | [[arXiv]](https://arxiv.org/abs/2512.12686) |
| CogMem | 2025 | Implements a cognitively-motivated memory architecture with separate buffers for working memory, episodic traces, and semantic knowledge to support sustained reasoning across extended multi-turn interactions. | [[arXiv]](https://arxiv.org/abs/2512.14118) |
| Memory Bear | 2025 | Proposes a cognitively-inspired memory architecture modeled after human memory systems (sensory, short-term, long-term) with attention-based gating mechanisms to simulate memory formation, consolidation, and retrieval processes toward more general intelligence. | [[arXiv]](https://arxiv.org/abs/2512.20651) |
| Hindsight | 2025 | Develops a three-phase memory system where agents retain important experiences, recall relevant memories through similarity matching, and reflect on past interactions to extract generalizable insights for improved future decision-making. | [[arXiv]](https://arxiv.org/abs/2512.12818) |
| GR-Agent | 2025 | Combines graph-based knowledge representation with adaptive memory to enable reasoning under uncertainty, updating beliefs as new information arrives while maintaining consistency with prior knowledge. | [[arXiv]](https://arxiv.org/abs/2512.14766) |
| Collaborative Memory | 2025 | Enables multiple users to share agent memories with fine-grained access control, supporting collaborative scenarios where shared context improves collective task performance while respecting privacy boundaries. | [[arXiv]](https://arxiv.org/abs/2505.18279) |
| Memory as a Service | 2025 | Proposes memory-as-a-service architecture where memory operations are decoupled from agent logic, allowing multiple agents to access shared memory infrastructure through standardized APIs. | [[arXiv]](https://arxiv.org/abs/2506.22815) |
| A-MEM | 2025 | Implements a Zettelkasten-inspired memory system where agents autonomously organize memories through dynamic indexing and linking, creating interconnected knowledge networks with structured attributes (descriptions, keywords, tags) that evolve as new memories trigger updates to existing representations. | [[arXiv]](https://arxiv.org/abs/2502.12110) |
| Unveiling Privacy Risks | 2025 | Analyzes privacy vulnerabilities in LLM memory systems, including risks of memory extraction attacks, unintended information leakage, and proposes mitigation strategies for secure memory design. | [[arXiv]](https://arxiv.org/abs/2502.13172) |
| Mem2Ego | 2025 | Creates a two-level memory system combining global spatial maps with egocentric observations for embodied navigation, enabling vision-language models to reason about both local surroundings and global navigation goals. | [[arXiv]](https://arxiv.org/abs/2502.14254) |
| Mem0 | 2025 | Introduces a production-scale memory architecture with extraction and update phases that dynamically consolidate salient conversational facts, plus a graph-based variant (Mem0g) for relational reasoning, achieving 26% accuracy improvement over OpenAI with 91% lower latency and 90% token savings. | [[arXiv]](https://arxiv.org/abs/2504.19413) [[GitHub]](https://github.com/mem0ai/mem0) |
| From RAG to Memory | 2025 | Proposes evolving RAG systems into true memory systems through non-parametric continual learning, where retrieved knowledge is integrated and updated without model retraining. | [[arXiv]](https://arxiv.org/abs/2502.14802) |
| ENGRAM | 2025 | Proposes a lightweight memory system that organizes conversations into three canonical types (episodic, semantic, procedural) through a single router and retriever, demonstrating that careful memory typing enables effective long-term memory without complex architectures. | [[arXiv]](https://arxiv.org/abs/2511.12960) |
| SimpleDoc | 2025 | Combines visual and textual cues for efficient document memory and retrieval, enabling accurate page-level retrieval in large document collections for question answering tasks. | [[arXiv]](https://arxiv.org/abs/2506.14035) [[GitHub]](https://github.com/ag2ai/SimpleDoc) |
| Zero-RAG | 2025 | Eliminates redundancy in retrieved memories by deduplicating and compressing overlapping information, improving both efficiency and coherence of memory-augmented generation. | [[arXiv]](https://arxiv.org/abs/2511.00505) |
| RAG with Hierarchical Knowledge | 2025 | Organizes retrieved knowledge in hierarchical structures from specific facts to general concepts, enabling more appropriate granularity selection based on query requirements. | [[arXiv]](https://arxiv.org/abs/2503.10150) |
| RoboMemory | 2025 | Implements separate memory systems for spatial, object, and interaction memories in robotic agents, inspired by brain region specialization for different types of environmental knowledge. | [[arXiv]](https://arxiv.org/abs/2508.01415) |
| Ella | 2025 | Creates an embodied agent that learns continuously from environmental interactions, building both episodic memories of specific experiences and semantic knowledge abstracted across episodes. | [[arXiv]](https://arxiv.org/abs/2506.24019) |
| Mind Palace | 2025 | Uses spatial memory organization inspired by the method of loci, where information is anchored to locations in a mental spatial map for improved recall during long-horizon embodied tasks. | [[arXiv]](https://arxiv.org/abs/2507.12846) |
| Neural Brain | 2025 | Implements multiple interacting neural-inspired modules (perception, memory, planning, action) with biologically plausible connectivity patterns for more human-like embodied agent behavior. | [[arXiv]](https://arxiv.org/abs/2505.07634) |
| LLM-Empowered Embodied | 2025 | Augments robot task planners with LLM-based memory that stores object locations, user preferences, and successful action sequences for more efficient household task completion. | [[arXiv]](https://arxiv.org/abs/2504.21716) |
| Graph2Nav | 2025 | Constructs 3D scene graphs from robot observations as navigational memory, encoding object identities, spatial relationships, and traversability for efficient path planning. | [[arXiv]](https://arxiv.org/abs/2504.16782) |
| Episodic Memory for Video | 2025 | Develops episodic memory representations specifically designed for video content, capturing temporal event structure and enabling efficient retrieval for long-form video question answering. | [[arXiv]](https://arxiv.org/abs/2508.09486) |
| Pre-training Limited Memory | 2025 | Pre-trains language models with constrained internal memory that must learn to effectively utilize external knowledge stores, improving retrieval and integration of external information. | [[arXiv]](https://arxiv.org/abs/2505.15962) |
| Memoro | 2024 | Presents a wearable audio-based memory assistant that uses LLMs to infer user memory needs in conversational context, featuring Query and Queryless interaction modes that reduce device interaction time by 85% while maintaining conversation quality in real-time social settings. | [[ACM]](https://doi.org/10.1145/3613904.3642450) |
| MovieChat | 2024 | Addresses long video understanding by converting dense frame-level tokens into sparse memory representations through a memory consolidation mechanism, enabling efficient processing of hour-long videos while preserving semantically important temporal information. | [[CVPR]](https://doi.org/10.1109/CVPR52733.2024.01725) |
| RoleLLM | 2024 | Provides systematic evaluation and improvement methods for role-playing capabilities, including memory mechanisms for maintaining character knowledge, speaking styles, and behavioral patterns across conversations. | [[ACL]](https://doi.org/10.18653/v1/2024.findings-acl.878) |
| AI PERSONA | 2024 | Develops continuous personalization mechanisms that allow LLMs to adapt to individual users over extended periods, learning communication styles, preferences, and knowledge gaps through ongoing interactions. | [[arXiv]](https://arxiv.org/abs/2412.13103) |
| OASIS | 2024 | Creates large-scale social simulations with up to one million interacting agents to study emergent social phenomena, collective behavior patterns, and information propagation in artificial societies. | [[arXiv]](https://arxiv.org/abs/2411.11581) |
| Memolet | 2024 | Enables users to explicitly save, organize, and reuse fragments of past AI conversations as reusable memory units, giving users agency over which conversational knowledge persists and how it's applied. | [[ACM]](https://doi.org/10.1145/3654777.3676388) |
| Dynamic Tree Memory | 2024 | Implements MemTree, a tree-structured memory that dynamically organizes information hierarchically with varying abstraction levels across depths, outperforming flat memory approaches on multi-turn dialogue and document QA benchmarks. | [[arXiv]](https://arxiv.org/abs/2410.14052) |
| Inner Loop Query | 2024 | Improves long-context processing by implementing inner query loops that iteratively refine memory retrieval, enabling more accurate information extraction from extended contexts through progressive focusing. | [[arXiv]](https://arxiv.org/abs/2410.12859) |
| Editable Memory Graphs | 2024 | Combines graph-based memory structures with RAG, allowing users to directly edit, add, or remove memory nodes and relationships for fine-grained control over agent personalization. | [[arXiv]](https://arxiv.org/abs/2409.19401) |
| AriGraph | 2024 | Constructs dynamic knowledge graphs from agent experiences that serve as world models, combining episodic memory of specific events with structured relational knowledge for improved reasoning. | [[arXiv]](https://arxiv.org/abs/2407.04363) |
| ChatHaruhi | 2024 | Creates faithful recreations of anime characters using character-specific memory banks containing dialogue patterns, personality traits, and relationship knowledge extracted from source material. | [[arXiv]](https://arxiv.org/abs/2308.09597) |
| Context and Time Sensitive Memory | 2024 | Incorporates temporal awareness into memory retrieval by weighting memories based on both semantic relevance and temporal proximity, enabling more contextually appropriate recall for time-sensitive conversational tasks. | [[arXiv]](https://arxiv.org/abs/2406.00057) |
| Hierarchical Aggregate Tree | 2024 | Organizes memories in a tree structure where leaf nodes contain raw information and parent nodes contain progressively aggregated summaries, enabling efficient retrieval at multiple granularity levels. | [[arXiv]](https://arxiv.org/abs/2406.06124) |
| Timeline-based Memory | 2024 | Organizes conversational memories along temporal timelines with event markers, enabling agents to reason about the sequence and duration of past interactions for more coherent lifelong dialogue. | [[arXiv]](https://arxiv.org/abs/2406.10996) |
| HippoRAG | 2024 | Draws from hippocampal memory indexing theory to create a retrieval system using knowledge graphs as an artificial hippocampal index, enabling pattern separation and completion for more human-like associative memory retrieval in knowledge-intensive tasks. | [[arXiv]](https://arxiv.org/abs/2405.14831) [[GitHub]](https://github.com/OSU-NLP-Group/HippoRAG) |
| Memory Sharing | 2024 | Enables agents to share relevant memories with each other through controlled access mechanisms, improving collective task performance while maintaining appropriate information boundaries between agents. | [[arXiv]](https://arxiv.org/abs/2404.09982) |
| Knowledge Graph Tuning | 2024 | Updates knowledge graph representations in real-time based on user feedback, enabling dynamic personalization without model retraining by modifying the structured knowledge the LLM retrieves. | [[arXiv]](https://arxiv.org/abs/2405.19686) |
| Graph RAG | 2024 | Builds entity knowledge graphs from documents and pregenerates community summaries, enabling global sensemaking queries over million-token corpora through map-reduce processing of community-level partial responses. | [[arXiv]](https://arxiv.org/abs/2404.16130) |
| User Behavior Simulation | 2024 | Creates realistic user simulators by equipping LLM agents with memory of past behaviors, preferences, and interaction patterns for more accurate evaluation of recommendation and dialogue systems. | [[arXiv]](https://arxiv.org/abs/2306.02552) [[GitHub]](https://github.com/RUC-GSAI/YuLan-Rec) |
| ReMEmbR | 2024 | Constructs spatio-temporal memory graphs from robot exploration that capture both spatial layouts and temporal observations, enabling long-horizon reasoning for navigation tasks. | [[arXiv]](https://arxiv.org/abs/2409.13682) |
| Episodic Memory Verbalization | 2024 | Verbalizes robot experiences into hierarchical episodic memories at multiple abstraction levels, from low-level sensory observations to high-level activity summaries for improved experience recall. | [[arXiv]](https://arxiv.org/abs/2409.17702) |
| Mobility VLA | 2024 | Combines vision-language models with topological memory graphs for instruction-following navigation, maintaining spatial memory of visited locations for efficient path planning. | [[arXiv]](https://arxiv.org/abs/2407.07775) |
| CRAG | 2024 | Introduces a corrective mechanism that evaluates retrieval quality and triggers web search when initial retrieval is insufficient, improving robustness of RAG systems through dynamic retrieval correction. | [[arXiv]](https://arxiv.org/abs/2401.15884) [[GitHub]](https://github.com/HuskyInSalt/CRAG) |
| CAMEL | 2023 | Introduces role-playing communication framework where AI agents engage in cooperative task-solving through structured dialogue, demonstrating emergent collaborative behaviors and enabling study of multi-agent social dynamics. | [[NeurIPS]](https://proceedings.neurips.cc/paper_files/paper/2023/hash/a3621ee907def47c1b952ade25c67571-Abstract-Conference.html) [[GitHub]](https://github.com/camel-ai/camel) |
| AutoGen | 2023 | Provides a framework for building multi-agent applications where LLM agents can converse, collaborate, and leverage tools through customizable conversation patterns, enabling complex workflows through agent cooperation. | [[arXiv]](https://arxiv.org/abs/2308.08155) [[GitHub]](https://github.com/microsoft/autogen) |
| MemGPT | 2023 | Reconceptualizes LLM memory management as a virtual memory system with hierarchical tiers (main context as RAM, external storage as disk), using function calls for self-directed memory operations to enable unbounded context handling in extended conversations and document analysis. | [[arXiv]](https://arxiv.org/abs/2310.08560) [[GitHub]](https://github.com/cpacker/MemGPT) |
| GameGPT | 2023 | Coordinates multiple specialized agents (designer, programmer, artist) with shared memory of game requirements and progress for collaborative game development tasks. | [[arXiv]](https://arxiv.org/abs/2310.08067) |
| CALYPSO | 2023 | Maintains narrative memory of game state, character actions, and world lore to assist tabletop RPG dungeon masters with consistent storytelling and rule adjudication. | [[AIIDE]](https://doi.org/10.1609/aiide.v19i1.27534) |
| Lyfe Agents | 2023 | Creates efficient social agents with compressed memory representations that enable real-time interaction while preserving essential personality and relationship information. | [[arXiv]](https://arxiv.org/abs/2310.02172) |
| MetaGPT | 2023 | Encodes Standardized Operating Procedures (SOPs) into prompt sequences for multi-agent collaboration, using assembly line paradigms where agents with specialized roles (Product Manager, Architect, Engineer) produce structured outputs to reduce cascading hallucinations in complex tasks. | [[arXiv]](https://arxiv.org/abs/2308.00352) |
| MemoChat | 2023 | Fine-tunes LLMs through iterative memorization-retrieval-response cycles using structured memos, with tailored instructions for each stage that teach models to memorize and retrieve past dialogues for enhanced long-range conversation consistency. | [[arXiv]](https://arxiv.org/abs/2308.08239) [[GitHub]](https://github.com/LuJunru/MemoChat) |
| MPC | 2023 | Decomposes long conversation handling into modular prompted components including memory management, topic tracking, and response generation for improved open-domain dialogue. | [[ACL]](https://doi.org/10.18653/v1/2023.findings-acl.277) [[GitHub]](https://github.com/krafton-ai/MPC) |
| Recursive Summarization | 2023 | Applies recursive summarization to conversation history, creating hierarchical summaries that preserve key information while fitting within context limits for extended dialogues. | [[arXiv]](https://arxiv.org/abs/2308.15022) |
| S³ | 2023 | Simulates social networks where agents maintain memory of relationships, shared experiences, and social context for realistic modeling of information spread and social dynamics. | [[arXiv]](https://arxiv.org/abs/2307.14984) |
| RecurrentGPT | 2023 | Uses recurrent memory mechanisms to generate coherent long-form text by maintaining paragraph-level memory that tracks plot, characters, and narrative threads across unlimited length. | [[arXiv]](https://arxiv.org/abs/2305.13304) |
| MemoryBank | 2023 | Implements a psychologically-inspired memory system using the Ebbinghaus Forgetting Curve to selectively forget and reinforce memories based on time elapsed and significance, enabling LLMs to build user portraits and provide empathetic, personalized companionship. | [[arXiv]](https://arxiv.org/abs/2305.10250) [[GitHub]](https://github.com/zhongwanjun/MemoryBank-SiliconFriend) |
| RET-LLM | 2023 | Proposes a general-purpose external memory interface allowing LLMs to explicitly read from and write to persistent storage, enabling knowledge accumulation across sessions. | [[arXiv]](https://arxiv.org/abs/2305.14322) |
| Generative Agents | 2023 | Creates believable agents by combining LLMs with a memory stream architecture that records experiences, synthesizes reflections into higher-level abstractions, and retrieves relevant memories based on recency, importance, and relevance for planning behaviors. | [[arXiv]](https://arxiv.org/abs/2304.03442) [[GitHub]](https://github.com/joonspk-research/generative_agents) |
| HuaTuo | 2023 | Fine-tunes LLaMA on Chinese medical corpora with structured medical knowledge memory, enabling accurate medical consultation while maintaining factual consistency with established medical knowledge. | [[arXiv]](https://arxiv.org/abs/2304.06975) |
| SCM | 2023 | Gives LLMs autonomous control over memory operations (store, retrieve, forget) through learned policies, enabling adaptive memory management based on task requirements. | [[arXiv]](https://arxiv.org/abs/2304.13343) [[GitHub]](https://github.com/wbbeyourself/scm4LLMs) |
| Think-in-Memory | 2023 | Introduces a two-phase approach where LLMs first recall relevant memories and then perform reasoning over retrieved content, improving long-term memory utilization through explicit post-retrieval thinking. | [[arXiv]](https://arxiv.org/abs/2311.08719) |
| ChatDB | 2023 | Uses SQL databases as symbolic external memory for LLMs, enabling structured storage and precise retrieval of facts through database queries rather than vector similarity search. | [[Website]](https://chatdatabase.github.io/) |
| RoboVQA | 2023 | Benchmarks long-horizon visual question answering for robotics, requiring agents to maintain memory of past observations and actions to answer questions about extended task sequences. | [[arXiv]](https://arxiv.org/abs/2311.00899) [[Website]](https://robovqa.github.io/) |
| Self-RAG | 2023 | Trains LLMs to adaptively retrieve information, generate responses, and critique their own outputs through self-reflection tokens, improving factuality by learning when retrieval helps versus hurts. | [[arXiv]](https://arxiv.org/abs/2310.11511) [[GitHub]](https://github.com/AkariAsai/self-rag) |
| FLARE | 2023 | Implements active retrieval that predicts when the LLM needs additional information during generation, fetching relevant documents on-the-fly only when confidence is low to reduce unnecessary retrieval. | [[arXiv]](https://arxiv.org/abs/2305.06983) [[GitHub]](https://github.com/jzbjyb/FLARE) |
| Atlas | 2023 | Combines retrieval-augmented pre-training with few-shot learning, demonstrating that smaller models with retrieval can match or exceed larger models on knowledge-intensive tasks with minimal examples. | [[JMLR]](https://www.jmlr.org/papers/v24/23-0037.html) [[GitHub]](https://github.com/facebookresearch/atlas) |
| LLMLingua | 2023 | Compresses long prompts while preserving essential information for LLM inference, reducing computational costs and enabling processing of longer contexts within fixed context windows. | [[arXiv]](https://arxiv.org/abs/2310.05736) [[GitHub]](https://github.com/microsoft/LLMLingua) |
| CLIP-Fields | 2022 | Creates 3D semantic memory fields using CLIP embeddings, enabling robots to store and query spatial memories using natural language without dense manual annotations. | [[arXiv]](https://arxiv.org/abs/2210.05663) [[GitHub]](https://github.com/notmahi/clip-fields) |
| LM-Nav | 2022 | Combines language models with vision and action models for zero-shot robotic navigation, using language as an interface to query spatial memory and plan navigation routes. | [[arXiv]](https://arxiv.org/abs/2207.04429) |
| Contriever | 2022 | Develops dense retrieval through contrastive pre-training without labeled data, learning useful passage representations from self-supervised objectives for zero-shot retrieval performance. | [[arXiv]](https://arxiv.org/abs/2112.09118) [[GitHub]](https://github.com/facebookresearch/contriever) |
| DPR | 2020 | Proposes dual-encoder architecture for learning dense representations of queries and passages, enabling efficient nearest-neighbor search that outperforms traditional sparse retrieval methods. | [[arXiv]](https://arxiv.org/abs/2004.04906) [[GitHub]](https://github.com/facebookresearch/DPR) |
| REALM | 2020 | Pre-trains language models jointly with a neural retriever, enabling the model to learn to retrieve and attend to relevant documents as part of its core language understanding capabilities. | [[arXiv]](https://arxiv.org/abs/2002.08909) |
| kNN-LM | 2020 | Augments language models with a nearest neighbor mechanism over cached representations, improving generalization by explicitly memorizing and retrieving from training examples at inference time. | [[ICLR]](https://openreview.net/forum?id=HklBjCEKvH) |
| Scene Memory Transformer | 2019 | Applies transformer attention over stored scene observations, enabling embodied agents to selectively attend to relevant past observations for long-horizon task completion. | [[arXiv]](https://arxiv.org/abs/1903.03878) |

#### ⚙️ **Parametric Factual Memory**

> **Parametric Factual Memory** encodes factual knowledge directly into model weights through training or fine-tuning. This includes knowledge editing methods (ROME, MEMIT), adapter-based knowledge injection (K-Adapter, LoRA), and continual learning approaches that update model parameters to incorporate new facts.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| Doc-to-Atom | 2026 | Decomposes documents into typed knowledge atoms, each compiled into a micro-LoRA adapter with a retrieval key and selected by a query router; +8.58 F1 over Doc-to-LoRA across six QA benchmarks. | [[arXiv]](https://arxiv.org/abs/2606.12400) |
| Revisiting Parameter-Based Knowledge Editing | 2026 | Uses a dimensional-collapse hypothesis to explain how localized weight edits cause global interference; parameter-editing methods consistently degrade core abilities while a simple retrieval baseline outperforms them (ICML 2026). | [[arXiv]](https://arxiv.org/abs/2606.00570) |
| How LoRA Remembers | 2026 | Establishes a power-law relation between loss reduction and parameters in LoRA finetuning, with a phase transition to verbatim recall; proposes MemFT, which reallocates training toward under-memorized tokens. | [[arXiv]](https://arxiv.org/abs/2605.30260) [[GitHub]](https://github.com/zjunlp/ParametricMemoryLaw) |
| Labyrinth and the Thread | 2026 | Shows via optimization analysis that single and sequential knowledge edits are formally equivalent, so stability follows from accounting for accumulated editing constraints rather than null-space tricks (ICML 2026). | [[arXiv]](https://arxiv.org/abs/2605.26670) [[GitHub]](https://github.com/Wangzzzzzzzz/OTE-SE-Alignment) |
| Tensor-Structured Editing for MoE | 2026 | Exploits the tensor structure of mixture-of-experts layers and the Woodbury identity to reduce knowledge-editing updates to inversions of fixed low-rank matrices, accelerating editing by up to 6x. | [[arXiv]](https://arxiv.org/abs/2605.16686) |
| LightEdit | 2026 | Lifelong editing framework that selects relevant retrieved knowledge to rewrite the query and uses a decoding strategy suppressing the model's original knowledge probabilities, at lower training cost. | [[arXiv]](https://arxiv.org/abs/2604.19089) |
| Doc-to-LoRA | 2026 | Hypernetwork that meta-learns approximate context distillation in one forward pass, emitting LoRA adapters that internalize a document; near-perfect needle-in-haystack accuracy beyond 4x the base model's context window. | [[arXiv]](https://arxiv.org/abs/2602.15902) |
| CrispEdit | 2026 | Casts model editing as constrained optimization, projecting updates onto the low-curvature subspace of the capability-loss landscape using Bregman divergence and Kronecker-factored approximations. | [[arXiv]](https://arxiv.org/abs/2602.15823) |
| Norm-Anchor Scaling | 2026 | Identifies a positive feedback loop in sequential editing where value vectors and edited MLP weights amplify each other; rescaling value vectors to original norms extends the usable editing window over 4x. | [[arXiv]](https://arxiv.org/abs/2602.02543) |
| MemLoRA | 2025 | Equips small language models with distilled LoRA expert adapters for memory extraction, update and memory-augmented generation, enabling on-device memory systems that match much larger models. | [[arXiv]](https://arxiv.org/abs/2512.04763) |
| SEAL | 2025 | Self-Adapting Language Models: the LLM generates its own finetuning data and update directives ("self-edits") applied as persistent weight updates, with an RL outer loop rewarding downstream performance. | [[arXiv]](https://arxiv.org/abs/2506.10943) |
| MEMOIR | 2025 | Lifelong editing through a dedicated residual memory module with sparse, sample-dependent activation masks that isolate each edit, sustaining thousands of sequential edits on LLaMA-3 and Mistral (NeurIPS 2025). | [[arXiv]](https://arxiv.org/abs/2506.07899) |
| UltraEdit | 2025 | Training-, subject- and memory-free editor computing parameter shifts in one step from hidden states and gradients with lifelong normalization; over 7x faster than prior best, scaling to 2M edits. | [[arXiv]](https://arxiv.org/abs/2505.14679) [[GitHub]](https://github.com/XiaojieGu/UltraEdit) |
| Parametric RAG | 2025 | Replaces in-context document injection with document-specific parameters merged into the LLM's feed-forward networks at inference time, cutting context overhead while integrating retrieved knowledge more deeply. | [[arXiv]](https://arxiv.org/abs/2501.15915) [[GitHub]](https://github.com/oneal2000/PRAG) |
| Pretraining with Hierarchical Memories | 2025 | Pre-trains models with separate memory modules for common and rare knowledge, allowing efficient storage of long-tail facts in external memory while keeping frequent knowledge in model parameters. | [[arXiv]](https://arxiv.org/abs/2510.02375) |
| MLP Memory | 2025 | Augments language models with MLP-based external memory modules that are pretrained alongside retrievers, enabling efficient storage and retrieval of factual knowledge. | [[arXiv]](https://arxiv.org/abs/2508.01832) |
| Self-Updatable LLMs | 2025 | Enables LLMs to update their own parameters based on new context, integrating learned information directly into model weights for persistent knowledge without external storage. | [[OpenReview]](https://openreview.net/forum?id=aCPFCDL9QY) |
| ELDER | 2025 | Uses mixture-of-LoRA adapters for lifelong model editing, where different LoRA modules store different knowledge updates that can be dynamically combined during inference. | [[AAAI]](https://doi.org/10.1609/aaai.v39i23.34622) |
| WISE | 2024 | Introduces a wise memory architecture for continual model editing that prevents catastrophic forgetting while allowing unlimited sequential knowledge updates to model parameters. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2024/hash/60960ad78868fce5c165295fbd895060-Abstract-Conference.html) |
| CharacterGLM | 2024 | Fine-tunes LLMs to embody specific social characters by encoding personality traits, speaking styles, and behavioral patterns directly into model parameters for consistent role-playing. | [[EMNLP]](https://doi.org/10.18653/v1/2024.emnlp-industry.107) |
| Online Adaptation (MAC) | 2024 | Enables online model adaptation by maintaining a memory of amortized context representations that can be quickly integrated into model computations without full fine-tuning. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2024/hash/eaf956b52bae51fbf387b8be4cc3ce18-Abstract-Conference.html) [[GitHub]](https://github.com/jihoontack/MAC) |
| AlphaEdit | 2024 | Constrains knowledge edits to the null space of preserved knowledge, enabling targeted factual updates without disrupting other learned information in model parameters. | [[arXiv]](https://arxiv.org/abs/2410.02355) |
| Neighboring Perturbations | 2024 | Analyzes how knowledge edits affect neighboring facts in the model's knowledge space, proposing methods to minimize unintended side effects of parameter modifications. | [[OpenReview]](https://openreview.net/forum?id=K9NTPRvVRI) |
| Memory Layers at Scale | 2024 | Scales memory-augmented transformer layers to billions of parameters, demonstrating that explicit memory modules improve factual recall without proportional compute increases. | [[arXiv]](https://arxiv.org/abs/2412.09764) [[GitHub]](https://github.com/facebookresearch/memory) |
| MoExtend | 2024 | Adds new expert modules to mixture-of-experts models for handling new modalities and tasks, storing specialized knowledge in dedicated expert parameters. | [[arXiv]](https://arxiv.org/abs/2408.03511) [[GitHub]](https://github.com/zhongshsh/MoExtend) |
| Character-LLM | 2023 | Develops character agents by training on character-specific data including background stories, behavioral patterns, and dialogue samples, enabling consistent persona maintenance across conversations. | [[EMNLP]](https://doi.org/10.18653/v1/2023.emnlp-main.814) [[GitHub]](https://github.com/choosewhatulike/trainable-agents) |
| MEND | 2022 | Learns a hypernetwork that predicts parameter updates for rapid model editing, enabling fast factual corrections without expensive gradient-based fine-tuning. | [[ICLR]](https://openreview.net/forum?id=0DcZxeWfOPt) |
| MEMIT | 2022 | Enables simultaneous editing of thousands of facts in transformer models by identifying and modifying specific MLP layers that store factual associations. | [[ICLR]](https://openreview.net/forum?id=MkbcAHIYgyS) [[GitHub]](https://github.com/kmeng01/memit) |
| SERAC | 2022 | Maintains a separate memory of edits that overrides base model outputs when relevant, enabling scalable knowledge updates without modifying original model parameters. | [[ICML]](https://proceedings.mlr.press/v162/mitchell22a.html) [[GitHub]](https://github.com/eric-mitchell/serac) |
| K-Adapter | 2021 | Injects factual and linguistic knowledge into frozen pre-trained models through trainable adapter modules, enabling knowledge updates without full model retraining. | [[ACL]](https://doi.org/10.18653/v1/2021.findings-acl.121) |
| ROME | 2021 | Localizes factual knowledge to specific model components and enables precise single-fact edits by modifying targeted MLP weights in transformer layers. | [[arXiv]](https://arxiv.org/abs/2104.08164) |
| ELLA | 2013 | Proposes efficient lifelong learning through shared task knowledge bases, enabling rapid learning of new tasks by leveraging previously learned parameter configurations. | [[ICML]](https://proceedings.mlr.press/v28/ruvolo13.html) |

#### 🧬 **Latent Factual Memory**

> **Latent Factual Memory** stores factual information in continuous vector representations or hidden states. This includes memory-augmented architectures (Neural Turing Machines, Memorizing Transformers), state space models (Mamba, RWKV), and learned memory tokens that compress knowledge into dense representations.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| DART | 2026 | Decoded Attention over Recurrent States: extends Mamba-2 by decoding token-conditioned keys and values from chunk states and attending over those recurrent memories, saving 75% of inference cache versus attention baselines. | [[arXiv]](https://arxiv.org/abs/2608.02032) |
| ARMT | 2026 | Associative Recurrent Memory Transformer splits long inputs into segments with layer-wise associative memory read/write, giving linear scaling; extends pretrained LLMs to 65k tokens with 30% fewer FLOPs. | [[arXiv]](https://arxiv.org/abs/2607.11614) |
| HOLA | 2026 | "A Hippocampus for Linear Attention": pairs a compressive linear-attention recurrent state with a bounded exact key-value cache storing tokens with the largest committed prediction residual. | [[arXiv]](https://arxiv.org/abs/2607.02303) |
| VisMem | 2025 | Gives VLMs dynamic latent vision memories (a short-term perceptual module and a long-term semantic module) invoked during inference to counter visual degradation; average 11.0% gain across visual benchmarks. | [[arXiv]](https://arxiv.org/abs/2511.11007) [[GitHub]](https://github.com/YU-deep/VisMem) |
| Memory³ | 2025 | Augments language models with three types of explicit memory (working, episodic, semantic) stored in latent space, enabling efficient long-range information flow beyond attention mechanisms. | [[arXiv]](https://arxiv.org/abs/2407.01178) |
| HMT | 2025 | Processes long contexts through hierarchical memory compression, where lower levels store recent detailed information and higher levels maintain compressed summaries of distant context. | [[arXiv]](https://arxiv.org/abs/2405.06067) |
| General Continuous Memory | 2025 | Develops continuous latent memory representations for vision-language models that persist across inputs, enabling more coherent multimodal reasoning over extended interactions. | [[arXiv]](https://arxiv.org/abs/2505.17670) |
| M+ | 2025 | Extends MemoryLLM with hierarchical memory architecture combining working memory with scalable external memory banks for information retention across millions of tokens. | [[arXiv]](https://arxiv.org/abs/2502.00592) |
| R3Mem | 2025 | Uses reversible compression to store memories in compact latent representations that can be decompressed for retrieval, balancing storage efficiency with information preservation. | [[arXiv]](https://arxiv.org/abs/2502.15957) |
| NAMM | 2025 | Evolves memory mechanisms using neural architecture search, discovering novel memory configurations that improve transformer performance across diverse tasks. | [[arXiv]](https://arxiv.org/abs/2410.13166) [[GitHub]](https://github.com/SakanaAI/evo-memory) |
| Thinker | 2025 | Implements dual-process cognition with fast intuitive responses and slow deliberative reasoning, using different memory access patterns for each thinking mode. | [[arXiv]](https://arxiv.org/abs/2505.21097) |
| Hierarchical Reasoning Model | 2025 | Structures reasoning in hierarchical levels from concrete operations to abstract planning, maintaining memory at each level for coordinated multi-step problem solving. | [[arXiv]](https://arxiv.org/abs/2506.21734) [[GitHub]](https://github.com/sapientinc/HRM/) |
| Mamba | 2024 | Introduces selective state space models that achieve linear-time complexity while maintaining the ability to selectively remember or forget information based on input content. | [[arXiv]](https://arxiv.org/abs/2312.00752) [[GitHub]](https://github.com/state-spaces/mamba) |
| Mamba-2 | 2024 | Unifies transformers and state space models under a common framework, showing that attention can be viewed as a special case of structured state space layers with efficient hardware implementations. | [[arXiv]](https://arxiv.org/abs/2405.21060) |
| Jamba | 2024 | Combines transformer attention layers with Mamba state space layers in a hybrid architecture, leveraging the strengths of both for efficient long-context processing. | [[arXiv]](https://arxiv.org/abs/2403.19887) |
| Griffin | 2024 | Combines gated linear recurrent layers for global context with local attention windows, achieving efficient inference while preserving the modeling power of attention. | [[arXiv]](https://arxiv.org/abs/2402.19427) |
| Zamba | 2024 | Creates a compact 7B parameter model by combining state space layers with shared attention layers, achieving strong performance with significantly reduced memory footprint. | [[arXiv]](https://arxiv.org/abs/2405.16712) [[GitHub]](https://github.com/Zyphra/Zamba) |
| An Empirical Study of Mamba | 2024 | Provides systematic comparison between 8B-parameter Mamba and Transformer models across diverse tasks, analyzing strengths and weaknesses of state space architectures at scale. | [[arXiv]](https://arxiv.org/abs/2406.07887) |
| Efficient Episodic Memory | 2024 | Enables efficient sharing and utilization of episodic memories in multi-agent reinforcement learning, improving coordination through selective experience replay. | [[OpenReview]](https://openreview.net/forum?id=LjivA1SLZ6) |
| RWKV | 2023 | Combines the parallelizable training of transformers with the efficient inference of RNNs through a novel attention-free architecture with linear complexity and unlimited context length. | [[EMNLP]](https://aclanthology.org/2023.findings-emnlp.936/) [[GitHub]](https://github.com/BlinkDL/RWKV-LM) |
| RetNet | 2023 | Proposes retention mechanism as an alternative to attention, achieving training parallelism, low-cost inference, and linear complexity while matching transformer performance. | [[arXiv]](https://arxiv.org/abs/2307.08621) [[GitHub]](https://github.com/microsoft/torchscale) |
| H3 | 2023 | Develops state space model layers that can match transformer performance on language modeling through selective gating and efficient convolution-based implementations. | [[ICLR]](https://openreview.net/forum?id=COZDy0WYGg) [[GitHub]](https://github.com/HazyResearch/H3) |
| Hyena | 2023 | Replaces attention with long convolutions and gating, achieving subquadratic complexity while maintaining competitive performance through hierarchical filter learning. | [[ICML]](https://proceedings.mlr.press/v202/poli23a.html) [[GitHub]](https://github.com/HazyResearch/safari) |

### 🎓 Experiential Memory

> **Experiential Memory** (also called Episodic or Procedural Memory) stores records of past experiences, interactions, and learned skills. It answers "what have I done?" and enables agents to learn from past successes and failures, accumulate skills, and improve over time.

#### 🔤 **Token-level Experiential Memory**

> **Token-level Experiential Memory** stores past experiences, interactions, and learned skills as explicit records (e.g., conversation logs, action trajectories, skill libraries). Agents retrieve relevant past experiences to inform current decisions, enabling learning from trial-and-error and skill accumulation.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| Recuris | 2026 | Couples persistent experiential memory with dynamically maintained working memory so skill selection is grounded in current task progress, and uses structured traces for component-level failure attribution. | [[arXiv]](https://arxiv.org/abs/2608.24876) |
| HyperSkill | 2026 | Hypergraph-structured skill memory with subtask and skill nodes linked by trajectory hyperedges, plus dual-path retrieval ranked by co-occurrence; reports +11.51 on GAIA and +11.18 on WebWalkerQA over ten memory baselines. | [[arXiv]](https://arxiv.org/abs/2608.16114) [[GitHub]](https://github.com/rux001/HyperSkill) |
| SESA | 2026 | Self-evolving search agents combining self-play (a challenger poses questions, a solver answers) with a persistent skill memory distilled from failed rollouts; improves accuracy over plain self-play on seven benchmarks. | [[arXiv]](https://arxiv.org/abs/2607.29468) [[GitHub]](https://github.com/Zenghuang-Fu/SESA-Self-Evolving-Search-Agents) |
| Subtask-Level Memory for SWE Agents | 2026 | Organizes software-engineering agent memory at the subtask level, structurally aligned with the agent's workflow, instead of per issue instance; improves Pass@1 by 4.7 points on average (ICML 2026). | [[ICML]](https://icml.cc/virtual/2026/poster/66605) |
| Executable Agentic Memory | 2026 | Stores GUI states and actions as an executable knowledge graph, turning GUI automation from step-wise LLM generation into retrieval-based planning; reports 19.6% improvement over UI-TARS-7B on AndroidWorld (ICML 2026). | [[ICML]](https://icml.cc/virtual/2026/poster/65931) |
| Darwinian Memory | 2026 | Training-free, self-regulating memory for GUI agents that decomposes trajectories into reusable units and applies evolutionary selection to keep or prune them; reports 18% success-rate gains (ICML 2026). | [[ICML]](https://icml.cc/virtual/2026/poster/61134) |
| SkillComposer | 2026 | Decomposes skill construction into learnable create, improve and merge operations trained via rejection sampling, so a model evolves skills at inference time; a 4B composer improves a 27B executor on agent tasks. | [[arXiv]](https://arxiv.org/abs/2606.06079) |
| MUSE-Autoskill | 2026 | Integrates skill creation, per-skill memory, management and unit-test evaluation inside the agent execution loop; reaches 68.4% on SkillsBench, and its self-generated skills transfer to other agents. | [[arXiv]](https://arxiv.org/abs/2605.27366) |
| CodeSkill | 2026 | Uses reinforcement learning to extract and maintain reusable procedural skills from coding-agent trajectories; improves average pass rate by 9.69% over baselines while keeping the skill bank compact and stable. | [[arXiv]](https://arxiv.org/abs/2605.25430) |
| SkillOpt | 2026 | Optimizes agent skills by bounded text-space edits proposed by a separate optimizer model and accepted only when validation improves, with zero inference-time overhead. | [[arXiv]](https://arxiv.org/abs/2605.23904) |
| When Continual Learning Moves to Memory | 2026 | Analyses memory-augmented agents as continual learners through a key-value framework; finds abstract procedural memories transfer better than detailed trajectories, and that memory design trades forward transfer against forgetting. | [[arXiv]](https://arxiv.org/abs/2604.27003) |
| SkillFoundry | 2026 | Mines heterogeneous scientific resources (repos, APIs, notebooks, papers) into validated agent skill packages via a domain knowledge tree and closed-loop expand/repair/merge/prune operations. | [[arXiv]](https://arxiv.org/abs/2604.03964) |
| EvoSkills | 2026 | Co-evolves a Skill Generator that refines multi-file skill packages with a Surrogate Verifier that independently synthesizes tests, needing no ground truth; reaches a 71.1% pass rate on SkillsBench and transfers across LLMs. | [[arXiv]](https://arxiv.org/abs/2604.01687) |
| SkillRL | 2026 | Distills experience into a hierarchical skill library that is recursively evolved and co-trained with the agent policy during reinforcement learning; outperforms baselines by 15.3% across ALFWorld, WebShop and search-augmented tasks. | [[arXiv]](https://arxiv.org/abs/2602.08234) [[GitHub]](https://github.com/aiming-lab/SkillRL) |
| MemRL | 2026 | Non-parametric agent evolution via RL on episodic memory with a two-phase retrieval mechanism that reconciles the stability-plasticity dilemma without weight updates. | [[arXiv]](https://arxiv.org/abs/2601.03192) [[GitHub]](https://github.com/MemTensor/MemRL) |
| PhysMem | 2026 | Three-tier memory (episodic raw experiences, working memory hypotheses, long-term verified principles) enabling VLM robot planners to learn physics from interaction without parameter updates. | [[arXiv]](https://arxiv.org/abs/2602.20323) |
| CoMAM | 2026 | Multi-agent system with local and global rewards enabling end-to-end RL optimization with simultaneous updates of heterogeneous policies for personalized memory. | [[arXiv]](https://arxiv.org/abs/2603.12631) |
| ReMe | 2025 | "Remember Me, Refine Me": dynamic procedural memory with multi-faceted experience distillation, context-aware reuse and utility-based pruning; an 8B model with ReMe outperforms larger models without dynamic memory (ACL 2026 Findings). | [[arXiv]](https://arxiv.org/abs/2512.10696) |
| MemOrb | 2025 | Implements verbal reinforcement learning for customer service agents, where positive/negative feedback strengthens/weakens associated memory entries for improved response quality. | [[arXiv]](https://arxiv.org/abs/2509.18713) |
| Dynamic Affective Memory | 2025 | Manages emotional context in agent memory, tracking user affect states over time to enable emotionally appropriate and personalized responses across conversations. | [[arXiv]](https://arxiv.org/abs/2510.27418) |
| Preference-Aware Memory | 2025 | Dynamically updates user preference models in memory as new interactions reveal changing tastes, ensuring recommendations and responses reflect current rather than outdated preferences. | [[arXiv]](https://arxiv.org/abs/2510.09720) |
| Mem-PAL | 2025 | Creates personalized dialogue assistants that maintain comprehensive user memories including preferences, history, and relationship context for natural long-term interactions. | [[arXiv]](https://arxiv.org/abs/2511.13410) |
| PersonalAgent | 2025 | Enables agents to proactively customize user profiles based on interaction patterns, anticipating needs before explicit requests through learned behavioral models. | [[arXiv]](https://arxiv.org/abs/2512.15302) |
| Enabling Personalized Long-term | 2025 | Implements persistent user profiles and conversation memories that survive across sessions, enabling truly long-term personalized agent interactions. | [[arXiv]](https://arxiv.org/abs/2510.07925) |
| Agentic Context Engineering | 2025 | Enables agents to modify their own context and prompts based on experience, creating self-improving systems that optimize their operating conditions over time. | [[arXiv]](https://arxiv.org/abs/2510.04618) |
| FLEX | 2025 | Implements forward-only learning where agents continuously evolve from accumulated experiences without backward passes, enabling efficient online adaptation. | [[arXiv]](https://arxiv.org/abs/2511.06449) |
| Scaling Agent Learning | 2025 | Generates synthetic experiences to augment real interactions, enabling agents to learn from larger and more diverse experience pools for improved generalization. | [[arXiv]](https://arxiv.org/abs/2511.03773) |
| UFO2 | 2025 | Provides operating system-level infrastructure for desktop automation agents, with unified memory and tool interfaces for controlling applications across the desktop environment. | [[arXiv]](https://arxiv.org/abs/2504.14603) |
| PRINCIPLES | 2025 | Stores abstract communication strategies in memory that agents can retrieve and apply proactively, improving dialogue effectiveness through learned conversational principles. | [[arXiv]](https://arxiv.org/abs/2509.17459) |
| Training-Free GRPO | 2025 | Optimizes agent policies through relative comparisons within experience groups without gradient-based training, enabling rapid adaptation from interaction feedback. | [[arXiv]](https://arxiv.org/abs/2510.08191) |
| ToolMem | 2025 | Maintains memory of tool capabilities and usage patterns, enabling multimodal agents to select and apply appropriate tools based on learned effectiveness. | [[arXiv]](https://arxiv.org/abs/2510.06664) |
| H²R | 2025 | Applies hierarchical reflection on past experiences at multiple abstraction levels, extracting both task-specific and transferable insights from agent trajectories. | [[arXiv]](https://arxiv.org/abs/2509.12810) |
| BrowserAgent | 2025 | Creates web automation agents that learn from human browsing patterns, maintaining memory of successful navigation strategies and page interaction methods. | [[arXiv]](https://arxiv.org/abs/2510.10666) |
| LEGOMem | 2025 | Implements composable procedural memory modules that can be shared and combined across agents, enabling modular skill transfer and reuse in multi-agent systems. | [[arXiv]](https://arxiv.org/abs/2510.04851) |
| Alita-G | 2025 | Creates meta-agents that generate and improve other agents, maintaining memory of successful agent designs and optimization strategies. | [[arXiv]](https://arxiv.org/abs/2510.23601) |
| SAGE | 2025 | Combines reflection mechanisms with memory augmentation for continuous self-improvement, enabling agents to learn from mistakes and successes over time. | [[Neurocomputing]](https://doi.org/10.1016/j.neucom.2025.130470) |
| ReasoningBank | 2025 | Stores successful reasoning chains in a searchable memory bank, enabling agents to retrieve and adapt prior reasoning patterns for improved problem-solving on new tasks. | [[arXiv]](https://arxiv.org/abs/2509.25140) |
| Memento | 2025 | Achieves agent improvement without model updates by maintaining an evolving memory of successful strategies and examples that guide inference-time behavior. | [[arXiv]](https://arxiv.org/abs/2508.16153) |
| Memp | 2025 | Investigates procedural memory in agents, storing how-to knowledge as executable procedures that can be retrieved and executed for task completion. | [[arXiv]](https://arxiv.org/abs/2508.06433) |
| SEAgent | 2025 | Develops self-evolving computer use agent with autonomous learning from experience. | [[arXiv]](https://arxiv.org/abs/2508.04700) |
| Agent KB | 2025 | Builds cross-domain knowledge bases from agent experiences, enabling transfer of problem-solving strategies between different task domains. | [[arXiv]](https://arxiv.org/abs/2507.06229) |
| MemTool | 2025 | Optimizes which tool usage examples and outcomes to keep in limited context windows, improving tool selection accuracy through intelligent memory management. | [[arXiv]](https://arxiv.org/abs/2507.21428) |
| JARVIS-1 | 2025 | Builds open-world Minecraft agents with multimodal memory of visual observations and action sequences for flexible multi-task completion. | [[TPAMI]](https://doi.org/10.1109/TPAMI.2024.3511593) |
| Agent Workflow Memory | 2025 | Stores and retrieves complete workflow patterns from past task completions, enabling efficient automation of recurring procedural tasks. | [[OpenReview]](https://openreview.net/forum?id=NTAhi2JEEE) |
| Darwin Godel Machine | 2025 | Implements self-modifying agents that evolve their own code and strategies through accumulated experience, pursuing open-ended capability improvement. | [[arXiv]](https://arxiv.org/abs/2505.22954) |
| Alita | 2025 | Creates generalist agents that learn task-specific behaviors from minimal examples, scaling to new domains through experience accumulation. | [[arXiv]](https://arxiv.org/abs/2505.20286) |
| SkillWeaver | 2025 | Enables web agents to discover reusable skills through exploration and refine them through practice, building expanding skill libraries over time. | [[arXiv]](https://arxiv.org/abs/2504.07079) |
| LearnAct | 2025 | Introduces a benchmark for few-shot mobile gui agent with a unified demonstration benchmark. | [[arXiv]](https://arxiv.org/abs/2504.13805) |
| Tool Retrieval Benchmark | 2025 | Introduces a benchmark for retrieval models aren't tool-savvy: benchmarking tool retrieval for LLMs. | [[arXiv]](https://arxiv.org/abs/2503.01763) |
| Dynamic Cheatsheet | 2025 | Develops test-time learning with adaptive memory. | [[arXiv]](https://arxiv.org/abs/2504.07952) |
| Inducing Programmatic Skills | 2025 | Extracts programmatic skill representations from agent trajectories that can be composed and reused for efficient task completion. | [[arXiv]](https://arxiv.org/abs/2504.06821) |
| COLA | 2025 | Coordinates multiple specialized agents for Windows UI automation, sharing memory of successful interaction patterns across the agent team. | [[arXiv]](https://arxiv.org/abs/2503.09263) |
| Memory-augmented Query | 2025 | Reconstructs and refines knowledge graph queries using memory of past successful query patterns, improving reasoning accuracy. | [[arXiv]](https://arxiv.org/abs/2503.05193) |
| From Exploration to Mastery | 2025 | Guides LLMs from initial tool exploration to mastery through self-driven practice, accumulating tool usage expertise in memory. | [[arXiv]](https://arxiv.org/abs/2410.08197) |
| REFLECT | 2025 | Generates natural language summaries of robot failures from experience, enabling diagnosis and correction of recurring error patterns. | [[arXiv]](https://arxiv.org/abs/2306.15724) [[Website]](https://robot-reflect.github.io/) |
| MemEvolve | 2025 | Meta-evolutionary framework that jointly evolves agents' experiential knowledge and their memory architecture itself, improving frameworks like SmolAgent by up to 17%. | [[arXiv]](https://arxiv.org/abs/2512.18746) [[GitHub]](https://github.com/bingreeky/MemEvolve) |
| EchoVLA | 2025 | VLA model with scene memory (spatial-semantic maps) and episodic memory (task-level experiences with multimodal features) for long-horizon mobile manipulation. | [[arXiv]](https://arxiv.org/abs/2511.18112) |
| MACLA | 2025 | Hierarchical procedural memory via Bayesian selection and contrastive refinement that compresses 2851 trajectories into 187 reusable procedures in 56 seconds (AAMAS 2026 Oral). | [[arXiv]](https://arxiv.org/abs/2512.18950) [[GitHub]](https://github.com/S-Forouzandeh/MACLA-LLM-Agents-AAMAS-Conference) |
| CodeMem | 2025 | Implements procedural memory as validated code, where agents write, validate, and save successful logic into a persistent procedural memory bank for deterministic reuse. | [[arXiv]](https://arxiv.org/abs/2512.15813) [[GitHub]](https://github.com/zhu-zhu-ding/CodeMem) |
| LD-Agent | 2024 | Develops personalized dialogue agents that learn and adapt to individual users over extended interactions, maintaining coherent user models across conversations. | [[arXiv]](https://arxiv.org/abs/2406.05925) |
| Buffer of Thoughts | 2024 | Maintains a buffer of high-level thought templates that can be instantiated for new problems, enabling more structured and reusable reasoning. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2024/hash/cde328b7bf6358f5ebb91fe9c539745e-Abstract-Conference.html) |
| Planning from Imagination | 2024 | Combines episodic memory with mental simulation for navigation planning, imagining future states based on past experience for better route selection. | [[arXiv]](https://arxiv.org/abs/2412.01857) |
| ExpeL | 2024 | Demonstrates that LLM agents can learn from accumulated experiences stored in memory, extracting generalizable insights that transfer to new tasks. | [[AAAI]](https://doi.org/10.1609/aaai.v38i17.29936) [[GitHub]](https://github.com/LeapLabTHU/ExpeL) |
| RepairAgent | 2024 | Introduces autonomous, LLM-based agent for program repair. | [[arXiv]](https://arxiv.org/abs/2403.17134) |
| Fincon | 2024 | Coordinates multiple financial analysis agents with shared memory of market conditions and investment strategies for improved decision making. | [[arXiv]](https://arxiv.org/abs/2407.06567) |
| COLT | 2024 | Retrieves comprehensive sets of tools needed for tasks by learning from complete successful tool usage patterns in memory. | [[arXiv]](https://arxiv.org/abs/2405.16089) |
| ChatDev | 2024 | Simulates software company with communicating agents (CEO, CTO, programmer, tester) sharing project memory for collaborative code development. | [[arXiv]](https://arxiv.org/abs/2307.07924) [[GitHub]](https://github.com/OpenBMB/ChatDev) |
| LOTUS | 2024 | Discovers and accumulates manipulation skills from demonstrations without supervision, building expanding repertoires of reusable robot behaviors. | [[arXiv]](https://arxiv.org/abs/2311.02058) |
| RecMind | 2024 | Creates recommendation agents that learn user preferences through interaction, maintaining memory of user feedback for improved suggestions. | [[NAACL]](https://doi.org/10.18653/v1/2024.findings-naacl.271) |
| ToolLLM | 2023 | Enables LLMs to learn usage patterns for thousands of APIs, storing tool documentation and usage examples for accurate API calling. | [[arXiv]](https://arxiv.org/abs/2307.16789) |
| CREATOR | 2023 | Enables agents to create new tools by abstracting patterns from experience, separating high-level reasoning from implementation details. | [[EMNLP]](https://doi.org/10.18653/v1/2023.findings-emnlp.462) |
| Reflexion | 2023 | Enables agents to learn from verbal feedback by storing self-reflections on failures in memory, improving performance through linguistic experience replay. | [[arXiv]](https://arxiv.org/abs/2303.11366) [[GitHub]](https://github.com/noahshinn/reflexion) |
| Toolformer | 2023 | Trains language models to autonomously decide when and how to use tools by learning from self-generated tool usage examples. | [[arXiv]](https://arxiv.org/abs/2302.04761) |
| Voyager | 2023 | Creates an open-ended Minecraft agent that continuously expands its skill library through exploration, storing discovered programs in memory for reuse. | [[arXiv]](https://arxiv.org/abs/2305.16291) [[Website]](https://voyager.minedojo.org/) |
| GITM | 2023 | Develops generally capable Minecraft agents with hierarchical memory of goals, plans, and learned skills for flexible behavior in open-ended environments. | [[arXiv]](https://arxiv.org/abs/2305.17144) [[GitHub]](https://github.com/OpenGVLab/GITM) |
| Synapse | 2023 | Uses past successful computer control trajectories as in-context examples, enabling task completion through trajectory memory retrieval. | [[Website]](https://ltzheng.github.io/Synapse/) |
| ReAct | 2023 | Interleaves reasoning traces with actions, storing thought-action-observation sequences that demonstrate effective problem-solving strategies. | [[arXiv]](https://arxiv.org/abs/2210.03629) [[GitHub]](https://github.com/ysymyth/ReAct) |
| TPTU | 2023 | Integrates task planning with tool usage through memory of successful plan-tool combinations for complex task completion. | [[arXiv]](https://arxiv.org/abs/2308.03427) |
| TPTU-v2 | 2023 | Extends task planning with improved memory mechanisms for real-world deployment, handling uncertainty through experience-based fallbacks. | [[arXiv]](https://arxiv.org/abs/2311.11315) [[GitHub]](https://github.com/OPS-KK2024/TPTU-v2) |
| CLIN | 2023 | Introduces continually learning language agent for rapid task adaptation. | [[arXiv]](https://arxiv.org/abs/2310.10134) [[GitHub]](https://github.com/allenai/clin) |
| MetaAgents | 2023 | Simulates human behavioral patterns for multi-agent coordination, using memory of interaction dynamics for realistic collaboration. | [[arXiv]](https://arxiv.org/abs/2310.06500) |
| AgentVerse | 2023 | Creates environments for multi-agent collaboration where agents with diverse roles share experiences and develop emergent cooperative behaviors through interaction. | [[arXiv]](https://arxiv.org/abs/2308.10848) [[GitHub]](https://github.com/OpenBMB/AgentVerse) |
| AutoGPT | 2023 | Introduces autonomous gpt-4 experiment. | [[GitHub]](https://github.com/Significant-Gravitas/AutoGPT) |
| BabyAGI | 2023 | Implements autonomous task management where an AI agent creates, prioritizes, and executes tasks based on objectives, learning from task completion outcomes. | [[GitHub]](https://github.com/yoheinakajima/babyagi) |
| HuggingGPT | 2023 | Coordinates ChatGPT with specialized Hugging Face models, maintaining memory of model capabilities for automatic model selection and task routing. | [[arXiv]](https://arxiv.org/abs/2303.17580) [[GitHub]](https://github.com/microsoft/JARVIS) |
| RT-2 | 2023 | Transfers knowledge from web-scale vision-language pretraining to robotic control, encoding action knowledge in the same representation space. | [[arXiv]](https://arxiv.org/abs/2307.15818) |
| PaLM-E | 2023 | Introduces embodied multimodal language model. | [[arXiv]](https://arxiv.org/abs/2303.03378) |
| RT-1 | 2022 | Trains transformers on large-scale robot demonstration data, learning generalizable manipulation skills stored as model weights for real-world deployment. | [[arXiv]](https://arxiv.org/abs/2212.06817) [[Website]](https://robotics-transformer1.github.io/) |
| SayCan | 2022 | Grounds language instructions in robot capabilities by scoring actions based on both language relevance and affordance feasibility from experience. | [[arXiv]](https://arxiv.org/abs/2204.01691) [[Website]](https://say-can.github.io/) |
| Code as Policies | 2022 | Generates executable robot control code from language instructions, storing successful code patterns as reusable policy primitives. | [[arXiv]](https://arxiv.org/abs/2209.07753) [[Website]](https://code-as-policies.github.io/) |
| Inner Monologue | 2022 | Enables robots to reason about plans through internal language dialogue, incorporating feedback from perception and action into planning memory. | [[arXiv]](https://arxiv.org/abs/2207.05608) [[Website]](https://innermonologue.github.io/) |
| Episodic Memory for Robotics | 2021 | Stores robot manipulation experiences as retrievable episodes, enabling learning from specific past attempts for improved task execution. | [[arXiv]](https://arxiv.org/abs/2104.10218) |
| Generalizable Episodic Memory | 2021 | Creates episodic memory systems for RL agents that generalize across similar situations, improving sample efficiency through experience reuse. | [[arXiv]](https://arxiv.org/abs/2103.06469) |

#### ⚙️ **Parametric Experiential Memory**

> **Parametric Experiential Memory** encodes learned experiences and skills into model parameters through reinforcement learning, imitation learning, or continual fine-tuning. This includes RLHF, policy gradient methods, and approaches that update model weights based on interaction feedback.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| RPMem | 2026 | Two-stage design compiling each session into a model-independent latent memory, then integrating sessions via a recurrent gate mapped to backbone-specific LoRA weights; reports 85.52% on PERMA with Qwen3-8B. | [[arXiv]](https://arxiv.org/abs/2609.23466) |
| aTTT | 2026 | Agentic test-time training: test-time LoRA updates for LLM agents that downweight loss on tokens in n-grams repeated from prior updates, preventing drift in looping episodes on ALFWorld and SWE-bench Lite. | [[arXiv]](https://arxiv.org/abs/2607.03441) |
| TMEM | 2026 | Scales self-evolving agents via parametric memory: agents learn within an episode through lightweight online updates to fast LoRA weights, combined with explicit memory compression; outperforms summary- and retrieval-based baselines. | [[arXiv]](https://arxiv.org/abs/2606.04536) |
| Language Models Need Sleep | 2026 | A "Sleep" stage for continual learning: Knowledge Seeding distills a smaller model's memories into a larger network, and Dreaming self-improves on RL-generated synthetic data. | [[arXiv]](https://arxiv.org/abs/2606.03979) |
| Do Language Models Need Sleep? | 2026 | Periodically converts recent context into persistent fast weights via offline recurrent passes through state-space blocks, moving computation to "sleep" while keeping wake-time latency. | [[arXiv]](https://arxiv.org/abs/2605.26099) |
| SleepGate | 2026 | Augments transformers with a learned sleep cycle over the KV cache for synaptic downscaling, selective replay, and targeted forgetting, reducing interference horizon from O(n) to O(log n). | [[arXiv]](https://arxiv.org/abs/2603.14517) |
| Nested Learning (HOPE) | 2025 | Views models and optimizers as nested multi-level optimization problems acting as associative memories; introduces the Hope continual-learning module with a continuum memory system (NeurIPS 2025). | [[arXiv]](https://arxiv.org/abs/2512.24695) |
| AgentEvolver | 2025 | Enables agents to evolve their own capabilities through parameter updates based on task performance, achieving self-improvement without human intervention. | [[arXiv]](https://arxiv.org/abs/2511.10395) |
| Agent Learning via Early Experience | 2025 | Prioritizes learning from early interaction experiences that shape foundational agent behaviors, similar to critical periods in biological development. | [[arXiv]](https://arxiv.org/abs/2510.08558) |
| Scaling Agents via Continual Pre-training | 2025 | Scales agent capabilities through continual pre-training on agent trajectories, encoding procedural knowledge directly into model parameters. | [[arXiv]](https://arxiv.org/abs/2509.13310) |
| ToolGen | 2024 | Unifies tool retrieval and execution in a single generative framework, encoding tool knowledge in model parameters for seamless tool use. | [[arXiv]](https://arxiv.org/abs/2410.03439) |
| Interactive Continual Learning | 2024 | Develops interactive continual learning: fast and slow thinking. | [[arXiv]](https://arxiv.org/abs/2403.02628) [[GitHub]](https://github.com/BiqingQi/Interactive-continual-Learning-Fast-and-Slow-Thinking) |
| Dynamic Gradient Calibration | 2024 | Introduces effective dynamic gradient calibration method for continual learning. | [[arXiv]](https://arxiv.org/abs/2407.20956) |
| A Machine with Memory | 2023 | Implements cognitive memory architecture with distinct short-term, episodic, and semantic stores that interact through consolidation processes. | [[AAAI]](https://doi.org/10.1609/aaai.v37i1.25075) |
| Retroformer | 2023 | Optimizes agent policies through retrospective analysis of past trajectories, updating model parameters based on outcome-weighted experiences. | [[arXiv]](https://arxiv.org/abs/2308.02151) [[GitHub]](https://github.com/weirayao/Retroformer) |
| DualPrompt | 2022 | Uses complementary prompt pairs for task-specific and task-invariant knowledge, enabling continual learning without storing past examples. | [[arXiv]](https://arxiv.org/abs/2204.04799) [[GitHub]](https://github.com/JH-LEE-KR/dualprompt-pytorch) |
| L2P | 2022 | Learns a pool of prompts that can be dynamically selected for different tasks, encoding task knowledge in prompt parameters. | [[arXiv]](https://arxiv.org/abs/2112.08654) [[GitHub]](https://github.com/google-research/l2p) |
| DualNet | 2021 | Implements dual-network architecture with fast adaptation and slow consolidation systems for balanced continual learning. | [[arXiv]](https://arxiv.org/abs/2110.00175) [[GitHub]](https://github.com/phquang/DualNet) |
| EWC | 2017 | Protects important parameters from modification during new learning by penalizing changes to weights critical for previous tasks. | [[PNAS]](https://www.pnas.org/doi/10.1073/pnas.1611835114) |
| iCaRL | 2017 | Maintains exemplar sets and uses nearest-mean classification for incremental class learning without forgetting previous classes. | [[CVPR]](https://arxiv.org/abs/1611.07725) [[GitHub]](https://github.com/srebuffi/iCaRL) |
| Progressive Neural Networks | 2016 | Adds new network columns for new tasks while freezing previous columns, enabling knowledge transfer without forgetting. | [[arXiv]](https://arxiv.org/abs/1606.04671) |

#### 🧬 **Latent Experiential Memory**

> **Latent Experiential Memory** stores experiences as latent representations, such as experience replay buffers in RL or learned skill embeddings. These compressed representations enable efficient storage and generalization across similar experiences.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| ActiveMem | 2026 | Organizes agent experience into dependency-aware latent execution trees that preserve procedural relations between steps instead of flat retrieval, improving task completion and memory efficiency. | [[arXiv]](https://arxiv.org/abs/2609.33244) |
| LaMem-VLA | 2026 | Reconstructs historical task experience into latent memory tokens that enter vision-language-action reasoning directly, via curator, seeker, condenser and weaver components, for long-horizon manipulation. | [[arXiv]](https://arxiv.org/abs/2607.07608) [[GitHub]](https://github.com/quhongyu/LaMem-VLA) |
| ElasticMem | 2026 | Builds offline latent memory banks, retrieves from the reasoner's hidden state and gives each memory a variable latent-token budget via a reward-trained policy. | [[arXiv]](https://arxiv.org/abs/2605.30690) [[GitHub]](https://github.com/ulab-uiuc/ElasticMem) |
| Mem-W | 2026 | Latent memory-native GUI agent weaving past trajectories and in-session segments into compact tokens through a shared compressor, trained with self-distillation and outcome-aware supervision. | [[arXiv]](https://arxiv.org/abs/2605.09317) |
| Auto-scaling Continuous Memory | 2025 | Dynamically scales continuous memory representations based on GUI complexity, automatically adjusting memory capacity for efficient desktop automation across varying interface states. | [[arXiv]](https://arxiv.org/abs/2510.09038) |

### ⚡ Working Memory

> **Working Memory** (also called Short-term Memory) manages the currently active context and information being processed. It answers "what am I focusing on now?" and handles the limited attention window, deciding what to keep, compress, or discard during extended interactions.

#### 🔤 **Token-level Working Memory**

> **Token-level Working Memory** manages the active context window through explicit text manipulation—deciding what information to keep, summarize, or discard as conversations extend beyond context limits. This includes context compression, summarization, and selective attention mechanisms.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| CCM | 2026 | Continuous Context Management: compacts context at every agent turn instead of at thresholds, trained with GRPO plus privileged full-history distillation on open-weight models, keeping a much smaller retained context. | [[arXiv]](https://arxiv.org/abs/2609.35540) |
| ARC | 2026 | Addressable Recall Compaction: lossless compaction that keeps an append-only, ID-addressable archive of tool observations and replaces old content in the active context with compact citations. | [[arXiv]](https://arxiv.org/abs/2607.25066) |
| ACM | 2026 | Agentic Context Management: gives agents manage_context and query_memory tools to decide when to compress, offload to external memory and recall on demand; post-training improves BrowseComp-Plus, DeepSearchQA and SWE-Bench Verified. | [[arXiv]](https://arxiv.org/abs/2607.23809) [[GitHub]](https://github.com/lixiaochuan2020/agentic-context-management) |
| CompactionRL | 2026 | RL training with context compaction in the loop, jointly optimizing task execution and summary generation via token-level loss normalization and cross-trajectory GAE; improves SWE-bench Verified and Terminal-Bench 2.0 results. | [[arXiv]](https://arxiv.org/abs/2607.05378) |
| Governance Decay | 2026 | Shows context compaction can silently drop safety constraints: across 1,323 episodes, policy violations rise from 0% with full context to 30% after compaction; a Constraint Pinning mitigation restores 0%. | [[arXiv]](https://arxiv.org/abs/2606.22528) |
| AdaCoM | 2026 | Trains an external LLM with RL to manage the context of a frozen agent, preserving task constraints while pruning stale content; stronger agents benefit from fidelity preservation and weaker ones from aggressive compression. | [[arXiv]](https://arxiv.org/abs/2605.30785) |
| LongSeeker | 2026 | Context-ReAct gives search agents five context operations (Skip, Compress, Rollback, Snippet, Delete) to reshape working context; LongSeeker, fine-tuned on 10k trajectories, reaches 61.5% on BrowseComp. | [[arXiv]](https://arxiv.org/abs/2605.05191) |
| MemoBrain | 2026 | Executive memory for tool-augmented agents that maintains a dependency-aware memory over reasoning steps, pruning invalid steps and folding completed sub-trajectories into a compact backbone. | [[arXiv]](https://arxiv.org/abs/2601.08079) |
| Context-Folding | 2025 | Lets an agent branch into a sub-trajectory for a subtask and then fold it, keeping only an outcome summary; trained with FoldGRPO process rewards, it matches ReAct baselines using a 10x smaller active context. | [[arXiv]](https://arxiv.org/abs/2510.11967) |
| Memory as Action | 2025 | Treats memory management as an action in the agent's policy, learning when to store, retrieve, or forget information for long-horizon tasks. | [[arXiv]](https://arxiv.org/abs/2510.12635) |
| IterResearch | 2025 | Reconstructs sufficient state representations at each step for Markovian decision making in long-horizon research tasks. | [[arXiv]](https://arxiv.org/abs/2511.07327) |
| MemSearcher | 2025 | Trains unified reasoning, search, and memory management capabilities through end-to-end reinforcement learning. | [[arXiv]](https://arxiv.org/abs/2511.02805) |
| AgentFold | 2025 | Proactively manages context in web automation by anticipating future information needs and preemptively caching relevant content. | [[arXiv]](https://arxiv.org/abs/2510.24699) |
| PRIME | 2025 | Integrates planning with memory retrieval, using anticipated reasoning steps to guide what information to retrieve. | [[arXiv]](https://arxiv.org/abs/2509.22315) |
| Context as Memory | 2025 | Maintains scene consistency in video generation through memory retrieval of previously generated visual elements. | [[arXiv]](https://arxiv.org/abs/2506.03141) |
| DeepAgent | 2025 | Creates general-purpose agents with dynamically scalable tool access and working memory for complex reasoning tasks. | [[arXiv]](https://arxiv.org/abs/2510.21618) |
| ACON | 2025 | Optimizes which context to compress vs retain for long-horizon agents, balancing information preservation with memory efficiency. | [[arXiv]](https://arxiv.org/abs/2510.00615) |
| ReSum | 2025 | Applies strategic summarization to search results for long-horizon research tasks, maintaining relevant findings across extended investigations. | [[arXiv]](https://arxiv.org/abs/2509.13313) |
| MemAgent | 2025 | Uses reinforcement learning to train memory management policies across multiple conversation turns for improved long-context handling. | [[arXiv]](https://arxiv.org/abs/2507.02259) |
| Agent S | 2024 | Creates computer-using agents with human-like interaction patterns, maintaining working memory of application state and task progress. | [[arXiv]](https://arxiv.org/abs/2410.08164) |

#### ⚙️ **Parametric Working Memory**

> **Parametric Working Memory** implements working memory through learned model components, such as attention mechanisms that learn what to focus on, or architectural modifications that improve context utilization efficiency.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| Self-Guided Test-Time Training | 2026 | The LLM first identifies evidence spans in a long context, then test-time trains with the language-modeling loss restricted to those spans; up to 15% relative accuracy improvement on LongBench-v2 and LongBench-Pro. | [[arXiv]](https://arxiv.org/abs/2607.09415) |
| TTT-E2E | 2025 | Treats long-context modeling as continual learning: a sliding-window Transformer compresses context into weights at test time from a meta-learned initialization, with constant latency. | [[arXiv]](https://arxiv.org/abs/2512.23675) [[GitHub]](https://github.com/test-time-training/e2e) |
| ATLAS (Memory Module) | 2025 | Long-term memory module that optimizes memory over current and past tokens rather than purely online updates, raising capacity over Titans-style recurrent memories; +80% accuracy at 10M context on BABILong. | [[arXiv]](https://arxiv.org/abs/2505.23735) |
| Miras | 2025 | Recasts sequence architectures as associative memories defined by attentional bias and retention objectives; the resulting Moneta, Yaad and Memora models beat linear RNNs on recall-intensive tasks. | [[arXiv]](https://arxiv.org/abs/2504.13173) |
| Lightning Attention | 2025 | Achieves constant-speed inference regardless of sequence length through linear attention with learned decay patterns. | [[OpenReview]](https://openreview.net/forum?id=Lwm6TiUP4X) |

#### 🧬 **Latent Working Memory**

> **Latent Working Memory** manages active context through compressed latent representations, including KV cache optimization, recurrent memory states, and memory tokens. These approaches reduce memory footprint while preserving essential information for ongoing computation.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| RestoreKV | 2026 | Adds a compact context-conditioned restore cache, produced by learnable restore tokens with LoRA-adapted attention and self-distillation, to query-agnostic eviction; at 5% budget lifts KVzip from 38.2 to 73.2 on RULER-4K. | [[arXiv]](https://arxiv.org/abs/2608.01247) |
| InfoKV | 2026 | Entropy-aware KV cache compression scoring how compressed tokens affect future contexts by combining predictive uncertainty with attention, for long-context reasoning. | [[arXiv]](https://arxiv.org/abs/2606.26875) |
| MemoryVLA++ | 2026 | Extends MemoryVLA with a perceptual-cognitive memory bank for historical context plus a latent world model that imagines future states, with real-robot gains on memory-dependent tasks. | [[arXiv]](https://arxiv.org/abs/2606.09827) |
| LCLM | 2026 | Latent Context Language Models: a 0.6B encoder compresses token sequences into latent embeddings for a 4B decoder at 1:4 to 1:16 ratios, pretrained on 350B+ tokens. | [[arXiv]](https://arxiv.org/abs/2606.09659) |
| Still | 2026 | Lightweight per-layer Perceiver, trained once against a frozen model, that compacts the KV cache in a single forward pass without per-context optimization; 8x–200x compression. | [[arXiv]](https://arxiv.org/abs/2606.07878) |
| Tangram | 2026 | Serving system for non-uniform KV compression in multi-turn workloads using budget reservation, ragged paging and ahead-of-time load balancing; up to 2.6x end-to-end throughput at accuracy parity. | [[arXiv]](https://arxiv.org/abs/2606.06302) [[GitHub]](https://github.com/aiha-lab/TANGRAM) |
| KV-CAT | 2026 | Formalizes KV compressibility as a learned representation property and trains with randomly masked KV slots so models become compressible, improving quality–budget trade-offs of downstream compressors. | [[arXiv]](https://arxiv.org/abs/2605.05971) |
| DSCache | 2026 | Training-free streaming-video KV cache construction keeping separate cumulative and instant caches with position-agnostic encoding, so video LLMs handle streams beyond training length. | [[arXiv]](https://arxiv.org/abs/2605.01858) |
| GVote | 2026 | Eliminates manual budget specification for KV cache via query sampling and voting, achieving 0.35 accuracy with only 10% memory on Multi-Doc QA (ICLR 2026). | [[OpenReview]](https://openreview.net/forum?id=0yLdDZMutq) |
| SemantiCache | 2026 | Partitions KV cache into semantically coherent chunks and applies greedy seed-based clustering to preserve semantic integrity during compression. | [[arXiv]](https://arxiv.org/abs/2603.14303) |
| VQKV | 2026 | Applies vector quantization to KV representations, achieving 82.8% compression on LLaMA3.1-8B while retaining 98.6% baseline performance. | [[arXiv]](https://arxiv.org/abs/2603.16435) |
| EchoKV | 2026 | Flexible KV cache compression enabling on-demand transitions between standard and compressed inference via similarity-based reconstruction. | [[arXiv]](https://arxiv.org/abs/2603.22910) [[GitHub]](https://github.com/noforit/EchoKV) |
| Mixture of Chapters | 2026 | Learnable sparse memory banks of latent tokens queried via cross-attention with chapter-based MoE routing, scaling to 262K memory tokens. | [[arXiv]](https://arxiv.org/abs/2603.21096) [[GitHub]](https://github.com/Tasmay-Tibrewal/Memory) |
| Latent Context Compilation | 2026 | Distills long contexts into compact buffer tokens via a disposable LoRA compiler, creating portable memory artifacts compatible with frozen base models. | [[arXiv]](https://arxiv.org/abs/2602.21221) |
| Cartridges | 2025 | Trains a corpus-specific KV cache offline through "self-study" and loads it at inference instead of the documents; matches in-context learning with 38.6x less memory. | [[arXiv]](https://arxiv.org/abs/2506.06266) |
| DMS | 2025 | Dynamic Memory Sparsification delays token eviction so representations implicitly merge, reaching 8x KV compression after 1K training steps for inference-time hyper-scaling (NeurIPS 2025). | [[arXiv]](https://arxiv.org/abs/2506.05345) |
| KVzip | 2025 | Query-agnostic eviction scoring KV pairs by how much the model needs them to reconstruct the context; 3–4x cache reduction with negligible loss on contexts up to 170K tokens (NeurIPS 2025). | [[arXiv]](https://arxiv.org/abs/2505.23416) [[GitHub]](https://github.com/snu-mllab/KVzip) |
| EvicPress | 2025 | Jointly optimizes KV cache compression and eviction strategies for efficient LLM inference, balancing memory usage with generation quality. | [[arXiv]](https://arxiv.org/abs/2512.14946) |
| ChunkKV | 2025 | Compresses KV cache by grouping semantically similar tokens into chunks, preserving attention patterns while reducing memory footprint. | [[arXiv]](https://arxiv.org/abs/2502.00299) |
| SmallKV | 2025 | Uses a small auxiliary model to compensate for information lost during aggressive KV cache compression in the main model. | [[arXiv]](https://arxiv.org/abs/2508.02751) |
| KVCompose | 2025 | Creates composite tokens that summarize multiple KV cache entries, enabling structured compression that preserves important information. | [[arXiv]](https://arxiv.org/abs/2509.05165) |
| Expected Attention | 2025 | Predicts which KV cache entries will be attended to by future tokens, enabling proactive eviction of unlikely-to-be-used entries. | [[arXiv]](https://arxiv.org/abs/2510.00636) |
| MemMamba | 2025 | Analyzes and improves memory utilization patterns in state space models, optimizing how information flows through recurrent computations. | [[arXiv]](https://arxiv.org/abs/2510.03279) |
| Time-VLM | 2025 | Applies vision-language model memory mechanisms to time series, enabling multimodal understanding of temporal patterns. | [[arXiv]](https://arxiv.org/abs/2502.04395) |
| SoftCoT | 2025 | Replaces explicit reasoning tokens with soft continuous representations, enabling efficient chain-of-thought reasoning in latent space. | [[ACL]](https://aclanthology.org/2025.acl-long.1137/) |
| MemoRAG | 2025 | Enhances RAG with global memory that captures document-wide patterns, improving retrieval for queries requiring broad context understanding. | [[ACM]](https://doi.org/10.1145/3696410.3714805) |
| MemGen | 2025 | Creates generative memory models that can synthesize new memories from latent representations, enabling creative experience recombination. | [[arXiv]](https://arxiv.org/abs/2509.24704) |
| Conflict-Aware Soft Prompting | 2025 | Uses soft prompts to resolve conflicts between retrieved information and model knowledge, improving RAG reliability. | [[arXiv]](https://arxiv.org/abs/2508.15253) |
| MemoryVLA | 2025 | Integrates perceptual and cognitive memory in vision-language-action models, enabling robots to remember and reason about manipulation tasks. | [[arXiv]](https://arxiv.org/abs/2508.19236) |
| MEM1 | 2025 | Learns optimal integration of memory retrieval with reasoning steps for efficient completion of long-horizon tasks. | [[arXiv]](https://arxiv.org/abs/2506.15841) |
| RazorAttention | 2025 | Identifies retrieval-focused attention heads and compresses their KV caches specifically, preserving critical information access patterns. | [[OpenReview]](https://openreview.net/forum?id=tkiZQlL04w) |
| LM2 | 2025 | Introduces large-scale learnable memory modules that augment language models with massive external memory capacity. | [[arXiv]](https://arxiv.org/abs/2502.06049) |
| Titans | 2025 | Enables models to learn and update memory during inference, adapting to test-time information without training. | [[arXiv]](https://arxiv.org/abs/2501.00663) [[GitHub]](https://github.com/ai-inpm/Titans---Learning-to-Memorize-at-Test-Time) |
| TTT | 2025 | Implements test-time training in RNN hidden states, enabling dynamic memory updates during inference. | [[arXiv]](https://arxiv.org/abs/2407.04620) [[GitHub]](https://github.com/test-time-training/ttt-lm-pytorch) |
| Adacc | 2025 | Adaptively trades off compression and checkpointing based on memory pressure, optimizing memory usage during LLM inference. | [[arXiv]](https://arxiv.org/abs/2508.00806) |
| EdgeInfinite | 2025 | Enables infinite-context processing on edge devices through extreme memory efficiency techniques for on-device deployment. | [[arXiv]](https://arxiv.org/abs/2503.22196) |
| ClusterKV | 2024 | Clusters KV cache entries in semantic space for compression while maintaining ability to recall detailed information when needed. | [[arXiv]](https://arxiv.org/abs/2412.03213) |
| KV Cache Survey | 2024 | Comprehensively surveys KV cache optimization techniques including compression, eviction, quantization, and architectural modifications for efficient LLM inference. | [[arXiv]](https://arxiv.org/abs/2412.19442) |
| Sentinel Tokens | 2024 | Inserts learnable sentinel tokens that aggregate context information, providing compressed working memory anchors for improved modeling. | [[EMNLP]](https://doi.org/10.18653/v1/2024.findings-emnlp.233) |
| SnapKV | 2024 | Predicts important KV cache entries before generation begins, enabling proactive caching of relevant context. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2024/hash/28ab418242603e0f7323e54185d19bde-Abstract-Conference.html) |
| StreamingLLM | 2024 | Enables infinite-length streaming by maintaining attention sinks that anchor the working memory window for stable generation. | [[ICLR]](https://openreview.net/forum?id=NG7sS51zVF) [[GitHub]](https://github.com/mit-han-lab/streaming-llm) |
| PyramidKV | 2024 | Applies pyramidal compression where early layers retain more keys while later layers are more aggressively compressed. | [[arXiv]](https://arxiv.org/abs/2406.02069) [[GitHub]](https://github.com/Zefan-Cai/PyramidKV) |
| KIVI | 2024 | Quantizes KV cache to 2 bits using asymmetric quantization that preserves important value ranges without fine-tuning. | [[arXiv]](https://arxiv.org/abs/2402.02750) [[GitHub]](https://github.com/jy-yuan/KIVI) |
| MiniCache | 2024 | Compresses KV cache across the depth dimension by sharing representations between adjacent layers. | [[arXiv]](https://arxiv.org/abs/2405.14366) |
| CacheGen | 2024 | Accelerates context loading through pre-computed and cached KV representations that can be rapidly loaded for repeated contexts. | [[arXiv]](https://arxiv.org/abs/2310.07240) [[GitHub]](https://github.com/LMCache/LMCache) |
| Infini-Attention | 2024 | Combines local attention with compressive memory that accumulates information from unbounded past context for infinite-length processing. | [[arXiv]](https://arxiv.org/abs/2404.07143) |
| H2O | 2023 | Identifies and retains heavy-hitter tokens that receive disproportionate attention, enabling aggressive KV cache reduction without quality loss. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/6ceefa7b15572587b78ecfcebb2827f8-Abstract-Conference.html) |
| Augmenting LLMs with Long-Term Memory | 2023 | Augments LLMs with differentiable long-term memory modules that persist across contexts and can be updated through backpropagation. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/ebd82705f44793b6f9ade5a669d0f0bf-Abstract-Conference.html) |
| Context Compression | 2023 | Trains language models to compress long contexts into shorter representations while preserving task-relevant information. | [[EMNLP]](https://doi.org/10.18653/v1/2023.emnlp-main.232) |
| Gist Tokens | 2023 | Learns compressed gist tokens that capture prompt semantics, enabling efficient prompt caching and reuse. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/3d77c6dcc7f143aa2154e7f4d5e22d68-Abstract-Conference.html) |
| Scissorhands | 2023 | Leverages the observation that token importance persists across layers to efficiently prune KV cache entries. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/a452a7c6c463e4ae8fbdc614c6e983e6-Abstract-Conference.html) |
| Focused Transformer | 2023 | Uses contrastive learning to train transformers that better focus attention on relevant context, improving long-range dependencies. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/8511d06d5590f4bda24d42087802cc81-Abstract-Conference.html) |
| In-Context Autoencoder | 2023 | Trains an autoencoder within the language model that compresses and reconstructs context representations for efficient processing. | [[arXiv]](https://arxiv.org/abs/2307.06945) |
| Scaling RMT to 1M Tokens | 2023 | Scales Recurrent Memory Transformer to handle 2 million token contexts through improved memory management and training. | [[arXiv]](https://arxiv.org/abs/2304.11062) |
| Memorizing Transformers | 2022 | Augments transformers with kNN-based memory that can store and retrieve from massive external databases at inference time. | [[OpenReview]](https://openreview.net/forum?id=TrjbxzRcnf-) |
| Recurrent Memory Transformer | 2022 | Adds recurrent memory tokens that carry information across segments, enabling transformers to process unlimited length sequences. | [[NeurIPS]](https://openreview.net/forum?id=Uynr3iPhksa) [[GitHub]](https://github.com/booydar/recurrent-memory-transformer) |
| XMem | 2022 | Models video object segmentation memory after human memory systems with sensory, working, and long-term memory stores. | [[arXiv]](https://arxiv.org/abs/2207.07115) |
| Compressive Transformer | 2020 | Compresses old memories into fixed-size representations that can still be attended to, balancing memory capacity with computational cost. | [[arXiv]](https://arxiv.org/abs/1911.05507) |
| Longformer | 2020 | Uses sliding window attention with global tokens to achieve linear complexity for long document processing. | [[arXiv]](https://arxiv.org/abs/2004.05150) [[GitHub]](https://github.com/allenai/longformer) |
| BigBird | 2020 | Combines random, window, and global attention patterns to create sparse attention that scales linearly with sequence length. | [[NeurIPS]](https://proceedings.neurips.cc/paper/2020/hash/c8512d142a2d849725f31a9a7a361ab9-Abstract.html) |
| Transformer-XL | 2019 | Introduces segment-level recurrence where hidden states from previous segments are cached and reused, enabling longer context modeling. | [[arXiv]](https://arxiv.org/abs/1901.02860) [[GitHub]](https://github.com/kimiyoung/transformer-xl) |
| Differentiable Neural Computer | 2016 | Extends Neural Turing Machines with improved memory addressing including content-based lookup and temporal memory linking. | [[Nature]](https://www.nature.com/articles/nature20101) |
| Neural Turing Machine | 2014 | Augments neural networks with differentiable external memory that can be read from and written to through attention-based addressing. | [[arXiv]](https://arxiv.org/abs/1410.5401) |

## 🧭 Spatial Memory for Mobile Robots

> **Spatial memory** is what lets a mobile robot answer "where am I, what is where, and where did I last see it?" after the observation has left its field of view. It spans dense metric-semantic maps, 3D scene graphs, topological and episodic stores, and the implicit memory inside navigation foundation models. This section covers wheeled and legged robots, drones, and mobile manipulators across object-goal and instance navigation, vision-language navigation (VLN), embodied question answering (EQA), and mobile manipulation.

For a focused treatment of the representations and their on-robot memory cost, see [A Survey of Spatial Memory Representations for Efficient Robot Navigation](https://arxiv.org/abs/2604.16482) (2026).

### Spatial Memory Representations

| Representation | What is stored | Queried by | Strengths | Limitations |
|----------------|----------------|------------|-----------|-------------|
| **Metric-semantic maps** | Voxels, points, neural fields or Gaussians carrying open-vocabulary features | Text/image similarity, rendering | Precise geometry, direct path planning | Memory grows with map size; costly to update when the scene changes |
| **3D scene graphs** | Objects, places, rooms and floors as nodes; spatial and semantic relations as edges | Graph search, LLM reasoning over subgraphs | Compact, hierarchical, readable by LLM planners | Depends on segmentation and relation quality; fine geometry is abstracted away |
| **Topological / episodic memory** | Keyframes, places, captions and events linked by traversability and time | Retrieval (vector, graph, temporal) | Scales to long horizons and multiple sessions; cheap to append | No metric guarantees; retrieval quality bounds performance |
| **Implicit / token memory** | Compressed visual-history tokens, recurrent states, KV caches, spatial-foundation-model states | Attention inside the policy | End-to-end trainable, no explicit mapping pipeline | Bounded context, hard to inspect or edit, weak over very long horizons |
| **Neuro-inspired memory** | Cognitive maps, grid-like codes, landmark/route/survey knowledge | Learned read-out | Sample-efficient structure, biological grounding | Mostly validated in simulation |

In terms of the taxonomy above, explicit maps and graphs are the spatial analogue of **token-level** memory, map-free policies carry **latent** memory, and the map itself plays the role of **factual** memory while cross-episode stores of where things were found are **experiential**.

### Metric-Semantic and Open-Vocabulary Maps

> Dense spatial memories (voxel grids, point maps, neural fields, Gaussian splats) that attach open-vocabulary features to geometry so a robot can localize language-specified goals and plan directly on the map.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| OASIS-Map | 2026 | Multi-session object-level mapping: keeps a spatio-temporally consistent object map and detects appeared, removed, moved or replaced objects using dense patch correspondences across revisits, for long-term inspection robots. | [[arXiv]](https://arxiv.org/abs/2607.14899) [[Website]](https://dynamic.robots.ox.ac.uk/projects/oasis-map/) |
| SERF | 2026 | Spatiotemporal Environment and Robot Feature map: environment and articulated robot body are neural points in one latent space, updated by object-level rigid tracking and forward kinematics, tokenized for a VLA on BEHAVIOR-1K. | [[arXiv]](https://arxiv.org/abs/2606.12956) [[Website]](https://existentialrobotics.org/serf/) |
| ESCAPE | 2026 | Episodic spatial memory for long-horizon mobile manipulation: a depth-free persistent 3D memory built autoregressively by spatio-temporal fusion mapping, queried by a memory-driven grounding module on ALFRED. | [[arXiv]](https://arxiv.org/abs/2604.13633) |
| MetaNav | 2026 | A persistent 3D semantic map combined with history-aware planning and reflective (metacognitive) correction to stop redundant wandering; evaluated on GOAT-Bench, HM3D-OVON and A-EQA. | [[arXiv]](https://arxiv.org/abs/2604.02318) |
| R2F | 2026 | Repurposes ray frontiers for LLM-free open-vocabulary object navigation: language-aligned features accumulated along out-of-range rays at frontiers are scored against the query embedding to select goals; Habitat and real robot. | [[arXiv]](https://arxiv.org/abs/2603.08475) [[Website]](https://lab-roccoo-sapienza.github.io/r2f/) |
| LAMP (Implicit Language Map) | 2026 | Implicit Language Map: stores language features in an implicit neural field instead of per-location embeddings, paired with a sparse graph for coarse planning and gradient-based goal-pose refinement in a multi-floor building. | [[arXiv]](https://arxiv.org/abs/2602.11862) [[Website]](https://lab-of-ai-and-robotics.github.io/LAMP/) |
| LangGS-SLAM | 2026 | Real-time language-feature Gaussian-splatting RGB-D SLAM: each Gaussian carries VLM features, rendered with a Top-K pipeline and pruned by multi-criteria map management; open-vocabulary text queries at 15 FPS. | [[arXiv]](https://arxiv.org/abs/2602.06991) |
| APEX | 2026 | Decoupled memory-based explorer for aerial object-goal navigation: a VLM builds 3D attraction, exploration and obstacle maps as interpretable spatio-semantic memory that an RL action module queries. | [[arXiv]](https://arxiv.org/abs/2602.00551) [[GitHub]](https://github.com/4amGodvzx/apex) |
| Multimodal Spatial Language Maps | 2025 | Extends VLMaps/AVLMaps by fusing visual, audio and language foundation features into one 3D map built during exploration; queried by text, image or sound to ground goals. | [[arXiv]](https://arxiv.org/abs/2506.06862) |
| DualMap | 2025 | Online open-vocabulary mapping with a dual structure: an abstract global map for coarse retrieval and a concrete local map updated in changing scenes; language queries drive navigation as objects move. | [[arXiv]](https://arxiv.org/abs/2506.01950) [[GitHub]](https://github.com/Eku127/DualMap) |
| RayFronts | 2025 | Open-set semantic ray frontiers: stores dense open-set features in voxels within depth range and on rays at map frontiers beyond it, so robots can query beyond-range semantics during exploration. | [[arXiv]](https://arxiv.org/abs/2504.06994) |
| OpenGS-SLAM | 2025 | Open-set dense semantic SLAM with 3D Gaussians: integrates labels from 2D foundation models using Gaussian voting splatting and multi-view consensus, giving an object-level, queryable Gaussian map. | [[arXiv]](https://arxiv.org/abs/2503.01646) [[Website]](https://young-bit.github.io/opengs-github.github.io/) |
| DynaMem | 2024 | Online dynamic spatio-semantic memory: a voxel map of VLM features whose points are added and removed as the scene changes; queried by text for open-world mobile manipulation. | [[arXiv]](https://arxiv.org/abs/2411.04999) [[Website]](https://dynamem.github.io/) |
| LEGS | 2024 | Language-Embedded Gaussian Splats: a mobile robot incrementally trains a room-scale Gaussian-splat map with language features online while exploring, then answers open-vocabulary object-localization queries. | [[arXiv]](https://arxiv.org/abs/2409.18108) |
| OneMap | 2024 | "One Map to Find Them All": a real-time open-vocabulary feature map with uncertainty-aware probabilistic fusion, reused across successive queries for zero-shot multi-object navigation on onboard compute. | [[arXiv]](https://arxiv.org/abs/2409.11764) [[Website]](https://finnbsch.github.io/OneMap) |
| GaussNav | 2024 | Builds a semantic 3D Gaussian map of the scene, renders novel views to match a goal-instance image, and plans on the grounded map for instance-image-goal navigation. | [[arXiv]](https://arxiv.org/abs/2403.11625) [[GitHub]](https://github.com/XiaohanLei/GaussNav) |
| OK-Robot | 2024 | Open-knowledge pick-and-drop system: a VoxelMap of CLIP/OWL-ViT features built from a phone scan is queried by language to get navigation and grasp targets for a Stretch robot in real homes. | [[arXiv]](https://arxiv.org/abs/2401.12202) [[GitHub]](https://github.com/ok-robot/ok-robot) |
| LangSplat | 2023 | 3D Language Gaussian Splatting: attaches compressed, SAM-hierarchical CLIP features to 3D Gaussians for fast open-vocabulary 3D queries; the template for Gaussian-splat language maps on robots. | [[arXiv]](https://arxiv.org/abs/2312.16084) [[Website]](https://langsplat.github.io/) |
| VLFM | 2023 | Vision-Language Frontier Maps: builds an occupancy map plus a language-grounded value map from VLM image–text similarity and picks the most promising frontier for zero-shot object-goal navigation; deployed on Spot. | [[arXiv]](https://arxiv.org/abs/2312.03275) [[Website]](https://naoki.io/vlfm) |
| GOAT | 2023 | "GO to Any Thing": an instance-aware semantic memory stores per-object views and category/language/image features in a top-down map, updated over a lifelong episode and matched to multimodal goals. | [[arXiv]](https://arxiv.org/abs/2311.06430) |
| HomeRobot OVMM | 2023 | Open-vocabulary mobile manipulation benchmark and stack: agents keep a semantic map built from open-vocabulary detections to find, pick and place arbitrary objects in unseen homes. | [[arXiv]](https://arxiv.org/abs/2306.11565) [[Website]](https://ovmm.github.io/) |
| USA-Net | 2023 | Unified semantic and affordance representation for robot memory: a neural field jointly storing CLIP-aligned semantics and a differentiable collision field, so language-specified goals and paths come from one memory. | [[arXiv]](https://arxiv.org/abs/2304.12164) [[Website]](https://usa.bolte.cc/) |
| LERF | 2023 | Language Embedded Radiance Fields: distills multi-scale CLIP embeddings into a NeRF so 3D relevancy maps can be rendered for open-ended language queries; the basis of later robot language-field memories. | [[arXiv]](https://arxiv.org/abs/2303.09553) [[Website]](https://lerf.io) |
| ConceptFusion | 2023 | Open-set multimodal 3D mapping: fuses pixel-aligned foundation-model features into a dense SLAM point map, queryable zero-shot by text, image, audio or click. | [[arXiv]](https://arxiv.org/abs/2302.07241) [[GitHub]](https://github.com/concept-fusion/concept-fusion) |
| OpenScene | 2022 | Predicts dense per-point 3D features co-embedded with CLIP text and pixels, giving a task-agnostic open-vocabulary scene representation queryable by arbitrary text. | [[arXiv]](https://arxiv.org/abs/2211.15654) [[Website]](https://pengsongyou.github.io/openscene) |
| VLMaps | 2022 | Visual Language Maps: fuses pixel-aligned vision-language features into a top-down grid; landmarks are localized by text-query similarity, letting an LLM compose spatial navigation goals. | [[arXiv]](https://arxiv.org/abs/2210.05714) [[Website]](https://vlmaps.github.io) |
| NLMap | 2022 | Open-vocabulary queryable scene representation: a map of class-agnostic region proposals with VLM embeddings built during exploration; an LLM planner queries it for object presence and location. | [[arXiv]](https://arxiv.org/abs/2209.09874) [[Website]](https://nlmap-saycan.github.io) |

> See also in [Token-level Factual Memory](#-token-level-factual-memory): CLIP-Fields, Mem2Ego.

### 3D Scene Graphs and Hierarchical Memory

> Object-, place- and room-level graphs that compress a scene into a hierarchy an LLM or planner can search, including dynamic and spatio-temporal graphs that track how the scene changes.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| TRACKGRAPH | 2026 | Online open-vocabulary 3D scene graphs via image-space tracking: tracked 2D masks are fused into persistent class-agnostic 3D segments with compact multi-view CLIP embeddings; runs onboard quadrupeds for object search. | [[arXiv]](https://arxiv.org/abs/2609.31005) |
| Hierarchical Scene Graph Belief Planning | 2026 | Online hierarchical 3D scene graph (objects, zones, regions) built with Voronoi-diagram and spectral clustering; a hierarchical belief fuses LLM priors with evidence and plans by POUCT for semantic navigation. | [[arXiv]](https://arxiv.org/abs/2606.31071) |
| Relationship-Aware Hierarchical 3DSG | 2026 | Five-layer hierarchical 3D scene graph with open-vocabulary features and VLM-derived object relationships, built incrementally from RGB-D and odometry; queried by CLIP similarity and LLM reasoning on a quadruped. | [[arXiv]](https://arxiv.org/abs/2602.02456) |
| DAAAM | 2025 | "Describe Anything Anywhere At Any Moment": builds a hierarchical 4D scene graph with detailed, geometrically grounded descriptions online as a spatially and temporally consistent memory; evaluated on NaVQA and SG3D. | [[arXiv]](https://arxiv.org/abs/2512.00565) |
| VL-KnG | 2025 | Spatiotemporal knowledge graphs as persistent scene memory: built once from egocentric video with LLM-based object association, then queried by graph-enhanced retrieval for embodied QA and real-robot navigation. | [[arXiv]](https://arxiv.org/abs/2510.01483) |
| GraphPad | 2025 | Inference-time 3D scene-graph updates for embodied QA: a modifiable structured memory the VLM edits through API calls, adding task-relevant detail on demand. | [[arXiv]](https://arxiv.org/abs/2506.01174) |
| UniGoal | 2025 | Universal zero-shot goal-oriented navigation: represents both the online scene and the goal (object, image or text) as graphs and uses LLM graph matching to steer exploration stages. | [[arXiv]](https://arxiv.org/abs/2503.10630) |
| CURB-OSG | 2025 | Collaborative dynamic 3D scene graphs for open-vocabulary urban scenes: multiple agents fuse observations into one dynamic scene graph of outdoor environments via multi-agent loop closure. | [[arXiv]](https://arxiv.org/abs/2503.08474) [[Website]](https://ov-curb.cs.uni-freiburg.de) |
| OpenIN | 2025 | Open-vocabulary instance-oriented navigation in dynamic homes: a carrier-relationship scene graph records which furniture carries which movable objects and is updated as items move. | [[arXiv]](https://arxiv.org/abs/2501.04279) [[Website]](https://OpenIN-nav.github.io) |
| GraphEQA | 2024 | A real-time metric-semantic 3D scene graph plus task-relevant images forms multimodal memory that grounds a VLM planner for exploration and embodied question answering. | [[arXiv]](https://arxiv.org/abs/2412.14480) |
| DovSG | 2024 | Dynamic open-vocabulary 3D scene graphs for long-term language-guided mobile manipulation: the graph is updated locally as the robot acts and the scene changes, avoiding full rebuilds. | [[arXiv]](https://arxiv.org/abs/2410.11989) [[Website]](https://bjhyzj.github.io/dovsg-web) |
| SG-Nav | 2024 | Online 3D scene graph prompting for zero-shot object navigation: incrementally builds a hierarchical 3D scene graph and prompts an LLM over subgraphs to score frontiers and re-verify detections. | [[arXiv]](https://arxiv.org/abs/2410.08189) |
| Clio | 2024 | Real-time task-driven open-set 3D scene graphs: uses the Information Bottleneck to cluster 3D primitives into only the task-relevant objects and places, deciding what the map keeps. | [[arXiv]](https://arxiv.org/abs/2404.13696) |
| HOV-SG | 2024 | Hierarchical open-vocabulary 3D scene graphs: floor, room and object nodes with CLIP features, far more compact than dense maps; queried hierarchically by language for multi-story navigation. | [[arXiv]](https://arxiv.org/abs/2403.17846) [[Website]](http://hovsg.github.io/) |
| MoMa-LLM | 2024 | Grounds LLMs in a dynamically built hierarchical scene graph (Voronoi navigation graph, rooms, objects) that grows during exploration, for interactive object search by a mobile manipulator. | [[arXiv]](https://arxiv.org/abs/2403.08605) [[Website]](http://moma-llm.cs.uni-freiburg.de) |
| Khronos | 2024 | Spatio-temporal metric-semantic SLAM: factorizes short-term dynamics and long-term changes to maintain a 4D map of how objects appear, move and disappear over time. | [[arXiv]](https://arxiv.org/abs/2402.13817) [[GitHub]](https://github.com/MIT-SPARK/Khronos) |
| Open3DSG | 2024 | Open-vocabulary 3D scene graphs from point clouds: object nodes queryable through CLIP features and open-set relationships predicted without labeled scene-graph data. | [[arXiv]](https://arxiv.org/abs/2402.12259) [[Website]](https://kochsebastian.com/open3dsg) |
| ConceptGraphs | 2023 | Open-vocabulary 3D scene graphs: object nodes fused from 2D foundation-model segments with CLIP features and LLM-captioned relations; queried by LLMs for navigation, manipulation and re-localization. | [[arXiv]](https://arxiv.org/abs/2309.16650) [[Website]](https://concept-graphs.github.io/) |
| SayPlan | 2023 | Grounds LLM task planning in large 3D scene graphs: the LLM semantically searches a collapsed graph, expanding only relevant subgraphs, then refines plans with a simulator. | [[arXiv]](https://arxiv.org/abs/2307.06135) [[Website]](https://sayplan.github.io) |
| Hydra | 2022 | Real-time spatial perception system that incrementally builds and optimizes a hierarchical 3D scene graph (mesh, objects, places, rooms) online, with loop closures correcting all layers. | [[arXiv]](https://arxiv.org/abs/2201.13360) |
| 3D Dynamic Scene Graphs | 2020 | A layered graph from metric-semantic mesh to places, rooms and buildings with tracked agents, built automatically from visual-inertial data as an actionable spatial memory. | [[arXiv]](https://arxiv.org/abs/2002.06289) |
| 3D Scene Graph | 2019 | The original layered graph of buildings, rooms, objects and cameras with attributes and relations, unifying semantics, 3D space and camera. | [[arXiv]](https://arxiv.org/abs/1910.02527) |

> See also in [Token-level Factual Memory](#-token-level-factual-memory): Graph2Nav, RoboMemory.

### Topological, Episodic and Spatio-Temporal Memory

> Graphs of places and keyframes, retrieval-based long-term stores, and lifelong memories that answer "where did I see X?" across long horizons, multiple sessions and changing scenes.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| ECROM | 2026 | Retrospective open-vocabulary memory for long-term object search: treats memory as probabilistic inference from censored observations, estimating object prevalence at query time as an active-search prior. | [[arXiv]](https://arxiv.org/abs/2610.00330) |
| EvolvingNav | 2026 | "Beyond the Remembered World": a time-indexed predictive 4D belief over timestamped 3D object histories with a persistence-relocation model, for finding objects that moved while unobserved. | [[arXiv]](https://arxiv.org/abs/2609.39166) [[GitHub]](https://github.com/ZJU4EmbodiedAI/EvolvingNav) |
| LT-Mem | 2026 | Volatility-aware lifelong memory: Live, Delta (timestamped event log) and Meta (volatility statistics) memories over multi-session SLAM, with overwrite/hold/multi-hypothesis updates and cross-session temporal queries. | [[arXiv]](https://arxiv.org/abs/2608.19059) [[Website]](https://lt-mem.github.io/) |
| HAM-VLN | 2026 | Hierarchical agentic memory for zero-shot VLN: a depth-grounded world graph of places and objects plus working memory of recent frames; older observations are retrieved by relevance, recency and salience. | [[arXiv]](https://arxiv.org/abs/2607.29600) |
| VTM-Nav | 2026 | Cross-episode hierarchical visual-topological memory for object-goal navigation: a coarse room topology indexes room-owned visual memories, retrieved coarse-to-fine to re-rank actions of a frozen VLM. | [[arXiv]](https://arxiv.org/abs/2607.14514) |
| RAVEN | 2026 | Visuo-spatio-temporal agentic memory: stores visual embeddings with pose and time in a vector database, grounding retrieval in a spatial map without captioning; long-horizon QA and goal-reaching on a quadruped. | [[arXiv]](https://arxiv.org/abs/2606.25206) |
| VL-MemKnG | 2026 | Hybrid memory for QA over long egocentric navigation trajectories: a spatio-temporal knowledge graph plus persistent segment-level contextual memory, queried jointly by hybrid retrieval. | [[arXiv]](https://arxiv.org/abs/2606.17183) |
| SpaceVLN | 2026 | Zero-shot VLN with online hierarchical Spatial Cognitive Memory that abstracts explored regions into spatial waypoints and tracks subtask-grounded landmark evidence; R2R-CE, RxR-CE, HM3D-OVON and real robot. | [[arXiv]](https://arxiv.org/abs/2606.08992) |
| eMEM | 2026 | Hybrid spatio-temporal memory system for embodied agents: an embedded multi-index store (SQLite, HNSW semantic search, R-tree spatial queries) unified as a graph; evaluated in ProcTHOR. | [[arXiv]](https://arxiv.org/abs/2606.03374) |
| Change-Robust Topological Memory | 2026 | Pose-aware topological graph of RGB-D keyframes with a bounded Gaussian-mixture pose belief, for long-term relocalization and object-goal navigation under lighting shifts and furniture rearrangement. | [[arXiv]](https://arxiv.org/abs/2605.02227) |
| HiCo-Nav | 2026 | Deployable VLN system with hierarchical cognition: incrementally builds a compact memory graph and feeds decomposed subgraphs to a VLM in an asynchronous fast/slow architecture on real robots. | [[arXiv]](https://arxiv.org/abs/2604.21363) [[GitHub]](https://github.com/xukuanHIT/HiCo-Nav) |
| OVAL | 2026 | Open-vocabulary augmented memory for lifelong object-goal navigation: structured memory descriptors manage long-term memory, with probability-based multi-value frontier scoring. | [[arXiv]](https://arxiv.org/abs/2604.12872) |
| ReMemNav | 2026 | Zero-shot object navigation with a bounded FIFO episodic buffer of visited positions and language descriptions; geometry-triggered retrieval projects past nodes into the current view to correct decisions. | [[arXiv]](https://arxiv.org/abs/2603.26788) |
| HiMemVLN | 2026 | Hierarchical memory for open-source zero-shot VLN: a short-term visual graph of appearance embeddings detects revisits, and long-term instruction schemas constrain exploration; tested on a wheeled quadruped. | [[arXiv]](https://arxiv.org/abs/2603.14807) [[GitHub]](https://github.com/lvkailin0118/HiMemVLN) |
| T²-Nav | 2026 | Temporal graph memory linking scene graphs across time to capture object permanence, with persistent homology to detect loops, for training-free instance-image-goal navigation. | [[arXiv]](https://arxiv.org/abs/2603.06918) [[GitHub]](https://github.com/cogniboticslab/t2nav) |
| STaR | 2026 | Scalable task-conditioned retrieval for long-horizon robot memory: a task-agnostic multimodal long-term memory (objects, spatial relations, events) with Information-Bottleneck retrieval; indoor and outdoor robot. | [[arXiv]](https://arxiv.org/abs/2602.09255) [[Website]](https://trailab.github.io/STaR-website/) |
| MerNav | 2026 | Memory-Execute-Review framework for zero-shot object-goal navigation: a hierarchical memory module supplies information, an execute module decides, and a review module handles anomalies; deployed on a humanoid. | [[arXiv]](https://arxiv.org/abs/2602.05467) [[Website]](https://qidekang.github.io/MerNav.github.io/) |
| MemoryExplorer | 2026 | RL-fine-tuned multimodal LLM that actively queries long-term memory during embodied exploration, rewarded on action prediction, frontier selection and question answering (introduces LMEE-Bench). | [[arXiv]](https://arxiv.org/abs/2601.10744) [[Website]](https://wangsen99.github.io/papers/lmee/) |
| Meta-Memory | 2025 | LLM-driven agent that builds a dense memory of the environment and jointly retrieves semantic and spatial memories to answer location queries; introduces SpaceLocQA and evaluates on NaVQA. | [[arXiv]](https://arxiv.org/abs/2509.20754) [[Website]](https://itsbaymax.github.io/meta-memory.github.io/) |
| Mem4Nav | 2025 | Hierarchical spatial-cognition long-short memory for urban VLN: a sparse octree for fine voxel indexing and a semantic topological graph, with reversible long-term memory tokens and a short-term cache. | [[arXiv]](https://arxiv.org/abs/2506.19433) [[GitHub]](https://github.com/tsinghua-fib-lab/Mem4Nav) |
| STMA | 2025 | Spatio-Temporal Memory Agent: a spatio-temporal memory module with a dynamic knowledge graph for spatial reasoning and a planner-critic loop, for long-horizon embodied tasks. | [[arXiv]](https://arxiv.org/abs/2502.10177) |
| 3D-Mem | 2024 | 3D scene memory of "Memory Snapshots" (informative multi-view images covering co-visible objects) plus frontier snapshots for unexplored areas; incrementally built for VLM exploration and embodied QA. | [[arXiv]](https://arxiv.org/abs/2411.17735) |
| Embodied-RAG | 2024 | Non-parametric embodied memory: a topological map organized into a hierarchical semantic forest of language descriptions, built during exploration and retrieved at multiple granularities. | [[arXiv]](https://arxiv.org/abs/2409.18313) [[Website]](https://quanting-xie.github.io/Embodied-RAG-web/) |
| KARMA | 2024 | Long- and short-term memory for embodied agents: a 3D scene graph as long-term memory plus a dynamically updated short-term memory of object states, retrieved to help LLM planners. | [[arXiv]](https://arxiv.org/abs/2409.14908) [[GitHub]](https://github.com/WZX0Swarm0Robotics/KARMA/tree/master) |
| ETPNav | 2023 | Evolving Topological Planning for VLN-CE: self-organizes predicted waypoints into an online topological map along the trajectory, enabling long-range cross-modal planning. | [[arXiv]](https://arxiv.org/abs/2304.03047) [[GitHub]](https://github.com/MarSaKi/ETPNav) |
| NoMaD | 2023 | Goal-masked diffusion policy unifying goal-directed navigation and undirected exploration; used with a topological memory graph of observations for long-horizon navigation. | [[arXiv]](https://arxiv.org/abs/2310.07896) [[Website]](https://general-navigation-models.github.io/nomad/) |
| ViNT | 2023 | Visual navigation foundation model: a Transformer goal-conditioned policy paired with a topological image graph and diffusion-proposed subgoals for kilometer-scale navigation across embodiments. | [[arXiv]](https://arxiv.org/abs/2306.14846) [[Website]](https://visualnav-transformer.github.io) |
| GNM | 2022 | General Navigation Model: one goal-conditioned policy trained on data from many robots, deployed zero-shot on new robots by navigating over a topological graph of image observations. | [[arXiv]](https://arxiv.org/abs/2210.03370) [[Website]](https://sites.google.com/view/drive-any-robot) |
| ViKiNG | 2022 | Vision-based kilometer-scale navigation: combines a learned local controller and image topological graph with geographic hints (satellite images, roadmaps) as planning heuristics. | [[arXiv]](https://arxiv.org/abs/2202.11271) [[Website]](https://sites.google.com/view/viking-release) |
| ViNG | 2020 | Learns a traversability/distance function over a topological graph of past image observations, used to plan to visual goals on a real outdoor ground robot. | [[arXiv]](https://arxiv.org/abs/2012.09812) [[Website]](https://sites.google.com/view/ving-robot) |
| Neural Topological SLAM | 2020 | Topological representation for image-goal navigation: nodes hold semantic features with coarse geometric connectivity, and learned modules build, maintain and plan over the graph. | [[arXiv]](https://arxiv.org/abs/2005.12256) |
| SPTM | 2018 | Semi-Parametric Topological Memory: a non-parametric graph of visited locations plus a learned retrieval network that localizes the agent and goal in it, built from exploration video. | [[arXiv]](https://arxiv.org/abs/1803.00653) |

> See also in [Token-level Factual Memory](#-token-level-factual-memory): ReMEmbR, Mobility VLA, LM-Nav, Episodic Memory Verbalization, Embodied VideoAgent, Mind Palace, Ella.

### Memory in Navigation Foundation Models

> Implicit spatial memory inside navigation VLMs, VLAs and world models: compressed frame histories, slow-fast token caches, map-as-prompt inputs, and persistent states from 3D foundation models.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| AdaGeoVLN | 2026 | Selective geometry memory for VLN: retains VGGT global-attention KV states under a per-layer budget, chosen by instruction relevance, geometric confidence and novelty; deployed on a humanoid from single RGB. | [[arXiv]](https://arxiv.org/abs/2609.18789) [[Website]](https://humanoid-research.github.io/adageovln/) |
| GA-VLN | 2026 | Geometry-aware BEV representation for efficient VLN: projects visual features from RGB-D into 3D to form compact BEV spatial maps fed to a multimodal LLM in place of long frame histories. | [[arXiv]](https://arxiv.org/abs/2605.22036) |
| StateLinFormer | 2026 | Stateful training for long-term navigation memory: a linear-attention recurrent memory state is preserved across training batches, approximating infinitely long sequences. | [[arXiv]](https://arxiv.org/abs/2603.23571) |
| DecoVLN | 2026 | Decouples observation, reasoning and correction for VLN: long-term memory is built by selecting frames from a history pool with a score balancing relevance, diversity and temporal coverage. | [[arXiv]](https://arxiv.org/abs/2603.13133) |
| PROSPECT | 2026 | Unified streaming VLN: fuses a streaming CUT3R spatial encoder with semantic features by cross-attention for long-context spatial memory, and predicts next-step latent representations. | [[arXiv]](https://arxiv.org/abs/2603.03739) |
| ABot-N0 | 2026 | VLA navigation foundation model covering five navigation tasks; pairs an LLM reasoner and flow-matching action expert with a planner using hierarchical topological memory. | [[arXiv]](https://arxiv.org/abs/2602.11598) [[Website]](https://amap-cvlab.github.io/ABot-Navigation/ABot-N0/) |
| VLingNav | 2026 | Navigation VLA with adaptive reasoning and visual-assisted linguistic memory: a persistent cross-modal semantic memory lets the agent recall past observations and avoid repeated exploration. | [[arXiv]](https://arxiv.org/abs/2601.08665) [[Website]](https://wsakobe.github.io/VLingNav-web/) |
| UniWM | 2025 | Unified memory-augmented world model for visual navigation: one multimodal backbone imagines future views and plans actions, with hierarchical intra-step and cross-step memory. | [[arXiv]](https://arxiv.org/abs/2510.08713) [[GitHub]](https://github.com/UWMILab/UniWM) |
| JanusVLN | 2025 | Dual implicit memory for VLN: spatial-geometric and visual-semantic memories are kept as fixed-size neural caches from a 3D-foundation encoder and the VLM, updated incrementally without explicit maps. | [[arXiv]](https://arxiv.org/abs/2509.22548) [[Website]](https://miv-xjtu.github.io/JanusVLN.github.io/) |
| NavFoM | 2025 | Cross-embodiment, cross-task embodied navigation foundation model trained on millions of samples; handles variable camera setups and bounds visual-history tokens under a fixed budget. | [[arXiv]](https://arxiv.org/abs/2509.12129) [[Website]](https://pku-epic.github.io/NavFoM-Web/) |
| StreamVLN | 2025 | Streaming VLN with SlowFast context: a fast sliding window of recent dialogue plus a slow-updating memory of compressed historical visual tokens, with KV-cache reuse for low latency. | [[arXiv]](https://arxiv.org/abs/2507.05240) [[GitHub]](https://github.com/OpenRobotLab/StreamVLN) |
| MTU3D | 2025 | "Move to Understand a 3D Scene": unifies active exploration and 3D vision-language grounding by treating frontiers and objects as queries in an online spatial memory. | [[arXiv]](https://arxiv.org/abs/2507.04047) |
| Point3R | 2025 | Streaming 3D reconstruction with explicit spatial pointer memory: memory pointers anchored at 3D positions hold local features and are fused as new frames arrive. | [[arXiv]](https://arxiv.org/abs/2507.02863) [[GitHub]](https://github.com/YkiWu/Point3R) |
| 3DLLM-Mem | 2025 | Long-term spatial-temporal memory for an embodied 3D LLM: working-memory tokens query and fuse relevant features from an episodic memory of past 3D observations for multi-room tasks. | [[arXiv]](https://arxiv.org/abs/2505.22657) [[Website]](https://3dllm-mem.github.io) |
| Persistent Embodied World Models | 2025 | A video diffusion world model predicts RGB-D, which is aggregated into a persistent 3D map that conditions later generations for consistent long-horizon simulation and planning. | [[arXiv]](https://arxiv.org/abs/2505.05495) |
| MapNav | 2025 | Replaces frame history with Annotated Semantic Maps: a top-down semantic map updated each step and annotated with text labels is fed to the VLM as compact memory for VLN. | [[arXiv]](https://arxiv.org/abs/2502.13451) |
| CUT3R | 2025 | Continuous 3D perception model with persistent state: recurrent state tokens are updated per frame and read out as metric pointmaps; used as a spatial-memory encoder in later VLN models. | [[arXiv]](https://arxiv.org/abs/2501.12387) [[Website]](https://cut3r.github.io/) |
| Uni-NaVid | 2024 | Video-based VLA unifying VLN, object-goal, EQA and following: an online token-merging scheme keeps short- and long-term visual memory compact for real-time deployment. | [[arXiv]](https://arxiv.org/abs/2412.06224) [[Website]](https://pku-epic.github.io/Uni-NaVid/) |
| NaVILA | 2024 | Legged-robot VLA for navigation: a VLM consumes sampled history frames plus the current view and emits mid-level language actions executed by a locomotion policy. | [[arXiv]](https://arxiv.org/abs/2412.04453) [[Website]](https://navila-bot.github.io/) |
| Navigation World Models | 2024 | Conditional diffusion transformer that predicts future egocentric observations from past frames and navigation actions, used to simulate and rank trajectories. | [[arXiv]](https://arxiv.org/abs/2412.03572) [[Website]](https://www.amirbar.net/nwm/) |
| Spann3R | 2024 | 3D reconstruction with spatial memory: extends DUSt3R with an external spatial memory of past features queried by attention to predict globally consistent pointmaps online. | [[arXiv]](https://arxiv.org/abs/2408.16061) [[Website]](https://hengyiwang.github.io/projects/spanner) |
| NaVid | 2024 | Video-based VLM for VLN: uses only monocular RGB video history, compressed into a few tokens per past frame, as implicit memory to output next-step actions without maps or odometry. | [[arXiv]](https://arxiv.org/abs/2402.15852) |

> See also: Scene Memory Transformer (Token-level Factual Memory); MemoryVLA, MemoryVLA++ (Latent Working Memory); EchoVLA, PhysMem (Token-level Experiential Memory).

### Neuro-Inspired and Classical Spatial Memory

> Learned mapping modules and cognitive-map models that predate foundation models, plus brain-inspired designs built on grid-cell and hippocampal principles.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| BIT-Nav | 2026 | Brain-inspired trajectory memory: a Bi-GRU encodes action and relative-pose sequences with contrastive learning, and the embedding is injected into a VLM as a single memory token per navigation step. | [[arXiv]](https://arxiv.org/abs/2606.21398) |
| BSC-Nav | 2025 | Brain-inspired spatial cognition: structured memory of landmarks, route knowledge and allocentric survey knowledge, retrieved by MLLMs for navigation (Nature Communications, 2026). | [[arXiv]](https://arxiv.org/abs/2508.17198) [[Nature]](https://www.nature.com/articles/s41467-026-74358-5) |
| Emergence of Maps | 2023 | Navigation agents with only egomotion sensing learn map-like structure in recurrent memory, from which occupancy maps can be decoded; evidence for emergent implicit spatial memory. | [[arXiv]](https://arxiv.org/abs/2301.13261) |
| SemExp | 2020 | Goal-oriented semantic exploration: builds an episodic top-down semantic map from first-person detections and learns a long-term goal policy over it for object-goal navigation. | [[arXiv]](https://arxiv.org/abs/2007.00643) [[Website]](https://devendrachaplot.github.io/projects/semantic-exploration.html) |
| Active Neural SLAM | 2020 | A learned neural SLAM module builds a top-down occupancy map and pose estimate, used by a hierarchical global and local policy for exploration and point-goal navigation. | [[arXiv]](https://arxiv.org/abs/2004.05155) |
| Vector-based Navigation | 2018 | A recurrent network trained for path integration develops grid-cell-like representations that give RL agents a Euclidean metric for goal-directed vector navigation and shortcuts. | [[Nature]](https://www.nature.com/articles/s41586-018-0102-6) |
| Grid-like RNN Representations | 2018 | RNNs trained for spatial localization by path integration develop grid-, border- and band-like units, suggesting grid codes as a natural solution for spatial memory. | [[arXiv]](https://arxiv.org/abs/1803.07770) |
| Neural Map | 2017 | Structured memory for deep RL: a spatially indexed 2D memory written at the agent's current location and read by context-based attention, for partially observable 3D navigation. | [[arXiv]](https://arxiv.org/abs/1702.08360) |
| Cognitive Mapping and Planning | 2017 | A differentiable mapper accumulates an egocentric top-down belief map from first-person views, and a differentiable planner uses it; trained end-to-end for visual navigation. | [[arXiv]](https://arxiv.org/abs/1702.03920) |

### Spatial Memory Benchmarks

> Benchmarks that require remembering space: lifelong and multi-goal navigation, episodic-memory EQA, long-video spatial recall, and memory-dependent manipulation. FindingDory and Memento (embodied) are listed under [Benchmarks & Evaluation](#-benchmarks--evaluation).

| Benchmark | Year | Memory ability tested | Scale / Environment | Links |
|-----------|------|-----------------------|---------------------|-------|
| **EmbodiedMemory-Bench** | 2026 | Embodied memory in long-horizon tasks: visual retention, dynamic world-state tracking, failed-interaction recall, experience generalization | 2,554 episodes, 1,118 scenes; AI2-THOR + ProcTHOR | [[arXiv]](https://arxiv.org/abs/2609.28236) [[Website]](https://zju-omniai.github.io/EmbodiedMemoryBench/) |
| **EvoNav-Bench** | 2026 | Lifelong navigation when the environment changes between subtasks; whether agents reuse and correctly update stale scene memory | Evolving ProcTHOR scenes | [[arXiv]](https://arxiv.org/abs/2609.08292) |
| **MEMOBench** | 2026 | Process-level memory for VLA manipulation with separate storage, update and compression metrics | 30 tasks, 1,500 demos, 4,200 checkpoint instances | [[arXiv]](https://arxiv.org/abs/2609.07047) [[GitHub]](https://github.com/Collab-Gen/MEMOBench) |
| **GST-Bench** | 2026 | Whether VLMs form globally consistent spatial maps from long egocentric video: self-localization, out-of-view object localization, layout | 2,762 questions, 50 indoor scenes | [[arXiv]](https://arxiv.org/abs/2608.05747) [[Website]](https://qwerirwq.github.io/GST-Bench/) |
| **RoboMME-Interference** | 2026 | Multi-session robot memory under interference; retention as unrelated distractor sessions accumulate | Built on RoboMME | [[arXiv]](https://arxiv.org/abs/2606.22338) [[Website]](https://robotmemorybench.com) |
| **LongSpace-Bench** | 2026 | Long-horizon spatial memory in room-tour videos, from scene perception through spatial relations to delayed recall | Room-tour videos | [[arXiv]](https://arxiv.org/abs/2606.05677) |
| **OVO-S-Bench** | 2026 | Streaming spatial intelligence: tracking objects after they leave view, spatial reasoning, bird's-eye map construction | 1,680 questions, 348 videos, 30 task types | [[arXiv]](https://arxiv.org/abs/2606.03890) [[Website]](https://internlm.github.io/OVO-S-Bench/) |
| **RoboMME** | 2026 | Memory for VLA generalist policies along temporal, spatial, object and procedural dimensions | 16 manipulation tasks | [[arXiv]](https://arxiv.org/abs/2603.04639) [[Website]](https://robomme.github.io) |
| **RMBench** | 2026 | Memory-dependent dual-arm manipulation graded by task memory complexity | 9 tasks; RoboTwin 2.0 sim | [[arXiv]](https://arxiv.org/abs/2603.01229) [[GitHub]](https://github.com/robotwin-Platform/rmbench) |
| **LMEE-Bench** | 2026 | Long-term-memory embodied exploration: multi-goal navigation plus memory-based QA, scoring process and outcome | Simulated indoor scenes | [[arXiv]](https://arxiv.org/abs/2601.10744) [[Website]](https://wangsen99.github.io/papers/lmee/) |
| **StreamEQA** | 2025 | Streaming video QA in embodied scenarios: backward (memory), real-time and forward reasoning | 156 long videos, ~21,000 timestamped QA pairs | [[arXiv]](https://arxiv.org/abs/2512.04451) |
| **LIBERO-Mem** | 2025 | Non-Markovian manipulation under object-level partial observability with temporally sequenced subgoals | LIBERO sim | [[arXiv]](https://arxiv.org/abs/2511.11478) |
| **VSI-SUPER** | 2025 | Spatial supersensing in arbitrarily long video: long-horizon spatial recall and continual counting (from Cambrian-S) | Two-part benchmark; VSI-590K training set | [[arXiv]](https://arxiv.org/abs/2511.04670) [[Website]](https://cambrian-mllm.github.io/) |
| **LA-EQA** | 2025 | Long-term active EQA: answer temporally grounded questions by combining recall of past episodes with new exploration (from Mind Palace) | Days-to-months horizons; sim + real sites | [[arXiv]](https://arxiv.org/abs/2507.12846) |
| **OST-Bench** | 2025 | Online spatio-temporal understanding while an agent explores; accuracy as memory load grows | 1.4K scenes, 10K QA pairs | [[arXiv]](https://arxiv.org/abs/2507.07984) [[Website]](https://rbler1234.github.io/OSTBench.github.io/) |
| **MMSI-Bench** | 2025 | Multi-image spatial intelligence requiring cross-view integration of camera, object and region relations | 1,000 questions from 120,000+ images | [[arXiv]](https://arxiv.org/abs/2505.23764) [[Website]](https://runsenxu.com/projects/MMSI_Bench) |
| **∞-THOR** | 2025 | QA and tasks over unlimited-length synthetic trajectories requiring recall across hundreds of steps | AI2-THOR trajectory generator | [[arXiv]](https://arxiv.org/abs/2505.16928) |
| **MT-HM3D** | 2025 | Multi-target EQA requiring memory of information gathered across several regions (from Memory-Centric EQA) | 1,587 QA pairs; HM3D | [[arXiv]](https://arxiv.org/abs/2505.13948) |
| **MIKASA-Robo** | 2025 | Memory-intensive RL: a taxonomy of memory tasks plus a tabletop manipulation suite needing object, spatial and sequential memory | 32 manipulation tasks | [[arXiv]](https://arxiv.org/abs/2502.10550) |
| **MemoryBench (SAM2Act)** | 2025 | Spatial memory in manipulation: recalling earlier object or location states that are no longer visible | Built on RLBench | [[arXiv]](https://arxiv.org/abs/2501.18564) [[Website]](https://sam2act.github.io) |
| **VSI-Bench** | 2024 | Whether MLLMs see, remember and recall spaces from egocentric video: distances, sizes, counts, layouts, cognitive maps | 5,000+ QA pairs; real indoor scans | [[arXiv]](https://arxiv.org/abs/2412.14171) [[Website]](https://vision-x-nyu.github.io/thinking-in-space.github.io/) |
| **LHPR-VLN** | 2024 | Long-horizon multi-stage VLN with pick-and-place subtasks; retention of context across consecutive subtasks | 3,260 tasks, 150 steps on average | [[arXiv]](https://arxiv.org/abs/2412.09082) |
| **HourVideo** | 2024 | Hour-long egocentric video understanding including spatial and navigation-style reasoning | 500 videos, 12,976 questions | [[arXiv]](https://arxiv.org/abs/2411.04998) [[Website]](https://hourvideo.stanford.edu) |
| **NaVQA** | 2024 | Spatial, temporal and descriptive questions over long robot navigation videos (from ReMEmbR) | 210 examples, up to 20 min | [[arXiv]](https://arxiv.org/abs/2409.13682) [[GitHub]](https://github.com/NVIDIA-AI-IOT/remembr) |
| **HM3D-OVON** | 2024 | Open-vocabulary ObjectNav; exploration and semantic scene memory for free-form goal categories | 15K+ object instances, 379 categories | [[arXiv]](https://arxiv.org/abs/2409.14296) [[Website]](https://naoki.io/ovon) |
| **SIF** | 2024 | Situated Instruction Following: instructions whose meaning depends on the human's moving location and past actions | Habitat household sim | [[arXiv]](https://arxiv.org/abs/2407.12061) [[GitHub]](https://github.com/soyeonm/SIF_github) |
| **GOAT-Bench** | 2024 | Lifelong multi-goal navigation; reuse memory of earlier sub-episodes to reach category, language and image goals | 5–10 sequential goals per episode; HM3D | [[arXiv]](https://arxiv.org/abs/2404.06609) [[GitHub]](https://github.com/Ram81/goat-bench) |
| **HM-EQA** | 2024 | Active EQA: explore an unseen home, build a semantic map, and stop to answer once confident (from Explore-EQA) | HM3D sim | [[arXiv]](https://arxiv.org/abs/2403.15941) [[Website]](https://explore-eqa.github.io/) |
| **OpenEQA** | 2024 | Episodic-memory EQA (answer from a recorded tour) plus active-exploration EQA | 1,600+ questions, 180+ real environments | [[Paper]](https://open-eqa.github.io/assets/pdfs/paper.pdf) [[GitHub]](https://github.com/facebookresearch/open-eqa) |
| **EXCALIBUR** | 2023 | Long free-form exploration followed by physical-world queries; agents may re-enter the scene to refine knowledge | Interactive simulated homes | [[CVPR]](https://openaccess.thecvf.com/content/CVPR2023/html/Zhu_EXCALIBUR_Encouraging_and_Evaluating_Embodied_Exploration_CVPR_2023_paper.html) |
| **EgoSchema** | 2023 | Very long-form egocentric video QA; diagnostic for long-range video memory | 5,000+ QA, 250+ h | [[arXiv]](https://arxiv.org/abs/2308.09126) [[Website]](http://egoschema.github.io) |
| **HomeRobot OVMM** | 2023 | Open-vocabulary mobile manipulation in multi-room homes: find, pick and place on a remembered receptacle | Sim + real Stretch robot | [[arXiv]](https://arxiv.org/abs/2306.11565) [[Website]](https://ovmm.github.io/) |
| **InstanceImageNav** | 2022 | Navigate to a specific object instance shown in a goal image; instance-level recall and re-identification | HM3D sim | [[arXiv]](https://arxiv.org/abs/2211.15876) |
| **Long-HOT** | 2022 | Long-horizon object transport: explore, find, pick and carry objects, needing spatial memory of object locations | Habitat sim | [[arXiv]](https://arxiv.org/abs/2210.15908) |
| **Memory Maze** | 2022 | Long-term memory of RL agents in randomized 3D mazes; online RL, offline dataset and probing evaluation | Small to large mazes | [[arXiv]](https://arxiv.org/abs/2210.13383) |
| **Ego4D Episodic Memory** | 2021 | "Where did I leave X?" retrieval from past egocentric video by language or visual query (NLQ / VQ2D / VQ3D) | 3,670 h parent dataset | [[arXiv]](https://arxiv.org/abs/2110.07058) [[Website]](https://ego4d-data.org/) |
| **SOON** | 2021 | Scenario-oriented object navigation from any start to a richly described target | Matterport3D | [[arXiv]](https://arxiv.org/abs/2103.17138) |
| **MultiON** | 2020 | Multi-object navigation to an ordered sequence of objects; designed to probe map and memory use | Habitat sim | [[arXiv]](https://arxiv.org/abs/2012.03912) |
| **RxR** | 2020 | Multilingual VLN with longer, more varied paths; stresses long-trajectory history | English/Hindi/Telugu; Matterport3D | [[arXiv]](https://arxiv.org/abs/2010.07954) |
| **Habitat ObjectNav** | 2020 | Canonical ObjectGoal navigation task and evaluation protocol ("ObjectNav Revisited") | Habitat sim | [[arXiv]](https://arxiv.org/abs/2006.13171) |
| **VLN-CE** | 2020 | VLN in continuous environments with low-level actions and no nav-graph, so agents must build their own spatial memory | Habitat + Matterport3D | [[arXiv]](https://arxiv.org/abs/2004.02857) |
| **REVERIE** | 2019 | Remote embodied referring expressions: navigate from a high-level instruction, then localize the target object | Matterport3D | [[arXiv]](https://arxiv.org/abs/1904.10151) |
| **R2R** | 2017 | Room-to-Room vision-and-language navigation in real buildings | Matterport3D | [[arXiv]](https://arxiv.org/abs/1711.07280) |

### Spatial Memory Datasets

> Scene, trajectory and egocentric datasets used to build and evaluate spatial memory, including multi-session and changing-scene data for long-term operation.

| Dataset | Year | Contents | Scale | Links |
|---------|------|----------|-------|-------|
| **EgoNav data** | 2026 | Human walking data used to train a diffusion navigation policy deployed zero-shot on a humanoid | 5 h human walking | [[arXiv]](https://arxiv.org/abs/2604.00416) [[Website]](https://egonav.weizhuowang.com) |
| **EgoWalk** | 2025 | Human egocentric navigation data across indoor/outdoor settings and seasons, prepared for imitation learning | 50 h | [[arXiv]](https://arxiv.org/abs/2505.21282) |
| **TartanGround** | 2025 | Simulated ground-robot data (wheeled and legged) with 360° RGB-D, LiDAR and semantic occupancy | 70+ environments, 910 trajectories | [[arXiv]](https://arxiv.org/abs/2505.10696) |
| **EgoLife** | 2025 | Week-long multi-person, multi-view egocentric recordings in a shared house | 300 h, 6 participants | [[arXiv]](https://arxiv.org/abs/2503.03803) |
| **CityWalker data** | 2024 | Web-scale city walking and driving videos with extracted action labels for urban navigation | Thousands of hours | [[arXiv]](https://arxiv.org/abs/2411.17820) [[Website]](https://ai4ce.github.io/CityWalker/) |
| **LeLaN** | 2024 | Language-labeled, action-free in-the-wild video for language-conditioned object navigation | 130+ h | [[arXiv]](https://arxiv.org/abs/2410.03603) [[Website]](https://learning-language-navigation.github.io/) |
| **GND** | 2024 | Global Navigation Dataset: multi-campus outdoor navigation with LiDAR, RGB and 360° images plus traversability maps | 10 campuses, ~2.7 km² | [[arXiv]](https://arxiv.org/abs/2409.14262) |
| **GRScenes** | 2024 | Interactive annotated scenes across homes, shops and offices for city-scale embodied simulation (from GRUtopia) | 100K scenes | [[arXiv]](https://arxiv.org/abs/2407.10943) [[GitHub]](https://github.com/OpenRobotLab/GRUtopia) |
| **Nymeria** | 2024 | In-the-wild egocentric daily motion with full-body mocap, Aria sensors and narration in a shared 3D frame | 300 h, 264 participants, 399 km | [[arXiv]](https://arxiv.org/abs/2406.09905) [[Website]](https://www.projectaria.com/datasets/nymeria) |
| **MMScan** | 2024 | Hierarchical grounded language (object, region, spatial relations) on real 3D scans | 1.4M captions, 109K objects | [[arXiv]](https://arxiv.org/abs/2406.09401) |
| **RoboCasa** | 2024 | Large-scale kitchen simulation with generated assets and demonstrations for mobile manipulators | 100 tasks | [[arXiv]](https://arxiv.org/abs/2406.02523) [[Website]](https://robocasa.ai/) |
| **BEHAVIOR-1K** | 2024 | Human-centered household activity definitions with interactive scenes and annotated objects | 1,000 activities, 50 scenes, 9,000+ objects | [[arXiv]](https://arxiv.org/abs/2403.09227) [[Website]](https://behavior.stanford.edu) |
| **Aria Everyday Activities** | 2024 | Aria egocentric multi-sensor recordings with trajectories, point clouds, gaze and speech | Multi-location daily activities | [[arXiv]](https://arxiv.org/abs/2402.13349) [[Website]](https://www.projectaria.com/datasets/aea/) |
| **SceneVerse** | 2024 | Million-scale 3D vision-language pairs across real and synthetic indoor scenes | 68K scenes, 2.5M pairs | [[arXiv]](https://arxiv.org/abs/2401.09340) [[Website]](https://scene-verse.github.io) |
| **EmbodiedScan** | 2023 | Ego-centric multi-view RGB-D with oriented 3D boxes, occupancy and spatial language | 5,000+ scans, ~1M RGB-D images | [[arXiv]](https://arxiv.org/abs/2312.16170) [[Website]](http://tai-wang.github.io/embodiedscan) |
| **Ego-Exo4D** | 2023 | Time-synchronized ego and exo video of skilled activities with poses, point clouds and gaze | 1,286 h, 740 participants | [[arXiv]](https://arxiv.org/abs/2311.18259) [[Website]](http://ego-exo4d-data.org/) |
| **Open X-Embodiment** | 2023 | Pooled cross-embodiment robot learning datasets, with navigation and mobile subsets | 22 robots, 527 skills | [[arXiv]](https://arxiv.org/abs/2310.08864) [[Website]](https://robotics-transformer-x.github.io) |
| **CODa** | 2023 | Campus-scale egocentric robot perception data with 3D boxes and semantics across weather and time of day | 8.5 h, 1.3M 3D boxes | [[arXiv]](https://arxiv.org/abs/2309.13549) [[Website]](https://amrl.cs.utexas.edu/coda) |
| **ScanNet++** | 2023 | Sub-millimeter laser scans paired with DSLR and iPhone RGB-D, with semantics | 460 scenes | [[arXiv]](https://arxiv.org/abs/2308.11417) [[Website]](https://cy94.github.io/scannetpp/) |
| **ScaleVLN** | 2023 | Large-scale augmented VLN instruction-trajectory pairs | 4.9M pairs, 1,200+ environments | [[arXiv]](https://arxiv.org/abs/2307.15644) |
| **HSSD-200** | 2023 | Human-authored synthetic houses with real-world object models for ObjectNav training | 211 scenes, 18,656 object models | [[arXiv]](https://arxiv.org/abs/2306.11290) |
| **Aria Digital Twin** | 2023 | Aria-glasses sequences in fully digitized rooms with ground-truth object poses, gaze and human pose | 200 sequences, 398 object instances | [[arXiv]](https://arxiv.org/abs/2306.06362) |
| **HuRoN** | 2023 | Indoor autonomous navigation data with rich human-robot interactions for social navigation (from SACSoN) | Large-scale indoor | [[arXiv]](https://arxiv.org/abs/2306.01874) |
| **MuSoHu** | 2023 | Human-worn egocentric multi-sensor social navigation data in public spaces | ~100 km, 20 h | [[arXiv]](https://arxiv.org/abs/2303.14880) |
| **LaMAR** | 2022 | Multi-device AR trajectories co-registered to laser scans in large changing scenes | Multi-building, multi-session | [[arXiv]](https://arxiv.org/abs/2210.10770) [[Website]](https://lamar.ethz.ch/) |
| **SQA3D** | 2022 | Situated QA: the agent is given a position and orientation in a 3D scene, then asked reasoning questions | 650 scenes, 33.4K questions | [[arXiv]](https://arxiv.org/abs/2210.07474) [[Website]](https://sqa3d.github.io) |
| **HM3D-Semantics** | 2022 | Dense object instance annotations on HM3D scenes; basis for ObjectNav, OVON and GOAT | 142,646 instances, 216 spaces | [[arXiv]](https://arxiv.org/abs/2210.05633) |
| **GNM dataset mix** | 2022 | Aggregated heterogeneous visual navigation trajectories across robots | 60 h, 6 robots | [[arXiv]](https://arxiv.org/abs/2210.03370) [[Website]](https://sites.google.com/view/drive-any-robot) |
| **HM3D-AutoVLN** | 2022 | Automatically generated VLN data from unlabeled HM3D buildings | 900 buildings | [[arXiv]](https://arxiv.org/abs/2208.11781) |
| **ProcTHOR-10K** | 2022 | Procedurally generated interactive houses for large-scale embodied training | 10,000 houses | [[arXiv]](https://arxiv.org/abs/2206.06994) [[Website]](https://procthor.allenai.org) |
| **SCAND** | 2022 | Teleoperated, socially compliant navigation demonstrations on two robots | 8.7 h, 138 trajectories, 25 miles | [[arXiv]](https://arxiv.org/abs/2203.15041) |
| **Boreas** | 2022 | Multi-season repeated-route driving with LiDAR, radar, camera and cm-accurate poses | 350+ km over one year | [[arXiv]](https://arxiv.org/abs/2203.10168) [[Website]](https://www.boreas.utias.utoronto.ca) |
| **ScanQA** | 2021 | Free-form 3D question answering grounded in ScanNet scenes | 40K+ QA pairs, 800 scenes | [[arXiv]](https://arxiv.org/abs/2112.10482) |
| **ARKitScenes** | 2021 | Mobile LiDAR RGB-D indoor captures with laser-scanner depth and 3D oriented boxes | Large-scale indoor | [[arXiv]](https://arxiv.org/abs/2111.08897) |
| **Ego4D** | 2021 | Daily-life egocentric video with audio, 3D scans, gaze and episodic-memory annotations | 3,670 h, 931 wearers | [[arXiv]](https://arxiv.org/abs/2110.07058) [[Website]](https://ego4d-data.org/) |
| **HM3D** | 2021 | Largest set of real building-scale 3D reconstructions for embodied AI simulation in Habitat | 1,000 scenes | [[arXiv]](https://arxiv.org/abs/2109.08238) |
| **RECON** | 2021 | Open-world outdoor exploration trajectories used to learn latent goal models with topological memory | Outdoor, multi-environment | [[arXiv]](https://arxiv.org/abs/2104.05859) [[Website]](https://sites.google.com/view/recon-robot) |
| **4Seasons** | 2020 | Cross-season multi-weather stereo-inertial data for visual odometry, place recognition and relocalization | 350+ km | [[arXiv]](https://arxiv.org/abs/2009.06364) [[Website]](https://go.vision.in.tum.de/4seasons) |
| **TartanAir** | 2020 | Photorealistic simulated multi-modal SLAM data with varied lighting, weather and dynamics | Simulated, multi-environment | [[arXiv]](https://arxiv.org/abs/2003.14338) [[Website]](http://theairlab.org/tartanair-dataset) |
| **3RScan** | 2019 | Repeated RGB-D scans of the same rooms over time with object-instance changes; core data for changing-scene memory | 1,482 scans of 478 environments | [[arXiv]](https://arxiv.org/abs/1908.06109) |
| **Replica** | 2019 | Very high-fidelity indoor reconstructions with dense meshes, HDR textures and semantics | 18 scenes | [[arXiv]](https://arxiv.org/abs/1906.05797) |
| **Gibson** | 2018 | Virtualized real buildings with perception-realistic rendering for embodied agents | 572 buildings | [[arXiv]](https://arxiv.org/abs/1808.10654) [[Website]](http://gibsonenv.vision/) |
| **GoStanford** | 2018 | Fisheye-camera indoor robot video for traversability estimation (from GONet) | ~24 h, 25+ environments | [[arXiv]](https://arxiv.org/abs/1803.03254) |
| **AI2-THOR** | 2017 | Interactive near-photorealistic indoor simulator with object state changes | Interactive indoor scenes | [[arXiv]](https://arxiv.org/abs/1712.05474) [[Website]](http://ai2thor.allenai.org) |
| **Matterport3D** | 2017 | Building-scale RGB-D panoramas with meshes and semantics; substrate for R2R, REVERIE and many EQA benchmarks | 90 buildings, 10,800 panoramas | [[arXiv]](https://arxiv.org/abs/1709.06158) |
| **Oxford RobotCar** | 2017 | Repeated traversals of one urban route across weather, season and construction changes | 100+ traversals, 1,000 km | [[Website]](https://robotcar-dataset.robots.ox.ac.uk/) |
| **ScanNet** | 2017 | RGB-D video of indoor scenes with camera poses, reconstructions and semantic segmentation | 1,513 scenes, 2.5M views | [[arXiv]](https://arxiv.org/abs/1702.04405) [[Website]](http://www.scan-net.org) |
| **NCLT** | 2016 | Long-term multi-session campus dataset (LiDAR, omnidirectional vision, GPS) across seasons | 27 sessions, 15 months, 147.4 km | [[Website]](https://robots.engin.umich.edu/nclt/) |

---

## 📊 Benchmarks & Evaluation

### Memory Evaluation Benchmarks

| Benchmark | Year | Focus | Context Length | Links |
|-----------|------|-------|----------------|-------|
| **DyadMem** | 2026 | User-conditioned relational memory: how agents remember ways of working with specific users | 3,065 episodes, 50,961 sessions, 61,210 QA | [[arXiv]](https://arxiv.org/abs/2610.03020) |
| **APM-Bench** | 2026 | Cross-session persistent memory for egocentric streaming video assistants; utility–latency–storage trade-off | 549 video sessions, 104 trajectories | [[arXiv]](https://arxiv.org/abs/2609.37559) |
| **Correlated Promotion Benchmark** | 2026 | Epistemic admission: which claims should be admitted into shared multi-agent memory | 8 admission policies, 4 agent families | [[arXiv]](https://arxiv.org/abs/2609.30813) |
| **MemCalib** | 2026 | Whether agents calibrate how much memory should influence responses (over-use vs under-use) | 15,000 examples | [[arXiv]](https://arxiv.org/abs/2609.24259) |
| **VibeMemBench** | 2026 | Memory systems for coding agents on real repository tasks | 111 tasks, 90 repos, 3,634 historical trajectories | [[arXiv]](https://arxiv.org/abs/2609.23570) |
| **EgoMonth** | 2026 | Month-level egocentric video for long-term spatiotemporal memory in MLLMs | 300+ hours, 20 participants, 1,443 QA | [[arXiv]](https://arxiv.org/abs/2608.13113) |
| **AgentMemBench** | 2026 | Compares five memory management strategies (windowing, key-value, graph, summarization, web-augmented) on multi-session dialogue | 3 datasets | [[arXiv]](https://arxiv.org/abs/2608.00009) |
| **MemSecBench** | 2026 | Memory poisoning lifecycle: persistence, execution consequence and repair across memory backends | 310 test cases | [[arXiv]](https://arxiv.org/abs/2607.27080) |
| **RECON (Memory Reasoning)** | 2026 | Compositional reasoning over memory: evidence chains and cascade propagation | 1,604 questions; 24 case files of 50K–100K tokens | [[arXiv]](https://arxiv.org/abs/2607.16716) |
| **AgenticSTS** | 2026 | Bounded-memory testbed for long-horizon agents in Slay the Spire 2 | 298 trajectories | [[arXiv]](https://arxiv.org/abs/2607.02255) |
| **AFTER** | 2026 | Procedural-memory management: skill transfer across tasks, roles and models in workplace settings | 382 tasks, 6 roles, 22 skills | [[arXiv]](https://arxiv.org/abs/2606.23127) [[HuggingFace]](https://huggingface.co/datasets/DavydenkoGr/AFTER) |
| **M3Exam** | 2026 | Multimodal conversational memory in realistic user-agent interactions | Various | [[arXiv]](https://arxiv.org/abs/2606.07402) |
| **AgentCL** | 2026 | Continual learning in language agents using naive vs compositional task streams (coding, research, reasoning) | Various | [[arXiv]](https://arxiv.org/abs/2606.02461) |
| **EGOSTREAM** | 2026 | Diagnostic streaming episodic memory in egocentric vision across seven cognitive dimensions | 2,250 questions | [[arXiv]](https://arxiv.org/abs/2605.31557) [[Website]](https://saroo25.github.io/Egostream/) |
| **EvoMemBench** | 2026 | Self-evolving memory: in-episode vs cross-episode, knowledge- vs execution-oriented; 15 methods compared | Various | [[arXiv]](https://arxiv.org/abs/2605.18421) [[GitHub]](https://github.com/DSAIL-Memory/EvoMemBench) |
| **GroupMemBench** | 2026 | Agent memory in multi-party / group conversations | Various | [[arXiv]](https://arxiv.org/abs/2605.14498) |
| **LongMemEval-V2** | 2026 | Long-term memory for web and enterprise agents across five memory abilities | 451 questions; up to 500 trajectories / 115M tokens | [[arXiv]](https://arxiv.org/abs/2605.12493) [[GitHub]](https://github.com/xiaowu0162/LongMemEval-V2) |
| **EgoMemReason** | 2026 | Entity, event and behavior memory reasoning over week-long egocentric video | 500 questions; 25.9 h average backtracking | [[arXiv]](https://arxiv.org/abs/2605.09874) [[Website]](https://egomemreason.github.io/) |
| **Memora** | 2026 | Remembering, reasoning and recommending over weeks-to-months conversations; forgetting-aware accuracy metric | Various | [[arXiv]](https://arxiv.org/abs/2604.20006) |
| **MemoryCD** | 2026 | Lifelong cross-domain user memory from real Amazon review histories | 12 domains, 4 tasks | [[arXiv]](https://arxiv.org/abs/2603.25973) |
| **ATM-Bench** | 2026 | Long-term personalized referential memory QA over multimodal personal data | ~4 years of personal memory data | [[arXiv]](https://arxiv.org/abs/2603.01990) [[GitHub]](https://github.com/JingbiaoMei/ATM-Bench) |
| **MemoryArena** | 2026 | Memory across interdependent multi-session agentic tasks (shopping, travel planning, search, formal reasoning) | Multi-session task suites | [[arXiv]](https://arxiv.org/abs/2602.16313) [[Website]](https://memoryarena.github.io/) |
| **StructMemEval** | 2026 | Whether agents organize memory into structures (ledgers, to-do lists), not just recall | Various | [[arXiv]](https://arxiv.org/abs/2602.11243) |
| **LoCoMo-Plus** | 2026 | Beyond-factual "cognitive" memory: latent constraints and implicit user state in long dialogue | Various | [[arXiv]](https://arxiv.org/abs/2602.10715) [[GitHub]](https://github.com/xjtuleeyf/Locomo-Plus) |
| **SWE-ContextBench** | 2026 | Experience reuse in coding agents across related GitHub issues and pull requests | 1,100 base + 376 related tasks, 51 repos | [[arXiv]](https://arxiv.org/abs/2602.08316) |
| **CL-bench** | 2026 | Context learning: using new task-specific knowledge supplied in context | 500 contexts, 1,899 tasks | [[arXiv]](https://arxiv.org/abs/2602.03587) |
| **AgentLongBench** | 2026 | Long-context agents via environment rollouts; dynamic synthesis vs static retrieval | 32K–4M tokens | [[arXiv]](https://arxiv.org/abs/2601.20730) |
| **MemoryRewardBench** | 2026 | Whether reward models can judge long-term memory management quality | 8K–128K tokens | [[arXiv]](https://arxiv.org/abs/2601.11969) |
| **CloneMem** | 2026 | Long-term memory for AI clones from diaries, social posts and emails | 1–3 years of digital traces | [[arXiv]](https://arxiv.org/abs/2601.07023) [[GitHub]](https://github.com/AvatarMemory/CloneMemBench) |
| **RealMem** | 2026 | Long-term project-oriented cross-session interactions | 2,000+ cross-session dialogues, 11 scenarios | [[arXiv]](https://arxiv.org/abs/2601.06966) [[GitHub]](https://github.com/AvatarMemory/RealMemBench) |
| **KnowMe-Bench** | 2026 | Person understanding from autobiographical narratives: facts, subjective states, motivations | Various | [[arXiv]](https://arxiv.org/abs/2601.04745) [[GitHub]](https://github.com/QuantaAlpha/KnowMeBench) |
| **EvolMem** | 2026 | Cognitive-psychology-grounded multi-session memory: declarative and non-declarative dimensions | Various | [[arXiv]](https://arxiv.org/abs/2601.03543) [[GitHub]](https://github.com/shenye7436/EvolMem) |
| **Mem-Gallery** | 2026 | Multimodal long-term conversational memory for MLLM agents; 13 memory systems evaluated | Various | [[arXiv]](https://arxiv.org/abs/2601.03515) |
| **PERMA** | 2026 | Persona consistency over temporally ordered multi-session interactions | Various | [[arXiv]](https://arxiv.org/abs/2603.23231) [[GitHub]](https://github.com/PolarisLiu1/PERMA) |
| **AMA-Bench** | 2026 | Long-horizon memory for agentic applications with arbitrary-length trajectories | Various | [[arXiv]](https://arxiv.org/abs/2602.22769) |
| **EMemBench** | 2026 | Interactive benchmarking of episodic memory for VLM agents | Various | [[arXiv]](https://arxiv.org/abs/2601.16690) |
| **PersonaMem-v2** | 2025 | Implicit personalization from user-chatbot interactions | 1,000 interactions, 20,000+ preferences, 128K context | [[arXiv]](https://arxiv.org/abs/2512.06688) |
| **LoCoBench-Agent** | 2025 | Interactive long-context software-engineering agent benchmark | 8,000 scenarios; 10K–1M tokens | [[arXiv]](https://arxiv.org/abs/2511.13998) |
| **ConvoMem** | 2025 | Conversational memory at scale; when full context beats RAG | 75,336 QA pairs | [[arXiv]](https://arxiv.org/abs/2511.10523) |
| **BEAM** | 2025 | "Beyond a Million Tokens": long-term memory in very long conversations | 100 conversations, 2,000 questions, up to 10M tokens | [[arXiv]](https://arxiv.org/abs/2510.27246) |
| **TeleEgo** | 2025 | Streaming omni-modal egocentric assistant: memory, understanding, cross-memory reasoning | 14+ h per participant; 3,291 QA | [[arXiv]](https://arxiv.org/abs/2510.23981) |
| **MEMTRACK** | 2025 | Long-term memory and state tracking across Slack, Linear and Git enterprise environments | Various | [[arXiv]](https://arxiv.org/abs/2510.01353) |
| **M3-Bench** | 2025 | Long-video QA for multimodal agents with entity-centric episodic and semantic memory (from M3-Agent) | 1,020 videos | [[arXiv]](https://arxiv.org/abs/2508.09736) [[GitHub]](https://github.com/bytedance-seed/m3-agent) |
| **OdysseyBench** | 2025 | Long-horizon office-application workflows requiring long-term interaction history | 602 tasks | [[arXiv]](https://arxiv.org/abs/2508.09124) |
| **SWE-Bench-CL** | 2025 | Continual learning for coding agents on chronologically ordered GitHub issues | Various | [[arXiv]](https://arxiv.org/abs/2507.00014) [[GitHub]](https://github.com/thomasjoshi/agents-never-forget) |
| **StoryBench** | 2025 | Long-term memory via multi-turn interactive fiction games | Various | [[arXiv]](https://arxiv.org/abs/2506.13356) |
| **LifelongAgentBench** | 2025 | Agents as lifelong learners across Database, OS and Knowledge Graph environments | Various | [[arXiv]](https://arxiv.org/abs/2505.11942) [[Website]](https://caixd-220529.github.io/LifelongAgentBench/) |
| **PersonaMem** | 2025 | Dynamic user profiling and personalized responses as preferences evolve | 180+ simulated histories, 15 tasks | [[arXiv]](https://arxiv.org/abs/2504.14225) [[GitHub]](https://github.com/bowen-upenn/PersonaMem) |
| **MINJA** | 2025 | Memory injection attack on agents through query-only interaction (security) | Various | [[arXiv]](https://arxiv.org/abs/2503.03704) |
| **EgoLifeQA** | 2025 | Week-long egocentric life-assistant QA requiring long-term multimodal memory (from EgoLife) | 300 hours, 6 participants | [[arXiv]](https://arxiv.org/abs/2503.03803) [[HuggingFace]](https://huggingface.co/datasets/lmms-lab/EgoLife) |
| **MemoryCode** | 2025 | Tracking and applying coding instructions across multiple sessions amid distractors | Various | [[arXiv]](https://arxiv.org/abs/2502.13791) |
| **MEXTRA** | 2025 | Black-box extraction of private data from agent memory (privacy) | Various | [[arXiv]](https://arxiv.org/abs/2502.13172) |
| **MMRC** | 2025 | Multimodal real-world conversation memory and reasoning | 5,120 conversations, 28,720 questions | [[arXiv]](https://arxiv.org/abs/2502.11903) |
| **PrefEval** | 2025 | Inferring, remembering and following user preferences in long conversations | 3,000 preference–query pairs, 20 topics | [[arXiv]](https://arxiv.org/abs/2502.09597) [[Website]](https://prefeval.github.io/) |
| **Minerva** | 2025 | Programmable memory tests: search, recall, edit, match, compare, composite operations | Various | [[arXiv]](https://arxiv.org/abs/2502.03358) |
| **Episodic Memories Benchmark** | 2025 | Episodic recall of events grounded in time and space | 10K–100K token contexts | [[arXiv]](https://arxiv.org/abs/2501.13121) |
| **LOCCO** | 2025 | Long-term chronological conversations for evaluating LLM long-term memory | Various | [[ACL]](https://aclanthology.org/2025.findings-acl.1014/) |
| **Context-Bench** | 2025 | Agentic context engineering: chained file operations, entity tracing, multi-step retrieval | Various | [[Website]](https://www.letta.com/blog/context-bench/) [[Website]](https://leaderboard.letta.com) |
| **Evo-Memory** | 2025 | Self-evolving memory and test-time learning | Various | [[arXiv]](https://arxiv.org/abs/2511.20857) |
| **MemBench** | 2025 | Comprehensive memory evaluation (effectiveness, efficiency, capacity) | Various | [[arXiv]](https://arxiv.org/abs/2506.21605) |
| **FindingDory** | 2025 | Memory evaluation in embodied agents | Various | [[arXiv]](https://arxiv.org/abs/2506.15635) [[HuggingFace]](https://huggingface.co/yali30/findingdory-qwen2.5-VL-3B-finetuned) |
| **MemoryBench** | 2025 | Memory and continual learning | Various | [[arXiv]](https://arxiv.org/abs/2510.17281) |
| **MemoryAgentBench** | 2025 | Incremental multi-turn interactions | Various | [[arXiv]](https://arxiv.org/abs/2507.05257) |
| **Memento (Benchmark)** | 2025 | Personalized embodied assistance evaluation | Various | [[arXiv]](https://arxiv.org/abs/2505.16348) |
| **HaluMem** | 2025 | Operation-level hallucinations in agent memory systems (extraction, update, QA) | ~15K memory points, 3.5K questions; >1M-token contexts | [[arXiv]](https://arxiv.org/abs/2511.03506) [[GitHub]](https://github.com/MemTensor/HaluMem) |
| **LTM Benchmark** | 2024 | Dynamic conversational benchmark with interleaved tasks and context switching | Various | [[arXiv]](https://arxiv.org/abs/2409.20222) |
| **MemSim / MemDaily** | 2024 | Bayesian simulator generating reliable memory QA for personal assistants | Various | [[arXiv]](https://arxiv.org/abs/2409.20163) [[GitHub]](https://github.com/nuster1128/MemSim) |
| **AgentPoison** | 2024 | Backdoor attack poisoning agent memory or RAG knowledge bases (security) | 3 agent types | [[arXiv]](https://arxiv.org/abs/2407.12784) |
| **DialSim** | 2024 | Real-time long-term multi-party dialogue understanding built from TV shows | 1,300+ sessions; 352K+ tokens | [[arXiv]](https://arxiv.org/abs/2406.13144) |
| **StreamBench** | 2024 | Continuous improvement of agents from feedback streams after deployment | Various | [[arXiv]](https://arxiv.org/abs/2406.08747) [[GitHub]](https://github.com/stream-bench/stream-bench) |
| **PerLTQA** | 2024 | Personal long-term memory QA: memory classification, retrieval and synthesis | 8,593 questions, 30 characters | [[arXiv]](https://arxiv.org/abs/2402.16288) [[GitHub]](https://github.com/Elvin-Yiming-Du/PerLTQA) |
| **LoCoMo** | 2024 | Very long-term conversational memory | ~9K tokens, 35 sessions | [[arXiv]](https://arxiv.org/abs/2402.17753) [[Website]](https://snap-research.github.io/locomo/) |
| **LongMemEval** | 2024 | Long-term interactive memory | ~115K-1.5M tokens | [[arXiv]](https://arxiv.org/abs/2410.10813) [[GitHub]](https://github.com/xiaowu0162/LongMemEval) |
| **LongLaMP** | 2024 | Long-text language model personalization benchmark | Long contexts | [[arXiv]](https://arxiv.org/abs/2407.11016) [[GitHub]](https://github.com/LaMP-Benchmark/LongLaMP) |
| **LaMP** | 2023 | Language model personalization benchmark | Various | [[arXiv]](https://arxiv.org/abs/2304.11406) [[GitHub]](https://github.com/LaMP-Benchmark/LaMP) |

### Datasets

> Corpora used to build, train, and evaluate agent memory: multi-session dialogue, personal histories, egocentric video, and agent trajectories. Many benchmarks above also release their data; the entries here are the ones most often reused as training or evaluation material.

| Dataset | Year | Contents | Links |
|---------|------|----------|-------|
| **SWE-ZERO-12M-trajectories** | 2026 | 12.29M execution-free coding-agent rollouts (112B tokens) over 122,908 pull requests and 3,222 repositories, usable as experience data for agents | [[HuggingFace]](https://huggingface.co/datasets/AlienKevin/SWE-ZERO-12M-trajectories) |
| **TopicGuidedChat** | 2026 | Persona-grounded generated conversations with long-term memory as knowledge graphs and short-term memory as topic-guided chats (from AgenticAI-DialogGen) | [[arXiv]](https://arxiv.org/abs/2604.12179) |
| **Agent Data Protocol** | 2025 | Unified schema converting 13 existing agent trajectory datasets (coding, browsing, tool use, research) into one format for fine-tuning | [[arXiv]](https://arxiv.org/abs/2510.24702) |
| **HaluMem (Medium / Long)** | 2025 | ~15K memory points and 3.5K questions with operation-level hallucination labels; 1.5K–2.6K dialogue turns per user and contexts above 1M tokens | [[arXiv]](https://arxiv.org/abs/2511.03506) [[GitHub]](https://github.com/MemTensor/HaluMem) |
| **EgoLife** | 2025 | 300 hours of week-long multimodal egocentric recordings from six co-living participants | [[arXiv]](https://arxiv.org/abs/2503.03803) [[HuggingFace]](https://huggingface.co/datasets/lmms-lab/EgoLife) |
| **ImplexConv** | 2025 | 2,500 examples, each with ~100 conversation sessions, targeting implicit reasoning in personalized dialogue | [[arXiv]](https://arxiv.org/abs/2503.07018) |
| **REALTALK** | 2025 | 21-day corpus of authentic messaging-app conversations between real people; a non-synthetic counterpart to LoCoMo | [[arXiv]](https://arxiv.org/abs/2502.13270) [[GitHub]](https://github.com/danny911kr/REALTALK) |
| **SHARE** | 2024 | Long-term dialogues built from movie scripts with personas, events and shared memories between speakers | [[arXiv]](https://arxiv.org/abs/2410.20682) [[GitHub]](https://github.com/e1kim/SHARE) |
| **LongMemEval data** | 2024 | 500 questions; S variant ~40 sessions (~115K tokens) and M variant ~500 sessions per history | [[arXiv]](https://arxiv.org/abs/2410.10813) [[HuggingFace]](https://huggingface.co/datasets/xiaowu0162/longmemeval-cleaned) |
| **MemDaily** | 2024 | Automatically generated daily-life user messages with reliable QA pairs for testing personal-assistant memory (from MemSim) | [[arXiv]](https://arxiv.org/abs/2409.20163) [[GitHub]](https://github.com/nuster1128/MemSim) |
| **LongDialQA** | 2024 | Multi-party TV-show dialogue: 1,300+ sessions and 352K+ tokens (from DialSim) | [[arXiv]](https://arxiv.org/abs/2406.13144) |
| **LoCoMo data** | 2024 | Very long-term multi-session conversations; the public release contains 10 conversations | [[arXiv]](https://arxiv.org/abs/2402.17753) [[GitHub]](https://github.com/snap-research/locomo) |
| **PerLTQA** | 2024 | Personal long-term memory QA combining semantic and episodic memories; 8,593 questions for 30 characters | [[arXiv]](https://arxiv.org/abs/2402.16288) [[GitHub]](https://github.com/Elvin-Yiming-Du/PerLTQA) |
| **Conversation Chronicles** | 2023 | 200,000 five-session episodes (1M sessions) with time intervals and speaker relationships | [[arXiv]](https://arxiv.org/abs/2310.13420) [[HuggingFace]](https://huggingface.co/datasets/jihyoung/ConversationChronicles) |
| **LaMP data** | 2023 | Seven personalization tasks (citation, movie tagging, rating, headline, title, email subject, tweet paraphrase) with user- and time-based splits | [[arXiv]](https://arxiv.org/abs/2304.11406) [[Website]](https://lamp-benchmark.github.io/download) |
| **CareCall (memory)** | 2022 | Korean multi-session open-domain dialogues with memory updates across five sessions | [[arXiv]](https://arxiv.org/abs/2210.08750) [[GitHub]](https://github.com/naver-ai/carecall-memory) |
| **DuLeMon** | 2022 | Chinese open-domain dialogues with long-term persona memory for both user and bot | [[arXiv]](https://arxiv.org/abs/2203.05797) |
| **Ego4D** | 2021 | 3,670 hours of egocentric daily-life video from 931 wearers across 74 locations, including episodic-memory query tasks | [[arXiv]](https://arxiv.org/abs/2110.07058) [[Website]](https://ego4d-data.org/) |
| **Multi-Session Chat (MSC)** | 2021 | Human-human multi-session chats where partners recall earlier sessions, with session summaries | [[arXiv]](https://arxiv.org/abs/2107.07567) [[Website]](https://parl.ai/projects/msc/) |
| **PersonaChat** | 2018 | Persona-grounded chit-chat dialogues between crowdworkers conditioned on profiles; precursor to multi-session memory corpora | [[arXiv]](https://arxiv.org/abs/1801.07243) |

### Evaluation Metrics

| Metric | Description |
|--------|-------------|
| **F1 Score** | Token-level overlap between predicted and ground-truth answers |
| **BLEU** | N-gram lexical similarity |
| **LLM-as-a-Judge** | Semantic correctness evaluation via LLM |
| **Retrieval Accuracy** | Correctness of retrieved memories |
| **Memory Efficiency** | Storage and retrieval speed |
| **Token Cost** | Tokens spent constructing and reading memory per query |
| **Forgetting / Update Accuracy** | Whether stale facts are overwritten and superseded knowledge is no longer returned |
| **SR / SPL** | Success rate and success weighted by path length, for navigation with spatial memory |
| **Memory Footprint** | Map or memory size and peak runtime memory on the robot |

---

## 🛠️ Open-Source Frameworks

| Framework | Year | Description | Links |
|-----------|------|-------------|-------|
| **OpenViking** | 2026 | Self-evolving context database unifying agent memory, knowledge RAG and skills | [[GitHub]](https://github.com/volcengine/OpenViking) |
| **TencentDB Agent Memory** | 2026 | Team-level memory hub turning chats, docs and code into chat memory, skill, wiki and code-graph assets | [[GitHub]](https://github.com/TencentCloud/TencentDB-Agent-Memory) |
| **EverMemOS / EverOS** | 2026 | Self-organizing memory OS (MemCells, MemScenes); now a local-first, Markdown-native memory layer | [[GitHub]](https://github.com/EverMind-AI/EverOS) [[arXiv]](https://arxiv.org/abs/2601.02163) |
| **SimpleMem** | 2026 | Efficient lifelong memory via semantic structured compression and intent-aware retrieval | [[GitHub]](https://github.com/aiming-lab/SimpleMem) [[arXiv]](https://arxiv.org/abs/2601.02553) |
| **Hyperconsciousness** | 2026 | MIT-licensed developer-alpha Rust knowledge store for agents, with signed, encrypted, append-only records, device sync, and scoped, expiring grants through CLI/MCP/HTTP interfaces. Source build instructions and alpha release binaries are available. | [[GitHub]](https://github.com/louis030195/hyperconsciousness) |
| **LWC** | 2026 | Proactive, source-grounded project memory for coding agents with immutable sources, citations, provenance, SQLite/FTS5 retrieval, and optional document and code graphs | [[GitHub]](https://github.com/JanYork/llm-wiki-cli) [[Docs]](https://janyork.github.io/llm-wiki-cli/) |
| **TeleMem** | 2025 | Drop-in Mem0 replacement with semantic deduplication, long-term dialogue memory and multimodal video reasoning | [[GitHub]](https://github.com/TeleAI-UAGI/telemem) |
| **LightMem** | 2025 | Lightweight, efficient memory-augmented generation (ICLR 2026) | [[GitHub]](https://github.com/zjunlp/LightMem) [[arXiv]](https://arxiv.org/abs/2510.18866) |
| **Hindsight** | 2025 | Agent memory system for agents that learn over time (retain, recall, reflect) | [[GitHub]](https://github.com/vectorize-io/hindsight) [[arXiv]](https://arxiv.org/abs/2512.12818) |
| **MemMachine** | 2025 | Universal memory layer for agents: scalable, extensible, interoperable storage and retrieval | [[GitHub]](https://github.com/MemMachine/MemMachine) [[arXiv]](https://arxiv.org/abs/2604.04853) |
| **MemU** | 2025 | Lightweight agent-driven memory shared across sessions, agents and devices | [[GitHub]](https://github.com/NevaMind-AI/memU) |
| **claude-mem** | 2025 | Captures coding-agent sessions, compresses them with AI and injects relevant context into later sessions | [[GitHub]](https://github.com/thedotmack/claude-mem) |
| **Memori** | 2025 | LLM-agnostic, agent-native memory layer turning execution and conversation into structured persistent state | [[GitHub]](https://github.com/MemoriLabs/Memori) [[arXiv]](https://arxiv.org/abs/2603.19935) |
| **MemoryOS** | 2025 | Memory operating system for personalized agents with hierarchical storage, updating, retrieval and generation (EMNLP 2025) | [[GitHub]](https://github.com/BAI-LAB/MemoryOS) [[arXiv]](https://arxiv.org/abs/2506.06326) |
| **MIRIX** | 2025 | Multi-agent personal assistant that turns on-screen activity into structured multi-type memories | [[GitHub]](https://github.com/Mirix-AI/MIRIX) [[arXiv]](https://arxiv.org/abs/2507.07957) |
| **Second Me** | 2025 | Train a personal "AI self" on your own memories, built on AI-native memory | [[GitHub]](https://github.com/mindverse/Second-Me) [[arXiv]](https://arxiv.org/abs/2503.08102) |
| **OpenMemory** | 2025 | Local persistent memory store for LLM applications and coding assistants | [[GitHub]](https://github.com/CaviraOSS/OpenMemory) |
| **Basic Memory** | 2025 | Local-first persistent memory for AI conversations, stored as Markdown | [[GitHub]](https://github.com/basicmachines-co/basic-memory) |
| **Mem0** | 2025 | Production-ready memory for AI agents with graph-based storage | [[GitHub]](https://github.com/mem0ai/mem0) [[arXiv]](https://arxiv.org/abs/2504.19413) |
| **A-MEM** | 2025 | Agentic memory with Zettelkasten-inspired organization | [[GitHub]](https://github.com/agiresearch/A-mem) [[arXiv]](https://arxiv.org/abs/2502.12110) |
| **Zep/Graphiti** | 2025 | Temporal knowledge graph for agent memory | [[GitHub]](https://github.com/getzep/zep) [[Graphiti]](https://github.com/getzep/graphiti) [[arXiv]](https://arxiv.org/abs/2501.13956) |
| **Memory-R1** | 2025 | RL-based memory management for LLM agents | [[arXiv]](https://arxiv.org/abs/2508.19828) |
| **MemOS** | 2025 | Operating system for memory-augmented generation in LLMs | [[GitHub]](https://github.com/MemTensor/MemOS) [[arXiv]](https://arxiv.org/abs/2507.03724) |
| **PowerMem** | 2025 | Agent-powered long-term memory with Ebbinghaus forgetting curve | [[GitHub]](https://github.com/Teingi/PowerMem) |
| **Memobase** | 2024 | User-profile-based long-term memory for AI chatbot applications | [[GitHub]](https://github.com/memodb-io/memobase) |
| **Supermemory** | 2024 | Memory and context engine with a memory API; can run fully locally | [[GitHub]](https://github.com/supermemoryai/supermemory) |
| **Honcho** | 2024 | Memory infrastructure for stateful agents that model people, agents and groups over time | [[GitHub]](https://github.com/plastic-labs/honcho) |
| **HippoRAG** | 2024 | Neurobiologically inspired long-term memory with knowledge graphs | [[GitHub]](https://github.com/OSU-NLP-Group/HippoRAG) [[arXiv]](https://arxiv.org/abs/2405.14831) |
| **LangMem** | 2024 | Long-term memory for LangChain agents | [[Docs]](https://langchain-ai.github.io/langmem/) |
| **Cognee** | 2023 | AI memory platform providing persistent long-term memory via a knowledge-graph plus vector engine | [[GitHub]](https://github.com/topoteretes/cognee) [[arXiv]](https://arxiv.org/abs/2505.24478) |
| **MemGPT/Letta** | 2023 | LLMs as operating systems with hierarchical memory management; now the Letta platform for stateful agents | [[GitHub]](https://github.com/letta-ai/letta) [[arXiv]](https://arxiv.org/abs/2310.08560) |

---

## 🎮 Applications

Memory mechanisms are used across various LLM agent applications:

| Domain | Description | Key Papers |
|--------|-------------|------------|
| **🎭 Role-Playing** | Maintaining consistent character personas over extended interactions | Character-LLM, ChatHaruhi, RoleLLM, CharacterGLM, MOOM |
| **🌐 Social Simulation** | Simulating human social behaviors at scale | Generative Agents, OASIS, S³, Lyfe Agents, AgentVerse |
| **🤝 Personal Assistants** | Learning user preferences and providing personalized responses | MemoryBank, Mem0, A-MEM, AI PERSONA, Livia |
| **🎮 Open-World Games** | Accumulating skills and world knowledge for exploration | Voyager, GITM, JARVIS-1, Minecraft agents |
| **💻 Code Generation** | Iterative debugging and cross-project learning | ChatDev, MetaGPT, AutoGPT, Reflexion, RepairAgent |
| **📊 Recommendation** | Personalizing suggestions based on interaction history | RecMind, InteRecAgent, Recommender AI Agent |
| **🏥 Expert Systems** | Domain-specific knowledge management | HuaTuo, InvestLM, medical/legal agents |
| **🌐 Web Agents** | Navigating and automating web tasks | Agent S, SkillWeaver, UFO2, BrowserAgent |
| **🔬 Scientific Research** | Managing research context and hypotheses | JARVIS-1, Darwin Godel Machine |
| **🤖 Embodied Agents** | Persistent memory for physical world interaction | RT-1, RT-2, PaLM-E, SayCan, Mem2Ego, MemoryVLA, EchoVLA, PhysMem |
| **🧭 Mobile Robot Navigation** | Spatial memory for navigation, embodied QA and mobile manipulation | VLMaps, ConceptGraphs, HOV-SG, DynaMem, ReMEmbR, Embodied-RAG, GOAT, StreamVLN, NavFoM |
| **📹 Video Understanding** | Long-term video comprehension | MovieChat, XMem, Context as Memory |

---

## 🔮 Future Directions

Based on current research, future directions include:

| Direction | Description |
|-----------|-------------|
| **🤖 Memory Automation** | Reducing manual design through learned memory operations (Mem-α, Memory-R1) |
| **🎯 RL Integration** | Using reinforcement learning for memory optimization |
| **🖼️ Multimodal Memory** | Extending beyond text to images, audio, and video |
| **👥 Multi-Agent Memory** | Shared and distributed memory across agent teams (G-Memory, MAGMA, MemMA, CoMAM, Memory as Asset) |
| **🔒 Trustworthiness** | Privacy, security, and reliability of agent memories |
| **⚡ Efficiency** | Scalable long-term memory for extended operations |
| **🧪 Standardized Benchmarks** | Unified evaluation protocols (LoCoMo, LongMemEval-V2, MemoryArena, BEAM, MemoryBench, LaMP) |
| **🧠 Cognitive Inspiration** | Drawing from neuroscience (HippoRAG, episodic memory) |
| **🔄 Self-Evolution** | Agents that continuously improve their own memory systems |
| **🧰 Skills as Memory** | Reusable, evolvable skill libraries as procedural memory (SkillRL, EvoSkills, SkillOpt, HyperSkill) |
| **🗜️ Learned Context Management** | Training agents to compact, fold and recall their own context (Context-Folding, ACM, CompactionRL), without dropping constraints (Governance Decay) |
| **🛡️ Memory Security** | Defending persistent memory against poisoning and extraction (MemPoison, SPORE, A-MemGuard, MemSecBench) |
| **🧭 Lifelong Spatial Memory** | Maps and scene graphs that stay correct as the world changes across sessions (Khronos, DynaMem, LT-Mem, EvolvingNav, EvoNav-Bench) |
| **📦 Memory-Efficient Mapping** | Bounding on-robot memory footprint of open-vocabulary maps and visual-history tokens (HOV-SG, Clio, StreamVLN, AdaGeoVLN) |

---

## 📚 References

This repository synthesizes insights from the following surveys and papers:

**Surveys**

- [Memory in the Age of AI Agents: A Survey](https://arxiv.org/abs/2512.13564) (2025) [[GitHub]](https://github.com/Shichun-Liu/Agent-Memory-Paper-List)
- [Memory-Augmented Transformers: From Neuroscience Principles to Technical Solutions](https://arxiv.org/abs/2508.10824) (2025)
- [From S4 to Mamba: A Comprehensive Survey on Structured State Space Models](https://arxiv.org/abs/2503.18970) (2025)
- [From Human Memory to AI Memory: A Survey on Memory Mechanisms in the Era of LLMs](https://arxiv.org/abs/2504.15965) (2025)
- [Retrieval-Augmented Generation for Natural Language Processing: A Survey](https://arxiv.org/abs/2407.13193) (2025)
- [A Survey of Robotic Navigation and Manipulation with Physics Simulators in the Era of Embodied AI](https://arxiv.org/abs/2505.01458) (2025)
- [KV Cache Compression for Inference Efficiency in LLMs: A Survey](https://arxiv.org/abs/2412.19442) (2024)
- [A Comprehensive Survey of Continual Learning: Theory, Method and Application](https://arxiv.org/abs/2302.00487) (2024) [[GitHub]](https://github.com/Wang-ML-Lab/llm-continual-learning-survey)
- [Retrieval-Augmented Generation for Large Language Models: A Survey](https://arxiv.org/abs/2312.10997) (2024)
- [A Survey on the Memory Mechanism of Large Language Model based Agents](https://arxiv.org/abs/2404.13501) (2024) [[GitHub]](https://github.com/nuster1128/LLM_Agent_Memory_Survey)
- [Robot Learning in the Era of Foundation Models: A Survey](https://arxiv.org/abs/2311.14379) (2023)
- [Memory in LLM-based Multi-agent Systems: Mechanisms, Challenges, and Collective Intelligence](https://www.techrxiv.org/users/810975/articles/1267314-memory-in-LLM-based-multi-agent-systems-a-survey-on-mechanisms-challenges-and-collective-intelligence) (2025)
- [Memory for Autonomous LLM Agents: Mechanisms, Evaluation, and Emerging Frontiers](https://arxiv.org/abs/2603.07670) (2026)
- [Continual Learning in LLMs: Methods, Challenges, and Opportunities](https://arxiv.org/abs/2603.12658) (2026)
- [Graph-Based Personalized Memory for LLM Agents: Representation, Evolution, Retrieval, and Evaluation](https://arxiv.org/abs/2609.08599) (2026)
- [Memory for Large Language Models](https://arxiv.org/abs/2607.25380) (2026)
- [Dynamic Agent Skills: A Lifecycle Survey and Taxonomy of Evolving Skill Libraries](https://arxiv.org/abs/2607.10113) (2026)
- [Towards Efficient Large Language Model Serving: A Survey on System-Aware KV Cache Optimization](https://arxiv.org/abs/2607.08057) (2026)
- [From Storage to Experience: A Survey on the Evolution of LLM Agent Memory Mechanisms](https://arxiv.org/abs/2605.06716) (2026)
- [A Survey on Long-Term Memory Security in LLM Agents: Attacks, Defenses, and Governance Across the Memory Lifecycle](https://arxiv.org/abs/2604.16548) (2026)
- [Agent Skills for Large Language Models: Architecture, Acquisition, Security, and the Path Forward](https://arxiv.org/abs/2602.12430) (2026)
- [Rethinking Memory Mechanisms of Foundation Agents in the Second Half: A Survey](https://arxiv.org/abs/2602.06052) (2026)

**Spatial Memory Surveys**

- [A Survey of Spatial Memory Representations for Efficient Robot Navigation](https://arxiv.org/abs/2604.16482) (2026)
- [3D Scene Graphs: Open Challenges and Future Directions](https://arxiv.org/abs/2606.19383) (2026) [[Website]](https://3dscenegraphs.com/)
- [Semantic Mapping in Indoor Embodied AI: A Survey on Advances, Challenges, and Future Directions](https://arxiv.org/abs/2501.05750) (2025)

**Papers**

- [Continual Learning as Computationally Constrained Reinforcement Learning](https://arxiv.org/abs/2307.04345) (2023)

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
- Appropriate categorization by Form × Function (or by representation type for spatial memory)

---

<p align="center">
  <strong>⭐ Star this repo if you find it helpful!</strong>
</p>

<p align="center">
  Made with ❤️ for the Agent Research Community
</p>
