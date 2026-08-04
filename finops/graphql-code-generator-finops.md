# GraphQL Code Generator FinOps

## Overview

GraphQL Code Generator is open-source software with no licensing cost. FinOps considerations focus on the infrastructure and tooling costs associated with running codegen in CI/CD pipelines, managing dependencies, and optionally using the GraphQL Hive managed platform.

## Direct Costs

### Core Tool
- **License cost: $0** — MIT-licensed, freely available on npm
- No per-seat, per-schema, or per-generation fees

### GraphQL Hive (Optional)
If your team adopts the GraphQL Hive managed platform for schema registry and observability:
- **Hobby tier**: Free, suitable for small/personal projects
- **Pro tier**: Paid monthly subscription — see https://the-guild.dev/graphql/hive#pricing
- **Enterprise tier**: Custom pricing — contact The Guild

## Indirect / Infrastructure Costs

### CI/CD Compute
- Codegen runs as a build step; cost is embedded in your CI runner charges (GitHub Actions minutes, CircleCI credits, etc.)
- Typical codegen runs complete in seconds; for large mono-repos with many schemas, runs may take 1–3 minutes
- Optimize by caching `node_modules` and only regenerating when schema/operation files change (use `--watch` in local dev; cache hashes in CI)

### npm Package Management
- All `@graphql-codegen/*` packages are free from the npm public registry
- Private registries (Artifactory, Verdaccio, GitHub Packages) may incur storage/bandwidth costs depending on your setup

### Developer Time
- Initial setup: 1–4 hours depending on project complexity
- Ongoing maintenance: low; codegen config rarely changes unless adding new plugins or updating GraphQL schema structure significantly
- Plugin upgrades: The Guild publishes major versions periodically; budget time for migration when major versions release

## Cost Optimization Tips

1. **Cache generated files** in CI to avoid re-running codegen when no schema/operations changed.
2. **Use `codegen.ts` watch mode** locally to avoid manual regeneration during development.
3. **Pin plugin versions** with lock files to prevent unexpected upgrades that could require migration work.
4. **Scope plugins** — only install and run plugins for frameworks actually used in your project; avoid unnecessary plugin overhead.
5. **Self-host Hive** (Enterprise tier) if your data residency or volume requirements make the managed service cost-prohibitive.

## Summary Table

| Cost Item                    | Typical Cost        | Notes                                      |
|-----------------------------|---------------------|--------------------------------------------|
| GraphQL Code Generator CLI  | $0                  | MIT open source                            |
| npm packages                | $0                  | Public registry                            |
| GraphQL Hive Hobby          | $0                  | Limited features                           |
| GraphQL Hive Pro            | Paid (see website)  | Schema registry + observability            |
| GraphQL Hive Enterprise     | Custom              | Self-host or managed with SLA              |
| CI compute (codegen step)   | Varies              | Embedded in existing CI costs; seconds/run |
