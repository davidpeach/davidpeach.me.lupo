---
title: "Plans for Progressive Enhancement"
date: "2014-10-17"
categories: 
  - "programming"
tags: 
  - "css"
  - "html"
  - "javascript"
  - "programming"
---

One of my pet peeves with some websites is when they simply don't work without having JavaScript enabled. I mean, okay, a large percentage of web-users will have JavaScript enabled by default?—?but that's not the point. In my day to day job I do a lot of work with [Opencart](http://web.archive.org/web/20150505075436/http://www.opencart.com/). Although it's great at providing an out-of-the-box ecommerce site?—?with the ability to adapt it to clients' custom requirements?—?just you try and buy something without JavaScript enabled; you simply can't.

## What is Progressive Enhancement?

Progressive enhancement is a way of providing _all_ visitors with a base _working_ experience of a site. We then layer on features as and when browser capabilities are available. An ajax "Add to Cart" button should be wrapped in a form that?—?by default?—?posts to a server script to add the product to your basket. The ajax should simply enhance that action by doing it without leaving the page. With the idea of progressive enhancement in mind, it means we can take advantage of the latest APIs. Progressive Enhancement allows us to use them whether or not they're supported in all browsers. By using a feature detection library such as [Modernizr](http://web.archive.org/web/20150505075436/http://modernizr.com/), we can see whether or not a particular feature is available and enhance that visitor's experience accordingly.

## A real world example

Televisions. Back when colour television was being introduced, people who still owned black and white TVs, weren't cut off from those new TV shows, they were simply shown the same programmes except with no colour. And now with HD television. Before I had an HDMI lead, if I watched an HD channel, it would simply show me it in normal definition. This is how we should be approaching what we build for the web.

## An example with a contact page map

So what if we were to build up a business' contact page using progressive enhancement? Let's see how we could approach it: Firstly?—?as a baseline?—?we could use the html `<noscript>` tag to contain within it an image of the business' location. The `<noscript>` tag will only be displayed if javascript is not present, and so provides a great natural fallback. Next we can write some javascript to insert an interactive map of the location, such as [Google Maps](http://web.archive.org/web/20150505075436/https://developers.google.com/maps/documentation/javascript/). Now we have taken care of visitors both with and without JavaScript support. But lets enhance it further! One of the many JavaScript APIs available to us now is [Geolocation](http://web.archive.org/web/20150505075436/http://caniuse.com/#search=geolocation). This enables us to get the current location of whoever is visiting the site?—?with their permission of course?—?and use it within the site. So if we wanted to we could first detect whether or not the visitor's browser had access to geolocation, and if so, use it to pinpoint their location on the map and display directions and distance to the business. With some forethought we can enhance peoples experiences of the sites we build. We can go beyond their initial expectations and improve upon them.

## My own plans for Progressive Enhancement

I am planning on taking advantage of some of these APIs on my own site. This will be in order to enhance its basic working functionality. I plan on adding in support for people to flag articles they have read. They could then see at a glance those still left to read. Perhaps even loading in extra articles they may be interested in; based on what they've read. This will be taking advantage of the [local storage API](http://web.archive.org/web/20150505075436/http://caniuse.com/#search=local storage), to store references to read articles in the visitor's browser. Using this same API I plan on using it to save fields entered into my contact form and then removing them once it's submitted. This way if a person is interrupted during filling my form out, it will allow them to continue where they left off. Try it yourself Why not have a go on your own site? Look at potential ways to improve the overall experience for those whose browsers support the features you would use.
