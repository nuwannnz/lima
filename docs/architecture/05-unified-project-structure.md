### Unified Project Structure

```plaintext
lima-planner/
├── .github/
│   └── workflows/          # GitHub Actions CI/CD pipelines
│       ├── ci.yml          # Runs on PRs to develop
│       ├── deploy-staging.yml # Runs on merge to develop
│       └── deploy-prod.yml # Manually triggered on main
├── apps/
│   ├── lima-web/
│   │   └── src/
│   │       ├── app/              # Root layouts, pages, API routes
│   │       ├── features/         # Feature-based modules
│   │       │   ├── auth/
│   │       │   │   ├── components/
│   │       │   │   └── actions.ts
│   │       │   ├── tasks/
│   │       │   │   ├── components/ # e.g., TaskCard.tsx, TaskForm.tsx
│   │       │   │   ├── hooks/      # e.g., useTasks.ts
│   │       │   │   └── actions.ts  # Server Actions for tasks
│   │       │   └── ...             # Other features (projects, notes)
│   │       ├── lib/                # Core libraries (Supabase client, sync service)
│   │       └── styles/             # Global styles
│   └── lima-web-e2e/
├── packages/
│   ├── domain/               # Data access logic and mappers
│   ├── ui/                   # Shared, generic UI components
│   └── types/                # Shared TypeScript interfaces
└── package.json            # Root package.json with app version
```

***
