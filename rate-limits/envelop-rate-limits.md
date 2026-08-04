# Envelop Rate Limits

Envelop is a client-side GraphQL plugin library running inside your own infrastructure. It does not impose network-level rate limits — there is no hosted API to call and no quota enforced by The Guild on library usage.

## Rate Limiting Capabilities Within Envelop

Envelop provides several mechanisms to implement rate limiting in your own GraphQL server:

### @envelop/rate-limiter Plugin

The `@envelop/rate-limiter` plugin integrates with `graphql-rate-limit` to add field-level or operation-level rate limiting.

```bash
npm i @envelop/rate-limiter
```

Configuration options allow you to specify:
- Window duration (e.g., 60 seconds)
- Max requests per window (e.g., 100 requests)
- Identity function to derive the rate-limit key (e.g., user ID, IP address)
- Custom error message on limit exceeded

### useResourceLimitations Plugin

The `useResourceLimitations` built-in plugin allows you to enforce:
- Maximum query depth
- Maximum query complexity (field weighting)
- Maximum number of aliases in a single query
- Maximum number of directives

### maxDepthPlugin

Restricts the nesting depth of incoming GraphQL queries to prevent deeply recursive queries from consuming excessive server resources.

## Downstream Service Limits

If you use Envelop plugins that connect to third-party services, those services impose their own rate limits:

| Plugin | Service | Notes |
|---|---|---|
| `@envelop/sentry` | Sentry.io | Subject to your Sentry plan limits |
| `@envelop/hive` | GraphQL Hive | Subject to your Hive plan limits |
| `@envelop/opentelemetry` | Your OTLP backend | Varies by backend |
| `@envelop/statsd` | Your StatsD server | No external limit |

## npm Registry

npm does not impose rate limits on package downloads under normal usage. Authenticated publish operations are subject to standard npm rate limits.
