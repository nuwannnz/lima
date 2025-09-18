### Tech Stack

| Category                  | Technology       | Version | Purpose                        | Rationale                                                                             |
| :------------------------ | :--------------- | :------ | :----------------------------- | :------------------------------------------------------------------------------------ |
| **Monorepo Tool**         | Nx               | latest  | Manage the full-stack monorepo | Required by PRD for code sharing and build efficiency.                                |
| **Frontend Framework**    | Next.js          | latest  | Primary web framework          | Required by PRD; provides SSR, Server Actions, and a great DX.                        |
| **UI Component Library**  | Mantine          | latest  | Foundation for UI components   | Chosen in UI/UX spec for its accessibility and themeability.                          |
| **State Management**      | Zustand          | latest  | Global client-side state       | Lightweight, simple, and avoids boilerplate for managing global state.                |
| **Client-side DB**        | Dexie.js         | latest  | IndexedDB Wrapper              | Simplifies IndexedDB operations for the offline sync queue.                           |
| **Backend & Auth**        | Supabase         | latest  | BaaS (Database, Auth)          | Required by PRD for its integrated Postgres DB and secure auth.                       |
| **API Style**             | Server Actions   | N/A     | Secure backend logic           | Required by PRD; eliminates the need for traditional API routes.                      |
| **Unit/Integration Test** | **Vitest** / RTL | latest  | Component & logic testing      | Modern, fast, and Jest-compatible test runner.                                        |
| **E2E Testing**           | Playwright       | latest  | End-to-end user flow testing   | Required by PRD for critical path testing.                                            |
| **Styling**               | Mantine CSS      | N/A     | Styling solution               | Tightly integrated with the Mantine component library for a consistent design system. |

***
