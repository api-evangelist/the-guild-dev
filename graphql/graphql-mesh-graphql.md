# GraphQL Mesh GraphQL API

GraphQL Mesh is a framework by The Guild that unifies REST, gRPC, SOAP, OData, Thrift, GraphQL, and database sources into a single GraphQL schema. When deployed as a gateway using `mesh start` or `mesh dev`, it exposes a GraphQL endpoint that reflects the composed schema derived from all configured sources.

## Endpoint

The gateway serves a GraphQL endpoint at `/graphql` by default (configurable via `serve.endpoint`). No single static endpoint URL applies — each deployment defines its own host and port (default port: `4000`).

## Gateway GraphQL Endpoint

- **Protocol:** GraphQL over HTTP (POST `/graphql`, GET for queries if `useGETForQueries` is enabled)
- **Subscriptions:** SSE (`/graphql`), WebSocket via `graphql-ws` (`WS`), or legacy `subscriptions-transport-ws` (`LEGACY_WS`)
- **Playground:** GraphiQL at `/graphql` when `serve.playground: true` (default in dev mode)
- **Health Check:** configurable via `serve.healthCheckEndpoint` (e.g., `/health`)
- **Batching:** supported via `serve.batchingLimit`

## Configuration Schema

The gateway is configured through `.meshrc.yaml` / `.meshrc.json` / `.meshrc.ts`. The schema for this configuration is formally published as a JSON Schema:

- **JSON Schema:** https://raw.githubusercontent.com/api-evangelist/graphql-mesh/refs/heads/main/json-schema/meshrc-configuration.json
- **NPM Package:** `@graphql-mesh/types` — TypeScript types for all configuration interfaces
- **Source:** https://github.com/ardatan/graphql-mesh/blob/master/packages/legacy/types/src/config.ts

## Key Configuration Types (as GraphQL SDL)

The GraphQL Mesh configuration is expressed as GraphQL SDL types in `/graphql/graphql-mesh-schema.graphql`.

## References

- **Documentation:** https://the-guild.dev/graphql/mesh/docs
- **Config Reference:** https://the-guild.dev/graphql/mesh/docs/config-reference
- **GitHub:** https://github.com/ardatan/graphql-mesh
- **NPM:** https://www.npmjs.com/package/@graphql-mesh/runtime
