---
title: "Chroot can't quit"
url: "https://discourse.haproxy.org/t/chroot-cant-quit/12162#post_2"
date: "2026-04-28"
author: "@lukastribus Lukas Tribus"
feed_url: "https://discourse.haproxy.org/posts.rss"
---
When you install haproxy on Debian Trixie, haproxy is already chrooted into /var/lib/haproxy and everything will just work. root@debian-4gb-fsn1-1:~# grep chroot /etc/haproxy/haproxy.cfg chroot /var/lib/haproxy root@debian-4gb-fsn1-1:~# Nothing else is needed.
