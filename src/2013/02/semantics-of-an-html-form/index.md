---
title: "Semantics of an HTML Form"
date: "2013-02-26"
categories: 
  - "programming"
tags: 
  - "html"
  - "theweb"
  - "web-development"
---

Working on a variety of different websites over the past few months, I have seen various things done in numerous different ways – one of the major ones being HTML forms. Now, this post isn’t me preaching about what I think is the “correct” way, but rather my findings of research done into the semantics of forms. Firstly, I’d like to demonstrate some of the different ways I’ve seen for marking up forms. The following examples are bare bones examples and don’t take into account the various attributes available such as name, placeholder and required.

## Wrapping each input with a `<div>`

```

<form action="post.php" method="post">
  <div>
    <label for="user_name">Name</label>
    <input type="text" id="user_name">
  </div>
  <div>
    <label for="user_email">Email</label>
    <input type="email" id="user_email">
  </div>
  <div>
    <button type="submit">Send<button>
  </div>
</form>
```

Wrapping each form input in a `<div>` element seems to be a popular choice by authors, likely because of its being a block level element by default. And since <div>s have no real semantic value, they probably wouldn’t affect the document outline.

## Wrapping each input with a `<p>`

```

<form action="post.php" method="post">
  <p>
    <label for="user_name">Name</label>
    <input type="text" id="user_name">
  </p>
  <p>
    <label for="user_email">Email</label>
    <input type="email" id="user_email">
  </p>
  <p>
    <button type="submit">Send<button>
  </p>
</form>
```

Just like the `<div>`, the `<p>` element also gives that default block level behaviour, which allows for an easy jumping off point for applying styling.

## Wrapping each input with a `<li>`

```

<form action="post.php" method="post">
  <ol>
    <li>
      <label for="user_name">Name</label>
      <input type="text" id="user_name">
    </li>
    <li>
      <label for="user_email">Email</label>
      <input type="email" id="user_email">
    </li>
    <li>
      <button type="submit">Send<button>
    </li>
  </ol>
</form>
```

This one is interesting and brings up a really good point. Each author of HTML, given the same design mock up (if that’s how you roll), could interpret it’s markup in completely different ways. When you think about it a form, or its elements to be precise, are in a way a list of entry fields, which presumably have an order of importance (hence the use of `<ol>` over `<ul>` ). This method, although giving the block level elements like the previous examples, also bring with it the need the override other things such as any default list padding and / or list numbers / bullet points.

## Some Research

On using `<div>`s as input field wrappers, as far as semantics go, here’s what the w3c say about the `<div>` element:

> The div element has no special meaning at all. It represents its children.
> 
> [w3c](https://www.w3.org/html/wg/drafts/html/master/grouping-content.html#the-div-element)

So with that said, you could probably get a good night’s sleep knowing that you’ve wrapped your inputs in `<div>`s. Or could you… …The w3c go on to say:

> Authors are strongly encouraged to view the div element as an element of last resort, for when no other element is suitable. Use of more appropriate elements instead of the div element leads to better accessibility for readers and easier maintainability for authors.
> 
> [w3c](https://www.w3.org/html/wg/drafts/html/master/grouping-content.html#the-div-element)

Okay, so is there a more suitable element that we could perhaps use instead of a `<div>`? Well as it turns out, yes. It looks as though our trusty friend, the <p> element is the most semantic. Check it one time:

> Any form starts with a form element, inside which are placed the controls. Most controls are represented by the input element, which by default provides a one-line text field. To label a control, the label element is used; the label text and the control itself go inside the label element. Each part of a form is considered a paragraph, and is typically separated from other parts using p elements…
> 
> [w3c](https://www.w3.org/html/wg/drafts/html/master/forms.html#forms)

Here’s the example they give on the w3c page, note the lack of a specified input type defaults to a standard text field:

```

<form>
  <p><label>name: <input></label></p>
</form>
```

What I also found interesting is the way the input is nested _inside_ the label, which actually implies the ‘for’ => ‘id’ relationship of the label and input elements.

## My Verdict

The way I would normally code up forms, was to use `display: block;` on the labels, letting them stack on top of their inputs, and style from there. But I think now, since each part of a form is considered a paragraph by default, as described on the w3c, I will be coding my forms up using wrapping <p>s in the future. I didn’t see the need to go into the for or against using <li> elements, since the paragraph tag is considered the most semantic. But like I said at the beginning, this isn’t me telling you what you should be doing, this is me describing a thought and research process into how I now code up my own forms. A final example to show the way I now code up HTML forms, including the `<fieldset>` tag:

```

<form action="post.php" method="post">
  <p>
    <label>Name <input type="text" name="user_name"></label>
  </p>
  <p>
    <label>Email <input type="email" name="user_email"></label>
  </p>
  <p>
    <label>Phone <input type="phone" name="user_phone"></label>
  </p>
  <fieldset>
    <legend>How would you prefer to be contacted?</legend>
    <p>
      <label>Phone <input type="radio" value="phone" name="pref"></label>
    </p>
    <p>
      <label>Email <input type="radio" value="email" name="pref"></label>
    </p>
  </fieldset>
  <p>
    <button type="submit">Send<button>
  </p>
</form>
```

I hope this helps some of you out.
