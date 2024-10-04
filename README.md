# Memory is Awesome 🧠

A memory can be defined as:
- the actions and observations within a single trial, where a trial is a complete agent-environment interaction sequence involving a task.
- the actions and observations not only from the current trial but also from past trials and external sources of knowledge.

<img width="896" alt="image" src="https://github.com/user-attachments/assets/11bf212b-b1fb-4057-ac69-4a59d46bfced">

---
### 🧠 How does an agent interact with the environment?
This process shows how the agent learns and evolves through interactions with its environment <br>
(through tasks labeled as "Task A" and "Task B"). <br>

<img width="928" alt="image" src="https://github.com/user-attachments/assets/ed0136e6-9541-49a3-b428-e3bf3c719c5c">
<br> <br>

**Components:**
- [x] Agent (robot) - The LLM-based agent interacting with the environment.
- [x] Action - The agent performs specific actions based on prior observations and memory.
- [x] Observation - Feedback or information received by the agent after it performs an action in the environment.

**Memory Operations:**
- [x] W (Writing): The process of writing the information (actions and observations) into memory. After each observation, the memory is updated.
- [x] P (Processing/Management): The management operation that refines and processes stored memories, such as summarizing key information, merging or pruning redundant data, or forgetting irrelevant information.
- [x] R (Reading): The process of retrieving stored memory information to support the agent’s next action. This retrieval is based on the relevance of previous memories to the current context.

---
### 🧠 Memory Sources
- this refers to the various sources from which the memory's contents can originate. It can be classified into [1] Inside-trial information, [2] Cross-trial information, and [3] External Knowledge.

<p align="center"><img width="680" alt="image" src="https://github.com/user-attachments/assets/d538cc3c-794f-417f-af66-50cfa62258b3"></p>

- [x] **Inside-trial Information** - Memory specific to the current task or interaction. It focuses on immediate information, such as actions, observations, and decisions made during the ongoing task. <br>

The memory models that use inside-trial information are the following:
* [MemoryBank: Enhancing Large Language Models with Long-Term Memory](https://github.com/zhongwanjun/MemoryBank-SiliconFriend) <br>
* [Think-in-Memory: Recalling and Post-thinking enable LLMs with Long-term Memory](https://arxiv.org/pdf/2311.08719)
* [Unleashing Infinite-Length Input Capacity for Large-scale Language Models with Self-controlled Memory System](https://github.com/wbbeyourself/scm4llms)
* [Voyager: An open-ended embodied agent with large language models](https://voyager.minedojo.org/)
* [Memgpt: Towards LLMs as Operating Systems](https://memgpt.ai/)
* [MemoChat: Tuning LLMs to Use Memos for Consistent Long-Range Open-domain Conversation](https://github.com/LuJunru/MemoChat)
* [Prompted LLMs as Chatbot Modules for Long Open-domain Conversation](https://github.com/krafton-ai/MPC)
* [Generative Agents: Interactive Simulacra of Human Behavior](https://github.com/joonspk-research/generative_agents)
* [User Behavior Simulation with Large Language Model-based Agents](https://arxiv.org/abs/2306.02552)
* [Online Adaptation of Language Models with a Memory of Amortized Contexts](https://arxiv.org/abs/2403.04317)
* [MetaAgents: Simulating Interactions of Human Behaviors for LLM-based Task-oriented Coordination via Collaborative Generative Agents](https://arxiv.org/abs/2310.06500)
* [ChatDev: Communicative Agents for Software Development](https://arxiv.org/abs/2307.07924)
* [S3: Social-network Simulation System with Large Language Model-Empowered Agents](https://arxiv.org/abs/2307.14984)

- [x] **Cross-trial Information** - Memory that spans multiple trials or tasks that involves knowledge accumulated over time and used in different situations.
    
- [x] External Knowledge - Memory that comes from external resources, such as online databases, books, or magazines, rather than the agent’s own experiences or interactions.





----
### References:
[1] A Survey on the Memory Mechanism of Large Language Model-based Agents
 https://github.com/nuster1128/LLM_Agent_Memory_Survey



