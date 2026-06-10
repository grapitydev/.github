# Grapity — Agent Context

## Always read before working

- `docs/GENERAL_GUIDELINES.md` — engineering conventions that apply across all packages
- `docs/API_DESIGN_GUIDELINES.md` — API design decisions (open enums, contract serving, error shapes)

Each layer has its own architecture doc. Read the one relevant to the current work:

- `docs/l1/architecture.md` — L1 Registry: all recorded decisions, data model, routes, semver strategy

## Repo structure

```
docs/                   Cross-cutting docs and architecture decisions
docs/{layer}/           Per-layer architecture doc and PlantUML diagrams
core/                   @grapity/core — shared interfaces and types
registry/               @grapity/registry — L1: API contract registry server
cli/                    @grapity/cli — Commander CLI, HTTP client
grapity.dev/            Marketing site
```

## Working on a feature

Every feature follows this order before writing any code:

1. **Diagram first.** If the feature introduces or changes a flow, update or create the relevant PlantUML diagram under `docs/{layer}/diagrams/` before implementation. Diagrams are the design artifact — code follows them.

2. **Plan test scenarios.** Before implementing, identify: happy paths, error paths, and edge cases. Write the failing tests first.

3. **Update the contract.** If the layer exposes an API, update its OpenAPI/AsyncAPI spec first and regenerate types. If it doesn't, update the relevant interface or data model definition. The contract is the source of truth.

4. **Implement.** Code follows the diagram, the contract, and the test scenarios — not the other way around.

## Key constraints

- Never commit or push unless explicitly asked
- Use open strings (not closed enums) for any field whose value set may grow — see `docs/API_DESIGN_GUIDELINES.md`

## Definition of done

A task is not finished until all of the following pass — no exceptions, including one-line changes:

```bash
# Typecheck every affected package (change in core means checking registry and cli too)
cd core && bun run typecheck
cd registry && bun run typecheck
cd cli && bun run typecheck

# Full test suite
cd registry && bun test

# Verify the built package works (packages with bundling)
cd registry && bun run build
cd cli && bun run build
```

Run these before reporting the task as complete. If any check fails, fix it first.

For packages that bundle assets (migration folders, static files), also verify the bundled output resolves those assets correctly after `bun run build`. See `docs/GENERAL_GUIDELINES.md` for the asset path convention.

## Keeping docs current

Docs go stale fast. After any feature or decision:

- Update the relevant layer architecture doc if a decision was made or reversed
- Update or add a diagram if a flow changed
- Update `docs/API_DESIGN_GUIDELINES.md` if a new cross-cutting API pattern was established
- Update `docs/GENERAL_GUIDELINES.md` if a new engineering convention was agreed

If a doc is out of date, fix it as part of the same change — never leave stale documentation behind.
