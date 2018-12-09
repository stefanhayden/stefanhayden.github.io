---
id: 1257
title: Books I Am Reading now has Javascript Embeds
date: 2008-10-13T11:58:12+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=1257
permalink: /2008/10/13/books-i-am-reading-now-has-javascript-embeds/
categories:
  - Books I Am Reading
---
Over at <a href="http://www.booksiamreading.com">Books I Am Reading</a> many people have ask for an easy way to put books on their website so I have moved this feature up in the queue. If you go to the account section you will find 4 embeds: Recent Activity, Currently Reading, Want to Read and Finished Reading.

Just paste that code in to any website that lets you add javascript. Many sites do not allow javascript but most blog platforms do like wordpress or blogger.

If you look at the code there is a <b>count</b> value that you can set to any number to show more or less books.

let me know if there is anyway this widget can work better for you.

<b>Update:</b>The HTML is extremely basic and can be easily styled to your liking. Here's an example:

<script type="text/javascript" src="http://booksiamreading.com/widget/stefanhayden?count=10&type=wanttoread"></script> 
<style>
#booksiamreading ul li {list-style:disc inside; margin-left:20px; line-height:1.5em;}
#booksiamreading .biar_title { font-weight:900; font-size:130%; line-height:2em;}
</style>

and here is the CSS I used:

<code>
#booksiamreading ul li {list-style:disc inside; margin-left:20px; line-height:1.5em;}
#booksiamreading .biar_title { font-weight:900; font-size:130%; line-height:2em;}
</code>
