# PM Toolkit v2 by Meridian

> The PM skill that argues with you before it writes for you.

Built by [Meridian], an AI co-pilot for Product Managers that helps you pressure-test ideas, write right-sized PRDs, and prioritize your backlog.

---

## The v2 philosophy

AI can generate a flawless-looking PRD for a doomed idea in seconds. So the document is cheap — **the thinking is the product.** v2 stress-tests the idea first, then produces the smallest artifact that lets a decision get made. Expect pushback before paperwork; that's the feature.

Three behaviors run through every task:

1. **Right-size the artifact.** Most features get a one-pager, not a 10-section PRD. Docs have to earn their length.
2. **Grill before generating.** The skill surfaces the most likely failure causes and asks hard questions — including ones you haven't contemplated — *before* writing.
3. **Always land on a recommendation.** Including "don't build this."

---

## What's new in v2

### Complexity Triage
Before any PRD, five signals decide the document tier:

| Signal | Lightweight ← | → Heavyweight |
|--------|--------------|----------------|
| Reversibility | Easy to roll back | One-way door |
| Blast radius | One team | Multiple teams / platforms |
| Compliance | None | Security / legal / regulatory review |
| Audience | Your own team | Execs, partners, enterprise customers |
| Investment | Days–weeks | Multi-quarter |

→ **Tier 1: One-Pager** (the default) · **Tier 2: Standard PRD** (~2–3 pages) · **Tier 3: Enterprise PRD** (~5 pages, for one-way doors and regulated contexts)

### Pre-Mortem Grill (blocking gate)
Before writing, the skill assumes the product failed 12 months post-launch and identifies the 3–4 most plausible causes for *your specific idea* — across demand, distribution, viability, feasibility, timing, org politics, metric illusion, and dependencies. Then it asks 3–5 tough questions:

- *What's the cheapest experiment that could kill this idea before you build anything?*
- *Who loses if this ships?*
- *Which single assumption, if wrong, makes the whole thing pointless?*

No engagement, no document — unless you say "proceed anyway," in which case every unanswered question is written into the PRD as a named risk.

### PRD Red-Team mode
Paste an existing PRD and get a scorecard — demand evidence, vanity-metric check, kill criteria, unvalidated assumptions, scope discipline — plus a verdict (**Ship-ready / Needs work / Don't build**) and the five hardest questions the doc doesn't answer.

### Kill criteria & assumptions ledger
Every PRD tier now requires a kill condition with a date, and Tier 2+ includes an assumptions ledger: each assumption with its risk-if-wrong, confidence, and cheapest test.

---

## All task areas

| Task | What you get |
|------|-------------|
| **PRD Writing** | Triaged tier, pre-mortem-gated, kill criteria + assumptions ledger |
| **PRD Red-Team** | Scorecard, verdict, and the hardest unanswered questions |
| **User Stories** | Sprint-ready stories, testable acceptance criteria, cut-line challenge |
| **Prioritization** | RICE / MoSCoW / Impact-Effort with input grilling ("where does that Reach number come from?") |
| **OKRs & Metrics** | Outcome-based OKRs, vanity-metric test, counter-metrics |
| **Stakeholder Comms** | Audience-adaptive formats, one-ask discipline, recommendation-first escalations |
| **Competitive Analysis** | Comparison tables, positioning maps, mandatory "so what" + moat stress test |
| **Discovery & Research** | Method selection, interview guides with leading-question scan, insight synthesis |
| **Wireframing** | Screen inventory, text wireframes, all states named, interaction specs |

---

## AI Feature PRD principles (built-in)

When a PRD involves an AI-powered feature, four principles apply:

**1. Eval Layer (P0)** — ground-truth set, quality threshold, eval re-run on every model/prompt change, named owner. No eval baseline, no launch.

**2. Least-Privilege Access** — the AI component gets minimum permissions; anything that mutates data, spends money, or contacts external parties requires explicit human confirmation or is out of scope. Stated in the PRD as an architectural constraint.

**3. Decouple LLM from Repeat Reads** — saved results, dashboards, and reports persist with their underlying query and re-serve without a new LLM call. LLM calls are for generation, not retrieval.

**4. Design the Wrongness UX** — the model will be wrong; the PRD specifies what the user sees, how they correct it, and the escape hatch to a non-AI path.

---

## Repo structure

```
pm-toolkit-skill/
└── pm-toolkit-publish/
    ├── SKILL.md          ← Submission metadata (name, tags, compatibility, usage examples)
    ├── LICENSE           ← MIT License
    └── skills/
        └── SKILL.md      ← Full toolkit (triage, grill, 9 task areas, AI principles)
```

---

## Install

**Claude.ai**
1. Download `pm-toolkit.skill` from [Releases](https://github.com/raaghavgaur-png/pm-toolkit-skill/releases)
2. Go to **Customize → Skills → Upload skill**
3. Select the downloaded file

**Claude Code / CLI**
```bash
cp pm-toolkit-publish/skills/SKILL.md ~/.claude/skills/pm-toolkit.md
```

**Cursor / Codex CLI**
```bash
cp pm-toolkit-publish/skills/SKILL.md .cursor/skills/pm-toolkit.md
```

---

## Usage

Describe your PM task naturally — no special commands needed:

```
Write a PRD for a notification centre feature in a B2B SaaS product
Red-team this PRD: [paste]
Help me prioritize these 8 features for Q3
What OKRs should my team set for activation?
Draft a stakeholder update for our delayed launch
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

[Meridian] is an AI co-pilot built specifically for Product Managers at tech companies. Pressure-test ideas, write right-sized PRDs, and prioritize your backlog with AI-powered scoring — all in one place.

⭐ If this skill saves you time, star the repo — it helps other PMs find it.
