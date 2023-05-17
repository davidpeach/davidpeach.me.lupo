---
title: "Setting up Elasticsearch and Kibana using Docker for local development"
date: "2021-01-11"
categories: 
  - "braindumps"
tags: 
  - "docker"
  - "elasticsearch"
  - "kibana"
  - "programming"
  - "web-development"
---

## Overview

Elasticsearch is a super-fast search query program. Kibana is a separate program that can be used for interacting with elasticsearch.

Here I am setting up both Elasticsearch and Kibana in their own single Docker Containers. I do this as a way to help keep my computer relatively free from being cluttered with programs. Not only that, but since the containers are their own separate self-contained boxes, it also makes it easy to upgrade the Elasticsearch version I am using at a later date.

Or even remove them entirely with minimal fuss.

Please note: I am using version 7.10.1 of both programs in the examples below. You can look at each program's respective docker hub pages to target the exact version you require:

- [Kibana on Docker hub](https://hub.docker.com/_/kibana?tab=tags&page=1&ordering=last_updated).

- [Elasticsearch on Docker hub](https://hub.docker.com/_/elasticsearch?tab=tags&page=1&ordering=last_updated).

Just replace any uses of "7.10.1" below with your own version.

## Creating and running containers for the services needed

Run the two following commands to download and run Elasticsearch locally:

```
# Download the Elasticsearch docker image to your computer
docker pull elasticsearch:7.10.1
# Create a local container with Elasticsearch running
docker run -d --name my_elasticsearch --net elasticnetwork -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e "xpack.ml.enabled=false" elasticsearch:7.10.1
# Start the container
docker container start my_elasticsearch
```

And then run the two following commands to download and run Kibana locally:

```
# Download the Kibana docker image to your computer
docker pull kibana:7.10.1
# Create a local container with Kibana running
docker run -d --name my_kibana --net elasticnetwork -e ELASTICSEARCH_URL=http://elasticsearch:9200 -p 5601:5601 kibana:7.10.1
# Start the container
docker container start my_kibana
```

## Accessing Kibana

Since kibana will be connecting to our Elasticsearch container, which it was told to use with the `ELASTICSEARCH_URL=http://elasticsearch:9200` section of the Kibana create command, we really only need to use Kibana.

Kibana has it's own Devtools for querying Elasticsearch, which so far has been enough for my own usecases.

head to [http://localhost:5601](http://localhost:5601) to access your own Kibana installation.

Note: You can send curl requests directly to your Elasticsearch from the terminal by targeting the [http://127.0.0.1:9200](http://127.0.0.1:9200) endpoint.

## Deleting the containers

If you wish to remove Elasticsearch and/or Kibana from your computer, then enter the following commands into your terminal.

Using Docker for local development makes this a cinch.

```
# Stop the Elasticsearch container if it is running
# (Use it's name you gave it in the "--name" argument as its handle)
docker container stop my_elasticsearch
# Delete the Elasticsearch container
docker container rm my_elasticsearch
# Stop the Kibana container if it is running
# (Use it's name you gave it in the "--name" argument as its handle)
docker container stop my_kibana
# Delete the Kibana container
docker container rm my_kibana
```

If you need to set up the two programs again, you can just use the create commands shown above to create them as you did originally.
