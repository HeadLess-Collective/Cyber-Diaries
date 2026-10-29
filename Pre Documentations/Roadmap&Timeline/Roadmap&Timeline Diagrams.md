```mermaid
gantt
    title Roadmap and Timeline - Cyber Diaries
    dateFormat YYYY-MM-DD
    axisFormat %Y-%m

    section Anchors
    SRS v0.1 Start :milestone, m_start, 2026-10-26, 0d
    Final Submission Month :milestone, m_final, 2027-07-15, 0d

    section Immediate
    First 7 Days Hardening :crit, imm, 2026-10-26, 7d
    OI-013 Team Count :active, oi013, 2026-10-26, 7d
    OI-007 Hosting Provider :active, oi007, 2026-10-26, 7d
    OI-011 Input Policy :active, oi011, 2026-10-26, 7d
    Timesheet Starts :done, ts, 2026-10-26, 1d

    section Phases
    Phase 1 Foundation :p1, 2026-11-02, 24d
    Phase 2 Content Story Ethics :p2, 2026-11-26, 30d
    Phase 3 Structure API :p3, 2026-12-26, 31d
    Phase 4 Lab Critical Experiments :p4, 2027-01-26, 31d
    Phase 5 Pilot Episode :p5, 2027-02-26, 28d
    Phase 6 Measurement :p6, 2027-03-26, 31d
    Phase 7 Stabilization :p7, 2027-04-26, 35d
    Phase 8 Freeze Docs Submission :p8, 2027-06-01, 45d

    section Gates
    Gate 01 SRS Approved :milestone, g1, 2026-10-26, 0d
    Gate 02 Content Ready :milestone, g2, 2026-12-25, 0d
    Gate 03 Lab Isolation Passed :milestone, g3, 2027-02-25, 0d
    Gate 04 Episode Measured :milestone, g4, 2027-04-25, 0d
    Gate 05 Release Candidate :milestone, g5, 2027-05-31, 0d

    section Freeze
    Code Freeze Window :crit, cf, 2027-05-17, 14d
    Template Freeze :milestone, tf, 2027-06-15, 0d
    World Bible Freeze :milestone, wb, 2027-06-15, 0d

    section Releases
    v0.1 Pilot :milestone, r1, 2027-02-25, 0d
    v0.2 Stabilized :milestone, r2, 2027-05-31, 0d
    v1.0 Final :milestone, r3, 2027-07-15, 0d

    section Open Issues
    OI-001 Ethics Protocol :oi001, 2026-11-26, 30d
    OI-004 Consent Form :oi004, 2026-11-26, 30d
    OI-014 External Video :oi014, 2026-11-26, 30d
    OI-009 Retention Delete :oi009, 2026-12-26, 31d
    OI-010 Password Change :oi010, 2026-12-26, 31d
    OI-008 Tool Versions :oi008, 2027-01-26, 31d
    D14 Licenses Register :d14, 2027-01-26, 31d
    Plan B Isolation :planb, 2027-01-26, 31d
    OI-003 Ethics Approval :oi003, 2027-02-26, 60d
    OI-012 Retention Durations :oi012, 2027-02-26, 60d
    OI-015 Study Protocol :oi015, 2027-02-26, 60d
    OI-002 D12 Devices :oi002, 2027-04-26, 75d
    OI-005 WCAG Accessibility :oi005, 2027-04-26, 75d
    OI-006 Defense Committee :oi006, 2027-04-26, 75d
```

```mermaid
flowchart TD
  S0(["26-10-2026 · SRS v0.1 · نقطة الانطلاق"])
  META["16 نود رئيسية + 30 نود متفرعة · 5 بوابات · 4 فرق · ميزانية 0"]
  S0 --- META

  G01{"Gate 01 · اعتماد مواصفة المتطلبات"}
  S0 --> G01

  subgraph IMM["خطة التحرك الفوري — أول 7 أيام"]
    IMM1["اجتماع حسم سريع 60 دقيقة"]
    IMM2["OI-013 · تثبيت عدد الفريق"]
    IMM3["OI-007 · مزود النشر والاستضافة"]
    IMM4["OI-011 · سياسة صحة المدخلات"]
    IMM5["بدء جدول الساعات الفعلية من اليوم الأول"]
    IMM1 --> IMM2 --> IMM3 --> IMM4 --> IMM5
  end

  G01 --> IMM1
  IMM5 --> P1_1

  subgraph P1["المرحلة 1 — التأسيس وتحليل التجربة (أكتوبر 2026)"]
    P1_1["تحليل الجمهور والرحلات وتصميم تجربة المستخدم"]
    P1_2["تثبيت النطاق · حلقة Injection واحدة متكاملة وفق OWASP Top 10:2025 الرسمي D15"]
    P1_3["تعريف المسارين · التعلم واللابات · مسار مبسّط مستقل D8 · الدخول لأي مسار مباشرة BR-09"]
    P1_4["متطلبات العزل والأمان المبدئية"]
    P1_1 --> P1_2 --> P1_3 --> P1_4
  end

  P1_4 --> P2_1

  subgraph P2["المرحلة 2 — المحتوى والقصة والأخلاقيات (نوفمبر 2026)"]
    P2_1["اختيار سيناريو SQL Injection للحلقة الأولى"]
    P2_2["كتابة الشرح التقني بأركانه الخمسة"]
    P2_3["المشاهد القصصية قبل التوظيف وداخل نور تك · تحديث World Bible"]
    P2_4["OI-001 · تقديم بروتوكول الأخلاقيات"]
    P2_5["OI-004 · نموذج الموافقة المستنيرة"]
    P2_6["OI-014 · اعتماد الفيديو والمصادر الخارجية"]
    P2_1 --> P2_2 --> P2_3 --> P2_4 --> P2_5 --> P2_6
  end

  P2_6 --> G02{"Gate 02 · جاهزية المحتوى والسيناريو وملف الأخلاقيات"}
  G02 --> P3_1

  subgraph P3["المرحلة 3 — الهيكل الأساسي وعقود API (ديسمبر 2026)"]
    P3_1["CN-018 · تجميد Swagger/OpenAPI في الأسبوع الأول"]
    P3_2["Backend · .NET 10 Modular Monolith بوحدات 7"]
    P3_3["Database · PostgreSQL 16 + Identity + Progress"]
    P3_4["Frontend · Next.js 14 + RTL + لوحة البداية"]
    P3_5["OI-009 · سياسة الحذف والاحتفاظ D11"]
    P3_6["OI-010 · قرار تغيير كلمة المرور FR-007"]
    P3_7["Mock Servers + اختبارات تكامل أسبوعية"]
    P3_1 --> P3_2 --> P3_3 --> P3_4 --> P3_5 --> P3_6 --> P3_7
  end

  P3_7 --> P3OUT["مخرج المرحلة 3 · هيكل المنصة وعقود API مستقرة"]
  P3OUT --> P4_1

  subgraph P4["المرحلة 4 — التجارب الحرجة للمعمل (يناير 2027)"]
    P4_1["حاوية Docker مؤقتة معزولة شبكيًا"]
    P4_2["ttyd عبر WebSockets داخل المتصفح"]
    P4_3["Monaco Editor + Adminer + curl/nmap عند الحاجة"]
    P4_4["تطبيق وهمي يحتوي ثغرة SQL Injection"]
    P4_5["Container Reaper + تدمير تلقائي بعد الجلسة"]
    P4_6["اختبار عزل الشبكة + D3 · 60/120 دقيقة + 10 متزامنين + 2GB RAM"]
    P4_7["OI-008 · تثبيت إصدارات الأدوات D17b"]
    P4_8["D14 · سجل التراخيص قبل النشر"]
    P4_9["Plan B لعزل الحاويات"]
    P4_1 --> P4_2 --> P4_3 --> P4_4 --> P4_5 --> P4_6 --> P4_7 --> P4_8 --> P4_9
  end

  P4_9 --> G03{"Gate 03 · أمان المعمل والعزل مجتازان عبر IM-006"}
  G03 --> P5_1

  subgraph P5["المرحلة 5 — الحلقة التجريبية v0.1 (فبراير 2027)"]
    P5_1["مسار التعلم · مشهد قصصي · شرح · فيديو خارجي · اختبار MCQ فحص ذاتي لا بوابة BR-01"]
    P5_2["مسار اللاب · مقدمة حادث داخل نور تك · ملخص مكافئ عند التخطي · الصعوبة تحدد التلميحات فقط BR-02 · دخول مباشر أو تجربة كاملة اختيارية"]
    P5_3["Red Team · اكتشاف وإثبات آمن داخل النطاق"]
    P5_4["Blue Team · سلسلة استنتاج حقيقية من خطوتين إلى ثلاث BR-15"]
    P5_5["Developer · إصلاح السبب الجذري + اختبارات آلية"]
    P5_6["اليومية الاختيارية · نقاط خادمية · تتبع التقدم · لوحة صدارة Opt-in D13"]
    P5_7["v0.1 Pilot"]
    P5_1 --> P5_2 --> P5_3 --> P5_4 --> P5_5 --> P5_6 --> P5_7
  end

  P5_7 --> V01["v0.1 Pilot · فبراير 2027"]
  V01 --> P6_1

  subgraph P6["المرحلة 6 — القياس والتجربة الاستطلاعية (مارس 2027)"]
    P6_1["تجربة استطلاعية 5-10 مستخدمين · دراسة n ≥ 10 D16"]
    P6_2["OI-015 · اختبار قبلي/بعدي/مؤجل"]
    P6_3["قياس SUS وعتبات سهولة الاستخدام"]
    P6_4["تحليل BehaviorEvent · التلميحات والوقت والمسارات"]
    P6_5["تحليل اليوميات نوعيًا"]
    P6_6["OI-003 · استلام اعتماد الأخلاقيات أو خطة طوارئ"]
    P6_7["OI-012 · اعتماد مدد الاحتفاظ وسجلات التدقيق"]
    P6_8["حاسبة تكلفة الحلقة الأولى CN-019"]
    P6_1 --> P6_2 --> P6_3 --> P6_4 --> P6_5 --> P6_6 --> P6_7 --> P6_8
  end

  P6_8 --> G04{"Gate 04 · اكتمال الحلقة + أرقام الساعات الفعلية"}
  G04 --> P7_1

  subgraph P7["المرحلة 7 — التثبيت وضمان الجودة (أبريل–مايو 2027)"]
    P7_1["Code Freeze أواخر مايو 2027 لمدة أسبوعين"]
    P7_2["إصلاح العلل · اختبارات الأداء وفق D4 · API بسيط أقل من 500ms · API مركب أقل من 2s · بناء حاوية أقل من 90s · تحقق آلي أقل من 3s"]
    P7_3["اختبار إساءة استخدام موثق IM-006"]
    P7_4["OI-002 · دعم نظام التشغيل والدقة والهاتف D12"]
    P7_5["OI-005 · مراجعة WCAG وإتاحة الوصول D9"]
    P7_6["تعميم فئة ثانية فقط إذا سمح القياس والوقت"]
    P7_1 --> P7_2 --> P7_3 --> P7_4 --> P7_5 --> P7_6
  end

  P7_6 --> V02["v0.2 Stabilized · مايو 2027"]
  V02 --> G05{"Gate 05 · Release Candidate جاهز للتجميد"}
  G05 --> P8_1

  subgraph P8["المرحلة 8 — التجميد والتوثيق والتسليم (يونيو–يوليو 2027)"]
    P8_1["CN-016 · تجميد قوالب المحتوى والسيناريو منتصف يونيو"]
    P8_2["تجميد World Bible وإغلاق التناقضات السردية"]
    P8_3["التوثيق التقني · دليل المستخدم · دليل لوحة الإدارة · إدارة محتوى بلا كود CN-009"]
    P8_4["الدراسة التقييمية + الورقة البحثية"]
    P8_5["OI-006 · تثبيت لجنة المناقشة النهائية"]
    P8_6["v1.0 Final"]
    P8_1 --> P8_2 --> P8_3 --> P8_4 --> P8_5 --> P8_6
  end

  P8_6 --> FIN(["07-2027 · التسليم والمناقشة النهائية · اليوم المحدد TBD"])

  subgraph TEAMS["الفرق ومسؤوليات التسليم"]
    TEAM_SIZE["فريق HEADLESS — 13 عضوًا حسب هذه الخارطة"]
    BUDGET["ميزانية · 0 EGP / 0 USD"]
    TC["المحتوى والسيناريو · يقود P2-A/B/C/D"]
    TB["Backend · يقود P3-A/B/C + P4-C"]
    TF["Frontend & UX · يقود P1-A + P3-D + P6-A/B"]
    TL["Lab & DevOps · يقود P1-C + P4-A/B/D + P5-B/C/D"]
    TEAM_SIZE --- BUDGET
    TEAM_SIZE --- TC
    TEAM_SIZE --- TB
    TEAM_SIZE --- TF
    TEAM_SIZE --- TL
  end

  TC -.-> P2_1
  TB -.-> P3_1
  TF -.-> P3_4
  TL -.-> P4_1

  subgraph RULES["القيود والقواعد الحاكمة"]
    R001["CN-001 · Modular Monolith لا Microservices"]
    R002["CN-002 · فصل خدمة المعمل عن عملية API"]
    R003["CN-003 · تدمير الحاوية بعد الجلسة"]
    R004["CN-004 · منع الأدوات من الخروج عن نطاق المعمل"]
    R005["CN-005 · النقاط والإنجازات في الخادم"]
    R006["CN-006 · REST أولًا ولا GraphQL إلا بحاجة مثبتة"]
    R007["CN-007 · أدوات جاهزة حقيقية لا تُبنى من الصفر"]
    R008["CN-008 · سطح المكتب واجهة تفاعلية فقط"]
    R009["CN-009 · لوحة إدارة المحتوى بلا لمس الكود"]
    R010["CN-010 · التعلم قبل التوظيف واللابات بعد الانضمام"]
    R011["CN-011 · حادثة واحدة لكل فئة يعبّرها الأدوار الثلاثة"]
    R012["CN-012 · محتوى تعليمي دفاعي لا دليل هجوم جاهز"]
    R013["CN-013 · أسماء وشخصيات افتراضية بالكامل"]
    R014["CN-014 · لا معلومات شخصية أو أسرار في السجلات التعليمية"]
    R015["CN-015 · لا يُنشر محتوى خارج إعلان النطاق قبل اعتماد المشرف"]
    R016["CN-016 · تجميد القوالب مخرج رسمي"]
    R017["CN-017 · كلمة الحسم معلنة لقائد المعمارية وقائد المحتوى"]
    R018["CN-018 · عقود API قبل توزيع التنفيذ"]
    R019["CN-019 · لا جدول نهائي قبل قياس الحلقة الأولى"]
    RGOLD["القاعدة الذهبية · يُضحى بعدد الحلقات لا بأمان المعمل ولا بجودة التقييم"]
  end

  R001 -.-> P3_2
  R002 -.-> G03
  R003 -.-> P4_5
  R004 -.-> P4_6
  R005 -.-> P5_6
  R006 -.-> P3_1
  R009 -.-> P8_3
  R010 -.-> P5_1
  R011 -.-> P5_3
  R012 -.-> P2_2
  R013 -.-> P2_3
  R014 -.-> P4_4
  R016 -.-> P8_1
  R017 -.-> TEAM_SIZE
  R018 -.-> P3_1
  R019 -.-> G04
  RGOLD -.-> P7_6

  subgraph RISKS["المخاطر والتحصينات"]
    K1["RK-007 · انهيار عزل المعمل"]
    K2["RK-001 · تضخم النطاق إلى عشر فئات"]
    K3["RK-002 · انزلاق Blue Team إلى حفظ نصوص"]
    K4["RK-003 · كلفة المحتوى المرئي"]
    K5["RK-004 · صعوبة التقييم الآلي"]
    K6["RK-008 · تلاعب النقاط من العميل"]
    K7["RK-011 · تعطل التكامل بين الفرق"]
    K8["RK-005 · فقدان السياق عند الدخول المباشر"]
    K9["RK-009 · جودة العربية والمصطلحات"]
    K10["RK-010 · تناقضات سردية"]

    M1["Spike مبكر · اختبار شبكة · Container Reaper · فصل خدمة المعمل"]
    M2["تجميد النطاق على حلقة Injection واحدة"]
    M3["Rubric · طالب خارجي · سلسلة استنتاج BR-15"]
    M4["قالب مشاهد قصيرة · رابط بديل · النص هو المرجع"]
    M5["Verification في الخادم · SourceId · منع التكرار"]
    M6["عقود API · demo أسبوعي · integration مبكر"]
    M8["ملخص مكافئ · مشهد انتقال · سياق الدور"]
    M9["مراجعة لغوية · فصحى للشروح · عامية للحوارات · مصطلح إنجليزي عند الحاجة"]
    M10["World Bible · مالك واحد · تجميد معلنة"]

    K1 -.-> M1
    K2 -.-> M2
    K3 -.-> M3
    K4 -.-> M4
    K5 -.-> M5
    K6 -.-> M5
    K7 -.-> M6
    K8 -.-> M8
    K9 -.-> M9
    K10 -.-> M10
  end

  M1 -.-> G03
  M2 -.-> P1_2
  M3 -.-> P5_4
  M4 -.-> P2_6
  M5 -.-> P5_6
  M6 -.-> P3_7
  M8 -.-> P5_2
  M9 -.-> P2_2
  M10 -.-> P8_2
```

# خارطة الطريق والجدول الزمني — مشروع يوميات سايبر (Cyber Diaries)
## مخططات Mermaid فقط

---

## 1️⃣ المخطط الزمني الكلي (Gantt Chart)

```mermaid
gantt
    title الجدول الزمني التنفيذي المحصّن — Cyber Diaries (26-10-2026 ← 07-2027)
    dateFormat YYYY-MM-DD
    axisFormat %b-%Y
    excludes weekends
    
    section المراحل الرئيسية
    المرحلة 1 - التحليل وتصميم التجربة      :p1, 2026-10-26, 30d
    المرحلة 2 - المحتوى والأخلاقيات          :p2, 2026-11-25, 30d
    المرحلة 3 - الهيكل وAPI-First           :p3, 2026-12-25, 31d
    المرحلة 4 - التجارب التقنية الحرجة      :p4, 2027-01-25, 31d
    المرحلة 5 - النموذج التجريبي v0.1       :p5, 2027-02-25, 28d
    المرحلة 6 - القياس الميداني             :p6, 2027-03-25, 31d
    المرحلة 7 - التعميم المشروط v0.2       :p7, 2027-04-25, 21d
    نافذة التثبيت وضمان الجودة              :qa, 2027-05-16, 16d
    المرحلة 8 - التوثيق والدراسة الموسعة    :p8, 2027-06-01, 30d
    المناقشة النهائية v1.0                  :milestone, final, 2027-07-01, 0d
    
    section البوابات الحاكمة
    Gate 01 - إقرار النطاق                  :milestone, g1, 2026-11-24, 0d
    Gate 02 - العزل الأمني                  :milestone, g2, 2027-02-24, 0d
    Gate 03 - الأخلاقيات                    :milestone, g3, 2027-03-24, 0d
    Gate 04 - إعلان النطاق المشروط          :milestone, g4, 2027-04-24, 0d
    Gate 05 - تجميد القوالب                 :milestone, g5, 2027-06-15, 0d
```

---

## 2️⃣ شبكة النودز المترابطة الكاملة (Full DAG)

```mermaid
flowchart TD
    classDef anchor fill:#10b981,stroke:#059669,stroke-width:3px,color:#fff
    classDef phase fill:#38bdf8,stroke:#0284c7,stroke-width:2px,color:#000
    classDef gate fill:#f59e0b,stroke:#d97706,stroke-width:3px,color:#000
    classDef branch fill:#a855f7,stroke:#7c3aed,stroke-width:1.5px,color:#fff
    classDef qa fill:#f43f5e,stroke:#e11d48,stroke-width:2px,color:#fff
    classDef final fill:#10b981,stroke:#059669,stroke-width:4px,color:#fff

    START["🚀 N-START<br/>انطلاق المشروع<br/>26-10-2026 · SRS v0.1"]:::anchor
    
    START --> P1["📋 المرحلة 1<br/>التحليل وتصميم التجربة<br/>أكتوبر 2026"]:::phase
    P1 --> P1A["P1-A · UX<br/>رحلة المستخدم<br/>والمساران"]:::branch
    P1 --> P1B["P1-B · ARCH<br/>عزل المعامل<br/>والأدوار الثلاثة"]:::branch
    P1 --> P1C["P1-C · INFRA<br/>حسم الاستضافة<br/>OI-007"]:::branch
    P1 --> P1D["P1-D · GOV<br/>تثبيت العضو 13<br/>OI-013"]:::branch
    
    P1A --> G1
    P1B --> G1
    P1C --> G1
    P1D --> G1
    G1{"🚦 Gate 01<br/>إقرار النطاق<br/>نهاية أكتوبر 2026"}:::gate
    
    G1 --> P2["📝 المرحلة 2<br/>المحتوى والقصة<br/>+ الأخلاقيات<br/>نوفمبر 2026"]:::phase
    P2 --> P2A["P2-A · SCENARIO<br/>سيناريو SQL Injection<br/>JSON/MD خام"]:::branch
    P2 --> P2B["P2-B · EDU<br/>الشرح بأركانه 5<br/>+ المصادر"]:::branch
    P2 --> P2C["P2-C · NARRATIVE<br/>المشاهد القصصية<br/>World Bible"]:::branch
    P2 --> P2D["P2-D · ETHICS<br/>بروتوكول الأخلاقيات<br/>OI-001/004"]:::branch
    
    P2A --> P3
    P2B --> P3
    P2C --> P3
    P2D --> P3
    P2D -.->|موافقة مسبقة| G3
    
    P3["⚙️ المرحلة 3<br/>الهيكل الأساسي<br/>API-First<br/>ديسمبر 2026"]:::phase
    P3 --> P3A["P3-A · API<br/>عقود Swagger<br/>+ Mock Servers"]:::branch
    P3 --> P3B["P3-B · MONOLITH<br/>.NET 10<br/>7 وحدات"]:::branch
    P3 --> P3C["P3-C · DB<br/>PostgreSQL 16<br/>+ Argon2id"]:::branch
    P3 --> P3D["P3-D · FRONTEND<br/>Next.js 14<br/>+ RTL"]:::branch
    
    P3A --> P4
    P3B --> P4
    P3C --> P4
    P3D --> P4
    
    P4["🧪 المرحلة 4<br/>التجارب التقنية الحرجة<br/>يناير 2027"]:::phase
    P4 --> P4A["P4-A · DOCKER<br/>عزل + Reaper"]:::branch
    P4 --> P4B["P4-B · TOOLS<br/>ttyd · Monaco · Adminer"]:::branch
    P4 --> P4C["P4-C · VERIFIER<br/>تحقق خادمي"]:::branch
    P4 --> P4D["P4-D · PLAN-B<br/>خطة بديلة<br/>+ المرجع التقني"]:::branch
    
    P4A --> G2
    P4B --> G2
    P4C --> G2
    P4D --> G2
    G2{"🚦 Gate 02<br/>العزل الأمني<br/>IM-006<br/>نهاية يناير 2027"}:::gate
    
    G2 --> P5["🎯 المرحلة 5<br/>النموذج التجريبي v0.1<br/>فبراير 2027"]:::phase
    P5 --> P5A["P5-A · FLOW<br/>ربط الشرح بالمعمل<br/>واختيار الدور"]:::branch
    P5 --> P5B["P5-B · RED<br/>استغلال SQLi"]:::branch
    P5 --> P5C["P5-C · BLUE<br/>تحقيق جنائي"]:::branch
    P5 --> P5D["P5-D · DEV<br/>ترقيع الكود"]:::branch
    P5 --> P5E["P5-E · DIARY & DoD<br/>اليوميات + ساعات<br/>CN-019"]:::branch
    
    P5A --> G3
    P5B --> G3
    P5C --> G3
    P5D --> G3
    P5E --> G3
    P5E -.->|ساعات فعلية| G4
    
    G3{"🚦 Gate 03<br/>الأخلاقيات<br/>أو Dogfooding<br/>مطلع مارس 2027"}:::gate
    
    G3 --> P6["📊 المرحلة 6<br/>القياس الميداني<br/>5-10 طلاب<br/>مارس 2027"]:::phase
    P6 --> P6A["P6-A · STUDY<br/>تجربة 5-10 طلاب<br/>+ BehaviorEvent"]:::branch
    P6 --> P6B["P6-B · SUS<br/>حسم OI-015<br/>+ OI-002"]:::branch
    P6 --> P6C["P6-C · USER DOC<br/>دليل المستخدم"]:::branch
    
    P6A --> G4
    P6B --> G4
    P6C --> G4
    G4{"🚦 Gate 04<br/>قرار مشروط<br/>CN-019<br/>نهاية مارس 2027"}:::gate
    
    G4 --> P7A_PATH["✅ PATH A<br/>التعميم المشروط<br/>إضافة فئات عبر CMS"]:::branch
    G4 --> P7B_PATH["🔄 PATH B PIVOT<br/>ترسيخ الحقن<br/>عند عيوب UX"]:::branch
    
    P7A_PATH --> P7
    P7B_PATH --> P7
    
    P7["📈 المرحلة 7<br/>التعميم المشروط v0.2<br/>أبريل - منتصف مايو 2027"]:::phase
    P7 --> P7A["P7-A · CMS<br/>إدخال فئات<br/>بلا كود"]:::branch
    P7 --> P7B["P7-B · TEMPLATE<br/>وفر 30-40%<br/>SE-001"]:::branch
    P7 --> P7C["P7-C · E2E<br/>تحقق شامل<br/>من الفئات"]:::branch
    
    P7A --> QA
    P7B --> QA
    P7C --> QA
    QA["🧊 نافذة التثبيت<br/>Code Freeze & QA<br/>نصف مايو 2027"]:::qa
    QA --> QAA["QA-A · BUG BASH<br/>صفر أخطاء حرجة"]:::branch
    QA --> QAB["QA-B · PERF<br/>SP-001..004<br/>10 متعلمين"]:::branch
    QA --> QAC["QA-C · DOCS<br/>مزامنة الأدلة"]:::branch
    
    QAA --> P8
    QAB --> P8
    QAC --> P8
    
    P8["📚 المرحلة 8<br/>التوثيق والدراسة الموسعة<br/>يونيو 2027"]:::phase
    P8 --> P8A["P8-A · LEADERBOARD<br/>لوحة اختيارية<br/>Opt-in"]:::branch
    P8 --> P8B["P8-B · EVAL<br/>دراسة n≥10<br/>قبلي/بعدي"]:::branch
    P8 --> P8C["P8-C · 4 MANUALS<br/>الأدلة الأربعة<br/>الرسمية"]:::branch
    P8 --> P8D["P8-D · PAPER<br/>الورقة البحثية<br/>+ OI-006"]:::branch
    
    P8A --> G5
    P8B --> G5
    P8C --> G5
    P8D --> G5
    G5{"🚦 Gate 05<br/>تجميد القوالب<br/>CN-016<br/>منتصف يونيو 2027"}:::gate
    
    G5 --> FINAL["🏁 N-FINAL v1.0<br/>التسليم والمناقشة<br/>يوليو 2027"]:::final
    
    linkStyle default stroke:#64748b,stroke-width:2px
```

---

## 3️⃣ مسار البوابات الحاكمة (Governance Gates Flow)

```mermaid
flowchart LR
    classDef gate fill:#f59e0b,stroke:#d97706,stroke-width:3px,color:#000
    classDef inNode fill:#38bdf8,stroke:#0284c7,stroke-width:1.5px,color:#000
    classDef outNode fill:#10b981,stroke:#059669,stroke-width:1.5px,color:#fff
    
    subgraph G1_GRP["Gate 01 · نهاية أكتوبر 2026"]
        direction LR
        I1["P1-A · P1-B<br/>P1-C · P1-D"]:::inNode
        G1{"🚦 Gate 01<br/>توقيع CN-015..019<br/>OI-007 + OI-013"}:::gate
        O1["N-P2<br/>المحتوى والأخلاقيات"]:::outNode
        I1 --> G1 --> O1
    end
    
    subgraph G2_GRP["Gate 02 · نهاية يناير 2027"]
        direction LR
        I2["P4-A · P4-B<br/>P4-C · P4-D"]:::inNode
        G2{"🚦 Gate 02<br/>IM-006 + CN-004<br/>+ Plan B جاهز"}:::gate
        O2["N-P5<br/>النموذج التجريبي v0.1"]:::outNode
        I2 --> G2 --> O2
    end
    
    subgraph G3_GRP["Gate 03 · مطلع مارس 2027"]
        direction LR
        I3["P2-D (نوفمبر)<br/>+ P5-E (فبراير)"]:::inNode
        G3{"🚦 Gate 03<br/>موافقة PV-001<br/>أو Dogfooding"}:::gate
        O3["N-P6<br/>القياس الميداني"]:::outNode
        I3 --> G3 --> O3
    end
    
    subgraph G4_GRP["Gate 04 · نهاية مارس 2027"]
        direction LR
        I4["P5-E (ساعات)<br/>+ P6-A/B/C"]:::inNode
        G4{"🚦 Gate 04<br/>CN-015 + CN-019<br/>إعلان النطاق"}:::gate
        O4A["PATH A<br/>التعميم"]:::outNode
        O4B["PATH B PIVOT<br/>الترسيخ"]:::outNode
        I4 --> G4
        G4 -->|ساعات كافية + SUS جيد| O4A
        G4 -->|عيوب حرجة| O4B
    end
    
    subgraph G5_GRP["Gate 05 · منتصف يونيو 2027"]
        direction LR
        I5["N-QA + P8-A/B/C/D"]:::inNode
        G5{"🚦 Gate 05<br/>تجميد CN-016<br/>قبل التسليم بأسبوعين"}:::gate
        O5["N-FINAL<br/>المناقشة 07-2027"]:::outNode
        I5 --> G5 --> O5
    end
```

---

## 4️⃣ بوابة القرار المشروط Gate 04 (CN-019 Simulator)

```mermaid
flowchart TD
    classDef input fill:#38bdf8,stroke:#0284c7,stroke-width:2px,color:#000
    classDef calc fill:#a855f7,stroke:#7c3aed,stroke-width:2px,color:#fff
    classDef decision fill:#f59e0b,stroke:#d97706,stroke-width:3px,color:#000
    classDef pathA fill:#10b981,stroke:#059669,stroke-width:2px,color:#fff
    classDef pathB fill:#f43f5e,stroke:#e11d48,stroke-width:2px,color:#fff
    
    C["ساعات المحتوى<br/>H_Content"]:::input
    S["ساعات المشاهد<br/>H_Scenes"]:::input
    L["ساعات المعمل<br/>H_Lab"]:::input
    T["ساعات الاختبارات<br/>H_Tests"]:::input
    
    C --> TOTAL["Total Pilot Hours<br/>= H_Content + H_Scenes<br/>+ H_Lab + H_Tests"]:::calc
    S --> TOTAL
    L --> TOTAL
    T --> TOTAL
    
    TOTAL --> NEXT["H_Next Loop =<br/>Total × (1 - R)<br/>R = 30%..40%"]:::calc
    
    NEXT --> CHECK{"Max Extra Categories<br/>= floor(Available Hours / H_Next)<br/>n ≥ 2 ؟"}:::decision
    
    CHECK -->|"✅ نعم (n ≥ 2)"| PATH_A["PATH A<br/>إضافة فئات عبر CMS<br/>G4-PATH-A"]:::pathA
    CHECK -->|"⚠️ فئة واحدة فقط"| PATH_A1["PATH A<br/>فئة واحدة مع الحفاظ على الجودة"]:::pathA
    CHECK -->|"❌ صفر فئات"| PATH_B["PATH B PIVOT<br/>ترسيخ حلقة Injection<br/>G4-PATH-B"]:::pathB
    
    PATH_A --> P7["N-P7 · v0.2 Scale"]:::pathA
    PATH_A1 --> P7
    PATH_B --> P7
    
    SUS["نتيجة SUS<br/>من P6-B"]:::input
    SUS --> CHECK
```

---

## 5️⃣ مصفوفة الإصدارات المرحلية (Release Evolution)

```mermaid
flowchart LR
    classDef v01 fill:#38bdf8,stroke:#0284c7,stroke-width:3px,color:#000
    classDef v02 fill:#a855f7,stroke:#7c3aed,stroke-width:3px,color:#fff
    classDef v10 fill:#10b981,stroke:#059669,stroke-width:3px,color:#fff
    
    V01["📦 v0.1 PILOT<br/>فبراير 2027<br/>المراحل 1→5"]:::v01
    V02["📦 v0.2 SCALE<br/>منتصف مايو 2027<br/>المراحل 6→7 + QA"]:::v02
    V10["📦 v1.0 FINAL<br/>يوليو 2027<br/>المرحلة 8"]:::v10
    
    V01 --> V02 --> V10
    
    V01 -.-> D1["حلقة A05 Injection<br/>المسار المبسط D8<br/>الأدوار 3 Red/Blue/Dev<br/>اليوميات + الساعات<br/>حسم OI-007"]
    V02 -.-> D2["تعميم عبر CMS CN-009<br/>وفر 30-40% SE-001<br/>بيانات 5-10 طلاب<br/>نافذة التثبيت QA<br/>استقرار الحاويات"]
    V10 -.-> D3["لوحة صدارة Opt-in<br/>دراسة n≥10<br/>الأدلة الأربعة<br/>الورقة البحثية<br/>مناقشة رسمية"]
```

---

## 6️⃣ هيكلة الفرق الأربعة وصلاحيات الحسم (Teams Structure)

```mermaid
flowchart TB
    classDef team fill:#38bdf8,stroke:#0284c7,stroke-width:2px,color:#000
    classDef lead fill:#10b981,stroke:#059669,stroke-width:2px,color:#fff
    classDef track fill:#a855f7,stroke:#7c3aed,stroke-width:1.5px,color:#fff
    
    HEAD["HEADLESS Team<br/>13 عضوًا · CN-017"]:::lead
    
    HEAD --> T1["🎨 فريق المحتوى<br/>3 أعضاء"]:::team
    HEAD --> T2["⚙️ فريق Backend<br/>4 أعضاء"]:::team
    HEAD --> T3["💻 فريق Frontend<br/>4 أعضاء"]:::team
    HEAD --> T4["🔧 فريق Lab & DevOps<br/>عضوان"]:::team
    
    T1 --> T1A["P2-A/B/C/D<br/>P8-C/D<br/>OI-001/004/010/014"]:::track
    T1 --> T1L["الكلمة النهائية:<br/>قائد المحتوى<br/>+ مالك World Bible"]:::lead
    
    T2 --> T2A["P3-A/B/C<br/>P4-C<br/>CN-001 · CN-005<br/>CN-018"]:::track
    T2 --> T2L["الكلمة النهائية:<br/>قائد المعمارية<br/>+ مالك التقييم"]:::lead
    
    T3 --> T3A["P1-A · P3-D<br/>P6-A/B<br/>P8-A<br/>CN-005 · RTL"]:::track
    T3 --> T3L["الالتزام بـ CN-018<br/>حظر احتساب نقاط<br/>من العميل"]:::lead
    
    T4 --> T4A["P1-C · P4-A/B/D<br/>P5-B/C/D<br/>OI-007 · Plan B"]:::track
    T4 --> T4L["حق إيقاف فوري<br/>عند خلل العزل<br/>PUC-017"]:::lead
```

---

## 7️⃣ استراتيجية درء المخاطر الأربعة (Risk Mitigation)

```mermaid
flowchart LR
    classDef risk fill:#f43f5e,stroke:#e11d48,stroke-width:2px,color:#fff
    classDef fix fill:#10b981,stroke:#059669,stroke-width:2px,color:#fff
    classDef node fill:#38bdf8,stroke:#0284c7,stroke-width:1.5px,color:#000
    
    R1["⚠️ اختناق الأخلاقيات<br/>P2-D ➔ Gate 03<br/>تأخير 4-6 أسابيع"]:::risk
    R1 --> F1["✅ تقديم نوفمبر 2026<br/>+ Plan B Dogfooding<br/>عند التأخر"]:::fix
    
    R2["⚠️ اختناق الاستضافة<br/>OI-007<br/>RAM/CPU محدود"]:::risk
    R2 --> F2["✅ حسم في P1-C<br/>أكتوبر 2026<br/>+ Plan B في P4-D"]:::fix
    
    R3["⚠️ انهيار الجدول<br/>قبل المناقشة<br/>العلل البرمجية"]:::risk
    R3 --> F3["✅ نافذة QA مستقلة<br/>Code Freeze<br/>نصف مايو 2027"]:::fix
    
    R4["⚠️ ضغط التوثيق<br/>في الشهر الأخير<br/>ضعف الصياغة"]:::risk
    R4 --> F4["✅ توثيق تدريجي<br/>P1/P2/P4/P6/P8<br/>Incremental Docs"]:::fix
```

---

## 8️⃣ خريطة حسم القضايا المفتوحة على المسار (Open Issues Timeline)

```mermaid
flowchart LR
    classDef oct fill:#38bdf8,stroke:#0284c7,stroke-width:2px,color:#000
    classDef nov fill:#a855f7,stroke:#7c3aed,stroke-width:2px,color:#fff
    classDef dec fill:#06b6d4,stroke:#0891b2,stroke-width:2px,color:#fff
    classDef jan fill:#f59e0b,stroke:#d97706,stroke-width:2px,color:#000
    classDef mar fill:#10b981,stroke:#059669,stroke-width:2px,color:#fff
    classDef mayjun fill:#f43f5e,stroke:#e11d48,stroke-width:2px,color:#fff
    
    OCT["📅 أكتوبر 2026<br/>المرحلة 1"]:::oct
    NOV["📅 نوفمبر 2026<br/>المرحلة 2"]:::nov
    DEC["📅 ديسمبر 2026<br/>المرحلة 3"]:::dec
    JAN["📅 يناير 2027<br/>المرحلة 4"]:::jan
    MAR["📅 فبراير-مارس 2027<br/>المرحلتان 5-6"]:::mar
    MAYJUN["📅 أبريل-يونيو 2027<br/>المراحل 7-8"]:::mayjun
    
    OCT --> OI1["OI-007 الاستضافة<br/>OI-013 العضو 13<br/>→ P1-C / P1-D"]
    NOV --> OI2["OI-001/004 الأخلاقيات<br/>OI-010/014 المصادر<br/>→ P2-B / P2-D"]
    DEC --> OI3["OI-009/011 كلمات المرور<br/>→ P3-B"]
    JAN --> OI4["OI-008/012 الأدوات<br/>→ P4-B"]
    MAR --> OI5["OI-002/015 الشاشات+SUS<br/>→ P6-B"]
    MAYJUN --> OI6["OI-003/005/006<br/>المعايير واللجنة<br/>→ P8-D"]
    
    OCT -.-> G1["Gate 01"]
    MAR -.-> G3["Gate 03"]
    MAR -.-> G4["Gate 04"]
    MAYJUN -.-> G5["Gate 05"]
```

---

## 9️⃣ مصفوفة التحقق من شروط العبور (Exit Criteria Matrix)

```mermaid
flowchart TB
    classDef gate fill:#f59e0b,stroke:#d97706,stroke-width:3px,color:#000
    classDef crit fill:#38bdf8,stroke:#0284c7,stroke-width:1px,color:#000
    
    G1["🚦 Gate 01<br/>نهاية أكتوبر 2026"]:::gate
    G1 --> C1A["✓ SRS v0.1 معتمد"]:::crit
    G1 --> C1B["✓ توقيع CN-015..019"]:::crit
    G1 --> C1C["✓ OI-007 الاستضافة محسومة"]:::crit
    G1 --> C1D["✓ OI-013 العضو 13 مثبت"]:::crit
    
    G2["🚦 Gate 02<br/>نهاية يناير 2027"]:::gate
    G2 --> C2A["✓ IM-006 اجتياز إساءة الاستخدام"]:::crit
    G2 --> C2B["✓ CN-004 عزل شبكي تام"]:::crit
    G2 --> C2C["✓ Reaper يعمل"]:::crit
    G2 --> C2D["✓ Plan B جاهز"]:::crit
    
    G3["🚦 Gate 03<br/>مطلع مارس 2027"]:::gate
    G3 --> C3A["✓ PV-001 موافقة الأخلاقيات"]:::crit
    G3 --> C3B["✓ أو Dogfooding مفعّل"]:::crit
    G3 --> C3C["✓ نموذج موافقة مستنيرة"]:::crit
    
    G4["🚦 Gate 04<br/>نهاية مارس 2027"]:::gate
    G4 --> C4A["✓ ساعات المرحلة 5"]:::crit
    G4 --> C4B["✓ محضر CN-015 موقع"]:::crit
    G4 --> C4C["✓ نتائج SUS"]:::crit
    G4 --> C4D["✓ قرار PATH A/B"]:::crit
    
    G5["🚦 Gate 05<br/>منتصف يونيو 2027"]:::gate
    G5 --> C5A["✓ CN-016 تجميد القوالب"]:::crit
    G5 --> C5B["✓ تدقيق لغوي وتقني"]:::crit
    G5 --> C5C["✓ جاهزية العرض"]:::crit
```

---

## 🔟 التدفق التسلسلي المبسط للنودز الرئيسية (Spine Sequence)

```mermaid
flowchart TD
    classDef anchor fill:#10b981,stroke:#059669,stroke-width:3px,color:#fff
    classDef phase fill:#38bdf8,stroke:#0284c7,stroke-width:2px,color:#000
    classDef gate fill:#f59e0b,stroke:#d97706,stroke-width:3px,color:#000
    classDef qa fill:#f43f5e,stroke:#e11d48,stroke-width:2px,color:#fff
    
    START["N-START<br/>26-10-2026"]:::anchor
    P1["N-P1<br/>المرحلة 1"]:::phase
    G1["N-G1<br/>Gate 01"]:::gate
    P2["N-P2<br/>المرحلة 2"]:::phase
    P3["N-P3<br/>المرحلة 3"]:::phase
    P4["N-P4<br/>المرحلة 4"]:::phase
    G2["N-G2<br/>Gate 02"]:::gate
    P5["N-P5<br/>المرحلة 5 · v0.1"]:::phase
    G3["N-G3<br/>Gate 03"]:::gate
    P6["N-P6<br/>المرحلة 6"]:::phase
    G4["N-G4<br/>Gate 04"]:::gate
    P7["N-P7<br/>المرحلة 7 · v0.2"]:::phase
    QA["N-QA<br/>التثبيت"]:::qa
    P8["N-P8<br/>المرحلة 8"]:::phase
    G5["N-G5<br/>Gate 05"]:::gate
    FINAL["N-FINAL<br/>07-2027 · v1.0"]:::anchor
    
    START --> P1 --> G1 --> P2 --> P3 --> P4 --> G2 --> P5 --> G3 --> P6 --> G4 --> P7 --> QA --> P8 --> G5 --> FINAL
```

---
