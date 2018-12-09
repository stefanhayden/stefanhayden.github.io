---
id: 10
title: Why I hate Firefox
date: 2005-03-09T21:22:56+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=10
permalink: /2005/03/09/why-i-hate-firefox/
categories:
  - web
---
Okay, so I like Firefox but I feel like I’ve had what was definitely a bad user experience. If I wasn’t as computer literate as I am I might even have run back to IE. I’ve always had a problem with pop ups and trying to let certain ones through while keeping the block pop option on. I’ve also had problems with slow performance while using the options menu. Recently I also noticed a large memory leak that kept the Firefox process very bloated. The thing that finally put me over the edge was how JavaScript was not opening the new windows it was supposed to.

Finally I decided to reinstall Firefox in hope it would fix whatever had broken. I uninstalled 1.0.1 and reinstalled the only version I had on hand which was 1.0PR. Rule number 1: don’t install old Firefox versions. The problem was now it worked even worse then before. The window opened and did nothing, acted like it was frozen, but said it was running in the task manager. 

Looking on the Firefox knowledge base I found the <a href="http://kb.mozillazine.org/Browser_will_not_start_up">browser will not start article</a>. Not exactly what I want but close enough. That’s where I learned about the <a href="http://kb.mozillazine.org/Profile_folder">profile folder</a> that holds all the options for different profiles that use Firefox. I’m the only one who uses my computer and just had it set as the default user. It turns out this is also where your extensions are saved. I had an idea that it might have been an extension but could not figure out which extension was which, so I just deleted all of them; downloaded 1.0.1 with IE and it ran perfectly.

Going back and reinstalling extensions some would not download due to incompatibility.   It’s nice that they keep them from being installed but there needs to be more flexibility once the extension is installed. We’re never going to get people to use Firefox and keep it updated if it ends up messing up the browser.