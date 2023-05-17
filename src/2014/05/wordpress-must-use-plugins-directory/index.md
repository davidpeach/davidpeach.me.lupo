---
title: "Wordpress \"Must Use\" Plugins Directory"
date: "2014-05-21"
categories: 
  - "programming"
tags: 
  - "php"
  - "web-development"
  - "wordpress"
---

The Issue

I wanted to build a site with some custom post types, taxonomies and the like. But what if somebody who has used my theme decided to try another theme later on? What guarantee do they have that those custom post types will be recognized by a future theme?

None — that's what.

WordPress obviously has its plugin directory, which is designed for adding in pieces of functionality that should span across themes. But what if these are essential to the working of the site due to custom post types, taxonomies or shortcodes?

Either it can be a plugin — which could be accidentally deactivated, or added to the theme's functions.php — which would need copying over to any future theme.

A Hidden Gem of a Solution

Well it turns out that there is a third option — a way for WordPress to auto load essential plugins irregardless of the theme being used. Simply by creating a directory in the 'wp-content' folder called 'mu-plugins' — which stands for "must use plugins" — and adding plugins as you would into the regular plugins folder, they will be auto loaded with any theme and just work.

These 'must use' plugins will then be viewable in the plugin admin page, in a new option called 'must use' — grouped with the other plugin page navigation items, 'All', 'Active' and 'Inactive'.

'Must use' plugins can't be deactivated in the admin — creating a nice separation of essential plugins for a particular user.

Thanks to Justin Tadlock for this piece of info.
