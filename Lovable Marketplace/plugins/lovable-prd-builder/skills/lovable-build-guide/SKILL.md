---
name: lovable-build-guide
description: >
  Walk step-by-step through the Lovable.dev build execution workflow — from uploaded PRDs to published app.
  Covers Steps 4–9 of the 9-step fast track: Central Source of Truth, Knowledge Base configuration,
  the Magic Prompt build loop, maintaining sources of truth, precision editing, and deployment.
  Provides copy-ready Lovable prompts at every step.
  Use this skill when someone says "I have my PRDs, what's next?", "help me build with Lovable",
  "set up my Lovable project", "configure Knowledge Base", "how do I execute my build",
  "what's the Magic Prompt", "help me maintain my Lovable docs", or "how do I deploy with Lovable".
  This skill covers Steps 4–9 of the 9-step fast track workflow.
---

# Lovable Build Guide (Steps 4–9)

Walk the user through the post-PRD execution workflow — from uploaded documentation to a live, published app. Each step includes exact copy-ready prompts from `references/prompts-library.md`.

## Before Starting

Read `references/build-execution-guide.md` for the full technical detail on each step.
Read `references/prompts-library.md` for all copy-ready prompts.
Read `references/lovable-platform.md` for context on build modes and Lovable constraints.

## Starting Point Check

Before beginning, confirm what the user has:

1. **PRD documents ready?** — They should have `masterplan.md`, `implementation-plan.md`, `design-guidelines.md`, and `app-flow-pages-and-roles.md` from the `lovable-prd-builder` skill. If not, use that skill first.
2. **Lovable project created?** — They should have a new project at lovable.dev.
3. **Supabase project ready?** (if their app needs a database) — Project URL and anon key available.

If any are missing, help the user get them before proceeding.

## Step-by-Step Workflow

Work through these steps **sequentially**. At each step:
- Explain what the step accomplishes
- Provide the exact prompt or instruction (from `references/prompts-library.md`)
- Tell the user what to verify before moving on
- Offer to help if they get stuck

### Step 4 — Build Central Source of Truth

**What it accomplishes:** Uploads your PRDs to Lovable and orients the AI to treat them as the project's source of truth. Creates `tasks.md` — the sequenced build list you'll use throughout the project.

**Instructions to give the user:**

1. In your Lovable project, create a `/docs` folder (use the file tree panel on the left)
2. Upload all 4 PRD documents into `/docs`
3. Paste the following prompt into Lovable's chat:

**Prompt to copy (Prompt 2 from prompts-library.md):**
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

**Verify:** Lovable confirms it has read all 4 documents. A `docs/tasks.md` file appears in the file tree with your build sequence.

---

### Step 5 — Configure Knowledge Base

**What it accomplishes:** Tells Lovable to read your documentation before every response, maintaining consistency across all future sessions.

**Instructions to give the user:**

1. Go to **Lovable → Settings (top-right) → Knowledge → Manage Knowledge**
2. Paste this text exactly:

**Text to copy (Prompt 3 from prompts-library.md):**
```
Before you begin ANY response, say "I'm using knowledge"

Always read project documentation in the /docs folder.
Use masterplan.md and tasks.md as the source of truth.

Every time you complete tasks, mark them done in tasks.md and tell me:
1. What was completed
2. How to test it
3. What is the next step
```

3. Save the Knowledge Base settings

**Verify:** Start a new chat in Lovable. The AI's first words should be "I'm using knowledge." If they are, your Knowledge Base is working.

**Why this matters:** Without this configuration, Lovable might forget your documentation between sessions. This is what turns Lovable from a generic AI into *your* project-specific AI.

---

### Step 6 — Execute Your Plan (The Build Loop)

**What it accomplishes:** You begin the actual build using the Magic Prompt as your repeating loop.

**Instructions to give the user:**

This is your core build pattern. Use this prompt to start — and repeat it after every successful step:

**The Magic Prompt (Prompt 4 from prompts-library.md):**
```
Read tasks.md, check which group of tasks is next on the list, read relevant documentation, complete the tasks, mark them as done, and tell me what's next.
```

**The Build Loop:**
1. Paste the Magic Prompt
2. Lovable reads `tasks.md`, builds the next task group, marks them done, tells you what's next
3. **Test what was just built** — click through in the preview, check Supabase dashboard if needed
4. If it works: paste the Magic Prompt again for the next group
5. If it breaks: use Lovable's **Revert** button (in the chat history) — don't try to fix forward

**Revert is your safety net.** After each task group, test and verify before moving on. Lovable's revert is cheaper than debugging loops.

**How long will the build take?** For a typical MVP:
- Foundation + Auth: ~30-60 min
- Page layouts: ~30-60 min
- Data layer: ~30-60 min
- Core behaviour: ~30-60 min
- Polish + deploy: ~20-40 min
- **Total: 2.5–4.5 hours of focused sessions**

---

### Step 7 — Maintain Sources of Truth

**What it accomplishes:** Keeps your documentation current as the build evolves, preventing context drift over long builds.

**When to do this:** After each major phase, before bringing on a collaborator, or whenever you make an architectural decision.

**Four maintenance actions — provide prompts for each as needed:**

**a) Project Rules** (Prompt 5 from prompts-library.md):
Create `docs/rules.md` to record all project constraints, coding conventions, and architectural decisions. This file grows throughout the build.

**b) Changelog** (Prompt 6 from prompts-library.md):
Create `docs/changelog.md` to log every significant architectural or feature decision. Always append — never overwrite.

**c) Documentation Centre** (Prompt 7 from prompts-library.md):
Generate comprehensive project docs from the current codebase. Run this after each major phase.

**d) Update Knowledge Base** (Prompt 8 from prompts-library.md):
Generate an updated Knowledge Base entry reflecting the project's current state. Paste the output into Lovable Settings → Knowledge. Run this every ~50 prompts or after major changes.

---

### Step 8 — Master Precision Editing

**What it accomplishes:** Gives you surgical control for precise changes that the Magic Prompt is too broad for.

**Two techniques:**

**Code Editor with File Tagging:**
In Lovable's Code Editor, type `@` followed by a filename to tag it directly:
```
@Dashboard.tsx Update the stats cards to show a loading skeleton while data fetches
@tailwind.config.ts Add these brand colour tokens: primary: #[hex], secondary: #[hex]
@useAuth.ts Add an isLoading state that stays true until the profile query resolves
```
Rules: be specific about what to change, tell Lovable to only modify the tagged file.

**Visual Editor:**
Click any element directly to edit text, colours, and fonts — no prompts needed. 1 change per message. Best used for polish after functionality is complete.

**Screenshots and Design References:**
Attach images directly to prompts for visual changes:
- Screenshot the current state + a reference image for the desired state
- "Change from [current] to [desired]. Follow docs/design.md."
- Generate visuals with Aura.build or Midjourney → import as visual specifications
- See `references/design-toolbox.md` for the full AI generation workflow

---

### Step 9 — Share & Publish

**What it accomplishes:** Your app goes live.

**Instructions to give the user:**

**Before publishing, run through this checklist:**
- [ ] All MVP tasks in `tasks.md` are marked complete
- [ ] Test all user journeys (signup → core feature → edge cases)
- [ ] Tested on mobile (375px) and tablet (768px)
- [ ] Error states work gracefully
- [ ] Knowledge Base is current
- [ ] `docs/changelog.md` has a launch entry

**To publish:**
1. Click **Publish** in the top-right corner of the Lovable editor
2. Your app is live at `yourproject.lovable.app` within seconds
3. (Optional) Add a custom domain: **Settings → Domains**

**To collaborate:**
- Share the project URL with team members
- They can view the live preview and comment
- For coding collaboration, invite them as editors in Lovable settings

**Mission complete!** The user has gone from idea to published app. Point them to `references/design-toolbox.md` for community resources, design inspiration, and recommended reading to keep levelling up.

---

## Handling Common Questions During the Build

**"Lovable isn't responding with 'I'm using knowledge'"**
→ The Knowledge Base isn't configured correctly. Go back to Step 5 and re-paste the configuration text.

**"The Magic Prompt keeps doing the wrong things"**
→ Check `tasks.md` — it may need cleanup. Review the task grouping and sequencing. Use the Central Source of Truth prompt again to re-orient Lovable.

**"Something broke and I can't figure out why"**
→ Revert to the last working state (Lovable chat history → Revert button). Never try to debug forward in Lovable — it compounds errors.

**"Lovable is ignoring my design guidelines"**
→ Ensure `docs/design.md` exists and is referenced in the Knowledge Base. Add a condensed design token summary directly to the Knowledge Base text.

**"I've done 50+ prompts and quality seems worse"**
→ Context ceiling hit. Start a fresh chat session. The Magic Prompt will re-read your docs and pick up where you left off.

**"I want to add a new feature after launch"**
→ Update `tasks.md` with the new feature tasks. Then use the Magic Prompt as usual. Update your PRDs first if it's a significant feature.

---

## Summary: The Core Workflow in 5 Lines

```
1. Upload docs → Central Source of Truth prompt → tasks.md created
2. Paste KB config → Lovable says "I'm using knowledge" ✓
3. Magic Prompt → Build → Test → Repeat
4. Maintain: rules.md, changelog.md, update KB every ~50 prompts
5. Publish when tasks.md is complete ✓
```
