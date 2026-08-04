---
title: "Demand Control in Hive Router"
url: "https://the-guild.dev/graphql/hive/product-updates/2026-06-15-hive-router-demand-control"
date: "2026-06-15"
author: "Dotan Simha"
feed_url: "https://the-guild.dev/graphql/hive/blog/feed.xml"
---
Hive Router now protects federated graphs from expensive operations with Demand Control, a cost-based security layer that assigns numeric costs to operations and rejects those exceeding configured budgets. It implements the IBM GraphQL Cost Specification with directives like @cost and @listSize, estimating operation expense before execution, and supports supergraph-wide limits (up to 5000 cost units) as well as per-subgraph budgets (as low as 200 units for expensive services).
