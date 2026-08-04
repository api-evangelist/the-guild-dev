# GraphQL Scalars FinOps

GraphQL Scalars is a free, open-source MIT-licensed library. Direct costs of using the library are zero. This document covers the full cost surface for teams integrating graphql-scalars into production systems.

## Direct Costs

| Item | Cost |
|------|------|
| graphql-scalars npm package | Free (MIT) |
| Library runtime usage | Free (no metering) |
| Source code (GitHub) | Free |
| Documentation access | Free |

## Indirect / Infrastructure Costs

Costs may arise from the surrounding infrastructure where graphql-scalars is deployed:

### Compute
- Each scalar's parse/serialize/parseLiteral functions add negligible CPU overhead
- No meaningful compute cost increase expected in typical GraphQL server deployments
- Validation-heavy scalars (e.g., EmailAddress, UUID, IBAN) add microsecond-level latency per field

### Bundle Size
- Full import of all scalars adds ~45–60 KB minified to a server bundle (not typically a concern for Node.js servers)
- Tree-shaking via named imports reduces bundle footprint for edge/serverless deployments
- Serverless cold-start impact is minimal when importing only required scalars

### CI/CD
- npm install time is negligible (small package, minimal transitive dependencies)
- No additional build steps required

## Related Service Costs — GraphQL Hive

Teams using The Guild's GraphQL Hive alongside graphql-scalars should plan for:

| Usage Level | Estimated Monthly Cost |
|-------------|----------------------|
| < 1M operations | Free (Hobby tier) |
| 1M–10M operations | Pay-per-operation (Pro tier) |
| 10M+ operations | Contact The Guild for Enterprise pricing |

Hive pricing reference: https://the-guild.dev/graphql/hive/pricing

## Cost Optimization Tips

1. **Import only needed scalars** — use named imports (`import { DateTimeResolver } from 'graphql-scalars'`) rather than the full package default to enable tree-shaking
2. **Cache resolver instances** — instantiate scalar resolvers once at server startup, not per-request
3. **Monitor Hive usage** — if using GraphQL Hive, set operation budget alerts to avoid unexpected overage on the Pro tier
4. **Consolidate scalar validation** — avoid running the same validation logic in both the GraphQL layer and separate application layers to reduce redundant compute

## Summary

For the vast majority of teams, graphql-scalars carries **zero licensing or runtime cost**. Cost planning should focus on the surrounding compute, observability, and schema management infrastructure rather than the library itself.
