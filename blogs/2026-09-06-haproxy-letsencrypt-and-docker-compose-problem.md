---
title: "Haproxy, letsencrypt and docker compose problem"
url: "https://discourse.haproxy.org/t/haproxy-letsencrypt-and-docker-compose-problem/12250#post_10"
date: "2026-09-06"
author: "@sandy_ibis72 Bobby King"
feed_url: "https://discourse.haproxy.org/posts.rss"
---
DaleMiller: If the IP is fairly stable, that’s a reasonable thing to try. Just keep in mind that the Let’s Encrypt rate limit won’t be fixed by the IP being stable — it’s about the hostname/certificate identifiers, so you’ll need to wait until the indicated retry time before issuance can succeed again for that name. Yes, this is the key part: don’t let the container “forget” its ACME state between restarts.
