---
title: "Autofill share fields for status posts"
date: "2014-10-28"
tags: 
  - "indieweb"
  - "php"
  - "programming"
  - "wordpress"
---

Whenever I write a status update I write it on my own website. They then get syndicated out to services like Facebook or Twitter. For this I use a plugin called [SNAP](http://web.archive.org/web/20150505075823/https://wordpress.org/plugins/social-networks-auto-poster-facebook-twitter-g/), which posts to my chosen social networks. One thing that I found slightly fiddly was the quick posting of status updates. I would first type the update in the content area, then paste it into two other places — the share boxes for both twitter and facebook.

SNAP does allow the use of [formatting tags](http://web.archive.org/web/20150505075823/http://www.nextscripts.com/snap-features/message-formatting-tags/) for when posting to linked networks, but my configuration is to show the title and permalink when sharing unless it is a status update, in which case I want the full body text to be copied over. Although okay on desktop, it is a bit fiddly on mobile. So I wrote a small piece of JavaScript to auto fill the fields I was pasting into, but **only if the status post type is selected**. The fields in the JavaScript below are specific to the SNAP plugin. Please change the IDs of the target fields to suit your needs. `/your_theme/js/status-notes-autofill-fields.js:`

```

(function($, document, window, undefined){
	$(window).on('keyup', function(){
		var excerpt		=	$('#excerpt');
		var content		=	$('#content');
		var status_radio	=	$('#post-format-status');
		var twitter_share	=	$('#tw0SNAPformat');
		var facebook_share	=	$('#fb0SNAPformat');
		if (status_radio.is(':checked')) {
			if (excerpt.length) {
				excerpt.text(content.val());
			}
			if (twitter_share.length) {
				twitter_share.text(content.val());
			}
			if (facebook_share.length) {
				facebook_share.text(content.val());
			}
		};
	});
}(jQuery, document, window));
```

`/your_theme/functions.php:`

```

function my_enqueue($hook) {
	if ( 'post-new.php' != $hook ) {
		return;
	}
	wp_enqueue_script( 'my_custom_script', get_stylesheet_directory_uri() . '/js/status-notes-autofill-fields.js' );
}
add_action( 'admin_enqueue_scripts', 'my_enqueue' );
```

In the code above you'll notice I auto fill the excerpt field as well. This is because I am using another plugin that adds rel="syndication" links to the end of `the_content()` and I had one place where I didn't want that, so I just duplicate the content into the excerpt. Once you have incorporated the above code into your admin, simply select the 'status' post format and begin typing your status update into the content area. The other fields will now auto fill. As always, any questions, please don't hesitate to [give me a shout](http://web.archive.org/web/20150505075823/http://davidpeach.co.uk/hire/).
