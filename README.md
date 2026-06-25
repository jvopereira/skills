# Agent Skills

Reusable coding-agent skills for codebase maintenance.

## Skills

| Skill | Description |
|---|---|
| [`codebase-architecture-audit`](skills/codebase-architecture-audit/SKILL.md) | Architecture audit for messy, fast-built, prototype-like, hard-to-maintain, or scaling codebases; use when the user asks what to improve before refactoring. |

## Install

Install every skill in this repository:

```bash
npx skills add jvopereira/skills
```

Install one specific skill:

```bash
npx skills add jvopereira/skills --skill codebase-architecture-audit
```

General form:

```bash
npx skills add your-github-username/your-skills --skill your-skill-name
```

## Repository Structure

```text
.
├── README.md
└── skills/
    └── codebase-architecture-audit/
        └── SKILL.md
```
