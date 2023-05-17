---
title: "Semi-automated PESOS From Google Play Music"
date: "2015-05-28"
categories: 
  - "programming"
tags: 
  - "indieweb"
  - "own-your-data"
  - "programming"
---

One of the core principles of the [IndieWeb](http://web.archive.org/web/20160412100649/https://indiewebcamp.com/) is owning ones own data. This is something I'm really into.

I use Google Play Music: all access on a daily basis to stream music. The service keeps track of how many albums I've listened to and which albums I've listened to; but I wanted this data, or as as much of it is I could, on my own site. But sadly Google don't provide an API for querying this data.

I have tried different ways of scraping my old listening data from the site but to no avail. Plus that past data only shows a count of each song - it doesn't keep any listen dates.

So what I have put in place now is a way for me to semi-automatically keep track of the albums I listen to - both the dates of each listen and the total counts of each album.

I thought I'd share my method just in case anybody else wanted to do the same.

Note: If you need help with implemented this, please do [get in touch](http://web.archive.org/web/20160412100649/mailto:hello@davidpea.ch?subject=Pesos%20Google%20Play%20Music%20post). I'll do my best to help.

## The Task

To keep track of albums I listen to on Google Play: All Access as and when I listen to them to make a timeline of music listened to on my own website. This way not only do I own that data, I also have at least some information on past albums I've listened to. This way I can take that data anywhere - whether I choose to use a different stream service or even if Google stop providing the service at any future time.

## The way I've gone about it

Since I listen on my phone 90% of the time, I have added a custom bookmarklet, using [this free bookmarklet app](http://web.archive.org/web/20160412100649/https://play.google.com/store/apps/details?id=com.kurtchen.android.bookmarklet.free&hl=en), that allows me to easily share the URL of the current listening to album to a custom URL end point. Using that shared information I then save the album data I need along with the dates I listened to it.

### Setting up the bookmarklet

With the app that I use, I tap to add a new custom service, give a name and base url and save it.

The title and url parameter names can be left as is - these are what are passed through to your end point in order to do what you need with them. In my case I just use the url to the album that is passed over to scrape the public-accessible page of that particular album to get the title; artist; basic meta info. This is because when I am listening to the album I am logged in, but my website that then scrapes for the content isn't.

### The process of using the bookmarklet

Once you have saved your custom bookmarklet service and given it a name, you will then be able to select that service from within the share option of the Google Play Music app.

1. Open the Google Play Music app on your device

3. Browse to a particular album

5. Tap the boldest set of three dots - these will open the album options modal.

7. In that modal tap share

9. Scroll through the share choices and tap the one that is labelled 'My Services'

11. A new modal should pop up with any custom services you have added in the Bookmarklet app

13. Click your chosen custom service and it will share the url of that particular album to your specified end point.

So that will now send the request over to your custom end point.

So I suppose we should now put some logic in place in order to actually do something when the URL is received by the website.

### Listening for the album share

Essentially at your particular end point, whether it is a dedicated file or an endpoint that is routed to a controller (in my case I am using Laravel 5, which routes my endpoint to a controller) you will need to listen for the url that will hit your end point as a get parameter and act accordingly.

On my own website, when the request comes in from the share action, I use the URL received (which is a members-only URL for listening to the album) to create Google's public-accessible URL for the album (which gives visitors options to buy it but not stream). Luckily the URL structure is only changed in one slight way, which makes it easy to alter it to suit our needs. The base URLs differ but the unique identifier on the end of the URL is the same.

Members URL e.g : https://play.google.com/music/listen#/album/B2uruozjpnv5whcvc54o7rufjc4

Public URL e.g. : https://play.google.com/music/preview/B2uruozjpnv5whcvc54o7rufjc4

So from that you could split the members URL using the forward slash as a delimeter, then put the last part returned on the end of the public base URL (https://play.google.com/music/preview/)

Once I form the public-accessible URL, I then scrape that page using one [PHP library](http://web.archive.org/web/20160412100649/https://github.com/jonnnnyw/php-phantomjs) and then parse the html using [another library](http://web.archive.org/web/20160412100649/https://github.com/matgargano/simplehtmldom). Like I mentioned I use Laravel 5 for my website, but this could be implemented in any website. What I have done is added the full code for my controller that handles the share end point [here](http://web.archive.org/web/20160412100649/https://gist.github.com/davidpeach/91bad583aeda03e36611) so you can take it and alter it to your needs.

I realise that when people give a method of doing something that is different to your particular set up it can be frustrating. Like an implementation in WordPress that you want to do in Joomla! Which is why I encourage you to [contact me](http://web.archive.org/web/20160412100649/mailto:hello@davidpea.ch?subject=Pesos%20Google%20Play%20Music%20post) if you want to implement this into your own website and I'll do my best to help you.

I wont go through the ins and outs of using those two libraries or including them with composer as it's outside the scope of this post. But like I say, contact me if you need help.

You can view the full code for my end point controller [here](http://web.archive.org/web/20160412100649/https://gist.github.com/davidpeach/91bad583aeda03e36611).

Best of luck! And if you want to learn more about owning your own data, head over to the [IndieWebCamp](http://web.archive.org/web/20160412100649/https://indiewebcamp.com/).
