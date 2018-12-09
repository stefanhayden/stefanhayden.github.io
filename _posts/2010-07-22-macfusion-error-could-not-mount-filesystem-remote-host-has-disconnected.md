---
id: 1555
title: 'MacFusion Error: Could not mount filesystem: Remote host has disconnected.'
date: 2010-07-22T08:26:26+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=1555
permalink: /2010/07/22/macfusion-error-could-not-mount-filesystem-remote-host-has-disconnected/
categories:
  - Uncategorized
---
If you're getting the above error immediately after clicking mount it seems to be because you are using OSX 10.6. There's not a ton of good documentation but this is what seems to work.

Right click on the app and select "Show package contents". Navigate to <strong>Contents/PlugIns/sshfs.mfplugin/Contents/Resources/sshnodelay.so</strong> and delete or rename the file.

It should now magically work.