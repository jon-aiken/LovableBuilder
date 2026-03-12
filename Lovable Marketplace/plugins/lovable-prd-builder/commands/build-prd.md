---
description: Build a complete Lovable.dev-ready PRD knowledge base — Masterplan, Implementation Plan, Design Guidelines, and App Flow
argument-hint: "<brief project description or paste your idea>"
---

# /build-prd

Generate a complete, Lovable.dev-optimised Product Requirements Document in four structured parts, plus a condensed Knowledge Base summary ready to paste directly into Lovable's Knowledge Base settings.

## What You'll Get

```
┌─────────────────────────────────────────────────────────────────┐
│                   LOVABLE PRD BUILDER                            │
├─────────────────────────────────────────────────────────────────┤
│  OUTPUT DOCUMENTS                                                │
│  ✓ masterplan.md — Strategic foundation & data model           │
│  ✓ implementation-plan.md — Prompt-by-prompt build sequence    │
│  ✓ design-guidelines.md — Tailwind/shadcn/ui visual contract   │
│  ✓ app-flow-pages-and-roles.md — Routes, roles, components     │
│  ✓ lovable-knowledge-base.md — Paste into Lovable KB settings  │
├─────────────────────────────────────────────────────────────────┤
│  STACK (always Lovable-native)                                   │
│  React + Vite + Tailwind CSS + shadcn/ui + Supabase            │
└─────────────────────────────────────────────────────────────────┘
```

## Usage

```
/build-prd
```

Then describe your project idea, or paste an existing brief. Claude will run a short discovery interview to fill any gaps, then generate all five documents.

---

## How It Works

**Phase 1 — Discovery Interview**
Claude asks focused questions about your concept, users, scope, design direction, and technical needs. If you've already described your idea, it extracts answers automatically and only asks about gaps.

**Phase 2 — Masterplan**
Strategic foundation: what you're building, for whom, tech stack, data model, and explicit non-goals. Output: `masterplan.md`

**Phase 3 — Implementation Plan**
Prompt-sized build steps sequenced for Lovable's workflow — layout before behaviour, Supabase setup early, checkpoint strategy. Output: `implementation-plan.md`

**Phase 4 — Design Guidelines**
Visual contract mapped to Tailwind utilities and shadcn/ui components — colors as `bg-blue-500`, spacing as `p-4`, buttons as `<Button variant="outline">`. Output: `design-guidelines.md`

**Phase 5 — App Flow, Pages & Roles**
React Router routes, Supabase auth states, RLS policies, user journeys, and component hierarchy. Output: `app-flow-pages-and-roles.md`

**Phase 6 — Assemble & Deliver**
Consistency check across all docs, then a condensed Knowledge Base summary (under 2000 words). Output: `lovable-knowledge-base.md`

---

## Where Each File Goes

| File | Where It Goes |
|------|--------------|
| `lovable-knowledge-base.md` | Paste into Lovable → Settings → Knowledge Base |
| `masterplan.md` | Upload to Lovable `/docs` folder |
| `implementation-plan.md` | Upload to Lovable `/docs` folder |
| `design-guidelines.md` | Upload to Lovable `/docs` folder |
| `app-flow-pages-and-roles.md` | Upload to Lovable `/docs` folder |

---

## What Comes Next

After `/build-prd`, use **`/lovable-guide`** for the step-by-step build execution:
- Upload docs + Central Source of Truth setup (Step 4)
- Knowledge Base configuration — the AI memory layer (Step 5)
- The Magic Prompt build loop (Step 6)
- Maintaining docs throughout the build (Step 7)
- Precision editing with file tagging (Step 8)
- Publishing and deploying (Step 9)

---

## Tips

- **Be specific about non-goals.** Lovable builds whatever isn't excluded. If you don't want social login in v1, say so explicitly.
- **The Implementation Plan is your build script.** Each phase maps to a Lovable session. Work through it in order using `/lovable-guide`.
- **Paste the Knowledge Base summary first.** Before your first Lovable prompt, add `lovable-knowledge-base.md` to Settings → Knowledge Base so Lovable has full context from the start.
- **Design inspiration:** If you're not sure about visual direction, browse 21st.dev, Dribbble, or Mobbin (see `references/design-toolbox.md`) before the interview.
