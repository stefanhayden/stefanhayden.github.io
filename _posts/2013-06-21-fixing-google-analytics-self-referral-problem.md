---
id: 1672
title: Fixing Google Analytics self referral problem
date: 2013-06-21T21:21:37+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=1672
permalink: /2013/06/21/fixing-google-analytics-self-referral-problem/
categories:
  - development
---
If you are using Google Analytics you might see your own site listed as a referrer. Most commonly this is the case of having the same tracking code across multiple domains.

In the past this problem was mind numbing difficult to solve. Luckily Google has made this dead easy to fix with it's new Universal Analytics. Sadly if you have an old Analytics account you can not convert it, but do not worry you can still keep that old tracking code on your site and track to both places.

Once you have set up your new Universal Analytics account you can follow the <a href="https://developers.google.com/analytics/devguides/collection/analyticsjs/">development guide to get it integrated</a> on your site. Universal Analytics has a ton of new features and is well worth the time to set up.

<strong>The Fix:</strong>

In your universal Account go to the admin section. Find the "Tracking info" section. In that section there should be a option called "Referral Exclusion List". Here you may list ANY url that you do not wanted to be listed as a referrer. And that is all it takes.

This does not fix old data and will simply stop this problem from happening in the future. Also the fix is not instantaneous. Each day the number of referals from the url you just added to the "Referral Exclusion List" will show fewer and fewer visits. In my experience it could take one or two weeks for the problem to be totally fixed.