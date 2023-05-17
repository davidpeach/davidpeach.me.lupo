---
title: "There is always a logical answer"
date: "2015-08-02"
categories: 
  - "long-form"
tags: 
  - "classic-dave"
  - "grinding-my-gears"
  - "linux"
---

I installed Ubuntu server on my spare computer the other day and all was fine.

I then moved the Apache document root to a directory in my home folder -- a common thing done by people, I hear.

I have done this many times before and always worked fine -- as did this for a time.

I had done this via ssh as is common with a server OS. Only thing was, was once I exited the ssh, Apache seemed to stop working.

I spent about an hour then, at around midnight, trying to figure out what had gone wrong. What had I done differently? The answer was simple: nothing…… or so I thought.

Turns out I had encrypted my home directory on installation of the OS. Probably a good thing to do, except that of course when trying to view the Apache server page in a browser it would error -- due to my having moved it's root from its default into my home folder.

As soon as I logged in via ssh to the server, it would work again. But when exiting it would stop.

This was simply down to the fact that my logging into the home directory via ssh would cause it to decrypt itself -- making the apache page viewable. And then when I exited the ssh, it would re-encypt, thus breaking it.

Fu fu fu.

Off to see Mission Impossible: Rogue Nation tonight. Really looking forward to it.

I just hope there are no annoying people about. i.e. screaming kids, idiots on phones, people saying things like "Oh he was in thingymajig" or "This bit is sick".

I must be getting old.
