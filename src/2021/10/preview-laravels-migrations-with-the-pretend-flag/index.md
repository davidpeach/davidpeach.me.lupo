---
title: "Preview Laravel's migrations with the pretend flag"
date: "2021-10-20"
categories: 
  - "php"
tags: 
  - "laravel-2"
  - "php"
---

Here is the command to preview your Laravel migrations without running them:

```
cd /your/project/root
php artisan migrate --pretend
```

Laravel's migrations give us the power to easily version control our database schema creations and updates.

In a recent task at work, I needed to find out why a particular migration was failing.

This is when I discovered the simple but super-useful flag `--pretend`, which will show you the queries that Laravel will run against your database **without actually running those migrations**.
