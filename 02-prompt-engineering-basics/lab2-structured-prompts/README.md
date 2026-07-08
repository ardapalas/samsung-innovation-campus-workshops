# Lab 2 — Designing Specific Tasks with Structured Prompts
**Arda Palas · Samsung Innovation Campus · Generative AI & Marketing — Chapter 2: Prompt Engineering Basics**

**Lab objective:** Master the prompt-engineering cycle by systematically assembling prompt elements and tuning the result for optimal quality. Across five sub-labs I build an **AI Study Coach** that produces a realistic, *adherence-focused* study plan.

---

## Lab 2-1 — Step-by-Step Prompt Element Practice

**Mission:** Build a Professional Health Coach and watch how adding one prompt element at a time transforms a vague request into a high-quality, actionable answer.

I ran the same core task ("give me a plan to get healthier") six times, adding one element each step, to feel where the biggest "quality jump" happens.

| Step | Element added | Prompt | What changed in the output |
|------|---------------|--------|----------------------------|
| 0 | *(none — baseline)* | "Give me a plan to get healthier." | Generic bullet list: eat well, exercise, sleep. No numbers, not personal. |
| 1 | **Role** | "**Act as a certified health coach.** Give me a plan to get healthier." | More authoritative tone, mentions sustainability, still generic. |
| 2 | **Context** | "…I'm a 21-year-old CS student who sits 10+ hours/day and skips breakfast." | Now targets sitting and skipped meals specifically. |
| 3 | **Goal / Task** | "…**Goal:** more energy during long study sessions, not weight loss." | Reframes around energy & focus instead of dieting. |
| 4 | **Constraints** | "…**Constraints:** budget-friendly, ≤30 min/day, no gym." | Home workouts, cheap meals, realistic time budget. |
| 5 | **Format** | "…Return a **7-day table**: Day / Movement / Meal focus / Energy tip." | Clean structured table, easy to actually follow. |
| 6 | **Tone / Persona** | "…Keep it **encouraging and non-judgmental**." | Supportive language, reduces guilt — more likely to stick. |

**Representative result (Step 6 output, excerpt):**

> **Your 7-Day Energy-First Plan** 🌿
> | Day | Movement (≤30 min) | Meal focus | Energy tip |
> |-----|--------------------|-----------|------------|
> | Mon | 15-min brisk walk between study blocks | Protein breakfast: eggs + oats | Stand up every 45 min |
> | Tue | 20-min bodyweight circuit (no gym) | Add veg to lunch | 10-min sunlight before studying |
> | … | … | … | … |
> *"No perfect days needed — consistency beats intensity. You've got this."*

### Activity — my reflection
> "I felt the biggest 'quality jump' at **Step 3 (Goal/Task)**, because that's where the AI stopped giving generic health advice and started solving *my actual problem* — energy for long study sessions instead of weight loss. Also, the element I will use most often is **Constraints**, because it's what forces the AI to stay realistic (time, budget, no gym) instead of producing an ideal-world plan I'd never follow."

---

## Lab 2-2 — Creating My Own AI Study Coach

**Mission:** Design an AI Study Coach that generates a realistic, *adherence-focused* study plan for a scenario.

**Scenario:** "A university student preparing for finals in 3 subjects over 2 weeks, who studies well for two days then abandons every plan by day three."

**Discussion — the core problem:** The student's real problem isn't *knowledge*, it's *adherence* ("hard to stick to plans"). So the single most important thing to give the AI is not more content — it's a **Constraint that builds in realism and recovery**.

**My key constraint/instruction:**
> "Build the plan around **≤3 hours of focused study per day**, include **at least one rest day**, and add a **'fallback rule': if a day is missed, do NOT reschedule everything — just continue from today.** Never assume a perfect week."

This directly attacks the failure mode: most plans collapse on day three because one missed day makes the whole schedule feel "broken," so the student quits. A fallback rule removes the all-or-nothing trap.

### Activity — my strategy
> "I think adding a **'missed-day fallback rule' (don't reschedule everything, just continue)** is key to making this plan realistic because the student doesn't quit from lack of a plan — they quit the moment one missed day makes the whole plan feel already failed."

---

## Lab 2-3 — Structured Prompt Design (Master Template)

**Mission:** Organize the study-coach instructions into a clear, hierarchical **master template** the AI can parse with high accuracy.

```
[ROLE]
You are an experienced study coach specializing in adherence and habit design,
not just information delivery.

[CONTEXT]
- Student: university student, 3 subjects, finals in 14 days.
- Known problem: motivated for ~2 days, then abandons plans.
- Available: ~3 focused hours/day, evenings free.

[GOAL]
Produce a 14-day study plan the student can REALISTICALLY finish,
prioritizing consistency over volume.

[CONSTRAINTS / REALITY RULES]
1. Max 3 focused hours/day (use 25/5 Pomodoro blocks).
2. At least 2 rest/light days across the 2 weeks.
3. Fallback rule: if a day is missed, continue from today — never reschedule the whole plan.
4. No more than 2 subjects per day (avoid context-switching fatigue).

[OUTPUT FORMAT]
- A 14-day table: Day | Subject(s) | Focus blocks | Micro-goal.
- End with a 3-line "If you fall behind" survival note.

[TONE]
Encouraging, non-judgmental, realistic. No guilt, no "grind harder" language.
```

### Activity — my design logic
> "I intentionally designed the **[Constraints / Reality Rules]** section to **cap daily load and add a missed-day fallback** because **that is the exact point where real study plans break**. The reason I chose the **'continue from today, don't reschedule' input** for the Constraints section was to prevent the AI from **producing a rigid, all-or-nothing schedule that collapses after the first missed day.**"

---

## Lab 2-4 — Model Execution and 1st Result Check

**Mission:** Run the template and evaluate the output against the "Reality Rules" I defined.

**First output (excerpt):**

> **14-Day Realistic Finals Plan**
> | Day | Subject(s) | Focus blocks | Micro-goal |
> |-----|-----------|--------------|------------|
> | 1 | Math | 3 × 25 min | Finish chapter 1 problem set |
> | 2 | Physics | 3 × 25 min | Summarize key formulas |
> | 3 | Light day | 1 × 25 min review | Just re-read notes |
> | … | … | … | … |
> *"If you fall behind: skip, don't stack. Continue from today's row."*

**Critical evaluation against my Reality Rules:**

| Reality Rule | Followed? | Note |
|--------------|-----------|------|
| ≤3 focused hours/day | ✅ | All days ≤3 blocks |
| ≥2 rest/light days | ⚠️ | Only 1 clear light day in first output |
| Missed-day fallback present | ✅ | Survival note included |
| ≤2 subjects/day | ✅ | Never exceeded |

The gap: the AI under-delivered on **rest days** — it defaulted to productivity and only inserted one light day, quietly weakening the adherence goal.

### Activity — my tuning plan
> "Initially, the AI **only inserted one light/rest day and front-loaded the hardest subjects, which quietly breaks the adherence goal**, so I plan to refine the **[Constraints / Reality Rules]** section by **making the 2 rest days explicit and fixed (e.g., 'Day 4 and Day 10 are mandatory light days')** to improve accuracy."

---

## Lab 2-5 — Prompt 1st Tuning and Re-execution

**Mission:** Refine the template based on Lab 2-4 to maximize adherence and realism.

**Change made** (Constraints section):
```
2. Rest days are MANDATORY and FIXED: Day 4 and Day 10 are light-review only
   (max 1 block). Do not fill them with new material.
```
I also added: *"Distribute the hardest subject across the whole 2 weeks — never front-load it."*

**Re-execution (excerpt):**

> | Day | Subject(s) | Focus blocks | Micro-goal |
> |-----|-----------|--------------|------------|
> | 4 | 🟢 Light day | 1 × 25 min | Flashcards only, no new topics |
> | … | … | … | … |
> | 10 | 🟢 Light day | 1 × 25 min | Rest + light review |

Now both rest days appear exactly where intended, the hard subject is spread evenly, and the plan *feels* survivable — which is the whole point.

### Activity — my final refinement strategy
> "By adjusting the **[Constraints / Reality Rules]** section, I was able to solve the problem of **the AI silently dropping rest days and front-loading hard subjects**, resulting in a plan that is **realistic, recoverable, and actually stick-able — one that respects a real student's motivation curve instead of an idealized one.**"

---

## Key takeaway
The most powerful lever in this whole lab was not *adding more information* — it was writing **Constraints / Reality Rules** that anticipate *how the task fails in real life* (missed days, dropped rest, front-loading). Structure controls the AI; realism-focused constraints control the *usefulness*.
