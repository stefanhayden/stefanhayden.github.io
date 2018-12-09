---
id: 121
title: Google moving toward standards
date: 2006-02-23T19:17:28+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/2006/02/23/google-moving-toward-standards/
permalink: /2006/02/23/google-moving-toward-standards/
categories:
  - design
  - web
---
Google has come out with a WYSIWYG editor to go along with there brand new web hosting service. In general the service is mediocre and on par with most other services. 100 <span class="hm" id="misp_compose_2">mbs</span> of storage with the ability to up load images. The editor is smooth though lacking in features. Clearly there is room for improvement and a straight forward path of features to add. This is a product aimed at people who don't know what they are doing and so no web designer need to worry about losing their jobs yet.

What is interesting is the code it created. Google is know for writing bad code and discarding standards. The Google front page alone, in all it's bleakness, has 66 errors. Making a quick page and running through a validator shows only 10 errors which is  a large reduction.

Looking deeper in the the code you can see they have put some good effort in to making this a new age editor. About 95% of the design in done in <span class="hmd" id="misp_compose_6">CSS</span>. Al the code is very readable though there are browser hacks abound and it will be interesting to see how that degrades with time.

I don't know if they are storing the entire text file of HTML or generating the page on the fly. If it's generated on the fly they can update the <span class="hm" id="misp_compose_7">CSS</span> as needed but if it's all saved to a static file they might be saving hacks that will one day be a big problem to fix.

While no <span class="hm" id="misp_compose_8">techy</span> person is going to be overly impressed buy this release I think it's mostly a good thing that will hopefully help people who don't know what they are doing make better formed websites.

<tags>google, pagecreator, w3c, validate</tags>