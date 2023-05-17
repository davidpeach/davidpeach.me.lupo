---
title: "Setting up a beginner Kubernetes infrastructure in Digital Ocean with Terraform"
date: "2023-05-14"
categories: 
  - "uncategorised"
tags: 
  - "docker"
  - "kubernetes"
  - "programming"
  - "servers"
---

This guide will go step by step in creating some web development infrastructure with Kubernetes, managed database, domain name and other stuff, ready to have a project deployed to it.

All of this will be done through a single configuration file, which I will write piece by piece in this article.

## I'm not a devops person

By trade I am a PHP developer. I've never done devops in a professional setting. However, for a while I have had a strange fascination with various continuous integration and deployment strategies I've seen at many of my places of work.

I've seen some very complicated setups over the years, which has created a mental block for me to really dig in and understand setting up integration and deployment workflows.

But in my current role at Geomiq, I had the opportunity of being shown a possible setup -- specifically using Kubernetes. And that was sort of a gateway drug, which finally led me to getting a working workflow up and running.

I now want to share how I would set up a Kubernetes cluster in Digital Ocean, followed by how I set up projects -- Laravel projects in my case -- to automatically deploy to that cluster as part of a workflow.

## How a deployment will work

First off I'd like to explain how I have the setup working; what happens and when.

On completion of a new feature branch, I will create a Pull Request to merge it into the repository's `main` branch in Github.

Both pushing a branch to the repository and creating the Pull Request will trigger a Github Action. That Action will run

## The key parts of the process

It's probably easier to first get our heads around the main areas of the setup I use, before digging into each section in a separate post.

1. Setting up the Kubernetes Cluster itself

3. Setting up any API Keys and access keys / secrets

5. Configuring a web application to be deployed upon a certain condition (e.g. passing test-suite or manual deployment)

post unfinished...
