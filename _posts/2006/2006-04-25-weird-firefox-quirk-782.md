---
id: 157
title: 'Weird Firefox Quirk #782'
date: 2006-04-25T21:50:15+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/2006/04/25/weird-firefox-quirk-782/
permalink: /blog/2006/04/25/weird-firefox-quirk-782/
categories:
  - design
  - web
---
I noticed an interesting quirk of Firefox today. It happens when you are on a page that requires a login to view.

If you wait for your login to expire and then view source you don't get the source of the page you are looking at. Instead you get the html of what ever page you get kicked to when your login expires.

When you view source in Firefox it seems to go back to the server and re-download the page source. The Server see that you are not logged in and serves you the login expired page. So the HTML it shows you is different from the page you are looking at.

This seems like a really weird quirk. I have no idea why it can't just use the local copy it clearly has already downloaded. I suppose it would not be an issue in most situations. Though it can be confusing when you are trying to figure out what in the world is going on.

<tags>firefox, quirk, viewsource</tags>