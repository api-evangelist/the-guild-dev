# GraphQL Inspector Rate Limits

GraphQL Inspector is a local CLI tool and open-source library. It does not operate as a hosted API service with per-request rate limits. All schema comparisons, document validations, and coverage analyses run locally or within your CI environment.

## CLI and Programmatic API

**Rate Limits:** None

The `@graphql-inspector/cli` package and programmatic API run in-process. There are no remote API calls subject to rate limiting. Performance is bounded only by local CPU and memory resources.

## GitHub Action

**Rate Limits:** Subject to GitHub Actions usage limits per your GitHub plan

When using GraphQL Inspector as a GitHub Action (`graphql-inspector/action`), execution is governed by GitHub's standard Actions runner limits:
- **Concurrent jobs:** Governed by your GitHub plan (Free: 20 concurrent, Pro+: higher)
- **Job execution time:** 6 hours maximum per job
- **Workflow run time:** 35 days maximum
- **API rate limits:** GitHub REST API requests made by the action count against your GitHub token's rate limit (5,000 requests/hour for authenticated users)

**Reference:** https://docs.github.com/en/actions/administering-github-actions/usage-limits-billing-and-administration

## GitHub Application

**Rate Limits:** None specific to GraphQL Inspector

The GraphQL Inspector GitHub App makes GitHub API calls using installation tokens, which are subject to GitHub's standard rate limits for GitHub Apps (15,000 requests/hour per installation). Under normal schema-check workflows, these limits are not approached.

## Introspection of Remote Endpoints

When using `graphql-inspector introspect` against a live GraphQL endpoint, any rate limits are those of the target GraphQL server, not GraphQL Inspector itself.

## Notes

Because GraphQL Inspector is stateless and runs locally (no cloud backend for schema diffing), there are no usage quotas, throttling policies, or metering in the core tool. Teams with very large schemas (thousands of types) may see slower diff performance due to algorithm complexity, but this is a local resource concern rather than a rate limit.
