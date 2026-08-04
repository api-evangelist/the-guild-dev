# GraphQL Scalars Rate Limits

GraphQL Scalars is a client-side open-source library — it runs entirely within the consuming application's runtime and has **no API endpoints, no network calls, and no rate limits** of any kind.

## Library Usage

- All scalar validation and serialization logic executes locally in the application process
- No requests are made to The Guild's servers during normal operation
- No authentication tokens or API keys are required
- Throughput is bounded only by the host application's CPU and memory

## npm Registry

Installing or updating the package via npm/yarn/pnpm is subject to the npm registry's standard policies:

- **Anonymous requests:** 300 requests per minute per IP (npm default)
- **Authenticated requests:** 1,800 requests per minute per account

These limits apply only to installation/CI pipelines, not to runtime usage of the library.

## GitHub API (Source Access)

Accessing the source repository at https://github.com/graphql-hive/graphql-scalars programmatically is subject to GitHub's standard rate limits:

- **Unauthenticated:** 60 requests per hour per IP
- **Authenticated (personal token):** 5,000 requests per hour
- **GitHub Actions:** 1,000 requests per hour per repository

## Related Service — GraphQL Hive

If using The Guild's **GraphQL Hive** platform (schema registry / observability), operation ingestion limits apply per plan:

| Plan | Operation Limit |
|------|----------------|
| Hobby | 1,000,000 operations/month |
| Pro | Pay-as-you-go beyond free tier |
| Enterprise | Custom negotiated limits |

Reference: https://the-guild.dev/graphql/hive/pricing

## Summary

There are no rate limits to be aware of for standard use of the graphql-scalars library itself. Rate limits only apply to auxiliary infrastructure (npm registry, GitHub API, GraphQL Hive platform).
