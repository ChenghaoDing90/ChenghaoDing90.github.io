---
title: COVID-19 County Level Data Analysis
author: Chenghao Ding
layout: post
comments: true
---

# COVID-19 County Level Data Analysis
This project uses county level data about demographics and health-related information to predict one week deaths from April 23rd to April 30th. We consider some predictor variables, such as the polulation, agedistribution, gender distribution, per capita share of medical resources and health conditions. 
At first, to give a simple understanding, we perform the covid-19 growing pattern clustering by k-means method, demographics clustering by spectral method and health-related information clustering by agglomerative hierarchical clustering method. We use logistic regression and suport vector machine to predict whether death per 100,000 population in the county is larger than 1. Then, four regression methods, elastic penalized regression, random forest regression, GAM regression and XGboost method, are used to to predict one week deaths, based on the previous days’ amount of deaths, the cases a week ago and the characteristics of demogrphics and health-related information.
According to the clusters, we find cases and health resource are highly affected by the economic situation of a county. Comparing to them, deaths and demographics do not show any obvious regional characteristics and scatter throughout the country. The classification performs well and can give identify most counties with
high death rate.
According to the coefficients of the regression model, we conclude that the the population and population density makes their death toll rise even faster in the county. People over 85 with heart disease are more vulnerable to this virus. Comparing to male, female are more vulnerable. It is helpful for reducing the deaths to provide adequate medical resource, such as a hospital. However, because of the population base, age density and gender density are related to social situation in this area, we think the analysis of vulnerable poeple are affected.

<div class="fig figcenter fighighlight">
  <img src="/assets/images/cluster.png" width="800" height="800">
  <div class="figcaption"><br> cluster.<br>
  </div>
</div>

<div class="fig figcenter fighighlight">
  <img src="/assets/images/cluster2.png" width="800" height="800">
  <div class="figcaption"><br> clus.<br>
  </div>
</div>

<div class="fig figcenter fighighlight">
  <img src="/assets/images/cluster3.png" width="800" height="800">
  <div class="figcaption"><br> The sample images.<br>
  </div>
</div>

<div class="fig figcenter fighighlight">
  <img src="/assets/images/feature_importance.png" width="800" height="800">
  <div class="figcaption"><br> The sample images.<br>
  </div>
</div>

<div class="fig figcenter fighighlight">
  <img src="/assets/images/stepwise.png" width="800" height="800">
  <div class="figcaption"><br> Stepwise model.<br>
  </div>
</div>

<div class="fig figcenter fighighlight">
  <img src="/assets/images/GAM.png" width="800" height="800">
  <div class="figcaption"><br> The sample images.<br>
  </div>
</div>

<div class="fig figcenter fighighlight">
  <img src="/assets/images/random_forest.png" width="800" height="800">
  <div class="figcaption"><br> The sample images.<br>
  </div>
</div>

<div class="fig figcenter fighighlight">
  <img src="/assets/images/gradient_boosting.png" width="800" height="800">
  <div class="figcaption"><br> The sample images.<br>
  </div>
</div>
