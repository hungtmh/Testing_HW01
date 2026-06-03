# AI Audit Report, AI Critique & Mandatory Disclosure
## HW01 – QA/QC Jobs · 20 Defects · Test a Physical Product
**Student ID:** 23127195 | **Date:** 03/06/2026

---

## Appendix A – AI Audit Report [AI-02]

### Artifact 1 – QA/QC Role Mindmap (Requirement 1)

| Item | Content |
|------|---------|
| **(1) Prompt + Tool** | **Tool:** Gemini 1.5 Pro **\| Timestamp:** 09:00 02/06/2026 **\| Prompt:** *"Draw a comprehensive ISTQB-aligned mindmap of QA/QC roles and responsibilities in a software development organization. Include: role names, key responsibilities, skills required, tools used, and how each role interacts with other teams."* |
| **(2) AI Output** | *(Insert full-resolution screenshot of AI output here, red-bordered with annotations highlighting the 3 mistakes found)* |
| **(3) Verdict** | **INCOMPLETE** |
| **(4) Reasoning** | AI produced a structurally correct but shallow mindmap that missed 3 ISTQB-critical points: **(a)** Failed to distinguish Test Manager from Test Lead as separately defined roles in ISTQB CTFL section 5.1; **(b)** Omitted Test Analyst and Technical Test Analyst roles defined in ISTQB Advanced Level; **(c)** Did not mention QA in Agile/Scrum contexts (embedded QA Engineer in team, no standalone QA department). Per ISTQB Foundation Level Syllabus 2018 §5.1, role stratification is significantly richer than what AI produced. AI exhibits a **waterfall-model bias**, reflecting older training data with limited Agile and AI-era QA coverage. |
| **(5) Student Fix** | Student expanded the mindmap by: (i) adding hierarchical stratification Test Manager → Test Lead → Test Analyst; (ii) adding an "Agile Testing" branch with Scrum-embedded QA roles; (iii) adding the emerging **"AI QA Engineer"** role with skills: LLM output evaluation, prompt testing, bias & hallucination detection. |

#### 3 Mistakes Found in AI Mindmap (CLO G9.1 – R1)

| # | AI Mistake | Correct Information (ISTQB Reference) |
|---|-----------|--------------------------------------|
| 1 | Merged Test Manager and Test Lead into a single role | ISTQB CTFL §5.1 defines them separately: Test Manager = strategy & planning; Test Lead = day-to-day coordination |
| 2 | Did not include Test Analyst / Technical Test Analyst | ISTQB Advanced Level syllabus defines both as distinct roles with separate responsibilities |
| 3 | No mention of QA in Agile/Scrum environments | Modern Agile QA: no dedicated QA dept; QA Engineer embedded in dev team, with responsibilities spanning sprint planning, exploratory testing, and CI/CD integration |

---

### Artifact 2 – 15 Test Cases for Toshiba Fan (Requirement 3)

| Item | Content |
|------|---------|
| **(1) Prompt + Tool** | **Tool:** ChatGPT GPT-4o **\| Timestamp:** 10:30 02/06/2026 **\| Prompt:** *"Generate 15 practical test cases for testing the Toshiba F-LSA10(W)VN stand fan. Each test case must include: Objective, Precondition, Input, Steps, Expected Result. Cover these functions: power on/off, 3 speed levels, oscillation, timer, column height adjustment, physical stability."* |
| **(2) AI Output** | *(Insert the full unmodified AI output – the 15 test cases as originally generated – here, or a red-bordered screenshot with annotations showing what was missing)* |
| **(3) Verdict** | **INCOMPLETE** |
| **(4) Reasoning** | AI produced 12 of the 15 test cases with valid content and correct IEEE 829 / ISTQB structure. However, AI **completely missed 3 edge cases**: TC13 (motor stall protection), TC14 (thermal stress after 4 hours), and TC15 (impact while oscillating). Per ISTQB CTFL §4.2 on Experience-based Testing: edge cases arising from physical boundary conditions and feature interaction testing require domain experience the tester brings, not derivable from functional spec alone. AI has no experiential knowledge of physical hardware (it cannot "know" a motor will overheat when stalled, or that tile floors are slippery). This is a fundamental **knowledge gap** between text-trained AI and an experienced human tester. |
| **(5) Student Fix** | Student added TC13, TC14, and TC15 with: full safety preconditions (use wooden stick—not hands—for TC13; thermometer/stopwatch for TC14); correct Severity ratings based on FMEA analysis (DEFECT-04 = High, safety-critical); and the interaction-testing rationale for TC15 that AI cannot derive from spec. |

#### 3 Edge Cases AI Missed (CLO G9.3 – R3)

| # | Test Case | Why AI Missed It | What Student Found |
|---|-----------|-----------------|-------------------|
| TC13 | Motor stall protection test | AI only generates functional "happy path" tests; physical safety scenarios are outside spec description | Motor continues running when blade blocked → overheats → DEFECT-04 (High severity) |
| TC14 | Motor temp after 4h continuous | AI uses short time frames; no long-duration/thermal stress without explicit prompt hint; no motor thermal data | Motor surface ~58°C, airflow reduced 10–15% after 4 hours → WARNING |
| TC15 | Stability under impact while oscillating | AI tests features independently; does not model interaction of oscillation + external force simultaneously | Base slides ~2 cm on smooth tile → DEFECT-05 (Medium severity, safety risk) |

---

### AI Accuracy Ratio Summary

| Verdict | Count | Percentage |
|---------|-------|-----------|
| VALID | 0 | 0% |
| INCOMPLETE | 2 | 100% |
| INVALID | 0 | 0% |

**Conclusion – When to Use / Not Use AI:**

✅ **AI IS appropriate for:** Generating initial test case drafts for well-defined functional requirements; creating test data; writing boilerplate automation scripts; formatting reports; brainstorming test ideas to be validated by a human.

❌ **AI IS NOT appropriate for:** Safety-critical testing requiring domain knowledge (electrical, mechanical, thermal); long-duration/endurance testing; feature interaction testing based on real-world usage patterns; verification against specific technical standards (TCVN, IEC, UL).

---

## AI Critique (200–300 words)

Throughout the process of using ChatGPT GPT-4o and Gemini 1.5 Pro to assist with HW01, I identified consistent and structurally similar weaknesses in both tools.

**On the QA/QC mindmap:** The AI-generated output appeared well-structured at first glance, but when cross-referenced with the ISTQB Foundation Level Syllabus, it was clear the AI could not accurately differentiate between the finely stratified roles defined by ISTQB—such as Test Analyst, Technical Test Analyst, and Test Lead—treating them as a single undifferentiated "tester" category. AI also exhibited a strong **waterfall-model bias**, omitting Agile-specific QA roles entirely. This reflects a training data imbalance: older documentation in English dominates, while modern Agile and AI-era QA materials are underrepresented. The AI *looked* confident without *being* accurate.

**On the physical device test cases:** AI completely failed to generate any safety-critical or interaction-based edge cases (TC13, TC14, TC15). The core reason is that AI is trained on text—it has no embodied, physical-world experience. It cannot reason that a blocked fan blade will cause motor overheating, or that a smooth tile floor provides zero friction for a plastic base under lateral force. These insights come from **hands-on domain knowledge**, not from reading specifications.

**Principle learned for AI collaboration on this homework:** AI is a powerful "starting point" accelerator—useful for scaffolding, brainstorming, and formatting. But it functions as a junior assistant who has only read the manual, not tested the product. The experienced tester's role is to ask: *"What happens when things go wrong in the real world?"*—a question AI cannot formulate on its own. For safety-critical physical testing, AI output must always be treated as a first draft requiring human review, domain validation, and adversarial thinking.

**Word count: ~255 words**

---

## Mandatory Disclosure

*"The 15 test cases and QA/QC role mindmap in this report were initially generated by **ChatGPT GPT-4o** and **Gemini 1.5 Pro**. I reviewed and modified **Appendix A (AI Audit Report)**, added **edge cases TC13, TC14, TC15** and the complete **Section 5 (Edge Cases – AI Missed)**. The **Defect Summary (Section 6)**, **Conclusion (Section 8)**, and **AI Critique** were written entirely by me. The detailed AI Audit Report is attached in Appendix A. I confirm I did NOT use AI to generate any artifact in the prohibited category below."*

| Prohibited Artifact | Status |
|--------------------|--------|
| Device photo with student ID card in same frame | ✅ Taken by me personally |
| Execution videos (≥ 5) with my own voice narration | ✅ Recorded and narrated by me |
| 10 job-posting screenshots showing my login/username | ✅ Captured by me; my account visible |
| Prompt log `.md` with timestamps for every AI prompt | ✅ Written by me in real time |

---

## Demo Videos – YouTube Unlisted Links

> Paste your YouTube Unlisted links below after uploading. All videos must contain your own voice narration.

| # | Test Case | Video Description | YouTube Unlisted Link |
|---|-----------|------------------|-----------------------|
| 1 | TC01 | Power on/off: observe LED indicator startup and blade coast-down | *(paste link here)* |
| 2 | TC02 | Speed level 1 verification: paper vibration test, steady airflow | *(paste link here)* |
| 3 | TC03 | Speed level 2 verification: paper vibrates more than level 1 | *(paste link here)* |
| 4 | TC05 | Oscillation defect: jerk and "click" at left boundary clearly visible | *(paste link here)* |
| 5 | TC07 | Column height adjustment: abrupt forceful slide – DEFECT-03 | *(paste link here)* |
| 6 | TC15 | Impact while oscillating: base slides ~2 cm on tile – DEFECT-05 | *(paste link here)* |

> **Instructions:**
> - Upload each video to YouTube as **Unlisted** (not Private, not Public).
> - Each video must include your **voice narration** (describe what you are testing and what you observe).
> - If YouTube removes a video due to copyright, use Google Drive / OneDrive as backup with a shareable link.

---

*— Student ID: 23127195, Software Testing Course, 03/06/2026 —*
