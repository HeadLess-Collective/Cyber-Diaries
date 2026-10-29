[English](README.md) | [العربية](README.ar.md)
# Cyber Diaries
## Graduation Project Description: An Interactive Arabic Platform for Teaching the Full Lifecycle of Web Application Security Incident Handling
---
# 0. The Project in One Minute

**Cyber Diaries** is an interactive Arabic learning platform that teaches web application security through a continuous story centered on one main character. The story unfolds across two connected periods in the character’s life. In the **Learning Path**, the main character—provisionally named **Sābir**, subject to change—is shown before beginning his professional career, while he is still learning and building his cybersecurity knowledge. When the user moves to the **Labs Path**, the story advances to the period after the character joins **NoorTech**, a fictional Egyptian electronic-payment company. Workplace incidents begin to occur, and the character’s experience, responsibilities, and relationships develop as the company grows, changes its services, and expands its teams across ten episodes connected to the OWASP Top 10:2025 categories.

After entering the platform, the user chooses between two paths: **Learning**, where they browse the ten categories, select one, watch a story scene showing the main character learning before employment, study the technical explanation, watch an embedded external educational video, and answer a short quiz; or **Labs**, where they select a category and watch a short story-driven introduction—targeted at approximately ninety seconds—depicting an incident at NoorTech after the main character has joined the company. The user then chooses a difficulty level and one of three roles: **Red Team**, **Blue Team**, or **Developer**. Story scenes can be skipped, provided an equivalent contextual summary is available.

If the user chooses Red Team, the discovery task starts directly. If the user chooses Blue Team or Developer, a short transition scene shows the main character bringing in a colleague with the relevant specialization. The user then enters the workspace for the selected role. The lab presents the problem details and only the tools needed for that task. All activities run inside isolated lab environments.

The platform’s core value is not teaching isolated vulnerability exploitation. It connects discovery, investigation, remediation, and documentation in one learning experience. Users may enter a single role directly or complete the full scenario. The project will first build one fully integrated episode, measure its actual development cost and educational effectiveness, and then extend the template to additional categories according to available time and resources.

Four expected questions from the supervisor and concise answers:

| Expected question | Concise answer |
| --- | --- |
| What is new about the project? | An Arabic platform combining a pre-employment learning storyline with a professional storyline inside a growing company, two paths for learning and practice, three connected practical roles, and real tools inside isolated labs. |
| How does the user move through the platform? | The user starts at the home page, signs up or logs in, then chooses either the Learning Path or the Labs Path. Each path has a clear journey and can lead to the other. |
| What is the committed deliverable? | One fully developed episode (the Injection category), including its content, storyline, three roles, exercises, and assessment; then measure its cost and extend the template as resources allow. |
| How will educational value be measured? | Pre-, post-, and—where feasible—delayed assessments, behavioral data collected by the platform, usability testing, and analysis of learners’ journals. |

---

# 1. Project Profile

| Item | Details |
| --- | --- |
| Project name | **Cyber Diaries — Sābir Diaries** (Sābir is provisionally derived from the Arabic verb *sabara* / سَبَرَ, meaning to examine or probe something deeply; it was also selected for its phonetic resemblance to “Cyber.”) |
| Team name | **The Headless** (بلا رؤوس) |
| Project type | Story-driven interactive educational platform / serious game |
| Domain | Web application security and applied learning |
| Reference framework | OWASP Top 10:2025 — all ten categories |
| Primary audience | Computer science students and junior web developers with basic programming and web knowledge |
| Secondary audience | Cybersecurity enthusiasts without a programming background, introduced through the foundational material in the Learning Path |
| Content language | Arabic. Dialogue uses natural Egyptian colloquial Arabic; technical explanations use clear Modern Standard Arabic, with English terminology where needed. |
| Content structure | Two paths for each category: **Learning** (a story scene showing the main character before employment, a technical explanation, an embedded external educational video, and a short quiz) and **Labs** (a professional storyline at NoorTech after the character joins the company, an incident introduction, and a choice among Red Team, Blue Team, and Developer). |
| Narrative structure | A learning timeline before employment, followed by a professional timeline at NoorTech. The same main character appears in both, develops experience and responsibilities, and the company grows throughout the episodes. |
| User journey | Home page, followed by Get Started or Login, then a landing dashboard offering the Learning Path and Labs Path. |
| Frontend | React and Next.js |
| Backend | ASP.NET Core Web API using a Modular Monolith architecture |
| Database | PostgreSQL |
| Labs | Isolated Docker containers integrating existing real tools rather than building tools from scratch |
| Deliverables | Working platform, Arabic educational content, practical labs, technical and academic documentation, an evaluation study, and a research paper |

---

# 2. Core Value: The Full Security-Handling Lifecycle, Not Exploitation Alone

The project does not simply offer “Arabic vulnerability exploitation training.” It teaches the full lifecycle of handling a security problem in Arabic. In each episode, the learner experiences the following cycle:

1. A security incident occurs within the story.
2. The learner encounters the problem, discovers its cause, and safely demonstrates that it exists in a controlled environment.
3. The learner investigates its impact and builds an explanation of what happened based on the available evidence.
4. The learner takes action, fixes the root cause, and verifies that the remediation works.
5. The learner documents what they learned in their diary and sees the consequences of their actions.

This cycle defines success for the project. A successful learner should be able to explain the problem, demonstrate it, analyze the evidence, fix its cause, and document the outcome—not merely memorize the vulnerability’s name or execute a ready-made exploit.

---

# 3. The Problem the Project Addresses

1. **The theory–practice gap:** A learner may know the definition of SQL Injection without knowing how to discover it, explain its impact, or fix it.
2. **Fragmented learning resources:** Learners must move between multiple sources with different languages and difficulty levels.
3. **The language barrier:** Many advanced resources are in English, making it harder for a broad segment of Arabic-speaking learners to get started.
4. **Lack of workplace context:** Isolated exercises do not show the connection between a coding mistake, a security incident, and its impact on users and the organization.
5. **Lack of an integrated perspective:** Discovering a vulnerability does not necessarily prepare a learner to investigate its traces in logs or fix its root cause.
6. **Difficulty measuring real progress:** Completing a lesson or watching a video does not necessarily mean that a practical skill has been acquired.

These problems will be supported in the final documentation by a literature review and a documented comparison with existing platforms. The project will not claim to be unprecedented without supporting market and academic research.

---

# 4. The Learner Experience

The journey starts on the platform’s public home page and then moves into the signed-in experience. After logging in or creating an account, the user reaches a landing dashboard that clearly presents two primary paths: **Learning** and **Labs**.

### 4.1 Home Page and Entry

1. The home page briefly explains the idea behind Cyber Diaries and the nature of the experience. It provides two clear options: **Get Started** to begin or create an account, and **Login** to sign in.
2. After successful registration or login, the user is taken to the internal home page (Dashboard).
3. The landing dashboard presents the two main paths—Learning and Labs—and, when prior activity exists, displays the user’s progress and most recent activity.

### 4.2 Learning Path Journey

1. The user selects the **Learning Path**, which displays the ten OWASP Top 10:2025 categories.
2. The user selects a category. The experience begins with a story scene or video featuring the main character, “Sābir”—or whatever final name the team chooses—during the pre-employment stage, when he is learning and building his understanding of the selected security category. At this point, he has not yet joined NoorTech. He appears as a learner like the user, not as an employee responding to an incident at the company.
3. After the story scene, the page presents the technical explanation of the issue, its causes, impacts, and prevention methods. It also includes an embedded external educational video from a trusted source and a short multiple-choice quiz. The story video and external educational video are separate elements: the first connects the learner to the character and narrative world; the second explains the topic technically.
4. After reviewing the material, the user can move directly to the lab for the same category. Passing the quiz is not required to unlock the lab; the quiz is a self-assessment, not a progression gate.

### 4.3 Labs Path Journey

1. The user selects the **Labs Path**, sees the ten categories, and chooses the category they want to practice.
2. The lab begins with a short story-driven introduction, targeted at approximately ninety seconds. It presents the situation and incident that occurred at NoorTech and establishes the context for the task.
3. The user may watch or skip the introduction. If it is skipped, an equivalent text summary provides the incident context, objective, and essential information so the user does not lose track of the task.
4. The user chooses a difficulty level. This determines the amount of help available through hints.
5. The user chooses one of three roles: **Red Team**, **Blue Team**, or **Developer**.
6. If Red Team is selected, the user proceeds directly to the discovery task. If Blue Team is selected, a short scene shows the main character bringing in a colleague from the Blue Team/SOC to investigate the incident. If Developer is selected, a similar scene shows the main character bringing in a developer colleague to address the root cause. After the scene, the user enters the workspace for the selected role.
7. The workspace presents the problem description, objective, available evidence, and tools required for the selected role, without cluttering the interface with tools that are irrelevant to the task.
8. After the task is completed, the platform displays the assessment result and feedback. The user can then write in their journal and return to the category dashboard or continue to the full scenario, if available.

### 4.4 The Story Across the User Experience

The story has two connected timelines, each representing a different stage in the main character’s life:

- **Learning before employment:** The main character appears in Learning Path scenes as a learner who has not started working yet. He encounters and learns the security categories one by one. The scenes show moments from his learning journey and the gradual development of his understanding. NoorTech is not his workplace at this stage, and he is not shown as an employee responding to company incidents.
- **Working at NoorTech:** The story moves forward in time to the period after the character joins the company. Security incidents and lab events begin here. The main character becomes central to handling these incidents and works with specialized colleagues from security and development teams, depending on the role selected by the user.

The same main character therefore appears in both paths, but his status and context change logically: he is a learner before employment in the first path and a member of a workplace environment in the second. The scenes must preserve this chronological order so that the character is never shown working at NoorTech before joining the company.

### 4.5 Experience Rules

- Story scenes explain the reason for the task and establish its context; they are not decorative videos. If a scene can be skipped, an equivalent summary must be provided.
- Users may enter either the Learning Path or the Labs Path directly. Completing one path is not a prerequisite for the other.
- The user chooses the role they want to practice in a lab. A complete experience combining all three roles may also be offered as an additional option, without forcing every user to complete it.
- The transition between the story and the task must remain clear. Scenes and summaries must not reveal assessment answers or provide a ready-made solution.

---

# 5. Path One: Learning

This path starts by displaying the ten OWASP Top 10:2025 categories. When the user selects a category, they do not go directly to an abstract technical explanation. Instead, they first enter a story scene showing the main character during the pre-employment stage, when he is still learning web application security and building his experience. The video presents part of his learning journey and a moment related to the selected category. This allows the user to experience the moment with the character and become familiar with him before seeing him later in the workplace environment at NoorTech in the Labs Path.

After the story scene, the category’s dedicated learning page opens. It contains:

1. **Educational story scene:** A video or narrative scene for the selected category, showing the main character during his pre-employment learning period. It focuses on the character, context, and learning moment. It does not depict a professional incident at NoorTech because the character has not joined the company yet.
2. **Simple introduction:** What is the security problem, and what impact can it have?
3. **Technical explanation:** How does it happen, and under what conditions is it possible?
4. **A simplified illustrative example.**
5. **Root causes:** Design, implementation, or configuration mistakes that can lead to the issue.
6. **Prevention and remediation methods.**
7. **Embedded external educational video:** A resource selected from a trusted source and related to the category. It explains the technical aspects and complements the written material. This video is separate from the story scene produced or prepared by the project team. A direct alternative link will be retained in case embedding is unavailable.
8. **Short quiz:** Three to five multiple-choice questions. The quiz is a self-assessment of the learner’s understanding, not a gate that prevents access to the lab.
9. **Trusted external references:** Two or three links per category, such as OWASP documentation and recognized educational resources.
10. **A clear link** to the lab for the same category.

**How the story and educational content work together:**

- The story scene lets the learner experience a moment with the main character and follow his pre-employment journey. It provides narrative, motivation, and context; it does not replace the technical explanation.
- The embedded external video explains the category technically and does not replace the story scene.
- Original written content remains the primary reference, ensuring that the explanation is complete, accurate, and available even if a video cannot be displayed.
- The story scene may be skipped, but a text summary must preserve the context of the character and the learning moment without forcing the user to watch the video.

**Content and media priorities:**

- A consistent template will be designed for educational story scenes so it can be reused across all ten categories, with changes to the situation, topic, and the main character’s development.
- In the pilot version, the educational story scene for the Injection category will be produced or prepared first. Its production cost will then be measured before extending the format.
- The external educational video will be selected from a trusted source and will not require original video production by the team.
- Completion of the technical explanation will not depend on an external video being available. If no suitable video exists, a trusted alternative link will be provided or the written material will stand on its own.
- Long, cinematic, or expensive animations are deferred. The requirement is for short scenes that are consistent with the story and can be produced using a reusable template.

---

# 6. Path Two: Labs — A Connected Story with Three Practical Roles

### 6.1 The Three Roles

| Role | Main question | Learner’s responsibility | Assessment |
| --- | --- | --- | --- |
| Red Team | Where is the problem, and can it be safely demonstrated? | Discover the issue and prove that it exists within the lab’s scope | Automated validation of the security outcome, not merely finding hidden text |
| Blue Team / SOC | What happened, and how do we know? | Examine evidence and logs, correlate events, and identify the activity and affected resource | Questions and tasks tied to specific evidence and a two- or three-step reasoning chain |
| Developer | How do we prevent the issue from happening again? | Identify and fix the root cause, then verify that the fix is correct | Automated tests that demonstrate the issue, prevent the unsafe case, and preserve legitimate functionality |

### 6.2 Lab Flow from Start to Finish

1. The user selects a category from the ten OWASP categories in the Labs Path.
2. The user watches a short story-driven introduction, targeted at approximately ninety seconds. It presents the incident and situation at the company and explains why the issue needs attention. The scene can be skipped, provided an equivalent contextual summary is displayed.
3. The user selects a difficulty level: Easy, Medium, or Hard. The level determines the available hints, not the type of vulnerability or the solution itself.
4. The user selects the role they want to perform: Red Team, Blue Team, or Developer.
5. If Red Team is selected, the user proceeds directly to the discovery task after the introduction.
6. If Blue Team is selected, a short transition scene shows the main character bringing in a specialized colleague from the Blue Team/SOC. The user then enters the investigation and evidence interface.
7. If Developer is selected, a short transition scene shows the main character bringing in a developer colleague to address the issue. The user then enters the remediation workspace.
8. The workspace displays the vulnerability or problem details relevant to the selected role, the required objective, and the appropriate evidence, files, and tools.
9. The user performs the task inside the isolated lab. The platform automatically validates the result according to the requirements of the selected role.
10. Feedback and the result are displayed. The user then moves to the journal and closing scene, or returns to select another category.

### 6.3 Story and Supporting Characters

The main character is the narrative thread connecting both paths and all ten episodes. In Learning Path scenes, he appears before employment as a learner building his cybersecurity knowledge. The lab events take place later, after he joins NoorTech. When moving between lab roles, the main character remains the same and the narrative continues; he collaborates with supporting characters from specialized teams. When Blue Team is selected, a colleague specializing in monitoring and investigation appears. When Developer is selected, a colleague specializing in software development and remediation appears. The identity, details, and experience of supporting colleagues may vary from episode to episode according to the scenario, while preserving consistency in the story world.

### 6.4 One Security Scenario for Each Category

All three roles are based on one security incident per category. The issue discovered by Red Team is the same issue whose traces appear in the Blue Team evidence, and the root cause addressed by the Developer is connected to that same incident. This avoids building three unrelated experiences for each category and preserves the connection between discovery, investigation, and remediation.

Evidence and the environment will be prepared so that users can enter any role directly without completing the previous roles. The contextual summary must not reveal assessment answers, but it must provide the minimum information needed to understand the situation.

### 6.5 Choosing One Role or Completing the Full Experience

- **Direct entry:** The user chooses one of the three roles and completes its task independently, with the appropriate context and evidence.
- **Full Scenario:** An optional experience that combines the roles in sequence: discovery, investigation, remediation, and a summary connecting the cause, impact, evidence, and fix. This path is not mandatory for users who only want to practice one role.

### 6.6 Consistency and Variation

The three roles remain consistent at the platform-design level, while incident details, tools, and supporting characters vary by category. Each role must provide a genuine activity that serves a learning objective for the selected category, rather than a cosmetic screen. If a meaningful task cannot be designed for one of the roles in a particular category, the category and scenario must be reviewed before approval instead of filling the gap with an activity that does not contribute to learning.

### 6.7 Assessing the Investigation Stage

The greatest design risk is that the Blue Team stage becomes a reading comprehension test. The following rules address this risk:

- Every investigation task must contain a genuine reasoning chain: identify an anomaly, connect it to another event, and infer the activity and affected resource—not simply search for a line in a log.
- Example questions include: Which pieces of evidence point to the incident? What type of activity occurred? Which resource was affected? What is the most appropriate defensive action?
- Question formats include multiple choice, selecting the correct evidence, and ordering events chronologically. Free-text assessment is deferred.
- Before production, test task quality with a student who has not seen the scenario. If they can answer immediately without investigation, the stage is not functioning as an investigation.

---

# 7. Journals: Documentation as a Learning Mechanism

The journal is not decorative; it is a functional part of the experience. After each episode, the learner writes responses to four questions: What happened? Why did it happen? What did I do? What did I learn? The journal serves three purposes:

1. **Reflective learning:** Writing about what was learned can reinforce understanding more deeply than relying only on multiple-choice questions. This practice is supported by the literature on learning journals.
2. **Reducing assessment fatigue:** The journal provides a partial alternative to layers of multiple-choice questions.
3. **A qualitative research instrument:** The learner’s own reflections provide data that can be analyzed in the evaluation study and can become a valuable contribution to the research paper.

---

# 8. The Narrative World and Characters

### 8.1 A Ten-Episode Series

The story has one connected timeline, presented through two distinct stages:

1. **Learning before employment:** This stage comes before the events at NoorTech. The main character appears in Learning Path scenes while he is still learning web application security. He encounters the ten categories and gradually builds his knowledge and experience. Each category has a story scene or short video focused on a learning moment, keeping the character present alongside the learner. During this stage, the character has not started working at the company and is not shown carrying out tasks or responding to incidents as an employee.
2. **Working at NoorTech:** This stage follows the learning period. The character joins the company and begins dealing with the security incidents that form the lab storylines. He remains the connecting character across all ten episodes, while his experience, responsibilities, relationships, and professional position develop as the story progresses. NoorTech starts as a small company, then expands its customer base, services, teams, and technical infrastructure. Its data becomes more sensitive and its operations grow in scale. This progression provides a natural reason for changes in the risk context, systems, and affected people from one episode to another.

In the Labs Path, each category begins with a short narrative introduction, targeted at approximately ninety seconds. It presents an incident at NoorTech and the context in which it occurred after the main character joined the company. Users may skip the video if an equivalent text summary is provided. After role selection, a short transition scene appears when Blue Team or Developer is selected: the main character brings in a specialized colleague from the relevant team, and the task begins from that role’s perspective. The story video in the Learning Path therefore serves a different purpose from the lab introduction: the former shows the character as a learner before employment, while the latter shows him in a professional situation after joining the company.

The consistency of this world is managed through a **World Bible**: one file documenting the order of the two stages, the timeline from learning to employment and company growth, the main character’s development, character relationships, episode events, and the teams that appear. The file will have one owner on the team and clearly announced freeze dates, preventing contradictions when multiple team members write different scenarios.

### 8.2 Characters

| Character / Element | Description |
| --- | --- |
| The company | **NoorTech**, a fictional Egyptian electronic-payment services company that gradually expands in size, services, customers, and teams throughout the episodes. |
| Main character | One continuous character across both paths and all episodes, provisionally named **Sābir** and subject to change. In the Learning Path, he appears before employment as a learner who has not started working yet. In the Labs Path, he appears after joining NoorTech as a member of the technical team. His experience, responsibilities, relationships, and professional position develop as events progress. |
| Manager | A demanding manager whose changing pressures create narrative context for development pressures. Their priorities and management style may evolve as the company grows. |
| Developer colleague | An experienced, practical developer who may overlook certain controls. Design and implementation mistakes appear in realistic contexts rather than being treated as a permanent caricature of the character. |
| Blue Team / SOC colleague | A supporting character who appears when the user selects the investigation path and helps interpret evidence and correlate events. The character or their experience may vary by episode. |
| Developer colleague for remediation | A supporting character who appears when the user selects the remediation path and helps understand the code, root cause, and fix verification. The character may vary by episode. |
| Support employee | A point of contact with customers who may appear in events involving reports or social engineering. |
| Customers | Fictional characters through whom the real-world impact of security problems on individuals and the organization becomes clear. |
| Adversary | An external attacker whose presence is shown through events and evidence rather than direct scenes, without turning the story into an offensive how-to guide. |

### 8.3 Narrative Presentation Style

- **Learning Path story videos:** Short story scenes related to the categories, showing the main character before employment as he learns and builds knowledge. Their purpose is to let the learner experience the moment with the character and follow his development, not to repeat a technical explanation in story form.
- **External educational video:** A separate resource selected from a trusted source to explain the category technically.
- **Lab introduction:** A short story video or scene, targeted at approximately ninety seconds, placing the user inside a workplace incident at NoorTech after the main character has joined the company.
- **Red Team scene:** No additional transition is required; the user moves from the incident introduction to the discovery task.
- **Blue Team scene:** Shows the main character bringing in a colleague from monitoring and investigation, then opens the evidence and analysis interface.
- **Developer scene:** Shows the main character bringing in a colleague from the development team, then opens the code workspace and remediation task.
- **Skipping scenes:** Story scenes may be skipped, but a summary must preserve the context and task without revealing the solution.
- **Language:** Dialogue uses natural Egyptian colloquial Arabic; technical explanations use clear Modern Standard Arabic, with the English term introduced when it first appears.

Writing rule: Characters must feel realistic rather than caricatured. Not every programmer is careless, and not every manager is the source of problems. Instead, situations should show how pressure, mistakes, and poorly considered decisions can create real risks.

---

# 9. The Ten OWASP Top 10:2025 Categories

| # | Category | Story Event | Red Team: Discovery | Blue Team: Investigation | Developer: Remediation and Documentation |
| ---: | --- | --- | --- | --- | --- |
| 1 | Broken Access Control | A user accesses data that does not belong to them. | Demonstrate unauthorized access inside the lab. | Identify the affected requests and resources from the evidence. | Implement and test correct authorization checks. |
| 2 | Security Misconfiguration | Default settings or a service are exposed after a rushed maintenance change. | Discover the insecure configuration. | Analyze the traces of the exposed access. | Correct the configuration and reduce exposure. |
| 3 | Software Supply Chain Failures | An untrusted update or component is introduced into the application. | Identify a supply-chain issue. | Analyze the component’s origin and related events. | Improve verification of components and their sources. |
| 4 | Cryptographic Failures | Sensitive data is stored or transmitted without appropriate protection. | Identify and safely demonstrate the protection weakness. | Determine which data and operations were affected. | Apply suitable encryption and proper key management. |
| 5 | Injection | A search form passes untrusted input into a query. | Demonstrate a context-limited injection. | Identify suspicious requests from the evidence. | Use parameterized queries and appropriate input handling. |
| 6 | Insecure Design | A payment feature was designed without adequate business controls. | Discover a business-logic flaw. | Analyze the event sequence and outcomes. | Redesign the workflow and its controls. |
| 7 | Authentication Failures | Weaknesses exist in identity verification or session management. | Demonstrate an authentication weakness using test accounts. | Identify suspicious login attempts. | Improve authentication and session management. |
| 8 | Software or Data Integrity Failures | Data or updates are accepted without integrity verification. | Identify where verification is missing. | Analyze the origin of the data or update. | Add integrity and trust validation. |
| 9 | Security Logging and Alerting Failures | An incident goes undetected because appropriate logs are missing. | Perform controlled activity to test observability. | Infer what happened and identify logging gaps. | Add useful logging and alerts without exposing sensitive data. |
| 10 | Mishandling of Exceptional Conditions | An unhandled exception leads to unsafe behavior. | Demonstrate the unsafe behavior. | Analyze the error traces and event sequence. | Handle exceptions and edge cases safely. |

Two notes:

- A category is a **risk area**, not a single vulnerability. Therefore, one representative educational case will be selected for each category.
- Final names and ordering must match the official OWASP Top 10:2025 release when the educational content is prepared. Each category must also be reviewed against the three-role model before production; a role that does not meaningfully fit a category should be removed for that category rather than forced into it.

---

# 10. The First Pilot Category

The initial recommendation is to build the integrated prototype around **Injection**, using a limited SQL Injection scenario, because:

1. It is relatively easy to explain to beginners.
2. It provides a clear comparison between vulnerable and secure code.
3. Appropriate investigation evidence can be prepared.
4. Automated tests can demonstrate that remediation works.
5. It allows the team to test the connection between all three roles without building a large security environment.

This is an initial recommendation and should be reviewed against the team’s skills and available tools before final approval.

---

# 11. Difficulty Levels and Hints

| Level | Type of assistance | Points multiplier |
| --- | --- | ---: |
| Easy (default) | Detailed hints explaining the current step using a similar example, without revealing the solution | 1.0 |
| Medium | Directional hints: where to look, which evidence to inspect, or which tool to use | 1.5 |
| Hard | No hints | 2.0 |

Rules:

- No difficulty level reveals the complete ready-made solution.
- A higher multiplier is not awarded merely for selecting a higher difficulty. The level at which the success conditions are actually met is counted, and users cannot change it after completion to claim undeserved points.
- Hint usage is recorded for educational analysis. Hints remain supportive tools, not a penalty.

---

# 12. Points and Achievements

The system’s philosophy is that points provide light encouragement only. They do not unlock or block content, measure a learner’s worth, or place pressure on beginners to compete.

- Points may be awarded for completing each lab role, completing the full episode, completing without hints, completing at a higher difficulty, and achieving specific learning milestones.
- An optional leaderboard may offer weekly, monthly, and all-time periods. Display names are optional, and users can hide their accounts entirely.
- Badges are linked to categories, roles, and clearly defined achievements.
- Completion rates are calculated from actual data using documented definitions of completion (started, completed one role, or completed the full episode). Rates based on very small samples are hidden.
- All points and achievements must be calculated and validated on the server. Nothing is awarded based solely on browser-submitted data, and duplicate award attempts must be prevented.

---

# 13. Virtual Desktop and Tools

The desktop is an interface only—a visual workspace for accessing tools—not an operating system or virtual machine. It includes a taskbar, shortcuts, files and narrative messages that can be opened, and windows with fixed tabs rather than a complex window-management system.

Tools are displayed according to the selected role and the category. Users do not see every tool in every task. Red Team receives discovery and request-inspection tools; Blue Team receives logs, evidence, and analysis tools; Developer receives a code editor, tests, and resources required for remediation.

All tools are real, existing tools to be integrated rather than built from scratch. Only tools that serve the learning objective of a category are displayed:

| Tool | Purpose |
| --- | --- |
| ttyd | Web terminal connected to the lab container |
| Monaco Editor | Code editing during remediation |
| Adminer | Inspecting the lab database |
| curl | Sending requests and inspecting responses |
| nmap | Limited scanning within the lab scope when needed |
| GPG | Signing and verification operations in relevant scenarios |
| grep and tail | Processing text-based logs from the terminal |
| Browser developer tools | Inspecting requests and responses during training |

Tool integration rule: Do not build a tool from scratch unless no existing alternative meets the need. Review each tool’s license and integration method, and ensure that its operation cannot escape the lab’s defined scope.

---

# 14. Technical Architecture (High-Level)

```text
Cyber Diaries
├── Frontend: React + Next.js
│   ├── Home page and registration/login
│   ├── Landing dashboard, categories, and progress
│   ├── Learning Path
│   ├── Narrative rendering engine for both timelines
│   │   └── Pre-employment learning / Employment at NoorTech
│   ├── Story-scene, lab-introduction, and transition-scene player
│   ├── External educational video player
│   ├── Virtual desktop interface
│   ├── Three lab-role interfaces
│   ├── Journals
│   └── Leaderboard
├── Backend: ASP.NET Core (Modular Monolith)
│   ├── Identity: accounts and permissions
│   ├── LearningContent: lessons and resources
│   ├── Labs: lab-session lifecycle
│   ├── Assessment: validation and assessment rules
│   ├── Progress: progress and completion tracking
│   ├── Gamification: points and badges
│   └── Administration: content management
├── PostgreSQL: users, content, sessions, results, and points
├── Background worker: cleanup and deferred tasks
└── Isolated lab service (Docker)
    ├── Container lifecycle and constraints
    ├── Vulnerable practice applications and tools
    └── Educational evidence and logs
```

Settled architectural decisions:

- **Modular Monolith, not Microservices:** It supports the development speed and integration needs of a graduation team while retaining clear, testable module boundaries.
- **The lab service must be separated from the API process:** Running untrusted code is a different security concern from managing users and educational content.
- **REST first:** GraphQL will only be added if a demonstrated need justifies it.
- **Labs use temporary, network-isolated containers with restricted permissions.** They are destroyed after the session. User commands must never execute inside the API process.
- **A content-management interface** should allow categories, lessons, and scenarios to be added without changing application code, while strictly separating narrative/text content from lab execution configuration.

---

# 15. Educational and Theoretical Foundations

- **Situated learning:** Skills are acquired in the context where they are used, not in isolation.
- **Learning by doing:** Learners perform a task and analyze its result instead of only watching a video.
- **Instructional scaffolding:** Detailed hints are available by default, then support is reduced to encourage independent performance.
- **Feedback:** Errors are explained and learners are given an opportunity to correct them, rather than receiving generic failure messages.
- **Learning from consequences:** The impact of a decision is presented realistically, with an opportunity to recover rather than being used as punishment.
- **Dual and three-role perspective:** The design assumes that connecting discovery, investigation, and remediation may build deeper understanding. This assumption will be tested in the study rather than treated as an established result.
- **Reflective writing:** Journals support retention and provide qualitative research data.
- **Motivation:** Points and badges are supporting tools informed by Self-Determination Theory (SDT), not the core of the learning experience.

The final academic report will document the sources supporting these principles.

---

# 16. Scope of Implementation: Declared Commitment

This is one of the most important decisions in the project description and should be communicated clearly to the supervisor:

The envisioned product—ten fully developed categories—is not the same as the deliverable the team commits to at the defense. Because the two paths, connected storylines, three roles, content, and assessments multiply the workload, the committed scope is:

1. **One fully developed episode (Injection):** an educational story scene showing the main character before employment; the technical explanation, embedded external educational video, and quiz; then a chronological transition to the period when the character works at NoorTech; the lab introduction and role-dependent transition scenes; all three roles; journals; and automated assessment.
2. **The core user journey:** home page, registration/login, landing dashboard, and selection between the Learning Path and Labs Path.
3. **Measurement of the episode’s actual cost:** actual work hours for each component, including content writing, scene production, and lab preparation.
4. **Extension to additional categories** according to the time remaining after measurement. The number should be agreed with the supervisor early, not announced at the end.
5. **An evaluation study** using the prototype.
6. **Technical and academic documentation and a research paper.**

The guiding principle is that one carefully completed episode is stronger academically and in terms of safety than ten incomplete ones. If time becomes limited, the number of episodes is reduced—not lab safety or assessment quality.

**Video-production boundaries:** The Learning Path contains two distinct video types: a story scene prepared by the team, showing the main character learning the category before employment; and an embedded external educational video from a trusted source explaining the technical aspects. The Labs Path contains a story introduction to an incident at NoorTech after the character joins the company, as well as transition scenes when Blue Team or Developer is selected. The educational story-scene template, lab introduction, and transition scenes will first be implemented for the Injection episode, and the cost of extending them will then be measured. The project does not aim to produce long or cinematic animations for every category and role; it aims to produce short, consistent scenes that can be reused.

Explicitly outside the first release: a complete virtual operating system, security tools built from scratch, long or expensive animated videos for every category and role, commercial SIEM simulation, multiple system templates, multiplayer, a mobile app, accredited certifications, paid enterprise paths, and free-text assessment.

---

# 17. First-Release Acceptance Criteria

1. A home page that explains the project and provides Get Started and Login options.
2. Registration and login, followed by access to the landing dashboard.
3. Two clearly presented paths: Learning and Labs.
4. Display of the ten OWASP categories in each path, according to the implemented release scope.
5. Access to the category’s Learning page, showing a story scene in which the main character is still in the pre-employment stage, followed by written material, an embedded external educational video or alternative link, and a multiple-choice quiz.
6. Navigation from the category’s Learning page to the same category’s lab without requiring the quiz to be passed.
7. Display of the lab’s story introduction, which takes place after the character has joined NoorTech, with the option to skip it and receive an equivalent summary.
8. Selection of a difficulty level that controls the amount of available hint support.
9. Selection of Red Team, Blue Team, or Developer, with a Blue Team/Developer transition scene displayed when either is selected.
10. Display of task details and tools appropriate to the selected role.
11. Completion of the discovery task and verification of its security outcome.
12. Analysis of evidence in the investigation interface through a genuine reasoning chain.
13. Code modification in the remediation task and successful execution of automated tests.
14. Direct entry into one role or completion of the full episode, if that option is enabled.
15. Writing and saving the learner’s journal.
16. Correct persistence of progress and sessions.
17. Prevention of points being awarded based solely on client-side data.
18. Automatic termination of lab sessions and cleanup of their resources.
19. Testing the interface and narrative with a small group of users and documenting their feedback.

---

# 18. Team Structure and Decision-Making (12 Members)

| Team               | Members | Responsibilities                                                                         |
| ------------------ | ------: | ---------------------------------------------------------------------------------------- |
| Content and Story  |       2 | Lessons, scenarios, hints, questions, journals, and references                           |
| Backend (.NET)     |       2 | API, database, assessment logic, progress and points, lab integration                    |
| Frontend (Next.js) |       3 | Learning pages, narrative, virtual desktop, role interfaces, and journals                |
| Sec and DevOps     |       3 | Docker, vulnerable practice applications, security isolation, deployment, and monitoring |
| UI/UX              |       2 | Design Interface of users and Thier Experience                                           |
With a team of this size, the main risk is decision speed rather than team capacity. Therefore:

- The architecture lead and content lead must have clearly defined final decision-making authority, not merely coordination responsibilities.
- Content and scenario templates must have announced freeze dates and be treated as formal deliverables.
- API contracts must be agreed upon before work is distributed, with frequent integration of small increments and a shared test environment.
- An integration and release owner must track what is complete, what is waiting, and what is blocked.

---

# 19. Work Plan

| Phase | Deliverables |
| --- | --- |
| 1. Analysis and experience design | Requirements document; home-page and sign-in journey; definition of the two paths; Learning page design; the two narrative timelines (pre-employment / working at NoorTech); three-role model; pilot category; lab-isolation requirements |
| 2. Content and story design | Selection of the Injection scenario; technical explanation and quiz; selection of the external educational video; writing the educational story scene showing the character before employment; writing the lab introduction and transition scenes after he joins the company; updating the World Bible to control chronology and the development of the character and company |
| 3. Engineering design and foundation | Frontend and backend projects; database; authentication; API contracts; build and deployment pipeline; landing dashboard and navigation between the two paths |
| 4. Critical technical experiments | Isolated lab execution; session lifecycle; tool presentation; automated task validation; real-time communication test where needed |
| 5. Pilot prototype (Injection episode) | Learning Path scene set before employment; technical explanation and embedded educational video; lab introduction set after the character joins NoorTech; difficulty and role selection; transition scenes; three roles; journals; automated tests; complete episode; and isolation verification |
| 6. User evaluation | Pilot study with 5–10 students; identification of educational and technical issues; completion-time measurement; evaluation of story clarity, transitions, and tools; decisions about what to simplify before extension |
| 7. Expansion | After measuring the actual cost of the first episode, reuse the templates and add categories according to the agreed schedule; develop the story and the growth of the company and its characters across episodes |
| 8. Analytics, documentation, and delivery | Reliable points system; progress analytics; evaluation study; technical and academic documentation; research paper; deployment; and final presentation |

The schedule will be estimated bottom-up. The actual cost of the first episode will be measured—including content writing, storytelling, clip production, lab preparation, and testing—and used to estimate the remaining work. A final timeline should not be promised before this measurement. If time is insufficient, the number of categories or the level of video production will be reduced, not assessment quality or lab safety.

---

# 20. Research and Contributions

### 20.1 Research Questions

- **Main question:** Is the experience combining storytelling, discovery, investigation, remediation, and documentation associated with a measurable improvement in learners’ understanding of web application security?
- **Sub-questions:** Which roles take the most time and generate the most repeated errors? How is hint usage associated with completion rates? Does performance differ by difficulty level? Do users find the role interfaces clear?

### 20.2 Study Design

First, conduct a pilot study to identify usability problems. If time and academic procedures allow, follow it with a quasi-experimental study: a pre-test, the learning experience, a post-test, and a delayed test, accompanied by engagement and usability questionnaires. If a conventional comparison group is used, the team must produce equivalent conventional learning content for that group and account for the effort in the plan. Improvement must not be attributed to storytelling alone if the groups differ in other factors.

### 20.3 Proposed Contributions

1. **A measurable platform:** The system records learner actions within the experience (which evidence was opened, in what order, which hints were used, and how long tasks took), making the platform itself a measurement instrument. This is a methodological contribution beyond “a platform plus a questionnaire.”
2. **A reusable three-role assessment template:** Discovery, investigation, and remediation can be reused in other cybersecurity learning contexts.
3. **Journals as a qualitative measurement tool:** Learners’ reflections are analyzed alongside quantitative data to understand their reasoning.

Scientific integrity rule: Actual results must be reported as they are, even if they do not confirm the hypothesis. A statistical success threshold must not be selected in advance without calculating the required sample size.

---

# 21. Risks and Mitigation Plans

| Risk | Mitigation |
| --- | --- |
| Scope expansion (two paths × three roles × ten categories) | Build one episode first, measure its cost before expansion, agree on the scope with the supervisor early, and use standardized templates. |
| The investigation stage becomes a reading test | Require a genuine reasoning chain in each task and test task quality with a student who has not seen the scenario. |
| Cost of visual content and multiple timelines | Clearly separate pre-employment educational story scenes, external technical videos, lab introductions set after the character joins NoorTech, and role-transition scenes. Start production with the Injection episode to measure the cost of each type. Use consistent visual and narrative templates and defer long, expensive animations. |
| Difficulty assessing the quality of analysis | Tie questions to specific evidence, accept a predefined set of valid conclusions, provide explanations after answers, and defer free-text assessment. |
| Loss of context during direct entry | Provide a short contextual summary and consistent prepared evidence. Explain the objective and expected output without revealing the answers. |
| Learners become confused between roles | Provide a short introduction before each role, clear visual differentiation, and an explanation of how the roles connect in the full episode. |
| Lab isolation failure or unsafe configuration | Use restricted permissions, block unnecessary network access, set resource and time limits, perform automatic cleanup, and test misuse cases before deployment. |
| Points manipulation | Calculate points on the server, prevent duplicate awards, and log sensitive operations. |
| Arabic content and terminology quality | Technically review each lesson, linguistically review dialogue, test with the target audience, and standardize translations of technical terms. |
| Narrative contradictions or confusion between learning and employment stages | Maintain a World Bible that ensures Learning scenes occur before employment and lab events occur after the character joins NoorTech. Document the development of the character, company, and supporting cast; assign one owner and set freeze dates. |
| Integration failures between teams | Define API contracts early, integrate small increments frequently, maintain a shared test environment, and assign a clear integration owner. |

---

# 22. Ethical and Legal Considerations

- All target applications used for training are fictional and owned by the project. Labs must never be used to target real-world systems.
- Labs are network-isolated with restricted permissions and are destroyed after each session.
- All names and characters are fictional and do not refer to existing entities.
- The leaderboard uses optional display names and allows users to hide their accounts entirely.
- Every exploitation lesson is followed by investigation and remediation. Content is framed for defensive education and must not become an operational offensive guide.
- No personal information or secrets are included in educational logs.
- Study participants’ data is anonymized and limited to what is necessary, with prior consent in accordance with academic procedures.
- Licenses for all integrated open-source software and components must be reviewed.

---

# 23. Originality and Differentiation

- Entertainment-focused cyber narrative games (such as Hacknet and Cyber Manhunt) demonstrate the appeal of the format, but they are not Arabic educational platforms.
- Related research and projects (including The XSS Game, Grown-Up Blues, and IEEE serious-game studies) provide examples of isolated vulnerability training or general awareness experiences.
- Commercial story-based products such as Kontra offer short illustrated narratives in English, without lab simulation, a complete incident-handling cycle, or real tools.
- **The intended differentiators** are a continuous Arabic narrative featuring one evolving main character and a growing company across episodes; transition scenes connecting the character with Red Team, Blue Team, and Developer roles; two paths for learning and labs; a complete handling cycle (discovery / investigation / remediation / documentation); real tools in isolated labs; and an instrumented platform that supports research. The degree of differentiation must be demonstrated through a documented comparative review, not assumed.
- **Academic positioning:** The project builds on established frameworks (such as RAD-SIM and related work) and does not claim absolute novelty without documented research. This is the academically appropriate position.

---

# 24. Scientific and Technical References

- OWASP Top 10:2025 — primary reference for the categories.
- OWASP Web Security Testing Guide — testing guidance.
- OWASP Cheat Sheet Series — prevention and remediation practices.
- Verizon Data Breach Investigations Report — statistical context for incidents, with the report year and cited figures documented.
- Research on serious games in cybersecurity education, including The XSS Game, Grown-Up Blues, and relevant IEEE studies.
- Literature on situated learning, learning by doing, and instructional scaffolding.
- Literature on reflective writing and learning journals.
- Literature on motivation and gamification, including Self-Determination Theory.
- React, Next.js, ASP.NET Core, PostgreSQL, and Docker documentation, along with the licenses of integrated tools.

Study titles, publication details, and findings must be verified against their original sources before they are cited in the final report.
