**Session Date:** 2025-09-17
**Facilitator:** Business Analyst Mary
**Participant:** You

## Executive Summary

**Topic:** PWA Weekly Task Management App (Weekly board + Projects + Notes)

**Session Goals:** Define UX, technical features, and prioritization around a focused weekly planner with interconnected projects and notes; capture concrete decisions for a 4‑month MVP.

**Techniques Used:** Mind Mapping; First Principles; What‑If Scenarios; SCAMPER (S, C, A, M subsets); Role Clarifications

**Total Ideas Generated:** 25+

### Key Themes Identified:

- Weekly focus with minimal noise; goal-driven execution
- Interconnected model: standalone tasks, projects, and notes cross‑reference
- Next‑week planning and controlled carryover
- Lightweight prioritization (Low/Medium/High) driving sort and visuals
- Mobile‑first PWA with offline support (service worker)

## Technique Sessions

### Mind Mapping – 15m

**Description:** Expand core concept into branches and interconnections
**Ideas Generated:**

1. Weekly board with 7 columns (Mon–Sun); refresh weekly; carryover
2. Projects: tasks and notes inside projects; tasks with dates appear in week
3. Notes: can include tasks; can reference projects; tasks appear in week
4. Interlinks: task → note; note → tasks; project ↔ notes; weekly ↔ project

**Insights Discovered:**

- Weekly is the primary surface; projects/notes augment the week
- Standalone tasks must be first‑class (not only project tasks)

### First Principles – 10m

**Description:** Identify fundamentals to anchor design
**Ideas Generated:**

1. Focused current‑week view to drive weekly goal completion
2. Secondary needs: project grouping; brain offloading into notes; goal tracking

**Insights Discovered:**

- Weekly focus differentiates; avoid future overload by planning ahead but working now

### What‑If Scenarios – 10m

**Description:** Explore edge cases and adaptability
**Ideas Generated:**

1. Plan next week early; move tasks to next week without cluttering current
2. Goal changes mid‑week → reprioritize via priority levels
3. Chaotic week → filter by project; focus on one project at a time

**Insights Discovered:**

- Provide “Next Week” planning and quick project filters to reduce overwhelm

### SCAMPER – Substitute (selected)

**Description:** Replace elements to reveal new options
**Ideas Generated:**

1. Snooze to next week keeps metadata (project, note link, target weekday)
2. Next Week planning uses slots (Top 3, Nice‑to‑have) before assigning days
3. Highlight today’s column; sort by priority within each day

**Insights Discovered:**

- Separation of planning (slots) and scheduling (days) aids clarity

### SCAMPER – Combine (selected)

**Description:** Merge elements to amplify value
**Ideas Generated:**

2. Visual priority accents; day columns sort High→Medium→Low

**Insights Discovered:**

- A single “Today Focus” lane boosts execution clarity

### SCAMPER – Adapt (selected)

**Description:** Tailor UX patterns to contexts
**Ideas Generated:**

1. Mobile: sticky Today; per‑day (+); swipe left snooze; swipe right complete; long‑press quick actions
2. Carryover UX: mid‑week “Snooze to weekend/next week”; week‑start prompt with separate snoozed list
3. Project labels: colored pill; tap to inline filter; clear with X
4. Note links: peek panel on tap/hover; open note CTA

**Insights Discovered:**

- Micro‑interactions (swipe, long‑press, peek) keep flow on mobile/desktop

### SCAMPER – Modify/Minify/Magnify (selected)

**Description:** Adjust scale, density, and process
**Ideas Generated:**

1. Magnify Today Focus: persistent mini‑lane with drag‑in “Promote to Today”
2. Minify noise: collapse Low priority (user setting, default ON)
3. Modify weekly refresh: preview screen with carryovers, snoozed, and Next Week slots
4. Compact chips on mobile; expand on tap

**Insights Discovered:**

- User‑tunable density and a single refresh preview reduce friction

## Idea Categorization

### Immediate Opportunities

1. **Weekly board MVP**
   - Description: 7‑day kanban, priority sort, Today highlight, task chips with project/note indicators
   - Why immediate: Core interaction surface
   - Resources needed: UI scaffold, drag‑drop, state, service worker stub
2. **Next Week planning view**
   - Description: Sunday slots (Top 3, Nice‑to‑have) with suggest‑to‑days on rollover
   - Why immediate: Enables plan‑ahead while protecting current week focus
   - Resources needed: Secondary board, mapping logic
3. **Carryover & Snooze flow**
   - Description: Week‑start prompt; mid‑week snooze actions preserving metadata
   - Why immediate: Keeps board clean, supports intent
   - Resources needed: Task state machine, prompts, batch ops

### Future Innovations

1. **Time blocks (v2)**
   - Description: Schedule focus blocks rather than discrete tasks
   - Development needed: Calendar/time model, UI overlays
   - Timeline estimate: Post‑MVP
2. **Advanced goals**
   - Description: Multi‑month goals auto‑broken into weekly parts
   - Development needed: Goal engine, progress attribution
   - Timeline estimate: Post‑MVP

## Action Planning

### Top 3 Priority Ideas

#### #1 Priority: Weekly board MVP

- Rationale: Central value, validates PWA shell
- Next steps: Design wireframes; implement columns, drag‑drop; priority sort; Today highlight
- Resources needed: React/Vue/Svelte PWA, local DB (IndexedDB), DnD lib
- Timeline: Weeks 1–3

#### #2 Priority: Next Week planning view

- Rationale: Supports planning without breaking focus
- Next steps: Add slots view; mapping to days at rollover; accept/adjust UX
- Resources needed: View toggle, mapping algorithm, prompt UI
- Timeline: Weeks 2–4

#### #3 Priority: Carryover & Snooze flow

- Rationale: Keeps momentum across weeks
- Next steps: Implement snooze actions; week‑start carryover prompt; metadata preservation
- Resources needed: Task model updates; batch operations; tests
- Timeline: Weeks 3–5

## Reflection & Follow-up

- What worked well: Fast convergence on weekly‑first model; clear interaction rules
- Areas for further exploration: Goal decomposition engine; cross‑link UX in notes; monetization gates
- Recommended follow-up techniques: Six Thinking Hats for tradeoffs; Morphological Analysis for data model
- Questions that emerged: How to resolve conflicts when both slots and days are prefilled? Offline sync scope?
- Next session planning: Explore data model and PWA architecture; timeframe next 1–2 days; prepare rough ERD

---

_Session facilitated using the BMAD-METHOD™ brainstorming framework_

## MVP Scope Checklist

- App shell (PWA): installable, offline-ready (service worker, cache strategy)
- Data storage: local-first (IndexedDB) with simple export/import
- Weekly board (Mon–Sun):
  - Create/edit/delete tasks; drag across days; complete
  - Priority sort (High→Medium→Low); manual order within priority
  - Today column highlight;
  - Collapse Low priority toggle (setting, default ON)
  - Task chips show project pill and note icon (if linked)
- Next Week planning:
  - “Top 3” and “Nice-to-have” slots
  - Sunday planning toggle; map to days at week rollover with accept/adjust
- Carryover & Snooze:
  - Week-start carryover prompt for incomplete tasks
  - Mid-week actions: Snooze to weekend / Snooze to next week (preserve metadata)
- Projects:
  - Create/edit projects; color label
  - Optional link from task to project (editable later)
- Notes:
  - Create/edit notes; inline checklist items can become tasks (single note link per task)
  - Note peek panel from weekly board
- Settings:
  - Collapse Low priority default ON; toggle available
  - Priority levels: Low/Medium/High
- Mobile UX:
  - Sticky Today header, per-day (+), swipe complete/snooze, long-press quick actions
- Onboarding:
  - First-run sample week and quick tips

## Draft Data Model (concise)

- Task

  - id: string
  - title: string
  - description?: string
  - priority: 'low' | 'medium' | 'high'
  - status: 'open' | 'done' | 'snoozed'
  - scheduledWeekStart: ISO date (Mon of week)
  - scheduledWeekday?: 0–6 (Mon=0)
  - nextWeekSlot?: 'top3' | 'nice'
  - projectId?: string
  - noteId?: string
  - createdAt: ISO
  - updatedAt: ISO

- Project

  - id: string
  - name: string
  - color: string
  - createdAt: ISO
  - updatedAt: ISO

- Note

  - id: string
  - title: string
  - body: markdown
  - projectId?: string
  - createdAt: ISO
  - updatedAt: ISO

- System

  - settings:
    - collapseLowPriorityDefault: boolean (default true)
  - lastWeekStartSeen: ISO
  - snoozedTaskIdsForNextWeek: string[]

- Derived/Logic
  - Week rollover: map nextWeekSlot → proposed weekdays; prompt user
  - Carryover: pull open tasks from previous week; preserve project/note links and weekday
  - Filters: by project, priority, status

## Architecture Decisions (initial)

- Framework & Workspace
  - Next.js app within an Nx monorepo (apps + libs structure)
  - PWA configuration for installability
- Authentication & Backend
  - Supabase for auth and primary data storage
  - Row-Level Security (RLS) enabled; per-user data isolation
- Offline Strategy
  - Local-first cache using IndexedDB
  - Background sync to Supabase; conflict policy to be defined
  - Service Worker: cache shell + API fallbacks where feasible
- Data Sync
  - Realtime optional (Supabase Realtime) for multi-device coherence
  - Migrations tracked via Nx workspace generators

## Open Questions for Architect Agent

1. Sync model: CRDT vs. last-write-wins with merge prompts?
2. How to queue writes offline and replay safely with RLS?
3. Data modeling in Supabase: tables for tasks/projects/notes; indices and RLS policies?
4. Service worker strategy: Workbox vs. custom; versioning and cache invalidation?
5. Nx layout: what shared libs (ui, data-access, feature modules) and generators?
6. Realtime: do we need live updates or periodic pull is sufficient for v1?
7. Encryption at rest locally (e.g., IndexedDB) for sensitive note contents?

## Proposed Nx Workspace Structure

- apps/
  - lima-web (Next.js app, PWA)
- packages/
  - ui (shared UI components, headless + styled)
  - types (shared TypeScript types/interfaces)
  - auth (server-only auth helpers, cookie/session utils)
  - domain (TypeScript package encapsulating Supabase SDK and data services; framework-agnostic)

Principles:

- Supabase SDK usage is encapsulated in `packages/domain` (framework-agnostic TS)
- Next.js server actions live in `apps/lima-web` and call into `domain`
- Frontend imports only `ui`, `types`, and calls server actions—no direct Supabase on the client
- Auth uses http-only cookies with JWT; no tokens exposed to client JS.

## Server-only Supabase Access & Auth Pattern

- Auth Flow
  - Next.js server action signs in/up via Supabase auth API
  - Store session/JWT in http-only, secure cookies
  - Rotate/refresh via server; client receives only derived user state (id, name)
- Data Access
  - `packages/domain`: exports typed services/repositories using Supabase SDK
  - `apps/lima-web`: server actions validate user from cookies, then call domain services
  - Returns DTOs to UI; can replace backend by swapping domain implementation
- Offline
  - Client writes to IndexedDB; enqueue delta
  - Background sync triggers server actions when online

## Minimal Supabase Schema Draft (with RLS)

- tables: profiles

  - id uuid pk references auth.users
  - display_name text
  - created_at timestamptz default now()

- tables: projects

  - id uuid pk default gen_random_uuid()
  - user_id uuid not null references auth.users
  - name text not null
  - color text
  - created_at timestamptz default now()
  - updated_at timestamptz default now()

- tables: notes

  - id uuid pk default gen_random_uuid()
  - user_id uuid not null references auth.users
  - project_id uuid null references projects(id) on delete set null
  - title text not null
  - body text
  - created_at timestamptz default now()
  - updated_at timestamptz default now()

- tables: tasks
  - id uuid pk default gen_random_uuid()
  - user_id uuid not null references auth.users
  - title text not null
  - description text
  - priority text check (priority in ('low','medium','high')) not null default 'medium'
  - status text check (status in ('open','done','snoozed')) not null default 'open'
  - scheduled_week_start date
  - scheduled_weekday smallint check (scheduled_weekday between 0 and 6)
  - next_week_slot text check (next_week_slot in ('top3','nice'))
  - project_id uuid null references projects(id) on delete set null
  - note_id uuid null references notes(id) on delete set null
  - created_at timestamptz default now()
  - updated_at timestamptz default now()

RLS (per table):

- enable row level security
- policy "own rows" using (auth.uid() = user_id)
- inserts/updates restricted to auth.uid() = user_id

Indexes:

- tasks(user_id, scheduled_week_start, scheduled_weekday)
- tasks(user_id, status, priority)
- notes(user_id, project_id)
- projects(user_id)
