---
name: pm-toolkit
version: 2.0.0
author: Meridian
license: MIT
description: >
  A Product Manager toolkit that challenges thinking before producing documents.
  Use this skill when the user asks for help with a PM task or document, including:
  writing, reviewing, or red-teaming a PRD, product requirements, or spec; creating
  user stories or acceptance criteria; prioritizing features or roadmap items;
  defining OKRs, KPIs, or success metrics; drafting stakeholder updates or comms;
  running competitive analysis; planning discovery or user research; wireframing
  screens or flows. Also trigger on non-jargon phrasings like "I need to decide what
  to build next", "how do I explain this to leadership", or "help me figure out what
  users want". Do not trigger for general writing or engineering tasks that have no
  product-decision component.
tags:
  - product-management
  - PRD
  - pre-mortem
  - red-team
  - wireframing
  - prioritization
  - OKRs
  - user-stories
  - stakeholder-comms
  - competitive-analysis
  - discovery
  - research
compatibility:
  - claude.ai
  - claude-code
  - cursor
  - codex-cli
---

# PM Toolkit v2

**The PM skill that argues with you before it writes for you.** v2 is built on one belief: the document is cheap; the thinking is the product. Before generating anything, it stress-tests the idea — then produces the smallest artifact that lets a decision get made.

## What's new in v2

- **Complexity Triage** — no more default 10-section PRDs. Five signals (reversibility, blast radius, compliance, audience, investment) route every request to a one-pager, standard PRD, or full enterprise PRD. Most work gets a one-pager.
- **Pre-Mortem Grill** — a blocking gate before any PRD. The skill identifies the 3–4 most plausible ways *this specific idea* fails (demand, distribution, viability, timing, org politics, metric illusion…) and asks the tough questions you haven't contemplated. No answers, no document — unless you explicitly say "proceed anyway," in which case the unanswered questions become named risks in the doc.
- **PRD Red-Team mode** — paste an existing PRD and get a scorecard: demand evidence, vanity-metric check, kill criteria, unvalidated assumptions, scope sprawl — plus a verdict (Ship-ready / Needs work / Don't build) and the five hardest questions the doc doesn't answer.
- **Kill criteria and assumptions ledger** in every PRD tier.
- **Grilling across all tasks** — prioritization challenges your RICE inputs, OKRs get a vanity-metric test with counter-metrics, research guides get a leading-question scan, wireframes get "what's the one job of this screen" pushback.

## What it does

| Task | What you get |
|------|-------------|
| PRD Writing | Triaged to the right tier (one-pager → standard → enterprise), gated by a pre-mortem, with kill criteria and an assumptions ledger |
| PRD Red-Team | Scorecard + verdict on an existing PRD, and the hardest unanswered questions |
| User Stories | Sprint-ready stories with testable acceptance criteria and a cut-line challenge |
| Prioritization | RICE / MoSCoW / Impact-Effort with input grilling and a ranked recommendation |
| OKRs & Metrics | Outcome-based OKRs with vanity tests and counter-metrics |
| Stakeholder Comms | Audience-adaptive updates, one-ask discipline, escalations with recommendations |
| Competitive Analysis | Comparison tables, positioning maps, and a mandatory "so what" |
| Discovery & Research | Method selection, interview guides with bias checks, insight synthesis |
| Wireframing | Screen inventory, text wireframes, states, interaction specs |

## AI Feature PRD principles (built-in)

When the PRD involves an AI-powered feature, four principles apply:

- **Eval layer** — ground-truth set, quality threshold, and a named eval owner before launch
- **Least-privilege access** — the AI gets minimum permissions; mutations require human confirmation or are out of scope
- **Decouple LLM from repeat reads** — saved results re-serve from persistence, not a fresh LLM call
- **Design the wrongness UX** — specify what users see and do when the model is wrong

## Usage

Describe your PM task naturally. Examples:

```
Write a PRD for a notification centre feature
Red-team this PRD: [paste]
Help me prioritize these 8 features for Q3
What OKRs should my team set for activation?
Draft a stakeholder update for our delayed launch
How do I plan discovery for a feature I'm not sure users want?
```

Expect pushback before paperwork — that's the feature.

## Install

**Claude.ai:** Go to Customize → Skills → Upload skill → select `pm-toolkit.skill`

**Claude Code / CLI:**
```bash
cp -r skills/pm-toolkit ~/.claude/skills/
```

## About

Built by [Meridian] — an AI co-pilot for Product Managers.
Meridian helps PMs pressure-test ideas, write right-sized PRDs, and prioritize features in minutes.
