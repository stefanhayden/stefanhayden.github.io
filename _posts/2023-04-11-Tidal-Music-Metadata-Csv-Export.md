---
date: 2023-04-11T01:34:10.962Z
author: Stefan Hayden
title: Tidal Music Metadata Csv Export
layout: post
permalink: /blog/2023/04/11/Tidal-Music-Metadata-Csv-Export/
categories:
  - web
---

I never trust these music services to remember what music I love. Tidal doesn't have an easy way to export this. I just want a CSV file to keep so Tidal doesn't own the music I have found.

[So here is a small repo you can clone to run against your Tidal and pull your favorites out.](https://github.com/stefanhayden/music)

```javascript
# You need to install tidalapi using pip install tidalapi (more can be found here https://github.com/tamland/python-tidal)
# had to be fixed with https://github.com/tamland/python-tidal/pull/130

import csv
import sys
import pprint

import tidalapi

session = tidalapi.Session()
session.login_oauth_simple()
favorites = tidalapi.Favorites(session, session.user.id)

#
# Get Tracks
#
open('../tracks.csv', 'w').close()
f = open("../tracks.csv", "a")

f.write('track,album,artist\n')

getMore = True
limit = 1000
offset = 0

while getMore == True:

    tracks = favorites.tracks(limit, offset);
    offset += limit;
    if len(tracks) == 0:
        getMore = False

    for track in tracks:
        f.write(','.join([track.name, track.album.name, track.artist.name]) + '\n')


#
# Get Artists
#
open('../artists.csv', 'w').close()
f = open("../artists.csv", "a")

f.write('artist\n')

getMore = True
limit = 1000
offset = 0

while getMore == True:

    artists = favorites.artists(limit, offset);
    offset += limit;
    if len(artists) == 0:
        getMore = False

    for artist in artists:
        f.write(artist.name + '\n')


#
# Get Album
#
open('../albums.csv', 'w').close()
f = open("../albums.csv", "a")

f.write('album,artist\n')

getMore = True
limit = 1000
offset = 0

while getMore == True:

    albums = favorites.albums(limit, offset);
    offset += limit;
    if len(albums) == 0:
        getMore = False

    for album in albums:
        f.write(','.join([album.name, album.artist.name]) + '\n')

```
