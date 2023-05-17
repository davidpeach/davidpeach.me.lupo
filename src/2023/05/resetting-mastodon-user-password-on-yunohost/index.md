---
title: "Resetting mastodon user password on YunoHost"
date: "2023-05-11"
categories: 
  - "uncategorised"
tags: 
  - "mastodon"
  - "programming"
  - "servers"
  - "yunohost"
---

SSH on to the server

Switch to "root" `sudo su` .

```
(cd /var/www/mastodon/live && sudo -u mastodon \ 
RAILS_ENV=production \ 
PATH=/opt/rbenv/versions/mastodon/bin \ 
bin/tootctl accounts modify _USERNAME_ --reset-password)
```
