# 🎨 المخططات المعمارية — Cyber Diaries (arc42)

## 1. System Context Diagram (C4 Level 1)

```mermaid
C4Context
    title System Context — Cyber Diaries
    
    Person(learner, "المتعلّم", "طالب حاسبات / مهتم بالأمن السيبراني")
    Person(admin_content, "مسؤول المحتوى", "يضيف دروس وسيناريوهات")
    Person(admin_ops, "مسؤول التشغيل", "يدير المعامل والحاويات")
    Person(admin_release, "مسؤول الإصدار", "يحدّث قواعد التقييم والنقاط")
    Person(supervisor, "المشرف الأكاديمي", "يراجع ويعتمد")

    System(cyber_diaries, "منصة يوميات سايبر", "منصة عربية تفاعلية لتعليم دورة التعامل مع المشكلة الأمنية")

    System_Ext(owasp, "OWASP References", "Top 10:2025 · WSTG · Cheat Sheets")
    System_Ext(video_src, "مصدر فيديو خارجي", "فيديو تعليمي مدمج")
    System_Ext(ethics_committee, "لجنة أخلاقيات البحث", "اعتماد الموافقة والاحتفاظ")

    Rel(learner, cyber_diaries, "يتعلم ويختبر", "HTTPS")
    Rel(admin_content, cyber_diaries, "يدير المحتوى", "HTTPS")
    Rel(admin_ops, cyber_diaries, "يدير المعامل", "HTTPS")
    Rel(admin_release, cyber_diaries, "يحدّث الإعدادات", "HTTPS")
    Rel(supervisor, cyber_diaries, "يراجع النتائج", "عرض فقط")
    Rel(cyber_diaries, owasp, "مراجع خارجية", "روابط")
    Rel(cyber_diaries, video_src, "فيديو مدمج", "Iframe/Embed")
    Rel(cyber_diaries, ethics_committee, "تقارير الامتثال", "وثائق")
```

---

## 2. Container Diagram (C4 Level 2)

```mermaid
C4Container
    title Container Diagram — Cyber Diaries
    
    Person(learner, "المتعلّم")
    Person(admin, "الأدوار الإدارية")

    Container_Boundary(trusted_zone, "المنطقة الموثوقة — Windows Host") {
        Container(frontend, "Frontend", "Next.js 14 / React", "صفحات التعلم · اللابات · السرد · اليوميات · لوحة الصدارة")
        Container(api, "Platform API", "ASP.NET Core (.NET 10)", "Modular Monolith — 7 وحدات")
        ContainerDb(db, "PostgreSQL 16", "قاعدة بيانات", "المستخدمون · المحتوى · الجلسات · النتائج · النقاط · AuditLog")
        Container(worker, "Background Worker", ".NET Hosted Service", "Container Reaper · المهام المؤجلة · تنظيف الجلسات")
    }

    Container_Boundary(untrusted_zone, "المنطقة غير الموثوقة — VirtualBox VM (Ubuntu)") {
        Container(lab_service, "Lab Service", ".NET / REST API", "إدارة دورة حياة الحاويات — المالك الوحيد لـ Docker Socket")
        Container(docker_engine, "Docker Engine", "Linux Containers", "تشغيل حاويات المعمل المعزولة")
        Container(ttyd, "ttyd", "Web Terminal", "طرفية ويب عبر WSS")
        Container(lab_container, "Lab Container", "Ubuntu + أدوات", "البيئة المعزولة للمتعلم")
    }

    Container_Ext(registry, "Container Registry", "Docker Hub / Local", "صور الحاويات المثبتة بـ Digest")

    Rel(learner, frontend, "يستخدم", "HTTPS / WSS")
    Rel(admin, frontend, "يدير", "HTTPS")
    Rel(frontend, api, "REST/JSON", "HTTPS · /api/v1")
    Rel(api, db, "قراءة/كتابة", "TCP · PostgreSQL Wire")
    Rel(api, worker, "مهام مؤجلة", "In-process / Queue")
    Rel(worker, lab_service, "تنظيف حاويات", "REST · Control Channel")
    Rel(api, lab_service, "بدء/إيقاف جلسة", "REST · Control Channel · Token")
    Rel(lab_service, docker_engine, "إنشاء/تدمير حاوية", "Docker Socket")
    Rel(docker_engine, lab_container, "يشغّل", "Namespaces · Cgroups")
    Rel(frontend, ttyd, "طرفية المعمل", "WSS · Per-session Token")
    Rel(ttyd, lab_container, "أوامر/مخرجات", "PTY")
    Rel(registry, docker_engine, "سحب الصور", "HTTPS · Digest-pinned")
```

---

## 3. Component Diagram — الوحدات السبعة (C4 Level 3)

```mermaid
C4Component
    title Component Diagram — Platform API (Modular Monolith)
    
    Container_Boundary(api, "Platform API — ASP.NET Core") {
        Component(identity, "Identity", "وحدة الحسابات والمصادقة", "إنشاء حساب · تسجيل دخول · JWT · RBAC")
        Component(learning, "LearningContent", "وحدة المحتوى التعليمي", "فئات · دروس · مشاهد · اختبارات · فيديو")
        Component(labs, "Labs", "وحدة إدارة المعامل", "جلسات · مهام · أدوات · دورة حياة")
        Component(assessment, "Assessment", "وحدة التقييم والتحقق", "قواعد تحقق · نتائج · تغذية راجعة")
        Component(progress, "Progress", "وحدة التتبع والتقدم", "حالة · نسب إكمال · BehaviorEvent")
        Component(gamification, "Gamification", "وحدة النقاط والإنجازات", "نقاط · مضاعفات · شارات · لوحة صدارة")
        Component(admin, "Administration", "وحدة الإدارة والإصدار", "إدارة محتوى · إعدادات · إصدارات")
    }

    ContainerDb(db, "PostgreSQL 16")
    Container(lab_svc, "Lab Service", "خارج الـ Monolith")

    Rel(identity, db, "User · Account")
    Rel(learning, db, "LearningCategory · Lesson · NarrativeScene · QuizQuestion")
    Rel(labs, db, "LabSession · LabTask · LabTool")
    Rel(assessment, db, "Evidence · VerificationResult")
    Rel(progress, db, "Progress · BehaviorEvent")
    Rel(gamification, db, "PointTransaction · Achievement")
    Rel(admin, db, "إعدادات · سجل حالة")
    Rel(labs, lab_svc, "بدء/إيقاف جلسة", "REST · Control Channel")
    Rel(assessment, labs, "نتائج التحقق")
    Rel(gamification, progress, "حالة الإكمال")
    Rel(admin, learning, "إدارة المحتوى")
    Rel(learning, labs, "ربط الفئة بالمعمل")
```

---

## 4. خريطة اعتماديات الوحدات

```mermaid
flowchart TD
    subgraph modules["الوحدات السبع + Analytics (مقترح)"]
        ID["Identity"]
        LC["LearningContent"]
        LAB["Labs"]
        AS["Assessment"]
        PR["Progress"]
        GM["Gamification"]
        AD["Administration"]
        AN["Analytics<br/>(مقترح — Read-only)"]
    end

    ID --> LC
    ID --> LAB
    ID --> AS
    ID --> PR
    ID --> GM
    ID --> AD
    
    LC --> LAB
    LAB --> AS
    AS --> PR
    PR --> GM
    AD --> LC
    
    AN -.->|"يقرأ فقط"| PR
    AN -.->|"يقرأ فقط"| AS
    AN -.->|"يقرأ فقط"| GM

    style ID fill:#e74c3c,color:#fff
    style AN fill:#f39c12,color:#fff,stroke-dasharray: 5 5
```

---

## 5. Deployment View — البنية الفيزيائية

```mermaid
flowchart TB
    subgraph laptop["💻 اللابتوب الوحيد — Ryzen 7 · 16GB RAM · Windows 11"]
        subgraph windows["Windows Host — المنطقة الموثوقة"]
            W_IDE["IDE + AI Agents<br/>~3-4 GB"]
            W_BROWSER["Browser<br/>~1-2 GB"]
            W_PLATFORM["Platform<br/>Next.js + ASP.NET Core + PostgreSQL<br/>~2-3 GB"]
            W_WORKER["Background Worker<br/>~0.5 GB"]
        end
        
        subgraph vm["VirtualBox VM (Ubuntu) — المنطقة غير الموثوقة ~4-5 GB"]
            VM_LAB["Lab Service<br/>.NET REST API"]
            VM_DOCKER["Docker Engine"]
            VM_TTYD["ttyd (WSS)"]
            
            subgraph containers["حاويات المعمل (1-2 متزامنة · 1.5GB لكل حاوية)"]
                C1["🔴 Red Workspace<br/>Terminal · curl · nmap"]
                C2["🎯 Target App<br/>.NET · PostgreSQL"]
                C3["🔵 Blue/Dev Workspace<br/>grep · tail · Monaco · Adminer"]
            end
            
            VM_NET["Private Docker Network<br/>--internal · No Egress"]
        end
        
        CTRL["Control Channel<br/>REST + Session Token"]
    end

    LEARNER["👤 المتعلّم<br/>(متصفح خارجي)"]

    LEARNER -->|"HTTPS"| W_PLATFORM
    LEARNER -->|"WSS (Proxy)"| VM_TTYD
    W_PLATFORM -->|"REST/JSON"| CTRL
    CTRL --> VM_LAB
    W_WORKER -->|"Cleanup"| CTRL
    VM_LAB --> VM_DOCKER
    VM_DOCKER --> containers
    VM_DOCKER --> VM_NET
    VM_TTYD --> C1
    VM_TTYD --> C3

    style vm fill:#1a1a2e,stroke:#e74c3c,stroke-width:2px
    style windows fill:#0d1b2a,stroke:#2ecc71,stroke-width:2px
    style containers fill:#2d2d44,stroke:#f39c12
```

---

## 6. Trust Boundaries & Security Zones

```mermaid
flowchart TB
    subgraph Z0["🌐 Zone 0 — External (Untrusted)"]
        BROWSER["متصفح المتعلّم"]
        REGISTRY["Container Registry"]
        VIDEO["مصدر فيديو خارجي"]
    end

    subgraph Z1["🟢 Zone 1 — Trusted (Windows Host)"]
        FRONTEND["Next.js Frontend"]
        API["Platform API<br/>(Modular Monolith)"]
        DB[("PostgreSQL<br/>+ AuditLog")]
        WORKER["Background Worker"]
    end

    subgraph Z2["🟡 Zone 2 — Semi-Trusted (Ubuntu VM)"]
        LAB_SVC["Lab Service"]
        DOCKER["Docker Engine"]
        TTYD["ttyd"]
    end

    subgraph Z3["🔴 Zone 3 — Untrusted (Lab Containers)"]
        CONTAINER["حاوية المعمل<br/>(كود المتعلّم · أدوات)"]
    end

    BROWSER -->|"TB-01: HTTPS + JWT"| FRONTEND
    BROWSER -->|"TB-01b: WSS + Session Token"| TTYD
    REGISTRY -->|"TB-07: Digest-pinned Images"| DOCKER
    VIDEO -->|"TB-08: Iframe Embed"| FRONTEND
    
    FRONTEND -->|"TB-02: REST/JSON + Auth"| API
    API -->|"TB-03: TCP + Least Privilege"| DB
    WORKER -->|"TB-03b: Internal"| DB
    
    API -->|"TB-04: Control Channel + Token"| LAB_SVC
    WORKER -->|"TB-04b: Cleanup Commands"| LAB_SVC
    
    LAB_SVC -->|"TB-05: Docker Socket (exclusive)"| DOCKER
    DOCKER -->|"TB-06: Namespaces + Cgroups"| CONTAINER
    TTYD -->|"TB-06b: PTY + Token"| CONTAINER

    style Z0 fill:#1a1a2e,stroke:#666
    style Z1 fill:#0d2818,stroke:#2ecc71,stroke-width:3px
    style Z2 fill:#2d2000,stroke:#f39c12,stroke-width:2px
    style Z3 fill:#2d0000,stroke:#e74c3c,stroke-width:2px
```

---

## 7. Runtime View — سيناريو بدء جلسة المعمل

```mermaid
sequenceDiagram
    participant L as المتعلّم
    participant FE as Frontend (Next.js)
    participant API as Platform API
    participant DB as PostgreSQL
    participant LS as Lab Service
    participant DK as Docker Engine
    participant CT as Lab Container

    L->>FE: اختيار فئة + دور + صعوبة
    FE->>API: POST /api/v1/lab/sessions
    API->>DB: التحقق من الحساب + الصلاحيات
    DB-->>API: ✅ حساب صالح
    API->>DB: فحص السعة (≤ 2 جلسة نشطة)
    alt السعة ممتلئة
        DB-->>API: ❌ لا سعة
        API-->>FE: 429 Queue Position
        FE-->>L: "أنت في الطابور — المركز 3"
    else سعة متاحة
        API->>DB: إنشاء LabSession (Pending)
        API->>LS: POST /control/sessions (Token)
        LS->>DK: docker create --cap-drop=ALL --memory=1.5g
        DK->>CT: إنشاء حاوية معزولة
        LS->>DK: docker start
        DK-->>LS: Container Running
        LS-->>API: ✅ Session Ready (endpoint + token)
        API->>DB: تحديث الحالة → Active
        API-->>FE: Session URL + WSS Token
        FE-->>L: فتح واجهة المعمل + الطرفية
    end

    Note over CT: المتعلّم ينفذ أوامر بحرية داخل الحاوية
    Note over DK: لا egress · لا host mounts · لا privileged
```

---

## 8. Runtime View — سيناريو التحقق الآلي واحتساب النقاط

```mermaid
sequenceDiagram
    participant L as المتعلّم
    participant FE as Frontend
    participant API as Platform API
    participant AS as Assessment Module
    participant GM as Gamification Module
    participant DB as PostgreSQL

    L->>FE: تسليم الحل / إتمام المهمة
    FE->>API: POST /api/v1/assessment/submit
    API->>DB: التحقق من ملكية الجلسة
    API->>AS: تقييم الحل حسب الدور
    
    alt دور Red Team
        AS->>AS: التحقق من النتيجة الأمنية المكتشفة
    else دور Blue Team
        AS->>AS: التحقق من سلسلة الاستنتاج (2-3 خطوات)
    else دور Developer
        AS->>AS: تشغيل الاختبارات الآلية على الكود المُصلح
    end

    AS->>DB: حفظ VerificationResult (immutable)
    
    alt نجاح التحقق
        AS->>GM: احتساب النقاط (Multiplier حسب الصعوبة)
        GM->>DB: INSERT PointTransaction (SourceId = idempotent)
        GM->>DB: فحص الإنجازات (Achievement unlock)
        GM-->>API: ✅ Points Awarded
        API-->>FE: نتيجة + تغذية راجعة + نقاط
        FE-->>L: 🎉 نجاح + عرض النقاط
    else فشل التحقق
        AS-->>API: ❌ Failed + Feedback
        API-->>FE: تغذية راجعة تعليمية
        FE-->>L: شرح الخطأ + إمكانية إعادة المحاولة
    end
```

---

## 9. Runtime View — سيناريو انتهاء الجلسة والتدمير

```mermaid
sequenceDiagram
    participant T as Timer / User
    participant FE as Frontend
    participant API as Platform API
    participant WK as Background Worker
    participant LS as Lab Service
    participant DK as Docker Engine
    participant DB as PostgreSQL

    alt انتهاء المهلة (60/120 دقيقة)
        T->>API: Session Timeout Event
    else المستخدم أغلق الجلسة
        T->>FE: "إنهاء الجلسة"
        FE->>API: DELETE /api/v1/lab/sessions/{id}
    else انقطاع الاتصال
        T->>WK: Heartbeat Missing (Grace Period)
    end

    API->>DB: تحديث الحالة → Expired/Completed
    API->>LS: POST /control/sessions/{id}/destroy
    LS->>DK: docker stop + docker rm
    DK->>DK: تدمير الحاوية + مسح الملفات المؤقتة
    DK-->>LS: ✅ Container Destroyed
    LS-->>API: Confirmation
    API->>DB: تحديث الحالة → Destroyed
    API->>DB: INSERT AuditLog (session_end)
    API-->>FE: الجلسة انتهت
    FE-->>L: عودة للوحة البداية + عرض النتائج

    Note over WK: Reaper يفحص دوريًا الحاويات اليتيمة
    WK->>LS: GET /control/sessions?status=orphan
    LS->>DK: تنظيف أي حاوية بلا جلسة نشطة
```

---

## 10. Data Model — ERD مبسط

```mermaid
erDiagram
    User ||--|| Account : "1:1"
    User ||--o{ LabSession : "يملك"
    User ||--o{ JournalEntry : "يكتب"
    User ||--o{ Progress : "لديه"
    User ||--o{ PointTransaction : "يكتسب"
    User ||--o{ Achievement : "يفتح"
    User ||--o{ BehaviorEvent : "يولّد"

    LearningCategory ||--o{ Lesson : "تحتوي"
    LearningCategory ||--o{ NarrativeScene : "تحتوي"
    LearningCategory ||--o{ LabTask : "تحتوي"
    LearningCategory ||--o{ Progress : "تُقاس"

    Lesson ||--o{ ExternalResource : "تتضمن"
    Lesson ||--o{ QuizQuestion : "تتضمن"

    LabSession ||--|| LabTask : "تنفذ"
    LabSession ||--o{ VerificationResult : "تنتج"
    LabSession ||--o{ Evidence : "تجمع"
    LabSession ||--o| JournalEntry : "تليها"

    LabTask ||--o{ LabTool : "تستخدم"

    NarrativeScene ||--o{ ContinuityEntry : "تُوثق"

    User {
        int UserId PK
        string DisplayName
        bool IsHidden
        datetime CreatedAt
    }

    Account {
        string Username PK
        string PasswordHash
        string Role
    }

    LabSession {
        int SessionId PK
        string Difficulty
        string SelectedRole
        datetime StartedAt
        datetime ExpiresAt
        string Status
    }

    VerificationResult {
        int ResultId PK
        bool Passed
        string Feedback
        datetime CheckedAt
    }

    PointTransaction {
        int TransactionId PK
        int Points
        float Multiplier
        string SourceId
        datetime CreatedAt
    }

    JournalEntry {
        int EntryId PK
        text WhatHappened
        text WhyHappened
        text WhatIDid
        text WhatILearned
        datetime SavedAt
    }

    BehaviorEvent {
        int EventId PK
        string EventType
        string TargetRef
        datetime Timestamp
    }
```

---

## 11. Lab Session State Machine

```mermaid
stateDiagram-v2
    [*] --> Requested: المستخدم يطلب جلسة
    Requested --> Provisioning: فحص الصلاحيات + السعة
    Provisioning --> Ready: الحاوية جاهزة (< 90s)
    Provisioning --> Failed: فشل الإنشاء
    Ready --> Active: المتعلّم يبدأ التفاعل
    Active --> Verifying: تسليم الحل
    Verifying --> Completed: نجاح/فشل التحقق
    Active --> Expired: انتهاء المهلة (60/120 دقيقة)
    Completed --> Destroying: حفظ النتائج
    Expired --> Destroying: حفظ ما تحقق
    Failed --> Cleanup: تنظيف جزئي
    Destroying --> Destroyed: docker rm + مسح
    Cleanup --> Destroyed
    Destroyed --> [*]

    note right of Active
        المتعلّم ينفذ أوامر
        داخل الحاوية المعزولة
    end note

    note right of Failed
        تسجيل الخطأ
        + إشعار المستخدم
        + عدم احتساب نقاط
    end note
```

---

## 12. Security Controls per Trust Boundary

```mermaid
flowchart LR
    subgraph TB01["TB-01: Browser → Platform"]
        S1["HTTPS/TLS 1.3"]
        S2["JWT in HttpOnly Cookie"]
        S3["Rate Limiting (100 req/min)"]
        S4["CSRF Token"]
    end

    subgraph TB02["TB-02: Frontend → API"]
        S5["REST/JSON · /api/v1"]
        S6["Input Validation (FluentValidation)"]
        S7["ProblemDetails (RFC 7807)"]
    end

    subgraph TB03["TB-03: API → Database"]
        S8["Least Privilege DB Role"]
        S9["Parameterized Queries (EF Core)"]
        S10["Bound to localhost"]
        S11["Encryption at Rest"]
    end

    subgraph TB04["TB-04: API → Lab Service"]
        S12["Control Channel (REST)"]
        S13["Per-session Token"]
        S14["Operation Allowlist"]
        S15["Host-only Network"]
    end

    subgraph TB05["TB-05: Lab Service → Docker"]
        S16["Sole Socket Holder"]
        S17["--cap-drop=ALL"]
        S18["no-new-privileges"]
        S19["Read-only rootfs"]
        S20["Seccomp + AppArmor"]
    end

    subgraph TB06["TB-06: Container → Host"]
        S21["No shared folders"]
        S22["No clipboard"]
        S23["No drag-and-drop"]
        S24["NAT + Host-only"]
        S25["Snapshots before sessions"]
    end

    TB01 --> TB02 --> TB03
    TB02 --> TB04 --> TB05 --> TB06

    style TB01 fill:#0d2818,stroke:#2ecc71
    style TB02 fill:#0d2818,stroke:#2ecc71
    style TB03 fill:#0d2818,stroke:#2ecc71
    style TB04 fill:#2d2000,stroke:#f39c12
    style TB05 fill:#2d0000,stroke:#e74c3c
    style TB06 fill:#2d0000,stroke:#e74c3c
```

---

## 13. User Journey — المسارين

```mermaid
flowchart TD
    START(["🏠 الصفحة الرئيسية"])
    START --> AUTH{"تسجيل / دخول"}
    AUTH --> DASH["📋 لوحة البداية"]
    
    DASH --> PATH_CHOICE{"اختيار المسار"}
    
    PATH_CHOICE -->|"مسار التعلّم"| LEARN_PATH
    PATH_CHOICE -->|"مسار اللابات"| LAB_PATH

    subgraph LEARN_PATH["📚 مسار التعلّم"]
        L1["اختيار فئة (10 فئات)"]
        L2["🎬 مشهد قصصي (قبل التوظيف)"]
        L3["📖 شرح تقني مكتوب"]
        L4["🎥 فيديو خارجي مدمج"]
        L5["❓ اختبار قصير (3-5 أسئلة)"]
        L6["🔗 رابط إلى المعمل"]
        
        L1 --> L2
        L2 -->|"تخطي"| L2B["ملخص مكافئ"]
        L2 --> L3
        L2B --> L3
        L3 --> L4
        L4 --> L5
        L5 -->|"فحص ذاتي — ليس بوابة"| L6
    end

    subgraph LAB_PATH["🔬 مسار اللابات"]
        P1["اختيار فئة"]
        P2["🎬 افتتاحية اللاب (~1.5 د)"]
        P3["اختيار الصعوبة"]
        P4["اختيار الدور"]
        
        P1 --> P2
        P2 -->|"تخطي"| P2B["ملخص سياقي"]
        P2 --> P3
        P2B --> P3
        P3 --> P4
    end

    P4 --> ROLE_CHOICE{"الدور المختار"}
    
    ROLE_CHOICE -->|"Red Team"| RED["🔴 اكتشاف المشكلة"]
    ROLE_CHOICE -->|"Blue Team"| TRANS_B["🎬 مشهد انتقال"]
    ROLE_CHOICE -->|"Developer"| TRANS_D["🎬 مشهد انتقال"]
    
    TRANS_B --> BLUE["🔵 التحقيق والتحليل"]
    TRANS_D --> DEV["🟢 الإصلاح والتحقق"]

    RED --> VERIFY["⚙️ التحقق الآلي"]
    BLUE --> VERIFY
    DEV --> VERIFY

    VERIFY -->|"نجاح"| JOURNAL["📝 اليوميات (اختياري)"]
    VERIFY -->|"فشل"| FEEDBACK["💬 تغذية راجعة"]
    FEEDBACK -->|"إعادة محاولة"| P4

    JOURNAL --> PROGRESS["📊 التقدم + النقاط"]
    L6 --> LAB_PATH

    PROGRESS --> DASH

    style LEARN_PATH fill:#0a192f,stroke:#64ffda
    style LAB_PATH fill:#1a0a2e,stroke:#bb86fc
    style VERIFY fill:#2d1b00,stroke:#ff9800
```

---

## 14. Threat Model — STRIDE Matrix

```mermaid
mindmap
  root((Cyber Diaries<br/>Threat Model))
    Spoofing
      انتحال جلسة متعلّم
      انتحال دور إداري
      تزوير Session Token
    Tampering
      تعديل النقاط من المتصفح
      تلاعب بنتيجة التحقق
      تعديل Evidence بعد الإنشاء
      حقن SQL في المنصة
    Repudiation
      إنكار تنفيذ أمر في المعمل
      غياب سجل تدقيق
    Information Disclosure
      تسريب بيانات متعلّم آخر
      قراءة ملفات Host من الحاوية
      تسريب Connection Strings
      كشف أسئلة الاختبار
    Denial of Service
      Fork Bomb في الحاوية
      استهلاك كل RAM
      طلبات مزامنة مفرطة
    Elevation of Privilege
      Container Escape
      VM Escape
      Kernel Exploit
      الحصول على Docker Socket
```

---

## 15. Quality Attribute Scenarios

```mermaid
quadrantChart
    title أولوية خصائص الجودة
    x-axis "أقل أهمية" --> "أكثر أهمية"
    y-axis "سهل التحقيق" --> "صعب التحقيق"
    
    Security: [0.95, 0.7]
    Correctness: [0.9, 0.5]
    Simplicity: [0.75, 0.3]
    Testability: [0.7, 0.45]
    Performance: [0.55, 0.6]
    Reliability: [0.5, 0.5]
    Observability: [0.45, 0.35]
```

---

## 16. Release Roadmap

```mermaid
gantt
    title خارطة الإصدارات — Cyber Diaries
    dateFormat YYYY-MM
    axisFormat %Y-%m

    section المرحلة 1-3
    التحليل والتصميم والهيكل الأساسي    :done, p1, 2026-10, 2026-12
    
    section المرحلة 4
    التجارب التقنية الحرجة (Lab Spike)   :active, p4, 2027-01, 2027-01
    
    section المرحلة 5
    النموذج التجريبي v0.1 (Injection)    :p5, 2027-02, 2027-02
    
    section المرحلة 6
    القياس مع المستخدمين (5-10 طلاب)     :p6, 2027-03, 2027-03
    
    section المرحلة 7
    التعميم المشروط v0.2                 :p7, 2027-04, 2027-05
    
    section نافذة التثبيت
    Code Freeze + QA                     :crit, qa, 2027-05, 2027-06
    
    section المرحلة 8
    التوثيق والتسليم v1.0               :p8, 2027-06, 2027-07
    
    section المناقشة
    التسليم النهائي                      :milestone, final, 2027-07, 0d
```

---

## 17. Container Hardening Checklist

```mermaid
flowchart TD
    subgraph hardening["🔒 تحصين الحاوية — كل جلسة"]
        H1["--cap-drop=ALL"]
        H2["--security-opt no-new-privileges"]
        H3["--read-only + tmpfs /tmp"]
        H4["--memory=1.5g --memory-swap=1.5g"]
        H5["--cpus=1 --pids-limit=256"]
        H6["--network=internal (no egress)"]
        H7["--user 1000:1000 (non-root)"]
        H8["seccomp=default"]
        H9["apparmor=docker-default"]
        H10["لا host mounts · لا /var/run/docker.sock"]
        H11["Image pinned by digest"]
        H12["Auto-destroy on session end"]
    end

    H1 --> RESULT["✅ حاوية معزولة آمنة"]
    H2 --> RESULT
    H3 --> RESULT
    H4 --> RESULT
    H5 --> RESULT
    H6 --> RESULT
    H7 --> RESULT
    H8 --> RESULT
    H9 --> RESULT
    H10 --> RESULT
    H11 --> RESULT
    H12 --> RESULT

    style RESULT fill:#0d2818,stroke:#2ecc71,stroke-width:3px
```

---

## 18. Assessment Flow per Role

```mermaid
flowchart LR
    subgraph red["🔴 Red Team"]
        R1["استكشاف التطبيق"] --> R2["تحديد نقطة الاشتباه"]
        R2 --> R3["إثبات الثغرة بأمان"]
        R3 --> R4["تقديم الدليل"]
    end

    subgraph blue["🔵 Blue Team"]
        B1["فحص السجلات"] --> B2["تحديد الطلب المشبوه"]
        B2 --> B3["ربط الأحداث زمنيًا"]
        B3 --> B4["استنتاج النشاط + المورد"]
    end

    subgraph dev["🟢 Developer"]
        D1["قراءة تقرير الحادث"] --> D2["تحديد السبب الجذري"]
        D2 --> D3["تعديل الكود"]
        D3 --> D4["تشغيل الاختبارات الآلية"]
    end

    R4 --> V["⚙️ التحقق الآلي (الخادم)"]
    B4 --> V
    D4 --> V

    V -->|"نجاح"| SUCCESS["✅ نقاط + تقدم + يومية"]
    V -->|"فشل"| RETRY["🔄 تغذية راجعة + إعادة محاولة"]

    style red fill:#2d0000,stroke:#e74c3c
    style blue fill:#001a33,stroke:#3498db
    style dev fill:#002200,stroke:#2ecc71
    style V fill:#2d2000,stroke:#f39c12
```

---

> 💡 **ملاحظة:** كل هذه المخططات بصيغة **Mermaid** ويمكن عرضها في أي أداة تدعمها (GitHub, VS Code + extension, Notion, Obsidian, أو [mermaid.live](https://mermaid.live)). هل تريد تصديرها كصور، أو تعديل أي مخطط، أو إضافة مخططات إضافية لأقسام معينة؟