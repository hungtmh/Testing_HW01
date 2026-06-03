# AI Critique

**Student ID:** 23127195 | **Date:** 03/06/2026

---

## AI Critique (200–300 words)

Throughout the process of using ChatGPT GPT-4o and Gemini 1.5 Pro to assist with HW01, I identified consistent and structurally similar weaknesses in both tools.

**On the QA/QC mindmap:** The AI-generated output appeared well-structured at first glance, but when cross-referenced with the ISTQB Foundation Level Syllabus, it was clear the AI could not accurately differentiate between the finely stratified roles defined by ISTQB—such as Test Analyst, Technical Test Analyst, and Test Lead—treating them as a single undifferentiated "tester" category. AI also exhibited a strong **waterfall-model bias**, omitting Agile-specific QA roles entirely. This reflects a training data imbalance: older documentation in English dominates, while modern Agile and AI-era QA materials are underrepresented. The AI *looked* confident without *being* accurate.

**On the physical device test cases:** AI completely failed to generate any safety-critical or interaction-based edge cases (TC13, TC14, TC15). The core reason is that AI is trained on text—it has no embodied, physical-world experience. It cannot reason that a blocked fan blade will cause motor overheating, or that a smooth tile floor provides zero friction for a plastic base under lateral force. These insights come from **hands-on domain knowledge**, not from reading specifications.

**Principle learned for AI collaboration on this homework:** AI is a powerful "starting point" accelerator—useful for scaffolding, brainstorming, and formatting. But it functions as a junior assistant who has only read the manual, not tested the product. The experienced tester's role is to ask: *"What happens when things go wrong in the real world?"*—a question AI cannot formulate on its own. For safety-critical physical testing, AI output must always be treated as a first draft requiring human review, domain validation, and adversarial thinking.

**Word count: ~255 words**
