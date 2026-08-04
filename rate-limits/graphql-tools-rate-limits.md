# GraphQL Tools Rate Limits

GraphQL Tools is a client-side open-source library and does not itself impose any rate limits. The packages are installed via npm/yarn/pnpm and execute entirely within the consuming application's runtime environment.

## npm Registry

Package downloads are governed by the npm registry's own policies. The npm public registry does not enforce download rate limits for normal usage. See https://docs.npmjs.com/policies/rate-limit for current npm rate limit details.

## GitHub API (Source Access)

The GraphQL Tools source repository lives at https://github.com/ardatan/graphql-tools. GitHub's REST and GraphQL APIs apply standard rate limits (60 unauthenticated requests/hour, 5,000 authenticated requests/hour) if you are programmatically accessing repository metadata.

## Runtime Considerations

Because GraphQL Tools runs in-process within your own GraphQL server, any effective rate limits are determined by:

- Your GraphQL server's own request throttling configuration
- Downstream service rate limits when using schema stitching or remote executors
- Infrastructure-level limits (load balancers, API gateways) in front of your deployment

## GraphQL Hive

If you are using GraphQL Hive alongside GraphQL Tools for schema registry or observability, Hive's managed platform enforces its own per-plan usage limits. See https://the-guild.dev/graphql/hive for details.
