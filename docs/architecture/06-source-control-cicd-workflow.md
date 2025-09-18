### Source Control & CI/CD Workflow

#### Branching Strategy

* **`main`**: This branch is a mirror of the current **production code**. Direct commits are forbidden.
* **`develop`**: This is the primary integration branch containing the **latest development code**. All feature branches are created from `develop`.
* **Feature Branches (`feat/...`, `fix/...`, etc.)**: All new work must be done on a feature branch. When complete, a Pull Request is opened to merge the feature branch into `develop`.

***

#### Commit Conventions

* All commit messages **must** follow the **Conventional Commits** specification (e.g., `feat(tasks): ...`, `fix(auth): ...`). This is essential for automated versioning.
* This will be enforced automatically using Git hooks.

***

#### Git Hooks

* **`husky`** and **`commitlint`** will be configured to run a `commit-msg` hook, which will validate that every commit message adheres to the Conventional Commits format before it can be created.

***

#### Continuous Integration (CI)

* A **GitHub Actions** workflow (`ci.yml`) will run on every Pull Request targeting the `develop` branch.
* The CI pipeline will execute linting, testing, and build jobs. A PR cannot be merged into `develop` until all checks pass.

***

#### Staging Deployment & Versioning

* Upon a successful merge to `develop`, a **GitHub Actions** workflow (`deploy-staging.yml`) will trigger.
* This workflow has two key responsibilities:
  1. **Semantic Versioning:** It will analyze the commit messages since the last release and automatically bump the `version` in the root `package.json` (patch, minor, or major). It will then commit this change back to `develop`.
  2. **Staging Deployment:** It will deploy the application to a **staging environment** on Vercel for final review and QA.

***

#### Production Deployment

* **Release Process:** When the `develop` branch is stable and ready for production, a Pull Request is opened from `develop` to `main`.
* **Manual Trigger:** After the release PR is merged into `main`, the production deployment is **manually triggered**.
* **Production Workflow (`deploy-prod.yml`):**
  1. A project manager or lead developer manually runs the "Deploy to Production" action in GitHub.
  2. The workflow deploys the `main` branch to the **production environment** on Vercel.
  3. Upon successful deployment, it automatically creates a Git tag (e.g., `v1.2.0`) from the version in `package.json`, marking the release point.

***
