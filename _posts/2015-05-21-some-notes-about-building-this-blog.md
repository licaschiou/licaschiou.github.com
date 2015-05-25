---
layout: post
title: "Some Notes about building this blog."
description: ""
category: Tech
tags: [Jekyll, github]
---
{% include JB/setup %}

* Code hightlight syntax issue: 
	I tried to use the familiar triple ` syntax, but Jekyll keeps generating funky results. I have to switch to 
	{% raw %}
	{% highlight javascript %}  
	someCode();  
	moreCode();  
	{% endhighlight %}  
	{% endraw %}
	to get the right result. Note that the double quotes in the syntax were put to prevent the text been converted.
* Having pages build failure issuse:
	When I first encountered the code highlighting issue, I tried rouge highlighter and it worked under localhost. But when I pushed the repository to Github, pages build failures happened. After some digging, I found [the follow document](https://help.github.com/articles/page-build-failed-config-file-error/).
	Quote: 
	" Although Jekyll lets you define your own highlighter, at this time GitHub Pages only supports pygments. ... Using rouge or any other highlighter results in a build error.  
* The highlighter issue hasn't been fixed yet. I have to use rouge for local host and change to pygments for pushing.  
* The Markdown syntax in Jekyll is somehow weird. For example, it takes two tabs to create sub-list under a list.  
* ToDoList  
 		1. Embed d3.js in post.