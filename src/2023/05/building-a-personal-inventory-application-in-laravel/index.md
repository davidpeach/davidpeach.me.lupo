---
title: "Building a personal inventory application in Laravel"
date: "2023-05-12"
categories: 
  - "uncategorised"
tags: 
  - "laravel-2"
  - "php"
  - "programming"
---

I'm going to build myself an inventory system in Laravel, as a way to keep a track of where everything we have a round the house is kept.

I also have visions of it notifying me each morning, of certain foods that are approaching their use-by date.

I thought it would be interesting to share the building of it step by step.

## Sections of the build

Here I'll keep the contents of each area of the build.

### Part 1: [Starting a new Laravel 9 project](https://davidpeach.co.uk/2023/01/13/starting-a-new-laravel-9-project/).

The initial setup and continuous integration workflow for the project.

Merge request showing the changes from a fresh Laravel 9 project: [changes](https://github.com/davidpeach/inventory/pull/1/files).

### Part 2: Adding Laravel Jetstream

Pretty much just following the [Jetstream install documentation](https://jetstream.laravel.com/2.x/installation.html). But with a couple of extra bits.

### Part 3: Keeping an inventory list (coming soon)

This is the simplest form of an inventory, I think: Just a list of items. In this part I will first write out the tests for the setup and API I want to have. I will then use those failing tests to drive the writing of the code.
