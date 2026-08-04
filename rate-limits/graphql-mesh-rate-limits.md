# GraphQL Mesh Rate Limits

GraphQL Mesh is an open-source, self-hosted framework. As such, rate limiting is not enforced by the project itself — it is the responsibility of the operator deploying the gateway.

## Self-Hosted Deployments

When running GraphQL Mesh as a self-hosted gateway, rate limits depend entirely on the infrastructure you provision and any middleware or plugins you configure.

### Built-in Options

GraphQL Mesh supports configuring rate limiting through plugins and middleware in your `.meshrc.yaml` configuration:

- **Response Caching:** Reduce upstream load with built-in caching plugin (`@graphql-mesh/plugin-response-cache`)
- **Operation Limiting:** Restrict query depth and complexity via `@graphql-mesh/plugin-operation-field-count-limit` and similar plugins
- **Upstream Throttling:** Configure per-source request throttling when wrapping rate-limited upstream APIs

### Recommended Patterns

| Concern | Approach |
|---|---|
| Protect upstream REST APIs | Configure retry and throttle in OpenAPI handler options |
| Limit consumer query volume | Add rate-limit middleware (e.g., graphql-rate-limit) at the Yoga layer |
| Prevent query abuse | Enable query depth limiting and field count limits |
| Observe traffic | Integrate Prometheus, OpenTelemetry, or Sentry plugins |

## Hive Gateway (Cloud)

If using The Guild's hosted Hive Gateway (which builds on GraphQL Mesh v1), rate limits are set per plan. See https://the-guild.dev/graphql/hive/pricing for current plan-level limits.

## Upstream API Rate Limits

GraphQL Mesh acts as a proxy to upstream services. Each upstream source (REST, gRPC, SOAP, database) has its own rate limits set by the upstream provider. GraphQL Mesh does not override or bypass those limits.

## Notes

- Rate limits described here reflect self-hosted architecture patterns as of June 2026.
- For Hive Gateway cloud rate limits, consult The Guild's official documentation and pricing page.
- The Guild provides enterprise consulting for organizations that need help designing rate-limit and quota strategies.
