---
layout: post
title: "ng-model in ng-repeat"
description: ""
category: 
tags: [Angularjs]
---
{% include JB/setup %}

### Motivation   
To use ng-repeat to dynamically generate directives according to dataset. Each directive controls the assign dataset element.  

### Sample Code

The ng-repeat block :  

{% highlight html %}
<div ng-repeat="data in objectDataset">
	<slider-ctrl data="data"></slider-ctrl>
</div>  
{% endhighlight %}

The slider directive js:  

{% highlight javascript %}
app.directive('sliderCtrl', function(){  
	return {  
		link: link,  
		restrict : 'E',  
		scope: {  
			data: '='  
		},  
		templateUrl : 'src/directives/sliderCtrl.html'  
	};  
});  
{% endhighlight %}

The slider directive html: 

{% highlight html %}
<p>Current Value = {{data.value}}</p>    
<input type="range" ng-model="data.value">   
{% endhighlight %}

### Notes

* The wrong practice :

{% highlight html %}
<p>Current Value = {{data}}</p>    
<input type="range" ng-model="data">   
{% endhighlight %}

In this example, each iteration will create a childScope, and also assign the value to a new property data. When we change the value, ng-repeat will create new childScope for this new value, not overwriting the old one, and create performance issue.  

To correct this issue, we have to pass the **reference** of the value to ng-model. Remember, **_"if you are not seeing a  " . " in ng-model, you are doing something wrong."_**