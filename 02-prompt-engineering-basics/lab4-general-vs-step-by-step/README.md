# Lab 4 — General Prompt vs. Step-by-Step Instructions (A/B Comparison)
**Arda Palas · Samsung Innovation Campus · Generative AI & Marketing — Chapter 2: Prompt Engineering Basics**

**Learning goal:** Experience the impact of logical sequencing by comparing a **General Prompt (A)** with **Step-by-Step Instructions (B)** on the *same* task.

**Chosen scenario (course-aligned): launch a social-media marketing campaign** for a new product — a budget productivity app called **"FocusFlow"** targeting university students.

---

## Lab 4-1 — Understanding the Task and Scenario

**Mission:** Analyze the task to see why a *single* instruction might fail.

A marketing campaign is not one action — it's a chain of dependent decisions. If you skip a stage, everything downstream is guessed rather than reasoned. The "hidden steps" behind "make me a campaign":

1. Define the **target audience** precisely (who, pain point).
2. Set the **campaign goal & KPI** (awareness? installs? which metric?).
3. Choose the **channels** that match that audience.
4. Craft the **core message / value proposition**.
5. Produce **channel-specific content** (post copy, hashtags, CTA).
6. Define a **posting schedule** and how success is measured.

### Activity — hidden-step sequence
> "To solve this task perfectly, the AI must first **define the exact target audience and their pain point**, then **choose goal-appropriate channels and a core message**, and finally **write channel-specific content with a schedule and a success metric.**"

---

## Lab 4-2 — Designing and Executing Prompt A (General Technique)

**Mission:** Put everything in a single unified block to test baseline performance.

**Prompt A (general):**
> "Create a social media marketing campaign for FocusFlow, a budget productivity app for university students. Include the audience, channels, messaging, and some post ideas."

**Output A (excerpt):**
> **FocusFlow Campaign**
> - **Audience:** university students who want to be more productive.
> - **Channels:** Instagram, TikTok, Twitter, Facebook, LinkedIn.
> - **Message:** "Stay focused, get more done with FocusFlow!"
> - **Post ideas:** motivational quotes, app screenshots, study tips, a giveaway.
> - Post regularly and engage with followers.

**Observation:** Fast and broad, but shallow. The audience is generic ("students who want to be productive"), channels are a *catch-all list* (LinkedIn/Facebook don't fit this audience), there's **no measurable goal**, and the content is interchangeable with any app.

### Activity — evaluation of Prompt A
> "Prompt A produced a result that felt **generic and unfocused** because the AI **missed** the specific constraint of **a single measurable goal and a precisely-defined audience — it listed every channel instead of choosing the right ones.**"

---

## Lab 4-3 — Designing and Executing Prompt B (Advanced Technique)

**Mission:** Break the task into logical milestones to guide the AI's chain of thought.

**Prompt B (step-by-step):**
> "Act as a social media marketing strategist. Build a campaign for FocusFlow (a budget productivity app for university students). Work through these steps in order, and show your reasoning at each step:
> 1. **Audience:** Define ONE specific primary persona and their #1 pain point.
> 2. **Goal + KPI:** Pick ONE measurable objective and the metric to track it.
> 3. **Channels:** Choose only the 2 channels that best fit that persona, and justify why (exclude the rest).
> 4. **Core message:** Write one value proposition tied to the pain point.
> 5. **Content:** Write 3 concrete posts (platform, copy, hashtags, CTA).
> 6. **Schedule + measurement:** Give a 1-week posting cadence and how we'll judge success."

**Output B (excerpt):**
> **1. Audience:** *Second-year student who starts assignments the night before and feels constant low-grade guilt about procrastination.* Pain point: **can't start**, not "wants to be productive."
> **2. Goal + KPI:** Drive **app installs** in month 1; KPI = **install-through rate from TikTok bio link** (target 4%).
> **3. Channels:** **TikTok** (where the persona already scrolls during procrastination) + **Instagram Reels** (repurpose). *Excluded LinkedIn/Facebook — wrong audience; excluded Twitter — low install intent.*
> **4. Core message:** "You don't need more discipline — you need a smaller first step. FocusFlow starts you in 10 seconds."
> **5. Content:**
> - *TikTok:* POV of opening a laptop, freezing, then a 10-sec FocusFlow start. Copy: "The hardest part is starting. So we made starting stupidly easy." #studytok #procrastination CTA: "Link in bio — start your first session free."
> - *Instagram Reel:* before/after study desk. CTA: "Tap the link, block your first 25 min."
> - *TikTok:* student duet reacting to their own screen-time report. CTA: "Try FocusFlow tonight."
> **6. Schedule:** 3 TikToks + 2 Reels/week, post 7–9pm (pre-study hours); review install-through rate weekly, double down on the best-performing hook.

**Observation:** Each stage *constrains the next*. A sharp persona forces a real pain point, which forces the right channels, which shapes message and content. The output is executable, not decorative.

### Activity — comparing depth of logic
> "By using Step-by-Step instructions, the AI was able to **reason about *why* each channel and message was chosen (and explicitly reject the wrong ones), tie everything to one measurable KPI, and produce ready-to-post content**, which was missing in the general approach of Prompt A."

---

## Lab 4-4 — Comparing and Summarizing Results

| Dimension | Prompt A (General) | Prompt B (Step-by-Step) |
|-----------|--------------------|-------------------------|
| Audience | Generic ("productive students") | One sharp persona + real pain point |
| Goal / KPI | None | 1 measurable KPI (install-through 4%) |
| Channels | All 5, unfiltered | 2 justified, 3 explicitly rejected |
| Message | Interchangeable slogan | Tied to the specific pain point |
| Content | Vague "post ideas" | 3 ready-to-post pieces w/ CTA |
| Usability | Needs rework | Executable as-is |
| Speed | Faster | Slower but far higher quality |

The **control gap:** in Prompt A the AI made all decisions silently and simultaneously, so it defaulted to safe averages. In Prompt B, sequencing forced a *decision at each stage* that the next stage had to respect — that's where professional accuracy comes from.

### Activity — performance comparison
> "The biggest difference was **that step-by-step forced explicit, justified decisions at every stage instead of safe averages**. While Prompt A felt like a **generic brochure anyone could have written**, Prompt B provided a **targeted, executable, measurable** solution because it forced the AI to **reason through each dependent decision in order and reject the options that didn't fit.**"

---

## Lab 4-5 — A/B Usage Criteria & My Own Rule

**When each technique wins:**

- **General (A)** is best when I need **speed, a first draft, or broad brainstorming**, or when the task is simple and single-stage (e.g., "give me 10 hashtag ideas").
- **Step-by-Step (B)** is best when the task has **dependent stages, needs measurable output, or professional accuracy** (a real campaign, a financial analysis, a multi-part deliverable).

### Activity — my golden rule
> "I will use **Prompt A when I need a fast first draft or quick brainstorm on a simple, single-stage task**, and **Prompt B when the task has multiple dependent decisions and I need an accurate, executable, measurable result**, to ensure my AI outcomes are always **reasoned and ready-to-use rather than generic.**"

---

## Key takeaway
Step-by-step prompting doesn't just make the answer longer — it changes *how* the model decides. By forcing one justified decision per stage (and letting each stage constrain the next), it converts a plausible-sounding draft into a professional, executable plan. General prompts are for speed; sequential prompts are for accuracy.
