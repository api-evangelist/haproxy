---
title: "Syslog Forwarding with send-proxy not working"
url: "https://discourse.haproxy.org/t/syslog-forwarding-with-send-proxy-not-working/11771#post_3"
date: "2026-05-07"
author: "@lukastribus Lukas Tribus"
feed_url: "https://discourse.haproxy.org/posts.rss"
---
This was discussed on github, you can find the conversation here: github.com/haproxy/haproxy send-proxy-v2 in Rings results in segfault opened 01:42PM - 07 May 25 UTC dot-mike type: bug status: fixed 2.4 ### Detailed Description of the Problem When using `server` option `send-proxy- … v2` inside `ring`, the program crashes with segfault. Rings documentation specifically mention that _all_ parameters for `server` is supported. ### Expected Behavior Not to segfault ### Steps to Reproduce the Behavior 1.
