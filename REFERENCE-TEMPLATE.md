# Reference Repositories

This project includes reference repositories as git subtrees in `repos/` for pattern discovery and API lookup.

## Effect (`repos/effect/`)

The core Effect library for functional TypeScript.

### Core Package (`repos/effect/packages/effect/src/`)

Essential modules:

| Module | Path | Use For |
|--------|------|---------|
| **Effect** | `Effect.ts` | Core effect type, operations |
| **Schema** | `Schema.ts` | Validation, encoding/decoding |
| **Context** | `Context.ts` | Dependency injection |
| **Layer** | `Layer.ts` | Service composition |
| **Data** | `Data.ts` | Value objects, tagged unions |
| **Brand** | `Brand.ts` | Branded types (IDs, etc.) |
| **Either** | `Either.ts` | Error handling |
| **Option** | `Option.ts` | Optional values |
| **Match** | `Match.ts` | Pattern matching |
| **BigDecimal** | `BigDecimal.ts` | Precise decimal arithmetic |
| **DateTime** | `DateTime.ts` | Date/time handling |
| **Stream** | `Stream.ts` | Streaming data |
| **Config** | `Config.ts` | Configuration |
| **Fiber** | `Fiber.ts` | Concurrent execution |

### Search Patterns

```bash
# Find service definitions
grep -r "Context.Tag" repos/effect/packages/effect/src/

# Find schema examples
grep -r "Schema.Struct" repos/effect/packages/effect/src/

# Find branded type examples
grep -r "Brand.nominal" repos/effect/packages/effect/src/

# Find Layer patterns
grep -r "Layer.effect" repos/effect/packages/effect/src/

# Find tagged error examples
grep -rn "TaggedError" repos/effect/packages/effect/src/

# Find Effect.gen usage in tests
grep -rn "Effect.gen" repos/effect/packages/effect/test/ | head -20
```

### SQL Packages (`repos/effect/packages/sql*/`)

| Package | Path | Description |
|---------|------|-------------|
| **sql** | `repos/effect/packages/sql/` | Core SQL abstractions |
| **sql-pg** | `repos/effect/packages/sql-pg/` | PostgreSQL client |

```bash
# Find repository patterns
grep -r "SqlClient" repos/effect/packages/sql/src/

# Find query patterns
grep -rn "sql\`" repos/effect/packages/sql*/src/
```

### Platform Packages (`repos/effect/packages/platform*/`)

| Package | Path | Description |
|---------|------|-------------|
| **platform** | `repos/effect/packages/platform/` | Core platform abstractions |
| **platform-node** | `repos/effect/packages/platform-node/` | Node.js runtime |

Key modules: `HttpClient.ts`, `HttpServer.ts`, `FileSystem.ts`, `Terminal.ts`

### Testing (`repos/effect/packages/vitest/`)

```bash
# Find test utility patterns
grep -rn "it.effect\|it.live\|it.scoped\|it.layer" repos/effect/packages/vitest/src/

# Find test examples
grep -rn "describe\(" repos/effect/packages/vitest/test/
```

### Finding Tests (Best Source of Examples)

```bash
# Effect core tests — rich examples of every API
ls repos/effect/packages/effect/test/

# Find specific API usage in tests
grep -rn "Schema.Class" repos/effect/packages/effect/test/
grep -rn "Layer.effect" repos/effect/packages/effect/test/
```

---

## Customization Notes

Adapt this template for your project:

1. **Remove packages you don't use** — if you don't use `@effect/sql`, drop those sections
2. **Add project-specific search patterns** — e.g., patterns matching your domain model style
3. **Add other subtrees** — if you add TanStack Router, Drizzle, etc. as subtrees, document them here too
4. **Keep the search patterns updated** — as your project evolves, add patterns that help agents find relevant code
