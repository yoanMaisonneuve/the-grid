# CLAUDE.md — The Grid

> Système d'intelligence directionnelle vivant.
> Navigation spatiale 3D des 14 champs du GLOBAL-PLAN.
> Communauté de visionnaires + agents IA + canal de publication d'impact.

---

## QUI EST YOAN / WHO IS YOAN

Yoan Maisonneuve · Solo founder · Montréal / Lorraine QC
Email: ymaisonneuve@hotmail.com · Style : voice-first, autonomie déléguée, altruiste

---

## CE QU'EST THE GRID

**Tagline :** *The living intelligence network for civilizational direction.*

**Ce que c'est — en 3 phrases :**
The Grid est une plateforme communautaire pour visionnaires construite sur le GLOBAL-PLAN.
Les 14 champs deviennent des secteurs navigables en 3D. Les membres contribuent des observations,
les agents les transforment en Forsights, les meilleurs sont publiés chaque semaine.

**Ce que c'est PAS :** Reddit, Discord, Substack. Pas de fil chronologique. Pas de upvotes. Pas d'ego metrics.

**Ce que c'est OUI :**
- Une carte vivante de la transition civilisationnelle (GLOBAL-PLAN)
- Un réseau de contributeurs qui alimentent la carte
- Un moteur de publication d'insights directionnels (newsletter + LinkedIn + ISL)
- Un système de mémoire collective qui grandit avec chaque contribution

---

## ARCHITECTURE — 4 COUCHES

```
┌─────────────────────────────────────────────────────┐
│  COUCHE 1 : NAVIGATION 3D (Three.js)                │
│  14 nœuds · phases · activité · connexions          │
└─────────────────────────────────────────────────────┘
                        ↕
┌─────────────────────────────────────────────────────┐
│  COUCHE 2 : SECTEURS (14 champs GLOBAL-PLAN)        │
│  Phase · Bottlenecks · Forsights · Discussions       │
└─────────────────────────────────────────────────────┘
                        ↕
┌─────────────────────────────────────────────────────┐
│  COUCHE 3 : MÉMOIRE (Supabase PostgreSQL)           │
│  fields · forsights · members · discussions          │
└─────────────────────────────────────────────────────┘
                        ↕
┌─────────────────────────────────────────────────────┐
│  COUCHE 4 : PUBLICATION (Newsletter + LinkedIn)     │
│  Weekly curation · ISL byline · impact tracking     │
└─────────────────────────────────────────────────────┘
```

---

## STACK TECHNIQUE

| Composant | Technologie | Pourquoi |
|-----------|-------------|----------|
| Frontend 3D | Three.js (vanilla JS) | Comme ISL — pas de framework, contrôle total |
| Base de données | Supabase (PostgreSQL) | Realtime, auth inclus, SDK JS simple |
| Auth | Supabase Auth (magic link) | Friction zéro — email seulement |
| Agents IA | Claude API (claude-sonnet) | Forsight generation, synthesis, curation |
| Newsletter | Resend + template HTML | Simple, API directe |
| LinkedIn | LinkedIn API v2 | Publication collective |
| Hosting | Vercel ou GitHub Pages | Single-file HTML possible pour v1 |

---

## STRUCTURE DU REPO

```
the-grid/
├── Claude_init/
│   ├── CLAUDE.md           ← ce fichier
│   └── claudetodo.md       ← tâches en cours
│
├── README.md
│
├── architecture/
│   ├── SYSTEM.md           ← architecture système complète
│   ├── DATA-MODEL.md       ← schéma Supabase (SQL)
│   └── AGENTS.md           ← rôles et comportements des agents
│
├── frontend/
│   ├── index.html          ← app principale (Three.js + secteurs)
│   ├── grid-3d.js          ← scène Three.js (14 nœuds)
│   └── sector-view.js      ← vue détail par champ
│
├── backend/
│   ├── schema.sql          ← migrations Supabase
│   └── functions/          ← Supabase Edge Functions
│       ├── forsight-agent.ts
│       ├── sector-synthesis.ts
│       └── newsletter-curator.ts
│
└── agents/
    ├── forsight-agent.md   ← prompt + comportement
    ├── sector-agent.md     ← prompt + comportement
    └── curator-agent.md    ← prompt + comportement
```

---

## DÉCISIONS PRISES

| Date | Décision | Pourquoi |
|------|----------|----------|
| 2026-04-29 | Nom : The Grid | Navigation spatiale de la carte civilisationnelle |
| 2026-04-29 | 14 secteurs = 14 champs GLOBAL-PLAN | La structure existe déjà — pas à réinventer |
| 2026-04-29 | Three.js pour navigation 3D | Cohérence ISL, pas de framework lourd |
| 2026-04-29 | Supabase pour la mémoire | Realtime + auth + simple à solo-founder |
| 2026-04-29 | ISL comme partenaire institutionnel | Crédibilité + byline pour publication |
| 2026-04-29 | Newsletter hebdo comme canal d'impact | Publication concrète, pas juste discussion |

---

## CE QUI MANQUE ENCORE

**Phase 1 — Prototype (v0.1) :**
- [ ] Scène Three.js : 14 nœuds navigables (comme ISL Vallée mais constellation globale)
- [ ] Vue secteur : phase + bottlenecks + Forsights (statique pour l'instant)
- [ ] Schéma Supabase : fields + forsights + members

**Phase 2 — Communauté (v0.2) :**
- [ ] Auth magic link (Supabase)
- [ ] Contribution : formulaire d'observation → agent → Forsight draft
- [ ] Discussion par secteur (threads simples)

**Phase 3 — Publication (v0.3) :**
- [ ] Curation hebdomadaire par agent
- [ ] Newsletter Resend (template ISL design)
- [ ] LinkedIn publication (API + collectif)

**Phase 4 — Intelligence (v0.4) :**
- [ ] Agents actifs dans chaque secteur
- [ ] Phase tracking automatique (métriques GLOBAL-PLAN)
- [ ] askio1-llm intégré comme moteur de génération

---

## RÉFÉRENCES CLÉS

- `openClaude/ISL/GLOBAL-PLAN.md` — la carte, le contenu, les 14 champs
- `openClaude/ISL/Institut St-Laurent · Direction stratégique AGI-1.html` — design reference
- `openClaude/Forsight/` — le corpus de démonstration
- `openClaude/Enter-Game/` — le protocole d'adoption
- `openClaude/askio1-llm/` — le moteur IA (phase 4)

---

## SHORTHAND

```
Git/the-grid   → ce projet
contexte       → CLAUDE.md + claudetodo.md
go [tâche]     → exécute
```

*Créé 2026-04-29 · The Grid — the living intelligence network*
