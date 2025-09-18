# Requirements

## Functional

- **FR1**: The system shall be an installable Progressive Web App (PWA) that is offline-ready through the use of a service worker and cache strategy.
- **FR2**: The system must use Supabase for backend authentication and data storage, with a local IndexedDB cache providing an offline-first user experience.
- **FR3**: The user must be able to manage tasks on a 7-day (Mon-Sun) Kanban-style board with full CRUD (Create, Read, Update, Delete), drag-and-drop reordering, and a "complete" action.
- **FR4**: Tasks on the weekly board must automatically sort by High, Medium, and Low priority, with the user able to manually reorder tasks within each priority level.
- **FR5**: A separate "Next Week" planning view must be available, allowing the user to stage tasks in "Top 3" and "Nice-to-have" priority slots.
- **FR6**: The system must provide a prompt at the start of each week to handle incomplete tasks and offer mid-week actions to "Snooze to weekend/next week".
- **FR7**: Users must be able to create basic projects and notes, link them to tasks, and preview linked notes via a "peek" panel from the main board.
- **FR8**: The user experience must be mobile-first, featuring a responsive design, a sticky "Today" header, and support for mobile gestures like swipe and long-press for quick actions.

## Non-Functional

- **NFR1**: The application must function reliably offline, using the local IndexedDB cache as the primary source of truth during offline periods and syncing with Supabase when connectivity is restored.
- **NFR2**: The application must be fast and responsive to user input, with performance optimized for mobile devices.
- **NFR3**: Authentication must be handled via http-only, secure cookies to prevent client-side token exposure.
- **NFR4**: All data stored in Supabase must be protected by Row-Level Security (RLS) policies to ensure strict per-user data isolation.
- **NFR5**: The technology stack is fixed to Next.js (frontend), Supabase (backend), PostgreSQL (database), and an Nx monorepo structure.

---
