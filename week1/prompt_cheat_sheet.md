### **Week 1 Prompting Cheat Sheet: From Chatbot to Data Contract**

This guide explains when and how to use the R.A.F.T. framework to create reliable, machine-readable "data contracts" for your workflows.

---

### **When to Use a Structured Prompt (and When Not To)**

Not every task needs a complex prompt. Knowing when to use each level is a key professional skill.

#### Use a **Level 1 (Simple) Prompt** when:
*   You are brainstorming, exploring a topic, or having a creative "conversation" with an AI.
*   The end user is a human who can easily interpret conversational, slightly varied text.
*   The task is a one-off request where 100% structural consistency is not required.
*   **Example:** "Explain the concept of RAG in simple terms."

#### Use a **Level 2/3 (Structured R.A.F.T.) Prompt** when:
*   The output will be used by another program or step in an automated workflow (e.g., in n8n).
*   The output format must be **100% consistent and machine-readable** every single time (e.g., JSON).
*   The task is repetitive, and reliability is critical to the business process.
*   You are writing a **System Prompt** for a custom AI (like a Custom GPT or Gemini Gem) to define its core behavior.
*   **Motto:** Use a simple prompt for a **conversation**, use a structured prompt for **automation**.

---

### **The R.A.F.T. Framework: Your Professional Baseline for Reliability**

Use Markdown headers to structure your prompt for clarity and reusability.

#### `# Role`
**Who is the AI?** Sets the persona, tone, and expertise.
`You are an expert project management assistant.`

#### `# Audience`
**Who is the output for?** Defines the end user (human or machine) and informs the style.
`The audience is a downstream computer program.`

#### `# Format`
**What should the output look like?** Defines the exact structure, like a JSON schema.
`Provide the output in a single JSON object with the keys "decisions" and "action_items".`

#### `# Topic & Task`
**What is the subject and what should the AI do?** The core mission and source material.
`The topic is the meeting notes. Your task is to extract all decisions and action items.`

---

### **Advanced Technique: Few-Shot Prompting for Control**

**What is it?** Providing one or more high-quality examples (`shots`) within your prompt to *teach* the AI how to handle nuance and specific business logic that the Format instructions alone cannot capture.

**Why use it?** To gain **control** over the AI's interpretation of ambiguous text and ensure it populates your data contract with perfect accuracy, reflecting your unique business rules.

#### **New Example for Your Reference:**
This example teaches the AI how to identify a task with an implicit owner and a specific deadline. Notice how it populates a `deadline` key that isn't explicitly mentioned in the input.


---
**EXAMPLE**

Input: "The Q3 marketing report needs to be finalized. Jessica, you know the data best. The absolute deadline for this is next Monday."

Output:
```json

{
  "decisions": [],
  "action_items": [
    {
      "owner": "Jessica",
      "task": "Finalize the Q3 marketing report",
      "deadline": "Next Monday",
      "initiated_by": ""
    }
  ]
}
```
---


---

### **The Level 3 Prompt (from the video): The Final "Data Contract"**

This prompt combines R.A.F.T. for **reliability** with a Few-Shot example for **control**. This is the standard for building enterprise-grade workflow components. You can use this as a template for your own projects.

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
[Paste your context here]
```
