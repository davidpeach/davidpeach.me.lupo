---
title: "Adding Laravel Jetstream to a fresh Laravel project"
date: "2023-01-20"
categories: 
  - "programming"
tags: 
  - "laravel-2"
  - "laravel-inventory-app"
  - "php"
---

I only have this post here as there was a couple of extra steps I made after regular installation, which I wanted to keep a note of.

Here are the [changes made to my Inventory Manager](https://github.com/davidpeach/inventory/pull/2/files).

## Follow the Jetstream Installation guide

Firstly I just follow the [official installation guide](https://jetstream.laravel.com/2.x/installation.html).

When it came to running the Jetstream install command in the docs, this was the specific flavour I ran:

```
php artisan jetstream:install livewire --pest
```

This sets it up to use [Livewire](https://laravel-livewire.com/), as I wanted to learn that along the way, as well as setting up the Jetstream tests as [Pest](https://pestphp.com/) ones.

Again, I'm not too familiar with Pest (still loving phpunit) but thought it was worth learning.

## Enable API functionality

I want to build my Inventory Manager as a separate API and front end, so I enabled the API functionality after install.

Enabling the built-in API functionality, which is [Laravel Sanctum](https://laravel.com/docs/9.x/sanctum) by the way, is as easy as uncommenting a line in your `./config/jetstream.php` file:

```
'features' => [
    // Features::termsAndPrivacyPolicy(),
    // Features::profilePhotos(),
    Features::api(),
    // Features::teams(['invitations' => true]),
    Features::accountDeletion(),
],
```

The `Features::api(),` line should be commented out by default; just uncomment it and you're good to go.

## Setup Pest testing

The only thing that tripped me up was that I hadn't previously setup pest, which was causing the Jetstream tests to fail.

So I ran the following command, which is modified for my using [Laravel Sail](https://laravel.com/docs/9.x/sail), from the [Pest Documentation](https://pestphp.com/docs/plugins/laravel):

```
./vendor/bin/sail artisan pest:install
```

I then also added the `RefreshDatabase` trait to my `./tests/TestCase.php` file.

Then all of my tests pass.

That is Jetstream setup and ready to continue for me.
