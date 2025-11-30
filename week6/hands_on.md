# **Week 6 Hands-On Demo: "The Final Assembly" (Revised)**

**Title:** "The AI Consultant: Auditing & Packaging Your PDD"
**Duration:** ~20 Minutes
**Instructor Persona:** The Editor-in-Chief.

---

### **PART 0: THE ARTIFACTS (PRE-CLASS PREP)**
*(Same `Draft_PDD.txt` as before)*

---

### **PART 1: THE DEMO SCRIPT**

#### **1. Intro (0:00 – 3:00)**
**(Visual: Split Screen. Left: `Draft_PDD.txt`. Right: ChatGPT.)**

**Instructor:**
"Welcome to the finish line. You have your Logic Map and your Risk notes. But right now, they are just scattered notes.

Today, we are going to use **Few-Shot R.A.F.T. Prompts** to turn these rough notes into a professional proposal.

**Crucial Lesson:** Never use naked jargon in a prompt. If you just tell the AI to 'Make it SMART' or 'Use the Minto Principle,' you are trusting *its* definition, which might be wrong. We must **explicitly define** our terms in the prompt to force the result we want."

---

#### **2. The Context Dump (3:00 – 5:00)**
**(Visual: Copying `Draft_PDD.txt` into ChatGPT.)**

**Instructor:**
"First, we load the context. I am copying my entire rough draft."

**(Action: Paste Prompt)**
> "I am pasting my Draft Process Design Document (PDD) for a Refund Automation System. Read it, analyze the logic, and reply only with 'READY' when you have processed it. Do not summarize yet."

---

#### **3. The Deep Clean (Risk Audit) (5:00 – 10:00)**

**Instructor:**
"First, the Risk Audit. I'm not just asking for 'Risks.' I am defining the *categories* of risk I care about to prevent generic advice."

**(Action: Copy/Paste this Prompt)**

```text
ROLE: Senior Risk Consultant.
AUDIENCE: The Internal Technical Team (Be critical and specific).
TASK: Audit the "Risk Assessment" section of the PDD I provided.
FORMAT: Bullet points with "Risk Name", "Specific Scenario", and "Mitigation".

DEFINITIONS:
- "Blind Spots": Vulnerabilities related specifically to Data Privacy (PII) or Algorithmic Bias that I missed.

EXAMPLE (Few-Shot):
- Bad: "The bot might lie."
- Good: "Risk: Hallucination. Scenario: Bot invents a 50% discount policy that doesn't exist. Mitigation: Grounding via RAG."

YOUR TURN:
Critique my draft. Identify 2 specific "Blind Spots" based on the definition above.
```

**(Visual: LLM generates risks like "PII Leakage in Chat Logs".)**

**Instructor:**
"Perfect. By defining 'Blind Spot' as PII/Bias, we forced the AI to look at Ethics, not just bugs."

---

#### **4. The Value Polish (Explicit SMART KPIs) (10:00 – 15:00)**

**Instructor:**
"Now, the Business Case. My draft says *'Improve efficiency.'* That’s useless.
We need **SMART KPIs**. But I won't just say 'Make it SMART.' I will paste the definition into the prompt to ensure the AI does the math."

**(Action: Copy/Paste this Prompt)**

```text
ROLE: Business Analyst.
AUDIENCE: The CFO (Focus on hard dollars and timelines).
TASK: Convert my vague goal ("Improve efficiency") into a quantifiable KPI.
CONTEXT: Manual process takes 5 hours/week. Hourly rate is $50.

CONSTRAINT (S.M.A.R.T. Definition):
- Specific: What task is changing?
- Measurable: Use exact numbers (Hours/$).
- Achievable: Assume 80% automation, not 100%.
- Relevant: Link to Cost Savings.
- Time-bound: Set a deadline (e.g., Q3).

EXAMPLE (Few-Shot):
- Input: "Make it faster."
- Output: "Reduce Cycle Time from 48h to 5m by Q3, saving $12k/year."

YOUR TURN:
Convert "Improve efficiency" using the context and constraints above.
```

**(Visual: LLM Output: "Reduce weekly manual processing from 5 hours to 1 hour (80%) by Month 3, saving $10,400 annually.")**

**Instructor:**
"Look at that. It didn't just guess; it followed our 'Achievable' constraint (80% automation) because we explicitly defined it."

---

#### **5. The Executive Summary (Structured Narrative) (15:00 – 20:00)**

**Instructor:**
"Finally, the Executive Summary. We want the **Answer First** style. Again, I define the structure explicitly."

**(Action: Copy/Paste this Prompt)**

```text
ROLE: Strategy Partner.
AUDIENCE: The CEO (Lao Wang). He is busy and hates jargon.
TASK: Write the Executive Summary.

STRUCTURE REQURIEMENTS:
1. THE HOOK: Start with the financial loss of the status quo (The "Villain").
2. THE SOLUTION: Briefly describe the V3.0 Workflow and the Auditor Node.
3. THE ASK: A clear request to move to Pilot Phase.

EXAMPLE TONE (Few-Shot):
- Bad: "We built a great bot using Python."
- Good: "Current manual processing costs the firm $50k/year. We have designed a secure solution to reclaim 90% of that cost."

YOUR TURN:
Write the summary. Keep it under 200 words.
```

**(Visual: LLM generates the summary.)**

**Instructor:**
"This is your 'Door Opener.' Copy this to Page 1 of your PDD.

**Final Lesson:** The quality of the output depends on the **Definition** in the prompt. Don't use jargon; use Logic."

---
