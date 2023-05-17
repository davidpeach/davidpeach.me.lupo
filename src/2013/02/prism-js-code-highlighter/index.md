---
title: "Prism JS Code Highlighter"
date: "2013-02-14"
tags: 
  - "css"
  - "html"
  - "programming"
  - "web-development"
---

Before [Prism JS](http://web.archive.org/web/20150505075606/http://prismjs.com/), I'd had no previous experience with code highlighters. I’d seen them in use on other web sites but never looked into them until recently. I remembered hearing about Prism JS from [Lea Verou](http://web.archive.org/web/20150505075606/http://lea.verou.me/) on her twitter feed. After seeing it in action I kept it in the back of my mind — knowing that I would use it in the future for my own examples. Here is an example of Prism JS in action:

```

    if( awesome ){
      console.log('This is Awesome');
    }else{
      $('body').addClass('give-me-awesome');
    }
  
```

I'm sure you'll agree that it makes code examples look pretty dang good. All that’s needed to get _your_ code snippets looking this nice is two files — the JavaScript and CSS files from the Prism JS site — and three easy to follow steps.

## Getting it Working

Firstly [grab the JavaScript and CSS files](http://web.archive.org/web/20150505075606/http://prismjs.com/download.html) from the Prism JS download page and link them into your page. You will notice on the Prism download page that they've got  — at the time of writing — six different themes to choose from. This guide will work with any of the themes so choose the theme that tickles your fancy.

```

<style rel="stylesheet" href="css/prism.css">
<!-- Or include it as part of your main stylesheet / use as a sass partial -->
<script src="js/prism.js"></script>
<!-- Or include it as part of your main script file -->
  
```

Once you've downloaded and linked the style sheet and JavaScript, make sure you mark up your code snippet in the following way.

```

<pre>
  <code>
    if( awesome ){
      console.log('This is Awesome');
    }else{
      $('body').addClass('give-me-awesome');
    }
  </code>
<pre>
  
```

I have used some dummy JavaScript as an example, but Prism JS supports many languages for which it will intelligently highlight. The third and final step is to tell Prism which language it will be highlighting. This is done simply by adding the relevant class to the <code> element as in the next example.

```

<pre>
  <code class='language-javascript'>
    if( awesome ){
      console.log('This is Awesome');
    }else{
      $('body').addClass('give-me-awesome');
    }
  </code>
<pre>
  
```

As mentioned, the languages that Prism JS can highlight are numerous, and can be included when you download the files by clicking the relevant options on the [download page](http://web.archive.org/web/20150505075606/http://prismjs.com/download.html). The classes used for the various languages follow the same pattern when adding them to your markup: language-{LANGUAGE\_NAME}. For example:

```

<code class='language-markup'>
<code class='language-css'>
<code class='language-javascript'>
```

And there you have it. Prism JS is a great tool for giving you smooth-looking code highlighting. Make sure you visit the [Prism website](http://web.archive.org/web/20150505075606/http://prismjs.com/) to read about all of it’s functionality and to see all the themes and languages that are available!
