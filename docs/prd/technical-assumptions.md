# Technical Assumptions

## Repository Structure: Monorepo

The project will be structured as an Nx monorepo. This will contain separate packages for the web application (`lima-web`), shared UI components (`ui`), shared types (`types`), and a framework-agnostic domain layer (`domain`) for data access, as specified in the brief.

## Service Architecture: Serverless

The architecture will follow a serverless pattern. The frontend Next.js application will be the primary component, and all backend logic will be handled by Next.js Server Actions. These server actions will be the only part of the system authorized to interact with the data layer, ensuring a clear separation of concerns and a secure "server-only Supabase access" model.

## Testing Requirements: Full Testing Pyramid (Unit, Integration, and E2E)

The project will require a comprehensive testing strategy including unit tests, integration tests, and end-to-end tests for critical user flows.

## Additional Technical Assumptions and Requests

- **Frontend:** The frontend will be built with **Next.js**.
- **Backend & Database:** The backend will be provided by **Supabase**, utilizing its **PostgreSQL** database and authentication services.
- **Local Cache:** A local, client-side cache will be implemented using **IndexedDB** to support the offline-first requirement.
- **Hosting:** The Next.js application will be hosted on **Vercel**, and the backend on **Supabase's** infrastructure.
- **End-to-End Testing:** The `lima-web` application will have an associated end-to-end test project using **Playwright**.
- **Security:** Authentication will use **http-only, secure cookies**. Data access will be controlled via **Supabase Row-Level Security (RLS)**.

---
