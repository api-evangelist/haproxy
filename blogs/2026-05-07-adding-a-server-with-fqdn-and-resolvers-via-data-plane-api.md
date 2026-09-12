---
title: "Adding a server with FQDN and resolvers via Data Plane API"
url: "https://discourse.haproxy.org/t/adding-a-server-with-fqdn-and-resolvers-via-data-plane-api/12173#post_2"
date: "2026-05-07"
author: "@ema-pe Emanuele"
feed_url: "https://discourse.haproxy.org/posts.rss"
---
Quoting the reference manual about add server ( link here ): Currently a dynamic server is statically initialized with the none init-addr method. This means that no resolution will be undertaken if a FQDN is specified as an address, even if the server creation will be validated. And for set server / fqdn ( link here ): Change a server’s FQDN to the value passed in argument.
