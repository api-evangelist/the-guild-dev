# GraphQL Inspector Plans

GraphQL Inspector is a fully open-source project (MIT licensed) maintained by The Guild. There are no paid subscription plans for the core CLI or programmatic API. The tool is freely available via npm and as a GitHub Action.

## Free / Open Source (All Tiers)

**Cost:** $0

GraphQL Inspector core tooling is free for all users with no usage limits on schema diffing, document validation, or coverage analysis.

**Included:**
- Schema diffing (breaking, dangerous, non-breaking change classification)
- Document and fragment validation against schema
- Schema coverage analysis based on operations and fragments
- Similar and duplicate type detection
- CLI available via `npx @graphql-inspector/cli` or global install
- Programmatic API for embedding in custom tooling
- GitHub Action for CI integration
- Docker image support
- Multiple environment and endpoint configurations

## GitHub Application (Marketplace)

**Cost:** Free (GitHub Marketplace listing)

The GraphQL Inspector GitHub Application integrates directly into GitHub repositories. It can be installed from the GitHub Marketplace with a single click.

**Included:**
- Automatic schema change detection on pull requests
- Breaking change notifications as PR comments or checks
- Slack, Discord, and webhook notifications on schema changes
- Schema change interception via serverless functions
- Self-hosted option available (open-source deployment)

**Reference:** https://github.com/marketplace/graphql-inspector

## Self-Hosted

For teams wanting full control, GraphQL Inspector's GitHub application code is open-source and can be deployed to your own infrastructure (e.g., Netlify Functions, AWS Lambda).

**Cost:** Infrastructure costs only (no license fee)

## Notes

GraphQL Inspector is developed and maintained by The Guild, the same team behind GraphQL Hive, Yoga, Envelop, and other ecosystem tools. The Guild offers paid consulting, support, and integration services for enterprise teams — contact them at https://the-guild.dev for commercial arrangements.
