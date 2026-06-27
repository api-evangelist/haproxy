---
title: "Haproxy, letsencrypt and docker compose problem"
url: "https://discourse.haproxy.org/t/haproxy-letsencrypt-and-docker-compose-problem/12250#post_2"
date: "2026-06-27"
author: "@lukastribus Lukas Tribus"
feed_url: "https://discourse.haproxy.org/posts.rss"
---
You are using the LE staging endpoint, which will result in test certifictes. You need to switch to the production endpoint.
