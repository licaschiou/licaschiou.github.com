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

To explore the food safety violation dataset and compare it to recent food scandals.

#### Study Type  

This is a simple exploratory analysis, no association or causality implied.

#### The Data  

1. [FDA food safety violation dataset.](http://data.fda.gov.tw/frontsite/data/DataAction.do?method=doDetail&infoId=52){:target="_blank"}.
2. [Taiwan food scandals.](http://zh.wikipedia.org/wiki/%E5%8F%B0%E7%81%A3%E9%A3%9F%E5%93%81%E5%AE%89%E5%85%A8%E4%BA%8B%E4%BB%B6%E5%88%97%E8%A1%A8){:target="_blank"}

#### Data Processing  

1. Load FDA food safety violation dataset.  
2. Transform it to the structure which d3.js could use. The data values aren't changed.
3. For wikipedia source, copy the table, paste it on google sheet, and then export it as csv. If there are more than one entry in a row, then seperate them by date.  

#### Visualization  

![graph 1](/assets/img/2015-05-29-1.png)

1. This graph display the cases by countries of origin and the violated regulation.  

![graph 2](/assets/img/2015-05-29-2.png)

2. The second graph put the cases and the food scanfals of the same year together. This graphc allows us compare their trends but doesn't imply they have any association.  

#### Result

1. Most cases are from Japan(532), America(366) and China(276). 
2. Most cases violate pesticide(1384), preservative(286) and veterinary drug(198) residue standard.  
3. Most food scandals are local cases.  

Without detail information the case number doesn't tell us much. For example, the reason why there are more cases from Japan could be that we love Japanese food and import much more from Japan than from other countries. 

However, the food scandals are serious problems. Even though FDA tried to prevent bad food from importing into Taiwan. They failed to regulate local food companies and the situation is getting worse.  

#### Source code  

[Github](http://github.com/licaschiou/FDA_Food_Standards_Violation){:target="_blank"}