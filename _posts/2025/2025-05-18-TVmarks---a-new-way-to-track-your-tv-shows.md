---
date: 2025-05-25T22:00:00.383Z
author: Stefan Hayden
title: TVmarks - a new way to track your tv shows
layout: post
permalink: /blog/2025/05/18/TVmarks---a-new-way-to-track-your-tv-shows/
categories:
  - web
---

<img src="/img/tvmarks-screenshot.jpg" alt="Picture of Tvtime with lots of tv to watch" />

I am excited to annouce a new project, [Tvmarks](https://github.com/stefanhayden/tvmarks), a personal website to track your tv shows. It is inspired by and shares much of the same code as [Postmarks](https://github.com/ckolderup/postmarks).
Through the power of the [tvmaze](https://www.tvmaze.com/) database Tvmarks lets you a build a selfhosted version of what you are watching, what you have watched, and what you plan to watch.
Tvmarks is also fediverse enabled with shows added and episodes watched shared with your comments to activitypub.

### How I Got Here

Postmarks launched in 2023 but I didn't discover it till 2025. That still seems wild to think about since I am, or try to be, very pluged in to the fediverse.
But one thing it taught me that I never really thought of is how an sqlite can juist be a file that node can access.
I love web aplications but have never loved needing to care about servers and databses.
Glicth with sqlite really solves so many problems that are needed but I rather not care about.
With those obticals trivialized I was excited with the idea of owning my tv watching data.

### A cousin of Postmarks

Is it clear I love Postmarks?! I forked it in Febuary and got to work. Most changes were pretty strightforward to support shows and episodes in the database.
Tvmaze has great apis to source data from to host in your own database so you are never dependant of another website to host your data.

### RIP Glicth

Though Tvmarks was built to run on glitch.com I have also been able to run it on a VPS and on Render.com.

### Install it and let me know

If you try it link me to your instance -> [@stefan@gardenstate.social](https://gardenstate.social/@stefan)
