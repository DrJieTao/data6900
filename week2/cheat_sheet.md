### **Week 2 Prompting Cheat Sheet: The Architect's Blueprint**

This guide covers the **Advanced Prompting Patterns** needed to design, define, and orchestrate AI workflows. In Week 2, we stop just "chatting" with the AI and start acting as the **Architect** of a system.

---

### **The "Four Guardians" Prompting Strategy**

To build a reliable workflow, you must explicitly prompt for each of the four components. Do not rely on the AI to guess them.

| Guardian | Role | The Prompting Move |
| :--- | :--- | :--- |
| **1. Brain** | The Processor | Selecting the model (GPT-4o, Claude 3.5 Sonnet, etc.). |
| **2. Context** | The Memory | **Interactive Planning** & **The Scratch Pad**. |
| **3. Tools** | The Logic | Defining **ARTs** (Agent Reasoning Tools). |
| **4. Orchestrator** | The Manager | **The Assembly Line** (Prompt Chaining). |

---

### **Pattern 1: Interactive Planning (Building Context)**

**When to use:** When starting a complex task where the requirements are vague or exist only in your head. Instead of writing a massive prompt, make the AI interview you.

**Template:**
```markdown
I want to build a [Type of Workflow] for [Target Audience/Business].
Before we write any code or generate text, I need you to interview me.

Ask me [Number] specific clarifying questions about [Key Topics, e.g., Tone, Policy, Constraints].
Do not propose a solution yet. Just ask the questions one by one (or as a list).
```

**Why it works:** It forces the AI to extract the *hidden* context that you forgot to mention, preventing hallucinations later.

---

### **Pattern 2: The Scratch Pad (Freezing Memory)**

**When to use:** Immediately after the Interactive Planning phase. LLMs have short memories; this technique forces them to "save" the rules into a reusable block.

**Template:**
```markdown
Great. Now, summarize everything I just told you into a single code block called `[Current_Context]`.

Use bullet points. This will serve as your "Long Term Memory" for the rest of this session.
```

**Pro Tip:** In a real automation (like n8n), you will paste this `[Current_Context]` block at the top of every prompt in your chain.

---

### **Pattern 3: Defining an ART (Internal Tool)**

**When to use:** When you need the AI to perform a specific *reasoning* task (like "Classify," "Extract," or "Decide") consistently. Think of this as writing a "Standard Operating Procedure" (SOP) for the Brain.

**Key Elements:**
1.  **Input:** What data does it get?
2.  **Logic:** How should it think? (The "System Instruction").
3.  **Output:** What format must it return? (Markdown Tables are best for readability; JSON for code).

**Template:**
```markdown
Help me write a definition for an "[Name of Tool]" (ART).

1. **Input:** [e.g., A raw customer email].
2. **Logic:** [e.g., Determine if the customer is Angry, Neutral, or Happy. Then check if the request violates the policy in `[Current_Context]`].
3. **Output:** A Markdown Table with columns: [Column A, Column B, Column C].

Write the system instruction for this tool.
```

---

### **Pattern 4: The Assembly Line (Orchestration)**

**When to use:** To connect all pieces into a linear workflow. This prevents "The Blob" (asking for everything at once) and ensures reliability.

**Template:**
```markdown
Act as the Orchestrator. Design a linear "Assembly Line" workflow for this process.

Structure it as:
Step 1: [Trigger/Input]
Step 2: Load `[Current_Context]`
Step 3: Run "[Name of ART]"
Step 4: [Final Action, e.g., Draft Reply]

Do not execute the steps yet. Just output the plan as a numbered list.
```

---

### **Bonus: The Visualization (Mermaid.js)**

**When to use:** To turn your text-based Assembly Line into a professional flowchart for your presentation or documentation.

**Template:**
```markdown
Excellent plan. Now, translate this exact text plan into Mermaid Code (graph TD) so I can visualize it.
```

**How to use the output:**
1.  Copy the code block provided by the AI.
2.  Go to [Mermaid.live](https://mermaid.live/).
3.  Paste the code to see your diagram.

---

### **Debugging: What if the Code Breaks? (The Iterative Mindset)**

**The Reality:** LLMs are probability engines, not logic engines. They often write broken Mermaid code (or later, broken n8n workflows).

**The Golden Rule:** Do not panic. Do not try to fix the syntax yourself (unless you know how).

#### **Level 1: The "Repair Loop" (Try this first)**
1.  **Run it:** Paste the code into the tool (Mermaid Live).
2.  **Catch the Error:** If it turns red or says "Syntax Error," **copy that error message**.
3.  **Feedback:** Paste the error message *back* to the AI.

**Repair Template:**
```markdown
I tried to run your code, but I got this error:
[Paste the Error Message Here]

Fix the code and explain what went wrong.
```

#### **Level 2: The "Pivot" Strategies (If it's still stuck)**
If the AI keeps giving you broken code after 2 tries, stop. It is stuck in a bad loop. Use these strategies to unstick it.

**Strategy A: Simplify (Remove the "Bling")**
Often, the AI breaks because it tries to add fancy colors, icons, or complex sub-graphs. Tell it to go back to basics.
> **Prompt:** "The code is still breaking. Remove all styling, colors, and icons. Just give me a simple, standard flowchart with boxes and arrows."

**Strategy B: Change Structure**
Sometimes a specific graph type causes issues. Ask for a different layout.
> **Prompt:** "Let's try a different structure. Instead of a `graph TD` (Top-Down), try using `flowchart LR` (Left-Right). Keep the logic, but change the syntax."

**Strategy C: Decompose (The "Part-by-Part" Approach)**
If the workflow is huge, the AI might be overwhelmed. Ask it to map just the first half.
> **Prompt:** "Let's debug this by splitting it up. Just write the Mermaid code for Step 1 and Step 2. Do not include the rest yet."

**Why this matters:** In Part 2 of this course, we will use AI to write complex n8n automation code. It *will* break. Learning to calmly use this "Repair Loop" and "Pivot" strategy now is the most important skill for an AI Engineer. Code generation is always an iterative process, not a "one-shot" magic trick.

---

### **Summary: The "Architect's Loop"**

1.  **Interview:** "Ask me questions."
2.  **Freeze:** "Save to `[Current_Context]`."
3.  **Define:** "Create an ART for this logic."
4.  **Chain:** "Build the Assembly Line."
5.  **Visualize:** "Draw the Mermaid chart."
