---
title: ""
date: "2015-11-04"
categories: 
  - "programming"
tags: 
  - "laravel"
---

Normally, with Laravel ([@laravelphp](https://twitter.com/laravelphp) on Twitter), if you create a model and use the "-m" or "--migration" flag to create the accompanying migration, it will pluralize the table.

So for example "User" model will use a "users" table; "Vehicle" model will use a "vehicles" table.

I just discovered however, that if you create a "Data" model, the table will also be created as "data" - not "datas". It makes complete sense as datas isn't a word.

I love using this framework.
