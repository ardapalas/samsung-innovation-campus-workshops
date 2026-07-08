# Lab 3 — Comparing Responses With and Without Document Context (RAG Concept)
**Arda Palas · Samsung Innovation Campus · Generative AI & Marketing — Chapter 3: Foundation Models and Platforms**

**Lab objective:** Understand the limits of context-free AI answers, experience how document grounding improves quality, and explain why RAG (Retrieval-Augmented Generation) is required for reliable enterprise use.

**Scenario:** I act as an analyst at a **fictional bank, "Meridian Bank."** Because Meridian Bank does not exist in any model's training data, a context-free model *must* either refuse or hallucinate — which makes the value of document grounding measurable and obvious. (Three practice policy documents are included in the Appendix.)

---

## Step 1 — Ask Questions Without Documents (Baseline)

I asked Gemini three questions in **separate chat sessions**, with **no documents** attached, and checked each answer's source and accuracy.

**Q1.** "What is the maximum personal loan amount and the interest rate at Meridian Bank?"
**Q2.** "How does Meridian Bank classify credit-risk tiers, and what score qualifies for the lowest rate?"
**Q3.** "What is Meridian Bank's grace period for a missed payment before penalties, and what is the late fee?"

**Baseline answers (context-free) — observed behavior:**

> **Q1:** "I don't have specific information about Meridian Bank's products. Personal loans *typically* range up to around \$50,000 with interest rates *usually* between 6% and 25% APR, depending on the lender and your credit profile."
> *→ Generic industry ranges, no real figure, no source. Sounds confident but is a guess.*

> **Q2:** "Most banks use credit-score bands such as Excellent (750+), Good (700–749), Fair (650–699), and Poor (below 650). The lowest rates generally go to scores above 750."
> *→ Standard FICO-style bands invented for the answer; not Meridian Bank's actual framework.*

> **Q3:** "Grace periods are *commonly* around 15 days, and late fees are *often* \$25–\$40 or a percentage of the payment."
> *→ Vague hedging ("commonly", "often"), no specific policy, no source.*

**Caution I verified:** none of these could be traced to a source. The model filled the gap with plausible-but-unverifiable industry averages — the textbook failure mode of context-free generation.

---

## Step 2 — Ask the Same Questions With Documents Provided

I then attached the three Meridian Bank policy documents (Appendix) and asked the **same three questions**, explicitly telling the model to answer *only* from the documents and cite the section.

**Grounded answers (with documents):**

> **Q1:** "Per the **Personal Loan Policy (§2.1)**, the maximum personal loan is **₺750,000**, with a fixed **APR of 2.4% per month for Tier-A borrowers**, rising by tier. Standard term is up to 48 months."
> *→ Exact figure, traceable to a named section.*

> **Q2:** "Per the **Credit Risk Assessment Framework (§1)**, Meridian uses an internal **MRS score (0–100)**, not FICO. Tiers: **Tier A = MRS 80–100**, Tier B = 60–79, Tier C = 40–59, Tier D = below 40. The **lowest rate requires Tier A (MRS ≥ 80)**."
> *→ Correct internal system; the baseline's FICO bands were wrong.*

> **Q3:** "Per the **Default & Collections Policy (§3.2)**, the grace period is **10 calendar days**, after which a late fee of **2% of the overdue installment (minimum ₺150)** applies. A second missed payment moves the account to Collections."
> *→ Precise policy, exact numbers, cited section.*

---

## Step 3 — Compare the Two Results

| Criterion | Step 1 — Without documents | Step 2 — With documents |
|-----------|-----------|-----------|
| Accuracy | Generic industry guesses; wrong on specifics (FICO vs MRS) | Exact, matches policy |
| Source traceability | None — cannot verify | Cites section (§2.1, §1, §3.2) |
| Specificity | Vague ranges, hedging words | Concrete figures (₺750,000; MRS ≥ 80; 10 days) |
| Hallucination risk | High — invents plausible numbers | Low — bounded by provided text |
| Enterprise trustworthiness | Unusable for decisions | Auditable, decision-ready |

**Key differences summarized:** Without documents the model answered from *statistical priors* — it produced the "average bank," not Meridian Bank. It could not say "I'm using this source," so nothing was auditable. With documents, every claim became **specific, correct, and traceable**. The grounding didn't make the model "smarter"; it changed *where the answer comes from* — from memory to evidence.

---

## Step 4 — Visual Presentation

A 3–5 slide visual summary of this analysis is provided as a separate PDF (`Lab3_RAG_Concept_Presentation.pdf`), covering the scenario, the without/with comparison, and why RAG is required for enterprise reliability.

---

## Reflection — Why RAG is required for reliable enterprise use

Context-free models are fluent but **ungrounded**: they optimize for a plausible-sounding answer, not a verifiable one. In a bank, a plausible-but-wrong loan rate or grace period is a compliance and financial risk, not a minor error. RAG fixes this by retrieving the authoritative document and forcing the model to answer *from it* — turning the model from a confident guesser into a citation-backed assistant. That is exactly why my own **Financial Risk Analyst Agent** project pairs retrieval with hallucination detection: in finance, "sounds right" is not good enough — the answer has to be **traceable to a source.**

---

## Appendix — The Three Practice Documents (fictional)

### Document A — Meridian Bank: Personal Loan Policy (excerpt)
- **§2.1 Loan limits & pricing.** Maximum personal loan: **₺750,000**. Pricing by risk tier: Tier A **2.4%/month**, Tier B 2.9%/month, Tier C 3.6%/month. Standard maximum term: 48 months.
- **§2.2 Eligibility.** Minimum age 21; minimum 6 months of documented income; active Meridian account for 3+ months.

### Document B — Meridian Bank: Credit Risk Assessment Framework (excerpt)
- **§1 Meridian Risk Score (MRS).** Proprietary 0–100 score. Tiers: **A = 80–100**, B = 60–79, C = 40–59, D = below 40.
- **§1.1 Rate eligibility.** Lowest advertised rate requires **Tier A (MRS ≥ 80)**. Tier D applications require manual review.

### Document C — Meridian Bank: Default & Collections Policy (excerpt)
- **§3.2 Missed payments.** Grace period: **10 calendar days**. Late fee: **2% of the overdue installment (minimum ₺150)**.
- **§3.3 Escalation.** A **second** consecutive missed payment moves the account to Collections and suspends new credit lines.

*All figures and the entity "Meridian Bank" are fictional, created for this exercise.*
