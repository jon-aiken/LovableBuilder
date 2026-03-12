# LovableBuilder

LovableBuilder is a complete build system for [Lovable.dev](https://lovable.dev), built as a Claude plugin. It takes you from rough idea to published app using a structured, documentation-first approach that solves the biggest problem with AI-powered development: the AI has no memory.

---

## The Problem

Lovable is powerful. But every session starts from scratch.

Without structured documentation, your AI drifts from your original vision. You repeat context. You waste credits fixing things that worked fine two sessions ago. By the time you're halfway through a build, the app looks nothing like what you planned.

The solution isn't to be smarter about prompting. It's to give Lovable a memory layer — a set of structured documents that orient the AI at the start of every session, so it always knows what you're building, how it should look, and what comes next.

That's what this plugin does.

---

## How It Works

The moment you start a new project, LovableBuilder runs a discovery interview. It asks you about your idea, your users, your must-have features, and your design preferences. It doesn't rush to build anything.

From that conversation, it generates four structured documents: a **Masterplan** (your vision, problem statement, target audience, and roadmap), an **Implementation Plan** (a sequenced 7-phase build plan), **Design Guidelines** (your colour system, typography, spacing, and component conventions), and an **App Flow** (every route, role, and user journey in your app).

These documents are written specifically for Lovable's stack — React 18 + Vite + TypeScript + Tailwind CSS + shadcn/ui + Supabase — so they slot directly into Lovable's Knowledge Base without any translation.

Once your documents are ready, the second skill takes over. It walks you through uploading your docs to Lovable, configuring the Knowledge Base so the AI reads them before every prompt, and running the Magic Prompt — a repeating build loop that works through your implementation plan task by task, marks progress, and tells you what's next. By the time you're done, your app is built, documented, and ready to deploy.

Your agent just has a plan. And it never forgets it.

---

## Installation

### Claude Code

Register the marketplace:

```
/plugin marketplace add jon-aiken/LovableBuilder
```

Install the plugin:

```
/plugin install lovable-prd-builder@agent-builder-academy
```

### Verify Installation

Start a new session and say "I want to build a Lovable app" or run:

```
/lovable-prd-builder:build-prd
```

The PRD Builder skill will activate and begin the discovery interview.

---

## The Workflow

LovableBuilder covers all nine steps from idea to published app, split across two skills.

**Steps 1–3: Build Your PRDs** — triggered by `/lovable-prd-builder:build-prd`

1. **Discovery Interview** — Claude asks focused questions about your idea, users, features, and design direction. Takes about 10 minutes.
2. **Generate Documents** — Four PRD files are created, formatted for Lovable's stack and ready to upload.
3. **Review & Refine** — You review each document and confirm before moving to the build phase.

**Steps 4–9: Execute Your Build** — triggered by `/lovable-prd-builder:lovable-guide`

4. **Central Source of Truth** — Upload your PRDs to Lovable and orient the AI with a single prompt that sets the context for the entire build.
5. **Configure Knowledge Base** — Paste a configuration block into Lovable's Knowledge Base so the AI reads your docs before every single prompt.
6. **Run the Magic Prompt** — The core build loop. Claude reads `tasks.md`, identifies the next group of tasks, reads the relevant docs, completes the work, marks tasks done, and reports back. Repeat until shipped.
7. **Maintain Sources of Truth** — Create `rules.md` for coding conventions, `changelog.md` for session history, and a documentation centre that keeps your project docs accurate as the app evolves.
8. **Precision Editing** — Use `@filename` tagging in Lovable's Code Editor for targeted changes, plus screenshot-driven design feedback when the Visual Editor isn't enough.
9. **Ship It** — Pre-launch checklist, one-click publish, custom domain setup, and collaboration options.

---

## What's Inside

### Skills

**`lovable-prd-builder`** — Steps 1–3
Runs the discovery interview and generates your four PRD documents. Knows Lovable's full stack deeply: every shadcn/ui component, Supabase's auth and RLS system, Tailwind's utility-first patterns, and the documentation conventions that make Lovable's AI most effective.

**`lovable-build-guide`** — Steps 4–9
Covers everything from first upload to deployment. Provides copy-ready prompts at every step so you never have to figure out what to say to Lovable. Includes the exact Knowledge Base configuration text, the Magic Prompt build loop, maintenance workflows, and pre-launch checklist.

### Commands

| Command | What it does |
|---------|-------------|
| `/lovable-prd-builder:build-prd` | Starts the PRD builder — discovery interview then four documents |
| `/lovable-prd-builder:lovable-guide` | Starts the build execution guide — Steps 4–9 with copy-ready prompts |

### Reference Library

| File | What's in it |
|------|-------------|
| `prompts-library.md` | 10 copy-ready prompts covering every step of the workflow |
| `build-execution-guide.md` | Full technical detail for Steps 4–9 with troubleshooting |
| `design-toolbox.md` | Curated tools: component libraries, design inspiration, AI generation |
| `lovable-platform.md` | Lovable's full tech stack, KB system, and Four Ways to Build |
| `masterplan-template.md` | The Masterplan document template |
| `implementation-plan-template.md` | The 7-phase implementation plan template |
| `design-guidelines-template.md` | Design tokens, colour system, and component conventions template |
| `app-flow-template.md` | Routes, roles, RLS policies, and user journey template |

### Design Toolbox

The plugin includes a curated toolbox for when you need assets, inspiration, or components beyond what Lovable generates out of the box.

- **Component Libraries**: [21st.dev](https://21st.dev), [ReactBits](https://reactbits.dev), [Hover.dev](https://hover.dev)
- **Design Inspiration**: [Dribbble](https://dribbble.com), [Mobbin](https://mobbin.com), [LandingFolio](https://landingfolio.com)
- **AI Generation**: [Aura.build](https://aura.build) (images → components), Google Flow Veo 3 (video), Midjourney (visuals)
- **Community**: Felix Haas Prompt Directory, official Lovable docs, Lovable prompt library

---

## Philosophy

**Documentation-First** — Don't build until you've written down what you're building. PRDs aren't overhead. They're the memory layer that makes every subsequent session faster and more accurate.

**The AI Memory Problem** — Lovable resets every session. Without your docs in the Knowledge Base, it's starting blind. With them, it's starting with full context. The difference compounds over time.

**Copy-Ready, Not Vague** — Every prompt in this plugin is exact copy you can paste directly into Lovable. No "write a prompt that tells the AI to..." — just the prompt itself, ready to go.

**One Skill Hands Off to the Next** — The PRD Builder ends by pointing you to the Build Guide. The Build Guide ends when your app is live. The workflow is complete, not a collection of disconnected tools.

---

## Updating

When a new version is available:

```
/plugin update lovable-prd-builder
```

---

## Contributing

If you've found better prompts, new tools for the design toolbox, or workflow improvements from your own Lovable builds, contributions are welcome.

1. Fork this repository
2. Create a branch for your changes
3. Submit a PR with a clear description of what improved and why

---

## Support

- **Issues**: [github.com/jon-aiken/LovableBuilder/issues](https://github.com/jon-aiken/LovableBuilder/issues)
- **Contact**: jonathan@agentbuilder.academy
- **Built by**: [Agent Builder Academy](https://github.com/jon-aiken)

---

## License

MIT — see LICENSE file for details.
