# GraphQL Code Generator – GraphQL Schema

## Description

GraphQL Code Generator is a CLI tool from The Guild that generates TypeScript types, React hooks, resolvers, and SDKs from GraphQL schemas and operations. It has a plugin-based architecture with 50+ community and built-in plugins.

Because GraphQL Code Generator is itself a toolchain rather than a hosted service, it does not expose a live GraphQL endpoint. This schema documents the tool's internal type system: the configuration objects consumed by the CLI, the plugin API, and the generated output types.

The canonical source of truth is the `Types` namespace exported from `@graphql-codegen/plugin-helpers` (packages/utils/plugins-helpers/src/types.ts) and the `CodegenPlugin` interface.

## Endpoint

None. GraphQL Code Generator is a local CLI tool (`graphql-codegen`). It reads a `codegen.yml` / `codegen.ts` configuration file from the project root and writes generated files to the file-system. There is no network endpoint to query.

## Schema Source

- **Repository**: https://github.com/dotansimha/graphql-code-generator
- **Primary types file**: `packages/utils/plugins-helpers/src/types.ts`
- **CLI config loader**: `packages/graphql-codegen-cli/src/config.ts`
- **Core codegen engine**: `packages/graphql-codegen-core/src/codegen.ts`

## Documentation

- Docs home: https://the-guild.dev/graphql/codegen/docs
- Config reference: https://the-guild.dev/graphql/codegen/docs/config-reference/codegen-config
- Schema field: https://the-guild.dev/graphql/codegen/docs/config-reference/schema-field
- Plugins index: https://the-guild.dev/graphql/codegen/docs/plugins
- TypeScript plugin: https://the-guild.dev/graphql/codegen/plugins/typescript/typescript
- TypeScript resolvers plugin: https://the-guild.dev/graphql/codegen/plugins/typescript/typescript-resolvers
- Lifecycle hooks: https://the-guild.dev/graphql/codegen/docs/config-reference/lifecycle-hooks

## Schema File

See `graphql-code-generator-schema.graphql` in this directory for the SDL representation of the tool's configuration and plugin type system.
