# GraphQL Yoga FinOps

## Direct Cost: $0

GraphQL Yoga is an open-source MIT-licensed library. There is no SaaS subscription, no per-request charge, and no licensing fee from The Guild or the graphql-yoga project.

## Infrastructure Costs

All financial exposure comes from the platform you choose to host your GraphQL Yoga server. Costs vary significantly by runtime and provider:

### Node.js (Traditional Server)
- **AWS EC2 / GCP Compute / Azure VM:** On-demand or reserved instance pricing based on CPU/RAM tier and region.
- **Railway / Render / Fly.io:** Usage-based or flat monthly plans starting from ~$5–$7/month for a small container.
- **Heroku:** Dyno-based pricing (no free tier as of 2022).

### Serverless / Edge
- **Cloudflare Workers:** Free tier includes 100,000 requests/day; paid plans start at $5/month for 10M requests.
- **Vercel Functions:** Free tier available; Pro plan $20/month per seat includes higher limits.
- **AWS Lambda:** 1M free requests/month; $0.20 per additional 1M requests.
- **Deno Deploy:** Free tier available; teams plan $20/month.

### Bun / Deno (Self-Hosted)
Same infrastructure pricing as Node.js above — the runtime choice does not change hosting costs.

## Cost Drivers to Monitor

| Driver | Notes |
|---|---|
| Subscription connections (SSE / WebSocket) | Long-lived connections consume compute and memory continuously; size instances accordingly. |
| File upload bandwidth | Large file uploads increase egress and storage costs. |
| Query complexity | Deep or wide queries raise CPU time per request; complexity limiting can reduce bill. |
| Response caching | Using `@graphql-yoga/plugin-response-cache` reduces redundant execution and can lower compute spend. |
| Cold starts (serverless) | Bun or Deno runtimes cold-start faster than Node.js, potentially reducing billed duration on serverless platforms. |

## The Guild Support Contracts

If your team engages The Guild for paid consulting or support, that is a direct software services cost negotiated separately. See `plans/graphql-yoga-plans.md` for details.

## References

- Cloudflare Workers Pricing: https://developers.cloudflare.com/workers/platform/pricing/
- Vercel Pricing: https://vercel.com/pricing
- AWS Lambda Pricing: https://aws.amazon.com/lambda/pricing/
- Fly.io Pricing: https://fly.io/docs/about/pricing/
- GraphQL Yoga Deployment Guides: https://the-guild.dev/graphql/yoga-server/docs/integrations
