### Data Models

The following `camelCase` TypeScript interfaces will be defined in `packages/types`.

#### Project

```typescript
// packages/types/src/project.ts
export interface Project {
  id: string;
  userId: string;
  name: string;
  color: string;
  createdAt: string;
}
```

***

#### Note

```typescript
// packages/types/src/note.ts
export interface Note {
  id: string;
  userId: string;
  title: string;
  content: string;
  createdAt: string;
  updatedAt: string;
}
```

***

#### Task

```typescript
// packages/types/src/task.ts
export type TaskPriority = "High" | "Medium" | "Low";
export type TaskStatus = "Pending" | "Completed";

export interface Task {
  id: string;
  userId: string;
  projectId?: string | null;
  noteIds?: string[] | null;
  content: string;
  priority: TaskPriority;
  status: TaskStatus;
  dueDate: string;
  displayOrder: number;
  createdAt: string;
}
```

***
