---
date: 2024-04-13T20:38:13.355Z
author: Stefan Hayden
title: Tidal track not available for streaming
layout: post
permalink: /blog/2024/04/13/Tidal-track-not-available-for-streaming/
categories:
  - web
---

I kept finding songs on Tidal I had added to my tracks list but were marked as "not available for streaming" but if you went to the artist page the song stil existsed. 

For some reason Tidal's backend seems to generate a lot of new track IDs when they update or need to make some change to a track. Really frusterating.

To fix this I wrote a script to find exact song title matches of songs from the same artist and swap them. Its been working really well for me and [you can find it here on github](https://github.com/stefanhayden/music).
