---
title: "Deploying my sites and projects to Docker Swarm"
date: "2023-01-07"
categories: 
  - "braindumps"
tags: 
  - "docker"
  - "docker-swarm"
  - "servers"
---

This post is going to be a bit of a note taking and brain dump page but will, over time, be fleshed out and tidied up into a coherent post. The end goal for this post is to help regular developers get some form of server orchestration and automation under their belt.

I'm learning as I go so this could all end in tears.

## My end goals

Currently I run a bunch of different sites and projects on a server on Digital Ocean. These are pretty much all managed through a service called Laravel Forge.

Part of my aim is to take the $19 I spend on forge and use that to increase my own Digital Ocean server and learn the deployment and orchestration for myself.

### Services I want

My website

labs / experiments in different languages and libraries.

Mastodon server

Peertube maybe

Nextcloud / Syncthing (undecided which)

## Docker Swarm for server orchestration

The simplest way I can thing of putting the whole process behind Docker Swarm is this: Run a command, with a given docker configuration file, and it will set up your entire server working from end to end.

## Traefik for website routing

When one of my web addresses is requested by someone, I need a way to show that person the correct website (as I am hosting a bunch of them on the same server).

Previously, before using Docker Swarm, I would just configured a separate Nginx config file to catch the website address and route the person to the correct website (the correct directory on the server that had the website files).

However, now I am using the orchestrater Docker Swarm, each website is kept in its own isolated box (for want of a better word) on the server. Not only that, but if I wanted to stretch my "Swarm" across multiple servers (which is made super simple by Docker Swarm), I can never guarantee where the code will be physically.

For these reasons, I have chosen to use a program called "Traefik". Traefic will essentially catch all the routes I tell it about (by way of configuration) and point people to the correct place for the website they are visiting.

### Random notes

install and login to doctl.
