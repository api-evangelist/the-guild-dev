# GraphQL Inspector FinOps

GraphQL Inspector is free and open-source (MIT license). There are no licensing costs, subscription fees, or usage-based charges for the core tooling. FinOps considerations apply to the infrastructure and services that run alongside GraphQL Inspector in your CI/CD pipeline.

## Cost Drivers

### 1. GitHub Actions Minutes

If you use GraphQL Inspector as a GitHub Action, schema checks consume GitHub Actions compute minutes.

- **GitHub Free plan:** 2,000 minutes/month included (Linux runners)
- **GitHub Pro:** 3,000 minutes/month included
- **GitHub Team:** 3,000 minutes/month included
- **GitHub Enterprise Cloud:** 50,000 minutes/month included
- **Overage rate (Linux):** $0.008/minute

GraphQL Inspector schema diff runs are typically fast (seconds), so Actions cost impact is minimal unless run at very high frequency across many repositories.

**Reference:** https://docs.github.com/en/billing/managing-billing-for-your-products/managing-billing-for-github-actions/about-billing-for-github-actions

### 2. Self-Hosted GitHub App Infrastructure

If you self-host the GraphQL Inspector GitHub Application (e.g., on Netlify Functions, AWS Lambda, or Cloudflare Workers):

- **Netlify Functions Free tier:** 125,000 requests/month, 100 hours compute
- **AWS Lambda Free tier:** 1M requests/month, 400,000 GB-seconds compute
- **Cloudflare Workers Free tier:** 100,000 requests/day

Schema check webhook invocations are lightweight (milliseconds) and low-volume, so most self-hosted deployments operate within free tiers of serverless platforms.

### 3. npm Package Downloads

There are no costs for downloading and using the `@graphql-inspector/cli` npm package. npm package downloads are free for public packages.

## Optimization Recommendations

### Run Inspector Only on Schema-Affecting PRs

Configure your CI workflow to run GraphQL Inspector only when GraphQL schema files change, rather than on every commit. Use `paths:` filters in GitHub Actions workflows to limit unnecessary runs.

**Impact:** Reduces Actions minutes consumption

### Use Local CLI in Development, Action in CI

Reserve the GitHub Action for CI enforcement and run the CLI locally during development to avoid triggering remote notifications and API calls unnecessarily.

**Impact:** Reduces GitHub API rate limit consumption, cleaner signal in CI

### Cache npm Dependencies

Use GitHub Actions caching (`actions/cache`) for `node_modules` to avoid reinstalling `@graphql-inspector/cli` on every run.

**Impact:** Reduces Actions minutes per run

## Budget Scenarios

| Scenario | Monthly Cost | Notes |
|---|---|---|
| Open-source or personal project | $0 | Free GitHub plan Actions minutes sufficient |
| Small team, 1-5 repos | $0 | Well within included Actions minutes |
| Large org, 50+ repos, high PR frequency | $5–$20 | Actions overage minutes for Linux runners |
| Self-hosted GitHub App | $0–$5 | Fits within serverless free tiers |

## Summary

GraphQL Inspector has effectively zero direct licensing or SaaS cost. Any spend is incidental to CI/CD infrastructure choices (GitHub Actions minutes, serverless hosting). For most teams, total monthly cost attributable to GraphQL Inspector is $0.
