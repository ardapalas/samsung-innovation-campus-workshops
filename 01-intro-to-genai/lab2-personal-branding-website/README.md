# Personal Branding Website — Vibe Coding

A single-file personal branding website built entirely through Generative AI prompting, as part of **Lab 2** of the Samsung Innovation Campus *Generative AI & Marketing* program.

**Live site:** _add your GitHub Pages link here_ · **Source:** [`index.html`](./index.html)

> Built with the end-to-end vibe-coding workflow: **define → visualize → build → refine**. No manual design or hand-written layout — every section, illustration, and style choice was produced by prompting an AI, then reviewed and improved.

**Tech:** Single self-contained `index.html` · vanilla HTML/CSS/JS · embedded SVG illustrations · scroll-reveal animations · fully responsive · zero dependencies.

---

## Lab 2 — Process Documentation

This document records the workflow and the prompts used for each step.

### Step 1 — Define Your Personal Profile

**Goal:** Describe who I am so the AI structures my identity into three sections.

**Prompt used:**
> "I'm a Mathematics & Computer Science student (İstanbul Kültür University, GPA 3.20) and a Software Intern at Garanti BBVA Teknoloji. I build both AI/ML systems (RAG, LangGraph agents, PyTorch, Transformers) and full-stack web products (Next.js, React, Supabase, PostgreSQL). Organize this into three sections — *Who I Am*, *My Skills*, *My Future Goal* — and frame me as a **Full-Stack AI Developer** who takes projects from the model all the way to the user interface."

**Result:**

- **Who I Am** — An engineer at the intersection of ML and software engineering, who wraps models in reliable pipelines and clean interfaces and ships them.
- **My Skills** — Full-stack across the whole vertical: AI/LLM core (PyTorch, LangGraph, RAG), backend (Supabase, PostgreSQL), and frontend (Next.js, React, Tailwind). Backed by four deployed projects.
- **My Future Goal** — Grow into a Full-Stack AI Developer / AI Product Engineer role, building trustworthy AI products end-to-end, with a focus on finance where reliability matters.

### Step 2 — Generate Your Images

**Goal:** Three visuals that represent each section, driven by style/mood/purpose prompts.
Chosen approach: **vector (SVG) illustrations embedded in the site** — modern, crisp on any screen, and load instantly with no external files.

**Image prompt — Who I Am:**
> "Minimal flat vector portrait of a developer, soft blue (#2563eb) palette on white, with small floating badges for `</>` and `AI` orbiting the figure. Calm, professional, clean line-art mood."

**Image prompt — My Skills:**
> "Isometric stacked-layer diagram in blue gradient: three tiers labeled *AI/LLM*, *Backend*, *Frontend* — communicating one person owning the full stack. Modern, technical, minimal."

**Image prompt — My Future Goal:**
> "An upward line-chart path climbing from *Student* → *Intern* → *AI Dev* toward a small flag/goal marker, blue gradient stroke on white. Optimistic, forward-moving, growth mood."

A hero illustration (code window + neural-node cluster) was also generated to set the AI-developer tone at the top of the page.

### Step 3 — Build Your Personal Website

**Goal:** A complete HTML site using the three sections and the images.

**Prompt used:**
> "Create a complete single-file HTML personal website for a Full-Stack AI Developer. Minimal, clean, light theme; blue accent (#2563eb); generous whitespace; modern sans-serif typography. Sticky nav, hero, then three sections — *Who I Am*, *My Skills* (with a project grid), *My Future Goal* (with stats) — plus a contact block. Embed my three section illustrations as SVG. Add subtle scroll-reveal animations and hover effects. Fully responsive."

**Result:** `index.html` — sticky glass nav, clean hero, alternating text/illustration blocks, a 4-card project grid (Study Buddy, Financial Risk Analyst Agent, TaskFlow Kanban, GTSRB Classifier), a stats row, and a contact CTA. No external dependencies.

### Step 4 — Review and Improve

**What I evaluated and refined with AI:**

- **Clarity of positioning** — tightened the headline to *"Building intelligent products from data to interface"* so the Full-Stack AI angle is obvious in the first three seconds.
- **Evidence over adjectives** — replaced generic claims with concrete numbers (85% accuracy, 43 classes, ~39k images, 4+ deployed projects).
- **Visual hierarchy** — alternating layout and scroll-reveal so each section reads as a distinct chapter rather than a wall of text.
- **Trust signals** — surfaced the Garanti BBVA internship and RAGAS/LangSmith evaluation work, since reliability is central to my finance/AI goal.

**Share Your Result:**
> "I aimed for a **Full-Stack AI Developer** role, and I wanted my website to feel **clean, modern and trustworthy**. I used AI to improve **my positioning, visual hierarchy, and the way concrete results are presented** so that it better reflects my future career."

---

*Arda Palas · Samsung Innovation Campus — Generative AI & Marketing · 2026*
