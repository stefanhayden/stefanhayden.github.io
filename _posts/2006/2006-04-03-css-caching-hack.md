---
id: 139
title: CSS Caching Hack
date: 2006-04-03T06:53:16+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/2006/04/03/css-caching-hack/
permalink: /blog/2006/04/03/css-caching-hack/
categories:
  - blog
  - design
  - resources
  - web
---
If you change the HTML and the CSS of a page there is a decent chance that a user will get the new HTML but not the new CSS. This is especially true for sites with high usage and users that come back to the site several times a day.

If they only get the new HTML but not the new CSS then the site will break, the user will get confused, and you will look unprofessional. On the development site of this the problem is already solved. Having a Dev server as a place to test code is standard practice but how does this translate to CSS?

The problem is that the CSS is cashing on the client side and there isn't an obvious way of telling the browser to un-cache it. Luckily the key word is obvious. Though it's not in wide use there is a quick hack that will keep your CSS as fresh as your HTML.

The trick is to pass a variable on the end of the CSS file like so:

<code>&lt;link rel="stylesheet" xhref="http://www.stefanhayden.com/style.css?version=1"      type="text/css" /&gt;</code>

What does ?version=1 mean? This is what a URL looks like if it's passing a GET variable from one page to the next. To the browser it means the page is dynamic and it needs to get a new version because code may have changed. The browser has no way of knowing if the CSS file is actually dynamic or not.The trick is to change the number each time you update the CSS file to make sure the browser always downloads the new code.

When a browser looks to see if it has anything cashed it compares file names. If you have "style.css" in your cashe then it's not going to download it again. But if the browser compares "style.css?version=1" to what the new HTML is "style.css?version=2" then the browser thinks they are different files and needs to download the new CSS file.

The other reason this works is because you can add anything you want after the ? and the web page just ignores it unless it's an actually variable on the page.

This seems to be a really good solution to version css and yet so few seem to use it. The only 2 sites I know of who do is <a href="http://www.odeo.com">Odeo</a> and <a href="http://www.sconex.com">Sconex</a>. Yet clearly we are in the middle of a big web boom with CSS being used every where. How are other people versioning their CSS so it doesn't break the user experience?

In general I can't see to many other solutions. You could make the CSS file parsed by the web server and pass headers with different cacheing info. I have not tried this but I'll bet the browser would still cache the file as it does not know it is dynamic even if it is. You could rename the CSS file with .php but clearly no one is doing that and I'll bet there is a browser out there that would not apply the styles because of that.

No every one gets to work on a large production site but with so many jumping in the area and quickly updating the service I'm surprised this subject has not been covered.

<tags>odeo, sconex, css, versioning, hack</tags>