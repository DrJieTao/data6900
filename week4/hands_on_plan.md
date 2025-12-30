# Week 4 Hands-on: The Intelligent Network
**Course:** DATA 6900: AI-Powered Business Process Automation
**Theme:** Adaptive Systems (Routers, Loops, and Logic).

---

## 1. Sequence Overview

| Step | Activity | PDD Support |
| :--- | :--- | :--- |
| **0** | **Context Priming:** Load Week 3 PDD; Initialize `[SCRATCH_PAD]`. | (Foundation) |
| **1** | **Diagnostic Interview:** User reports failures; AI updates Scratch Pad. | **3.1 Strategy** |
| **2** | **Strategy Analysis:** AI compares Router vs. Loop vs. Parallel. | **3.1 Rationale** |
| **3** | **Visual Blueprint:** AI draws the Advanced Mermaid Map. | **3.2 Map** |
| **4** | **Component Design:** Defining the Router & Critic Specs. | **3.4 Specs** |
| **5** | **Logic OS & Trace:** Writing the Logic Block and running the Sim. | **3.3 & 3.5** |
| **6** | **The Compiler:** Generating the reproducible Master Prompt. | **(Deliverable)** |

---

## 2. Implementation Artifacts & Narration Guide

### Artifact 0: Context Priming (Step 0)
**Goal:** Initialize the AI with Week 3 constraints.

```markdown
# Role
You are a Senior AI Workflow Architect.

# Task
Read the attached **Week 3 PDD (Milestone 2)**. 
1. Extract the core Business Rules (Budget limits, MSA triggers).
2. Extract the Current Architecture (The 3-node Linear Chain).
3. Store these in a visible `[SCRATCH_PAD]` block at the start of your response.
4. **Stop** and await further instructions.

# Input
[PASTE WEEK 3 PDD HERE]
```

> **🎥 Video Narration Guide (Step 0)**
> *   "Welcome to Week 4. We are moving from **Pipelines** to **Networks**. But before we build, we must 'Load the Context'."
> *   "I am pasting my Week 3 PDD here. Watch how the AI creates a **Scratch Pad**. This is critical: AI has no long-term memory. We must force it to 'remember' our $10k limit and $5k MSA rule before we ask it to do anything complex."

---

### Artifact 1: The Diagnostic Interview (Step 1)
**Goal:** Interactive diagnosis of specific node failures.

```markdown
# Role
You are a Diagnostic Systems Engineer.

# Task
Interview me to identify specific failure points in the Week 3 Linear Pipeline.

# Protocol
1. **One Question at a Time:** Ask targeted questions about each node (Gatekeeper, Judge, Worker) individually.
2. **Focus Areas:**
   - Ask about **Gatekeeper** robustness (e.g., "Did it fail on vague inputs?").
   - Ask about **Judge** reasoning (e.g., "Did it make lazy assumptions?").
   - Ask about **Worker** tone/risk (e.g., "Did it promise things it shouldn't?").
3. **Action:** After each answer, update the `[SCRATCH_PAD]` with the specific "Failure Mode" identified.
```

> **🎥 Video Narration Guide (Step 1)**
> *   "Now, I play the role of the Lead Engineer. I'm not asking the AI to guess the problems; I'm reporting them."
> *   "I'll tell it: 'The Gatekeeper hallucinates when the input is noise.' and 'The Judge is lazy—it approves budgets without checking the MSA.' This is **Human-in-the-Loop Diagnostics**."
> *   "Watch the Scratch Pad update. These specific bugs are the justification we need for **PDD Section 3.1**."

---

### Artifact 2: The Strategy Analysis (Step 2)
**Goal:** Compare patterns (Router/Loop/Parallel) and get user buy-in.

```markdown
# Role
You are a Solutions Architect.

# Task
Analyze the "Failure Modes" in the `[SCRATCH_PAD]`. 
Compare three Adaptive Patterns: **Router**, **Evaluator-Optimizer Loop**, and **Parallel Workers**.

# Output Requirement
Provide a **Strategy Comparison Table**:

| Target Node | Proposed Pattern | Pros | Cons | Recommendation |
| :--- | :--- | :--- | :--- | :--- |
| **Gatekeeper** | **Router (Triage)** | Filters noise upstream. | Adds latency. | **RECOMMENDED** for Issue A (Noise). |
| **Judge** | **Evaluator Loop** | Enforces strict quality. | Can get stuck in loops. | **RECOMMENDED** for Issue B (Laziness). |
| **Judge** | **Parallel Workers** | Faster (Checks Budget & Legal at same time). | Harder to resolve conflicts. | **REJECTED** (Accuracy > Speed). |

# Constraint
Do not generate any code or diagrams yet.
**STOP** and ask: "Do you approve this architecture strategy?"
```

> **🎥 Video Narration Guide (Step 2)**
> *   "This is a key moment. We don't just pick patterns at random. We weigh the trade-offs."
> *   "Look at the table. It recommends a **Router** to fix the noise issue (Issue A) and a **Loop** to fix the laziness issue (Issue B)."
> *   "Crucially, look at the **Parallel Workers** row. It says 'REJECTED.' Why? Because for financial compliance, **Accuracy is more important than Speed.** This rationale goes straight into your PDD."

---

### Artifact 3: The Advanced Mermaid Map (Step 3)
**Goal:** Generate the PDD 3.2 Diagram based on the approved strategy.

```markdown
# Role
Visualization Expert (Mermaid.js).

# Task
Generate the **Week 4 Advanced Network Diagram** (`graph TD`) based on the **Approved Strategy**.

# Requirements (PDD 3.2)
1. **Implement the Router:** Insert a Decision Diamond (`{?}`) *before* the Gatekeeper. 
2. **Implement the Loop:** Insert a Critic Node and Decision Diamond *after* the Judge.
   - Show the "Feedback Arrow" looping back to the Judge.
3. **Styling:** 
   - Keep the Week 3 nodes in Orange (`#FFF4DD`).
   - Highlight the new **Router** and **Critic** nodes in Green (`#E6FFFA`) with a distinct border.

# Output
Provide the Mermaid code only.
```

> **🎥 Video Narration Guide (Step 3)**
> *   "Now we need to communicate this complexity to our boss. We ask for the **Advanced Mermaid Map**."
> *   "Notice the Green Nodes. Those are the 'Brains' we are wrapping around our 'Muscle' (the Orange nodes). This visual proves you aren't just building a straight line anymore; you are building a resilient system."

---

### Artifact 4: Component Spec Generator (Step 4)
**Goal:** Generate PDD 3.4 Specs (Modules A & B).

```markdown
# Role
Senior Tool Engineer.

# Task
Design the specifications for the new components defined in the Approved Strategy.

# Instructions
1. **Router Spec:** Define the `Input Variable`, `Output Categories` (e.g., VALID, AMBIGUOUS, SPAM), and the RAFT prompt.
2. **Critic Spec:** Define the `Input Variable`, the `Evaluation Rubric` (Rules from Scratch Pad), and the RAFT prompt.
3. **Format:** Output clearly labeled sections ready for **PDD Section 3.4**.
```

> **🎥 Video Narration Guide (Step 4)**
> *   "We have the map; now we need the engines. This step defines the **Tool Specs** for PDD 3.4."
> *   "Pay attention to the **Critic's Rubric**. It's not enough to say 'Check the work.' We have to say 'Check for the MSA Clause.' The Critic is only as good as the laws we teach it."

---

### Artifact 5: The Logic OS & Trace (Step 5)
**Goal:** PDD 3.3 (Logic) and 3.5 (Trace).

```markdown
# Role
System Orchestrator.

# Task 1: The Logic OS (PDD 3.3)
Write the "Operating System" logic block.
- Define `### VARIABLES` (from Scratch Pad).
- Define `### CONDITIONS` using IF/ELSE for the Router and WHILE/LOOP for the Critic.

# Task 2: The Master Simulation (PDD 3.5)
Execute this logic on a "Stress Test" input (e.g., A request that is valid but missing the MSA citation).
- **Requirement:** Output a **Trace Log** showing the decision path:
  `[ROUTER] -> VALID`
  `[JUDGE] -> APPROVE`
  `[CRITIC] -> REJECT (Reason: MSA missing)`
  `[JUDGE] -> RETRY`
  `[RESULT] -> FINAL MEMO`
```

> **🎥 Video Narration Guide (Step 5)**
> *   "This is the 'Operating System' (PDD 3.3). Notice the `VARIABLES` and `CONDITIONS`. This replaces manual copy-pasting."
> *   "Watch the **Trace Log**. This is your proof. You can see the Critic rejecting the Judge's first attempt. The Judge then *self-corrects*. That moment of self-correction is the definition of an **Agentic Workflow**."

---

### Artifact 6: The Master Compiler (Step 6)
**Goal:** Generate the reproducible System Prompt.

```markdown
# Role
Lead AI Engineer and System Integrator.

# Task
Compile all components designed in this session (Logic OS, Router, Critic, Core Chain) into a **Single, Self-Contained "Master System Prompt"**.
I should be able to paste this output into a fresh LLM window to run the entire simulation from scratch.

# Requirements
1. Include `### VARIABLES` and `### CONDITIONS`.
2. Include the full definition of every Tool (RAFT Prompts).
3. Enforce the **Trace Log** output format.
```

> **🎥 Video Narration Guide (Step 6)**
> *   "We've done a lot of work today. If I close this chat, I lose it all. That's unacceptable."
> *   "We use the **Compiler Pattern** to package everything—the Logic, the Tools, the Rubrics—into one **Master Prompt**."
> *   "You can save this text file. It is your 'Software.' You can paste it into any LLM tomorrow, and it will run your entire Project Nova Intelligent Network."
