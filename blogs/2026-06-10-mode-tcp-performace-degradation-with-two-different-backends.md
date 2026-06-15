---
title: "'mode tcp' performace degradation with two different backends"
url: "https://discourse.haproxy.org/t/mode-tcp-performace-degradation-with-two-different-backends/12194#post_2"
date: "2026-06-10"
author: "@lukastribus Lukas Tribus"
feed_url: "https://discourse.haproxy.org/posts.rss"
---
You have already filed a bug on Github about this: github.com/haproxy/haproxy 'mode tcp' performace degradation with two different backends opened 01:37PM - 08 Jun 26 UTC doka380 type: bug status: needs-triage ### Detailed Description of the Problem I’m trying to test new connections rate … in 'mode tcp' with the following config ``` frontend default_fe mode tcp bind *:443 default_backend default_be backend default_be mode tcp balance roundrobin # three autonomous apache servers server s3_v4 127.0.0.1:8443 server s1_v4 172.16.37.1:8443 server s2_v4 172.16.37.2:8443 ``` using and command: `wrk 
