### **Complete Plan for Week 2 Pre-Recorded Hands-On Demo**

**Video Title:** The Architect's Blueprint: From "The Blob" to "The Assembly Line"
**Video Length:** Approx. 15-18 minutes
**Format:** Continuous screen recording showing an LLM interface (ChatGPT/Claude) and a text editor. The final segment requires opening the [Mermaid Live Editor](https://mermaid.live/) in a browser tab.
**Pedagogical Goal:** To move students from "asking the AI to do work" (The Blob) to "designing how the AI works" (The Architect). Specifically, to demonstrate **Interactive Planning** for Context, **ART Definition** for Tools, and **Prompt Chaining** for Orchestration.

---

### **Required Artifacts for the Demo**

These are the final materials the instructor will use on-screen during the recording.

#### **1. The "Tricky" Customer Email (Lao Wang's Nightmare):**
```text
Subject: ORDER #888 - DISAPPOINTED!!

I bought these "Magma-Heat" socks for my skiing trip and they barely get warm! I spent $88 on these and I am freezing. This is false advertising. I want my money back immediately to my card ending in 4022. Don't tell me to troubleshoot, I already changed the batteries.
```

#### **2. The Prompt Sequence (The "Cheat Codes"):**

**Prompt A (The Failure / "The Blob"):**
```text
You are a customer service AI. Read this email and handle it for me. Be polite.

[Paste Email Here]
```

**Prompt B (Interactive Planning / Context Builder):**
```text
I want to build an automated email assistant for my dropshipping business (Heated Socks). Before we write any code or generate text, I need you to interview me.

Ask me 3 specific clarifying questions about my Refund Policy, Tone of Voice, and Escalation Rules. Do not propose a solution yet. Just ask.
```

**Prompt C (The Scratch Pad / Memory Freeze):**
```text
Great. Now, summarize everything I just told you into a single code block called [Current_Context].

Use bullet points. This will serve as your "Long Term Memory" for the rest of this session.
```

**Prompt D (The ART Definition / Internal Tool):**
```text
Now, help me write a definition for an "Intent Analysis Tool" (ART).

This tool should take an email text as input and output a Markdown Table with the following columns:
1. Category (Refund / Technical Support / Spam)
2. Sentiment (Angry / Neutral / Happy)
3. Urgency (High / Low)
4. Recommended_Action (One short sentence based on the [Current_Context])

Write the system instruction for this tool.
```

**Prompt E (The Assembly Line / Orchestration):**
```text
Act as the Orchestrator. Design a linear "Assembly Line" workflow for processing a new email using the components we just built.

Structure it as:
Step 1: Read Input
Step 2: Load [Current_Context]
Step 3: Run "Intent Analysis Tool"
Step 4: Draft Reply (if applicable)

Do not write the email yet. Just output the plan.
```

**Prompt F (The Visual Payoff / Mermaid):**
```text
Excellent plan. Now, translate this exact text plan into Mermaid Code (graph TD) so I can visualize it.
```

---

### **Detailed Video Flow & Narration Guide**

**(Segment 1: The Trap - "The Blob")**
*   **Action:** Instructor opens ChatGPT and pastes **Prompt A** + **The Tricky Email**.
*   **Key Narration:** "Lao Wang just sent us this angry email. Order #888, value $88. The amateur move is to just throw this at the AI and say 'Handle it.' We call this **The Blob Prompt**. Let's see what happens."
*   **Action:** Run the prompt. The AI likely apologizes and promises a refund.
*   **Key Narration (The Critique):** "Stop. Look at that. The AI just promised a refund. Does Lao Wang *allow* refunds for used items? We don't know! The AI didn't know! It hallucinated a policy to be nice. In business, this is called 'losing money.' The Blob failed because it had no **Context** and no **Process**."

**(Segment 2: Guardian 3 - Building Context & Memory)**
*   **Action:** Open a new chat. "Let's put on our Consultant Hat. We need to extract the rules from Lao Wang's head." Paste **Prompt B** (Interactive Planning).
*   **Action:** The AI asks 3 questions. Instructor types the answers live:
    1.  *Refunds:* "Max $50 auto-refund. Over $50 requires a photo of the defect. No refunds for 'user error'."
    2.  *Tone:* "Friendly, apologetic, but firm on policy. Use one emoji."
    3.  *Escalation:* "If they mention 'lawyer' or 'sue', forward to me."
*   **Key Narration:** "Now the AI knows the rules. But LLMs are forgetful. We need to freeze this into a 'Memory Block'."
*   **Action:** Paste **Prompt C** (The Scratch Pad).
*   **Key Narration:** "This block—`[Current_Context]`—is Guardian 3. In the future, every time we run our workflow, we will paste this block first. It’s our safety anchor."

**(Segment 3: Guardian 2 - Defining the ART)**
*   **Key Narration:** "Now we need a tool. Not a Python script, but a reasoning tool. We need the AI to 'Think' before it 'Writes'. We call this an **ART** (Agent Reasoning Tool)."
*   **Action:** Paste **Prompt D**.
*   **Key Narration:** "Notice I am asking for a **Markdown Table**. Why? Because structured output forces the AI to be precise. It stops it from rambling."
*   **Action:** The AI generates the Tool Definition.
*   **Instructor:** "Look at that. You just built a software tool using plain English."

**(Segment 4: Guardian 4 - The Assembly Line)**
*   **Key Narration:** "We have the Memory (Scratch Pad) and the Tool (ART). Now, we need the **Orchestrator** to link them up. We are going to use the **Assembly Line Pattern** (Prompt Chaining)."
*   **Action:** Paste **Prompt E**.
*   **Key Narration:** "We are forcing the AI to slow down. Step 1, get data. Step 2, check memory. Step 3, analyze. Step 4, act. This prevents the 'Blob' mistakes."
*   **Action:** "Now, let's run that tricky email again through this Assembly Line." (Paste the Tricky Email again with the instruction: *Execute the Assembly Line on this email*).
*   **Outcome:** The AI analyzes the email. It sees the value is $88 (>$50). It checks the Scratch Pad. It recommends: *Ask for a photo, do not refund yet.*
*   **Key Narration:** "Success! It didn't give away the money. It followed the logic perfectly. That is the power of a Workflow."

**(Segment 5: The Visual Payoff)**
*   **Key Narration:** "We have a text plan. But clients like Lao Wang don't read text. They like pictures. Can we turn this text into a diagram?"
*   **Action:** Paste **Prompt F** (Mermaid).
*   **Action:** Copy the code block. Switch tab to [Mermaid Live Editor](https://mermaid.live/). Paste the code.
*   **Key Narration:** "Boom. A professional flowchart. You just went from a messy email to a standardized, documented business process without writing a single line of real code. *This* is what an Analytics Consultant does."

**(Segment 6: Wrap Up)**
*   **Action:** Show the "Week 2 Cheat Sheet" (which contains these prompts).
*   **Key Narration:** "Your assignment this week is to do exactly this: Pick a process, interview the AI, build the Scratch Pad, define the ART, and draw the map. Good luck, architects!"
