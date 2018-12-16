---
id: 963
title: Page Bookmarks for Tor HTML Online Books
date: 2008-07-24T11:36:44+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=963
permalink: /blog/2008/07/24/page-bookmarks-for-tor-html-online-books/
categories:
  - books
  - web
---
<a href="http://tor.com/index.php?option=com_content&view=blog&id=577">Tor has put tons of awesome books online</a>. Though I don't really like reading books on my PC I checked out the HTML versions and was surprised there was no way to save your place. 

The HTML on the pages is well formed and each page is marked off ready for bookmarking. Here is a bookmarklet to add the page numbers. When you are ready to stop reading just save the link for the page to jump back in to the book where you left off.

Drag this link: <b><a href="javascript:void((function(){j=document.createElement('SCRIPT');j.src='http://code.jquery.com/jquery-latest.pack.js';document.getElementsByTagName('HEAD')[0].appendChild(j);setTimeout(function(){$('a').each(function(e){$(this).text($(this).attr('id'));$(this).attr('href','#'+$(this).attr('id'));this.style.position='absolute';this.style.left='10px';});},5000);})())">Tor HTML page numbers</a></b> to your Firefox bookmark toolbar, then just click it on the HTML of a Tor book to add page numbers. Try it out on <a href="http://hbpub.vo.llnwd.net/o16/video/olmk/tor.com/BuckellCRHTML/Buckell,%20Tobias%20-%20Crystal%20Rain.html">Crystal Rain by Tobias Buckell</a>.

Here is the code:

<pre style="overflow:scroll; width:460px; border:1px solid; padding-top:10px; margin-bottom:10px;"><code >javascript:void((function(){j=document.createElement('SCRIPT');j.src='http://code.jquery.com/jquery-latest.pack.js';document.getElementsByTagName('HEAD')[0].appendChild(j);setTimeout(function(){$('a').each(function(e){$(this).text($(this).attr('id'));$(this).attr('href','#'+$(this).attr('id'));this.style.position='absolute';this.style.left='10px';});},5000);})())
</code></pre>