---
id: 19
title: 'FCKeditor &#8211; review and help'
date: 2005-04-11T04:13:19+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=19
permalink: /blog/2005/04/11/fckeditor-review-and-help/
categories:
  - design
  - web
---
I’ve wanted to clean up the <a href="http://www.tcnj.edu/~cub/index.php">College Union Board</a> website for a long time now and only now got around to it by making it apart of my senior portfolio. I not only gave it a redesign with a much stronger hierarchy but also added a lot of back end functionality that is needed to keep the site running with out any one overly knowledgeable about html.

After wrestling with <a href="http://www.fckeditor.net/">FCKeditor</a> between the hours of 12 and 5am I finally got it working. FCKeditor is a WYSIWYG editor that can be implemented in a number of ways. It comes in flavors such as javascript, asp, php, coldfusion, and perl. The documentation was a bit sparse and only included an install walk through for javascript. This was luckily what I needed as what I wanted to do was replace a TEXTAREA with a WYSIWYG editor and javascript seemed to be the only one that did this, though it was the only one documented.

Though it took me a long time to pin point the main problem I was having was with the path to the .js file that was supposed to be running the show. The linked javascript file ended up being src="FCKeditor/fckeditor.js" while the base path ended up being oFCKeditor.BasePath = './FCKeditor/';

I don’t know if this is a little quirky or the way it is supposed to act. The documentation was very short for JavaScript with no troubleshooting and the sourceforge forum had no problem that seemed similar to mine. 

Another issue I had was that the options that were listed were simply held in an array in the config file and if you did not what an option you had to delete it from the array instead of turning the option true or false which would be better for getting options back if you wanted.

Now that it’s all working I can’t be happier and I know how much easier it will make it for my wonderful event planning organization to update the website.