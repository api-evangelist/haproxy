---
title: "Intermittent wrong fallback cert served on TCP-mode SNI passthrough (3.4.4), even with recent SNI/session-resumption fixes included"
url: "https://discourse.haproxy.org/t/intermittent-wrong-fallback-cert-served-on-tcp-mode-sni-passthrough-3-4-4-even-with-recent-sni-session-resumption-fixes-included/12697#post_1"
date: "2026-09-18"
author: "@Tech1UAE"
feed_url: "https://discourse.haproxy.org/posts.rss"
---
HAProxy version: 3.4.4 (also reproduced earlier on 3.2.23 before upgrading) OS: Ubuntu 24.04/26.04, installed via vbernat’s PPA Setup: TCP-mode frontend doing SNI-based passthrough routing to a mail server (SmarterMail), with an HTTP-mode local-termination fallback for everything else. Relevant config: frontend fe_tcp_443 mode tcp option tcplog bind *:443 tcp-request inspect-delay 5s tcp-request content accept if { req.ssl_hello_type 1 } { req.ssl_sni -m found } acl sni_mail req.ssl_sni -i mail.example.com autodiscover.example.com webmail.example.com [... ~20 more domain lines ...] use_backend
