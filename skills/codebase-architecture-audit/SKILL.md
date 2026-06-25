---
name: codebase-architecture-audit
description: Architecture audit for messy, fast-built, prototype-like, hard-to-maintain, or scaling codebases; use when the user asks what to improve before refactoring.
license: MIT
---

# Codebase Architecture Audit

Run an architecture audit: map the repo first, then identify structural risks and the smallest credible improvements. Do not refactor during the audit unless the user explicitly asks for implementation.

## Workflow

### 1. Discover the Repository

Inspect the file tree and project metadata before judging the architecture. Prefer `rg --files` and targeted reads over broad recursive dumps.

Check, when present:

- package, build, lock, and framework config files
- README and developer docs
- source entry points
- routing, API, data, UI, domain, and test directories
- environment/config conventions

Completion criterion: the stack, entry points, project shape, and available verification commands are known from files in the repo, not guessed.

### 2. Build the Map

Return a concise mental map before listing findings. Account for:

- framework and runtime
- routing and entry points
- main domains or features
- data access and external services
- API/server boundaries
- UI/component structure
- shared utilities and cross-cutting concerns
- test setup and quality gates

Completion criterion: every major code area that could own behavior has a named responsibility, or is explicitly called out as unclear.

### 3. Audit the Architecture

Look for pressure points:

- oversized files, components, routes, or modules
- mixed concerns, especially UI plus data access plus business rules
- unclear ownership of helpers, services, actions, models, or types
- duplicated logic, schemas, constants, or formatting
- weak domain boundaries
- fragile dependency direction
- server/client responsibility leaks
- unnecessary abstractions
- hardcoded environment, auth, permission, or business assumptions
- missing loading, empty, error, validation, or security paths
- inconsistent naming and folder conventions
- missing or ineffective tests around important behavior
- build, lint, typecheck, or dev workflow friction

Classify severity:

- Critical: correctness, security, deployability, or scaling is already blocked
- High: strong maintenance or change-risk pressure
- Medium: should be improved soon, but not urgent
- Low: cleanup, consistency, or local readability issue

Completion criterion: each finding names the evidence, impact, severity, and the smallest useful next step.

### 4. Propose Incremental Improvements

Prefer sequencing over sweeping redesign. Each recommendation should be safe to apply independently and should reduce one named risk.

For each proposed change, include:

- target files or areas
- intended boundary or responsibility after the change
- migration sequence
- verification command or manual check
- risk if postponed

Completion criterion: the user can choose one recommendation and start work without needing a second architecture pass.

### 5. Report Clearly

Lead with findings ordered by severity. Keep summaries brief and evidence-based.

Use this structure:

1. Architecture map
2. Findings
3. Recommended sequence
4. Verification gaps

Do not present speculative rewrites as required work. Mark assumptions explicitly when the repo does not provide enough evidence.

Completion criterion: the report separates observed facts from inference, and the recommended sequence starts with the lowest-risk high-value change.
