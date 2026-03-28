---
date: 2026-03-28T13:14:28.263Z
author: Stefan Hayden
title: Liveblog - a new mastodon client to quickly post durring live events
layout: post
permalink: /blog/2026/03/28/Liveblog---a-new-mastodon-client-to-quickly-post-durring-live-events/
categories:
  - web
---

TLDR: [do your live blogging here.](https://liveblog.stefanhayden.com/)


### The Problem

I have had the the same problem since the dawn of micro blogging.
If I am watching a live event like an awards show, I often want to have a series of posts all properly tagged with the right hashtags.
I want to quickly see what other are saying and boost and interact with those people.
And I want all other posts not about the event to fade in to the background.

But normal UI for micro blogging makes you re-type hash tags on every post.
You can reconfigure some UIs to show a column of posts about a topic but you have to do the work to reconfigure the UI.

### The Solution

No more. [Liveblog is a tool 100% focused on quickly posting during live events](https://liveblog.stefanhayden.com/).
Hashtags persist for every post. Content Warnings persist for every post for perfect spoiler warning protection.
Optionally you can toggle thread mode and auto reply to your last post for perfect thread creation.
Below you can do a search to see what others are saying and it will auto refresh to always show fresh content to reply to, boost or favorite.

### Security

[Liveblog](https://liveblog.stefanhayden.com/) is deployed on vercel. It auths against your mastodon instance with minial permisions. All credidentials are stored in encrypted, httpOnly cookies. This means they are never stored on my servers. It also means if you login from different browsers or clear cookies it will register a new app on your account.

[![Liveblog screenshot](/wp-content/liveblog-screenshot.png)](https://liveblog.stefanhayden.com/)

