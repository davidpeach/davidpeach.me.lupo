---
title: "On rethinking my database structure"
date: "2015-10-27"
categories: 
  - "long-form"
tags: 
  - "laravel-2"
  - "my-website"
  - "php"
---

I've been using Laravel for my personal website for about eight months now and haven't looked back since.

This huge advantage to my rebuilding it in that way -- from its original WordPress foundations -- was that I had a crash course in using Laravel as well as learning some best practices as well.

Now that I have been using my site daily for all this time, I have found places where it has got messy -- unavoidable through the learning experience -- as well as places where I want to refine how I publish.

At the moment I am using what are called explicit post types. Meaning that I manually choose which post type a particular post belongs to before publishing -- picking the appropriate create form to publish from.

However I have been thinking more and more about implicit post types -- post types whose contents define what sort of post it is. Going the way of implicit may also see me abolishing the need for post-type-specific areas of my site.

I could still do this to some degree I suppose. e.g. If a post doesn't have a title, it's a note; If it has a location, it's a checkin; etc.

The only way to see how this is going to go is to build it and actually publish with it for a while, I guess.

**_Update 8th February 2021_**: I now use WordPress for my website and have done for a few years now.
