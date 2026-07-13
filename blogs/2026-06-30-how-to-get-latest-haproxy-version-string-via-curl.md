---
title: "How to get latest Haproxy version string via curl?"
url: "https://discourse.haproxy.org/t/how-to-get-latest-haproxy-version-string-via-curl/12260#post_2"
date: "2026-06-30"
author: "@lukastribus Lukas Tribus"
feed_url: "https://discourse.haproxy.org/posts.rss"
---
You can find json files on the webserve for specific release trains: https://www.haproxy.org/download/3.4/src/releases.json You may also just use the external service endoflife.date : https://endoflife.date/haproxy Using their API you can use the one liner: curl -s "https://endoflife.date/api/v1/products/haproxy/releases/latest" | \ jq '.["result"]["latest"]["name"]'
