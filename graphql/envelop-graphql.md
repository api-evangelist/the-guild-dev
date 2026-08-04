# Envelop GraphQL Plugin API

## Description

Envelop is a lightweight JavaScript/TypeScript plugin system for wrapping the GraphQL execution pipeline. Developed by The Guild, it exposes composable lifecycle hooks that intercept and extend the parse, validate, execute, and subscribe phases of any GraphQL server. Plugins are authored against the `@envelop/core` and `@envelop/types` packages and compose via the `envelop()` factory function.

There is no hosted GraphQL endpoint. The schema documented here represents the TypeScript plugin API surface — extracted from the published `@envelop/core@5.5.1` and `@envelop/types@5.2.1` npm packages — modeled as GraphQL SDL for discoverability and tooling purposes.

## Endpoint

None. Envelop is a library, not a hosted service. It wraps your GraphQL server's execution engine at runtime.

## Documentation

- Getting Started: https://the-guild.dev/graphql/envelop/docs/getting-started
- Core API: https://the-guild.dev/graphql/envelop/docs/core
- Plugin Lifecycle: https://the-guild.dev/graphql/envelop/docs/plugins/lifecycle
- Building Plugins: https://the-guild.dev/graphql/envelop/docs/plugins/custom-plugin
- TypeScript Support: https://the-guild.dev/graphql/envelop/docs/plugins/typescript
- Plugin Hub: https://the-guild.dev/graphql/envelop/plugins
- Source Repository: https://github.com/graphql-hive/envelop
- npm (@envelop/core): https://www.npmjs.com/package/@envelop/core
- npm (@envelop/types): https://www.npmjs.com/package/@envelop/types

## Schema Source

SDL derived from TypeScript declarations in:
- `@envelop/types@5.2.1` — `typings/hooks.d.ts`, `typings/plugin.d.ts`, `typings/get-enveloped.d.ts`, `typings/context-types.d.ts`, `typings/graphql.d.ts`
- `@envelop/core@5.5.1` — `typings/plugins/*.d.ts`, `typings/create.d.ts`, `typings/utils.d.ts`

## Key Concepts

- **`envelop(plugins)`** — Factory that wraps the execution pipeline and returns `GetEnvelopedFn`.
- **`getEnveloped(initialContext?)`** — Returns `{ parse, validate, contextFactory, execute, subscribe, schema }` for each request.
- **`Plugin<PluginContext>`** — Interface implemented by every plugin; declares optional hook handlers.
- **Hook phases** — `onPluginInit` → `onEnveloped` → `onSchemaChange` → `onParse` → `onValidate` → `onContextBuilding` → `onExecute` / `onSubscribe`.
- **`EnvelopError`** — Error subclass whose message is safe to surface to API consumers (used with `useMaskedErrors`).
