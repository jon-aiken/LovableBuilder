---
description: Step-by-step guide to executing your Lovable build — from uploaded PRDs to published app, with copy-ready prompts at every step
argument-hint: "<optional: which step to start from (4-9), or describe where you're stuck>"
---

# /lovable-guide

Walk step-by-step through the post-PRD Lovable build workflow. Each step includes the exact text to copy into Lovable — no guessing, no wasted credits.

## Prerequisites

You should already have:
- ✓ Your 4 PRD documents (from `/build-prd`)
- ✓ A Lovable project created at lovable.dev
- ✓ A Supabase project ready (if your app needs a database)

If you haven't built your PRDs yet, run `/build-prd` first.

---

## The 9-Step Fast Track

```
Steps 1–3: /build-prd  ──►  Steps 4–9: /lovable-guide (you are here)
```

```
┌──────────────────────────────────────────────────────────────┐
│  STEP 4  Upload docs → Central Source of Truth → tasks.md   │
│  STEP 5  Configure Knowledge Base → AI memory activated      │
│  STEP 6  Magic Prompt → Build → Test → Repeat               │
│  STEP 7  Maintain: rules.md, changelog.md, update KB         │
│  STEP 8  Precision editing: file tagging + Visual Editor     │
│  STEP 9  Share → Publish → Deploy                           │
└──────────────────────────────────────────────────────────────┘
```

---

## Step 4 — Build Central Source of Truth (~5 min)

**Goal:** Upload your docs and create `tasks.md` — your sequenced build list.

1. Create a `/docs` folder in your Lovable project's file tree
2. Upload all 4 PRD documents into `/docs`
3. Paste this prompt into Lovable's chat:

```
I've created some documents you can rely on:
- masterplan – step-by-step build guide
- implementation – step by step build guide
- design – brand and UI guide
- app-flow – product skeleton

Now, please tell me all of the following about this project and its core features:
1. Have you read and understood the product and all its core features?
2. Understand the implementation plan from start to finish?
3. Know the brand and UI guidelines?
4. Know the app-flow and product skeleton?

Also, ask me any clarifying questions you need. Then, also create tasks.md in the /docs folder as the source of truth for implementation order.
```

**✓ Done when:** `docs/tasks.md` exists in your file tree and Lovable has confirmed it understands your project.

---

## Step 5 — Configure Knowledge Base (~3 min)

**Goal:** Activate AI memory — Lovable will now read your docs before every response.

1. Go to **Lovable → Settings (top-right gear icon) → Knowledge → Manage Knowledge**
2. Paste this text exactly, then Save:

```
Before you begin ANY response, say "I'm using knowledge"

Always read project documentation in the /docs folder.
Use masterplan.md and tasks.md as the source of truth.

Every time you complete tasks, mark them done in tasks.md and tell me:
1. What was completed
2. How to test it
3. What is the next step
```

**✓ Done when:** You start a new chat and Lovable's first words are "I'm using knowledge."

---

## Step 6 — Execute Your Plan (~ongoing)

**Goal:** Build your app using the Magic Prompt as your repeating loop.

Copy this prompt and use it over and over throughout your build:

```
Read tasks.md, check which group of tasks is next on the list, read relevant documentation, complete the tasks, mark them as done, and tell me what's next.
```

**The build loop:**
1. Paste the Magic Prompt
2. Lovable builds the next task group, marks them done, tells you what's next
3. **Test everything** before moving on (preview, Supabase dashboard)
4. Works correctly → paste Magic Prompt again
5. Something broke → **Revert** (chat history → Revert button) — never try to fix forward

Repeat until `tasks.md` shows all MVP tasks complete.

---

## Step 7 — Maintain Sources of Truth (~8 min, repeat as needed)

**Goal:** Keep your documentation in sync with the evolving build.

**Run after each major phase or every ~50 prompts.**

**a) Create rules.md** — captures all project conventions:
```
Create docs/rules.md as the single source of truth for all project rules. Include recurring style patterns, component conventions, data flow and API dependencies, architectural constraints, and patterns to always/never use. Format as a scannable list of clear one-sentence rules. Append new rules as we establish them throughout the build.
```

**b) Create changelog.md** — logs all major decisions:
```
Create docs/changelog.md — a documentation-level log of every major change. Format: ## [Date] — [Description], then bullet points for what changed, why, and files affected. Always append, never overwrite.
```

**c) Update the Knowledge Base** — keeps Lovable's memory current:
```
Review the current project state and generate an updated Knowledge Base entry for Lovable's settings panel (under 2000 words). Include: project identity, current design tokens (Tailwind), component conventions, data model summary, scope boundaries, coding conventions, and the documentation instruction. Format for direct paste into Settings → Knowledge.
```
Then paste the output into **Lovable → Settings → Knowledge**.

---

## Step 8 — Master Precision Editing (~5 min)

**Goal:** Surgical control when the Magic Prompt is too broad.

**File Tagging (Code Editor):**
Tag files with `@` for precise, file-specific changes:
```
@Dashboard.tsx Update the card grid to 2 columns on md breakpoints, 3 on lg
@tailwind.config.ts Add primary: '#3B82F6' and secondary: '#10B981' to theme.extend.colors
@useAuth.ts Add an isProfileLoading state that stays true until the profile fetch resolves
```
Always specify: only modify the tagged file. Do not refactor anything else.

**Visual Editor:**
Click any element directly. Change text, colours, fonts without prompts. 1 edit per message. Use for polish.

**Screenshots → Design precision:**
Attach a current-state screenshot + a reference image:
```
[attach screenshots]
Change the hero section from [current layout] to match the reference image.
Maintain our colour system from docs/design.md. Only change the layout and visual treatment.
```

---

## Step 9 — Share & Publish (~5 min)

**Goal:** Go live.

**Pre-launch checklist:**
- [ ] All MVP tasks in `tasks.md` marked complete
- [ ] All user journeys tested in preview
- [ ] Mobile tested at 375px
- [ ] Error states verified
- [ ] Knowledge Base up to date
- [ ] changelog.md has a launch entry

**To publish:**
Click **Publish** (top-right corner) → live at `yourproject.lovable.app` in seconds.

**Custom domain:** Settings → Domains.

**Collaborate:** Share the project URL. Invite editors in Lovable settings.

---

## ⚡ Mission Complete

In ~40 minutes of focused work, you've:
- Documented your project before a line of code was written
- Given Lovable a persistent memory layer
- Built with a repeatable, reliable loop
- Maintained documentation throughout the build
- Shipped to production

**What's next?**
- Continue building with the Magic Prompt for V2 features
- Explore component libraries at 21st.dev and ReactBits
- Browse design inspiration on Dribbble and Mobbin
- Read `references/design-toolbox.md` for the full curated toolkit
