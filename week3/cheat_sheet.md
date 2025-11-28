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

#### **Node 1: The Gatekeeper (Extraction)**
*Use this to turn messy text into structured data.*

```markdown
# Role
You are a meticulous Data Extraction Specialist. You have no emotions; you only care about facts.

# Audience
The audience is a downstream computer program. It cannot read conversational text.

# Format
Output RAW JSON ONLY.
Keys required: "entity_1", "entity_2", "sentiment".

# Task
Analyze the input provided in {{input_text}}.
Extract the relevant entities into the JSON format defined above.
```

#### **Node 2: The Judge (Logic & Reasoning)**
*Use this to make decisions based on rules/policy.*

```markdown
# Role
You are a strict Policy Compliance Officer.

# Format
Use XML tags to separate thinking from the decision:
<thinking> [Step-by-step reasoning] </thinking>
<verdict> [FINAL_DECISION] </verdict>

# Context
[Paste your Rules/Policy here]

# Task
Review the data provided in {{extracted_json}}.
1. Reason through the rules in <thinking> tags.
2. Output the final decision in <verdict> tags.
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

### **5. Reliability Checklist (Safety Features)**

Before you finalize your PDD, check these 3 safety features:

*   **[ ] The Grounding Instruction:** Did you tell the Gatekeeper what to do if data is missing?
    *   *Add:* "If the data is not explicitly found in the input, output `null`. Do not guess."
*   **[ ] The Edge Case Test:** Did you run a "Spam" or "Irrelevant" input through your Simulator?
    *   *Goal:* The Judge should catch it and output `<verdict>IGNORE</verdict>` (or similar) instead of writing a confused email.
*   **[ ] The Separation of Concerns:** Does the Worker know too much?
    *   *Goal:* The Worker should ideally only see the *Verdict*, not the raw angry email, to prevent it from getting defensive.
