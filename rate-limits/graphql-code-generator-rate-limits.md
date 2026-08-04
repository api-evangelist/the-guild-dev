# GraphQL Code Generator Rate Limits

## Overview

GraphQL Code Generator is a CLI tool that runs locally or in CI/CD pipelines. Because it executes on-premises or in your own build environment, there are no API rate limits imposed by The Guild on the core codegen tool itself.

## CLI / Local Execution

- No rate limits — runs entirely in your local environment or CI runner
- Processing speed depends on schema size, number of operations, and available CPU/memory
- Large schemas (1,000+ types) or projects with many operation documents may require tuning via the `--max-parallel-generators` option in the config

## npm Registry

When installing `@graphql-codegen/*` packages, standard npm registry rate limits apply:
- Unauthenticated requests: npm public registry policies (generally 200 requests per minute per IP)
- Authenticated (npm account): higher limits per npm's standard terms
- CI environments: use lock files (`package-lock.json`, `yarn.lock`, `pnpm-lock.yaml`) and caching to avoid re-fetching packages on every run

## GraphQL Hive (Optional Managed Service)

If using GraphQL Hive's schema registry alongside codegen, rate limits vary by plan:

| Plan       | Schema Publishes | Usage Reports | API Requests |
|------------|-----------------|---------------|--------------|
| Hobby      | Limited          | Limited       | Limited      |
| Pro        | Higher limits    | Higher limits | Higher limits|
| Enterprise | Custom / Unlimited | Custom      | Custom       |

See https://the-guild.dev/graphql/hive#pricing for current Hive plan limits.

## Remote Schema Fetching

If your codegen config fetches schemas from a remote GraphQL endpoint at generation time (using `schema: https://...`):
- Rate limits are governed by the **target GraphQL API**, not by The Guild
- Use local schema files or introspection caching where possible in high-frequency CI environments

## Notes

- There are no known throttling mechanisms in the open-source codegen CLI itself.
- Rate limit concerns are primarily relevant to downstream services (npm, remote schema endpoints, GraphQL Hive).
