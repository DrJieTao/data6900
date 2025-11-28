# Week 3 Hands-On Demo: "The Human API"
**Subtitle:** Simulating the Universal Workflow Engine
**Video Length:** Approx. 20 Minutes (Paced slowly for technical concepts)
**Required Tools:**
1.  **LLM Interface:** ChatGPT, Claude, Gemini or your favorite LLM.
2.  **Text Editor:** VS Code, Notepad++, or Sublime Text (Must handle plain text clearly).

---

### **Part 1: The Required Artifact**
*Create a text file named `Workflow_Engine_Simulator.txt` with the exact content below. You will share this file with students.*

```text
### THE UNIVERSAL WORKFLOW SIMULATOR ###
# Instructions: You are the Orchestrator. Copy data from Output to Input manually.

[GLOBAL CONTEXT]
Refund Policy: 
1. Claims under $50: Auto-Approve.
2. Claims over $50: Require Photo Evidence of defect.
3. User Error (e.g., batteries): Reject.
Tone: Professional but empathetic. Use one emoji.

---
### NODE 1: THE GATEKEEPER (Extraction Conceptual Tool) ###
[SYSTEM PROMPT]
# Role
You are a meticulous Data Extraction Specialist. You have no emotions; you only care about facts.

# Audience
The audience is a downstream computer program (Node 2). It requires structured data and cannot read conversational text.

# Format
Output RAW JSON ONLY. Do not use Markdown backticks. Do not say "Here is the data."
Keys required: "amount" (number), "issue" (string), "sentiment" (string).

# Task
Analyze the email provided in the variable {{email_body}}. Extract the relevant entities into the JSON format defined above.

<!-- DEVELOPER CHECK: Did I define the function correctly? -->
<!-- def extract(email_body) -> JSON { amount, issue, sentiment } -->

[INPUT VARIABLE: {{email_body}}]
(Paste the raw email here)

[OUTPUT LOG]
(Paste the clean JSON result here)

---
### NODE 2: THE JUDGE (Reasoning) ###
[SYSTEM PROMPT]
# Role
You are a strict Policy Compliance Officer. You follow the rules exactly as written in the Context.

# Audience
The audience is the Drafting Agent (Node 3). It needs a clear decision to act on.

# Format
Use XML tags for structure:
<thinking> [Your step-by-step logic goes here] </thinking>
<verdict> [APPROVE, REQUEST_PHOTO, or REJECT] </verdict>

# Task
Review {{extracted_json}}. Compare against [GLOBAL CONTEXT].
1. Reason step-by-step in <thinking>.
2. Output final decision in <verdict>.

<!-- DEVELOPER CHECK: Is the logic strict? -->
<!-- def judge(json, policy) -> XML { thinking, verdict } -->

[INPUT VARIABLE: {{extracted_json}}]
(Paste the JSON from Node 1 here)

[OUTPUT LOG]
(Paste the Verdict here)

---
### NODE 3: THE WORKER (Drafting) ###
[SYSTEM PROMPT]
# Role
You are a helpful, empathetic Customer Service Agent.

# Audience
The audience is a frustrated customer. You must make them feel heard.

# Format
A standard email body. No subject line. No JSON.

# Task
Draft a reply based strictly on the decision in {{verdict}}.
- If REQUEST_PHOTO: Apologize for the issue, blame the "high value" policy, and ask for a picture.
- Use the Tone defined in [GLOBAL CONTEXT].

<!-- DEVELOPER CHECK: Is the output human-ready? -->
<!-- def draft(verdict) -> String -->

[INPUT VARIABLE: {{verdict}}]
(Paste the Verdict from Node 2 here)

[OUTPUT LOG]
(Paste the final draft here)
```

---

### **Part 2: The Script & Visual Flow**

#### **Intro: The "Human Engine" (0:00 - 3:00)**
*   **Visual:** Full screen on `Workflow_Engine_Simulator.txt` in the Text Editor.
*   **Narrator:** "Welcome back. In Week 2, we *designed* the map. Today, we *test* the engine.
*   **Action:** Highlight the `{{email_body}}` text. **[ZOOM IN]**
*   **Narrator:** "Do you see these double curly braces? `{{ }}`. In engineering, this is called a **Variable**. It is a placeholder.
*   **Narrator:** "In Phase 2 of this course, the software (n8n) will automatically fill these slots. But today, **YOU** are the software. You are going to manually copy-paste data between these nodes. Why? Because if you can't make the logic work manually, you can't automate it."

#### **Segment 1: Node 1 & The "Dirty Data" Crash (3:00 - 8:00)**
*   **Narrator:** "Let's process that tricky email from Order #888. He wants a refund of $88 because his socks are cold."
*   **Action:** Paste the following text into the `{{email_body}}` slot in the text file:
    > "Subject: Order #888. I spent $88 on these socks and they don't work! I want a refund immediately to my card ending in 4022. I already changed the batteries."
*   **Narrator:** "Look at the prompt. The **Audience** is a machine. The **Format** is JSON. Let's run it."
*   **Action:** Copy the entire **NODE 1** block (System Prompt + Input) and paste it into ChatGPT. Hit Enter.
*   **Scenario:** ChatGPT generates the JSON, but adds text: *"Sure! I've extracted the data: ```json { ... } ```"*
*   **Action:** **[PAUSE VIDEO]**. Hover mouse over the conversational text "Sure! I've extracted..."
*   **Narrator:** "Stop. We have a problem. If this were a computer program, it just crashed. Why? Because the next node expects **Data**, but we gave it **English Conversation**. This is called 'Pollution'."
*   **Action:** Copy the output back to the Text Editor's `[OUTPUT LOG]`. Manually delete the text "Sure!...", delete the backticks, leaving *only* the raw `{ "amount": 88, ... }` object.
*   **Narrator:** "As the Engine, I must clean this. I am stripping away the English. Now I have clean JSON. **Clean Data is the oxygen of automation.**"

#### **Segment 2: Node 2 & Passing State (8:00 - 12:00)**
*   **Narrator:** "Now, we move to Node 2: The Judge. Notice that Node 2 *does not see* the original email. It only sees what Node 1 passed to it."
*   **Action:** Copy the *Clean JSON* from Node 1 Output. Paste it into Node 2's `{{extracted_json}}` slot. **[ZOOM IN]**
*   **Narrator:** "This is called **Passing State**. We are moving data from the Gatekeeper to the Judge."
*   **Narrator:** "Notice the R.A.F.T. change here. The **Format** asks for XML tags. This forces the AI to **Show Its Work**."
*   **Action:** Copy the NODE 2 block. Paste into ChatGPT.
*   **Result:** ChatGPT outputs:
    > `<thinking>` Amount is 88. Policy says >50 requires photo. Issue is 'cold', not user error. `<thinking>`
    > `<verdict>` REQUEST_PHOTO `<verdict>`
*   **Narrator:** "Perfect. It used the thinking tags to check the price ($88 > $50) and selected the correct path."

#### **Segment 3: Node 3 & The Final Output (12:00 - 15:00)**
*   **Narrator:** "Finally, Node 3: The Worker. Look at the R.A.F.T. settings. The **Audience** is now the Customer. The **Format** is Plain Text."
*   **Action:** Copy `REQUEST_PHOTO` from the Node 2 output. Paste it into Node 3's `{{verdict}}` slot.
*   **Action:** Run Node 3 in ChatGPT.
*   **Result:** A polite email: *"I'm so sorry to hear that! Since this is a specialized item, could you please send us a photo?"*
*   **Narrator:** "It didn't offer the refund. It followed the strict instruction passed down from the Judge."

#### **Segment 4: The Edge Case Stress Test (15:00 - 18:00)**
*   **Narrator:** "Our engine handles refunds. But what if a Spam bot emails us? Does the engine explode?"
*   **Action:** Scroll back to Node 1 in the Text Editor. Delete the old email. Paste: *"DEAR SIR, I HAVE $50M USD FOR YOU. CLICK HERE."*
*   **Action:** Run Node 1.
    *   *Result:* `{"issue": "Spam", "amount": 0}`
*   **Action:** Run Node 2 with this new JSON.
    *   *Result:* `<thinking>` Category is Spam. No policy check needed. `<thinking>` `<verdict>` REJECT `<verdict>`
*   **Narrator:** "It didn't break. The Gatekeeper identified it. The Judge dismissed it. This workflow is **Robust**."

#### **Segment 5: The "Auto-Simulator" (Meta-Prompt) (18:00 - 21:00)**
*   **Narrator:** "You have proven the logic works manually. Now, let's treat ourselves. Because we wrote clear R.A.F.T. prompts, we can ask the AI to run the whole simulation for us."
*   **Action:** Open a **New Chat**. Paste the following **Master Prompt**:
    ```text
    # Role
    You are a Workflow Engine Simulator.

    # Node Definitions
    [NODE 1: GATEKEEPER]
    Format: JSON. Task: Extract amount/issue from input.

    [NODE 2: JUDGE]
    Format: XML. Task: If amount > 50, output <verdict>REQUEST_PHOTO</verdict>. Else <verdict>APPROVE</verdict>.

    [NODE 3: WORKER]
    Format: Email. Task: Write reply based on verdict.

    # Instruction
    I will give you an input. You must:
    1. EXECUTE Node 1. Show JSON.
    2. PASS variable to Node 2.
    3. EXECUTE Node 2. Show Verdict.
    4. PASS variable to Node 3.
    5. EXECUTE Node 3. Show Email.

    # Input
    "My $88 socks are broken!"
    ```
*   **Action:** Hit Enter. Watch the AI generate the full log.
*   **Narrator:** "Boom. Step 1, Step 2, Step 3. Automatic. This is what we will build in n8n next month. But today, you built the logic."

#### **Wrap Up (21:00 - End)**
*   **Narrator:** "For Milestone 2, you must download this `Workflow_Engine_Simulator.txt` file. Fill it with *your* project's prompts. Run the manual test. If it works here, it will work in the real world."
