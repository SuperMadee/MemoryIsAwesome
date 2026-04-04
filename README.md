<h1 align="center">🧠 Memory is Awesome</h1>

<p align="center">
  <strong>Your Guide to Memory in Foundation Model Agents</strong>
</p>

<p align="center">
  <em>"Without memory, there is no culture. Without memory, there would be no civilization, no society, no future."</em><br/>
  — Elie Wiesel
</p>

<p align="center">
  <a href="#-paper-collection"><img src="https://img.shields.io/badge/Papers-360+-blue" alt="Papers"></a>
  <a href="#-benchmarks--evaluation"><img src="https://img.shields.io/badge/Benchmarks-13+-green" alt="Benchmarks"></a>
  <a href="#%EF%B8%8F-open-source-frameworks"><img src="https://img.shields.io/badge/Frameworks-9+-orange" alt="Frameworks"></a>
  <a href="#-references"><img src="https://img.shields.io/badge/References-15+-purple" alt="References"></a>
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

### 📊 Repository Highlights

This repository collects agent memory research, featuring:

- **350+ papers** spanning from foundational works (Neural Turing Machines, 2014) to recent research (March 2026)
- **Unified taxonomy** organizing research by Forms × Functions × Dynamics
- **11+ benchmarks** for evaluating memory capabilities (LoCoMo, LongMemEval, MemBench, LaMP, etc.)
- **9+ open-source frameworks** (Mem0, A-MEM, Zep, MemGPT, HippoRAG, etc.)
- **13+ references** including surveys synthesizing the field's evolution

### 🔬 Coverage Areas

| Category | Description | Key Topics |
|----------|-------------|------------|
| **🔤 Token-level Memory** | Explicit, discrete text/symbols | RAG (Self-RAG, CRAG, DPR), knowledge graphs, episodic stores, conversation history |
| **⚙️ Parametric Memory** | Knowledge encoded in weights | Model editing (ROME, MEMIT, SERAC), LoRA adapters, continual learning (EWC, iCaRL) |
| **🧬 Latent Memory** | Compressed hidden states | KV cache (StreamingLLM, SnapKV), state space models (Mamba, H3, Hyena, Griffin), memory tokens |
| **🤖 Multi-Agent Memory** | Shared knowledge across agents | G-Memory, collaborative memory, AgentVerse, AutoGen, memory-as-a-service |
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
| O-Mem | 2025 | Introduces a three-component memory framework (Persona Memory, Working Memory, Topical Memory) that dynamically extracts and updates user characteristics through active profiling, enabling hierarchical retrieval of persona attributes and topic-related context for adaptive personalized responses in long-horizon interactions. | [[arXiv]](https://arxiv.org/abs/2511.13593) |
| In Prospect and Retrospect | 2025 | Proposes a dual-phase memory management approach where agents prospectively anticipate future information needs while retrospectively reflecting on past interactions, enabling more coherent and personalized long-term dialogue through selective memory retention and retrieval. | [[ACL]](https://aclanthology.org/2025.acl-long.413/) |
| Memoro | 2025 | Presents a wearable audio-based memory assistant that uses LLMs to infer user memory needs in conversational context, featuring Query and Queryless interaction modes that reduce device interaction time by 85% while maintaining conversation quality in real-time social settings. | [[ACM]](https://doi.org/10.1145/3613904.3642450) |
| RCR-Router | 2025 | Addresses context management in multi-agent systems by routing relevant memory segments to appropriate agent roles, reducing redundant context processing while maintaining coherent inter-agent communication through structured memory organization. | [[arXiv]](https://arxiv.org/abs/2508.04903) |
| Livia | 2025 | Creates an augmented reality companion that combines emotion detection with progressive memory compression, allowing the AR agent to maintain long-term emotional context while adapting its responses to user affect states in real-time. | [[arXiv]](https://arxiv.org/abs/2509.05298) |
| D-SMART | 2025 | Combines a Dynamic Structured Memory (DSM) that incrementally builds an OWL-compliant knowledge graph with a Reasoning Tree (RT) for explicit multi-step inference, achieving 48% improvement in dialogue consistency by enabling traceable reasoning over evolving conversational context. | [[arXiv]](https://arxiv.org/abs/2510.13363) |
| WebWeaver | 2025 | Organizes web-scale information into dynamically evolving outline structures during research tasks, enabling LLMs to systematically gather, organize, and synthesize evidence across multiple sources for comprehensive open-ended inquiry. | [[arXiv]](https://arxiv.org/abs/2509.13312) |
| CAM | 2025 | Proposes a constructivist memory framework where agents actively construct understanding by integrating new information with existing knowledge structures, improving reading comprehension through schema-based memory organization rather than passive information storage. | [[arXiv]](https://arxiv.org/abs/2510.05520) |
| MovieChat | 2025 | Addresses long video understanding by converting dense frame-level tokens into sparse memory representations through a memory consolidation mechanism, enabling efficient processing of hour-long videos while preserving semantically important temporal information. | [[CVPR]](https://doi.org/10.1109/CVPR52733.2024.01725) |
| Pre-Storage Reasoning | 2025 | Pre-computes and stores reasoning chains about user information at memory write time rather than query time, reducing inference latency while maintaining personalization quality by front-loading computational work to the memory formation phase. | [[arXiv]](https://arxiv.org/abs/2509.10852) |
| LightMem | 2025 | Proposes a parameter-efficient memory augmentation approach that adds minimal computational overhead to base LLMs while enabling effective long-term information retention through compressed memory representations. | [[arXiv]](https://arxiv.org/abs/2510.18866) |
| Mem-α | 2025 | Uses reinforcement learning to train agents to construct optimal memory representations, learning when and what to store through interaction feedback rather than relying on hand-crafted memory formation heuristics. | [[arXiv]](https://arxiv.org/abs/2509.25911) |
| SGMem | 2025 | Structures conversational memory as sentence-level graphs where nodes represent utterances and edges capture semantic relationships, enabling more precise retrieval of relevant dialogue history for context-aware response generation. | [[arXiv]](https://arxiv.org/abs/2509.21212) |
| Nemori | 2025 | Implements self-organizing memory maps inspired by cognitive neuroscience, where memories automatically cluster and reorganize based on semantic similarity and usage patterns without explicit indexing. | [[arXiv]](https://arxiv.org/abs/2508.03341) |
| MOOM | 2025 | Addresses the unique challenges of maintaining character consistency in extended role-playing scenarios through specialized memory maintenance routines that preserve character traits, plot points, and relationship dynamics across hundreds of dialogue turns. | [[arXiv]](https://arxiv.org/abs/2509.11860) |
| Multiple Memory Systems | 2025 | Proposes a multi-system memory architecture inspired by human cognitive models, separating episodic, semantic, and procedural memories with distinct storage and retrieval mechanisms for improved long-term agent performance. | [[arXiv]](https://arxiv.org/abs/2508.15294) |
| Semantic Anchoring | 2025 | Uses linguistic dependency structures and semantic roles as anchors for organizing conversational memory, enabling more precise context retrieval by matching query semantics to stored discourse structures. | [[arXiv]](https://arxiv.org/abs/2508.12630) |
| Multi-Layered Memory | 2026 | Decomposes dialogue history into working, episodic, and semantic layers with adaptive retrieval gating and retention regularization, controlling cross-session drift while maintaining bounded context growth. | [[arXiv]](https://arxiv.org/abs/2603.29194) |
| Anatomy of Agentic Memory | 2026 | Taxonomy and empirical analysis of evaluation and system limitations for agentic memory, identifying gaps between current benchmarks and real-world agentic requirements. | [[arXiv]](https://arxiv.org/abs/2602.19320) |
| LRAgent | 2026 | KV cache sharing framework for multi-LoRA agents that decomposes cache into shared base and adapter-dependent components with Flash-LoRA-Attention kernel, reducing memory overhead for multi-agent systems. | [[arXiv]](https://arxiv.org/abs/2602.01053) |
| Agent Memory Below the Prompt | 2026 | Persists each agent's KV cache to disk in 4-bit quantized format for multi-agent LLM inference on edge devices, eliminating redundant prefill computation via direct cache restoration. | [[arXiv]](https://arxiv.org/abs/2603.04428) [[GitHub]](https://github.com/yshk-mxim/agent-memory) |
| Memento 2 | 2025 | Learning by stateful reflective memory with continual experiential updates, extending the original Memento framework with structured memory states. | [[arXiv]](https://arxiv.org/abs/2512.22716) |
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
| Recommender AI Agent | 2025 | Combines LLM reasoning with user interaction history to provide contextually-aware recommendations, maintaining memory of user preferences, past interactions, and feedback to improve recommendation relevance over time. | [[ACM]](https://doi.org/10.1145/3731446) |
| ComoRAG | 2025 | Organizes retrieved information using cognitive memory principles (episodic, semantic, working memory) to maintain narrative state across complex multi-turn reasoning tasks, improving coherence in story understanding and question answering. | [[arXiv]](https://arxiv.org/abs/2508.10419) |
| Seeing, Listening, Remembering | 2025 | Extends agent memory to handle multimodal inputs (vision, audio, text), creating unified memory representations that enable cross-modal retrieval and reasoning for more comprehensive environmental understanding. | [[arXiv]](https://arxiv.org/abs/2508.09736) |
| RoleLLM | 2025 | Provides systematic evaluation and improvement methods for role-playing capabilities, including memory mechanisms for maintaining character knowledge, speaking styles, and behavioral patterns across conversations. | [[ACL]](https://doi.org/10.18653/v1/2024.findings-acl.878) |
| Memory-R1 | 2025 | Trains agents to autonomously decide when to read, write, or forget memories using reinforcement learning, optimizing memory operations for downstream task performance rather than relying on fixed heuristics. | [[arXiv]](https://arxiv.org/abs/2508.19828) |
| Intrinsic Memory Agents | 2025 | Designs agents with built-in memory capabilities that don't require external databases, using structured internal representations to maintain context across heterogeneous multi-agent interactions. | [[arXiv]](https://arxiv.org/abs/2508.08997) |
| MIRIX | 2025 | Designs a shared memory infrastructure for multi-agent systems that enables agents to selectively share, query, and update collective knowledge while maintaining individual agent memory boundaries. | [[arXiv]](https://arxiv.org/abs/2507.07957) |
| Hierarchical Memory | 2025 | Organizes memory in hierarchical levels from detailed episodic traces to abstract semantic summaries, enabling efficient retrieval at appropriate granularity levels based on query requirements. | [[arXiv]](https://arxiv.org/abs/2507.22925) |
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
| Intrinsic Memory Agents | 2025 | Equips diverse agent types with role-specific memory structures, enabling heterogeneous multi-agent systems where each agent maintains contextually appropriate information for its specialized function. | [[arXiv]](https://arxiv.org/abs/2508.08997) |
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
| CAM | 2025 | Proposes a constructivist memory framework where agents actively construct understanding by integrating new information with existing knowledge structures, improving reading comprehension through schema-based memory organization rather than passive information storage. | [[arXiv]](https://arxiv.org/abs/2510.05520) |
| Pre-training Limited Memory | 2025 | Pre-trains language models with constrained internal memory that must learn to effectively utilize external knowledge stores, improving retrieval and integration of external information. | [[arXiv]](https://arxiv.org/abs/2505.15962) |
| CAMEL | 2023 | Introduces role-playing communication framework where AI agents engage in cooperative task-solving through structured dialogue, demonstrating emergent collaborative behaviors and enabling study of multi-agent social dynamics. | [[NeurIPS]](https://proceedings.neurips.cc/paper_files/paper/2023/hash/a3621ee907def47c1b952ade25c67571-Abstract-Conference.html) [[GitHub]](https://github.com/camel-ai/camel) |
| AutoGen | 2023 | Provides a framework for building multi-agent applications where LLM agents can converse, collaborate, and leverage tools through customizable conversation patterns, enabling complex workflows through agent cooperation. | [[arXiv]](https://arxiv.org/abs/2308.08155) [[GitHub]](https://github.com/microsoft/autogen) |
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
| CLIP-Fields | 2022 | Creates 3D semantic memory fields using CLIP embeddings, enabling robots to store and query spatial memories using natural language without dense manual annotations. | [[arXiv]](https://arxiv.org/abs/2210.05663) [[GitHub]](https://github.com/notmahi/clip-fields) |
| LM-Nav | 2022 | Combines language models with vision and action models for zero-shot robotic navigation, using language as an interface to query spatial memory and plan navigation routes. | [[arXiv]](https://arxiv.org/abs/2207.04429) |
| Scene Memory Transformer | 2019 | Applies transformer attention over stored scene observations, enabling embodied agents to selectively attend to relevant past observations for long-horizon task completion. | [[arXiv]](https://arxiv.org/abs/1903.03878) |
| Self-RAG | 2023 | Trains LLMs to adaptively retrieve information, generate responses, and critique their own outputs through self-reflection tokens, improving factuality by learning when retrieval helps versus hurts. | [[arXiv]](https://arxiv.org/abs/2310.11511) [[GitHub]](https://github.com/AkariAsai/self-rag) |
| CRAG | 2024 | Introduces a corrective mechanism that evaluates retrieval quality and triggers web search when initial retrieval is insufficient, improving robustness of RAG systems through dynamic retrieval correction. | [[arXiv]](https://arxiv.org/abs/2401.15884) [[GitHub]](https://github.com/HuskyInSalt/CRAG) |
| FLARE | 2023 | Implements active retrieval that predicts when the LLM needs additional information during generation, fetching relevant documents on-the-fly only when confidence is low to reduce unnecessary retrieval. | [[arXiv]](https://arxiv.org/abs/2305.06983) [[GitHub]](https://github.com/jzbjyb/FLARE) |
| DPR | 2020 | Proposes dual-encoder architecture for learning dense representations of queries and passages, enabling efficient nearest-neighbor search that outperforms traditional sparse retrieval methods. | [[arXiv]](https://arxiv.org/abs/2004.04906) [[GitHub]](https://github.com/facebookresearch/DPR) |
| Contriever | 2022 | Develops dense retrieval through contrastive pre-training without labeled data, learning useful passage representations from self-supervised objectives for zero-shot retrieval performance. | [[arXiv]](https://arxiv.org/abs/2112.09118) [[GitHub]](https://github.com/facebookresearch/contriever) |
| REALM | 2020 | Pre-trains language models jointly with a neural retriever, enabling the model to learn to retrieve and attend to relevant documents as part of its core language understanding capabilities. | [[arXiv]](https://arxiv.org/abs/2002.08909) |
| Atlas | 2023 | Combines retrieval-augmented pre-training with few-shot learning, demonstrating that smaller models with retrieval can match or exceed larger models on knowledge-intensive tasks with minimal examples. | [[JMLR]](https://www.jmlr.org/papers/v24/23-0037.html) [[GitHub]](https://github.com/facebookresearch/atlas) |
| kNN-LM | 2020 | Augments language models with a nearest neighbor mechanism over cached representations, improving generalization by explicitly memorizing and retrieving from training examples at inference time. | [[ICLR]](https://openreview.net/forum?id=HklBjCEKvH) |
| LLMLingua | 2023 | Compresses long prompts while preserving essential information for LLM inference, reducing computational costs and enabling processing of longer contexts within fixed context windows. | [[arXiv]](https://arxiv.org/abs/2310.05736) [[GitHub]](https://github.com/microsoft/LLMLingua) |

#### ⚙️ **Parametric Factual Memory**

> **Parametric Factual Memory** encodes factual knowledge directly into model weights through training or fine-tuning. This includes knowledge editing methods (ROME, MEMIT), adapter-based knowledge injection (K-Adapter, LoRA), and continual learning approaches that update model parameters to incorporate new facts.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| Pretraining with Hierarchical Memories | 2025 | Pre-trains models with separate memory modules for common and rare knowledge, allowing efficient storage of long-tail facts in external memory while keeping frequent knowledge in model parameters. | [[arXiv]](https://arxiv.org/abs/2510.02375) |
| MLP Memory | 2025 | Augments language models with MLP-based external memory modules that are pretrained alongside retrievers, enabling efficient storage and retrieval of factual knowledge. | [[arXiv]](https://arxiv.org/abs/2508.01832) |
| Self-Updatable LLMs | 2025 | Enables LLMs to update their own parameters based on new context, integrating learned information directly into model weights for persistent knowledge without external storage. | [[OpenReview]](https://openreview.net/forum?id=aCPFCDL9QY) |
| WISE | 2025 | Introduces a wise memory architecture for continual model editing that prevents catastrophic forgetting while allowing unlimited sequential knowledge updates to model parameters. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2024/hash/60960ad78868fce5c165295fbd895060-Abstract-Conference.html) |
| CharacterGLM | 2025 | Fine-tunes LLMs to embody specific social characters by encoding personality traits, speaking styles, and behavioral patterns directly into model parameters for consistent role-playing. | [[EMNLP]](https://doi.org/10.18653/v1/2024.emnlp-industry.107) |
| ELDER | 2025 | Uses mixture-of-LoRA adapters for lifelong model editing, where different LoRA modules store different knowledge updates that can be dynamically combined during inference. | [[AAAI]](https://doi.org/10.1609/aaai.v39i23.34622) |
| Online Adaptation (MAC) | 2025 | Enables online model adaptation by maintaining a memory of amortized context representations that can be quickly integrated into model computations without full fine-tuning. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2024/hash/eaf956b52bae51fbf387b8be4cc3ce18-Abstract-Conference.html) [[GitHub]](https://github.com/jihoontack/MAC) |
| AlphaEdit | 2024 | Constrains knowledge edits to the null space of preserved knowledge, enabling targeted factual updates without disrupting other learned information in model parameters. | [[arXiv]](https://arxiv.org/abs/2410.02355) |
| Neighboring Perturbations | 2024 | Analyzes how knowledge edits affect neighboring facts in the model's knowledge space, proposing methods to minimize unintended side effects of parameter modifications. | [[OpenReview]](https://openreview.net/forum?id=K9NTPRvVRI) |
| Character-LLM | 2024 | Develops character agents by training on character-specific data including background stories, behavioral patterns, and dialogue samples, enabling consistent persona maintenance across conversations. | [[EMNLP]](https://doi.org/10.18653/v1/2023.emnlp-main.814) [[GitHub]](https://github.com/choosewhatulike/trainable-agents) |
| Memory Layers at Scale | 2024 | Scales memory-augmented transformer layers to billions of parameters, demonstrating that explicit memory modules improve factual recall without proportional compute increases. | [[arXiv]](https://arxiv.org/abs/2412.09764) [[GitHub]](https://github.com/facebookresearch/memory) |
| MoExtend | 2024 | Adds new expert modules to mixture-of-experts models for handling new modalities and tasks, storing specialized knowledge in dedicated expert parameters. | [[arXiv]](https://arxiv.org/abs/2408.03511) [[GitHub]](https://github.com/zhongshsh/MoExtend) |
| K-Adapter | 2023 | Injects factual and linguistic knowledge into frozen pre-trained models through trainable adapter modules, enabling knowledge updates without full model retraining. | [[ACL]](https://doi.org/10.18653/v1/2021.findings-acl.121) |
| MEND | 2022 | Learns a hypernetwork that predicts parameter updates for rapid model editing, enabling fast factual corrections without expensive gradient-based fine-tuning. | [[ICLR]](https://openreview.net/forum?id=0DcZxeWfOPt) |
| MEMIT | 2022 | Enables simultaneous editing of thousands of facts in transformer models by identifying and modifying specific MLP layers that store factual associations. | [[ICLR]](https://openreview.net/forum?id=MkbcAHIYgyS) [[GitHub]](https://github.com/kmeng01/memit) |
| SERAC | 2022 | Maintains a separate memory of edits that overrides base model outputs when relevant, enabling scalable knowledge updates without modifying original model parameters. | [[ICML]](https://proceedings.mlr.press/v162/mitchell22a.html) [[GitHub]](https://github.com/eric-mitchell/serac) |
| ROME | 2021 | Localizes factual knowledge to specific model components and enables precise single-fact edits by modifying targeted MLP weights in transformer layers. | [[arXiv]](https://arxiv.org/abs/2104.08164) |
| ELLA | 2013 | Proposes efficient lifelong learning through shared task knowledge bases, enabling rapid learning of new tasks by leveraging previously learned parameter configurations. | [[ICML]](https://proceedings.mlr.press/v28/ruvolo13.html) |

#### 🧬 **Latent Factual Memory**

> **Latent Factual Memory** stores factual information in continuous vector representations or hidden states. This includes memory-augmented architectures (Neural Turing Machines, Memorizing Transformers), state space models (Mamba, RWKV), and learned memory tokens that compress knowledge into dense representations.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| Memory³ | 2025 | Augments language models with three types of explicit memory (working, episodic, semantic) stored in latent space, enabling efficient long-range information flow beyond attention mechanisms. | [[arXiv]](https://arxiv.org/abs/2407.01178) |
| HMT | 2025 | Processes long contexts through hierarchical memory compression, where lower levels store recent detailed information and higher levels maintain compressed summaries of distant context. | [[arXiv]](https://arxiv.org/abs/2405.06067) |
| Mamba | 2024 | Introduces selective state space models that achieve linear-time complexity while maintaining the ability to selectively remember or forget information based on input content. | [[arXiv]](https://arxiv.org/abs/2312.00752) [[GitHub]](https://github.com/state-spaces/mamba) |
| Mamba-2 | 2024 | Unifies transformers and state space models under a common framework, showing that attention can be viewed as a special case of structured state space layers with efficient hardware implementations. | [[arXiv]](https://arxiv.org/abs/2405.21060) |
| RWKV | 2023 | Combines the parallelizable training of transformers with the efficient inference of RNNs through a novel attention-free architecture with linear complexity and unlimited context length. | [[EMNLP]](https://aclanthology.org/2023.findings-emnlp.936/) [[GitHub]](https://github.com/BlinkDL/RWKV-LM) |
| RetNet | 2023 | Proposes retention mechanism as an alternative to attention, achieving training parallelism, low-cost inference, and linear complexity while matching transformer performance. | [[arXiv]](https://arxiv.org/abs/2307.08621) [[GitHub]](https://github.com/microsoft/torchscale) |
| Jamba | 2024 | Combines transformer attention layers with Mamba state space layers in a hybrid architecture, leveraging the strengths of both for efficient long-context processing. | [[arXiv]](https://arxiv.org/abs/2403.19887) |
| H3 | 2023 | Develops state space model layers that can match transformer performance on language modeling through selective gating and efficient convolution-based implementations. | [[ICLR]](https://openreview.net/forum?id=COZDy0WYGg) [[GitHub]](https://github.com/HazyResearch/H3) |
| Hyena | 2023 | Replaces attention with long convolutions and gating, achieving subquadratic complexity while maintaining competitive performance through hierarchical filter learning. | [[ICML]](https://proceedings.mlr.press/v202/poli23a.html) [[GitHub]](https://github.com/HazyResearch/safari) |
| Griffin | 2024 | Combines gated linear recurrent layers for global context with local attention windows, achieving efficient inference while preserving the modeling power of attention. | [[arXiv]](https://arxiv.org/abs/2402.19427) |
| Zamba | 2024 | Creates a compact 7B parameter model by combining state space layers with shared attention layers, achieving strong performance with significantly reduced memory footprint. | [[arXiv]](https://arxiv.org/abs/2405.16712) [[GitHub]](https://github.com/Zyphra/Zamba) |
| An Empirical Study of Mamba | 2024 | Provides systematic comparison between 8B-parameter Mamba and Transformer models across diverse tasks, analyzing strengths and weaknesses of state space architectures at scale. | [[arXiv]](https://arxiv.org/abs/2406.07887) |
| General Continuous Memory | 2025 | Develops continuous latent memory representations for vision-language models that persist across inputs, enabling more coherent multimodal reasoning over extended interactions. | [[arXiv]](https://arxiv.org/abs/2505.17670) |
| M+ | 2025 | Extends MemoryLLM with hierarchical memory architecture combining working memory with scalable external memory banks for information retention across millions of tokens. | [[arXiv]](https://arxiv.org/abs/2502.00592) |
| R3Mem | 2025 | Uses reversible compression to store memories in compact latent representations that can be decompressed for retrieval, balancing storage efficiency with information preservation. | [[arXiv]](https://arxiv.org/abs/2502.15957) |
| NAMM | 2025 | Evolves memory mechanisms using neural architecture search, discovering novel memory configurations that improve transformer performance across diverse tasks. | [[arXiv]](https://arxiv.org/abs/2410.13166) [[GitHub]](https://github.com/SakanaAI/evo-memory) |
| Thinker | 2025 | Implements dual-process cognition with fast intuitive responses and slow deliberative reasoning, using different memory access patterns for each thinking mode. | [[arXiv]](https://arxiv.org/abs/2505.21097) |
| Hierarchical Reasoning Model | 2025 | Structures reasoning in hierarchical levels from concrete operations to abstract planning, maintaining memory at each level for coordinated multi-step problem solving. | [[arXiv]](https://arxiv.org/abs/2506.21734) [[GitHub]](https://github.com/sapientinc/HRM/) |
| Efficient Episodic Memory | 2024 | Enables efficient sharing and utilization of episodic memories in multi-agent reinforcement learning, improving coordination through selective experience replay. | [[OpenReview]](https://openreview.net/forum?id=LjivA1SLZ6) |

### 🎓 Experiential Memory

> **Experiential Memory** (also called Episodic or Procedural Memory) stores records of past experiences, interactions, and learned skills. It answers "what have I done?" and enables agents to learn from past successes and failures, accumulate skills, and improve over time.

#### 🔤 **Token-level Experiential Memory**

> **Token-level Experiential Memory** stores past experiences, interactions, and learned skills as explicit records (e.g., conversation logs, action trajectories, skill libraries). Agents retrieve relevant past experiences to inform current decisions, enabling learning from trial-and-error and skill accumulation.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| Memory-R1 | 2025 | Trains agents using reinforcement learning to autonomously decide when to read, write, or delete memories, optimizing memory operations for downstream task performance. | [[arXiv]](https://arxiv.org/abs/2508.19828) |
| MemOrb | 2025 | Implements verbal reinforcement learning for customer service agents, where positive/negative feedback strengthens/weakens associated memory entries for improved response quality. | [[arXiv]](https://arxiv.org/abs/2509.18713) |
| Dynamic Affective Memory | 2025 | Manages emotional context in agent memory, tracking user affect states over time to enable emotionally appropriate and personalized responses across conversations. | [[arXiv]](https://arxiv.org/abs/2510.27418) |
| Preference-Aware Memory | 2025 | Dynamically updates user preference models in memory as new interactions reveal changing tastes, ensuring recommendations and responses reflect current rather than outdated preferences. | [[arXiv]](https://arxiv.org/abs/2510.09720) |
| Mem-PAL | 2025 | Creates personalized dialogue assistants that maintain comprehensive user memories including preferences, history, and relationship context for natural long-term interactions. | [[arXiv]](https://arxiv.org/abs/2511.13410) |
| PersonalAgent | 2025 | Enables agents to proactively customize user profiles based on interaction patterns, anticipating needs before explicit requests through learned behavioral models. | [[arXiv]](https://arxiv.org/abs/2512.15302) |
| Enabling Personalized Long-term | 2025 | Implements persistent user profiles and conversation memories that survive across sessions, enabling truly long-term personalized agent interactions. | [[arXiv]](https://arxiv.org/abs/2510.07925) |
| LD-Agent | 2024 | Develops personalized dialogue agents that learn and adapt to individual users over extended interactions, maintaining coherent user models across conversations. | [[arXiv]](https://arxiv.org/abs/2406.05925) |
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
| Buffer of Thoughts | 2025 | Maintains a buffer of high-level thought templates that can be instantiated for new problems, enabling more structured and reusable reasoning. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2024/hash/cde328b7bf6358f5ebb91fe9c539745e-Abstract-Conference.html) |
| From Exploration to Mastery | 2025 | Guides LLMs from initial tool exploration to mastery through self-driven practice, accumulating tool usage expertise in memory. | [[arXiv]](https://arxiv.org/abs/2410.08197) |
| REFLECT | 2025 | Generates natural language summaries of robot failures from experience, enabling diagnosis and correction of recurring error patterns. | [[arXiv]](https://arxiv.org/abs/2306.15724) [[Website]](https://robot-reflect.github.io/) |
| Planning from Imagination | 2024 | Combines episodic memory with mental simulation for navigation planning, imagining future states based on past experience for better route selection. | [[arXiv]](https://arxiv.org/abs/2412.01857) |
| ExpeL | 2024 | Demonstrates that LLM agents can learn from accumulated experiences stored in memory, extracting generalizable insights that transfer to new tasks. | [[AAAI]](https://doi.org/10.1609/aaai.v38i17.29936) [[GitHub]](https://github.com/LeapLabTHU/ExpeL) |
| RepairAgent | 2024 | Introduces autonomous, LLM-based agent for program repair. | [[arXiv]](https://arxiv.org/abs/2403.17134) |
| Fincon | 2024 | Coordinates multiple financial analysis agents with shared memory of market conditions and investment strategies for improved decision making. | [[arXiv]](https://arxiv.org/abs/2407.06567) |
| COLT | 2024 | Retrieves comprehensive sets of tools needed for tasks by learning from complete successful tool usage patterns in memory. | [[arXiv]](https://arxiv.org/abs/2405.16089) |
| ChatDev | 2024 | Simulates software company with communicating agents (CEO, CTO, programmer, tester) sharing project memory for collaborative code development. | [[arXiv]](https://arxiv.org/abs/2307.07924) [[GitHub]](https://github.com/OpenBMB/ChatDev) |
| LOTUS | 2024 | Discovers and accumulates manipulation skills from demonstrations without supervision, building expanding repertoires of reusable robot behaviors. | [[arXiv]](https://arxiv.org/abs/2311.02058) |
| RecMind | 2023 | Creates recommendation agents that learn user preferences through interaction, maintaining memory of user feedback for improved suggestions. | [[NAACL]](https://doi.org/10.18653/v1/2024.findings-naacl.271) |
| ToolLLM | 2023 | Enables LLMs to learn usage patterns for thousands of APIs, storing tool documentation and usage examples for accurate API calling. | [[arXiv]](https://arxiv.org/abs/2307.16789) |
| CREATOR | 2023 | Enables agents to create new tools by abstracting patterns from experience, separating high-level reasoning from implementation details. | [[EMNLP]](https://doi.org/10.18653/v1/2023.findings-emnlp.462) |
| Reflexion | 2023 | Enables agents to learn from verbal feedback by storing self-reflections on failures in memory, improving performance through linguistic experience replay. | [[arXiv]](https://arxiv.org/abs/2303.11366) [[GitHub]](https://github.com/noahshinn/reflexion) |
| Toolformer | 2023 | Trains language models to autonomously decide when and how to use tools by learning from self-generated tool usage examples. | [[arXiv]](https://arxiv.org/abs/2302.04761) |
| Voyager | 2023 | Creates an open-ended Minecraft agent that continuously expands its skill library through exploration, storing discovered programs in memory for reuse. | [[arXiv]](https://arxiv.org/abs/2305.16291) [[Website]](https://voyager.minedojo.org/) |
| GITM | 2023 | Develops generally capable Minecraft agents with hierarchical memory of goals, plans, and learned skills for flexible behavior in open-ended environments. | [[arXiv]](https://arxiv.org/abs/2305.17144) [[GitHub]](https://github.com/OpenGVLab/GITM) |
| Synapse | 2023 | Uses past successful computer control trajectories as in-context examples, enabling task completion through trajectory memory retrieval. | [[Website]](https://ltzheng.github.io/Synapse/) |
| MemRL | 2026 | Non-parametric agent evolution via RL on episodic memory with a two-phase retrieval mechanism that reconciles the stability-plasticity dilemma without weight updates. | [[arXiv]](https://arxiv.org/abs/2601.03192) [[GitHub]](https://github.com/MemTensor/MemRL) |
| MemEvolve | 2025 | Meta-evolutionary framework that jointly evolves agents' experiential knowledge and their memory architecture itself, improving frameworks like SmolAgent by up to 17%. | [[arXiv]](https://arxiv.org/abs/2512.18746) [[GitHub]](https://github.com/bingreeky/MemEvolve) |
| EchoVLA | 2025 | VLA model with scene memory (spatial-semantic maps) and episodic memory (task-level experiences with multimodal features) for long-horizon mobile manipulation. | [[arXiv]](https://arxiv.org/abs/2511.18112) |
| PhysMem | 2026 | Three-tier memory (episodic raw experiences, working memory hypotheses, long-term verified principles) enabling VLM robot planners to learn physics from interaction without parameter updates. | [[arXiv]](https://arxiv.org/abs/2602.20323) |
| MACLA | 2025 | Hierarchical procedural memory via Bayesian selection and contrastive refinement that compresses 2851 trajectories into 187 reusable procedures in 56 seconds (AAMAS 2026 Oral). | [[arXiv]](https://arxiv.org/abs/2512.18950) [[GitHub]](https://github.com/S-Forouzandeh/MACLA-LLM-Agents-AAMAS-Conference) |
| CodeMem | 2025 | Implements procedural memory as validated code, where agents write, validate, and save successful logic into a persistent procedural memory bank for deterministic reuse. | [[arXiv]](https://arxiv.org/abs/2512.15813) [[GitHub]](https://github.com/zhu-zhu-ding/CodeMem) |
| CoMAM | 2026 | Multi-agent system with local and global rewards enabling end-to-end RL optimization with simultaneous updates of heterogeneous policies for personalized memory. | [[arXiv]](https://arxiv.org/abs/2603.12631) |
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
| RT-1 | 2022 | Trains transformers on large-scale robot demonstration data, learning generalizable manipulation skills stored as model weights for real-world deployment. | [[arXiv]](https://arxiv.org/abs/2212.06817) [[Website]](https://robotics-transformer1.github.io/) |
| PaLM-E | 2023 | Introduces embodied multimodal language model. | [[arXiv]](https://arxiv.org/abs/2303.03378) |
| SayCan | 2022 | Grounds language instructions in robot capabilities by scoring actions based on both language relevance and affordance feasibility from experience. | [[arXiv]](https://arxiv.org/abs/2204.01691) [[Website]](https://say-can.github.io/) |
| Code as Policies | 2022 | Generates executable robot control code from language instructions, storing successful code patterns as reusable policy primitives. | [[arXiv]](https://arxiv.org/abs/2209.07753) [[Website]](https://code-as-policies.github.io/) |
| Inner Monologue | 2022 | Enables robots to reason about plans through internal language dialogue, incorporating feedback from perception and action into planning memory. | [[arXiv]](https://arxiv.org/abs/2207.05608) [[Website]](https://innermonologue.github.io/) |
| Episodic Memory for Robotics | 2021 | Stores robot manipulation experiences as retrievable episodes, enabling learning from specific past attempts for improved task execution. | [[arXiv]](https://arxiv.org/abs/2104.10218) |
| Generalizable Episodic Memory | 2021 | Creates episodic memory systems for RL agents that generalize across similar situations, improving sample efficiency through experience reuse. | [[arXiv]](https://arxiv.org/abs/2103.06469) |

#### ⚙️ **Parametric Experiential Memory**

> **Parametric Experiential Memory** encodes learned experiences and skills into model parameters through reinforcement learning, imitation learning, or continual fine-tuning. This includes RLHF, policy gradient methods, and approaches that update model weights based on interaction feedback.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| SleepGate | 2026 | Augments transformers with a learned sleep cycle over the KV cache for synaptic downscaling, selective replay, and targeted forgetting, reducing interference horizon from O(n) to O(log n). | [[arXiv]](https://arxiv.org/abs/2603.14517) |
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
| Auto-scaling Continuous Memory | 2025 | Dynamically scales continuous memory representations based on GUI complexity, automatically adjusting memory capacity for efficient desktop automation across varying interface states. | [[arXiv]](https://arxiv.org/abs/2510.09038) |

### ⚡ Working Memory

> **Working Memory** (also called Short-term Memory) manages the currently active context and information being processed. It answers "what am I focusing on now?" and handles the limited attention window, deciding what to keep, compress, or discard during extended interactions.

#### 🔤 **Token-level Working Memory**

> **Token-level Working Memory** manages the active context window through explicit text manipulation—deciding what information to keep, summarize, or discard as conversations extend beyond context limits. This includes context compression, summarization, and selective attention mechanisms.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
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
| Lightning Attention | 2025 | Achieves constant-speed inference regardless of sequence length through linear attention with learned decay patterns. | [[OpenReview]](https://openreview.net/forum?id=Lwm6TiUP4X) |
| Attention Sinks | 2024 | Maintains stable attention patterns in streaming by preserving initial sink tokens that anchor the attention distribution. | [[OpenReview]](https://openreview.net/forum?id=NG7sS51zVF) |

#### 🧬 **Latent Working Memory**

> **Latent Working Memory** manages active context through compressed latent representations, including KV cache optimization, recurrent memory states, and memory tokens. These approaches reduce memory footprint while preserving essential information for ongoing computation.

| Paper | Year | Description | Links |
|-------|------|-------------|-------|
| GVote | 2026 | Eliminates manual budget specification for KV cache via query sampling and voting, achieving 0.35 accuracy with only 10% memory on Multi-Doc QA (ICLR 2026). | [[OpenReview]](https://openreview.net/forum?id=0yLdDZMutq) |
| SemantiCache | 2026 | Partitions KV cache into semantically coherent chunks and applies greedy seed-based clustering to preserve semantic integrity during compression. | [[arXiv]](https://arxiv.org/abs/2603.14303) |
| VQKV | 2026 | Applies vector quantization to KV representations, achieving 82.8% compression on LLaMA3.1-8B while retaining 98.6% baseline performance. | [[arXiv]](https://arxiv.org/abs/2603.16435) |
| EchoKV | 2026 | Flexible KV cache compression enabling on-demand transitions between standard and compressed inference via similarity-based reconstruction. | [[arXiv]](https://arxiv.org/abs/2603.22910) [[GitHub]](https://github.com/noforit/EchoKV) |
| Mixture of Chapters | 2026 | Learnable sparse memory banks of latent tokens queried via cross-attention with chapter-based MoE routing, scaling to 262K memory tokens. | [[arXiv]](https://arxiv.org/abs/2603.21096) [[GitHub]](https://github.com/Tasmay-Tibrewal/Memory) |
| Latent Context Compilation | 2026 | Distills long contexts into compact buffer tokens via a disposable LoRA compiler, creating portable memory artifacts compatible with frozen base models. | [[arXiv]](https://arxiv.org/abs/2602.21221) |
| EvicPress | 2025 | Jointly optimizes KV cache compression and eviction strategies for efficient LLM inference, balancing memory usage with generation quality. | [[arXiv]](https://arxiv.org/abs/2512.14946) |
| ChunkKV | 2025 | Compresses KV cache by grouping semantically similar tokens into chunks, preserving attention patterns while reducing memory footprint. | [[arXiv]](https://arxiv.org/abs/2502.00299) |
| ClusterKV | 2024 | Clusters KV cache entries in semantic space for compression while maintaining ability to recall detailed information when needed. | [[arXiv]](https://arxiv.org/abs/2412.03213) |
| SmallKV | 2025 | Uses a small auxiliary model to compensate for information lost during aggressive KV cache compression in the main model. | [[arXiv]](https://arxiv.org/abs/2508.02751) |
| KVCompose | 2025 | Creates composite tokens that summarize multiple KV cache entries, enabling structured compression that preserves important information. | [[arXiv]](https://arxiv.org/abs/2509.05165) |
| Expected Attention | 2025 | Predicts which KV cache entries will be attended to by future tokens, enabling proactive eviction of unlikely-to-be-used entries. | [[arXiv]](https://arxiv.org/abs/2510.00636) |
| MemMamba | 2025 | Analyzes and improves memory utilization patterns in state space models, optimizing how information flows through recurrent computations. | [[arXiv]](https://arxiv.org/abs/2510.03279) |
| KV Cache Survey | 2024 | Comprehensively surveys KV cache optimization techniques including compression, eviction, quantization, and architectural modifications for efficient LLM inference. | [[arXiv]](https://arxiv.org/abs/2412.19442) |
| Time-VLM | 2025 | Applies vision-language model memory mechanisms to time series, enabling multimodal understanding of temporal patterns. | [[arXiv]](https://arxiv.org/abs/2502.04395) |
| SoftCoT | 2025 | Replaces explicit reasoning tokens with soft continuous representations, enabling efficient chain-of-thought reasoning in latent space. | [[ACL]](https://aclanthology.org/2025.acl-long.1137/) |
| MemoRAG | 2025 | Enhances RAG with global memory that captures document-wide patterns, improving retrieval for queries requiring broad context understanding. | [[ACM]](https://doi.org/10.1145/3696410.3714805) |
| MemGen | 2025 | Creates generative memory models that can synthesize new memories from latent representations, enabling creative experience recombination. | [[arXiv]](https://arxiv.org/abs/2509.24704) |
| Conflict-Aware Soft Prompting | 2025 | Uses soft prompts to resolve conflicts between retrieved information and model knowledge, improving RAG reliability. | [[arXiv]](https://arxiv.org/abs/2508.15253) |
| MemoryVLA | 2025 | Integrates perceptual and cognitive memory in vision-language-action models, enabling robots to remember and reason about manipulation tasks. | [[arXiv]](https://arxiv.org/abs/2508.19236) |
| MEM1 | 2025 | Learns optimal integration of memory retrieval with reasoning steps for efficient completion of long-horizon tasks. | [[arXiv]](https://arxiv.org/abs/2506.15841) |
| Sentinel Tokens | 2025 | Inserts learnable sentinel tokens that aggregate context information, providing compressed working memory anchors for improved modeling. | [[EMNLP]](https://doi.org/10.18653/v1/2024.findings-emnlp.233) |
| H2O | 2025 | Identifies and retains heavy-hitter tokens that receive disproportionate attention, enabling aggressive KV cache reduction without quality loss. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/6ceefa7b15572587b78ecfcebb2827f8-Abstract-Conference.html) |
| RazorAttention | 2025 | Identifies retrieval-focused attention heads and compresses their KV caches specifically, preserving critical information access patterns. | [[OpenReview]](https://openreview.net/forum?id=tkiZQlL04w) |
| SnapKV | 2025 | Predicts important KV cache entries before generation begins, enabling proactive caching of relevant context. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2024/hash/28ab418242603e0f7323e54185d19bde-Abstract-Conference.html) |
| LM2 | 2025 | Introduces large-scale learnable memory modules that augment language models with massive external memory capacity. | [[arXiv]](https://arxiv.org/abs/2502.06049) |
| Titans | 2025 | Enables models to learn and update memory during inference, adapting to test-time information without training. | [[arXiv]](https://arxiv.org/abs/2501.00663) [[GitHub]](https://github.com/ai-inpm/Titans---Learning-to-Memorize-at-Test-Time) |
| TTT | 2025 | Implements test-time training in RNN hidden states, enabling dynamic memory updates during inference. | [[arXiv]](https://arxiv.org/abs/2407.04620) [[GitHub]](https://github.com/test-time-training/ttt-lm-pytorch) |
| Adacc | 2025 | Adaptively trades off compression and checkpointing based on memory pressure, optimizing memory usage during LLM inference. | [[arXiv]](https://arxiv.org/abs/2508.00806) |
| EdgeInfinite | 2025 | Enables infinite-context processing on edge devices through extreme memory efficiency techniques for on-device deployment. | [[arXiv]](https://arxiv.org/abs/2503.22196) |
| Augmenting LLMs with Long-Term Memory | 2024 | Augments LLMs with differentiable long-term memory modules that persist across contexts and can be updated through backpropagation. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/ebd82705f44793b6f9ade5a669d0f0bf-Abstract-Conference.html) |
| Context Compression | 2024 | Trains language models to compress long contexts into shorter representations while preserving task-relevant information. | [[EMNLP]](https://doi.org/10.18653/v1/2023.emnlp-main.232) |
| Gist Tokens | 2024 | Learns compressed gist tokens that capture prompt semantics, enabling efficient prompt caching and reuse. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/3d77c6dcc7f143aa2154e7f4d5e22d68-Abstract-Conference.html) |
| Scissorhands | 2024 | Leverages the observation that token importance persists across layers to efficiently prune KV cache entries. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/a452a7c6c463e4ae8fbdc614c6e983e6-Abstract-Conference.html) |
| StreamingLLM | 2024 | Enables infinite-length streaming by maintaining attention sinks that anchor the working memory window for stable generation. | [[ICLR]](https://openreview.net/forum?id=NG7sS51zVF) [[GitHub]](https://github.com/mit-han-lab/streaming-llm) |
| PyramidKV | 2024 | Applies pyramidal compression where early layers retain more keys while later layers are more aggressively compressed. | [[arXiv]](https://arxiv.org/abs/2406.02069) [[GitHub]](https://github.com/Zefan-Cai/PyramidKV) |
| KIVI | 2024 | Quantizes KV cache to 2 bits using asymmetric quantization that preserves important value ranges without fine-tuning. | [[arXiv]](https://arxiv.org/abs/2402.02750) [[GitHub]](https://github.com/jy-yuan/KIVI) |
| MiniCache | 2024 | Compresses KV cache across the depth dimension by sharing representations between adjacent layers. | [[arXiv]](https://arxiv.org/abs/2405.14366) |
| CacheGen | 2024 | Accelerates context loading through pre-computed and cached KV representations that can be rapidly loaded for repeated contexts. | [[arXiv]](https://arxiv.org/abs/2310.07240) [[GitHub]](https://github.com/LMCache/LMCache) |
| Focused Transformer | 2024 | Uses contrastive learning to train transformers that better focus attention on relevant context, improving long-range dependencies. | [[NeurIPS]](http://papers.nips.cc/paper_files/paper/2023/hash/8511d06d5590f4bda24d42087802cc81-Abstract-Conference.html) |
| In-Context Autoencoder | 2023 | Trains an autoencoder within the language model that compresses and reconstructs context representations for efficient processing. | [[arXiv]](https://arxiv.org/abs/2307.06945) |
| Memorizing Transformers | 2022 | Augments transformers with kNN-based memory that can store and retrieve from massive external databases at inference time. | [[OpenReview]](https://openreview.net/forum?id=TrjbxzRcnf-) |
| Recurrent Memory Transformer | 2022 | Adds recurrent memory tokens that carry information across segments, enabling transformers to process unlimited length sequences. | [[NeurIPS]](https://openreview.net/forum?id=Uynr3iPhksa) [[GitHub]](https://github.com/booydar/recurrent-memory-transformer) |
| Scaling RMT to 1M Tokens | 2023 | Scales Recurrent Memory Transformer to handle 2 million token contexts through improved memory management and training. | [[arXiv]](https://arxiv.org/abs/2304.11062) |
| Transformer-XL | 2019 | Introduces segment-level recurrence where hidden states from previous segments are cached and reused, enabling longer context modeling. | [[arXiv]](https://arxiv.org/abs/1901.02860) [[GitHub]](https://github.com/kimiyoung/transformer-xl) |
| Compressive Transformer | 2020 | Compresses old memories into fixed-size representations that can still be attended to, balancing memory capacity with computational cost. | [[arXiv]](https://arxiv.org/abs/1911.05507) |
| Infini-Attention | 2024 | Combines local attention with compressive memory that accumulates information from unbounded past context for infinite-length processing. | [[arXiv]](https://arxiv.org/abs/2404.07143) |
| Longformer | 2020 | Uses sliding window attention with global tokens to achieve linear complexity for long document processing. | [[arXiv]](https://arxiv.org/abs/2004.05150) [[GitHub]](https://github.com/allenai/longformer) |
| BigBird | 2020 | Combines random, window, and global attention patterns to create sparse attention that scales linearly with sequence length. | [[NeurIPS]](https://proceedings.neurips.cc/paper/2020/hash/c8512d142a2d849725f31a9a7a361ab9-Abstract.html) |
| Neural Turing Machine | 2014 | Augments neural networks with differentiable external memory that can be read from and written to through attention-based addressing. | [[arXiv]](https://arxiv.org/abs/1410.5401) |
| Differentiable Neural Computer | 2016 | Extends Neural Turing Machines with improved memory addressing including content-based lookup and temporal memory linking. | [[Nature]](https://www.nature.com/articles/nature20101) |
| XMem | 2022 | Models video object segmentation memory after human memory systems with sensory, working, and long-term memory stores. | [[arXiv]](https://arxiv.org/abs/2207.07115) |

## 📊 Benchmarks & Evaluation

### Memory Evaluation Benchmarks

| Benchmark | Year | Focus | Context Length | Links |
|-----------|------|-------|----------------|-------|
| **PERMA** | 2026 | Persona consistency over temporally ordered multi-session interactions | Various | [[arXiv]](https://arxiv.org/abs/2603.23231) [[GitHub]](https://github.com/PolarisLiu1/PERMA) |
| **AMA-Bench** | 2026 | Long-horizon memory for agentic applications with arbitrary-length trajectories | Various | [[arXiv]](https://arxiv.org/abs/2602.22769) |
| **EMemBench** | 2026 | Interactive benchmarking of episodic memory for VLM agents | Various | [[arXiv]](https://arxiv.org/abs/2601.16690) |
| **Evo-Memory** | 2025 | Self-evolving memory and test-time learning | Various | [[arXiv]](https://arxiv.org/abs/2511.20857) |
| **MemBench** | 2025 | Comprehensive memory evaluation (effectiveness, efficiency, capacity) | Various | [[arXiv]](https://arxiv.org/abs/2506.21605) |
| **FindingDory** | 2025 | Memory evaluation in embodied agents | Various | [[arXiv]](https://arxiv.org/abs/2506.15635) [[HuggingFace]](https://huggingface.co/yali30/findingdory-qwen2.5-VL-3B-finetuned) |
| **MemoryBench** | 2025 | Memory and continual learning | Various | [[arXiv]](https://arxiv.org/abs/2510.17281) |
| **MemoryAgentBench** | 2025 | Incremental multi-turn interactions | Various | [[arXiv]](https://arxiv.org/abs/2507.05257) |
| **Memento (Benchmark)** | 2025 | Personalized embodied assistance evaluation | Various | [[arXiv]](https://arxiv.org/abs/2505.16348) |
| **HaluMem** | 2025 | Evaluating hallucinations in memory systems | Various | [[arXiv]](https://arxiv.org/abs/2505.00000) |
| **LoCoMo** | 2024 | Very long-term conversational memory | ~9K tokens, 35 sessions | [[arXiv]](https://arxiv.org/abs/2402.17753) [[Website]](https://snap-research.github.io/locomo/) |
| **LongMemEval** | 2024 | Long-term interactive memory | ~115K-1.5M tokens | [[arXiv]](https://arxiv.org/abs/2410.10813) [[GitHub]](https://github.com/xiaowu0162/LongMemEval) |
| **LaMP** | 2023 | Language model personalization benchmark | Various | [[arXiv]](https://arxiv.org/abs/2304.11406) [[GitHub]](https://github.com/LaMP-Benchmark/LaMP) |
| **LongLaMP** | 2024 | Long-text language model personalization benchmark | Long contexts | [[arXiv]](https://arxiv.org/abs/2407.11016) [[GitHub]](https://github.com/LaMP-Benchmark/LongLaMP) |

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
| **Zep/Graphiti** | 2025 | Temporal knowledge graph for agent memory | [[GitHub]](https://github.com/getzep/zep) [[arXiv]](https://arxiv.org/abs/2501.13956) |
| **Memory-R1** | 2025 | RL-based memory management for LLM agents | [[arXiv]](https://arxiv.org/abs/2508.19828) |
| **MemOS** | 2025 | Operating system for memory-augmented generation in LLMs | [[GitHub]](https://github.com/MemoryAgent/MemOS) |
| **PowerMem** | 2025 | Agent-powered long-term memory with Ebbinghaus forgetting curve | [[GitHub]](https://github.com/Teingi/PowerMem) |
| **HippoRAG** | 2024 | Neurobiologically inspired long-term memory with knowledge graphs | [[GitHub]](https://github.com/OSU-NLP-Group/HippoRAG) [[arXiv]](https://arxiv.org/abs/2405.14831) |
| **LangMem** | 2024 | Long-term memory for LangChain agents | [[Docs]](https://langchain-ai.github.io/langmem/) |
| **MemGPT/Letta** | 2023 | LLMs as operating systems with hierarchical memory management | [[GitHub]](https://github.com/cpacker/MemGPT) [[arXiv]](https://arxiv.org/abs/2310.08560) |

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
| **🧪 Standardized Benchmarks** | Unified evaluation protocols (LoCoMo, LongMemEval, MemoryBench, LaMP) |
| **🧠 Cognitive Inspiration** | Drawing from neuroscience (HippoRAG, episodic memory) |
| **🔄 Self-Evolution** | Agents that continuously improve their own memory systems |

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
- Appropriate categorization by Form × Function

---

<p align="center">
  <strong>⭐ Star this repo if you find it helpful!</strong>
</p>

<p align="center">
  Made with ❤️ for the Agent Research Community
</p>
