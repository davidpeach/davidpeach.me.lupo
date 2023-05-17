---
title: "Blogging Via SMS To Your Website With Twilio"
date: "2015-09-24"
tags: 
  - "my-website"
  - "php"
  - "programming"
  - "twilio"
---

The end goal of this guide is to be able to send a text message to a Twilio number - a phone number given to you by Twilio - and have whatever message you send it get passed over to an endpoint on your website.

The reason behind this, is that I like the idea of microblogging every now and again - sort of like tweeting - except I always post to my website first. The only thing is though, is that sometimes if I'm out and about my 3g/4g signal may drop out. However my phone reception is generally a bit better. Then when I saw that Jeremy Keith had already done this same thing, I had a go myself.

## Get a free Twilio account

Firstly go to the Twilio website and sign up for a free account. I have found that Twilio's prices are very reasonable ($1 per month for a twilio phone number and $0.0075 per text message you send to it)

Once you have your account, get yourself a Twilio number from within the dashboard and make a note of it. Then head to the numbers page from the dashboard top navigation and click on your new number.

This should bring you to a configuration screen for that number.

Go down to the bottom of this page to the section called SMS & MMS - more specifically the field labelled 'Request URL'. Whatever full URL you put in here, will be pinged by twilio when your number receives a message.

If you know what the endpoint will be i.e. http://mysite.com/smstarget, then add it now and save. If not, you will need to come back here once you have set your endpoint up and add it.

## Set up your target endpoint

Whatever endpoint you set up, and tell Twilio about, doesn't need that much work doing to it,

Twilio will basically POST you a small array of data. Inside which you will find the keys 'Body' and 'From', amongst others. I'm currently only using these two in my own site at the moment. I'm checking the 'From' value to ensure that the number that sent the message to my Twilio number came from my own phone, and then storing the 'Body' as the content for a blog post on my site.

And that's all I had to do to get it set up.

## Test it

Once you have added your logic to check and insert the 'Body' content as a blog post on your website, you can test it by sending a text message from your phone to your Twilio number - just make sure you check for this number in your endpoint logic for some security.

I have not added any code examples as the logic is essentially just inserting the body text into you database - so just incorporate that into your site in whichever way makes sense for you.

Thanks for reading.

## Tagged for extra Credit

On my website I also use post tags when blogging from the web UI. I wanted to be able to tag posts when I 'text them in'. So when I want to add tags, I format my text message like so:

`This is the blog message --tagone,tagtwo,tagthree`

I then explode the 'Body' value on the '--' delimeter, if it has one, and then add each comma-separated tag to that new post.
