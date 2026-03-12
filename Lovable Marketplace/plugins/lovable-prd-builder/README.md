# Lovable PRD Builder Plugin

The complete Lovable.dev build system — from idea to published app.

Built by [Agent Builder Academy](https://github.com/jon-aiken).

---

## What This Plugin Does

Lovable.dev has no persistent memory. Without structured documentation, your AI vision drifts, credits get wasted, and every session starts from scratch. This plugin solves that with a **Documentation-First** approach that gives Lovable a memory layer.

Two skills cover the full 9-step workflow:

| Skill | Steps | What it does |
|-------|-------|--------------|
| `lovable-prd-builder` | 1–3 | Runs a discovery interview and generates 4 structured PRD documents optimised for Lovable's stack |
| `lovable-build-guide` | 4–9 | Walks you through uploading docs, configuring the Knowledge Base, running the Magic Prompt build loop, and deploying |

---

## Installation

Install via the Claude plugin manager, or load locally for development:

```bash
claude --plugin-dir ./lovable-prd-builder
```

---

## Commands

| Command | What it triggers |
|---------|-----------------|
| `/lovable-prd-builder:build-prd` | Starts the PRD Builder skill — discovery interview → 4 documents |
| `/lovable-prd-builder:lovable-guide` | Starts the Build Guide skill — Steps 4–9 with copy-ready prompts |

---

## Skills

### `lovable-prd-builder` — Steps 1–3

Runs a structured discovery interview, then generates four documents ready to upload to Lovable:

- **Masterplan** — vision, problem, target audience, core features, data model, roadmap
- **Implementation Plan** — 7-phase build sequence with tasks.md for AI sequencing
- **Design Guidelines** — colour system, typography, spacing, component conventions
- **App Flow** — routes, roles, components, RLS policies, user journeys

Tailored for Lovable's fixed stack: React 18 + Vite + TypeScript + Tailwind CSS + shadcn/ui + Supabase.

### `lovable-build-guide` — Steps 4–9

Covers everything after your PRDs are ready:

- **Step 4** — Upload docs and create the Central Source of Truth
- **Step 5** — Configure Lovable's Knowledge Base for persistent AI memory
- **Step 6** — Run the Magic Prompt build loop
- **Step 7** — Maintain rules.md, changelog.md, and documentation centre
- **Step 8** — Master precision editing with file tagging and screenshots
- **Step 9** — Pre-launch checklist, publish, custom domain

All prompts are copy-ready — no guesswork.

---

## Reference Files

The plugin includes a curated reference library:

- `prompts-library.md` — 10 copy-ready Lovable prompts for every step
- `build-execution-guide.md` — full technical detail for Steps 4–9
- `design-toolbox.md` — component libraries (21st.dev, ReactBits, Hover.dev), design inspiration, AI generation tools, community resources
- `lovable-platform.md` — Lovable tech stack, constraints, KB system, Four Ways to Build
- Four PRD templates (Masterplan, Implementation Plan, Design Guidelines, App Flow)

---

## Recommended Workflow

```
New idea → /lovable-prd-builder:build-prd → get 4 PRD docs
    ↓
Upload to Lovable → /lovable-prd-builder:lovable-guide → ship your app
```

---

## About

Built by [Agent Builder Academy](https://github.com/jon-aiken) to help founders and developers ship faster with Lovable.dev.

- **Version**: 2.0.0
- **License**: MIT
- **Support**: jonathan@agentbuilder.academy
