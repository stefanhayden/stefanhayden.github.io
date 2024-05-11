---
date: 2024-05-10T23:53:05.690Z
author: Stefan Hayden
title: How long does a Mastodon post take to federate between servers?
layout: post
permalink: /blog/2024/05/10/mastodon-federation-speed-test/
categories:
  - web
  - mastodon
  - federation
  - development
---

[Recently Stefan Bohacek ran a poll to find out how long a post takes to appear to his followers.](https://stefanbohacek.com/blog/data-on-sending-a-post-into-the-fediverse/) A great question!

There is no one speed a post is circulated. When a post is made it enters a queue on sidekiq (below) to be sent out to other servers. Those servers receive that message and it goes in a queue to be processed. At peak times these queues can grow thousands of entries depending on how it is provisioned.

My server, [GardenState.social](https://gardenstate.social), is hosted on [cloudplane at the medium level](https://cloudplane.org/docs/applications/mastodon). It has 2 cpus and 8 sidekiq queues.

![image](https://github.com/stefanhayden/stefanhayden.github.io/assets/87616/44f5518a-38a8-47a2-a0ee-724a78818bd9)

## The Speed Test

To do my own test I wrote a script ([code on github](https://github.com/stefanhayden/mastodon-federation-speed-test)) to get all my followers, get all their servers, make a post and then check each server until that post appears. Because mastodon redirects you back to your server when viewing your own profile I instead generated a unique hashtag and then check to see if the page for that hashtag 404s or 200s.

I ran this code at 7:30 on May 10th. There is no way to know the queue status of other servers but my own servers had empty queues.

## Results

My post made it to 251 servers over 240 seconds (4 minutes). The average time for my post to appear on another server was 8.6 seconds.

The top 5 fastest servers (in seconds):
- 0.959 - lostcreek.social
- 0.985 - social.giurdanella.it
- 1.045 - happyfedi.better-than.tv
- 1.068 - social.lugal.io
- 1.069 - blahaj.zone

The top 5 slowest servers (in seconds):
- 240.34 - climatejustice.rocks
- 54.134 - postchat.io
- 51.491 - mastodon.africa
- 18.53 - mastodon.acc.sunet.se
- 17.733 - mstdn.party

Notible servers (in seconds):
- 3.308 - beige.party
- 6.394 - mastodon.social
- 5.535 - mas.to
- 11.662 - universeodon.com
- 4.716 - fosstodon.org

[see the full results dataset here!](https://github.com/stefanhayden/mastodon-federation-speed-test/blob/main/results.txt)

I could imagine this being turned into a bot and report some kind of federation health check. Though this does spam the servers with web requests a bit so it seems like something we can just run occasionally to get a feel for the state of the fediverse.

Overall, federation seems to be pretty speedy!

