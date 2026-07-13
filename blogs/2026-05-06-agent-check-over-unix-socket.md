---
title: "Agent check over Unix socket"
url: "https://discourse.haproxy.org/t/agent-check-over-unix-socket/12172#post_3"
date: "2026-05-06"
author: "@buzztee buzztee"
feed_url: "https://discourse.haproxy.org/posts.rss"
---
Thanks for your feedback @lukastribus Some part of this question was probably driven by my inner neat freak: keep conntrack for user sessions only and try to avoid using loopbacks to minimize the attack surface (so my customers don’t accidentally create configs using the agents as servers). Plus my HAProxy is running in a container, so the chroot question can be somewhat relaxed in this case. That said, I noticed that there are multiple directives that already accept various address families (like unix@, config docs section 2.9.1 ).
