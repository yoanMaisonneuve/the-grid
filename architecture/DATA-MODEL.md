# DATA MODEL — The Grid
## Supabase / PostgreSQL Schema

---

## Tables

### `fields` — Les 14 champs du GLOBAL-PLAN

```sql
create table fields (
  id            serial primary key,
  slug          text unique not null,  -- 'human-ai', 'energy', 'cities'...
  name_fr       text not null,
  name_en       text not null,
  phase         text not null check (phase in ('emergence', 'disruption', 'integration')),
  phase_detail  text,                  -- 'early', 'mid', 'late', 'transition'
  description   text,
  bottlenecks   jsonb,                 -- [{level: 'critical', description: '...'}]
  human_tasks   text[],
  ai_tasks      text[],
  primary_metric jsonb,                -- {name, current, target_2030, target_2040}
  position_3d   jsonb,                 -- {x, y, z} pour la scène Three.js
  connections   text[],               -- slugs des champs connectés
  color_accent  text,                  -- couleur hex pour la scène 3D
  updated_at    timestamptz default now()
);

-- Seed data (14 champs)
insert into fields (slug, name_fr, name_en, phase, phase_detail, position_3d, connections) values
  ('human-ai',    'Collaboration Humain-IA',    'Human-AI Collaboration',  'disruption',  'early', '{"x": 0,  "y": 2,  "z": 0}',   '["companies","education","people"]'),
  ('robotics',    'Robotique Humanoïde',         'Humanoid Robotics',       'emergence',   'late',  '{"x": 2,  "y": 1,  "z": -1}',  '["human-ai","energy","cities"]'),
  ('energy',      'Énergie',                     'Energy',                  'disruption',  'mid',   '{"x": -2, "y": 0,  "z": 1}',   '["environment","robotics","cities"]'),
  ('education',   'Éducation',                   'Education',               'emergence',   'late',  '{"x": 1,  "y": -1, "z": 2}',   '["human-ai","people","governance"]'),
  ('health',      'Santé',                       'Health',                  'emergence',   'transition', '{"x": -1, "y": 2,  "z": 1}', '["mental-health","people","governance"]'),
  ('economy',     'Économie',                    'Economy',                 'disruption',  'early', '{"x": 0,  "y": -2, "z": 0}',   '["companies","people","governance"]'),
  ('environment', 'Environnement',               'Environment',             'disruption',  'mid',   '{"x": -2, "y": -1, "z": -1}',  '["energy","food","cities"]'),
  ('peace',       'Paix & Conflits',             'Peace & Conflict',        'disruption',  'mid',   '{"x": 2,  "y": -1, "z": 1}',   '["governance","people","economy"]'),
  ('cities',      'Villes',                      'Cities',                  'emergence',   'mid',   '{"x": 1,  "y": 1,  "z": -2}',  '["energy","robotics","governance"]'),
  ('governance',  'Gouvernance',                 'Governance',              'emergence',   'early', '{"x": -1, "y": -1, "z": 2}',  '["economy","education","peace"]'),
  ('companies',   'Entreprises',                 'Companies & Organizations','disruption', 'early', '{"x": 2,  "y": 0,  "z": 2}',   '["human-ai","economy","people"]'),
  ('people',      'Individus',                   'People & Individuals',    'emergence',   'early', '{"x": 0,  "y": 0,  "z": -2}',  '["mental-health","education","economy"]'),
  ('food',        'Alimentation',                'Food & Agriculture',      'emergence',   'mid',   '{"x": -2, "y": 1,  "z": -2}',  '["environment","energy","health"]'),
  ('mental-health','Santé Mentale',              'Mental Health',           'disruption',  'mid',   '{"x": 1,  "y": -2, "z": -1}',  '["people","health","governance"]');
```

---

### `members` — Les visionnaires

```sql
create table members (
  id                uuid primary key default gen_random_uuid(),
  email             text unique not null,
  name              text,
  bio               text,
  fields_of_interest text[],        -- slugs des champs qui les intéressent
  forsight_count    int default 0,
  role              text default 'member' check (role in ('member', 'curator', 'admin')),
  joined_at         timestamptz default now(),
  last_active       timestamptz
);
```

---

### `forsights` — Les insights directionnels

```sql
create table forsights (
  id              uuid primary key default gen_random_uuid(),
  number          text unique,            -- 'F001', 'F002', etc.
  field_id        int references fields(id),
  author_id       uuid references members(id),
  raw_input       text not null,          -- texte brut, voice-to-text
  published_content text,                -- version LinkedIn structurée
  title           text,                  -- titre court
  formula         text,                  -- la formule transmissible (dernière ligne)
  hashtags        text[],
  status          text default 'draft' check (status in ('draft','review','published','featured')),
  source          text default 'community' check (source in ('yoan','community','agent')),
  newsletter_issue_id uuid,
  linkedin_url    text,
  created_at      timestamptz default now(),
  published_at    timestamptz
);

create index on forsights(field_id);
create index on forsights(status);
create index on forsights(created_at desc);
```

---

### `discussions` — Les fils par secteur

```sql
create table discussions (
  id          uuid primary key default gen_random_uuid(),
  field_id    int references fields(id),
  forsight_id uuid references forsights(id),  -- null si discussion générale du secteur
  author_id   uuid references members(id),
  parent_id   uuid references discussions(id), -- pour les réponses (1 niveau max)
  content     text not null,
  type        text default 'observation' check (type in ('observation','question','challenge','synthesis','agent')),
  created_at  timestamptz default now()
);

create index on discussions(field_id);
create index on discussions(forsight_id);
```

---

### `newsletter_issues` — Les publications hebdomadaires

```sql
create table newsletter_issues (
  id                  uuid primary key default gen_random_uuid(),
  week_label          text not null,        -- '2026-W18'
  featured_forsights  uuid[],               -- top 3 forsight IDs
  synthesis           text,                 -- intro rédigée par l'agent
  field_highlights    jsonb,               -- {field_slug: "note de la semaine"}
  subscriber_count    int default 0,
  open_rate           float,
  published_at        timestamptz,
  created_at          timestamptz default now()
);
```

---

### `phase_events` — Historique des changements de phase

```sql
create table phase_events (
  id          uuid primary key default gen_random_uuid(),
  field_id    int references fields(id),
  from_phase  text,
  to_phase    text,
  trigger     text,           -- ce qui a déclenché le changement
  evidence    text,           -- données/sources
  announced   boolean default false,
  created_at  timestamptz default now()
);
```

---

## Policies RLS (Row Level Security)

```sql
-- Members peuvent lire tout
alter table fields enable row level security;
alter table forsights enable row level security;
alter table members enable row level security;
alter table discussions enable row level security;

-- Lecture publique pour fields et forsights published
create policy "fields are public" on fields for select using (true);
create policy "published forsights are public" on forsights for select using (status = 'published' or status = 'featured');

-- Membres authentifiés peuvent contribuer
create policy "members can insert forsights" on forsights for insert 
  with check (auth.uid() = author_id);
create policy "members can insert discussions" on discussions for insert 
  with check (auth.uid() = author_id);
```

---

*DATA-MODEL.md · The Grid · 2026-04-29*
