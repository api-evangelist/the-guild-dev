# GraphQL Yoga Rate Limits

## No Built-In Rate Limits

GraphQL Yoga is a self-hosted library. It does not impose any default rate limits on incoming requests. All rate-limiting decisions are the responsibility of the application developer or the infrastructure in front of the server.

## Implementing Rate Limits

Developers can add rate limiting at several layers:

### Plugin Layer (Recommended)
GraphQL Yoga's plugin system supports request-level and operation-level throttling. Community and third-party plugins are available for common rate-limiting patterns:

- **`@graphql-yoga/plugin-response-cache`** — caches responses and reduces redundant execution, which can indirectly reduce load.
- **`graphql-rate-limit`** — a schema-directive-based rate limiter that can be wired into Yoga's plugin lifecycle.
- Custom `onRequest` / `onExecute` plugins can count tokens, depth, or complexity per client.

### Reverse Proxy / Edge Layer
Most production deployments place GraphQL Yoga behind a reverse proxy or CDN that enforces rate limits before requests reach the application:

- **Nginx / HAProxy** — `limit_req` / `stick-table` directives
- **Cloudflare** — rate limiting rules (if deployed to Cloudflare Workers)
- **AWS API Gateway** — usage plans and throttle settings
- **Vercel / Netlify** — edge middleware

### Query Complexity / Depth Limiting
To guard against expensive GraphQL queries, GraphQL Yoga supports complexity and depth validation rules via plugins such as:

- **`graphql-query-complexity`**
- **`graphql-depth-limit`**

These can be registered as validation rules in the Yoga configuration.

## References

- GraphQL Yoga Plugins: https://the-guild.dev/graphql/yoga-server/docs/features/plugins
- Response Cache Plugin: https://the-guild.dev/graphql/yoga-server/docs/features/response-caching
- GraphQL Armor (security + rate limiting): https://escape.tech/graphql-armor/
