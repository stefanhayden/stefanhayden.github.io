---
id: 1567
title: Exclude svn files from grep
date: 2010-08-04T15:12:52+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=1567
permalink: /blog/2010/08/04/exclude-svn-files-from-grep/
categories:
  - Uncategorized
---
Grep is confusing enough and does not need to be even harder to use. SVN files are almost always not wanted in a search and just make finding what you want even harder. Luckily you can set a default option.

First jump in to the .bashrc file in your home directory.
<code>
nano ~/.bashrc
</code>

Then add the options for grep in that file:
<code>
GREP_OPTIONS="--exclude=*.svn-base"
export GREP_OPTIONS
</code>

Now save and exit the file. Before it will work you need to either restart the session or enter this in the console:
<code>
source ~/.bashrc
</code>

Wave goodbye to all those pesky svn file.