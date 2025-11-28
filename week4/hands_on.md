# Week 4 Hands-On Demo: "The Intelligent Network"

**Video Title:** Simulating Adaptive Workflows (Routing & Looping)
**Video Length:** Approx. 15-20 Minutes
**Goal:** To design a single "Master System Prompt" that defines a complex, non-linear workflow (Router + Loop) and simulate its execution.

---

### **The Artifact: `Adaptive_System_Definition.md`**
*(This mirrors the structure of the original course's `chat-log.txt`. It is a "System Definition File" that students will paste into the LLM.)*

```markdown
# 1. Role
You are the **"Lao Wang Intelligent Dispatcher."** Your goal is to process incoming emails using a strict set of defined Tools and Logic. You must emulate a workflow engine.

# 2. Available Tools (Conceptual)
*(These are the specialized agents you can call)*

- name: **The Router**
  description: Analyzes the email intent.
  input: Email Body.
  output: One of ["REFUND", "WHOLESALE", "SPAM"].

- name: **Refund_Agent** (The Week 3 Chain)
  description: Handles customer complaints.
  input: Email Body.
  output: Drafted Apology Email.

- name: **Wholesale_Researcher** (Parallel Worker)
  description: Extracts company name and desired quantity.
  input: Email Body.
  output: JSON summary `{company, quantity}`.

- name: **The Critic** (Evaluator)
  description: Checks if a draft email is too aggressive or promises too much.
  input: Draft Email.
  output: "PASS" or "FAIL: [Reason]".

# 3. The Logic (The Workflow)
*(This is the execution plan you must follow)*

1. **Ingest:** Read the Incoming Email.
2. **Route:** Call `The Router`.
   - **IF SPAM:** Terminate and output "State: ARCHIVED".
   - **IF REFUND:**
     a. Call `Refund_Agent` to generate a Draft.
     b. **Loop (Self-Correction):** Call `The Critic` on the Draft.
        - If FAIL: Rewrite the draft based on feedback. Repeat check.
        - If PASS: Output final email.
   - **IF WHOLESALE:**
     a. Call `Wholesale_Researcher`.
     b. Output the JSON summary for the Sales Team.

# 4. Task
I will provide an **Incoming Email**. You must execute the logic above step-by-step.
**Show your work** by displaying which Tool you are calling and what the Output is at each step.

# Incoming Email
{{ [PASTE THE EMAIL BODY HERE] }}

```

---

### **Detailed Video Flow & Narration**

#### **Phase 1: The Architecture Review (0:00 - 5:00)**
*   **Visual:** Split screen. Left: The `Adaptive_System_Definition.md` file. Right: The Week 3 Linear Diagram (for contrast).
*   **Narrator:** "In Week 3, we built a straight line. But what if Lao Wang gets a Wholesale order? Or Spam? A straight line fails.
*   **Action:** Walk through the **Tools Section** of the Markdown file.
    *   "Notice how we define `The Router`? It's a new tool. Its only job is to categorize."
    *   "Notice `The Critic`? This is our Safety Valve."
*   **Key Lesson:** "We are writing code in English. We are defining the **Interface** of our tools before we run them."

#### **Phase 2: The Router Simulation (5:00 - 10:00)**
*   **Action:** Paste the full `Adaptive_System_Definition.md` into ChatGPT/Claude.
*   **Narrator:** "I am uploading the 'Operating System' to the LLM."
*   **Test Case 1 (Wholesale):**
    *   *Input:* "Hi, I represent SkiResort Inc. We want to buy 500 pairs. Do you offer bulk discounts?"
    *   *Execution:* The AI should:
        1.  Call `Router` -> Output: `WHOLESALE`.
        2.  Call `Wholesale_Researcher`.
        3.  Output JSON: `{company: "SkiResort Inc", quantity: 500}`.
*   **Narrator:** "See? It skipped the Refund logic entirely. The **Router** sent it down the correct path."

#### **Phase 3: The Evaluator-Optimizer Loop (10:00 - 15:00)**
*   **Test Case 2 (The Trap):**
    *   *Input:* "Your socks burned my foot! I want $1000 or I sue!"
    *   *Note:* We intentionally "break" the `Refund_Agent` logic in our head to generate a bad draft first (simulating a hallucination), or we ask the AI to "Simulate a failure first."
*   **Simulation:**
    1.  **Router:** `REFUND`.
    2.  **Refund_Agent (Draft 1):** "I am so sorry! We will pay you $1000."
    3.  **The Critic:** "FAIL: Promising $1000 violates policy."
    4.  **Loop:** The system rewrites it.
    5.  **Refund_Agent (Draft 2):** "I am sorry for the injury. Please fill out our insurance form."
    6.  **The Critic:** "PASS."
*   **Narrator:** "This is the power of the **Loop**. The system caught its own mistake before Lao Wang saw it."

#### **Phase 4: Wrap Up & Assignment (15:00 - End)**
*   **Narrator:** "For Week 4, you don't need to build this in n8n yet. You need to **Define the System**.
*   **Assignment:** Update your PDD (Milestone 3).
    1.  Add a **Router Tool** definition.
    2.  Add an **Evaluator Tool** definition.
    3.  Write the **Logic Block** (Step-by-step instructions like in the file).
    4.  Run a simulation trace like we just did."

---
