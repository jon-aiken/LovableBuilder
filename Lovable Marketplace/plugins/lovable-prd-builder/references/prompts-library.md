# Lovable Prompts Library

This file contains copy-ready prompts for every stage of the Lovable build workflow. Use these verbatim — they have been refined for Lovable's context window and behaviour.

---

## Prompt 1 — PRD Generation Prompt

Use this prompt inside Lovable (or with Claude) to generate your full PRD knowledge base from an existing project description. Paste your project context, then append this prompt:

```
Based on what you know about this project, create a comprehensive set of PRDs (Product Requirement Documents) that will serve as priority context.

Create these 4 documents inside the /docs folder:

1. "masterplan.md" – The product's North Star
   - Define the vision and core purpose
   - Identify/target users and their needs
   - Outline the primary value proposition
   - Establish success metrics and end goals

2. "implementation.md" – Step-by-step build guide
   - Break down the technical architecture
   - Define database schema and data models
   - List core features and their implementation
   - Cover a phased rollout plan

3. "design.md" – Brand and UI guidelines
   - Establish visual style and design principles
   - Specify component behaviour and accessibility
   - Document any branding requirements

4. "app-flow.md" – The product's skeleton
   - Map out primary user journeys
   - Define screen-by-screen flows
   - Document navigation and state transitions
   - Cover edge cases and error states

Each document should be detailed enough that any developer could pick up the project and understand exactly what to build.
```

---

## Prompt 2 — Central Source of Truth (Step 4)

After uploading your PRD docs to Lovable's `/docs` folder, use this prompt to orient Lovable to your documentation. This establishes your docs as the project's source of truth for the entire build:

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

---

## Prompt 3 — Knowledge Base Configuration (Step 5)

This is the exact text to paste into **Lovable → Settings → Knowledge → Manage Knowledge**. It tells Lovable to always reference your documentation before responding.

```
Before you begin ANY response, say "I'm using knowledge"

Always read project documentation in the /docs folder.
Use masterplan.md and tasks.md as the source of truth.

Every time you complete tasks, mark them done in tasks.md and tell me:
1. What was completed
2. How to test it
3. What is the next step
```

**Why this step is critical:** Without this configuration, Lovable might forget to check your documentation. By adding these instructions to the Knowledge Base, you ensure the AI always references your source of truth — keeping every feature, every decision aligned with your documentation.

---

## Prompt 4 — The Magic Prompt (Step 6)

This is the core execution prompt. Use it repeatedly throughout your build. It tells Lovable to read your tasks, pick up the next group of work, complete it, and report back — simple, repeatable, effective.

```
Read tasks.md, check which group of tasks is next on the list, read relevant documentation, complete the tasks, mark them as done, and tell me what's next.
```

Use this prompt over and over as your build loop. Each time it:
1. Reads `tasks.md` to find what's next
2. Reads the relevant documentation for that task group
3. Completes the tasks
4. Marks them done in `tasks.md`
5. Reports what it built and what comes next

---

## Prompt 5 — Project Rules File (Step 7)

Create a `docs/rules.md` file as a single place to record all project constraints, style patterns, data flows, and API dependencies. Use this prompt:

```
Create docs/rules.md as the single source of truth for all project rules.

Include:
- Recurring style patterns and component conventions
- Data flow and API dependencies
- Architectural constraints
- Patterns to always follow / patterns to never use
- Any decisions made that future prompts should respect

Format it as a simple, scannable list of rules. Each rule should be one clear sentence. This file grows throughout the build — append rules whenever we establish a new convention.
```

---

## Prompt 6 — Changelog (Step 7)

Create a changelog to track documentation-level changes throughout the build:

```
Create docs/changelog.md — a documentation-level log of every major change.

Format:
## [Date] — [Brief description]
- What changed
- Why it changed
- Any files affected

Append to this file whenever we make significant architectural or feature decisions. Never overwrite previous entries.
```

---

## Prompt 7 — Documentation Centre (Step 7)

Use this prompt to generate comprehensive project documentation from your existing codebase:

```
Build docs from the current state of the app in the /docs folder. Include:
- Architecture overview
- Data flows and API dependencies
- Component inventory with purpose
- Key decisions made and why
- Any known technical debt or trade-offs

This should be detailed enough for a new developer to understand the project without asking questions.
```

---

## Prompt 8 — Update Knowledge Base (Step 7)

As your project evolves, update your Knowledge Base to reflect the current state. Use this prompt to generate an updated version:

```
Review the current state of the project and generate an updated Knowledge Base entry for Lovable's settings panel.

The Knowledge Base should be under 2000 words and include:
1. Project identity (one paragraph)
2. Current design tokens (Tailwind colors, fonts, spacing)
3. Component conventions and naming patterns
4. Current data model summary (key tables and relationships)
5. Scope boundaries — what the app does NOT do
6. Coding conventions (file naming, folder structure)
7. The documentation instruction (always read /docs before responding)

Format for direct paste into Lovable → Settings → Knowledge → Manage Knowledge.
```

---

## Prompt 9 — Precision Editing with File Tagging (Step 8)

When you need Lovable to make precise changes to specific files, use `@` file tagging in Code Editor mode to give the agent exact context:

```
@[filename] Please make the following changes:
[Your specific change request]

Only modify the tagged file. Do not refactor or change any other files.
```

**Examples:**
- `@Dashboard.tsx` — Update the card grid to use 2 columns on tablet breakpoints
- `@useAuth.ts` — Add a loading state that persists until the profile fetch completes
- `@tailwind.config.ts` — Add the brand colour tokens from our design guidelines

The more specific your file context, the more precise the change. Combine with screenshots for visual changes.

---

## Prompt 10 — Screenshots & Sketches for Design (Step 8)

Lovable can process images directly. Use this pattern when making design changes:

```
[Attach screenshot of current state]
[Optionally attach a sketch or reference image]

Referring to the attached images:
- Current state: [describe what's wrong or what you want to change]
- Desired state: [describe what you want]

Apply the changes to [specific component/page]. Follow the design guidelines in docs/design.md.
```

**Pro tip:** Generate → Animate → Import. Use AI image tools (Aura.build, Midjourney) to create design references, then import them directly into your Lovable prompts as visual specifications.
