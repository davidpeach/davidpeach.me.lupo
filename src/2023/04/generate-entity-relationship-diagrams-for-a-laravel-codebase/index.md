---
title: "Generate Entity Relationship Diagrams for a Laravel codebase"
date: "2023-04-14"
categories: 
  - "programming"
tags: 
  - "laravel-2"
  - "php"
---

When starting on a codebase that has been worked on for some time, it can be handy to try and get **an over-arching picture of the system** and relationships between the various models.

I recently decided to add this to my own onboarding process steps, which should of course be in addition to actual discussions with your co-workers.

There will inevitably be idiosyncrasies in every codebase that a relational diagram just wont show. And many aspects of an older codebase will only come with time and exposure to the weeds of said codebase.

However, I think an ERD can help in many cases. Although if you're dealing with a huge monolith, this could end up adding much extra confusion.

This guide uses a third party package: [https://github.com/beyondcode/laravel-er-diagram-generator](https://github.com/beyondcode/laravel-er-diagram-generator)

## Setup

Please refer to the official README steps on the package's website/repository. This guide is kind of a braindump as I do the steps.

_Note: I branch off in a temporary branch and run these commands so as to not muddy the `main` / `master` branch._

### Install Dependencies

Install graphviz. On Arch I did this:

```
sudo pacman -S graphviz
```

Install in a Laravel project as a dev dependency:

```
composer require beyondcode/laravel-er-diagram-generator --dev
```

## Generation

Generate the ERD with default settings (using the `app/Models` folder for ERD generation):

```
php artisan generate:erd
```

This will give you a file called `graph.png` in your current directory, unless you give it a specific name on the end of the command.

```
# With a custom name
php artisan generate:erd my-file.png

# With a custom name and different format
php artisan generate:erd my-file.jpg --format=jpg
```
