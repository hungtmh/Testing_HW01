# AI Audit Report

**Student ID:** 23127195 | **Date:** 03/06/2026

---

## Appendix A – AI Audit Report [AI-02]

### Artifact 1 – QA/QC Role Mindmap (Requirement 1)

| Item | Content |
|------|---------|
| **(1) Prompt + Tool** | **Tool:** Gemini 3.1 Pro **\| Timestamp:** 09:00 02/06/2026 **\| Prompt:** *"Draw a comprehensive ISTQB-aligned mindmap of QA/QC roles and responsibilities in a software development organization. Include: role names, key responsibilities, skills required, tools used, and how each role interacts with other teams."* |
| **(2) AI Output** | ![QA/QC Role Mindmap](images/Mind%20map.png) |
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

### Artifact 2 – 12 Test Cases for Toshiba Fan (Requirement 3)

| Item | Content |
|------|---------|
| **(1) Prompt + Tool** | **Tool:** ChatGPT GPT-4o **\| Timestamp:** 10:30 02/06/2026 **\| Prompt:** *"Generate 12 practical test cases for testing the Toshiba F-LSA10(W)VN stand fan. Each test case must include: Objective, Precondition, Input, Steps, Expected Result. Cover these functions: power on/off, 3 speed levels, oscillation, timer, column height adjustment, physical stability."* |
| **(2) AI Output** | ![12 Test Cases](images/12%20TEST%20CASE.png) |
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

### Artifact 3 – 20 Software Defects (Requirement 2)

| Item | Content |
|------|---------|
| **(1) Prompt + Tool** | **Tool:** ChatGPT GPT-4o **\| Timestamp:** 11:15 02/06/2026 **\| Prompt:** *"Tạo cho tôi 20 lỗi software giữa năm 2022 tới năm 2026. Danh sách phải có ít nhất 5 lỗi liên quan đến AI/LLM Theo như yêu cầu của đề"* |
| **(2) AI Output** |  |
| **(3) Verdict** | **INCOMPLETE** |
| **(4) Reasoning** | AI successfully generated 20 defects with correct formatting and included 7 AI/LLM defects, satisfying the "at least 5" requirement. However, AI exhibited significant **recency bias, numerical hallucinations**, and **technical classification errors** (e.g., conflating OWASSRF with ProxyNotShell, hallucinating that Storm-2139 members were convicted when investigation was ongoing, or claiming lawyers in Mata v. Avianca were disbarred instead of fined). The AI's meta-critique of other models' biases was useful, but it itself repeated several of those same hallucinations. |
| **(5) Student Fix** | The student fact-checked all 20 defects against original security advisories, court filings, and news sources (e.g., NIST NVD, Palo Alto Advisories, BBC, court documents), correcting the severity levels, fixing dates, and documenting the specific hallucinations/biases present in AI-generated technical summaries. |

---

### AI Accuracy Ratio Summary

| Verdict | Count | Percentage |
|---------|-------|-----------|
| VALID | 0 | 0% |
| INCOMPLETE | 3 | 100% |
| INVALID | 0 | 0% |

**Conclusion – When to Use / Not Use AI:**

✅ **AI IS appropriate for:** Generating initial test case drafts for well-defined functional requirements; creating test data; writing boilerplate automation scripts; formatting reports; brainstorming test ideas to be validated by a human.

❌ **AI IS NOT appropriate for:** Safety-critical testing requiring domain knowledge (electrical, mechanical, thermal); long-duration/endurance testing; feature interaction testing based on real-world usage patterns; verification against specific technical standards (TCVN, IEC, UL).

---

### Helper Prompts for Supporting Files (ai_audit, ai_critique, ai_disclosure, git_commit_log, self_assessment)

| Purpose | AI Tool & Prompt |
|---------|------------------|
| **File Structure Template** | **Tool:** ChatGPT GPT-4o **\| Prompt:** *"Generate the skeletal structure and content templates for the following software testing homework files: `ai_audit.md` (containing AI audit logs), `ai_critique.md` (critique of AI assistance), `ai_disclosure.md` (mandatory AI use disclosure), `git_commit_log.md` (formatted git logs), and `self_assessment.md` (student grading checklist). Ensure each file complies with the course requirements for student ID 23127195, uses clean markdown, and has placeholders where human edits are required."* |
