---
id: 1745
title: How to use Gem CLI commands in Supervisor on Ubuntu
date: 2015-05-14T22:32:11+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=1745
permalink: /blog/2015/05/14/how-to-use-gem-cli-commands-in-supervisor-on-ubuntu/
categories:
  - development
---
<a href="http://supervisord.org/">Supervisor</a> is a great unix program that lets you run persistant long-running programs. In general it's easy to use and <a href="https://www.digitalocean.com/?refcode=21f84017dd35">DigitalOcean ($5 a month hosting)</a> has a great <a href="https://www.digitalocean.com/community/tutorials/how-to-install-and-manage-supervisor-on-ubuntu-and-debian-vps?refcode=21f84017dd35">tutorial on how to set it up here</a>.

I was interested in Supervisor because I wanted to run the <a href="https://github.com/mispy/twitter_ebooks">mispy/twitter_ebooks</a> repo for building some twitter bots. It gives you a great command line interface for both creating new bots (<code>ebooks new &lt;reponame&gt;</code>) and starting the bots (<code>ebooks start</code>).

For whatever reason you can't just point Supervisor at a directory and call that command. You'll need to find where the gem wrapper is located and run the command from there.

First find the path of the executable gem:

<code><a href="http://en.wikipedia.org/wiki/Which_%28Unix%29">which</a> ebooks</code>

For me it was located here:
<code>/home/shayden/.rvm/gems/ruby-2.2.2/bin/ebooks</code>

Then we can switch the <code>/bin/</code> dir to the <code>/wrappers/</code> dir which is the packaged file you will tell Supervisor to run.

<code>/home/shayden/.rvm/gems/ruby-2.2.2/wrappers/ebooks</code>

In Supervisor the .conf file should now look like this:

<code>[program:ebooks]
command=/home/shayden/.rvm/gems/ruby-2.2.2/wrappers/ebooks start
directory=/home/shayden/ebooks_bot/
autostart=true
autorestart=true
stderr_logfile=/var/log/ebooks.err.log
stdout_logfile=/var/log/ebooks.out.log</code>

Now Supervisor should have no problems keeping your twitter bots alive and tweeting.