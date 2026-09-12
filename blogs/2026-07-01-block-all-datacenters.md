---
title: "Block all datacenters"
url: "https://discourse.haproxy.org/t/block-all-datacenters/12270#post_5"
date: "2026-07-01"
author: "@lukastribus Lukas Tribus"
feed_url: "https://discourse.haproxy.org/posts.rss"
---
You can add new IP addresses to both the list file and to the existing haproxy instance by using the admin socket. So you avoid to have to reload every time, and if you reload/restart for other reason, you still have an uptodate file.
