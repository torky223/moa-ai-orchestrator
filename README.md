# منسق الذكاء الاصطناعي لـ Mixture-of-Agents (MoA)

إطار عمل خفيف الوزن وفعال من حيث التكلفة لمزيج من العوامل (MoA) يدمج وينسق بين 5 نماذج لغة كبيرة (LLMs) مفتوحة المصدر ومجانية بالكامل لتعمل معاً كفريق واحد، مما يحقق نتائج عالية الدقة بتكلفة برمجية صفرية.

---

## 📊 المخطط المعماري لتدفق البيانات (System Architecture)

```mermaid
graph TD
    %% تدفق المخطط المعماري الأساسي
    User[📥 طلب المستخدم - User Prompt] --> L1_1
    User --> L1_2
    User --> L1_3
    User --> L1_4
    User --> L1_5

    %% الطبقة الأولى: الوكلاء المرجعيون
    subgraph الطبقة الأولى: النماذج المرجعية (The Specialists)
        L1_1[🤖 deepseek-v4-flash-free <br> التفكير والاستدلال]
        L1_2[⚡ nemotron-3-ultra-free <br> التحليل السريع]
        L1_3[💻 north-mini-code-free <br> البرمجة والأكواد]
        L1_4[💬 mimo-v2.5-free <br> المحادثة والتفاعل]
        L1_5[📦 big-pickle <br> الأغراض العامة]
    end

    %% الطبقة الثانية: المجمع النهائي
    L1_1 --> L2[🧠 طبقة التجميع والمزامنة <br> DeepSeek V4 Flash]
    L1_2 --> L2
    L1_3 --> L2
    L1_4 --> L2
    L1_5 --> L2

    %% النتيجة النهائية
    L2 --> FinalOut[🏆 مخرج نهائي موحد عالي الجودة]

    %% التنسيق اللوني الافتراضي للمخطط
    style User fill:#2ecc71,stroke:#27ae60,stroke-width:2px,color:#fff
    style L2 fill:#9b59b6,stroke:#8e44ad,stroke-width:2px,color:#fff
    style FinalOut fill:#e67e22,stroke:#d35400,stroke-width:2px,color:#fff
