---
id: 992
title: Javascript Event onJSReady Fires When All JS Files Have Loaded
date: 2008-07-29T10:57:35+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=992
permalink: /2008/07/29/javascript-event-onjsready-fires-when-all-js-files-have-loaded/
openid_comments:
  - 'a:1:{i:0;s:5:"49396";}'
categories:
  - design
  - resources
  - web
---
<strong>Update:</strong> <a href="http://www.protolific.net/">jdalton</a> has what looks like a great improvement on my attempt below. Read below to learn about the problem but look at <strong><a href="http://pastie.org/244187">jdalton's script</a></strong> to see what is now the current best way to implement a solution.

<strong>Update (August 5th, 2008):</strong> There was an update to the JavaScript below to better handle IE firing off the ready state.

<strong style="font-size:150%; color:#FDCB26">Warning!:</strong> Due to a Prototype bug This code is not reliable in any version of IE. This bug is expected to be fixed in Prototype 1.6.0.3.

<hr />


So the <a href="http://yuiblog.com/blog/2008/07/22/non-blocking-scripts/">YUI blog had a great post on how javascript blocks downloads</a> and makes the page take longer to load. This is because any JS file can modify the DOM and so the DOM can't be ready until all JS files have loaded.

<a href="http://www.flugpo.com">Flugpo</a> uses Prototype and not YUI and so to get the speed benefits I needed to build my own Bells and whistles. The problem is that once you load the JS files asynchronously any onDOMReady function will fire before all the JS files download. This is a problem for any inline function calls that have dependencies on other JS files.

Using the Prototype based onDOMReady extension I have created an onJSReady function that checks that all JS files have been loaded. The function needs to know 2 things. How many JS files there are and how many have currently been loaded. When those two number match the even fires and runs any code that is waiting.

<pre style="overflow:scroll; width:460px; border:1px solid; margin-bottom:10px;"><code >
/**
 * A modified version of Stefan Hayden's onJSReady Prototype plugin. 
 * http://www.stefanhayden.com/blog/2008/07/29/javascript-event-onjsready-fires-when-all-js-files-have-loaded/
 *
 * @author John-David Dalton <john.david.dalton[at]gmail[dot]com>
 * @usage
 *   Prototype.include(['test1.js','test2.js','test3.js']); // array
 *   Prototype.include('test1.js', 'test2.js', 'test3.js'); // separate arguments OR
 *   Prototype.include('test1.js,test2.js,test3.js');       // comma separated string OR 
 *
 *   document.observe('scripts:loaded', function(){ dependent_on_external_js() });
 */
Prototype.include = Object.extend(
  function() {
    var callee = arguments.callee,
     head = document.getElementsByTagName('HEAD')[0],
     args = Array.prototype.slice.call(arguments, 0);

    args._each(function(files) {
      if (Object.isString(files))
        files = files.split(',');
      
      callee.total += files.length;
      files._each(function(file) {
        head.appendChild(
          new Element('script', { type: 'text/javascript', src: file.strip() })
        )
        .observe('readystatechange', function () {
          if (!this.loaded && /^(loaded|complete)$/.test(this.readyState)) {
            this.loaded = true;
            callee.downloaded++;
          }
        })
        .observe('load', function () {
          if (this.loaded) return;
          this.loaded = true;
          callee.downloaded++;
        }); // end observers
      }); // end files _each 
    }); // end args _each
  }, 
  {
    total: 0,
    downloaded: 0
  }
);

(function() {
  var timer;
  function ready() {
    if (arguments.callee.done) return;
    clearInterval(timer);
    arguments.callee.done = true;
    document.fire('scripts:loaded');
  }
  
  timer = setInterval(function() {
    var i = Prototype.include;
    if (i.total && i.downloaded === i.total) ready();
  }, 10);
})();

</code></pre>

<pre style="overflow:scroll; width:460px; height:100px; border:1px solid; margin-bottom:10px;"><code >
This is old... ignore this.
<del datetime="2008-07-30T21:44:42+00:00">window.Total_JS_Files;
window.Downloaded_JS_Files = 0;

function include_js(files) {
	var js=new Array();
	window.Total_JS_Files = files.length;
	
	for(var i=0; i < files.length; i++) { 
		
	    var html_doc = document.getElementsByTagName('head')[0];
	    js[i] = document.createElement('script');
	    js[i].setAttribute('type', 'text/javascript');
	    js[i].setAttribute('src', files[i]);
	    html_doc.appendChild(js[i]);
	
	    js[i].onreadystatechange = function () {
	        if (js[i].readyState == 'complete') {
	            //alert('JS onreadystate fired ');
	            window.Downloaded_JS_Files += 1;
	        }
	    }
	
	    js[i].onload = function () {
	        //alert('JS onload fired ');
	            window.Downloaded_JS_Files += 1;
	    }
    }
    return false;
}//include_js


Object.extend(Event, {
  timeout : function() {
	alert('asd');
  },
  jsReady : function() {
  
    if (arguments.callee.done) {return;}
    arguments.callee.done = true;
		
	Event._NreadyCallbacks.each(function(f) { f(); });
	Event._NreadyCallbacks = null;
		
  },
  onJSReady : function(f) {
    if (!this._NreadyCallbacks) {
      var jsReady = this.jsReady;
      
      if (jsReady.done) {return f();} 
        
		function jsTest() {
			if(window.Downloaded_JS_Files == window.Total_JS_Files) { 
				//setTimeout(jsReady,1);
				jsReady();
			}
			Event._Ntimer = setTimeout(jsTest,1); 
		}
		Event._Ntimer = setTimeout(jsTest,10); 
        
        //Event.observe(window, 'load', jsReady);
        Event._NreadyCallbacks =  [];
    }
    Event._NreadyCallbacks.push(f);
  }
});
  </del>
</code></pre>

To implement this the only JS that needs to load is prototype and these two functions above. Then you just need to load the URLs for the JS files and fire off the include_js function.

<pre style="overflow:scroll; width:460px; border:1px solid; margin-bottom:10px;"><code >
var js_paths = new Array;
js_paths[js_paths.length] = '/path/to/js/one.js';
js_paths[js_paths.length] = '/path/to/js/two.js';
js_paths[js_paths.length] = '/path/to/js/three.js';

<del datetime="2008-07-30T21:45:28+00:00">include_js(js_paths);</del>
Prototype.include(js_paths);
</code></pre>

Once all of the JS files have loaded then just like onDOMReady the onJSReady code will fire.

<pre style="overflow:scroll; width:460px; border:1px solid; padding-top:10px; margin-bottom:10px;"><code >
<del datetime="2008-07-30T21:45:28+00:00">Event.onJSReady(function () { dependent_on_external_js(); });</del>
 document.observe('scripts:loaded', function(){ dependent_on_external_js() });
 
</code></pre>