# Week 3 Cheatsheet: The Engineer's Toolkit 🛠️
**Theme:** From "Prompt Engineering" to "Workflow Architecture"

In Week 3, we stop treating the AI as a chatbot and start treating it as a **Stateless Processing Node**. This guide provides the code snippets and patterns needed to build your **Linear Assembly Line**.

---

### **1. The "Assembly Line" Configuration (R.A.F.T. Matrix)**

To build a reliable chain, you must change the **Audience** and **Format** at each step.

| Node Role | **R**ole | **A**udience | **F**ormat | **T**ask |
| :--- | :--- | :--- | :--- | :--- |
| **1. Gatekeeper** | Data Scientist | A Computer Program | **Strict JSON** | Clean & Extract Data |
| **2. Judge** | Compliance Officer | Internal System | **XML Tags** | Reason & Decide |
| **3. Worker** | Support Agent | The Human Customer | **Plain Text** | Draft Final Content |

---

### **2. The "Clean Data" Discipline**

#### **A. The Handlebars Syntax `{{variable}}`**
In automation (and n8n), we don't paste data directly into the prompt. We use placeholders.
*   **Bad:** "Analyze this email: 'My socks are broken...'"
*   **Good:** "Analyze the email provided in `{{email_body}}`."

#### **B. The "No Pollution" Rule**
When a node talks to another machine (like Node 1 $\to$ Node 2), it **cannot** be conversational.
*   **Polluted Output:** "Sure! I found the data. Here is your JSON: `{ "amount": 88 }`" $\to$ **CRASH 💥**
*   **Clean Output:** `{ "amount": 88 }` $\to$ **SUCCESS ✅**

**The Fix:** Always add this constraint to your Gatekeeper Prompt:
> *"Output RAW JSON ONLY. Do not use Markdown code blocks. Do not write any conversational text intro/outro."*

---

### **3. The Node Templates (Copy-Paste Ready)**

Use these templates for your PDD. Note the **Developer Check** comments—use these to verify your logic is sound.

#### **Node 1: The Gatekeeper (Extraction)**
*Use this to turn messy text into structured data.*

```markdown
# Role
You are a meticulous Data Extraction Specialist. You have no emotions; you only care about facts.

# Audience
The audience is a downstream computer program. It cannot read conversational text.

# Format
Output RAW JSON ONLY. Do not use Markdown backticks.
Keys required: "entity_1", "entity_2", "sentiment".

# Task
Analyze the input provided in {{input_text}}.
Extract the relevant entities into the JSON format defined above.
If a data point is missing, return null. Do not guess.

<!-- DEVELOPER CHECK: def extract(text) -> JSON -->
```

#### **Node 2: The Judge (Logic & Reasoning)**
*Use this to make decisions based on rules/policy.*

```markdown
# Role
You are a strict Policy Compliance Officer.

# Format
Use XML tags to separate thinking from the decision:
<thinking> [Step-by-step reasoning against the rules] </thinking>
<verdict> [FINAL_DECISION] </verdict>

# Context
[Paste your Rules/Policy here]

# Task
Review the data provided in {{extracted_json}}.
1. Reason through the rules in <thinking> tags.
2. Output the final decision in <verdict> tags.

<!-- DEVELOPER CHECK: def judge(json) -> XML {thinking, verdict} -->
```

#### **Node 3: The Worker (Generation)**
*Use this to create the final human-facing deliverable.*

```markdown
# Role
You are a helpful Assistant.

# Audience
The End User (Human).

# Format
Plain text (Natural Language).

# Task
Generate the final response based on the decision in {{verdict}}.
Do not mention the internal logic or policy codes. Keep the tone [Professional/Friendly].

<!-- DEVELOPER CHECK: def draft(verdict) -> String -->
```

---

### **4. The Auto-Simulator (The "Meta-Prompt")**

Use this prompt to test your entire chain logic in one go inside ChatGPT/Claude.

```markdown
# Role
You are a Workflow Engine Simulator.

# Node Definitions
[NODE 1: GATEKEEPER]
Logic: (Paste your System Prompt for Node 1 here)

[NODE 2: JUDGE]
Logic: (Paste your System Prompt for Node 2 here)

[NODE 3: WORKER]
Logic: (Paste your System Prompt for Node 3 here)

# Instruction
I will provide an input. You must simulate the execution:
1. EXECUTE Node 1. Show the RAW JSON output.
2. PASS that variable to Node 2.
3. EXECUTE Node 2. Show the <verdict>.
4. PASS that variable to Node 3.
5. EXECUTE Node 3. Show the final result.

# Input Data
(Paste your test case here)
```

---

### **5. Reliability & Debugging Checklist**

Before you submit your PDD, check your work against these safety features.

#### **Pattern 5: The "Grounding" Instruction**
*   **The Problem:** The AI hallucinates data that isn't there to be helpful.
*   **The Fix:** Add this specific line to your Gatekeeper and Judge prompts:
    > *"Answer ONLY using the provided Input. If the answer is not explicitly found, output 'NULL' or 'UNKNOWN'. Do not guess."*

#### **The "Repair Loop" (When Mermaid/JSON Breaks)**
If the AI gives you broken code or bad JSON, do not fix it yourself.
1.  **Catch the Error:** Copy the error message (or the broken text).
2.  **Feedback:** Paste it back to the AI with: *"I got this error: [Paste Error]. Fix the code."*
3.  **Pivot:** If it fails twice, simplify the request (e.g., "Remove the styling").
