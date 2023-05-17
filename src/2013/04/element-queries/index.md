---
title: "Element Queries"
date: "2013-04-29"
categories: 
  - "programming"
tags: 
  - "css"
  - "web-development"
---

I loves me some media queries. In fact if I arrive on a website that I like the look of I’ll often first resize my browser to see how the site looks at different sizes. And if its a fixed width site… I cry and pray for their soul. Okay so that’s not strictly true… I don’t always cry, but I do test a site’s responsiveness on first arrival. But this is only for my own learning – I like to see how other people have approached the challenge of responsive design.

## First Thoughts on @element queries

A couple of weeks ago I found I had an idea in my head, an idea to bring something like @media queries down to the selector level. And that’s all I had – an idea. I didn’t have a workable syntax example or anything.

## We already have @media queries!

It’s true that we already have @media queries. And it’s true – they’re awesome, but one thing that @media queries don’t really do justice for is modular CSS. Consider, if you will, a contact form. Here’s an example of how we might have that in our css:

```

.contact-form{
  /* mobile first styles */
}
@media (min-width: 640px){
  .contact-form{
    /* Styles applied at your first breakpoint */
  }
}
@media (min-width: 1000px){
  .contact-form{
    /* Styles applied at your next breakpoint */
  }
}
```

With the above code, you could style your contact form and make different decisions at different breakpoints in the screens width. But what is stopping you from taking that exact same contact form and using it as the main content on your contact page? Well for one you’d need to add an extra class in to overwrite the styles of the contact form:

```

/* ... */
@media (min-width: 1000px){
  /* the contact form styled for use in the sidebar */
  .contact-form{
    font-size:1.2em;
    padding:10px;
  }
  /* overwriting styles for use in the main contact area */
  .main-content .contact-form{
    font-size:2em;
    padding:20px;
  }
}
/* ... */
```

With @media queries we have power to make stylistic designs based on many things including screen width, but the overall screen size available has no correlation with modules / widgets that you could be using in your design.

## People are already talking about it

The same week I had my own initial thoughts on this, I saw a tweet in my feed by Ian Storm Taylor. The tweet was referencing a blog post by him that talked about this exact thing – the idea of @element queries. His post also goes on to describe a possible syntax for the idea and he also references other people’s thoughts on the subject. I was happy that other people had had similar thoughts to my own – made me feel along side people I follow instead of behind. So instead of copying the examples from the other posts on this subject, which I will reference at the end of this post, I thought I would offer my own idea for a syntax.

## @element query syntax idea

```

@element .contact-form (min-width:600px){
  .input{
    width:80%;
  }
  .label{
    width:20%;
    font-size:1.2em;
  }
}
@element .contact-form (min-width:1000px){
  input:required{
    border:3px solid darkgreen;
    padding:10px;
  }
  .label{
    font-size:2.2em;
    font-weight:bold;
  }
}
```

The code above is all self contained. It doesn’t rely on an overall screen size. The only dimensions that it is concerned with are its own, allowing us to style the element’s children in a truly modular fashion. Of course there are lots of things that could get messy with this syntax. Like if you started trying to use them inside of @media queries, or overusing them on every element in your design. But this is just my thoughts on the subject.

## Use with Sass Partials

What I think would be a great way of using these element queries in a maintainable way would be to have a sass partial for each collection of styles for an element. Then who knows – we could even share these out with other people like we do now with full blog themes.
