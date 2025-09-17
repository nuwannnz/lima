# Lima Planner Product Requirements Document (PRD)

---

## Goals and Background Context

### Goals

- **FR1**: Validate the "weekly-first" focus model as a viable product differentiator in the productivity market.
- **FR2**: Launch a functional, offline-capable Progressive Web App (PWA) as a Minimum Viable Product (MVP) within a 4-month development timeframe.
- **FR3**: Ensure users feel more focused and less overwhelmed by their weekly tasks.
- **FR4**: Enable users to achieve a high completion rate for tasks scheduled within a given week.
- **FR5**: Drive consistent engagement with the "Next Week" planning feature.

### Background Context

Modern professionals are overwhelmed by task management tools that fail to separate immediate priorities from long-term goals, creating a high-noise environment that undermines focus. Existing solutions don't enforce a clear boundary between the "planning space" for future work and the "execution space" for the present.

Lima Planner solves this by being a mobile-first PWA centered on a 7-day "execution view" for the current week. It's differentiated by a dedicated "Next Week" planning area that protects user focus, all built on an offline-first architecture to ensure speed and constant availability.

### Change Log

| Date       | Version | Description                              | Author    |
| :--------- | :------ | :--------------------------------------- | :-------- |
| 2025-09-17 | 1.0     | Initial PRD draft based on Project Brief | John (pm) |

---

## Requirements

### Functional

- **FR1**: The system shall be an installable Progressive Web App (PWA) that is offline-ready through the use of a service worker and cache strategy.
- **FR2**: The system must use Supabase for backend authentication and data storage, with a local IndexedDB cache providing an offline-first user experience.
- **FR3**: The user must be able to manage tasks on a 7-day (Mon-Sun) Kanban-style board with full CRUD (Create, Read, Update, Delete), drag-and-drop reordering, and a "complete" action.
- **FR4**: Tasks on the weekly board must automatically sort by High, Medium, and Low priority, with the user able to manually reorder tasks within each priority level.
- **FR5**: A separate "Next Week" planning view must be available, allowing the user to stage tasks in "Top 3" and "Nice-to-have" priority slots.
- **FR6**: The system must provide a prompt at the start of each week to handle incomplete tasks and offer mid-week actions to "Snooze to weekend/next week".
- **FR7**: Users must be able to create basic projects and notes, link them to tasks, and preview linked notes via a "peek" panel from the main board.
- **FR8**: The user experience must be mobile-first, featuring a responsive design, a sticky "Today" header, and support for mobile gestures like swipe and long-press for quick actions.

### Non-Functional

- **NFR1**: The application must function reliably offline, using the local IndexedDB cache as the primary source of truth during offline periods and syncing with Supabase when connectivity is restored.
- **NFR2**: The application must be fast and responsive to user input, with performance optimized for mobile devices.
- **NFR3**: Authentication must be handled via http-only, secure cookies to prevent client-side token exposure.
- **NFR4**: All data stored in Supabase must be protected by Row-Level Security (RLS) policies to ensure strict per-user data isolation.
- **NFR5**: The technology stack is fixed to Next.js (frontend), Supabase (backend), PostgreSQL (database), and an Nx monorepo structure.

---

## User Interface Design Goals

### Overall UX Vision

The application's UX will be centered on creating a "calm productivity" environment. The design must be clean, intuitive, and mobile-first, actively protecting the user's focus on the current week. The core philosophy is "clarity over cleverness," ensuring users can manage their tasks with minimal noise and cognitive load.

### Key Interaction Paradigms

- **Primary View:** A 7-day Kanban-style board.
- **Task Manipulation:** Drag-and-drop for reordering and rescheduling tasks.
- **Quick Actions:** Swipe gestures (e.g., swipe right to complete) and long-press menus for common actions like snoozing or deleting.
- **Contextual Information:** A "peek" panel will allow users to quickly preview linked notes without leaving the main board.

### Core Screens and Views

- Main Weekly Board (the primary 7-day view)
- Next Week Planning View
- Task Creation / Editing View
- Project & Note Management Views
- Start-of-Week Carryover/Snooze Prompt
- Settings Page
- Authentication (Login/Signup) Flow

### Accessibility: WCAG AA

The application will adhere to Web Content Accessibility Guidelines (WCAG) 2.1 Level AA to ensure it is usable by people with a wide range of disabilities.

### Branding

To be defined. The initial design will use a clean, minimalist aesthetic with a focus on typography and clear visual hierarchy.

### Target Device and Platforms: Web Responsive

The application will be a Progressive Web App (PWA) built with a mobile-first approach. It must be fully responsive and functional across modern mobile, tablet, and desktop browsers.

---

## Technical Assumptions

### Repository Structure: Monorepo

The project will be structured as an Nx monorepo. This will contain separate packages for the web application (`lima-web`), shared UI components (`ui`), shared types (`types`), and a framework-agnostic domain layer (`domain`) for data access, as specified in the brief.

### Service Architecture: Serverless

The architecture will follow a serverless pattern. The frontend Next.js application will be the primary component, and all backend logic will be handled by Next.js Server Actions. These server actions will be the only part of the system authorized to interact with the data layer, ensuring a clear separation of concerns and a secure "server-only Supabase access" model.

### Testing Requirements: Full Testing Pyramid (Unit, Integration, and E2E)

The project will require a comprehensive testing strategy including unit tests, integration tests, and end-to-end tests for critical user flows.

### Additional Technical Assumptions and Requests

- **Frontend:** The frontend will be built with **Next.js**.
- **Backend & Database:** The backend will be provided by **Supabase**, utilizing its **PostgreSQL** database and authentication services.
- **Local Cache:** A local, client-side cache will be implemented using **IndexedDB** to support the offline-first requirement.
- **Hosting:** The Next.js application will be hosted on **Vercel**, and the backend on **Supabase's** infrastructure.
- **End-to-End Testing:** The `lima-web` application will have an associated end-to-end test project using **Playwright**.
- **Security:** Authentication will use **http-only, secure cookies**. Data access will be controlled via **Supabase Row-Level Security (RLS)**.

---

## Epic List

- **Epic 1: Foundation & Core Task Management:** Establish the core application infrastructure, authentication, and the primary weekly task board with basic create, read, update, and delete (CRUD) functionality.
- **Epic 2: Advanced Task Management & Planning Flow:** Implement the core value proposition of focused planning by adding prioritization, focus features, and the complete weekly planning and carryover/snooze cycle.
- **Epic 3: Contextualization & Offline Sync:** Enrich the user experience by adding contextual layers with Projects and Notes, and deliver the full offline-first promise with robust data synchronization.

---

## Epic and Story Details

### Epic 1: Foundation & Core Task Management

**Epic Goal:** To establish the core application infrastructure, including the project setup, user authentication, and the primary weekly task board. By the end of this epic, a user will be able to sign up, log in, and perform basic create, read, update, and delete (CRUD) operations on tasks within a responsive, 7-day Kanban-style interface.

#### Story 1.1: Project Setup & Foundation

**As a** developer,
**I want** the Nx monorepo and Next.js application initialized and configured with Supabase,
**so that** I have a clean, consistent, and ready-to-use codebase to begin building features.

**Acceptance Criteria:**

1.  An Nx monorepo is initialized with the package structure (`lima-web`, `ui`, `types`, `domain`) defined in the technical assumptions.
2.  The `lima-web` Next.js application is created and can be run successfully in a local development environment.
3.  The Supabase client is installed and configured with the necessary environment variables (`.env.example`).
4.  Basic linting (ESLint) and code formatting (Prettier) are configured and operational at the root level.
5.  The initial project structure is committed to a Git repository.

#### Story 1.2: User Authentication

**As a** user,
**I want** to be able to sign up, log in, and log out,
**so that** I can securely access my personal task board.

**Acceptance Criteria:**

1.  A user can create a new account using an email and password via a signup form.
2.  A registered user can sign in using their credentials via a login form.
3.  A logged-in user has the ability to log out of the application.
4.  Authentication state is managed securely using http-only cookies.
5.  Unauthenticated users attempting to access the main application are redirected to the login page.

#### Story 1.3: Basic Weekly Board UI

**As a** logged-in user,
**I want** to see the main 7-day Kanban-style board UI,
**so that** I have the primary interface for managing my weekly tasks.

**Acceptance Criteria:**

1.  After logging in, the user is directed to a view containing a board with 7 columns, labeled for each day of the week (e.g., Monday-Sunday).
2.  The column corresponding to the current day is visually highlighted.
3.  The layout is responsive and provides a usable experience on both mobile and desktop screens.
4.  The board initially displays a message or prompt for the user to create their first task.

#### Story 1.4: Task Data Model & Creation

**As a** user,
**I want** to create a new task for a specific day,
**so that** I can add my to-do items to the weekly board.

**Acceptance Criteria:**

1.  A `tasks` table is created in the Supabase database with fields for content, priority, status, due_date, and a link to the user ID.
2.  A Row-Level Security (RLS) policy is enabled on the `tasks` table to ensure users can only access their own tasks.
3.  The UI provides a mechanism (e.g., a button in each day's column) to open a "New Task" form.
4.  Submitting the form with task content creates a new record in the database and displays the task in the correct day's column on the board.

#### Story 1.5: View, Update, and Delete Tasks

**As a** user,
**I want** to be able to view details, edit, and delete my tasks,
**so that** I can manage the full lifecycle of my to-do items.

**Acceptance Criteria:**

1.  All of a user's tasks for the current week are correctly fetched from the database and displayed on the board upon loading.
2.  Clicking on a task card opens a view (e.g., a modal) where its content and priority can be edited.
3.  Saving changes in the edit view updates the task in the database and on the UI.
4.  The user can delete a task from the board, which removes it permanently from the database.
5.  A confirmation prompt is displayed before a task is deleted.

#### Story 1.6: Drag-and-Drop Rescheduling

**As a** user,
**I want** to drag and drop tasks between different days of the week,
**so that** I can easily reschedule my work.

**Acceptance Criteria:**

1.  A task card can be dragged from one day's column and dropped into another.
2.  Upon dropping, the task's due date is updated in the database to reflect the new day.
3.  The UI optimistically updates the task's position on the board immediately.
4.  The change in schedule persists after a full page refresh.

### Epic 2: Advanced Task Management & Planning Flow

**Epic Goal:** To implement the application's core value proposition of focused, intentional planning. This epic will introduce task prioritization, a "Today Focus" lane for high-priority items, and the complete weekly planning cycle, including the "Next Week" planning view and the start-of-week carryover workflow.

#### Story 2.1: Implement Task Prioritization

**As a** user,
**I want** to set a priority for my tasks and see them sorted accordingly,
**so that** my most important work is always displayed first.

**Acceptance Criteria:**

1.  The `tasks` data model is updated to include a priority field (e.g., High, Medium, Low).
2.  The task creation and editing forms allow the user to set a task's priority.
3.  Tasks within each day's column on the weekly board are automatically sorted by priority (High > Medium > Low).
4.  Users can still manually reorder tasks within the same priority group via drag-and-drop.
5.  The priority of a task is clearly visible on its card on the board (e.g., via a colored indicator).

#### Story 2.2: Create "Next Week" Planning View

**As a** user,
**I want** a separate space to plan for the upcoming week,
**so that** I can organize future tasks without cluttering my current week's view.

**Acceptance Criteria:**

1.  A new, navigable "Next Week" page or view is created.
2.  This view contains two distinct lists or columns: "Top 3 Priorities" and "Nice-to-haves".
3.  Users can create, edit, and delete "staged" tasks within these two sections.
4.  These staged tasks are stored separately and do not appear on the main weekly board.

#### Story 2.3: Implement Start-of-Week Carryover Workflow

**As a** user,
**I want** a guided process at the start of a new week to handle unfinished and planned tasks,
**so that** I can start each week with a clean, intentional plan.

**Acceptance Criteria:**

1.  When the user first opens the app in a new week, a dedicated "Weekly Planning" view or modal is presented.
2.  This view displays all incomplete tasks from the previous week and all staged tasks from the "Next Week" area.
3.  The user can drag these tasks onto the new, empty weekly board for the current week.
4.  The user has options to delete or defer tasks they do not schedule for the current week.
5.  Once the planning is complete, the user can start their week, and the "Next Week" area is cleared.

#### Story 2.4: Implement Mid-Week Snooze Actions

**As a** user,
**I want** to quickly defer tasks to the weekend or the next planning cycle,
**so that** I can adapt my plan and maintain focus as the week progresses.

**Acceptance Criteria:**

1.  An action is available on each task card (e.g., in a long-press menu) to "Snooze".
2.  The snooze options include "Snooze to Weekend" (moves the task to the current week's Saturday or Sunday) and "Snooze to Next Week" (moves the task to the "Next Week" planning area).
3.  The task's location is updated in the database and UI immediately upon snoozing.

### Epic 3: Contextualization & Offline Sync

**Epic Goal:** To enrich the user experience by allowing tasks to be linked to broader contexts like Projects and Notes. This epic will also deliver the full offline-first promise by implementing a robust and reliable data synchronization system between the local device and the Supabase backend.

#### Story 3.1: Create and Manage Projects & Notes

**As a** user,
**I want** to create and manage a list of my projects and a collection of notes,
**so that** I can organize my work into larger contexts and capture detailed information.

**Acceptance Criteria:**

1.  New `projects` and `notes` tables are created in Supabase with RLS policies ensuring user data privacy.
2.  A UI is available for creating, viewing, updating, and deleting projects (which consist of a title and a color attribute).
3.  A UI is available for creating, viewing, updating, and deleting notes (which consist of a title and long-form text content).

#### Story 3.2: Link Projects and Notes to Tasks

**As a** user,
**I want** to associate tasks with my projects and notes,
**so that** I can see the broader context of my work directly from my weekly board.

**Acceptance Criteria:**

1.  The database schema is updated to support relationships between tasks, projects, and notes.
2.  The task creation and editing forms are updated to allow a user to link a task to one project and one or more notes.
3.  On the weekly board, task cards visually indicate when they are linked to a project (e.g., a colored tag) or notes (e.g., an icon).

#### Story 3.3: Implement "Peek" Panel for Notes

**As a** user,
**I want** to quickly preview the content of a linked note without leaving my board,
**so that** I can reference detailed information without losing my flow.

**Acceptance Criteria:**

1.  Clicking the note indicator on a task card opens a non-disruptive overlay or side panel.
2.  The panel displays the content of the linked note(s) in a read-only format.
3.  The panel can be easily dismissed, returning the user to their board view.

#### Story 3.4: Implement Offline Data Queuing

**As a** user,
**I want** the application to save all my changes while I'm offline,
**so that** I can continue working with confidence, regardless of my internet connection.

**Acceptance Criteria:**

1.  The application correctly detects when it is offline.
2.  While offline, any action that modifies data (creating, updating, or deleting tasks, projects, or notes) is saved to the local IndexedDB.
3.  These changes are also added to a separate "sync queue" in IndexedDB, awaiting a network connection.
4.  The UI updates immediately and optimistically, as if the save was successful.

#### Story 3.5: Implement Background Sync and Basic Conflict Handling

**As a** user,
**I want** my offline changes to be automatically saved to the cloud when I reconnect,
**so that** my data is safe and consistent across all my devices.

**Acceptance Criteria:**

1.  When network connectivity is restored, a background process automatically begins processing the sync queue.
2.  Queued changes are sent to the Supabase backend in the order they were made.
3.  A basic "last write wins" conflict resolution strategy is implemented to handle potential data conflicts.
4.  Successfully synced changes are removed from the queue.
5.  If a sync operation fails repeatedly, the user is notified about the unsaved data.
