---
title: "WebSocket Connection Multiplexing in Hive Router"
url: "https://the-guild.dev/graphql/hive/product-updates/2026-08-12-hive-router-websocket-multiplexing"
date: "2026-08-13"
feed_url: "https://the-guild.dev/feed.xml"
---
Hive Router now multiplexes subscriptions over shared, pooled WebSocket connections to subgraphs instead of opening one connection per subscription, and can optionally route queries and mutations over that same pool.
