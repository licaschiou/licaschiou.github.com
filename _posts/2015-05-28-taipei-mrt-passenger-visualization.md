---
layout: post
title: "Taipei MRT passenger visualization"
description: ""
category: Tech
tags: [d3.js, leaflet]
---
{% include JB/setup %}


<iframe frameborder="0" height="600" marginheight="0" marginwidth="0" scrolling="no" src="http://licaschiou.github.io/TaipeiMrtPassengerCount/" width="100%"></iframe>

#### Motivation  

Explore the Taipei MRT passenger count dataset and look for any patterns or outliers.        

#### Load data

In this project, we are going to load three datasets and merge them together. To deal with the asynchronous loading, I create a custom loader. This loader accepts an array of urls and loads them one by one. When all files are loaded, the loader will fire a dataLoaded event. When we receive this event, we can start data processing.

{% highlight javascript %}
var csv = d3.dsv(",", "text/csv; charset=big5"); //Dataset contains chinese characters.
MultiDataLoader.prototype = Object.create(EventTarget.prototype, {
	startLoading : {
		value : function(){
			var dataurl = this.__url[this.__fileLoadedCount];
			csv(dataurl, function(d){
				loader.fileLoaded(d);
				return;
			});	
		},
		enumerable : true
	},
	fileLoaded : {
		value : function(d){
			rawData.push(d);
			this.__fileLoadedCount ++;			
			if(this.__fileLoadedCount === this.__fileCount){
				this.__fire(
					new DataLoadedEvent(d)
				);
			}else{
				this.startLoading();
			}
		},
		enumerable : true
	}
});
{% endhighlight %}

#### Data processing  

The main dataset is an array of objects which represent MRT stations.   
1. First, extract the list of stations and create station object for each item in the list.  
2. Then fill in the basic information such as line, id, etc, by matching the station name.  
3. The passenger count data will be an object like this. So we can use the date as the key to get the count.

{% highlight javascript %}
passengerCount = {
	2015-04-01:{in: 5000, out:5000},
	2015-04-02:{in: 4000, out:4000},
};
{% endhighlight %}

#### Visualization

1. Use two circles to reprecent passenger-in and passenger-out.   
2. On mouseover, display the count number and the average.   

[Check the result in full screen.](http://licaschiou.github.io/TaipeiMrtPassengerCount/){:target="_blank"}

#### Citation  

1. [Taipei MRT passenger count dataset.](http://data.taipei/opendata/datalist/datasetMeta?oid=1d71c478-205f-42c5-8386-35f86d74fdd1){:target="_blank"}  
2. [Taipei MRT information.](http://kuro.tw/posts/2015/05/20/join-the-d3-in-google-map-image){:target="_blank"}  

#### Source code  

[Github](https://github.com/licaschiou/TaipeiMrtPassengerCount/tree/gh-pages){:target="_blank"}