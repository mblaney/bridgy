Brid.gy ![Brid.gy](https://raw.github.com/snarfed/bridgy/master/static/bridgy_logo_128.jpg)
===

Got a web site? Post links to it on social networks? Wish
[comments/replies](http://indiewebcamp.com/comment),
[likes](http://indiewebcamp.com/like), and
[reshares](http://indiewebcamp.com/repost) showed up on your site too? Brid.gy
copies them back for you.

http://brid.gy/

Brid.gy uses [webmentions](http://www.webmention.org/), which are a part of the
[IndieWeb](http://indiewebcamp.com/) ecosystem, so your site will need to accept
webmentions for Brid.gy to work with it. Check out some of the
[existing implementations](http://indiewebcamp.com/webmention#Implementations)!

License: This project is placed in the public domain.


Development
---
All dependencies are in git submodules. Be sure to run
`git submodule init; git submodule update` after you clone the repo.

The tests require the App Engine SDK and python-mox.


Related work
---
* http://webmention.io/
* https://github.com/vrypan/webmention-tools
* http://indiewebcamp.com/original-post-discovery
* http://indiewebcamp.com/permashortcitation
* http://indiewebcamp.com/Twitter#Why_permashortcitation_instead_of_a_link


TODO
---

* store and render 'skipped' targets. (test: http://instagram.com/p/hc1xLpp72X/)
* replace t.co links with url entities
* move fetching replies (the fetch_replies kwarg to get_activities()) to
  activitystreams-unofficial
* handle 401 Unauthorized response from Twitter in Poll and disable source
* implement the other direction: convert incoming webmentions into API calls to
  post them as comments, etc.

Lower priority:

* detect updated comments and send new webmentions for them
* only handle public posts? (need to add privacy/audience detection to
  activitystreams-unofficial)
* clear toast messages?

Optimizations:

* cache some API calls with a short expiration, e.g. twitter mentions
* cache webmention discovery
* cache served MF2 HTML and JSON with a short expiration. ideally include the
  cache expiration in the content.
* ...and/or serve the comments (and activities?) directly from the datastore.
  drawback is that we don't get updated content.
* detect and skip non-HTML links before downloading, maybe with a HEAD request?
  e.g. https://twitter.com/snarfed_org/status/414172539837874176 links to
  https://research.microsoft.com/en-us/people/mickens/thesaddestmoment.pdf
