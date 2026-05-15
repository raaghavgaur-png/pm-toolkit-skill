# PM Toolkit by Meridian

> The complete Product Manager skill for Claude — covering the full PM workflow from discovery to shipping.

Built by [Meridian], an AI co-pilot for Product Managers that helps you write PRDs, generate wireframes, and prioritize features in minutes.

---

## What it does

PM Toolkit by Meridian turns Claude into a senior PM thought partner. It covers every core PM task with battle-tested templates, frameworks, and output formats — and adapts its depth to your level, whether you're an early-career PM or a seasoned CPO.

| Task | What you get |
|------|-------------|
| **PRD Writing** | Full PRD with TL;DR, problem statement, requirements (P0/P1/P2), risks, open questions |
| **User Stories** | Epics broken into sprint-ready stories with testable acceptance criteria |
| **Prioritization** | RICE scoring, MoSCoW, or Impact/Effort matrix with ranked output and sequencing rationale |
| **OKRs & Metrics** | Outcome-based OKRs, north star metric, metric framework by product stage |
| **Stakeholder Comms** | Audience-adaptive updates, escalations, and exec briefs |
| **Competitive Analysis** | Feature comparison tables, positioning maps, strategic implications |
| **Discovery & Research** | Interview guides, research synthesis, method selection by question type |
| **Wireframing** | Screen inventory, text wireframes, interaction specs, designer/engineer annotation system |

---

## AI Feature PRD rules (built-in)

When writing a PRD for any AI-powered feature, the skill automatically enforces three non-negotiable rules:

**1. Eval Layer (P0)**
Every AI feature PRD includes a mandatory evaluation section — ground truth set, accuracy threshold, hallucination rate tracking, and a named eval owner. Never ship an AI feature without a defined eval baseline.

**2. Read-Only Access (architectural constraint)**
AI may never execute `INSERT`, `UPDATE`, `DELETE`, or `DDL` queries — ever, including in dev/staging. This is an architectural constraint, not a product decision.

**3. Dashboard Persistence (decouple AI from refresh)**
AI-generated charts are saved with their underlying SQL. Dashboard refreshes re-run the SQL directly against the DB — no LLM call needed. Keeps costs low, latency fast, and dashboards reliable.

---

## Repo structure

```
pm-toolkit-skill/
└── pm-toolkit-publish/
    ├── SKILL.md          ← Submission metadata (name, tags, compatibility, usage examples)
    ├── README.md         ← This file
    ├── LICENSE           ← MIT License
    └── skills/
        └── SKILL.md     ← Full toolkit (all 8 task areas + AI feature rules)
```

---

## Install

**Claude.ai**
1. Download `pm-toolkit.skill` from [Releases](https://github.com/raaghavgaur-png/pm-toolkit-skill/releases)
2. Go to **Customize → Skills → Upload skill**
3. Select the downloaded file

**Claude Code / CLI**
```bash
cp -r pm-toolkit-publish/skills/SKILL.md ~/.claude/skills/pm-toolkit.md
```

**Cursor / Codex CLI**
```bash
cp pm-toolkit-publish/skills/SKILL.md .cursor/skills/pm-toolkit.md
```

---

## Usage

Just describe your PM task naturally — no special commands needed:

```
Write a PRD for a notification centre feature in a B2B SaaS product
Help me prioritize these 8 features for Q3
Write user stories for our onboarding flow
What OKRs should my team set for activation?
Draft a stakeholder update for our delayed launch
Wireframe the AI data analyst feature
How do I plan discovery for a feature I'm not sure users want?
I need to decide what to build next
```

---

## Compatibility

| Platform | Supported |
|----------|-----------|
| Claude.ai | ✅ |
| Claude Code | ✅ |
| Cursor | ✅ |
| Codex CLI | ✅ |
| Gemini CLI | ✅ |

---

## Contributing

Found a gap, have a framework that's saved you hours, or want to improve a template? PRs are welcome.

1. Fork the repo
2. Edit `pm-toolkit-publish/skills/SKILL.md`
3. Test with a few PM prompts
4. Open a PR with a short description of what changed and why

Please don't add frameworks for completeness — every addition should make a real PM's day faster.

---

## License

MIT — free to use, fork, and build on. See [LICENSE](./pm-toolkit-publish/LICENSE).

---

## About Meridian

[Meridian] is an AI co-pilot built specifically for Product Managers at tech companies. Write PRDs in minutes, generate wireframes from your spec, and prioritize your backlog with AI-powered RICE scoring — all in one place.

⭐ If this skill saves you time, star the repo — it helps other PMs find it.
