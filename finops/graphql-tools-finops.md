# GraphQL Tools FinOps

GraphQL Tools is MIT-licensed open-source software. Direct licensing or subscription costs are zero. Financial considerations are limited to infrastructure and operational overhead.

## Direct Costs

| Item | Cost |
|------|------|
| npm package licenses | Free (MIT) |
| Source code access | Free (GitHub public repo) |
| Community support | Free (GitHub Issues / Discussions) |

## Indirect / Operational Costs

### Server Infrastructure
Schema stitching and remote executor patterns add network hops between your gateway and upstream GraphQL services. Factor in:
- Additional compute for the stitching gateway layer
- Egress costs for inter-service traffic (especially relevant in cloud environments)
- Memory overhead of caching merged schemas at runtime

### The Guild Professional Services
If your team engages The Guild for consulting, workshops, or long-term support contracts, budget accordingly. Rates are negotiated directly — contact https://the-guild.dev/contact for a quote.

### GraphQL Hive (Optional Managed Layer)
Teams using GraphQL Hive as a schema registry and observability platform alongside GraphQL Tools should budget for Hive's commercial tiers. Hive introduces:
- Schema registry storage costs
- Observability data retention costs
- Gateway request volume costs

See https://the-guild.dev/graphql/hive for current Hive pricing.

## Cost Optimization Tips

- Use `@graphql-tools/executor-http` with HTTP keep-alive and batching to reduce per-request overhead in stitched gateways.
- Cache the merged schema in memory rather than rebuilding on every request.
- Monitor upstream service latency independently to isolate cost drivers in a stitched architecture.
- Evaluate whether full schema stitching or simple schema merging fits your use case — merging is lower overhead when all schemas are local.
