---
id: 42
title: My Adventures with hCal, iCal, webcal and their lack of support
date: 2005-08-08T00:28:49+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=42
permalink: /blog/2005/08/08/my-adventures-with-hcal-ical-webcal-and-their-lack-of-support/
categories:
  - web
---
Working on a project that involved events I wanted to add the ability to click a button and add that particular event to you <a href="http://en.wikipedia.org/wiki/ICalendar">iCal</a> enabled calendar. iCal does not work every where and right now it is limited to a select number of calender programs. In general this is a rather new idea and and is only implemented will in a couple of places (like <a href="http://www.upcoming.org">Upcoming.org</a>).

There are a couple of reasons that this feature has not proliferated more. One is that the programs that support iCal are not widely use and are not always associated with the iCal standard by the typical user.  Second is that iCal is not easy to write out. It's meant to be read by a computer, not a person and so most will shy away from manually typing the awkward formatting. Another reason is that the way to bridge this problem of human/machine readability was only created about a year ago. Called <a href="http://microformats.com/wiki/hcalendar">hCal</a> it stands as a XHTML solution to adding event information directly in a web page.

What does adding these XHTML tags to your page get you? Well that's the problem as of today there is not a large advantage to adding the tags. The tags are there to be read by some other online application that will see these tags and then do something with them. These exciting applications that interact with hCal tags are almost nonexistent at this point though. Currently the only Fancy widget I know of to work with the tags (beyond the occasional CMS plug-in to list the events) is <a href="http://suda.co.uk/projects/X2V/">XV2</a> which can actually take the XHTML tags and turn it in to an .ics iCal file that you can add to the iCal enabled calendar on your computer. But even this is listed as a beta and is only done on a small scale.

Another feature to bootstrap the iCal technology is a (new?) web protocol called <a href="http://www.mhsoftware.com/caldemo/manual/en/iCalExporter.htm">webcal</a>. With this you replace http:// with webcal:// and this gets your browser to launch your iCal enabled calendar to add the event. I don't know much about webcal since there is little written about the protocol. While Firefox recognises the protocol IE has no idea what it is and just refuses to do anything. It reminds me of another protocol where you replace http:// with <a href="http://www.brindys.com/winrss/feedformat.html">feed://</a> to denote a xml feed but even my up-to-date firefox doesn't know what to do with that and I don't know exactly what program does. Even Wikipedia doesn't seem to have anything to say about either feed:// or webcal://.

So if you see event information and are lucky enough for them to be formatted in the special hCal tags and there happens to be a link to add the event to your iCal enabled calendar and you happen to actually have an iCal enabled calendar AND your browser suports the webcal protocol you have a killer combination of technology. Until more applications can do things with hCal adding the tags don't really have much of an advantage. XV2 is letting me use my hCal tags to generate iCal files but if the load got to be to large it would not be fair to pass that onto XV2. Something needs to take a bigger role in hCal and iCal before it really gets a chance to take of. A while a go there was <a href="http://www.b2blog.com/2005/02/i-know-what-googles-going-to-do-next.htm">report that google might come out with some support for hCal</a>. I think <a href="http://technorati.com/">technorati</a> would be a good place to have some hCal support and with <a href="http://tantek.com/log">Tantek</a> kind of spear heading the microformats I would not be surprised if they were that far off from releasing something.

here are some iCal enabled calendars:
Linux: <a href="http://korganizer.kde.org/">KOrganizer</a>, <a href="http://www.horde.org/kronolith/">Kronolith</a>, <a href="http://www.mozilla.org/projects/calendar/">Mozilla Calendar</a>, <a href="http://www.novell.com/products/evolution/">Novell Evolution</a>, <a href="http://www.mozilla.org/projects/calendar/sunbird.html">Sunbird</a><br />
Macintosh: <a href="http://www.apple.com/ical/">iCal</a>, <a href="http://www.mozilla.org/projects/calendar/">Mozilla Calendar</a>, <a href="http://www.mozilla.org/projects/calendar/sunbird.html">Sunbird</a><br />
Windows: <a href="http://www.eventsherpa.com/">EventSherpa</a>, <a href="http://www.microsoft.com/products/works/default.mspx">Microsoft Works (Version 8 or higher)</a>, <a href="http://www.mozilla.org/projects/calendar/">Mozilla Calendar</a>, <a href="http://www.mozilla.org/projects/calendar/sunbird.html">Sunbird</a>, <a href="http://windates.com/windates.aspx">WinDates</a>

<tags>hcal, ical, webcal, upcoming, technorati, microformats</tags>