# Open-Source Mixture-of-Agents (MoA) Orchestrator
```mermaid
graph TD
    %% تعريف الألوان والتنسيقات
    classDef user fill:#2ecc71,stroke:#27ae60,stroke-width:2px,color:#fff;
    classDef layer1 fill:#3498db,stroke:#2980b9,stroke-width:2px,color:#fff;
    classDef layer2 fill:#9b59b6,stroke:#8e44ad,stroke-width:2px,color:#fff;
    classDef output fill:#e67e22,stroke:#d35400,stroke-width:2px,color:#fff;

    %% تدفق البيانات
    User([📥 User Prompt]) :::user --> |Parallel Execution| L1_1
    User --> |Parallel Execution| L1_2
    User --> |Parallel Execution| L1_3
    User --> |Parallel Execution| L1_4
    User --> |Parallel Execution| L1_5

    %% الطبقة الأولى: النماذج المرجعية
    subgraph Layer 1: Reference Models (The Specialists)
        L1_1[🤖 deepseek-v4-flash-free <br><b>Reasoning</b>] :::layer1
        L1_2[⚡ nemotron-3-ultra-free <br><b>Analysis</b>] :::layer1
        L1_3[💻 north-mini-code-free <br><b>Coding</b>] :::layer1
        L1_4[💬 mimo-v2.5-free <br><b>Chat</b>] :::layer1
        L1_5[📦 big-pickle <br><b>General Purpose</b>] :::layer1
    end

    %% تجميع الردود
    L1_1 --> |Response Payload| L2[🧠 Aggregator Layer:<br>DeepSeek V4 Flash] :::layer2
    L1_2 --> |Response Payload| L2
    L1_3 --> |Response Payload| L2
    L1_4 --> |Response Payload| L2
    L1_5 --> |Response Payload| L2

    %% المخرج النهائي
    L2 --> |Synthesize & Refine| FinalOut([🏆 Consolidated Output]) :::output

An efficient, cost-effective, and highly reliable AI system that orchestrates multiple open-source Large Language Models (LLMs) concurrently using the **Mixture-of-Agents (MoA)** architecture—achieving enterprise-grade results at zero API cost.

## 🏗️ Architecture Overview

The framework operates on a dual-layer architectural pattern designed to maximize output quality through collaborative intelligence:

1. **Layer 1: Reference Models (The Specialists):** Executes 4 specialized free-tier models in parallel to process the initial prompt based on their distinct domains:
   * **NVIDIA Nemotron 3 Ultra:** Analytical processing and behavior modeling.
   * **North Mini Code:** Architectural design and code structuring.
   * **Mimo v2.5:** Conversational flow and interactive logic.
   * **Big Pickle:** General contextual reasoning.
2. **Layer 2: Aggregator Model (The Synthesizer):** Powered by **DeepSeek V4 Flash**, this layer ingests all preliminary responses, cross-references inputs, resolves inconsistencies, and synthesizes the definitive high-quality output.

## 🛠️ Solved Technical Challenges

During development, several production-level engineering roadblocks were successfully resolved:
* **Platform Incompatibility:** Replaced the unstable `httpx` asynchronous behavior on Windows environments with a deterministic, retry-capable implementation using the `requests` library.
* **Response Schema Inconsistencies:** Designed an adaptive JSON parser to gracefully handle and extract text from diverse model response structures, seamlessly unified across both standard `content` payloads and advanced `reasoning` paths.
* **API Key Resilience:** Implemented a robust failover mechanism (Fallback) ensuring uninterrupted agent coordination and high system availability.

## 🚀 Getting Started

### Prerequisites
Ensure you have Python 3.8+ installed along with the required dependencies:
```bash
pip install requests python-dotenv

