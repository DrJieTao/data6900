### **Complete Plan for Week 1 Pre-Recorded Hands-On Demo**

**Video Title:** From Chatbot to Data Contract: The Power of Professional Prompting
**Video Length:** Approx. 10-12 minutes
**Format:** A continuous screen recording showing a text editor and an LLM chat interface. No slides will be used.
**Pedagogical Goal:** To demonstrate *why* structured prompting is essential for creating **reliable, consistent, and controllable** outputs for automated workflows, moving beyond simple factual accuracy to achieve industrial-grade reliability.

---

### **Required Artifacts for the Demo**

These are the final materials the instructor will use on-screen during the recording.

#### **1. The "Genuinely Difficult" Lao Wang Transcript Snippet:**
```
Subject: Project Nova - Q3 Strategy Review

Lao Wang: Okay, the main agenda item is the vendor for our new cloud infrastructure. The finance team is still pushing for Vendor B due to cost.

Priya: I'm hesitant. Vendor A has much better security protocols, which is a major concern for the tech team.

Lao Wang: I agree. My final call is that we'll stick with Vendor A, but this is contingent on them providing the updated security compliance report by this Thursday, EOD. If they miss that deadline, we're forced to reconsider.

Alex: That puts pressure on marketing to have the partnership announcement ready. The messaging will need to be updated depending on the outcome.

Lao Wang: Right. That needs to be handled. Also, I reviewed the draft of the legal MSA. It’s missing the data residency clause. This is a showstopper, so it needs to be addressed immediately. Maria, can you get that ball rolling?

Maria: I can. I'll ping Daniel in the legal department right away.
```

#### **2. The Three Levels of Prompts to be Demonstrated:**

**Level 1 Prompt (The "Chatbot" / Brittle Prompt):**
```
Summarize the decisions and action items from the following meeting transcript.

[Paste the transcript here]
```

**Level 2 Prompt (The R.A.F.T. / Reliable "Data Contract" Prompt):**
```markdown
# Role
You are an expert project management assistant.

# Audience
The audience is a downstream computer program, so strict adherence to the JSON format is critical.

# Format
Provide the output in a single JSON object. The JSON must contain two top-level keys: "decisions" and "action_items".
- The "decisions" key should be a list of objects. Each object must have two keys: "decision" and "condition". If there is no condition, the value should be an empty string.
- The "action_items" key should be a list of objects. Each object must have four keys: "owner", "task", "priority", and "initiated_by". If a value is not mentioned, use an empty string.
- Do not include any introductory text or explanations outside of the JSON object.

# Topic & Task
The topic is the following meeting notes. Your task is to extract all decisions and action items, following the formatting rules precisely.

Meeting Notes:
[Paste the transcript here]
```

**Level 3 Prompt (The R.A.F.T. + Few-Shot / "Controlled" Prompt with Business Logic):**
```markdown
# Role
You are an expert project management assistant.

# Audience
The audience is a downstream computer program, so strict adherence to the JSON format is critical.

# Format
Provide the output in a single JSON object. The JSON must contain two top-level keys: "decisions" and "action_items".
- The "decisions" key should be a list of objects. Each object must have two keys: "decision" and "condition". If there is no condition, the value should be an empty string.
- The "action_items" key should be a list of objects. Each object must have four keys: "owner", "task", "priority", and "initiated_by". If a value is not mentioned, use an empty string.
- Do not include any introductory text or explanations outside of the JSON object.

# Topic & Task
The topic is the following meeting notes. Your task is to extract all decisions and action items, following the formatting rules precisely. To ensure accuracy and handle ambiguity, you must follow the logic demonstrated in the example below.

---
**EXAMPLE**
Input: "Let's use the blue design, but only if the client approves. Jane, can you get legal to check the new logo? It's urgent."
Output:
{
  "decisions": [
    {
      "decision": "Use the blue design",
      "condition": "Client must approve"
    }
  ],
  "action_items": [
    {
      "owner": "Legal Department",
      "task": "Check the new logo",
      "priority": "High",
      "initiated_by": "Jane"
    }
  ]
}
---

**MEETING NOTES TO PROCESS:**
[Paste the transcript here]
```

---

### **Detailed Video Flow & Narration Guide**

**(Segment 1: Introduction - The Reliability Crisis)**
*   **Action:** Instructor introduces the topic and pastes the difficult transcript into a text editor on screen.
*   **Key Narration:** "Welcome. You've seen ChatGPT give you accurate answers to simple questions. So why do we need complex frameworks? The answer is **reliability.** A business workflow that works 'most of the time' is a failing business process. Let's use this realistic transcript from Lao Wang's meeting to see why."

**(Segment 2: Level 1 - The 'Correct but Brittle' Chatbot Answer)**
*   **Action:** Instructor copies the Level 1 prompt and the transcript into the LLM interface. Runs it.
*   **Key Narration (on first run):** "Let's analyze this. As you can see, the facts are all here. The model is smart enough to extract the conditional decision and the action items. For a human, this is a perfect summary. But what happens if we need to run this automatically 1,000 times a day?"
*   **"Aha!" Moment Action:** The instructor runs the **exact same Level 1 prompt two more times.**
*   **Key Narration (comparing the runs):** "Look closely. The phrasing is slightly different. The order of the items has changed. For a human, these summaries are the same. But for an automated n8n workflow expecting a specific structure, these inconsistencies would cause the process to fail. This is a **brittle** result. We cannot build a business on this."

**(Segment 3: Level 2 - R.A.F.T. to Create a 'Data Contract')**
*   **Action:** Instructor builds the Level 2 R.A.F.T. prompt in the text editor, explaining each `# Section`.
*   **Key Narration:** "The Level 1 prompt failed the reliability test. Now, we'll use the R.A.F.T. framework to create a stable and predictable **data contract**. The 'Audience' and 'Format' sections are our commands for absolute consistency."
*   **Action:** Instructor runs the Level 2 prompt. Then, runs it a second time and places the two JSON outputs side-by-side.
*   **Key Narration:** "Look. They are **structurally identical.** This is a **reliable payload.** An n8n workflow can process this output a million times without breaking. We have solved the **consistency** problem. However, look at the data itself. It missed the 'High' priority, and it incorrectly assigned the legal task to 'Maria'. The structure is reliable, but the business logic is not yet perfect."

**(Segment 4: Level 3 - Few-Shot for 'Business Logic & Control')**
*   **Action:** Instructor returns to the text editor and adds the `--- EXAMPLE ---` block to the Level 2 prompt.
*   **Key Narration:** "To solve the final problem of nuance, we have to *teach* the AI our business rules. This is Few-Shot Prompting, and it's about **control.** I'm adding an example that teaches it how to infer 'priority' from the word 'immediately' and how to identify the true owner ('Legal Department') even when someone else ('Maria') initiates the task."
*   **Action:** Instructor runs the final Level 3 prompt.
*   **Key Narration (showcasing the result):** "This is the final product. A perfectly reliable JSON structure, AND it has correctly interpreted the business nuance. It captured the 'High' priority and assigned the task to the 'Legal Department' while noting Maria as the initiator. This is a reliable, controlled, production-ready output that can safely power an automated workflow for Lao Wang."

**(Segment 5: Wrap-Up & The Cheat Sheet)**
*   **Action:** Instructor displays the final "Prompting Cheat Sheet" PDF on screen.
*   **Key Narration:** "This entire professional workflow is captured in your cheat sheet. Level 1 is for chats. R.A.F.T. is for **reliability**. And Few-Shot is for **control**. Master this combination, and you'll be able to build truly robust AI solutions. See you in the live workshop!"
