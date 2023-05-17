---
title: "Syndicating your content with Wordpress"
date: "2014-11-06"
tags: 
  - "indieweb"
  - "my-website"
  - "own-your-data"
  - "php"
  - "wordpress"
---

If you have decided to become a part of the IndieWeb, then you have decided to make your own personal website the home of all, if not most, of the on line content you publish - whether that be an article, a tweet or anything in between. But just because you're not writing your status updates directly into twitter any more, it doesn't mean that you can't still _share_ your content to Twitter - or indeed any third party service. After all you will still have followers on those social silos and you wont want to lose contact with them. This act of sending a copy of your original content out to other places is known as syndication.

## What is Syndication in the IndieWeb?

Syndication is the act of posting copies of your self-hosted original content to third party services like Twitter or Facebook.

The immediate benefit of syndication is that you have full control over all of your content. If you only write updates on Twitter or Facebook - and they close their doors or start filtering content in some way - then you're not having any amount of control over how or when that content is shown. With having it's original home on your own website, that content is under your full control. The copies you syndicate out are just that - copies.

## Automating syndication with WordPress

If you have read [my previous post on setting up my own website](http://web.archive.org/web/20150505075450/http://davidpeach.co.uk/wordpress-as-my-indieweb-foundation/), you will know that I use WordPress to power it. This is not a prerequisite, but it does enable you to start publishing within minutes of deciding to use it; and with its plugin ecosystem, it means that it has a very small learning curve to get yourself on the IndieWeb. For syndicating my content to my own third parties of choice, I use a plugin called [SNAP](http://web.archive.org/web/20150505075450/https://wordpress.org/plugins/social-networks-auto-poster-facebook-twitter-g/). SNAP makes it easy and flexible to share posts with social networks like Twitter, Flickr, Facebook and a host of others. There are many plugins out there that do the same sort of thing, but this is the one that I use and it plays well with other IndieWeb plugins, which I will come to a little later on.

## SNAP Plugin

Please Note: [I have forked the SNAP plugin](http://web.archive.org/web/20150505075450/https://github.com/davidpeach/social-networks-auto-poster-facebook-twitter-g) to allow posting replies to other tweets and have them show up as part of the conversation on Twitter. If using my fork of it, download the zip from the Github page, drop the unzipped folder into your plugins folder and activate. In order to write a status update as a reply to a tweet, simply add a custom meta field in the post with the key of 'in\_reply\_to\_id' and paste in the ID of the tweet. When you then publish the post it will copy to twitter as part of the replied-to tweet's conversation. Alternatively, in your WordPress admin, go to add a new plugin and search for "snap". You should find it on the first page - its full title will be NextScripts: Social Networks Auto-Poster Install it and follow its instructions for configuring it to post to your chosen social networks.

When you add a social network to post to, it will give you a link that contains detailed instructions on getting it synchronized with that particular network.

## Making the link between the original and the copy

The second step in syndicating original content from your website is to create a link between it and any copies you have made. This can be done a couple of different ways but the only way I have experience with is using the attribute of `rel="syndication"`. To accomplish this, all that's needed is to link to syndicated copies of a post from that post's permalink page and give that link the syndication attribute. The example below can be found at [this page](http://web.archive.org/web/20150505075450/http://davidpeach.co.uk/note-1530/).

```

<a href="https://twitter.com/davidpeach1/status/530136972036022273" rel="syndication">Copied to Twitter</a>
```

Now there is a semantic link between the original post and the copy on Twitter. With WordPress there is a way to automate this with a plugin called rel-syndication for WordPress.

## Rel Syndication plugin for WordPress

Now, normally I would say search the plugins repository from inside your admin. However, the version in there is 0.1 and - at the time of writing - version 0.3 is available on the [plugin's Github repository](http://web.archive.org/web/20150505075450/https://github.com/jihaisse/wordpress-syndication). Simply download the plugin zip from there and add the unzipped folder into your plugins folder. What this plugin will then do, once activated, is add links beneath your content - one for each of the syndicated copies in the same format as the example above.

It reads the information brought back by the SNAP plugin to determine where copies have been syndicated to. The next thing to do now, is to automatically pull into our WordPress admin, replies to those syndicated copies. So if you copy a status update over to Twitter, and someone replies / favourites that tweet, have that reply / favourite be pulled into your site. But that, my friend, will be in future post coming very soon. I hope this has helped some people out there to start owning their content and copy it out to their chosen networks. As always, any questions you may have [don't hesitate to contact me](http://web.archive.org/web/20150505075450/http://davidpeach.co.uk/hire/).
