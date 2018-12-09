---
id: 27
title: 'Screen Scrape an RSS feed with PHP: A Guide'
date: 2005-05-31T14:46:43+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=27
permalink: /2005/05/31/screen-scrape-an-rss-feed-with-php/
categories:
  - resources
  - web
---
I was looking for a guide to making an RSS feed for a site that didn't have one* and found the internet very much lacking in what it provided. It turns out that there is not as much to choose from as a <a href="http://www.google.com/search?q=screen+scrape+rss">Google search</a> would lead you to believe. <a href="http://www.nocertainty.com/2004/08/19/rss-and-screen-scraping/">Dennis Pallett</a> seems to be one of the only people to have written a review and it is featured on many, many different sites. While it was very helpful I still thought it was lacking in its explanation. 

So I’m going to use Dennis’ code along with how I altered it and go over what I did and what things mean and hopefully paint a clearer picture of how to turn the world in to an RSS feed.

Screen scrapping an RSS feed is based on some simple concepts. Grab each individual post in an array and then grab the title, permalink, and full text out and throw them in their respective RSS tags.

<div class="code">
	<p>< ?php</p>

	</p><p>$url = &#8220;http://www.gailgauthier.com/blogger.html&#8221;;</p>

	<p>$data = getUrlTEXT($url);</p>

	<p>// Get content items<br />
preg_match_all ("/&lt;div class=\"posts\">([^`]*?)< \/div>/", $data, $matches);</p>
</div>

GetUrlTEXT is a quick function defined at the bottom of the script that uses cURL to get the full text of any url.

<a href="http://us3.php.net/preg_match_all">preg_match_all</a> and <a href="http://us3.php.net/preg_match">preg_match</a> are both functions that I don’t fully understand but they uses strings of characters called ‘regular expressions’ that tell PHP what text to include and not include (<a href="http://weblogtoolscollection.com/regex/regex.php">regular expressions guide here</a>). 

While I don’t completely understand it I can point some things out. preg_match takes 3 arguments. The first is the string you are looking for, the second is the full text you are searching, and the third is an array that all the found strings are put in. 

The first argument are in double quotes as well as forward and back slashes (ex. “/REGULAR EXPRESIONS HERE/”). You also see the start and end of a div as part of the expression. This tells preg_match what to look in between to find the text you are looking for. The regular expressions between the div tags, ([^`]*?), definitely have a meaning but you’ll have to read up to figure it out. Needless to say it works in finding whatever is in between whatever you put on either side of the regular expressions. 

Next you can just set up the RSS header information.

<div class="code">
	<p>// Begin feed<br />
header (&#8220;Content-Type: text/xml; charset=ISO-8859-1&#8221;);<br />
echo &#8220;< ?xml version="1.0" encoding="ISO-8859-1" ?>\n&#8221;;<br />
?></p>

	<p>&lt;rss version=&#8221;2.0&#8221;<br />
xmlns:dc=&#8221;http://purl.org/dc/elements/1.1/&#8221;<br />
xmlns:content=&#8221;http://purl.org/rss/1.0/modules/content/&#8221;<br />
xmlns:admin=&#8221;http://webns.net/mvcb/&#8221;<br />
xmlns:rdf=&#8221;http://www.w3.org/1999/02/22-rdf-syntax-ns#&#8221;><br />
&lt;channel><br />
&lt;title>Original Content&#8212;A Gail Gauthier Blog&#8212;Latest Content&lt;/title><br />
&lt;description>The latest content from Gail Gauthier (http://www.gailgauthier.com/blogger.html), screen scraped! &lt;/description><br />
&lt;link>http://www.gailgauthier.com/blogger.html&lt;/link><br />
&lt;language>en-us&lt;/language></p>

</div>

Nothing hard here, just change the title, description and link. The rest of the information is standard for the RSS file.

Next we loop through the ‘matches’ array we made to extract the title, permalink, full text and author name.

<div class="code">
	<p>&lt;?</p>

	<p>// Loop through each content item<br />
foreach ($matches[0] as $match) {</p>

	<p>// First, get title<br />
preg_match (&#8221;/&lt;h3>([^`]*?)&lt;/h3>/&#8221;, $match, $temp);<br />
$title = $temp[&#8216;1&#8217;];<br />
$title = strip_tags($title);<br />
$title = trim($title);</p>

	<p>// Second, get url<br />
preg_match (&#8221;/&lt;span class="byline">posted by gail at &lt;a href="([^`]*?)">/&#8221;, $match, $temp);<br />
$url = $temp[&#8216;1&#8217;];<br />
$url = trim($url);</p>

	<p>// Third, get text<br />
preg_match (&#8221;/< /h3>([^`]*?)&lt;span class="byline">/&#8221;, $match, $temp);<br />
$text = $temp['1'];
$text = trim($text);
$text = str_replace('&lt;br />', '&lt;br />', $text);

	</p><p>// Fourth, and finally, get author<br />
preg_match (&#8221;/&lt;span class="byline">By ([^`]*?)&lt;/span>/&#8221;, $match, $temp);<br />
$author = $temp[&#8216;1&#8217;];<br />
$author = trim($author);</p>
</div>

As you can see getting the title is simple enough, it’s the only thing inside of &lt;h3&gt; tags. The permalink was much harder though since it was not between any specific tags. Instead I used the string ‘&lt;span class=\"byline\">posted by gail at &lt;a href=\"’ this is obviously a very bad hack to get what you want but not all site will be nicely set up for you to make it in to an RSS feed.

<div class="code">
	<p>if (!($title  '') &#38;&#38; !($text  &#8216;&#8217;))<br />
{<br />
// Echo RSS XML<br />
echo &#8220;&lt;item>\n&#8221;;<br />
echo &#8220;\t\t\t&lt;title>&#8221; . strip_tags($title) . &#8220;&lt;/title>\n&#8221;;<br />
echo &#8220;\t\t\t&lt;link>&#8221; . strip_tags($url) . &#8220;&lt;/link>\n&#8221;;<br />
echo &#8220;\t\t\t&lt;description>&#8221; . strip_tags($text) . &#8220;&lt;/description>\n&#8221;;<br />
echo &#8220;\t\t\t&lt;content :encoded>< ![CDATA[ n&#8221;; <br />
echo $text . &#8220;\n&#8221;; <br />
echo &#8221; ]]>&lt;/content>\n&#8221;;<br />
echo &#8220;\t\t\t&lt;dc :creator>&#8221; . &#8220;Gail Gauthier&#8221; . &#8220;&lt;/dc>\n&#8221;;<br />
echo &#8220;\t\t&lt;/item>\n&#8221;;<br />
}//end if<br />
}//end foreach</p>

	<p>?&gt;</p>
</div>


After we find all our information we just need to print it out in RSS format. First I do a quick check that the post has actual information in it and then it is just outputted in to the tags. 

That about it for this method of screen scrapping an RSS feed. I’ve heard <a href="http://www.kottke.org/05/04/mcsweeneys-lists-rss">Kottke</a> mention ways of using the DOM from PHP5 but I am still working on learning DOM in general. <a href="http://www.stefanhayden.com/blog/wp-content/gailgauthier-rss.txt">You can download this full PHP script here</a>.

* It turns out what Blogger was FTPing to <a href="http://www.gailgauthier.com/blogger.html">Gail Gauthier’s site</a> was just not listing the ATOM feed in the html. I later found the feed and had to just be happy that I learned something.
