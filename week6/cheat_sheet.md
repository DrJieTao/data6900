# **DATA 6900: THE AI CONSULTANT’S TOOLKIT**
## **Week 6: The Final Assembly**

**INSTRUCTIONS:**
1.  **Step 0 (Context Dump):** Before using *any* of these prompts, you must paste your entire Draft PDD (Week 1-5 content) into the LLM so it knows your project context.
2.  **Step 1 (Copy & Edit):** Copy the prompt templates below. Replace the `[Bracketed Text]` with your specific project details.
3.  **Step 2 (Iterate):** If the output feels generic, add a constraint: *"Be more critical"* or *"Focus on financial loss."*

---

### **PHASE 1: THE DEEP CLEAN (Risk Audit)**
*Use this to find holes in your logic before the client does.*

**Prompt:**
```text
ROLE: Senior Risk Consultant.
AUDIENCE: The Internal Technical Team (Be critical and specific).
TASK: Audit the "Risk Assessment" section of the PDD I provided.
FORMAT: Bullet points with "Risk Name", "Specific Scenario", and "Mitigation".

DEFINITIONS:
- "Blind Spots": Vulnerabilities related specifically to Data Privacy (PII), Algorithmic Bias, or User Compliance that I might have missed.

EXAMPLE (Few-Shot):
- Bad: "The bot might lie."
- Good: "Risk: Hallucination. Scenario: Bot invents a 50% discount policy that doesn't exist. Mitigation: Grounding via RAG."

YOUR TURN:
Critique my draft. Identify 2 specific "Blind Spots" based on the definitions above.
```

---

### **PHASE 2: THE VALUE POLISH (KPIs)**
*Use this to turn vague hopes ("Improve efficiency") into bankable numbers.*

**Prompt:**
```text
ROLE: Business Analyst.
AUDIENCE: The CFO (Focus on hard dollars and timelines).
TASK: Convert my vague goal ("[Insert Your Goal, e.g., Save Time]") into a quantifiable KPI.
CONTEXT: Manual process currently takes [Insert Hours] per week. Hourly rate is $[Insert Rate].

CONSTRAINT (Follow this Formula):
- Specific: What exact task is changing?
- Measurable: Use exact numbers (Hours reduced or Dollars saved).
- Achievable: Assume 80% automation success, not 100%.
- Relevant: Link directly to Cost Savings or Revenue Protection.
- Time-bound: Set a realistic deadline (e.g., Q3).

EXAMPLE (Few-Shot):
- Input: "Make it faster."
- Output: "Reduce Cycle Time from 48h to 5m by Q3, saving $12k/year."

YOUR TURN:
Convert my goal using the context and constraints above.
```

---

### **PHASE 3: THE EXECUTIVE SUMMARY (The Door Opener)**
*Use this to write Page 1 of your report. This uses the "Answer First" principle.*

**Prompt:**
```text
ROLE: Strategy Partner at a top-tier consulting firm.
AUDIENCE: The CEO. (Busy, non-technical, hates jargon).
TASK: Write the Executive Summary for this PDD.

STRUCTURE REQUIREMENTS:
1. THE HOOK: Start with the financial loss or pain of the status quo (The "Villain").
2. THE SOLUTION: Briefly describe the V3.0 Workflow, emphasizing the Safety Architecture (Auditor Node).
3. THE ASK: A clear, concise request to move to Pilot Phase.

EXAMPLE TONE (Few-Shot):
- Bad: "We built a great bot using Python and OpenAI."
- Good: "Current manual processing costs the firm $50k/year in wasted hours. We have designed a secure, audited solution to reclaim 90% of that cost."

YOUR TURN:
Write the summary. Keep it under 200 words.
```

---

### **PHASE 4: THE TRANSLATION LAYER (Tech $\to$ Business)**
*Use this if you are struggling to explain a complex diagram node (like a Router or Loop) to a non-technical person.*

**Prompt:**
```text
ROLE: Product Manager.
TASK: Translate a technical feature into a business benefit.
INPUT FEATURE: [Insert Feature, e.g., "The Router Node" or "The Retry Loop"].

TRANSLATION RULES:
1. Do not explain *how* it works (no "JSON" or "API").
2. Explain *why* it matters (Risk, Speed, or Reliability).

EXAMPLE:
- Tech: "We added a Human-in-the-Loop Router if confidence < 0.7."
- Business: "We installed a Safety Net that instantly routes complex issues to a human manager, ensuring no VIP client receives a bad answer."

YOUR TURN:
Translate my Input Feature.
```

---

### **PHASE 5: THE PITCH SCRIPT (Live Session Prep)**
*Use this to generate your script for the "Lightning Round" presentation.*

**Prompt:**
```text
ROLE: Speechwriter.
TASK: Write a 3-minute pitch script for the Board of Directors.
TONE: Confident, Urgent, Professional.

NARRATIVE ARC:
1. The Status Quo: Describe the pain of the user today (The "Villain").
2. The Inciting Incident: Why we can't ignore this anymore (Cost/Risk).
3. The Magic: How the Workflow acts as a "Co-Pilot" to solve it.
4. The Resolution: The ROI and future outlook.

CONSTRAINT: Keep it under 400 words. Use short, punchy sentences.
```
