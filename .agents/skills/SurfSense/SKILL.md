```markdown
# SurfSense Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you the core development patterns, coding conventions, and common workflows used in the SurfSense project. SurfSense is a Python-based codebase (no major framework detected) with both backend and frontend components. The repository emphasizes maintainable code through shared helpers, observability integration, modular UI components, and consistent configuration management. The commit history follows conventional commit patterns, and workflows are streamlined with suggested commands for frequent tasks.

---

## Coding Conventions

### File Naming

- Use **snake_case** for all file names.
  - Example: `user_profile.py`, `team_content.tsx`

### Import Style

- Use **alias imports** to clarify module usage.
  - Example:
    ```python
    import numpy as np
    import surfsense_backend.app.observability as observability
    ```

### Export Style

- Use **named exports** (when applicable, e.g., in TypeScript/JavaScript).
  - Example:
    ```typescript
    export const TeamContent = () => { ... }
    ```

### Commit Messages

- Follow **conventional commit** format.
  - Prefixes: `feat`, `refactor`, `fix`, `docs`
  - Example:
    ```
    feat: add OpenTelemetry integration to indexing pipeline
    ```

---

## Workflows

### Extract Shared Helper or Contract

**Trigger:** When logic or contracts (e.g., permission checks, types) are duplicated and need centralization.  
**Command:** `/extract-shared-helper`

1. Identify duplicated logic or contract (e.g., permission checks, cookie payload types).
2. Extract the logic/type into a new shared file (e.g., `atoms/`, `types/`, or `lib/`).
3. Update all consumers to use the new shared helper/type.
4. Remove old, duplicated implementations.
5. Fix any orphaned or leftover code from the extraction.

**Example:**
```python
# Before: permission check duplicated in multiple files
def has_permission(user, action): ...

# After: shared in surfsense_web/atoms/permissions.py
def has_permission(user, action): ...
```

---

### Observability Feature Integration

**Trigger:** When adding or extending observability/telemetry features (e.g., OpenTelemetry, metrics) in backend services.  
**Command:** `/add-observability`

1. Add or update observability-related config (e.g., `docker-compose`, `.env`, `otel-collector`).
2. Implement new metrics, tracing, or telemetry helpers in observability modules.
3. Instrument backend services, pipelines, or middleware to emit telemetry.
4. Add or update unit tests for observability features.
5. Update or add documentation for observability.

**Example:**
```python
# surfsense_backend/app/observability/metrics.py
from opentelemetry import metrics

def record_indexing_time(duration):
    metrics.get_meter("surfsense").create_histogram(
        "indexing_duration"
    ).record(duration)
```

---

### UI Component Refactor or Consolidation

**Trigger:** When improving UI maintainability, replacing components, or updating event handling patterns.  
**Command:** `/refactor-ui-component`

1. Identify the component or event pattern to refactor (e.g., replace `ContextMenu` with `DropdownMenu`).
2. Update component implementation and all usages.
3. Update or remove related helper logic.
4. Test for UI/UX consistency.

**Example:**
```tsx
// Before
import { ContextMenu } from 'old-ui-lib';

// After
import { DropdownMenu } from 'new-ui-lib';
```

---

### Dependency or Config Update with Feature

**Trigger:** When introducing a new backend feature that requires dependency or config changes.  
**Command:** `/update-dependencies`

1. Update dependency files (e.g., `pyproject.toml`, `uv.lock`, `package.json`).
2. Update or add related configuration files (`.env.example`, `docker-compose`).
3. Implement or update feature code.
4. Test integration.

**Example:**
```toml
# pyproject.toml
[tool.poetry.dependencies]
opentelemetry-sdk = "^1.12.0"
```

---

### Merge Mainline or Feature Branch

**Trigger:** When synchronizing a feature branch with the latest mainline changes.  
**Command:** `/merge-upstream`

1. Fetch and merge the upstream/mainline branch.
2. Resolve merge conflicts if any.
3. Update multiple files across backend and frontend.
4. Test and verify integration.

**Example:**
```bash
git fetch upstream
git merge upstream/main
# Resolve conflicts, then:
git commit
```

---

## Testing Patterns

- **Framework:** Unknown (no standard detected).
- **File Pattern:** Test files use the `*.test.ts` naming convention.
  - Example: `user_permissions.test.ts`
- **Note:** While the backend is Python, some frontend tests may be in TypeScript.

---

## Commands

| Command                  | Purpose                                                                 |
|--------------------------|-------------------------------------------------------------------------|
| /extract-shared-helper   | Centralize duplicated logic or contracts into a shared helper or type.   |
| /add-observability       | Add or extend observability/telemetry features in backend services.      |
| /refactor-ui-component   | Refactor or consolidate UI components and event handling patterns.       |
| /update-dependencies     | Update dependencies/configuration as part of a new feature integration.  |
| /merge-upstream          | Merge changes from mainline/upstream into your feature branch.           |
```
