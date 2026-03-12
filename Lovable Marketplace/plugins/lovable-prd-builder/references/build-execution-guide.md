# Build Execution Guide — Steps 4–9

This guide covers everything that happens **after your PRDs are generated**. You have your documents — now here's how to execute your build from documentation to a published app.

Reference `prompts-library.md` for all copy-ready prompts mentioned here.

---

## Overview: The 9-Step Fast Track

The full workflow from idea to published app:

| # | Step | Time | What Happens |
|---|------|------|-------------|
| 1 | Before You Begin | ~5 min | Understanding Lovable and the AI memory problem |
| 2 | Define Your Problem | ~5 min | Craft a precise problem statement and prompt |
| 3 | Generate Your PRDs | ~10 min | Generate all 4 PRD documents with Claude |
| **4** | **Build Central Source of Truth** | **~5 min** | **Upload docs, orient Lovable, create tasks.md** |
| **5** | **Configure Knowledge Base** | **~3 min** | **Paste KB instruction into Lovable settings** |
| **6** | **Execute Your Plan** | **~5 min** | **Use the Magic Prompt to build** |
| **7** | **Maintain Sources of Truth** | **~8 min** | **rules.md, changelog.md, doc centre, update KB** |
| **8** | **Master Precision Editing** | **~5 min** | **File tagging, Visual Editor, screenshots** |
| **9** | **Share & Publish** | **~5 min** | **Collaborate with team, deploy to production** |

Steps 1–3 are covered by the `lovable-prd-builder` skill. This guide covers Steps 4–9.

---

## Step 4 — Build Central Source of Truth (~5 min)

### What Happens
Upload your PRD documents to Lovable and use the Central Source of Truth prompt to orient the AI to your documentation.

### How To Do It

1. In your Lovable project, create a `/docs` folder in the file structure
2. Upload your 4 PRD documents: `masterplan.md`, `implementation.md`, `design.md`, `app-flow.md`
3. Open the Lovable chat and paste **Prompt 2** from `prompts-library.md` (the Central Source of Truth prompt)
4. Lovable will confirm it has read your documentation and ask clarifying questions
5. It will then create `tasks.md` in `/docs` — this becomes your build sequence

### What You Get
A `tasks.md` file that organises your entire build into logical groups, sequenced for Lovable's workflow. This is your primary navigation tool for the rest of the build.

### Verify
- Lovable has confirmed it understands all 4 documents
- `docs/tasks.md` exists in the file structure
- The tasks are grouped logically (Foundation → Auth → Pages → Data → Behaviour → Polish)

---

## Step 5 — Configure Knowledge Base (~3 min)

### What Happens
Add the Knowledge Base instruction to Lovable's settings so every future prompt references your documentation.

### Why This Step Is Critical
Without this configuration, Lovable might forget to check your documentation. By adding these instructions to the Knowledge Base, you ensure the AI always references your source of truth — keeping every feature and every decision aligned with your PRDs.

### How To Do It

1. Open **Lovable → Settings → Knowledge → Manage Knowledge**
2. Paste exactly the text from **Prompt 3** in `prompts-library.md` (the Knowledge Base configuration)
3. Save

### The Knowledge Base Text (from prompts-library.md)
```
Before you begin ANY response, say "I'm using knowledge"

Always read project documentation in the /docs folder.
Use masterplan.md and tasks.md as the source of truth.

Every time you complete tasks, mark them done in tasks.md and tell me:
1. What was completed
2. How to test it
3. What is the next step
```

### Verify
- Start a new chat. Lovable should begin its response with "I'm using knowledge"
- If it does, your Knowledge Base is working correctly

---

## Step 6 — Execute Your Plan (~5 min to start, ongoing)

### What Happens
You use the Magic Prompt as your core build loop. It's simple, repeatable, and effective.

### The Magic Prompt (from prompts-library.md)
```
Read tasks.md, check which group of tasks is next on the list, read relevant documentation, complete the tasks, mark them as done, and tell me what's next.
```

### How To Use It
1. Paste the Magic Prompt into Lovable
2. Lovable reads `tasks.md`, identifies the next task group, reads relevant docs, and builds
3. After completing, it marks tasks done and tells you what's next
4. **Verify each completed group before moving on** — test in the preview, check Supabase dashboard
5. Repeat with the Magic Prompt for the next group

### The Build Loop
```
Magic Prompt → Lovable builds → You verify → Repeat
```

### Revert Strategy
Lovable's revert feature is your safety net. After each significant build step:
- Test everything that was just built
- If something breaks, revert immediately (don't try to fix forward)
- Revert is cheaper than debugging loops

---

## Step 7 — Maintain Sources of Truth (~8 min, ongoing)

As your project grows, your documentation needs to grow with it. This step covers four types of maintenance documentation.

### 7a — Project Rules (rules.md)

Use **Prompt 5** from `prompts-library.md` to create `docs/rules.md`. This file:
- Records all project constraints and architectural decisions
- Lists patterns to always follow / patterns to never use
- Grows throughout the build as new conventions are established
- Gets referenced in future prompts: `@rules.md Add this new feature following existing patterns`

### 7b — Changelog (changelog.md)

Use **Prompt 6** to create `docs/changelog.md`. This file:
- Logs every major architectural or feature decision
- Never overwrites — always appends
- Serves as a timeline of your build decisions
- Helps you understand "why did we do it this way?" months later

### 7c — Documentation Centre

Use **Prompt 7** to generate comprehensive project documentation from the current codebase. Do this:
- After completing each major phase (Foundation, Auth, Pages, etc.)
- Before bringing on a collaborator
- When you want a snapshot of the current architecture

### 7d — Update Knowledge Base

Use **Prompt 8** to generate an updated Knowledge Base entry as the project evolves. Update your Knowledge Base:
- After completing a major phase
- When design tokens or conventions change
- When scope changes materially
- At least every 50 prompts

---

## Step 8 — Master Precision Editing (~5 min)

Two tools for precise control when the Magic Prompt is too broad.

### Code Editor — File Tagging

In Lovable's Code Editor, use `@filename` to tag specific files and give the AI exact context:

```
@Dashboard.tsx Update the card grid to use 2 columns on tablet breakpoints
@useAuth.ts Add a loading state that persists until the profile fetch completes
@tailwind.config.ts Add the brand colour tokens from docs/design.md
```

**Rules for file tagging:**
- Tag only the file you want changed
- Be specific about what to change and what to preserve
- "Only modify the tagged file. Do not refactor anything else."

### Visual Editor — Direct Editing

Click any element in Lovable's Visual Editor to change text, colours, and fonts directly:
- **Best for**: Quick text changes, colour tweaks, font adjustments
- **1 edit per message** — focused and efficient
- Use for polish after functionality is complete

### Screenshots & Sketches

Attach images directly to your Lovable prompt for visual changes:
1. Screenshot the current state
2. Sketch or find a reference image for the desired state
3. Attach both to your prompt with: "Change from [current] to [desired]. Follow docs/design.md."

**Pro tip:** Use Aura.build or Midjourney to generate design references, then import them into Lovable as visual specs. See `design-toolbox.md` for the full AI generation workflow.

---

## Step 9 — Share & Publish (~5 min)

### Collaborate with Your Team

Your Lovable project has a live preview URL. Share it with team members to:
- Get feedback on features as they're built
- Allow non-technical stakeholders to view and comment
- Enable real-time collaboration

### Publish to Production

Lovable's one-click deploy publishes your app to Lovable's hosting:
1. Click **Publish** in the top-right corner
2. Your app is live at a `lovable.app` subdomain within seconds
3. (Optional) Add a custom domain in **Settings → Domains**

### Launch Checklist

Before publishing to production:
- [ ] All tasks in `tasks.md` are marked complete for your MVP scope
- [ ] Test all user journeys in the preview (signup → core feature → edge cases)
- [ ] Mobile responsiveness verified at 375px and 768px
- [ ] Error states tested (what happens when data fails to load?)
- [ ] Knowledge Base is up to date for future sessions
- [ ] `docs/changelog.md` has an entry for launch

### What's Next

After launching your MVP:
- Share your app URL with early users
- Use `tasks.md` to plan your V2 features
- Keep using the Magic Prompt for ongoing development
- Explore the Design Toolbox (`design-toolbox.md`) for component libraries and design inspiration

---

## Troubleshooting Common Issues

| Problem | Solution |
|---------|----------|
| Lovable keeps forgetting your design system | Verify Knowledge Base is set up (Step 5). Add design tokens directly to KB. |
| Build quality degrading over time | Context ceiling hit. Start a new session with the Magic Prompt — it will re-read docs. |
| Feature breaks after unrelated change | Use Revert immediately. Don't try to fix forward. |
| Lovable builds the wrong thing | Your prompt or docs are ambiguous. Revert + clarify. Add to `rules.md`. |
| Performance issues on complex pages | Break into smaller component files. Use Code Editor to split large components. |
| Supabase RLS blocking data | Check policy in Supabase dashboard. Reference your masterplan RLS definitions. |
