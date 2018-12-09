---
id: 36
title: 'Browsershots: a quick review'
date: 2005-07-06T02:18:49+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=36
permalink: /2005/07/06/browsershots-a-quick-review/
categories:
  - design
  - resources
  - web
---
One of the hard parts of web design is conditioning yourself to out put code that works in all browsers. I don't know how many people can code web sites with out needing to check to see if the code actually works, but I am not one of those people. Searching the internet for solutions there are services to check <a href="http://www.masternewmedia.org/2003/05/22/browser_compatibility_testing_online.htm">how</a> <a href="http://www.browsercam.com/Pricing.aspx">your page</a> <a href="http://www.crossbrowsing.com/price.asp">looks</a> in other browsers but they are all rather expensive for little college graduates like me.

The other solution that some subscribe to is called the "<a href="http://www.netmechanic.com/browser-photo/tutorial.htm#2.2">Avoid the Cutting Edge</a>" approach. For the most part I am appalled by this approach as I can not think of any other industry that advocates staying away from new and better ways of doing business. I feel an "Understand the Cutting Edge" is a better outlook to have. It's important to know what the new technologies can do. Yet no matter how fancy a new feature might be if it does not work in the dominant browser (currently IE) then the feature is dead in the water. Though I am waiting for the "<a href="http://en.wikipedia.org/wiki/Killer_app">Killer App</a>" that will propel Firefox to the forefront. Some where out there is an idea that can't run on IE and if implemented for everyone else the mass exodus of IE would begin.

Until that killer app comes I will continue to push IE as far as it will go and will need all the help I can get checking to make sure my web pages work in every browser with out spending a fortune. A long time coming some one has finally started an open source project that let you see your site in different browsers.
<a href="http://browsershots.org/">
Browsershots</a> works by letting you submit a URL and it renders out PNGs of what it looks like in different browsers. I'm unclear exactly how it works but from what I surmise it has a central server that dishes out jobs to people who are running the scrip on their computer similar to how <a href="http://setiathome.ssl.berkeley.edu/">Seti@Home</a> works. I downloaded the script and tried to see if I could figure out how to run it off my <a href="http://www.dreamhost.com/r.cgi?sthayden">dreamhost account</a> but did not have any luck. The project is still in it's baby stages, though it has already handled some very large hits from del.icio.us and the like. When you submit your link it gets put in a pool and it renders out PNGs <a href="http://browsershots.org/recent/">which you view on their</a> site. This is a very public way of testing websites and would especially be a problem for larger projects that need to be kept secret. It would be nice if there was an easier way to run it privately, which it says it can do but it is not documented well enough for me to figure it out. Perhaps it could use a wiki for documentation to help speed the writing up as I would love to run my own version.

While it tells you the stats that the PNG was rendered with next to the image it does nothing to help you with any display problems you might have. Perhaps it might be a pipe dream but it would be amazing if it pointed out likely problems that different browsers will have with the code (XHTML, javascript, CSS) that you have written. I ran in to my own error as I got the error shown below and can't figure out why. I get it for both my site and the one I'm working on.  Let me know if you figure the problem out because as of right now I'm stumped.

<img src="http://www.stefanhayden.com/blog/wp-content/error07052005.gif" alt="my stange error" />