---
layout: post
title: "d3.js + Leaflet map"
description: ""
category: Tech
tags: [d3.js, leaflet]
---
{% include JB/setup %}

<iframe frameborder="0" height="600" marginheight="0" marginwidth="0" scrolling="no" src="http://bl.ocks.org/licaschiou/raw/5bcc3cad999584c71f81/" width="800"></iframe>

#### Motivation

One of the best way to visualize the data about a city is to render it on a map. This way allows viewers connecting their spatial experience with the data and creating stronger engagement.

#### Sample Code

The first step is to initialize a leaflet map object. This map object will provide a complete interactive map and some important functions that help us mapping data to the map. The setView function takes 2 arguments, the first is the postion(latitute, longitutde) and the second is zoom scale.

{% highlight html %}
<div id="map"></div>
{% endhighlight %}

{% highlight javascript %}
var map = L.map('map').setView([25.046374, 121.517896], 13); 
{% endhighlight %}

Then setup tileLayer for the map. Different tileLayers vary style and detail. [Here are different map providers and their demo.](http://leaflet-extras.github.io/leaflet-providers/preview/)

{% highlight javascript %}
L.tileLayer(
            'http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; ' + mapLink + ' Contributors',
            maxZoom: 18,
            }).addTo(map);
{% endhighlight %}

Create a svg layer on the map and assign it as svg. This way allows the appended svg elements moving with the map.

{% highlight javascript %}
map._initPathRoot();
var svg = d3.select("#map").select('svg');
{% endhighlight %}

Now we can load the data and start our regular d3 visualization processes. One key step is using the latitude and longitude of the data as coordinates for rendering elements on the screen. The function we used here is map.latLngToLayerPoint(LatLngObject). LatLngObject is create by L.LatLng(latitude value, longitude value). We can assign the return value of latLngToLayerPoint to transform or x, y position. And be sure to update d3 elements' position if map is dragged.

{% highlight javascript %}
projectPosition(); //initialize elements position
map.on("viewreset", projectPosition); //listening to map event 

function projectPosition() {
	mrtStations.attr("transform", 
	function(d) { 
		return "translate("+ 
			map.latLngToLayerPoint(d.LatLng).x +","+ 
			map.latLngToLayerPoint(d.LatLng).y +")";
		}
	)
}
{% endhighlight %}

#### Citation
The Taipei MRT data I used here is from [longitude and latitude of Taipei MRT stations.](http://michaelhsu.tw/2013/06/25/%E6%8D%B7%E9%81%8B%E7%AB%99%E7%B6%93%E7%B7%AF%E5%BA%A6%E5%9D%90%E6%A8%99-open-data/)

#### Source code
[Gist](https://gist.github.com/licaschiou/5bcc3cad999584c71f81)

