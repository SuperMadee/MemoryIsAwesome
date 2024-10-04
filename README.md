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

⭐ The memory models that use **inside-trial information** are the following:
* [MemoryBank: Enhancing Large Language Models with Long-Term Memory](https://github.com/zhongwanjun/MemoryBank-SiliconFriend)
  
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

💡 _Personal take: Memory models use inside-trial information only to focus on the specific details and features relevant to a particular task or context. This approach simplifies the model, reducing complexity and computational demands while allowing for a more precise understanding of how memory functions within controlled settings._

- [x] **Cross-trial Information** - Memory that spans multiple trials or tasks that involves knowledge accumulated over time and used in different situations.
    
- [x] **External Knowledge** - Memory that comes from external resources, such as online databases, books, or magazines, rather than the agent’s own experiences or interactions.

⭐ The memory models that use **both inside-trial information and external knowledge** are the following:
* [RET-LLM: Towards a General Read-Write Memory for Large Language Models](https://arxiv.org/abs/2305.14322)
  
* [ChatDB: Augmenting LLMs with Databases as Their Symbolic Memory](https://chatdatabase.github.io/)
  
* [RecMind: Large Language Model Powered Agent For Recommendation](https://arxiv.org/pdf/2308.14296)

* [ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629)

* [Character-LLM: A Trainable Agent for Role-Playing](https://github.com/choosewhatulike/trainable-agents)

* [HuaTuo: Tuning LLaMA Model with Chinese Medical Knowledge](https://arxiv.org/pdf/2304.06975)

* [Recommender AI Agent: Integrating Large Language Models for Interactive Recommendations](https://github.com/microsoft/RecAI/blob/main/InteRecAgent)

* [TPTU: Large Language Model-based AI Agents for Task Planning and Tool Usage](https://arxiv.org/abs/2308.03427)

* [TPTU-v2: Boosting Task Planning and Tool Usage of Large Language Model-based Agents in Real-world Systems](https://arxiv.org/abs/2311.11315)

* [InvestLM: A Large Language Model for Investment using Financial Domain Instruction Tuning](https://github.com/AbaciNLP/InvestLM)

💡 _Personal take: Memory models integrate inside-trial information and external sources during the encoding and retrieval processes to allow the model to form stronger associations and adapt to various contexts, enhancing memory accuracy and resilience against errors._

⭐ The memory models that use **both inside-trial information and cross-trial information** are the following:

* [Synapse: Trajectory-as-Exemplar Prompting with Memory for Computer Control](https://ltzheng.github.io/Synapse/)

* [MetaGPT: Meta Programming for A Multi-Agent Collaborative Framework](https://arxiv.org/abs/2308.00352)

💡 _Personal take: Memory models use both inside-trial and cross-trial information to improve recall accuracy, adapt to varying contexts, recognize patterns, and enhance flexibility in memory retrieval. This approach better simulates complex, real-world memory processes._

⭐ The memory models that use **all sources of information** are the following:

* [Reflexion: Language Agents with Verbal Reinforcement Learning](https://github.com/noahshinn/reflexion)

* [ExpeL: LLM Agents are Experiential Learners](https://github.com/LeapLabTHU/ExpeL)

* [Ghost in the Minecraft: Generally Capable Agents for Open-World Environments via Large Language Models with Text-based Knowledge and Memory](https://github.com/OpenGVLab/GITM)

* [Retroformer: Retrospective large language agents with policy gradient optimization](https://github.com/weirayao/Retroformer) 

💡 _Personal take: Memory models use inside-trial information, cross-trial information, and external knowledge to improve recall, adapt to contexts, generalize patterns, and enhance flexibility, creating a more accurate representation of human memory._

----
### References:
[1] A Survey on the Memory Mechanism of Large Language Model-based Agents
 https://github.com/nuster1128/LLM_Agent_Memory_Survey



