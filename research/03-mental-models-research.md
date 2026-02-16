# Research Report: High-Level Mental Models for Non-Coder Vibe Coders

## Executive Summary

Non-coder vibe coders need a set of mental models that allow them to think about software systems, make architectural decisions, and effectively orchestrate AI agents -- all without writing code themselves. This report identifies 10 essential mental model categories, synthesized from current industry thinking (2025-2026), that form the conceptual foundation every vibe coder needs.

---

## 1. Systems Thinking: Seeing the Whole Machine

### The Core Concept

Systems thinking means stepping out of the details to see the bigger picture. A system is a whole that contains two or more parts, all interconnected, where each part influences the behavior of the whole. The system has **emergent behavior** that individual parts lack -- just as a car provides transportation, but no single car part can do that alone.

### Why It Matters for Vibe Coders

Traditional thinking breaks problems into separate parts, which leads to silos, bottlenecks, and duplicate work. Systems thinking considers the thing as a whole. For vibe coders, this means:

- **Understanding dependencies**: Changing one component affects others
- **Identifying feedback loops**: User behavior affects system load, which affects user experience, which affects user behavior
- **Recognizing emergent problems**: Issues that only appear when components interact (e.g., two features that work perfectly alone but conflict when combined)

### Practical Mental Model: "The Ripple Effect"

Before requesting any change, ask: "What else does this touch?" Every feature, database change, or API modification sends ripples through the system. A vibe coder who thinks in systems will naturally prompt AI with better constraints because they anticipate side effects.

### Key Principle

> "Rather than breaking things down into separate parts, consider the thing as a whole -- this streamlines work and boosts collaboration." -- O'Reilly on Systems Thinking in Software

**Sources:**
- [Systems Thinking for Software Engineers (Medium)](https://medium.com/@scott-altham/systems-thinking-a-quick-introduction-for-software-engineers-c99976246729)
- [O'Reilly: The Critical Role of Systems Thinking](https://www.oreilly.com/radar/the-critical-role-of-systems-thinking-in-software-development/)
- [Scott Hanselman: Systems Thinking for New Coders](https://www.hanselman.com/blog/systems-thinking-as-important-as-ever-for-new-coders)
- [Systems Thinking in Software Development Guide](https://daily.dev/blog/systems-thinking-in-software-development-guide)

---

## 2. Data Flow Intuition: Following Information Through the System

### The Core Concept

Data flow is the lifeblood of any software system. It refers to how information moves from source to destination through a specific sequence of steps: **ingestion (input) -> processing (transformation) -> storage -> output/delivery**.

### The Mental Model: "Follow the Data"

Every software application can be understood by tracing what happens to data:

1. **Input**: Where does data enter? (User form, API call, file upload, sensor)
2. **Processing**: What happens to it? (Validation, transformation, calculation, filtering)
3. **Storage**: Where does it live? (Database, cache, file system, memory)
4. **Output**: Where does it go? (Screen display, API response, email, report)

### Why Vibe Coders Need This

When describing what you want to an AI, the most effective prompts describe data flow:
- "The user enters their email, we validate it, store it in the users table, and send a confirmation email"
- NOT: "Make a signup feature"

### Data Flow Diagrams (DFDs)

DFDs use simple symbols -- rectangles, circles, and arrows with short text labels -- to show data inputs, outputs, storage points, and routes between destinations. They are popular because they convey information in an easily digestible manner to both technical and non-technical audiences.

### Practical Application

Before asking AI to build anything, draw (even on paper) the data flow:
- What goes in?
- What happens to it?
- Where is it stored?
- What comes out?

**Sources:**
- [Confluent: What Is Data Flow? The Beginner's Guide](https://www.confluent.io/learn/data-flow/)
- [Lucidchart: What is a Data Flow Diagram](https://www.lucidchart.com/pages/data-flow-diagram)
- [IBM: What Is a Data Flow Diagram](https://www.ibm.com/think/topics/data-flow-diagram)
- [Miro: What is a Data Flow Diagram?](https://miro.com/diagramming/what-is-a-data-flow-diagram/)

---

## 3. State Management: Why Apps "Forget" and Show Wrong Data

### The Core Concept

State is the **memory of your application**. It stores:
- What the user has done (clicked a button, filled a form)
- What is happening right now (a modal is open, data is loading)
- Data fetched from external sources (API responses)
- Current configuration (dark mode, language, user preferences)

### Why Apps Break: The State Problem

Most bugs and crashes are caused by **unexpected combinations of state**. Common failure modes:

1. **Data Loss from System Events**: The operating system can kill an app with little warning. If state is not saved, it is gone forever.
2. **Inconsistent State**: Multiple components manipulate the same data without knowing about each other, leading to contradictions.
3. **Stale Data (Multiple Copies Problem)**: If data is cached in multiple places, changing it in one place leaves old values elsewhere -- causing "ghost data" that surprises users.
4. **Unexpected Side Effects**: When one part of the app changes shared state, other parts that depend on that state may break.

### The Mental Model: "Single Source of Truth"

The key insight: data should live in ONE place, and everything else should reference that one place. When you have multiple copies of the same information, they inevitably get out of sync.

### Practical Application for Vibe Coders

When prompting AI to build features, specify:
- Where should this data live? (Database? Local state? URL parameters?)
- What happens when the user refreshes the page?
- What happens when two users edit the same thing simultaneously?
- What happens if the network drops mid-operation?

**Sources:**
- [State Management Explained (JavaPro)](https://javapro.io/2025/09/24/state-management-explained/)
- [What is Application State Management (Document360)](https://document360.com/blog/application-state-management/)
- [State Management Pitfalls (LogicLoom)](https://logicloom.in/state-management-gone-wrong-avoiding-common-pitfalls-in-modern-ui-development/)
- [State Management - Building Mobile Apps at Scale](https://www.mobileatscale.com/content/posts/01-state-management/)

---

## 4. API Thinking: How Services Talk to Each Other

### The Core Concept

An API (Application Programming Interface) is how one piece of software asks another piece of software to do something. Think of it as a **menu at a restaurant**: it defines what you can order (the endpoints), what you need to provide (the request), and what you will get back (the response).

### REST vs. GraphQL: Two Conversation Styles

**REST APIs** are like ordering fixed meals:
- Each resource has a URL (e.g., `/users/123`)
- You use standard actions: GET (read), POST (create), PUT (update), DELETE (remove)
- **The problem**: You always get the full meal -- even if you only wanted the appetizer (this is called "overfetching")

**GraphQL** is like ordering a la carte:
- Single endpoint where you specify exactly what you want
- You describe the data you need, and only that data is returned
- More efficient for mobile apps and complex UIs

### The Mental Model: "Contracts Between Services"

APIs are contracts. Service A promises: "If you send me X, I will give you back Y." This contract thinking is critical for vibe coders because:

- You need to understand what data your app needs from external services
- You need to define what your app promises to provide
- Breaking a contract (changing an API) can break everything that depends on it

### Practical Application

When designing features, think about:
- What external data does this feature need? (Maps, payments, authentication)
- What data does this feature expose to others?
- What happens when an API call fails? (Loading states, error messages, retries)

**Sources:**
- [AWS: GraphQL vs REST API](https://aws.amazon.com/compare/the-difference-between-graphql-and-rest/)
- [IBM: GraphQL vs REST](https://www.ibm.com/think/topics/graphql-vs-rest-api)
- [ProductPlan: 5 Technical Concepts for Non-Technical PMs](https://www.productplan.com/learn/non-technical-product-manager/)
- [Postman: GraphQL vs REST](https://blog.postman.com/graphql-vs-rest/)

---

## 5. UX/Product Sense: What Separates Good Software from Bad

### The Core Concept

Good software is not just about features -- it is about **behavior**. Product sense is the ability to judge whether software serves its users well, independent of visual design or technical implementation.

### Key Principles

1. **Form Follows Function**: Every interface element should exist because it serves a purpose, not because it looks nice
2. **Predictability**: Users should always know what will happen when they take an action
3. **Recoverability**: Users should be able to undo mistakes easily
4. **Progressive Disclosure**: Show only what is needed now; reveal complexity gradually
5. **Feedback**: The system should always communicate what it is doing

### The Mental Model: "Would a Tired Person at 11 PM Understand This?"

The best software requires zero explanation. If you need to add a tutorial, the interface has failed. Vibe coders should test their products by imagining the least patient, least attentive user.

### What Technical Debt Feels Like to Users

Code that was meant to be temporary often survives to become product functionality used by paying customers. Users experience technical debt as:
- Slowness that gets worse over time
- Features that work "most of the time"
- Inconsistent behavior between different parts of the app
- Mysterious errors with unhelpful messages

### Practical Application

Before shipping, ask:
- Can someone use this feature without reading instructions?
- What happens when things go wrong? (Empty states, errors, loading)
- Is the happy path the most obvious path?
- Does the app respect the user's time?

**Sources:**
- [Loomery: Lessons in AI-Assisted Coding from a Non-Engineer](https://www.loomery.com/insights/lessons-in-ai-coding-from-a-non-engineer)
- [Ali Kamalizade: Explaining Software Engineering to Non-Engineers](https://ali-dev.medium.com/explaining-software-engineering-concepts-to-non-engineers-166291337ef4)
- [Aman Agarwal: The Non-Engineer's Ultimate Guide to Software](https://aman-agarwal.com/2021/05/25/ultimate-guide-to-software/)

---

## 6. Cost and Performance Awareness: Understanding What You Are Paying For

### The Core Concept

Every software operation costs money. Cloud computing follows a usage-based model where you pay for what you consume across three main categories:

1. **Compute**: Processing power (CPU/GPU time, memory usage) -- the "thinking" your app does
2. **Storage**: Keeping data around (databases, file storage, backups) -- the "memory" your app uses
3. **Bandwidth/Networking**: Moving data between places (API calls, user downloads, cross-region traffic) -- the "communication" your app does

### Hidden Costs That Surprise Vibe Coders

- **Data retrieval charges**: Storing data is cheap; reading it back can be expensive
- **Cross-region traffic**: Moving data between geographic regions costs more than local access
- **AI API costs**: Every call to GPT-4, Claude, or other models costs real money that scales with usage
- **Idle resources**: Servers running with no traffic still cost money
- **Support tiers**: Enterprise support from cloud providers can cost thousands per month

### The Mental Model: "Every Click Has a Price Tag"

When a user clicks a button, trace the costs:
- Server compute time to process the request
- Database query time and storage I/O
- Network bandwidth to send the response
- Third-party API calls (maps, payments, AI)

### Practical Application

When designing features, consider:
- How many API calls does this feature make per user action?
- Are we storing data we do not need?
- Can we cache responses instead of fetching them every time?
- What happens to costs if we get 10x more users?

**Sources:**
- [Vantage: Cloud Costs Every Programmer Should Know](https://www.vantage.sh/blog/cloud-costs-every-programmer-should-know)
- [Sedai: Complete Guide to Cloud Computing Costs 2026](https://sedai.io/blog/determining-the-breakdown-of-cloud-computing-costs-in-2025)
- [AceCloud: How To Estimate Cloud Server Costs In 2026](https://acecloud.ai/blog/cloud-server-pricing-guide/)

---

## 7. Security Mindset: Thinking About What Could Go Wrong

### The Core Concept

Security is not a feature you add -- it is a way of thinking. The security mindset means constantly asking: "How could someone misuse this?" For vibe coders, this is especially critical because AI-generated code has significant security blind spots.

### Alarming Statistics

- **45% of all AI-generated code introduces security vulnerabilities** (research across 100+ LLMs)
- LLMs failed to secure code against Cross-Site Scripting in **86% of cases**
- **5% of AI-generated code** references non-existent packages (which attackers can hijack)
- Testing of 5 vibe coding tools found **69 vulnerabilities across 15 test apps**, with half a dozen rated "critical"

### Common Vulnerability Categories for Vibe Coders

1. **Injection Attacks**: When user input is treated as commands (SQL injection, XSS)
2. **Hardcoded Secrets**: AI often puts API keys and passwords directly in code
3. **Missing Authentication**: Pages or APIs accessible without login
4. **Weak Authorization**: Users can access other users' data by changing a URL parameter
5. **Supply Chain Attacks**: AI recommends packages that are malicious or do not exist
6. **Prompt Injection**: Attackers manipulating AI tools through connected services (Slack, Jira)

### The Mental Model: "Assume Everyone is Trying to Break In"

For every feature, ask:
- What if someone puts malicious code in this input field?
- What if someone changes the URL to access someone else's data?
- What if someone intercepts the data in transit?
- What secrets are visible in the code?

### The "STRIDE" Framework (Simplified)

- **S**poofing: Can someone pretend to be someone else?
- **T**ampering: Can someone modify data they should not?
- **R**epudiation: Can someone deny doing something?
- **I**nformation Disclosure: Can someone see data they should not?
- **D**enial of Service: Can someone make the system unavailable?
- **E**levation of Privilege: Can someone gain access they should not have?

### Practical Application

Always include in your AI prompts:
- "Validate all user inputs"
- "Use parameterized queries for database operations"
- "Never hardcode secrets -- use environment variables"
- "Implement proper authentication and authorization"
- "Sanitize all output displayed to users"

**Sources:**
- [Kaspersky: Security Risks of Vibe Coding (2025)](https://www.kaspersky.com/blog/vibe-coding-2025-risks/54584/)
- [Contrast Security: Vibe Coding Security Risks](https://www.contrastsecurity.com/glossary/vibe-coding)
- [BayTech Consulting: 45% of AI-Generated Code is a Security Risk](https://www.baytechconsulting.com/blog/ai-vibe-coding-security-risk-2025)
- [Lawfare: Security Risks of AI-Generated Code](https://www.lawfaremedia.org/article/when-the-vibe-are-off--the-security-risks-of-ai-generated-code)
- [CSO Online: Vibe Coding Tools Prone to Critical Flaws](https://www.csoonline.com/article/4116923/output-from-vibe-coding-tools-prone-to-critical-security-flaws-study-finds.html)
- [Databricks: The Dangers of Vibe Coding](https://www.databricks.com/blog/passing-security-vibe-check-dangers-vibe-coding)

---

## 8. Technical Taste: Judging Architecture Without Reading Code

### The Core Concept

Technical taste is the ability to recognize good software architecture without necessarily understanding the implementation details. It is distinct from technical skill -- "you can be technically strong but have bad taste, or technically weak with good taste."

### What Good Taste Looks Like

> "Taste in software architecture is not about style or fashion, but about judgment -- the quiet discipline of choosing what to include, what to leave out, and what must endure." -- Burzcast

Characteristics of good architectural taste:
- **Complexity is treated as a cost**, not a badge of sophistication
- Systems are **easier to reason about** (you can explain them simply)
- They **accommodate change** without collapsing
- They **age gracefully** without constant intervention
- **Simplicity is not minimalism** -- it is generosity toward the future

### The Mental Model: "Can You Explain It on a Napkin?"

If the architecture of your system cannot be sketched on a napkin with boxes and arrows that a non-engineer could follow, it is probably too complex. Good architecture has a clear story: "Data comes in here, gets processed here, is stored here, and comes out here."

### How to Develop Technical Taste Without Coding

1. **Study failure stories**: Read postmortems from companies about outages and failures
2. **Ask "Why?"**: When engineers propose solutions, ask why they chose that approach over alternatives
3. **Look for patterns**: Notice when similar problems keep appearing -- it usually means the architecture is fighting the product
4. **Value boring technology**: Mature, well-understood tools almost always beat cutting-edge ones for real products
5. **Count the moving parts**: Fewer components that each do one thing well beats many components with overlapping responsibilities

### Evaluating Architecture: 11 Key Questions

Key criteria include: scalability, performance, security, maintainability, reliability, interoperability, cost efficiency, flexibility, compliance, user experience, and disaster recovery capabilities.

**Sources:**
- [Sean Goedecke: What is "good taste" in software engineering?](https://www.seangoedecke.com/taste/)
- [Burzcast: On Taste in Software Architecture](https://burzcast.com/newsroom/on-taste-in-software-architecture)
- [Pragmatic Engineer: What is Good Software Architecture?](https://newsletter.pragmaticengineer.com/p/what-is-good-software-architecture)
- [CIO: Evaluating Technical Architecture - 11 Key Criteria](https://www.cio.com/article/189465/evaluating-technical-architecture-11-key-criteria-and-how-to-apply-them.html)
- [Pragmatic Engineer: Architecture Overrated, Clear Design Underrated](https://blog.pragmaticengineer.com/software-architecture-is-overrated/)

---

## 9. Prompt Engineering for Code Generation: Describing What You Want

### The Core Concept

The quality of AI-generated code depends directly on the quality of your prompts. For vibe coders, prompt engineering IS the primary skill -- it replaces coding as the main way to express intent.

### Essential Techniques

**1. Be Specific About What You Want**
- BAD: "Make a login page"
- GOOD: "Create a login page with email and password fields. Email should be validated. Password must be at least 8 characters. On success, redirect to /dashboard. On failure, show an inline error message below the form. Use session-based authentication."

**2. Provide Context and Constraints**
- Specify the target environment (Node.js 18, Python 3.10+, etc.)
- State security requirements explicitly
- Mention performance constraints
- Reference existing code patterns in your project

**3. Include Examples and Test Cases**
Examples act as implicit constraints, guiding the model toward the behavior you expect. Show sample inputs and expected outputs.

**4. Use Structured Prompts**
- Start with context (what exists)
- State the goal (what you want)
- Define constraints (what to avoid)
- Specify acceptance criteria (how to verify)

**5. Leverage Context Architecture**
Modern tools like Claude Code use CLAUDE.md files and Cursor uses rules files to provide persistent context. These act as "always-on prompts" that guide every interaction:
- Architecture decisions
- Coding standards
- Project-specific conventions
- Security requirements

### The Mental Model: "Write a Spec, Not a Wish"

The difference between amateur and professional vibe coding is the difference between wishes and specifications. A wish says "make it work." A spec says exactly what "work" means, including edge cases, error handling, and success criteria.

### Advanced Technique: Context Engineering

Context engineering is closer to designing software than writing prompts -- you are building a system that works across many interactions, over time, and across various inputs. This includes:
- Rules files that persist across sessions
- Architecture documentation that AI reads before coding
- Task breakdowns saved as project files
- Test specifications that define "done"

### Trigger Words for Deeper AI Reasoning

In Claude Code, specific phrases trigger different levels of reasoning depth: "think" < "think hard" < "think harder" < "ultrathink"

**Sources:**
- [Addy Osmani: The Prompt Engineering Playbook for Programmers](https://addyo.substack.com/p/the-prompt-engineering-playbook-for)
- [Graphite: How to Write Better Prompts for AI Code Generation](https://graphite.com/guides/better-prompts-ai-code)
- [OpenAI: Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering)
- [Practical Context Engineering for Vibe Coding with Claude Code](https://abvijaykumar.medium.com/practical-context-engineering-for-vibe-coding-with-claude-code-6aac4ee77f81)
- [Laurent Cazanove: A Structured Approach to Cursor Vibe Coding](https://laurentcazanove.com/blog/vibe-coding-tutorial)

---

## 10. Version Control: Why Git Matters

### The Core Concept

Version control is a system that records changes to files over time so you can recall specific versions later. Git, the dominant version control system, allows multiple people to work on the same project simultaneously without overwriting each other's work.

### Key Concepts Explained Simply

**Repository (Repo)**: A project folder that Git is tracking. It contains all your files plus the complete history of every change ever made.

**Commit**: A snapshot of your project at a specific moment. Think of it as a "save point" in a video game -- you can always go back to any previous save point.

**Branch**: A parallel version of your project where you can make changes without affecting the main version. Like drafting a chapter of a book in a separate document before adding it to the manuscript.

> "A branch tells the story of a feature, e.g. 'fast sequence extraction' or 'Python interface' or 'fixing bug in matrix inversion algorithm'."

**Merge**: Combining changes from one branch into another. Like incorporating your draft chapter into the main manuscript.

**Conflict**: When two people change the same line differently, Git cannot automatically decide which version to keep. A human must resolve the conflict.

### Why Git Matters for Vibe Coders

1. **Safety Net**: AI-generated code sometimes breaks things. Git lets you instantly revert to a working version.
2. **Experimentation**: Create branches to try different AI-generated approaches without risk.
3. **Collaboration**: Multiple AI sessions or human collaborators can work on different features simultaneously.
4. **History**: Every change is recorded with who made it and why, creating an audit trail.
5. **Rollback**: If AI introduces a security vulnerability, you can trace exactly when it was introduced and revert it.

### The Mental Model: "Time Travel for Code"

Git gives you the ability to travel back in time to any point in your project's history, create parallel timelines (branches) to explore different approaches, and merge timelines back together when you are satisfied with the results.

### Practical Application

Even as a vibe coder, you should:
- Commit frequently (after each working feature)
- Write descriptive commit messages ("Add user login with email validation" not "update code")
- Use branches for experimental features
- Never commit secrets (API keys, passwords) -- use `.gitignore`

**Sources:**
- [Git Official: Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
- [Atlassian: Git Merge Tutorial](https://www.atlassian.com/git/tutorials/using-branches/git-merge)
- [CodeRefinery: Branching and Merging](https://coderefinery.github.io/git-intro/branches/)
- [Demystifying Git (redShift Recruiting)](https://www.redshiftrecruiting.com/demystifying-version-control-git)

---

## Bonus: The Orchestrator Mental Model (2026)

### The Evolution: Vibe Coder -> Orchestrator -> Agentic Engineer

The role of the software creator is evolving rapidly:

**Phase 1 - Vibe Coding (Early 2025)**: Conversational, casual interaction with one AI. "Just see if it works." Andrej Karpathy coined this term in February 2025.

**Phase 2 - Agentic Engineering (2026)**: Orchestrating multiple AI agents with structured oversight. Karpathy now says vibe coding is "passe" -- the new default is "agentic engineering" where "you are not writing the code directly 99% of the time... you are orchestrating agents who do and acting as oversight."

**Phase 3 - Cosmic Orchestrator (Emerging)**: Managing fleets of AI agents, setting goals and success criteria, and reviewing results -- more like a CTO than a coder.

### The Key Insight from Addy Osmani

> "AI does the implementation. Human owns the architecture, quality, and correctness."

Developers succeeding with agentic engineering spend **70% of their time on problem definition and verification strategy, 30% on execution** -- the inverse of traditional development, but total time decreases dramatically.

### The 80% Problem

The biggest differentiator between vibe coding and agentic engineering is **testing**. A solid test suite allows AI agents to iterate until tests pass. Without tests, AI gets you 80% of the way there, and the last 20% -- the hard part -- takes longer than building it from scratch.

### What This Means for Non-Coders

Notably, agentic engineering is accessible to non-coders. One author built five products using this methodology without writing a single line of code. The critical skills are:
- Clear problem definition
- Effective constraint specification
- Quality judgment (reviewing AI output)
- Understanding system architecture at a conceptual level

**Sources:**
- [Addy Osmani: Agentic Engineering](https://addyosmani.com/blog/agentic-engineering/)
- [Addy Osmani: The 80% Problem in Agentic Coding](https://addyo.substack.com/p/the-80-problem-in-agentic-coding)
- [Addy Osmani: Conductors to Orchestrators](https://addyosmani.com/blog/future-agentic-coding/)
- [The New Stack: Vibe Coding is Passe (Karpathy)](https://thenewstack.io/vibe-coding-is-passe/)
- [Glide: What is Agentic Engineering](https://www.glideapps.com/blog/what-is-agentic-engineering)
- [Medium: Vibe Coding Revolution - Why 2026 Belongs to Orchestrators](https://medium.com/@techie.fellow/the-vibe-coding-revolution-why-2026-belongs-to-the-orchestrators-46b32d530133)

---

## Synthesis: The Mental Model Stack

These 10 mental models form a progressive stack for vibe coders:

### Foundation Layer (Think About Systems)
1. **Systems Thinking** -- See the whole, not just parts
2. **Data Flow Intuition** -- Follow information through the system
3. **State Management** -- Understand why apps "forget"

### Communication Layer (Think About Interfaces)
4. **API Thinking** -- Understand how services talk
5. **UX/Product Sense** -- Judge software by behavior, not features

### Governance Layer (Think About Consequences)
6. **Cost Awareness** -- Every operation has a price
7. **Security Mindset** -- Assume everything can be misused
8. **Technical Taste** -- Judge quality without reading code

### Execution Layer (Think About Process)
9. **Prompt Engineering** -- Describe intent precisely
10. **Version Control** -- Manage change safely

### The Orchestrator Layer (Tying It All Together)
11. **Agentic Engineering** -- Orchestrate AI agents as an architect, not a coder

### Key Takeaway

The vibe coder who masters these mental models transforms from someone who "asks AI to code stuff" into a **software architect who happens to express intent through natural language rather than programming languages**. The mental models are the same ones that senior engineers use -- the execution medium has changed, but the thinking has not.

---

*Research compiled February 2026. Sources span 2019-2026, with emphasis on 2025-2026 developments in vibe coding and agentic engineering.*
