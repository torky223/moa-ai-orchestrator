# منسق الذكاء الاصطناعي لـ Mixture-of-Agents (MoA)

إطار عمل خفيف الوزن وفعال من حيث التكلفة لمزيج من العوامل (MoA) يدمج وينسق بين 5 نماذج لغة كبيرة (LLMs) مفتوحة المصدر ومجانية بالكامل لتعمل معاً كفريق واحد، مما يحقق نتائج عالية الدقة بتكلفة برمجية صفرية.

---

## 📊 المخطط المعماري لتدفق البيانات (System Architecture)

```mermaid
graph TD
    %% تعريف تنسيقات الألوان (CSS Classes)
    classDef userNode fill:#2ecc71,stroke:#27ae60,stroke-width:2px,color:#fff;
    classDef layer1Node fill:#3498db,stroke:#2980b9,stroke-width:2px,color:#fff;
    classDef layer2Node fill:#9b59b6,stroke:#8e44ad,stroke-width:2px,color:#fff;
    classDef outputNode fill:#e67e22,stroke:#d35400,stroke-width:2px,color:#fff;

    %% تدفق المخطط المعماري
    User[User Prompt Input] :::userNode --> L1_1
    User --> L1_2
    User --> L1_3
    User --> L1_4
    User --> L1_5

    %% الطبقة الأولى: الوكلاء المرجعيون
    subgraph Layer 1: Reference Models (The Specialists)
        L1_1[deepseek-v4-flash-free - Reasoning] :::layer1Node
        L1_2[nemotron-3-ultra-free - Analysis] :::layer1Node
        L1_3[north-mini-code-free - Coding] :::layer1Node
        L1_4[mimo-v2.5-free - Chat] :::layer1Node
        L1_5[big-pickle - General Purpose] :::layer1Node
    end

    %% الطبقة الثانية: المجمع النهائي
    L1_1 --> L2[Aggregator Layer: DeepSeek V4 Flash] :::layer2Node
    L1_2 --> L2
    L1_3 --> L2
    L1_4 --> L2
    L1_5 --> L2

    %% النتيجة النهائية
    L2 --> FinalOut[Consolidated High Quality Output] :::outputNode
