---
title: "What is the PHP __call magic method?"
date: "2022-05-29"
categories: 
  - "programming"
tags: 
  - "php"
---

Consider this PHP class:

```
<?php
class FooClass
{
    public function bar(): string
    {
        return 'Bar';
    }
}
```

We could call the `bar` method as follows:

```
<?php
$fooClass = new FooClass;

$fooClass->bar();

// returns the string 'Bar'
```

However, in PHP, we have **the ability to call methods that don't actually exist on a class**. They can instead be **caught by a "magic method" named `__call`**, which you can define on your class.

```
<?php
class BazClass
{
    public function __call(string $name, array $args)
    {
        // $name will be given the value of the method
        // that you are trying to call

        // $args will be given all of the values that
        // you have passed into the method you are
        // trying to call
    }
}
```

So if you instantiated the `BazClass` above and called a non-existing method on it with some arguments, you would see the following behavior:

```
<?php
$bazClass = new BazClass;
$bazClass->lolcats('are' 'awesome');
```

In this example, `BazClass`'s `__call` method would catch this method call, **as there is no method on it named `lolcats`**.

The `$name` value in `__call` would then be set to the string "lolcats", and the `$args` value would be set to the array `[0 => 'are', 1 => 'awesome']`.

You may not end up using the `__call` method much in your day to day work, but it is used by frameworks that you possibly _will_ be using, such as Laravel.
