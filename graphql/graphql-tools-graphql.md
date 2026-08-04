# GraphQL Tools - GraphQL Schema Documentation

## Description

GraphQL Tools is a modular toolkit from The Guild for building, merging, stitching, transforming, and mocking GraphQL schemas. It is a library — not a hosted API — distributed as a set of npm packages under the `@graphql-tools/` scope. This SDL document captures the key types, interfaces, input types, and enumerations that make up the public API surface of the library.

The schema is documented using GraphQL SDL to represent the TypeScript interfaces and types exported by the library, enabling tooling, introspection, and documentation generation against the GraphQL Tools type system.

## Endpoint

GraphQL Tools is a library with no hosted GraphQL endpoint. The types below describe the library's TypeScript API surface as GraphQL SDL.

- **Package registry:** https://www.npmjs.com/search?q=%40graphql-tools
- **Main entry package:** `@graphql-tools/graphql-tools`
- **GitHub:** https://github.com/ardatan/graphql-tools

## Documentation

- **Docs:** https://the-guild.dev/graphql/tools/docs
- **Schema package:** https://the-guild.dev/graphql/tools/docs/generate-schema
- **Schema merging:** https://the-guild.dev/graphql/tools/docs/schema-merging
- **Schema stitching:** https://the-guild.dev/graphql/tools/docs/schema-stitching
- **Schema wrapping/transforms:** https://the-guild.dev/graphql/tools/docs/schema-wrapping
- **Mocking:** https://the-guild.dev/graphql/tools/docs/mocking

## Schema File

See `graphql-tools-schema.graphql` for the full SDL schema documenting all key types.

## Packages

| Package | Purpose |
|---|---|
| `@graphql-tools/schema` | `makeExecutableSchema`, `addResolversToSchema` |
| `@graphql-tools/merge` | `mergeTypeDefs`, `mergeResolvers`, `mergeSchemas` |
| `@graphql-tools/utils` | Shared interfaces, `mapSchema`, `filterSchema` |
| `@graphql-tools/mock` | `addMocksToSchema`, `MockStore`, `mockServer` |
| `@graphql-tools/wrap` | Schema transforms: Rename, Filter, Wrap, Hoist |
| `@graphql-tools/load` | Schema and document loading from files/URLs |
| `@graphql-tools/executor` | Schema execution utilities |
