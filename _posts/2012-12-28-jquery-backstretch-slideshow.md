---
id: 1657
title: jQuery Backstretch Slideshow
date: 2012-12-28T11:51:12+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=1657
permalink: /2012/12/28/jquery-backstretch-slideshow/
categories:
  - Uncategorized
---
<a href="https://github.com/srobbin/jquery-backstretch">Backstretch</a> is a pretty great slideshow library both because of it's features as well as the small amount of code it is all done in. But when implementing a code light library you will always run in to the problem of needing the library to do things that it does not have features for. And for that reason I'm going to highlight some of the features I built in to my own fork of Backstretch, all of wich are also <a href="https://github.com/STHayden/jquery-backstretch">documented on github</a>.

<h2 style="margin-bottom:10px; font-size:16px;"><strong>Options:</strong></h2>

<strong>Pause:</strong> By default the slideshow just starts to play but for us we wanted to start out with it just sitting on one slide.

<strong>lazyload:</strong> By default all of the images you pass in are loaded. This is not great for page speed and so this option only loads image when the slideshow goes to show the image or specifically requested though a call.

<strong>start:</strong> The array of images you pass in will always be shown in that order. But if you pass in an index then the slideshow will start at that point.

<strong>default_height &amp; default_width:</strong> These are actually in the original library but were undocumented. This just speeds up getting the slideshow to draw it self correctly if you know the height and width in advance.

<h2 style="margin-bottom:10px; font-size:16px;"><strong>API:</strong></h2>

<strong>cacheNext() &amp; cachePrev():</strong> With lazyload turned on the next image will not start to load until that slide is requested. With this call you can choose when is best to preload that next or previous image. I always keep the next image in the slideshow cashed and ready to show.

You can <a href="https://github.com/STHayden/jquery-backstretch">find all these features on my own fork of Backstetch</a> where I will also attempt to keep it up to date with the main repo.