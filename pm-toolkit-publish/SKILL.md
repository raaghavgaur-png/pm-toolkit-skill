---
name: pm-toolkit
version: 1.0.0
author: Meridian
license: MIT
description: >
  A comprehensive Product Manager toolkit for all levels — from early-career to senior PMs.
  Use this skill whenever the user asks for help with any PM task, document, or framework,
  including but not limited to: writing or reviewing a PRD, product requirements, or spec;
  creating user stories or acceptance criteria; prioritizing features or roadmap items;
  defining OKRs, KPIs, or success metrics; drafting stakeholder updates or comms;
  running competitive analysis; planning discovery or user research; wireframing screens
  or user flows; or any task where someone is acting in a product management capacity.
  Trigger even if the user doesn't use PM jargon — phrases like "I need to decide what
  to build next", "how do I explain this to leadership", or "help me figure out what
  users want" are PM tasks. When in doubt, use this skill.
tags:
  - product-management
  - PRD
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

# PM Toolkit

**The complete Product Manager skill.** Covers the full PM workflow from discovery to
communication — with battle-tested templates, frameworks, and AI-specific rules baked in.

## What it does

| Task | What you get |
|------|-------------|
| PRD Writing | Full PRD with TL;DR, problem statement, requirements, risks, open questions |
| User Stories | Epics broken into sprint-ready stories with testable acceptance criteria |
| Prioritization | RICE scoring, MoSCoW, or Impact/Effort matrix with ranked output |
| OKRs & Metrics | Outcome-based OKRs, north star metric, metric framework by product stage |
| Stakeholder Comms | Audience-adaptive updates, escalations, exec briefs |
| Competitive Analysis | Feature comparison tables, positioning maps, strategic implications |
| Discovery & Research | Interview guides, research synthesis, method selection by question type |
| Wireframing | Screen inventory, text wireframes, interaction specs, annotation system |

## AI Feature PRD rules (built-in)

When the PRD involves an AI-powered feature, the skill automatically applies three
non-negotiable rules:

- **Eval layer** — ground truth set, accuracy threshold, and eval ownership required before launch
- **Read-only access** — AI may never execute INSERT, UPDATE, DELETE, or DDL queries, ever
- **Dashboard persistence** — chart refresh re-runs SQL directly; no LLM call needed

## Usage

Just describe your PM task naturally. Examples that trigger this skill:

```
Write a PRD for a notification centre feature
Help me prioritize these 8 features for Q3
Write user stories for our onboarding flow
What OKRs should my team set for activation?
Draft a stakeholder update for our delayed launch
Wireframe the AI data analyst feature
How do I plan discovery for a feature I'm not sure users want?
```

## Install

**Claude.ai:** Go to Customize → Skills → Upload skill → select `pm-toolkit.skill`

**Claude Code / CLI:**
```bash
cp -r skills/pm-toolkit ~/.claude/skills/
```

## About

Built by [Meridian](https://meridian.ai) — an AI co-pilot for Product Managers.
Meridian helps PMs write PRDs, generate wireframes, and prioritize features in minutes.
