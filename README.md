# Agentic Last-Mile Coordinator (Project Synapse)

## 📌 Overview  
Last-mile delivery often faces unpredictable real-time disruptions such as incorrect addresses, unavailable recipients, sudden road closures, traffic congestion, merchant delays, and inventory issues. Traditional rule-based systems are brittle and fail to handle such dynamic, uncertain scenarios.  

**Project Synapse** proposes an **agentic AI architecture** that leverages both **Large Language Models (LLMs)** and **Small Language Models (SLMs)** in a **multi-layer, non-monolithic framework**. This architecture provides **human-like reasoning, task-specific intelligence, and secure coordination** across multiple delivery tasks.  

---

## 🚀 Key Features & Contributions
- **Architectural Design (not full implementation)**: Designed the complete system architecture for scalable, adaptive last-mile coordination.  
- **Non-Monolithic, Modular Design**: Each agent operates independently, enabling scalability, simplified integration, and reduced maintenance overhead.  
- **Multi-Layer Reasoning**:  
  - **LLM (Orchestrator)** – Extracts intent from user input and generates structured parameters.  
  - **Model Context Protocol (MCP)** – Maps tasks to appropriate SLMs with guardrails for security and consistency.  
  - **SLMs (Specialized Agents)** – Task-specific reasoning and minimal-context inference prevent hallucinations and improve reliability.  
  - **Tool Ecosystem** – External APIs (e.g., Maps, Traffic, Inventory) for final execution.  
- **Guardrails & Security**: MCP enforces policies, protects against prompt injection attacks, and ensures secure routing of tasks.  
- **Data Privacy**: Retrieval-Augmented Generation (RAG) provides contextual knowledge while allowing **local hosting of SLMs** to safeguard sensitive company data.  
- **Scalability**: Supports extending the system with additional specialized agents without redesigning the architecture.  

---

## 🏗️ Architecture  

### 🔹 Process Flow  
1. **User Input** → A natural language delivery request is entered.  
2. **LLM Orchestrator** → Parses input into structured parameters (JSON).  
3. **MCP (Model Context Protocol)** → Maps the task to the right SLM(s) and applies system-defined policies.  
4. **SLM Agents** → Perform domain-specific reasoning (traffic, routing, inventory checks, etc.) using minimal context.  
5. **Tool Layer** → Executes tasks via APIs (Google Maps, traffic monitoring, inventory systems, etc.).  
6. **Final Output** → Optimized decision returned to the user/system.  

---

### 🔹 High-Level Diagram (Mermaid)

```mermaid
flowchart LR
    A[User Input] --> B[LLM Orchestrator]
    B --> C[MCP - Task Mapper + Guardrails]
    C --> D[SLM Agents - Domain Specific]
    D --> E[External Tools/APIs]
    E --> F[Final Decision]
