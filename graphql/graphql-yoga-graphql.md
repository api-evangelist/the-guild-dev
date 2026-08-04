# GraphQL Yoga

GraphQL Yoga is a fully-featured, cross-platform GraphQL server from The Guild, built on top of graphql-js with an Envelop plugin system. It runs anywhere JavaScript runs — Node.js (Express, Fastify, Koa, Next.js, NestJS), Deno, Bun, Cloudflare Workers, and all major edge runtimes — using a single isomorphic Request/Response API.

The server supports the full GraphQL over HTTP specification, plus subscriptions via server-sent events (SSE), real-time via WebSockets with graphql-ws, file uploads via the multipart request spec, persisted documents, request batching, and automatic CORS handling. The plugin system (Envelop) hooks into every phase of the execution lifecycle.

**Endpoint:** Self-hosted — each deployment configures its own endpoint (default: /graphql)

**Documentation:** https://the-guild.dev/graphql/yoga-server/docs

**References:**

- Documentation: https://the-guild.dev/graphql/yoga-server/docs
- GettingStarted: https://the-guild.dev/graphql/yoga-server/docs/quick-start
- GitHub: https://github.com/dotansimha/graphql-yoga
- Plugins: https://the-guild.dev/graphql/yoga-server/docs/features/envelop-plugins
- Changelog: https://github.com/dotansimha/graphql-yoga/releases
