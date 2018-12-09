---
id: 876
title: 'Tethered Data: Not Really Portable'
date: 2008-05-16T10:18:27+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=876
permalink: /2008/05/16/tethered-data-not-really-portable/
categories:
  - web
---
I'm glade a lot of these <a href="http://www.techcrunch.com/2008/05/16/data-portability-its-the-new-walled-garden/">attempts at data portability</a> from google, myspace, and facebook have been <a href="http://radar.oreilly.com/archives/2008/05/myspaces-data-availability-is.html">getting bad press</a>. They are at best halfhearted attempts at data portability with the data still tethered at the original site.

I am at best a modest programmer and as I build <a href="http://www.booksiamreading.com/">Books I Am Reading</a> (BIAR) I am looking for different ways to add features that are fully integrated with out needing to reinvent the wheel. If I could add a friends module I would love to. But they are not giving out friends data, just links to friends on other sites. I don't need links to myspace. I need links to other profile on BIAR.

Recently I put a lot of thought in to adding Disqus comments to the site. I was excited about not needing to build a comment system for a few days. Disqus has a good comment module with great features.

But it is just not able to integrate enough to truly feel part of a site. If I log in there is no way to also log you in to disqus forcing people to log in twice. Most likely most comments would end up being anonymous. There is also no easy way to associate a comment thread with a profile and have the person emailed. Perhaps disqus was not meant for this application but it illustrates a common problem with how social modules are being built.

These will not meet the requirements of data portability until all these modules can freely talk to one another. The question is how much of Books I Am Reading will I have to build before these easier options become available? Hopefully the data portability wars will force it to happen sooner then later. 