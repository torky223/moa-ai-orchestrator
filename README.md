# منسق الذكاء الاصطناعي لـ Mixture-of-Agents (MoA)

إطار عمل خفيف الوزن وفعال من حيث التكلفة لمزيج من العوامل (MoA) يدمج وينسق بين 5 نماذج لغة كبيرة (LLMs) مفتوحة المصدر ومجانية بالكامل لتعمل معاً كفريق واحد، مما يحقق نتائج عالية الدقة بتكلفة برمجية صفرية.

---

## 📊 System Architecture

```mermaid
graph TD
    User[User Prompt Input] --> L1
    User --> L2
    User --> L3
    User --> L4
    User --> L5

    subgraph Layer1 [Layer 1: Reference Models]
        L1[deepseek-v4-flash-free]
        L2[nemotron-3-ultra-free]
        L3[north-mini-code-free]
        L4[mimo-v2.5-free]
        L5[big-pickle]
    end

    L1 --> Aggregator[Aggregator Layer: DeepSeek V4 Flash]
    L2 --> Aggregator
    L3 --> Aggregator
    L4 --> Aggregator
    L5 --> Aggregator

    Aggregator --> FinalOut[Consolidated High Quality Output]

    %% تخصيص الألوان البرمجية اللامعة المتوافقة مع الـ Dark Mode
    style User fill:#218838,stroke:#28a745,stroke-width:2px,color:#fff
    style Aggregator fill:#6f42c1,stroke:#8a59e3,stroke-width:2px,color:#fff
    style FinalOut fill:#fd7e14,stroke:#f85a1b,stroke-width:2px,color:#fff
