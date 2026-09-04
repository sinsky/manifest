# Manifest Agent Guidelines

## Domain Terminology

Manifest terminology is directional:

- A **Manifest Request** is one logical request from an agent to Manifest and lives in `requests`.
- A **Provider Attempt** is one request from Manifest to an AI provider and lives in `agent_messages`.
- An **Agent** is an AI agent owned by a tenant. The dashboard labels agents **Harnesses** (nav under `/harnesses`; legacy `/agents/*` URLs redirect) — this is UI copy only; backend code, database tables, and API routes still say *agent*.

[`docs/glossary.md`](docs/glossary.md) is the canonical contract for statuses, ordering, recovery, database mapping, and counting rules. Do not duplicate those definitions in agent guides.

## Branch Strategy & Workflow Guidelines

### Branch Structure
- **`main`**: Upstream base branch. Mirror of the official upstream repository.
- **`custom/next`**: Main integration and active development branch for custom features. Feature branches target this branch for merging.
- **`custom/<version>-<identifier>`** (e.g., `custom/6.17.1-sinsky`): Version-specific custom tracking/working branches.
- **`feat/<feature-name>`** (e.g., `feat/use-generic-oidc`): Short-lived feature branches for individual feature development.
- **`release/<version>`** (e.g., `release/6.17.1-sinsky`): Release stabilization branches for deployment.

### Workflow & Merge Rules
1. **Feature Branching**: Always create a `feat/<feature-name>` branch for new features or bug fixes.
2. **Commits & Changesets**:
   - Follow Conventional Commits format (`feat(scope): ...`, `fix(scope): ...`, `chore: ...`).
   - Include a Changeset file in `.changeset/` for user-facing or package-level changes.
3. **Testing & Push**:
   - Run workspace tests (`npm test`) before pushing.
   - Push topic branches to `origin/feat/<feature-name>`.
4. **Integration**:
   - Merge `feat/<feature-name>` into `custom/next` via UI / Pull Request.

