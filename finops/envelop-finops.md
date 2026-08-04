# Envelop FinOps

Envelop is a free, open-source MIT-licensed npm library. There is no cost to download, install, or run Envelop in your own infrastructure.

## Direct Cost: $0

- No licensing fees
- No usage-based billing
- No API call charges
- No seat-based pricing

## Indirect / Operational Costs

While Envelop itself is free, using it in production may involve costs from the ecosystem around it:

### Infrastructure

Envelop runs inside your GraphQL server process. Any cost associated with compute, memory, or network is absorbed by your existing infrastructure bill (AWS, GCP, Azure, Fly.io, etc.). Envelop's overhead is minimal — it adds thin wrapper functions around GraphQL.js execution.

### Observability Plugins

| Plugin | Vendor | Typical Cost Driver |
|---|---|---|
| `@envelop/sentry` | Sentry | Events per month (free tier: 5k events/mo) |
| `@envelop/hive` | GraphQL Hive | Operations collected (free tier available) |
| `@envelop/opentelemetry` | Your OTLP backend | Spans/traces per month (varies by vendor) |
| `@envelop/statsd` | Self-hosted StatsD | Compute cost only |

### GraphQL Hive Integration

If you use the `@envelop/hive` plugin to send usage telemetry to GraphQL Hive:
- Free hobby tier: included with Hive's free plan
- Paid plans scale with number of operations reported
- Pricing: https://the-guild.dev/graphql/hive/pricing

### Engineering Cost

The main FinOps consideration is engineering time spent:
- Selecting and configuring plugins
- Writing custom plugins
- Maintaining plugin versions as Envelop releases updates

## Cost Optimization Tips

1. Use `@envelop/parser-cache` and `@envelop/validation-cache` to reduce CPU time per request and lower compute costs.
2. Use `useResourceLimitations` to prevent runaway queries that inflate compute bills.
3. Sample observability plugins (Sentry, OpenTelemetry) at a fraction of traffic to reduce vendor costs.
4. Pin Envelop plugin versions in `package.json` to avoid unexpected breaking changes during upgrades.

## Budget Estimate

For a typical production GraphQL API using Envelop:

| Item | Estimated Monthly Cost |
|---|---|
| Envelop library | $0 |
| Sentry (hobby) | $0–$26 |
| GraphQL Hive (hobby) | $0 |
| OpenTelemetry backend (e.g., Grafana Cloud) | $0–$50 |
| Additional compute overhead | Negligible |
