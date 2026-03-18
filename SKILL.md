---
name: init-effect-subtree
description: Set up the Effect-TS source repo as a git subtree so AI agents can learn Effect patterns from actual source code instead of docs or skills. Use when user wants to add Effect to a project for AI training, improve AI coding with Effect, set up Effect reference repo, or mentions "git subtree" with Effect.
---

# Effect Subtree Setup

Train AI agents to write excellent Effect-TS code by adding the Effect source repo as a git subtree. This is the approach recommended by Michael Arnaldi (creator of Effect) — source code outperforms docs and skills for LLM coding quality (proven via evals).

## Why source code beats docs

- LLMs are exceptional at understanding code — much better than prose documentation
- The Effect repo contains canonical patterns, real tests, and type-level examples
- Docs lose nuance; source code is the ground truth
- Skills are for repetitive tasks, not for teaching a library

## Quick start

### Step 1: Add the Effect repo as a git subtree

```bash
git subtree add --prefix=repos/effect https://github.com/Effect-TS/effect.git main --squash
```

This places the full Effect monorepo under `repos/effect/`. The `--squash` flag collapses its history into one commit.

### Step 2: Create a reference guide

Create `specs/reference/reference-repos.md` (or similar) that maps the subtree structure to your project's needs. This is a navigation aid for the AI — it tells the agent *where to look* for specific patterns.

Include:

- **Module index** — table of key modules and their paths (Schema, Layer, Effect, Context, etc.)
- **Search patterns** — grep/ripgrep commands for finding common patterns (service definitions, branded types, error handling)
- **Package map** — which packages are relevant (`packages/effect/src/`, `packages/sql/`, `packages/platform/`, `packages/vitest/`)

See [REFERENCE-TEMPLATE.md](REFERENCE-TEMPLATE.md) for a complete template.

### Step 3: Write an Effect guide for your project

Create a project-specific Effect guide (e.g., `specs/guides/effect-guide.md`) with:

- **Critical rules** — what to never do (no `any`, no type casts, no `catchAllCause`, no `disableValidation`)
- **Preferred patterns** — Schema.Class for entities, Schema.TaggedError for errors, branded types for IDs
- **SQL patterns** — if using @effect/sql
- **Testing patterns** — @effect/vitest usage
- **Layer composition** — how your project wires services

This guide is *project-specific* — it encodes your team's conventions on top of Effect's patterns.

### Step 4: Reference in your agent instructions

Add to your project's `AGENTS.md` (or `AGENTS.md`, `COPILOT.md`, `.cursorrules`, etc.):

```markdown
## Reference Repositories

repos/effect/ contains the Effect-TS source code as a git subtree.
When you need to understand an Effect API, look at the actual source code
in repos/effect/ — do NOT rely on training data or documentation.

See specs/reference/reference-repos.md for navigation.
See specs/guides/effect-guide.md for project conventions.
```

## Updating the subtree

Pull latest changes periodically:

```bash
git subtree pull --prefix=repos/effect https://github.com/Effect-TS/effect.git main --squash
```

## Key directories in the Effect repo

| Path | Contains |
|------|----------|
| `packages/effect/src/` | Core library (Effect, Schema, Layer, Context, etc.) |
| `packages/effect/test/` | Tests — excellent examples of API usage |
| `packages/sql/src/` | SQL abstractions |
| `packages/sql-pg/src/` | PostgreSQL client |
| `packages/platform/src/` | HTTP, filesystem, terminal |
| `packages/vitest/src/` | Test utilities (it.effect, it.layer, etc.) |

## What to tell the agent

The critical instruction for your agent instructions file (`AGENTS.md`, `AGENTS.md`, etc.):

> When you have a question about Effect APIs, search the source code in `repos/effect/`.
> When you need examples, extract them from tests in `repos/effect/packages/*/test/`.
> Do NOT guess at Effect APIs from training data — look at the actual code.

## Checklist

- [ ] Added Effect repo as git subtree under `repos/effect/`
- [ ] Created reference guide mapping subtree structure
- [ ] Created project-specific Effect patterns guide
- [ ] Updated AGENTS.md to point agents at the subtree
- [ ] Verified agent can find patterns via grep in repos/effect/
