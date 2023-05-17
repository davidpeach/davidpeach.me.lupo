---
title: "Automatic Quick Where Clauses In Laravel"
date: "2015-11-09"
categories: 
  - "programming"
tags: 
  - "laravel-2"
  - "php"
  - "programming"
---

In Laravel (tested only in 5.1) there is a handy feature with where clauses in the query builder.

Imagine you wanted to query the database for records where they name was equal to 'Chevy'

Well you could do it like so:

```
YourModel::where('name', 'Chevy')->get();
```

But did you know you could also do the following:

```
YourModel::whereName('Chevy')->get();
```

A handy little feature that. Also works for a column like 'user\_name':

```
YourModel::whereUserName('Chevy')->get();
```
