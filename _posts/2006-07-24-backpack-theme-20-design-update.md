---
id: 173
title: 'Backpack Theme 2.0 &#8211; Design update'
date: 2006-07-24T20:57:48+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/2006/07/24/backpack-theme-20-design-update/
permalink: /blog/2006/07/24/backpack-theme-20-design-update/
categories:
  - blog
  - design
  - personal
  - web
---
Well this redesign is a long time in the making. There are still plenty of loose edges to clean up but as long as you don't dig too deep everything should be fine.

This redesign is feature rich with lots of additional feeds and functionality.

You'll notice to the right my info from <a href="http://www.last.fm/">Last.fm</a>, <a href="http://www.trackslife.com/">Trackslife</a>, <a href="http://www.netflix.com/">Netflix</a>, and links from <a href="http://del.icio.us/">Del.icio.us</a>. Since I'm using all of these services I might as well put them in one place where everyone can see.

The easiest way to integrate an RSS feed is with <a href="http://magpierss.sourceforge.net/">MagpieRSS</a>  which made adding Del.icio.us and Netflix super easy.

Anything that's not in an RSS feed become a bit more difficult. Tackslife has an RSS feed but it's horribly formed for getting out small bit of information.

Last.fm only has weekly artists in an XML file and while it would be nice if MagpieRSS supported XML it dies not.

Anything not in an RSS file I got the info with cURL and the pregmatch function <a href="http://www.stefanhayden.com/blog/2005/05/31/screen-scrape-an-rss-feed-with-php/">as I've outlined before</a>.

One last feature that is a great trick is how the site re-sizes if they screen is smaller then 1024. Re-size to 800 and the 2 columns will turn in to 1. Thanks to <a href="http://www.collylogic.com/?/comments/redesign-notes-1-width-based-layout/">Collylogic</a> for the tip on how to make it happen.

All and all I'm very happy with the final outcome and I'd love to help anyone who wants similar RSS integration in to their website. I'd love to hear any feedback!