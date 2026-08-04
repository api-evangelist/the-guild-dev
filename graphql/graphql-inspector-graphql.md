# GraphQL Inspector GraphQL API

GraphQL Inspector is a CLI tool and GitHub Action for schema change detection and validation — it consumes GraphQL schemas rather than exposing a live GraphQL endpoint. There is no public hosted GraphQL API for GraphQL Inspector itself.

This schema documents the **vocabulary** GraphQL Inspector uses internally: the type system of its programmatic (`@graphql-inspector/core`) package, which defines how schema changes, criticality levels, coverage reports, similar-type detection, and validation results are modelled. This is the schema any tool integrating `@graphql-inspector/core` works against.

**Package:** @graphql-inspector/core (npm)
**Endpoint:** N/A — library/CLI tool, no hosted GraphQL endpoint
**Documentation:** https://the-guild.dev/graphql/inspector/docs

## Key Concepts

- **diff** — Compares two `GraphQLSchema` objects and returns an array of `Change` objects, each tagged with a `CriticalityLevel` (BREAKING, DANGEROUS, NON_BREAKING).
- **coverage** — Given a schema and a set of operation sources, returns a `SchemaCoverage` report showing how many types and fields are exercised.
- **similar** — Finds types in a schema whose structure is similar to a named type (Dice-coefficient comparison), returning a `SimilarMap`.
- **validate** — Validates operation documents against a schema, returning `InvalidDocument` errors.

## GitHub Actions Inputs / Outputs

The `graphql-inspector` GitHub Action (`action.yml`) exposes these typed inputs:
- `schema` (required) — Ref:path or URL to the "after" GraphQL schema
- `endpoint` — URL of the live "before" GraphQL API
- `name` — Check name label (default: "GraphQL Inspector")
- `annotations` — Enable inline PR annotations (default: true)
- `fail-on-breaking` — Fail CI on breaking changes (default: true)
- `approve-label` — PR label that marks breaking changes as intentional (default: "approved-breaking-change")
- `github-token` — GitHub token (default: `${{ github.token }}`)
- `experimental_merge` — Merge PR branch with target before comparing (default: true)
- `rules` — Multiline YAML list of built-in rule names to apply
- `onUsage` — Path to a JS module implementing the `considerUsage` callback

Output:
- `changes` — Total number of detected changes (integer)

## Authentication

None. The GitHub Action uses the standard `github.token`. The CLI tool requires no authentication for local schema files; for live endpoints it passes custom headers via `--left-header` / `--right-header` flags.

**References:**
- Documentation: https://the-guild.dev/graphql/inspector/docs
- Getting Started: https://the-guild.dev/graphql/inspector/docs/installation
- GitHub Repository: https://github.com/graphql-hive/graphql-inspector
- npm Package: https://www.npmjs.com/package/@graphql-inspector/core
- GitHub Action Marketplace: https://github.com/marketplace/graphql-inspector
- Diff Docs: https://the-guild.dev/graphql/inspector/docs/essentials/diff
- Coverage Docs: https://the-guild.dev/graphql/inspector/docs/essentials/coverage
- Validate Docs: https://the-guild.dev/graphql/inspector/docs/essentials/validate
