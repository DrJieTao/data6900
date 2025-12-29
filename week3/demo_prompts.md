### **Artifact 1: The "To-Be" Architect Prompt (Step 1)**
*This is the "icebreaker" for the session. It redraws the map.*

```markdown
# Role
You are a Senior Systems Architect specializing in AI-Powered Business Process Automation.

# Task
Your task is to transform an "AS-IS" manual flowchart into a "TO-BE" Linear Assembly Line by replacing a specific manual bottleneck with an automated 3-node pipeline.

# Transformation Rules
1. **Identify the Target:** Locate the manual "Target Step" and the "Decision Diamond" that follows it in the provided Mermaid code.
2. **The Replacement:** Remove those manual steps and replace them with a **subgraph** titled "Automated AI Pipeline". Inside this subgraph, create the following 3-node sequence:
   - **Node_1: [🤖 Gatekeeper: Extraction]**
   - **Node_2: [⚖️ Judge: Reasoning]**
   - **Node_3: [✍️ Worker: Drafting]**
3. **Linearity:** Keep the diagram type as `graph TD`. Ensure the flow is a straight "Assembly Line" (Node_1 -> Node_2 -> Node_3).
4. **Visual Highlighting:** 
   - Apply a distinct style to Node_1, Node_2, and Node_3.
   - **Fill Color:** Use an orange-yellow fill (`#FFF4DD`).
   - **Border:** Use a thick, **dotted or dashed border** (`stroke-dasharray: 5 5`).
5. **Preservation:** Keep the original Trigger (⚡), Inputs (📦), and final Outputs (🏁).

# Input
AS-IS Mermaid Code:
[PASTE YOUR WEEK 2 CODE HERE]

Target Step to Replace:
[e.g., Step G: Budget Reconciliation]
```

---

### **Artifact 2: The AI-Assisted Tool Design Prompt (Step 2)**
*Run this in the **SAME CONVERSATION** as Step 1. It will ingest the map automatically and prompt you for the PDD.*

```
# Role
You are a Senior AI Systems Architect specializing in "Sub-Workflow" engineering and Prompt Design.

# Context
I am designing a 3-node AI pipeline (Gatekeeper -> Judge -> Worker). 
- **Source of Truth:** My Week 2 PDD (Process Discovery).
- **Structure:** The TO-BE Mermaid Map generated in the previous step.

# Task
Interview me to define the **Input, Processing, and Output** for each node, then generate the RAFT-structured prompts.

# Step A: Grounding
Before we begin the interview, please ask me to provide the **"Source of Truth"** (The Week 2 PDD). Do not proceed until I provide it.

# Step B: The Interview Protocol
1. **One Question at a Time:** Ask exactly one question and wait for my response.
2. **Input Dependencies:** For each node, verify if it needs data from the original transcript or output from a *previous* node (e.g., The Worker needs BOTH the Gatekeeper's facts and the Judge's logic).
3. **The "Contract" Recommendation:** Suggest the best format (JSON, XML, or Plain Text) for each output.
   - **Node 2 (Judge) Requirement:** You MUST recommend XML and enforce the use of `<thinking>` and `<verdict>` tags to prevent the "Fast Thinking Trap."

# Output Requirements
Once the design is complete, generate the 3 RAFT prompts. Use the following **Strict Markdown Structure** for each prompt:

    # Role
    [Role definition]
    
    # Audience
    [Who is the output for? Machine or Human?]
    
    # Format
    [Strict formatting rules, e.g., JSON schema or XML tags]
    
    # Task
    [Detailed instructions and grounding rules, use bullet points or numbered list if needed]

# Grounding Instruction
Ensure that the "Judge" is instructed to show its work in `<thinking>` before the `<verdict>`. Ensure the "Worker" is instructed to use the facts from Node 1 to avoid placeholders like "[Insert Vendor]".
```

---

### **Artifact 3: The Universal Meta-Auditor (Step 3)**
*The "QA Injector" to show the iterative failure/fix loop.*

#### **Link 3.1: The Forensic Integrity Audit**
*Keep this exactly as you ran it—it is successfully finding the "Data Stitching" errors.*

```markdown
# Role
You are a Forensic Data Systems Auditor. 

# Task
Perform a "Primary Anchor Audit" on the output generated in the previous turn.

# Execution Rules
1. **Identify the Anchor:** Find the most unique value (e.g., an amount or ID) in the output and locate its **exact row** in the [Source Data].
2. **The Integrity Test:** For every other extracted field, check if it exists in that **exact same row**. 
3. **Detection:** If a field matches a word in the [Transcript] but contradicts the data in that [Source Row], flag it as a **"Contextual Hallucination."**

# Output
List each field and its status: [Grounded in Anchor Row] | [Inferred from Transcript] | [Contextual Hallucination].
```

#### **Link 3.2: The Logic Detective & Verdict**
*Use this next. It takes the "Hallucination" found in 3.1 and forces a FAIL verdict.*

```markdown
# Role
You are a Senior Logic Detective.

# Task
Evaluate the audit results from the previous turn.

# Decision Logic
1. **Did the Auditor find any "Contextual Hallucinations"?** 
   - If YES: Your verdict is **FAIL**. Explain that the tool prioritized "Fuzzy Human Language" over the "System of Record (CSV)."
   - If NO: Your verdict is **PASS**. 

# Output
- **Verdict:** [PASS/FAIL]
- **Reasoning:** [1-sentence explanation]
- **Next Step:** 
   - If FAIL: Ask the user "Should I provide the Grounding Guardrail to fix this?"
   - If PASS: Ask the user "Should I run the Stress Tests?"
```

#### **Link 3.3: The Universal Fixer (The Loop)**
*Run this after the FAIL verdict to get the "Hardened" prompt.*

```markdown
# Task
Based on the FAIL verdict, provide a **"Hardened Grounding Instruction"** to be added to the Gatekeeper's RAFT prompt.

# Goal
The instruction must specifically prevent the AI from "stitching" transcript labels onto CSV data rows.

# Format
Provide the specific instruction in a code block, then provide the **entire revised RAFT prompt**.
```

---
### **Artifact 4: The Automatic Chain Template (Step 4)**
*Runs the full sub-workflow simulation.*

```markdown
# Role
You are the Automated Pipeline Orchestrator. 

# Task
Execute the following 3-step chain on the provided input without further instruction.

# The Chain
1. **[GATEKEEPER]:** [Paste Verified Prompt 1]
2. **[JUDGE]:** [Paste Verified Prompt 2]
3. **[WORKER]:** [Paste Verified Prompt 3]

# Input
[Paste Transcript/Input Data Here]

# Output
Run the sequence and provide the output for all three steps clearly labeled.
```

---

### **Artifact 5: The KPI Value Auditor (Step 5)**
*Extracts the hard metrics for the PDD dashboard.*

```markdown
# Role
You are a Business Value Analyst.

# Task
1. Extract any mentions of time, money, or frequency from the [Previous/Current Version of the PDD].
2. If specific data is missing, provide **Industry Standard Benchmarks** for "Manual Budget Reconciliation" in a small e-commerce business.
3. Format the result as a table: Metric | Current (Manual) | Target (AI) | Estimated Impact.

PDD:
[Paste PDD Here]
```

---

### **Video Narration Cheat Sheet**

*   **Segment 1:** "First, we use the AI to redraw our map. We are 'zooming in' on Step G and replacing it with an automated subgraph. Notice the dotted lines and orange highlight—this is our new 'Engine Room'."
*   **Segment 2:** "Now, staying in the same chat, we ask the AI to be our Architect. It's going to ask me for my Week 2 PDD. Once I provide it, we'll design the 'Data Contracts' for our three tools."
*   **Segment 3:** "Engineering is iterative. I'm going to inject this 'QA Auditor' into our chat to see if our Gatekeeper is actually robust. Look—it found a flaw. Let's fix it."
*   **Segment 4:** "Now that we've hardened our tools, let's run them as a single assembly line to get our Proof of Life."
*   **Segment 5:** "Finally, we need the numbers for our KPI Dashboard. If your transcript was vague, this prompt will give you the industry benchmarks you need to calculate ROI."

I understand the frustration—but looking at the report you just shared, the prompt **actually succeeded** in its most important mission! 

It correctly identified the **"Contextual Hallucination"** in the `target_line_item`. It caught that the Gatekeeper was "people-pleasing" by using the transcript's "shipping" instead of the CSV's "Logistics" for the $10,000 transaction.

The reason it might feel like it "doesn't work" is that it's being too "chatty" or not sufficiently aggressive in its **Verdict**. To make this "Engineer-Ready" for your video, we need to tighten the **Link 3.2 (The Logic Detective)** so it uses that finding to trigger the **FAIL** sequence and provide the **FIX**.

---

### **Artifact 3: The Universal Forensic Audit Chain (Step 3 - Finalized)**



### **Recording Narrative: The "Aha!" Moment**

In your video, this sequence is your strongest "Teaching Moment":

1.  **The Error:** You run the Gatekeeper. It produces `"target_line_item": "shipping"`.
2.  **The Audit (3.1):** You run the Forensic Auditor. You point at the screen: *"Look, the AI caught itself. It sees that for the $10,000 anchor, the CSV says 'Logistics' but it used the transcript's 'shipping.' This is a Contextual Hallucination."*
3.  **The Verdict (3.2):** You run the Logic Detective. It gives a big **FAIL**. 
4.  **The Fix (3.3):** You get the revised prompt. You narrate: *"We are now adding a 'System of Record' guardrail. This tells the AI: if the human and the database disagree, the database wins."*
5.  **The Success:** You re-run the extraction with the fixed prompt and show the **Grounded JSON** (Logistics).

### **Why this is better:**
- It uses the **AI's own audit** as the reason to change the prompt.
- It proves to students that **"Prompt Engineering" is a cycle of testing**, not a one-time guess.
- It is **Universal** because Link 3.1 uses "Anchor" logic that works on any dataset.

**Does this sequence of three distinct prompts feel ready for your Segment 3 demonstration?**
