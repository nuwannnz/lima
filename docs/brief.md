# Project Brief: Lima Planner

### **Executive Summary**

This project brief outlines the development of a Progressive Web App (PWA) for weekly task management, tentatively named "Lima Planner." The application is designed for professionals who need a focused, goal-oriented planning tool. Its core feature is a 7-day board that prioritizes the current week's tasks to minimize noise and drive execution. The system integrates a simple, interconnected model of projects and notes, allowing tasks to be standalone or linked to greater context. Key differentiators include a dedicated "Next Week" planning view to protect current-week focus, offline-first capability, and a clean, intuitive mobile experience. The goal is to deliver a Minimum Viable Product (MVP) within a 4-month timeframe.

### **Problem Statement**

Modern professionals and planners are often overwhelmed by task management tools that act as "everything buckets," blending immediate priorities with long-term goals. This creates a high-noise environment where the critical tasks for the current week get lost, leading to a lack of focus and increased anxiety.

Existing solutions fail to enforce a clear separation between the "planning space" for future work and the "execution space" for the present. As a result, users spend more time organizing their tool than completing their work, and the primary goal—finishing this week's most important tasks—is consistently undermined. There is a need for a tool that actively protects the user's focus on the current week while still providing a structured, non-intrusive way to plan for the next.

### **Proposed Solution**

We propose a mobile-first Progressive Web App (PWA) that presents the user with a primary, 7-day Kanban-style board for the current week. This "execution view" is the core of the application, designed to be minimal and focused.

The solution's key differentiator is a dedicated "Next Week" planning area, which allows users to stage tasks in priority slots ('Top 3', 'Nice-to-have') without cluttering their current view. A structured carryover and snooze flow at the start of each week ensures a clean slate and intentional planning.

The data model is built on three interconnected entities: standalone **Tasks**, which can be grouped into **Projects**, and supplemented by long-form **Notes**. This provides flexibility for both simple to-do lists and more complex, project-based work. The UI will be enhanced with a clean, intuitive mobile experience. The application will be architected as an offline-first PWA, using local storage (IndexedDB) to ensure speed and constant availability.

### **Target Users**

**Primary User Segment: The Focused Professional**
This user is a busy professional, consultant, or small business owner who juggles multiple projects and responsibilities. They are tech-savvy and live in their calendar and digital tools, but they struggle with the constant "noise" and administrative overhead of complex project management software.

- **Behaviors & Workflows:** They plan their week in advance, often on a Sunday or Monday morning. They need to quickly capture tasks and ideas throughout the day without losing focus on their immediate priorities. They value tools that are fast, reliable, and work seamlessly across their desktop and mobile devices, even with intermittent connectivity.
- **Needs & Pain Points:** Their primary pain point is the mental clutter and anxiety caused by seeing a massive backlog of future tasks while trying to focus on the current week. They need a system that helps them compartmentalize planning from execution. They require a tool that is quick for capture but powerful enough to link tasks to broader project contexts or notes when needed.
- **Goals:** Their main goal is to end each week feeling accomplished, having completed their most important tasks. They want to feel in control of their workload and be confident that nothing is falling through the cracks, without needing to constantly re-organize a complex system.

### **Goals & Success Metrics**

**Business Objectives**

- Validate the "weekly-first" focus model as a viable product differentiator in the crowded productivity market.
- Successfully launch a functional, offline-capable PWA as a Minimum Viable Product (MVP) within a 4-month development timeframe.

**User Success Metrics**

- Users report feeling more focused and less overwhelmed by their weekly tasks.
- Users achieve a high completion rate for the tasks they schedule for a given week.
- Users consistently engage with the "Next Week" planning feature, indicating they value the separation of planning and execution.

**Key Performance Indicators (KPIs)**

- **Engagement:** Weekly Active Users (WAU).
- **Effectiveness:** Weekly Task Completion Rate (% of tasks marked 'done' versus 'created' or 'snoozed').
- **Core Feature Adoption:** Percentage of active users who utilize the "Next Week" planning view each week.

### **MVP Scope**

**Core Features (Must Have)**

- **PWA Shell:** An installable, offline-ready application using a service worker and cache strategy.
- **Data Storage & Sync:** The app will use **Supabase** as the primary backend for authentication and data storage. A local cache using **IndexedDB** will provide a fast, offline-first user experience, with data syncing to Supabase when the user is online.
- **Weekly Board:** A 7-day Kanban view (Mon-Sun) with full task CRUD (Create, Read, Update, Delete), drag-and-drop reordering, and a "complete" action.
- **Prioritization:** Tasks automatically sort by High→Medium→Low priority, with manual ordering within each priority level. The "Today" column will be visually highlighted.
- **Focus Features:** A user setting to collapse low-priority tasks by default.
- **Next Week Planning:** A separate view with "Top 3" and "Nice-to-have" slots for planning the upcoming week.
- **Carryover & Snooze:** A prompt at the start of the week to handle incomplete tasks, plus mid-week "Snooze to weekend/next week" actions.
- **Projects & Notes Integration:** Ability to create basic projects (with a color label) and notes, and link them to tasks. Task chips will visually indicate any links. A "peek" panel will allow for quick note previews from the board.
- **Mobile-First UX:** A responsive design including a sticky "Today" header, swipe gestures to complete/snooze, and long-press for quick actions.

**Out of Scope for MVP**

- Time blocking and calendar-style scheduling.
- Advanced goal tracking (e.g., multi-month goals broken down into weekly tasks).
- Real-time, multi-user collaboration and advanced data sync conflict resolution.
- Advanced reporting and analytics.

**MVP Success Criteria**

- The PWA can be successfully installed and functions reliably offline on modern mobile and desktop browsers, syncing data with the Supabase backend when online.
- All "Core Features" listed above are implemented and meet quality standards.
- Early user feedback confirms that the weekly-first focus model is intuitive and helps reduce feelings of overwhelm.
- KPIs show initial user engagement and consistent use of the core board and "Next Week" planning features.

### **Post-MVP Vision**

**Phase 2 Features**
Once the core MVP is validated, the next logical steps will be to introduce more advanced planning capabilities, including:

- **Time Blocks:** Allowing users to schedule dedicated focus blocks for tasks or projects directly on their weekly board, moving from task management to time management.
- **Advanced Goal Tracking:** Introducing a system for defining multi-month or quarterly goals that can be automatically broken down into suggested weekly tasks.
- **AI-Powered Project Decomposition:** When a user creates a new project, an AI assistant will help by suggesting a list of actionable tasks and organizing them into a proposed weekly schedule to kickstart the planning process.

**Long-term Vision**
The long-term vision for Lima Planner is to become a "calm productivity" partner that helps users manage their focus, not just their tasks. The application will evolve to proactively help users achieve their long-term objectives by translating them into manageable, focused weekly increments, preventing burnout and reducing the anxiety associated with traditional, backlog-heavy productivity systems.

**Expansion Opportunities**

- **Team Collaboration:** Introduce a team version for small, focused teams to plan their weekly sprints.
- **Integrations:** Connect with popular calendar, note-taking, and project management tools.
- **Monetization:** Explore premium features, such as advanced analytics, goal tracking, or team capabilities.
- **Enhanced Note-Taking:** Develop the notes feature into a more powerful, interconnected knowledge base.

### **Technical Considerations**

**Platform Requirements**

- **Target Platforms:** The application will be a Progressive Web App (PWA) designed with a mobile-first approach, ensuring responsiveness across modern mobile, tablet, and desktop browsers.
- **Performance Requirements:** The application must be fast and responsive, leveraging an offline-first architecture to ensure usability even with intermittent network connectivity.

**Technology Preferences**

- **Frontend:** Next.js.
- **Backend:** Supabase will be used for authentication and the primary PostgreSQL database.
- **Database:** PostgreSQL (via Supabase) for the primary data store and IndexedDB for the local, client-side cache.
- **Hosting/Infrastructure:** Vercel is the implied host for the Next.js application, with Supabase managing the backend infrastructure.

**Architecture Considerations**

- **Repository Structure:** The project will be structured as an Nx monorepo, with separate packages for the web app (`lima-web`), shared UI components (`ui`), shared types (`types`), and a framework-agnostic domain layer (`domain`) for data access.
- **Service Architecture:** A "server-only Supabase access" pattern will be used. Next.js server actions will be the only part of the application to interact with the `domain` package, which encapsulates all Supabase SDK calls. The client-side UI will not directly access Supabase.
- **Integration Requirements:** The primary integration is between the Next.js app and the Supabase backend. A Service Worker will be required to manage the offline cache and background data synchronization.
- **Security/Compliance:** Authentication will be handled via http-only, secure cookies to prevent client-side token exposure. Data access will be secured in Supabase using Row-Level Security (RLS) policies to ensure per-user data isolation.

### **Constraints & Assumptions**

**Constraints**

- **Timeline:** The project is strictly time-boxed to a 4-month development window for the Minimum Viable Product (MVP).
- **Resources:** Development will be executed by the BMad AI Agent Team.
- **Technical:** The technology stack (Next.js, Supabase, Nx) and the offline-first PWA architecture are considered fixed constraints for the MVP.

**Key Assumptions**

- **Value Proposition Assumption:** We assume that the "weekly-first" focus model is a compelling differentiator that will attract and retain users in the competitive productivity app market.
- **Technical Feasibility Assumption:** We assume that a reliable data synchronization model between the local IndexedDB cache and the Supabase backend can be successfully implemented within the MVP timeline, including handling offline writes and potential conflicts.
- **User Behavior Assumption:** We assume that the target users are willing to install a Progressive Web App (PWA) and that this format is sufficient for MVP validation, as opposed to requiring native mobile applications.
- **MVP Scope Assumption:** We assume that the feature set defined in the MVP scope is the right set to effectively test the core value proposition and gather meaningful user feedback.

### **Risks & Open Questions**

**Key Risks**

- **Technical Risk (High):** The complexity of implementing a robust and reliable offline-first data synchronization model. An incorrect implementation could lead to data loss or corruption, severely impacting user trust. The choice between sync models (e.g., CRDT vs. last-write-wins) has significant architectural implications.
- **Technical Risk (Medium):** Implementing a correct and maintainable service worker strategy for caching, background sync, and application updates is complex and can be a source of persistent bugs if not architected properly.
- **Scope Risk (Medium):** The feature set for the MVP, combined with the technical complexity of the offline-first architecture, may be too ambitious for the 4-month timeline.

**Open Questions**
The following questions were raised during brainstorming and need to be addressed by the Architect agent:

- What is the optimal sync model: CRDT vs. last-write-wins with merge prompts?.
- How should offline writes be queued and replayed safely against Supabase's Row-Level Security?.
- What is the optimal Service Worker strategy (Workbox vs. custom), especially regarding versioning and cache invalidation?.
- Is live, real-time data sync necessary for v1, or is a periodic pull sufficient?.
- Should sensitive content in the local IndexedDB be encrypted at rest?.

**Areas Needing Further Research**

- **Offline Synchronization Architecture:** A deep-dive is required to determine the best patterns for implementing a reliable sync layer between the browser's IndexedDB and the Supabase backend within a Next.js PWA.

### **Appendices**

**A. Brainstorming Session Summary**
This Project Brief is the direct result of a comprehensive brainstorming session conducted on 2025-09-17. The session output, detailed in `brainstorming-session-results.md`, provided the core concepts, MVP scope, initial architecture decisions, and open technical questions that form the foundation of this document.

### **Next Steps**

**Immediate Actions**

1.  **Handoff to Product Manager (PM):** The PM will use this approved brief as the primary input to begin creating the detailed Product Requirements Document (PRD).
2.  **Handoff to Architect:** The Architect will take this brief, paying special attention to the Technical Considerations and Risks sections, to begin researching and designing the full system architecture. The immediate priority is to solve the "Open Questions" regarding the offline-data synchronization strategy.
3.  **Schedule Follow-up:** A follow-up session should be scheduled within the next 1-2 days to review the Architect's initial data model and proposed sync strategy.

**Handoff to Product Manager & Architect**
This Project Brief provides the full context for the "Lima Planner" PWA.

- **To the PM:** Please begin the PRD generation process. Review this brief thoroughly and work with the user to create the PRD section by section, ensuring all requirements are captured in detail.
- **To the Architect:** Please begin the architecture design process. This brief and the referenced brainstorming document contain the foundational technical decisions and the most critical open questions that you need to solve.
