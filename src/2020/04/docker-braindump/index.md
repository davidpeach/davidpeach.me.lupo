---
title: "Docker braindump"
date: "2020-04-24"
categories: 
  - "braindumps"
tags: 
  - "docker"
  - "docker-swarm"
  - "web-development"
coverImage: "Docker-Swarm.jpg"
---

These are currently random notes and are not much help to anybody yet. They will get tidied as I add to the page.

## Docker Swarm

### Docker swarm secrets

From inside a docker swarm manager node, there are two ways of creating a secret.

Using a **string value**:

`printf <your_secret_value> | docker secret create your_secret_key -`

Using a **file path**:

`docker secret create your_secret_key ./your_secret_value.json`

Docker swarm secrets are saved, **encrypted**, and are **accessible to containers via a filepath**:

`/run/secrets/your_secret_key`.

### Posts to digest

[https://www.bretfisher.com/docker-swarm-firewall-ports/](https://www.bretfisher.com/docker-swarm-firewall-ports/)

[https://www.bretfisher.com/docker/](https://www.bretfisher.com/docker/)

[https://www.digitalocean.com/community/tutorials/how-to-set-up-laravel-nginx-and-mysql-with-docker-compose](https://www.digitalocean.com/community/tutorials/how-to-set-up-laravel-nginx-and-mysql-with-docker-compose)
