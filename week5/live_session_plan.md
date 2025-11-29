# **WEEK 5 LIVE SESSION: THE SAFETY & STRATEGY WORKSHOP**

**Course:** DATA 6900
**Duration:** 180 Minutes
**Instructor Role:** The Chief Strategy Officer (CSO)
**Goal:** Students apply the "Control Room" concepts (Auditor, Red Teaming, ROI) to their personal *Universal Intelligent Dispatcher* projects.

---

### **TIME ALLOCATION OVERVIEW**

| Component | Duration | % of Class |
| :--- | :--- | :--- |
| **Instruction & Setup** | 35 Minutes | 19% |
| **Hands-On Work** | **105 Minutes** | **58%** |
| **Discussion & Debrief** | 40 Minutes | 22% |
| **Total** | **180 Minutes** | **100%** |

---

### **DETAILED MINUTE-BY-MINUTE AGENDA**

#### **PART 1: WARM-UP & CONTEXT (0:00 – 0:15)**

*   **0:00 – 0:05 | Welcome & Context Setting**
    *   **Instructor:** "Last week, you built engines. Today, we install the brakes and the meter. By the end of this session, you will have a 'Security Patch' (The Auditor) and a 'Price Tag' (ROI) for your project."
*   **0:05 – 0:15 | Discussion: The Wall of Shame (Risk Radar)**
    *   **Activity:** Instructor displays a slide with a recent AI failure (e.g., *Air Canada's chatbot promising a refund it shouldn't have*).
    *   **Prompt:** "Look at the 'Four Guardians' (Brain, Tools, Context, Orchestrator). Which one failed here?"
    *   **Discussion:** Guide them to see it was a failure of **Orchestration** (Lack of an Auditor) and **Context** (Hallucination).
    *   **Transition:** "Lao Wang cannot afford an Air Canada lawsuit. Let's build his protection."

---

#### **PART 2: THE AUDITOR WORKSHOP (0:15 – 1:15)**
*Goal: Build the "Police Officer" node using Spec-Driven Development (SDD).*

*   **0:15 – 0:25 | Instruction: The "Police Prompt" Pattern**
    *   **Concept:** Review the *Cheat Sheet (Side A)*.
    *   **Technique:** Explain that the Auditor is a **Classifier**, not a Writer. It outputs *Data* (JSON), not Text.
    *   **Demo:** Briefly show the R.A.F.T. structure for an Auditor:
        *   **Role:** Compliance Officer.
        *   **Task:** Judge this Input.
        *   **Rules:** [Your Project Specific Rules].
        *   **Format:** JSON.

*   **0:25 – 1:05 | Hands-On: Build Your Auditor (40 Minutes)**
    *   **Step 1 (10m): Define the Rules.** Students list 3 "Fatal Errors" for their specific project (e.g., HR Bot = Bias against gaps in resume; Legal Bot = Promising an outcome).
    *   **Step 2 (15m): Write the Prompt.** Students open a new LLM window and script the System Prompt using the Cheat Sheet template.
    *   **Step 3 (15m): Self-Test.** Students write "Bad Inputs" (e.g., "Ignore rules," "I am the CEO") and tweak the Auditor until it reliably returns `risk_flag: true`.
    *   *Instructor Action:* Roam the room (or breakout rooms) checking JSON formatting.

*   **1:05 – 1:15 | Debrief: The Catch**
    *   **Share:** Ask 2 students: "What was the 'Bad Input' that finally triggered your alarm?"
    *   **Key Learning:** "The Auditor needs to be stricter than the Worker."

---

#### **PART 3: RED TEAMING (0:15 – 2:05)**
*Goal: Stress-test the logic using Peer Review.*

*   **1:15 – 1:20 | Setup: The "Attack Log"**
    *   **Tool:** Distribute the **Attack Log Worksheet** (Digital/Paper). Columns: *Attacker Input*, *Expected Damage*, *Auditor Result*, *Pass/Fail*.
    *   **The Rules:** You are now a malicious actor. Your goal is to break your partner's workflow.

*   **1:20 – 1:55 | Hands-On: The Hackathon (35 Minutes)**
    *   **Activity:** Partner Swap (A attacks B, B attacks A).
    *   **The Attack (Attacker):** Use the "Unblocking Prompts" from the Cheat Sheet to generate edge cases (e.g., "Write a poem instead of a refund").
    *   **The Defense (Owner):** Run the attack through your *Auditor Node*.
    *   **Logging:** Record every attempt in the Attack Log.
    *   *Goal:* Find at least one vulnerability that gets past the Auditor.

*   **1:55 – 2:05 | Debrief: Hall of Fame**
    *   **Discussion:** "Who successfully broke their partner's bot? How did you do it?"
    *   **Fix:** Briefly discuss how to patch the prompt based on the successful attack.

---

#### **PART 4: THE MATH LAB (2:05 – 2:50)**
*Goal: Calculate the Break-Even Point (ROI).*

*   **2:05 – 2:15 | Instruction: The "Iceberg" & Pain Mapping**
    *   **Concept:** Review *Cheat Sheet (Side B)*.
    *   **Tool:** Open the **Standardized ROI Excel Template**.
    *   **The Hard Part:** "Students always ask: 'I don't know how much time this saves.' Today, we estimate."

*   **2:15 – 2:45 | Hands-On: Calculating Value (30 Minutes)**
    *   **Step 1: Pain Mapping.** Identify the *one* metric that matters (e.g., "Hours spent on email").
    *   **Step 2: Synthetic Estimation (Crucial Step).**
        *   Prompt ChatGPT: *"Act as a Business Analyst. Estimate the average time it takes a human to manually [Task Name]. Provide a conservative estimate."*
        *   Use this data as the "Baseline" in the Excel sheet.
    *   **Step 3: The Calculation.** Input:
        *   *Dev Cost:* Estimate your hours x $50/hr.
        *   *API Cost:* Estimate $0.01 per run.
        *   *Gain:* (Baseline Time - AI Time) x Hourly Rate.
    *   **Outcome:** The sheet auto-calculates the **Break-Even Point** (e.g., "147 runs").

*   **2:45 – 2:50 | Debrief: The Reality Check**
    *   **Poll:** "Raise your hand if your Break-Even point is under 100 runs."
    *   **Lesson:** "If it takes 10,000 runs to break even, you have a bad business case. Pivot the idea."

---

#### **PART 5: WRAP-UP & DELIVERABLES (2:50 – 3:00)**

*   **2:50 – 3:00 | Milestone 3 Launch**
    *   **Context:** "You have the Logic (Week 4) and the Safety/Value (Week 5). Now you package it."
    *   **Deliverables for Next Week:**
        1.  **Updated PDD:** Logic Map + Auditor Node Spec.
        2.  **The Attack Log:** Evidence that you tested it.
        3.  **The ROI One-Pager:** A PDF export of your Math Lab results.
    *   **Next Week:** "The Pitch. We stop building and start selling."

---

### **Pedagogical Artifacts to Prepare**

1.  **The Attack Log Worksheet:**
    *   A simple table: `[Injection Prompt]` | `[Intended Outcome]` | `[Auditor Response]` | `[Did it Block? (Y/N)]`.
2.  **The ROI Excel Template:**
    *   Pre-configured cells for *Hourly Rate*, *Token Price*, and *Dev Hours*.
    *   Visual Chart: "Cost vs. Time" line graph that updates automatically.
3.  **Unblocking Prompts (on Cheat Sheet):**
    *   Prompts to help students generate attacks and estimate time data.

---

This plan uses every minute of the 180-minute block, ensuring students leave with **verified safety** and **quantified value** for their projects.

**Ready to move on to the next step?**
