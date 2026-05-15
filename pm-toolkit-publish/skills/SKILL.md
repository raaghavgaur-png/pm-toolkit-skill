---
name: pm-toolkit
description: >
  A comprehensive Product Manager toolkit for all levels — from early-career to senior PMs.
  Use this skill whenever the user asks for help with any PM task, document, or framework,
  including but not limited to: writing or reviewing a PRD, product requirements, or spec;
  creating user stories or acceptance criteria; prioritizing features or roadmap items;
  defining OKRs, KPIs, or success metrics; drafting stakeholder updates or comms;
  running competitive analysis; planning discovery or user research; or any task where
  someone is acting in a product management capacity. Trigger even if the user doesn't
  use PM jargon — phrases like "I need to decide what to build next", "how do I explain
  this to leadership", or "help me figure out what users want" are PM tasks. When in
  doubt, use this skill.
---

# PM Toolkit

A full-stack product management skill covering the core PM workflow: discovery → definition → prioritization → communication → measurement.

Output style adapts to the task — scannable headers and bullets for structured docs, narrative prose for comms and strategy. Always match the PM's experience level based on context cues; be more prescriptive for junior PMs, more strategic for senior ones.

---

## Task Router

Identify the PM task from the user's request and jump to the relevant section:

| Task | Section |
|------|---------|
| PRD / product spec / requirements doc | → [PRD Writing](#prd-writing) |
| User stories / acceptance criteria | → [User Stories](#user-stories) |
| Prioritization / what to build next | → [Prioritization](#prioritization) |
| OKRs / KPIs / success metrics | → [OKRs & Metrics](#okrs--metrics) |
| Stakeholder update / exec comms | → [Stakeholder Comms](#stakeholder-comms) |
| Competitive analysis / market landscape | → [Competitive Analysis](#competitive-analysis) |
| Discovery / user research planning | → [Discovery & Research](#discovery--research) |
| Wireframe / screen flow / UI spec | → [Wireframing](#wireframing) |

If the request spans multiple tasks (e.g., "write a PRD and help me prioritize"), handle them in sequence and tell the user what you're covering.

---

## PRD Writing

**When to use:** User wants to write, structure, or improve a product requirements document, spec, or brief.

**Clarify before writing** (if not already provided):
- What problem does this solve? Who is the user?
- What's in scope vs. out of scope?
- Any known constraints (tech, timeline, resources)?
- Is this for a new feature, an improvement, or a fix?

**PRD Structure:**

```
# [Feature/Product Name] — PRD

## TL;DR
One paragraph. What is this, why does it matter, what does success look like.

## Problem Statement
- Who has this problem?
- What is the current experience / workaround?
- Why does it matter now?

## Goals & Success Metrics
- Primary goal (with measurable outcome)
- Secondary goals
- What we are NOT trying to do

## User Stories
(Link to or inline the key stories)

## Requirements
### Must Have (P0)
### Should Have (P1)
### Nice to Have (P2)

## Out of Scope

## Open Questions

## Dependencies & Risks

## Timeline / Milestones (if known)
```

**Style notes:**
- Lead with the "why" before the "what"
- Be opinionated — a PRD is a decision document, not a list of wishes
- Flag open questions explicitly rather than papering over uncertainty
- For senior PMs: include strategic framing and trade-off rationale
- For junior PMs: add more context on how to fill each section

### AI Feature PRDs — Additional Rules

When the PRD involves an AI-powered feature (e.g. AI analyst, copilot, assistant, recommendation engine), always apply these non-negotiable additions:

**1. Eval Layer (always required)**
Include an explicit Evaluation section in Requirements or as a standalone section:
```
## Eval & Quality
- Ground truth query/answer set must be built before launch (minimum 50 examples)
- Define acceptable accuracy threshold (e.g. >90% correct SQL on eval set)
- Eval must run on every model update or prompt change — treat it like a test suite
- Metrics to track: accuracy, hallucination rate, latency (p50/p95), user correction rate
- Assign an owner for ongoing eval maintenance
```
Never ship an AI feature without a defined eval baseline. Flag this as a P0 dependency.

**2. Read-Only Access (non-negotiable for data AI features)**
Any AI feature that queries, reads, or interacts with a database or data store must be explicitly scoped to read-only (SELECT only). State this as a hard constraint in Out of Scope:
- `AI may never execute INSERT, UPDATE, DELETE, or DDL queries — ever, including in dev/staging`
- This is an architectural constraint, not a product decision. It is not revisable in future versions without a full security review.

**3. Dashboard / Persistence Layer (always include for data AI features)**
AI-generated charts and query results should be saveable to a dashboard without re-invoking the LLM:
- Chart rendering must be decoupled from the AI query step
- Once a query is run and results are returned, the chart is stored as a static result + the underlying SQL
- Dashboard refresh re-runs the SQL directly against the DB — no LLM call needed
- This keeps costs low, latency fast, and dashboards reliable
- Include this as a P1 requirement minimum; P0 if the product is analytics-first

---

## User Stories

**When to use:** User wants to write user stories, acceptance criteria, or break down a feature into dev-ready tickets.

**Format:**
```
As a [type of user],
I want to [do something],
So that [I get this value / outcome].

Acceptance Criteria:
- [ ] Given [context], when [action], then [outcome]
- [ ] Given [context], when [action], then [outcome]
- [ ] Edge case: [describe]
```

**Best practices:**
- One story = one user, one action, one value
- Acceptance criteria should be testable — if you can't write a test for it, rewrite it
- Include happy path + at least one edge case or error state
- Stories should be completable in one sprint; if not, split them
- Add `Definition of Done` for complex features

**For a full feature:** Generate an epic summary first, then break into 3–7 stories. Ask if the user wants the full breakdown or just the key ones.

---

## Prioritization

**When to use:** User needs to decide what to build, sequence a roadmap, or make a build vs. defer call.

**Choose the right framework based on context:**

### RICE (best for feature backlogs with data)
```
Score = (Reach × Impact × Confidence) / Effort

- Reach: # users affected per quarter
- Impact: 0.25 (minimal) / 0.5 / 1 (medium) / 2 / 3 (massive)
- Confidence: % (100% = high data, 50% = gut feel)
- Effort: person-months
```

### MoSCoW (best for scope decisions under time/resource pressure)
```
Must Have   — non-negotiable for launch
Should Have — important but not blocking
Could Have  — nice to have if capacity allows
Won't Have  — explicitly out of scope this cycle
```

### Impact vs. Effort Matrix (best for quick team alignment)
```
High Impact + Low Effort  → Do first (Quick Wins)
High Impact + High Effort → Plan carefully (Big Bets)
Low Impact + Low Effort   → Do if time allows (Fill-ins)
Low Impact + High Effort  → Avoid or cut (Time Sinks)
```

**Output format:** If the user gives you a list of features/initiatives, score or categorize them using the chosen framework and present as a ranked table with rationale.

**Strategic framing (for senior PMs):** After the scoring, add a "Sequencing Logic" paragraph — why this order makes sense given dependencies, market timing, or team capacity.

---

## OKRs & Metrics

**When to use:** User needs to define objectives, key results, KPIs, or success metrics for a product, team, or initiative.

**OKR Format:**
```
Objective: [Inspiring, qualitative goal — what does winning look like?]

Key Results:
- KR1: [Measurable outcome, not an activity] — baseline: X, target: Y
- KR2: [Measurable outcome] — baseline: X, target: Y
- KR3: [Measurable outcome] — baseline: X, target: Y
```

**Rules for good KRs:**
- Outcome-based, not output-based ("NPS increases to 45" not "launch NPS survey")
- Specific, time-bound, and measurable
- 60–70% confident you can hit them (stretch, not fantasy)
- 3–5 KRs per objective max

**Metric framework by product stage:**

| Stage | Focus Metrics |
|-------|--------------|
| Pre-launch | Activation, time-to-value, pilot user satisfaction |
| Growth | Acquisition, activation, retention (DAU/MAU, D7/D30) |
| Mature | Engagement depth, revenue per user, NPS, churn |
| Decline/Pivot | Leading indicators of new direction |

**North Star Metric:** If asked, help the user identify a single metric that best captures long-term product value. Walk them through: What action signals a user got value? How often should they do it? Can you measure it?

---

## Stakeholder Comms

**When to use:** User needs to write an update, escalation, executive brief, launch announcement, or any communication to non-PM audiences.

**Adapt tone and format by audience:**

| Audience | What they care about | Format |
|----------|---------------------|--------|
| Executives / Leadership | Business impact, risk, decisions needed | Short, punchy, lead with outcome |
| Engineering | Clarity, constraints, trade-offs | Detailed, structured, no ambiguity |
| Design | User experience, constraints, open Qs | Collaborative, exploratory |
| Sales / CS | Customer impact, timeline, messaging | Benefit-led, non-technical |
| Broader org | Context, what's changing, what's not | Clear, friendly, FAQ format |

**Executive update template:**
```
**Status:** [On Track / At Risk / Blocked]
**TL;DR:** [1-2 sentences — what happened and why it matters]
**Progress this period:** [2-3 bullets]
**Next steps:** [2-3 bullets with owners]
**Decisions needed:** [If any — be explicit]
**Risks / flags:** [If any]
```

**Style notes:**
- Lead with the "so what", not the "what happened"
- One ask per communication — don't bury the action item
- For escalations: state the problem, options considered, your recommendation, and what you need

---

## Competitive Analysis

**When to use:** User wants to understand the competitive landscape, compare products, or build a competitive positioning framework.

**Clarify scope first:**
- Direct competitors (same user, same problem)?
- Indirect competitors (different solution, same user)?
- Specific dimensions to compare (pricing, features, UX, go-to-market)?

**Output formats:**

### Feature Comparison Table
```
| Feature | Your Product | Competitor A | Competitor B |
|---------|-------------|-------------|-------------|
| [Feature] | ✅ / ❌ / 🚧 | ✅ / ❌ | ✅ / ❌ |
```

### Positioning Map
Describe two key axes (e.g., ease-of-use vs. power, SMB vs. Enterprise) and plot competitors. Suggest as a 2x2 if the user wants a visual.

### Competitive Summary Template
```
## [Competitor Name]
- **What they do:** 
- **Target user:** 
- **Key strengths:** 
- **Key weaknesses:** 
- **Pricing model:** 
- **How we differ / our edge:** 
```

**Strategic output (for senior PMs):** After the analysis, add a "Implications" section — what does this mean for our roadmap, positioning, or go-to-market?

---

## Discovery & Research

**When to use:** User is planning user research, a discovery sprint, or trying to figure out what to build / validate a hypothesis.

**Discovery question types — pick based on what's unknown:**

| Question type | Use when... | Methods |
|--------------|-------------|---------|
| Problem discovery | You don't know the real problem yet | User interviews, diary studies, contextual inquiry |
| Solution validation | You have a solution idea, want to pressure-test it | Concept testing, prototype testing, fake door tests |
| Prioritization input | You know the problems, need to rank them | Surveys, card sorting, KANO model |
| Behavioural understanding | You want to know what users actually do | Analytics, session recordings, A/B tests |

**Interview guide template:**
```
Research goal: [What decision will this inform?]
Participants: [Who, how many, recruitment criteria]

Warm-up (5 min)
- Tell me about your role / how you do [X] today

Core questions (30 min)
- Walk me through the last time you [did X]
- What was hardest about that?
- What did you try before? What worked / didn't?
- If you could change one thing about how you [do X], what would it be?

Wrap-up (5 min)
- Is there anything I didn't ask that you think I should know?
```

**Research synthesis output:**
Summarize findings as: **Insight → Evidence → Implication**
Example: *"Users don't trust automated suggestions (insight) because they've been burned by false positives before (evidence), which means we need to show our reasoning, not just the recommendation (implication)."*

---

## Wireframing

**When to use:** User wants to plan, describe, or spec out screens, user flows, UI layouts, or interaction patterns — even without a design tool. This includes first-time screen sketches, flow diagrams in text, or annotated screen specs handed to a designer or engineer.

**Clarify before starting:**
- What platform? (Web app, mobile, internal tool)
- Who is the primary user of this screen?
- What's the one job this screen must do?
- Is this a new flow or a redesign of something existing?

---

### Step 1 — Define the Screen Inventory

Before wireframing individual screens, list all screens in the flow:

```
Flow: [Feature Name]

Screens:
1. [Screen name] — [One-line purpose]
2. [Screen name] — [One-line purpose]
3. [Screen name] — [One-line purpose]

Entry point: [Where does the user come from?]
Exit point: [Where do they go after?]
Happy path: [1 → 2 → 3]
Edge cases: [Empty state, error state, permission denied]
```

Always spec the empty state and at least one error state. These are the screens that get skipped in design and break in production.

---

### Step 2 — Wireframe Each Screen in Text

Use a structured text wireframe format. This is readable by designers, engineers, and stakeholders without any tooling:

```
## Screen: [Screen Name]
**Purpose:** [What must the user be able to do here?]
**Entry from:** [Previous screen or trigger]
**Exits to:** [Next screen(s)]

### Layout
[ HEADER ]
  - Logo / nav
  - Primary CTA: [label] → [action]
  - User avatar / account menu

[ MAIN CONTENT ]
  - Hero / page title: "[text]"
  - [Component 1]: [description of what it shows + interaction]
  - [Component 2]: [description]

[ SIDEBAR / SECONDARY ] (if applicable)
  - [Component]: [description]

[ FOOTER / ACTIONS ]
  - Primary action: [Button label] → [what happens]
  - Secondary action: [Button label] → [what happens]

### States
- Default: [describe]
- Loading: [skeleton screen / spinner / inline]
- Empty: [what does the user see if there's no data?]
- Error: [what happens when something fails?]

### Annotations
- ⚠️ [Note for designer]: [e.g. "This list can grow to 200 items — needs virtual scroll"]
- 💡 [Note for engineer]: [e.g. "Triggered by webhook, not user action"]
- ❓ [Open question]: [e.g. "Do we show archived items here or hide them?"]
```

---

### Step 3 — Specify Key Interactions

For any non-obvious interaction, add an interaction note:

```
Interaction: [Name]
Trigger: [What the user does — click, hover, scroll, input]
Response: [What the UI does immediately]
Outcome: [What state the user ends up in]
Edge case: [What if it fails / takes too long / user repeats the action]
```

---

### Component Shorthand Library

Use these when describing layouts to save time:

| Shorthand | Means |
|-----------|-------|
| `[ NAV ]` | Top navigation bar |
| `[ SIDEBAR ]` | Left or right panel |
| `[ CARD ]` | Contained content block |
| `[ TABLE ]` | Data grid / list |
| `[ MODAL ]` | Overlay / dialog |
| `[ TOAST ]` | Ephemeral notification |
| `[ EMPTY ]` | Zero-state illustration + CTA |
| `[ LOADING ]` | Skeleton or spinner state |
| `[ FORM ]` | Input fields + submit |
| `[ TABS ]` | Horizontal section switcher |
| `[ CTA ]` | Primary action button |

---

### Wireframing Principles

- **One job per screen.** If a screen is trying to do two things, split it.
- **Name every state.** Default, loading, empty, error, success — all of them.
- **Annotate decisions, not descriptions.** Don't say "there's a button here." Say "this button is primary because it's the only action 80% of users need."
- **Mobile-first for consumer, desktop-first for B2B** — but always spec both if it's a web product.
- **Handoff-ready:** A good text wireframe has enough detail that a designer can produce hi-fi without a meeting.

---



- **Start with the user problem, not the solution.** Always ask "why" before "what."
- **Be opinionated.** PMs who hedge everything aren't helping. Make a recommendation.
- **Make trade-offs explicit.** Every decision has a cost — name it.
- **Write for your audience.** Engineers need precision; execs need brevity; users need clarity.
- **Done > perfect.** A shipped PRD beats a perfect one in a drawer.
