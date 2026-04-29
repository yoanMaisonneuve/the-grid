# The Grid

> *The living intelligence network for civilizational direction.*

A community platform for visionaries built on the [Global Plan](../ISL/GLOBAL-PLAN.md) —
14 fields, 4 phases, one shared map, one publication engine.

---

## What It Is

The Grid is not Reddit. Not Discord. Not Substack.

It is a **spatial intelligence network** — navigated in 3D, organized by field, powered by AI agents,
and connected to a weekly publication channel with real-world impact.

```
You navigate the 14 fields of the civilizational transition.
You contribute an observation in the field you know.
An agent transforms it into a structured Forsight.
The best ones reach 5,000 subscribers and the Institut St-Laurent.
Your name is on the work.
```

---

## The 14 Sectors

Each sector is one of the 14 fields from the Global Plan:

| Sector | Phase (Apr 2026) | Current Focus |
|--------|-----------------|---------------|
| Human-AI Collaboration | Disruption — Early | Context quality bottleneck |
| Humanoid Robotics | Emergence — Late | Cost + safety certification |
| Energy | Disruption — Mid | Grid infrastructure |
| Education | Emergence — Late | AI literacy gap |
| Health | Emergence → Disruption | Regulatory speed |
| Economy | Disruption — Early | Job transformation mapping |
| Pollution & Environment | Disruption — Mid | Carbon removal cost |
| Peace & Conflict | Disruption — Mid | Autonomous weapons race |
| Cities | Emergence — Mid | Housing supply |
| Governance | Emergence — Early | Regulatory lag |
| Companies & Organizations | Disruption — Early | SME adoption gap |
| People & Individuals | Emergence — Early | AI literacy gap |
| Food & Agriculture | Emergence — Mid | Climate impact on yields |
| Mental Health | Disruption — Mid | Therapist shortage |

---

## How It Works

**For members:**
1. Choose your fields of interest
2. Navigate the 3D map — see what's active, what's changing
3. Contribute an observation (voice or text)
4. The Forsight Agent structures it into a publishable insight
5. Review → publish → appear in the weekly newsletter

**For the AI agents:**
- **Forsight Agent**: raw observation → structured insight
- **Sector Agent**: weekly synthesis per field + open questions for the community
- **Curator Agent**: selects top 3 Forsights for the newsletter each Friday

**For the newsletter:**
- Weekly — every Monday
- Top 3 Forsights from the community
- One highlight per active sector
- One signal to watch
- Byline: collective + Institut St-Laurent

---

## Architecture

```
3D Navigation (Three.js)
        ↕
14 Sectors (Global Plan fields)
        ↕
Memory (Supabase — fields, forsights, members, discussions)
        ↕
Publication (Newsletter + LinkedIn + ISL)
```

Full technical docs: [architecture/](./architecture/)

---

## Stack

- **Frontend**: Three.js (3D navigation) + vanilla JS
- **Database**: Supabase (PostgreSQL + realtime)
- **Auth**: Magic link (Supabase Auth)
- **Agents**: Claude API
- **Publication**: Resend (newsletter) + LinkedIn API
- **Design**: Institut St-Laurent design language

---

## Intellectual Foundation

Built on:
- **[GLOBAL-PLAN](../ISL/GLOBAL-PLAN.md)** — the civilizational map
- **[Institut St-Laurent](../ISL/)** — the institutional framework
- **[Forsight corpus](../Forsight/)** — the insight pattern examples
- **[Enter-Game](../Enter-Game/)** — the individual adoption protocol

---

*The Grid · 2026 · Yoan Maisonneuve · Institut St-Laurent*
*"You don't manage a revolution. You direct it."*
