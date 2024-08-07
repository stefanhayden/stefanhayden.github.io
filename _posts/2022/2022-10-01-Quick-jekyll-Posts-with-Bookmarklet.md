---
date: 2022-10-01T19:17:57.923Z
author: Stefan Hayden
layout: post
permalink: /blog/2022/10/01/Quick-jekyll-Posts-with-Bookmarklet/
categories:
  - web
---

I've made a [/new-post-bookmarklet.html](bookmarkelt to add posts to this jekyll site). It propt me for a title and then opens up a new github file to add what ever content I want.

I hope this get me to post more here. The code is simple and you could easlily modify it for your jekyll site as well. You can use a [bookmarklet site to get it to work for you](https://caiorss.github.io/bookmarklet-maker/).

```
var isoDate = (new Date()).toISOString();
var date = isoDate.split('T')[0];
var d = date.split('-');
var dataPermaLink = d.join('/');
var t = prompt("title", "");
var title = t.replaceAll(/([&$\+,:;'"=\?@#\s<>\[\]\{\}[\/]|\\\^%])+/g, '-');

var filename = date + "-" + title + '.md';

var html = [
'---',
'date: '+ isoDate,
'author: Stefan Hayden',
'title: ' + t,
'layout: post',
'permalink: /blog/'+ dataPermaLink  +'/'+ title +'/',
'categories:',
'  - web',
'---',
].join('%0A');


window.location.href = "https://github.com/stefanhayden/stefanhayden.github.io/new/master/" + "?filename=_posts/" + d[0] + "/" + filename + "&value=" + html;
```

Updated 8/7/23024 to put new files in a year directory