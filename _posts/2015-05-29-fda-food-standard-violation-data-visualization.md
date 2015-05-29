---
layout: post
title: "FDA Food Standard Violation Data Visualization"
description: ""
category: Tech
tags: [d3.js]
---
{% include JB/setup %}

[The interactive charts.](http://licaschiou.github.io/FDA_Food_Standards_Violation/){:target="_blank"}

#### Motivation  

Explore the food safety violation dataset from Taiwan FDA and compare this dataset with recent food scanfals.

#### Study Type  

This is a simple exploratory analysis , no association or causality implied.

#### The Data  

1. [FDA food safety violation dataset.](http://data.fda.gov.tw/frontsite/data/DataAction.do?method=doDetail&infoId=52){:target="_blank"} This dataset contains the imported food in which FDA finds safety violation.
2. [Taiwan food scandal list.](http://zh.wikipedia.org/wiki/%E5%8F%B0%E7%81%A3%E9%A3%9F%E5%93%81%E5%AE%89%E5%85%A8%E4%BA%8B%E4%BB%B6%E5%88%97%E8%A1%A8){:target="_blank"}

#### Data Processing  

1. Load FDA food safety violation dataset.  
2. Transform it to the structure which d3.js could use. There is no modification on data value.  
3. For wikipedia source, I copy the table, paste it on google sheet, and then export it as csv. If there are more than one entries in a row, then seperate them by date.  

#### Visualization  

![graph 1](/assets/img/2015-05-29-1.png)


1. The first graph shows the relation between where the food comes from and the reason by which FDA consider it as violation.  

![graph 2](/assets/img/2015-05-29-2.png)

2. The second graph put the total food safety violation cases of a year and all the major food scanfals together. This graphc allows us compare their trends but doesn't imply they have any association.  

#### Result

1. Most cases are from Japan(532), America(366) and China(276). 
2. Most cases violate pesticide(1384), preservative(286) and veterinary drug(198) residue standard.  
3. Most food scandals are local cases.  

Without detail information for us to calculate the proportion of cases from each country, the case number doesn't mean much. For example, the reason why there are many cases from Japan could be that we just love Japanese food and import much more from Japan than from other countries. 

However, the food scandals do make us worry. Even though FDA tried to prevent bad food from importing into Taiwan. They seemed to fail to regulate local food companies.  