---
date: 2022-10-01T19:17:57.923Z
author: Stefan Hayden
layout: post
permalink: /blog/2022/10/01/Quick-jekyll-Posts-with-Bookmarklet/
categories:
  - web
---

I've made a [/new-post-bookmarklet.html](bookmarkelt to add posts to this jekyll site). It propt me for a title and then opens up a new github file to add what ever content I want.

I hope this get me to post more here. The code is simple and you could easlily modify it for your jekyll site as well. You can use a [https://caiorss.github.io/bookmarklet-maker/](bookmarklet site to get it to work for you).

```
var isoDate = (new Date()).toISOString();
var date = isoDate.split('T')[0];
var d = date.split('-');
var dataPermaLink = d.join('/');
var title= prompt("title", "").replaceAll(/([&$\+,:;'"=\?@#\s<>\[\]\{\}[\/]|\\\^%])+/g, '-');

var filename = date + "-" + title + '.md';

var html = [
'---',
'date: '+ isoDate,
'author: Stefan Hayden',
'layout: post',
'permalink: /blog/'+ dataPermaLink  +'/'+ title +'/',
'categories:',
'  - web',
'---',
].join('%0A');


window.location.href = "https://github.com/stefanhayden/stefanhayden.github.io/new/master/" + "?filename=_posts/" + filename + "&value=" + html;
```
