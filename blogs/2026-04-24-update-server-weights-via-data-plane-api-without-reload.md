---
title: "Update server weights via Data Plane API without reload"
url: "https://discourse.haproxy.org/t/update-server-weights-via-data-plane-api-without-reload/12151#post_2"
date: "2026-04-24"
author: "@ema-pe Emanuele"
feed_url: "https://discourse.haproxy.org/posts.rss"
---
Hi, after digging into the Data Plane API v3 documentation and doing some testing, I found the following two APIs: PUT /services/haproxy/runtime/backends/{parent_name}/servers/{name} ( doc ) POST /services/haproxy/runtime/backends/{parent_name}/servers ( doc ) These are sufficient to avoid restarting the proxy. I was missing the “runtime” part of the API path. The only minor issue is that the Data Plane API does not seem to expose the current weights, even though they are applied and used by HAProxy for load balancing.
