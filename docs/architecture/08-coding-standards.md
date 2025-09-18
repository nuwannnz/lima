### Coding Standards

* **SOLID Component Design:** Components should adhere to the Single Responsibility Principle. They should be focused on one piece of functionality and compose with other components to build complex UIs.
* **Automated Formatting:** **ESLint** and **Prettier** will be configured at the monorepo root to enforce a consistent coding style. A pre-commit hook will automatically format staged files.
* **Function Commenting:** All non-trivial, reusable functions, especially those in the `domain` and `lib` packages, **must** be documented with JSDoc-style comments explaining their purpose, parameters, and return values.
* **Database <> App Mapping:** The `domain` package **must** contain data mapper functions to translate between the database's `snake_case` and the application's `camelCase` conventions.
* **Server-Side Logic:** All database interactions **must** occur within Next.js Server Actions.

<!-- end list -->
