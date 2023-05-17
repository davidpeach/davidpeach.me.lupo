---
title: "PHP's __call magic method and named arguments"
date: "2022-05-29"
categories: 
  - "programming"
tags: 
  - "php"
  - "web-development"
---

Whilst working on a little library recently, I discovered some interesting behavior with PHP's `__call` magic method. Specifically around using named arguments in methods that are caught by the `__call` method.

Given the following class:

```
<?php
class EmptyClass
{
    public function __call(string $name, array $args)
    {
        var_dump($args); die;
    }
}
```

Calling a non-existing method without named parameters would result in the arguments being given to `__call` as an indexed array:

```
$myClass = new EmptyClass;

$myClass->method(
    'Argument A',
    'Argument B',
);

// This var dumps: [0 => 'Argument A', 1 => 'Argument B']
```

However, passing those values with named parameters, will cause them to be given to `__call` as an associative array:

```
$myClass = new EmptyClass;

$myClass->method(
    firstArg: 'Argument A',
    secondArg: 'Argument B',
);

// This var dumps: ['firstArg' => 'Argument A', 'secondArg' => 'Argument B']
```

I'm not sure if this is helpful to anyone but I thought it was quite interesting so thought I'd share. :)
