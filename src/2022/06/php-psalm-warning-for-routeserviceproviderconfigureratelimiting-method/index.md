---
title: "PHP Psalm warning for RouteServiceProvider configureRateLimiting method"
date: "2022-06-30"
categories: 
  - "programming"
tags: 
  - "laravel-2"
  - "php"
  - "psalm"
  - "static-analysis"
  - "web-development"
---

When running psalm in a Laravel project, I get the following error by default:

```
PossiblyNullArgument - app/Providers/RouteServiceProvider.php:45:46 - 
Argument 1 of Illuminate\Cache\RateLimiting\Limit::by cannot be null, 
possibly null value provided
```

This is the default implementation for `configureRateLimiting` in the `RouteServiceProvider` class in Laravel:

```
protected function configureRateLimiting()
{
    RateLimiter::for('api', function (Request $request) {
        return Limit::perMinute(60)->by($request->user()?->id ?: $request->ip());
    });
}
```

I change it to the following to get psalm to pass (I've added named parameters and the `static` keyword before the callback function):

```
protected function configureRateLimiting()
{
    RateLimiter::for(name: 'api', callback: static function (Request $request) {
        $limitIdentifier = $request->user()?->id ?: $request->ip();
        if (!is_null($limitIdentifier)) {
            return Limit::perMinute(maxAttempts: 60)->by(key: $limitIdentifier);
        }
    });
}
```
