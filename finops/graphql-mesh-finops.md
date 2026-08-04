# GraphQL Mesh FinOps

GraphQL Mesh is open-source software. Its cost profile differs substantially from SaaS API products: the framework itself has no licensing cost, but operating it incurs infrastructure and support costs that require active FinOps management.

## Cost Categories

### Infrastructure Costs

GraphQL Mesh is deployed on infrastructure you control. Cost drivers include:

| Cost Driver | Notes |
|---|---|
| Compute (CPU/Memory) | Node.js / Bun process for the gateway; scales with request volume and schema complexity |
| Egress / Bandwidth | Responses returned to consumers; upstream calls to source APIs |
| Container Orchestration | ECS, Kubernetes, Cloud Run, etc. |
| Serverless Invocations | AWS Lambda, Cloudflare Workers, Google Cloud Functions (per-invocation billing) |
| Caching Layer | Redis or in-memory cache to reduce upstream calls |
| Observability | Prometheus, Datadog, New Relic, Sentry ingestion costs |

### Upstream API Costs

GraphQL Mesh federates multiple upstream APIs. Each upstream may have its own usage-based billing:

- REST / OpenAPI sources — charges from the upstream provider per request
- Database connections — RDS, Cloud SQL, MongoDB Atlas costs
- Third-party APIs — billed independently by each vendor

### Support and Consulting

The Guild offers paid enterprise support and consulting. These are negotiated contracts rather than metered usage costs.

### Hive Gateway (Cloud)

If using The Guild's hosted Hive Gateway platform, you pay based on usage (schema pushes, operations, observability data). See https://the-guild.dev/graphql/hive/pricing.

## Cost Optimization Strategies

- **Enable response caching** (`@graphql-mesh/plugin-response-cache`) to reduce redundant upstream calls and associated costs.
- **Use DataLoader / batching** to collapse N+1 upstream requests into single batch calls.
- **Right-size compute:** Measure peak and average CPU/memory usage; scale down over-provisioned instances.
- **Serverless for bursty traffic:** AWS Lambda or Cloudflare Workers eliminate idle compute cost during low-traffic periods.
- **Monitor upstream call counts** per source to detect unexpected cost spikes from schema changes or new consumers.
- **Implement query depth and complexity limits** to prevent runaway queries that inflate upstream costs.

## Allocation and Tagging

- Tag gateway deployments with team, environment (dev/staging/prod), and application to enable chargeback or showback.
- Use OpenTelemetry spans to attribute upstream costs to specific GraphQL operations and consumers.
- Report cost per query/operation to engineering teams monthly.

## Unit Economics

| Metric | Formula |
|---|---|
| Cost per 1K gateway requests | Total infra cost / (requests / 1000) |
| Cost per upstream call | Total upstream API cost / upstream calls |
| Cache hit rate | Cached responses / total requests (target > 60%) |

## References

- GraphQL Mesh docs: https://the-guild.dev/graphql/mesh/docs
- Hive Gateway pricing: https://the-guild.dev/graphql/hive/pricing
- FinOps Foundation Framework: https://www.finops.org/framework/
- FOCUS Specification v1.3: https://focus.finops.org/focus-specification/v1-3/

*Last updated: 2026-06-14*
