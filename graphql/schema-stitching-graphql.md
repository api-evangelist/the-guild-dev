# Schema Stitching GraphQL API

Schema Stitching is a GraphQL technique for combining multiple GraphQL schemas into a single unified API gateway. The @graphql-tools/stitch package creates a combined proxy layer that delegates requests through to underlying service APIs, supporting type merging, stitching directives, and automated query planning comparable to Apollo Federation.

## Schema Stitching

**Documentation:** https://the-guild.dev/graphql/stitching

**References:**

- Documentation: https://the-guild.dev/graphql/stitching/docs
- GettingStarted: https://the-guild.dev/graphql/stitching/docs/getting-started

## GraphQL Mesh

GraphQL Mesh allows stitching together multiple data sources including REST APIs, databases, and other GraphQL APIs into a single unified GraphQL schema. It applies schema stitching techniques to transform and federate heterogeneous data sources.

**Documentation:** https://the-guild.dev/graphql/mesh

**References:**

- Documentation: https://the-guild.dev/graphql/mesh/docs

## Hive Gateway

Hive Gateway is a federated GraphQL routing engine from The Guild that supports both Apollo Federation and Schema Stitching approaches to compose distributed GraphQL services.

**Documentation:** https://the-guild.dev/graphql/hive/docs/gateway

**References:**

- Documentation: https://the-guild.dev/graphql/hive/docs/gateway

## Apollo Federation

Apollo Federation is an alternative to schema stitching for composing distributed GraphQL services. It uses a supergraph approach with subgraph schemas annotated with federation directives, managed through Apollo Studio or self-hosted routers.

**Documentation:** https://www.apollographql.com/docs/federation/

**References:**

- Documentation: https://www.apollographql.com/docs/federation/
