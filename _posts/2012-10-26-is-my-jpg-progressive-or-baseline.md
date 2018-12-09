---
id: 1651
title: Is my JPG progressive or baseline?
date: 2012-10-26T13:11:15+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=1651
permalink: /2012/10/26/is-my-jpg-progressive-or-baseline/
categories:
  - web
tags:
  - baseline
  - image
  - jpeg
  - jpg
  - loading
  - progressive
---
Ever wonder what format your JPG was saved in? Well wonder no more. Just open the JPG up in any text editor and do a search for the hex code ffda.
<ol>
	<li>0 results: this image will load all at once when it is done loading</li>
	<li>1 result: this image will slowly load from top to bottom in full resolution. this is called baseline.</li>
	<li>2 or more results: this image will draw multiple passes of the image in better and better resolution. this is called progressive.</li>

</ol>

