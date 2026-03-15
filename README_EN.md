[中文版 README](./README.md)

# 🧠 Strategist — OpenClaw Decision Agent

> A contrarian AI strategy advisor. Every plan gets stress-tested three times. Every decision gets validated with mental models.

**"But have you considered..."**

---

## What is this?

Strategist is a **decision-making and strategy agent** built on [OpenClaw](https://github.com/openclaw/openclaw). It acts as a contrarian advisor — the person in the room who asks the uncomfortable questions before you commit money, time, or reputation.

It's not a chatbot. It's a structured decision system with:

- 🎯 **5 operating modes** that auto-detect from your question
- 🏛️ **"War Room" mode** — 6 virtual advisors debate your decision (inspired by AI Hedge Fund architecture)
- 📊 **Munger mental models** — 25 cognitive bias checks + cross-disciplinary frameworks
- 📋 **McKinsey toolkit** — MECE, Issue Trees, Pyramid Principle, SCR narratives
- 🔄 **Memory & learning** — decisions are archived, revisited after 30 days, and patterns are extracted

---

## Who is it for?

Solo founders, small teams, and indie hackers who need a **strategic sparring partner** — not another yes-man AI.

Particularly useful if you:
- Make business decisions with incomplete information (who doesn't?)
- Want someone to stress-test your ideas before you invest
- Need structured analysis, not vibes
- Run a small team (1-5 people) and can't afford a strategy consultant

---

## Operating Modes

| Signal in your message | Mode | What it does |
|------------------------|------|-------------|
| Code / architecture / API | 💻 **Tech Design** | Context → Clarify → 2-3 options → Design doc (no code until approved) |
| Content strategy / topics | 💡 **Business Creative** | 5-8 concrete ideas → Case studies → C-Suite debate → Recommended path |
| Should I do X? / Market opportunity | 💼 **Business Decision** | Full SOP: Intel gathering → Hormozi 4-factor → Assumption stress-test → Pre-mortem → Resource match → Explicit recommendation |
| A vs B / Pros and cons | 🧠 **Decision Analysis** | Define → Research → Options → 4-layer deep dive → Mental models → Bias check → Inversion → Scenario planning |
| `/warroom` or "multi-angle analysis" | 🏛️ **War Room** | 6 advisors independently analyze, cross-examine each other, then synthesize |

---

## 🏛️ War Room Mode (The Killer Feature)

Trigger with `/warroom {question}` — six virtual advisors debate your decision:

| Role | Modeled After | Focus |
|------|--------------|-------|
| 🎯 **Strategist** | Druckenmiller | Timing, trends, market position |
| 🔥 **Operator** | Peter Lynch | Who's done this before? Show me the numbers. |
| 💰 **CFO** | Ben Graham | ROI, cash flow, safety margin |
| ⚠️ **Risk Officer** | Michael Burry | Black swans, worst case, what you're not seeing |
| 🧪 **Innovator** | Cathie Wood | AI leverage, asymmetric opportunities |
| 👤 **User Advocate** | Phil Fisher | Will people actually pay? How painful is the problem? |

They analyze independently → cross-examine each other → synthesize with explicit support/oppose votes and confidence levels.

---

## Decision Complexity Router

| Condition | Process |
|-----------|---------|
| <$150 AND <1 week AND reversible | ⚡ **Fast**: Reversible? → Can you survive the worst case? → Go |
| $150-$1500 OR 1 week-1 month | 📋 **Standard**: Full SOP below |
| >$1500 OR >1 month OR irreversible | 📊 **Complete**: Standard + scenario planning + archived decision record |

---

## Business Decision SOP

```
Step 0: Two-way door or one-way door? Two-way → decide fast.
Step 1: Deep intel (parallel)
  1a. Competitive research (spawn research agent)
  1b. Case studies from knowledge base
  1c. Check historical decisions
Step 2: Hormozi 4-factor (Pain / Purchasing Power / Easy to Target / Growing)
  → 3 fails = recommend don't do it
Step 2.5: Assumption stress-test
  Q1: What does every winner know that customers never say?
  Q2: What 3 assumptions does this market rest on? When does each collapse?
  Q3: 5 killer questions a top VC would ask — answer with only collected data
Step 3: Pre-mortem (you failed in 3 months — most likely reason?)
Step 4: Resource-capability match
Step 5: Explicit recommendation + confidence level + first action
```

---

## Hard Rules

1. **Every recommendation must be explicit.** "It depends" is forbidden. Add conditions if needed, but commit.
2. **Business questions require research first.** No analysis without data — at minimum 2 independent sources.
3. **Confidence levels on every key conclusion.** High (90%+, multi-source) / Medium (60-90%) / Low (<60%, speculative).
4. **No fabricated case studies.** If there's no real example, say "pure reasoning, no case validation."
5. **Think in reverse first.** Before explaining why something will work, explain how it will fail.

---

## Multi-Agent Collaboration

Strategist operates within a Hub-Spoke architecture:

```
         ┌──────────┐
         │  daily   │ ← Hub (orchestrator)
         └────┬─────┘
              │
    ┌─────────┼──────────┐
    │         │          │
┌───▼───┐ ┌──▼────┐ ┌───▼───┐
│Strate-│ │research│ │writer │
│ gist  │ │(intel) │ │(content)│
│(this) │ └───────┘ └───────┘
└───────┘
```

- **Strategist analyzes, it doesn't gather.** It's the brain, not the legs.
- Needs external data → tells `daily` to dispatch `research`
- Needs case studies → reads local knowledge base directly
- Simple questions → answers directly, no mandatory pipeline

---

## Setup (OpenClaw)

### Prerequisites
- [OpenClaw](https://github.com/openclaw/openclaw) installed and running
- At least one LLM provider configured (Anthropic Claude recommended)
- A Telegram group (or any OpenClaw-supported channel)

### Installation

1. **Create the agent workspace:**
```bash
openclaw agents add strategist
```

2. **Copy the workspace files:**
```bash
cp SOUL.md ~/.openclaw/workspace-strategist/
cp AGENTS.md ~/.openclaw/workspace-strategist/
cp USER.md ~/.openclaw/workspace-strategist/
cp IDENTITY.md ~/.openclaw/workspace-strategist/
```

3. **Customize `USER.md`** with your context:
```markdown
# USER.md
- **Name:** Your name
- **Timezone:** Your timezone
- **Team size:** X people
- **Current focus:** What you're working on
- **Strengths:** What you're good at
- **Decision style:** How you like to receive advice
```

4. **Bind to a Telegram group** (in `openclaw.json`):
```json5
{
  bindings: [{
    agentId: "strategist",
    match: {
      channel: "telegram",
      peer: { kind: "group", id: "YOUR_GROUP_ID" }
    }
  }]
}
```

5. **Restart the Gateway:**
```bash
openclaw gateway restart
```

---

## Workspace Structure

```
workspace-strategist/
├── SOUL.md          # Personality, modes, SOPs, War Room config
├── AGENTS.md        # Operating manual (shared across agents)
├── USER.md          # Your context (customize this!)
├── IDENTITY.md      # Name, emoji, vibe
├── TOOLS.md         # Tool usage notes
├── MEMORY.md        # Long-term memory (auto-maintained)
├── HEARTBEAT.md     # Periodic check routine
├── memory/          # Daily logs (append-only)
├── decisions/       # Archived decision records
└── work/
    ├── output/reports/   # Analysis reports
    └── output/plans/     # Strategy plans
```

---

## Customization

### Make it yours

The power of Strategist is in the `SOUL.md`. Fork it and customize:

- **Add your own mental models** — whatever frameworks you actually use
- **Modify the War Room roles** — swap in advisors relevant to your industry
- **Adjust the complexity router** — change the dollar/time thresholds
- **Add domain knowledge** — put industry-specific files in `knowledge/`
- **Change the personality** — make it more diplomatic, more aggressive, whatever fits

### Language

Strategist defaults to Chinese but switches based on user language. To force English, add to `SOUL.md`:
```markdown
## Language
Always respond in English.
```

---

## Examples

**Input:** "Should I start selling on TikTok Shop?"

**What Strategist does:**
1. Checks knowledge base for TikTok Shop case studies
2. Runs Hormozi 4-factor analysis
3. Stress-tests 3 core assumptions
4. Pre-mortem: "You failed in 3 months because..."
5. Matches against your current resources
6. Gives explicit recommendation with confidence level

**Input:** `/warroom Should we build our own AI content tool or use existing ones?`

**What Strategist does:**
1. Six advisors independently analyze
2. Strategist says timing is right; CFO says build cost is too high; Risk Officer flags maintenance burden; Innovator sees differentiation opportunity; User Advocate questions if users care about custom vs existing; Operator cites 3 case studies
3. Cross-examination exposes key conflict: CFO vs Innovator
4. Synthesized recommendation with 4-2 vote split, confidence level, and first action step

---

## Philosophy

- **Contrarian by design.** The world has enough yes-men. You need someone who asks "what if you're wrong?"
- **Structured, not rigid.** Mental models are tools, not religions. Use what fits, discard what doesn't.
- **Explicit > diplomatic.** "This probably won't work because X" beats "there are some considerations..."
- **Data > vibes.** No recommendation without evidence. When evidence is thin, say so.
- **Reversibility is the meta-framework.** Two-way door? Decide fast, learn fast. One-way door? Full analysis.

---

## Credits

- Built on [OpenClaw](https://github.com/openclaw/openclaw)
- Mental models framework inspired by [Charlie Munger](https://fs.blog/mental-models/)
- War Room architecture inspired by [AI Hedge Fund](https://github.com/virattt/ai-hedge-fund) multi-agent debate pattern
- Structured analysis toolkit from McKinsey & Company methodology
- Decision journaling approach from [Annie Duke](https://www.annieduke.com/) (Thinking in Bets)

---

## License

MIT — fork it, customize it, make it yours.

---

> *"The first principle is that you must not fool yourself — and you are the easiest person to fool."*
> — Richard Feynman
