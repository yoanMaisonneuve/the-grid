# CLAUDETODO.md — The Grid

*Créé : 2026-04-29*

---

## 🔴 CRITIQUE — Phase 1 : Prototype

- [ ] **Scène 3D — 14 nœuds** : Three.js. Constellation des 14 champs du GLOBAL-PLAN.
  - Fond marine ISL (`#001e30`), nœuds vivid (`#009ADE`), connexions lignes fines
  - Chaque nœud : label + indicateur de phase (couleur) + pulse d'activité
  - Navigation : click → zoom vers secteur
  - Connexions entre champs liés (Human-AI ↔ Companies, Energy ↔ Environment, etc.)
  - Rotation lente automatique (comme ISL camera sweep)

- [ ] **Vue secteur** : quand on clique sur un nœud
  - Panel latéral ISL Register A : nom du champ, phase actuelle, bottleneck principal
  - Liste des Forsights actifs dans ce secteur (statique pour v0.1)
  - Bouton "Contribuer une observation"

- [ ] **Schéma Supabase v1** : tables fields, forsights, members (cf. DATA-MODEL.md)

---

## 🟡 IMPORTANT — Phase 2 : Communauté

- [ ] **Auth magic link** : Supabase Auth, friction zéro
- [ ] **Formulaire contribution** : texte brut → agent → Forsight draft → review → publish
- [ ] **Threads de discussion** par secteur (structure simple, pas de threading infini)
- [ ] **Profil membre** : champs d'intérêt, Forsights contribuées, date de join

---

## 🟢 BIENTÔT — Phase 3 : Publication

- [ ] **Curation agent** : lit toutes les Forsights de la semaine, sélectionne top 3
- [ ] **Newsletter template** : design ISL Register A, Resend comme provider
- [ ] **LinkedIn integration** : publication collective (byline communautaire + ISL)
- [ ] **Annonces de phase** : quand un champ change de phase → post public automatique

---

## 💭 À VALIDER AVEC YOAN

- [ ] **Accès** — invite-only au départ ou ouvert ? Curated vs masse critique
- [ ] **Rôle ISL** — ISL publie les newsletters ? Ou juste byline/crédibilité ?
- [ ] **Langue** — FR/EN bilingue dès le début ou FR first ?
- [ ] **Domaine** — the-grid.io ou sous-domaine ISL (grid.isl.ca) ?
- [ ] **Monetization** — freemium ? donateur ? jamais ?

---

## ✅ COMPLÉTÉ 2026-04-29

- [x] Vision crystallisée et validée avec Yoan
- [x] Projet créé (dossier + CLAUDE.md + todo)
- [x] Architecture 4 couches définie
- [x] Stack technique choisi (Three.js + Supabase + Claude API + Resend)
- [x] Repo GitHub créé

---

*[ ] = à faire · [x] = complété*
