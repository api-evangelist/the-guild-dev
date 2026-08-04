# GraphQL Hive GraphQL API

GraphQL Hive exposes a public GraphQL API for programmatic management of organizations, projects, targets, and schema registries. Developers use this API to automate schema publishing workflows, retrieve usage analytics, manage access tokens, track breaking changes, and administer team members without relying on the CLI or web console. The API covers the full lifecycle of GraphQL schema management including schema version history, schema checks, CDN access tokens, and federation contract configuration.

The API is available as a single GraphQL endpoint at `https://api.graphql-hive.com/graphql`. Authentication is performed via Bearer tokens in the `Authorization` header. Hive issues two token formats: service/target tokens (prefixed `hvo1/`) for schema publishing operations and organization-scoped access tokens for management operations. Tokens are created from the Hive console under Settings for the relevant target or organization.

The schema is organized around a hierarchy of Organization → Project → Target. Query fields resolve a single entity by reference (by ID or by slug selector). Mutations cover project and target creation, member role management, CDN access token lifecycle, schema composition configuration, app deployment retirement, and conditional breaking-change configuration. Usage analytics are surfaced through OperationsStats and ClientStats on the Target type.

**Endpoint:** https://api.graphql-hive.com/graphql

**Documentation:** https://the-guild.dev/graphql/hive/docs/graphql-api/access-token-management

**References:**

- Documentation: https://the-guild.dev/graphql/hive/docs
- GettingStarted: https://the-guild.dev/graphql/hive/docs/get-started/first-steps
