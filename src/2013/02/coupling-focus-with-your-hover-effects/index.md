---
title: "Coupling :focus with your :hover effects"
date: "2013-02-19"
categories: 
  - "notes"
tags: 
  - "css"
  - "web-development"
---

After working on a range on different websites, I have noticed a recurring theme in regards to links and how they are highlighted.

Every developer reading this has, without a doubt, declared a :hover psuedo class in their stylesheet:

```

.nav-link{
  background:black;
}
.nav-link:hover{
  background:white;
}
```

So basically what this means is: the link has a background of black – then when the user hovers over it, it changes its background to white.

But what about those who don’t use a mouse or _can’t_ use a mouse? How do you inform them which link is currently in focus? Well, funnily enough, you can use the :focus psuedo class like so:

```

.nav-link{
  background:black;
}
.nav-link:hover, .nav-link:focus{
  background:white;
}
```

So now, without any extra work, you can broaden your site’s accessibility to include those who need to – or want to – use their keyboard for navigating your website.
