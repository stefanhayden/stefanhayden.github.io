---
id: 1542
title: Set Windows 7 Default Email program to Gmail (using Chrome)
date: 2010-06-23T23:02:41+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=1542
permalink: /2010/06/23/set-windows-7-default-email-program-to-gmail-using-chrome/
categories:
  - resources
---
yarg. why is this so hard?
<ol>
	<li><strong>Start</strong> > type "<strong>regedit</strong>" > hit enter</li>
	<li>go to HKEY_LOCAL_MACHINE\SOFTWARE\Classes\mailto\shell\open\command\</li>
	<li>Edit (default) to <strong>"C:\Users\*username*\AppData\Local\Google\Chrome\Application\chrome.exe" https://mail.google.com/mail?extsrc=mailto&url=%1</strong></li>
	<li>make sure to replace *username* with your username</li>
</ol>

