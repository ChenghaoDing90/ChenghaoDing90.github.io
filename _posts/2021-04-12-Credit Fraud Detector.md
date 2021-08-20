---
title: Credit Card Fraud Detection
author: Chenghao Ding
layout: post
comments: true
---

# Credit Card Fraud Detection

* Question: Identify the fraudulent credit card transactions from a huge imbalanced data?

It is important that credit card companies are able to recognize fraudulent credit card transactions so that customers are not charged for items that they did not purchase. Online shopping is on the rise as more of us stay at home and let our credit cards do the walking. Keeping pace with that trend is an unfortunate increase in credit card fraud. It’s no surprise that online fraud has been a growing problem for the past few years. And now, as consumers and businesses adapt to the worldwide pandemic and make more credit card transactions in the card-not-present (CNP) space, the resulting uptick in online shopping and ecommerce has opened up an even bigger playground for fraudsters to try out new tricks. 

## Data Description
The dataset contains transactions made by credit cards in September 2013 by European cardholders. This dataset presents transactions that occurred in two days, where we have 492 frauds out of 284,807 transactions. The dataset is highly unbalanced, the positive class (frauds) account for 0.172% of all transactions.<br />
There are in total 28 features are found after using PCA transformation, however, due to privacy issues, the real backgroud information is hided.<br />
Among those 28 features, 'time' and 'Amount' are the most significant two. Feature 'Time' contains the seconds elapsed between each transaction and the first transaction in the dataset. The feature 'Amount' is the transaction Amount, this feature can be used for example-dependant cost-sensitive learning. Feature 'Class' is the response variable and it takes value 1 in case of fraud and 0 otherwise.<br />
The whole project can be found in my GitHub: <a href="https://github.com/ChenghaoDing90/CreditCardFraudDetection">(CreditCardFraudDetection)</a>.

## Objective
<ul>
      <li>Find the how is the imbalanced data skewed and how to make them 'balanced' in terms of having a similar amount of "Fraud" and "Non-Fraud" transactions. </li>
      <li>Find a Classifiers that has a higher accuracy of identifying "Fraud" transactions.</a>  </li>
      <li>Create a Neural Network and compare the accuracy to our best classifier.</li>
</ul>

### Data Analysis
1. Understanding our data

</div><div class="fig figcenter fighighlight">
  <img src="/assets/images/class-dist-plot.png" width="600" height="300">
  <div class="figcaption"><br>
  </div>
</div>

<div class="fig figcenter fighighlight">
  <img src="/assets/images/trans.png" width="1200" height="300">
  <div class="figcaption"><br>
  </div>
</div>

On one hand, this figure shows that almost all of transaction records are non-fraud, while only 0.17% are actually fraudulent. On the other hand, the transaction amount is also significantly imbalanced with most of the amount very small. In fact, the mean of all the mounts made is approximately USD 88.

2. Preparing dataset
Before make a sub-sample of datasets, split the datasets into train data(80%) and test data(20%). Then, random under sampling technique is used to create a more balanced dataset and thus avoiding our models to overfitting. In more details, a 50/50 ratio subset is created with 492 cases of fraud and 492 cases of non-fraud transactions.

</div><div class="fig figcenter fighighlight">
  <img src="/assets/images/afterEqualRatio.png" width="1200" height="300">
  <div class="figcaption"><br>
  </div>
</div>

3. Observe Correlation of Features

</div><div class="fig figcenter fighighlight">
  <img src="/assets/images/featureCorrelationNegative.png" width="1200" height="300">
  <div class="figcaption"><br>
  </div>
</div>

</div><div class="fig figcenter fighighlight">
  <img src="/assets/images/featureCorrelationPositive.png" width="1200" height="300">
  <div class="figcaption"><br>
  </div>
</div>


<div class="fig figcenter fighighlight">
  <img src="/assets/images/IRQ-mod-Norm.png" width="1200" height="300">
  <div class="figcaption"><br>
  </div>
</div>

<div class="fig figcenter fighighlight">
  <img src="/assets/images/IRQ_good.png" width="1200" height="300">
  <div class="figcaption"><br> Summary of VGG Model Building.<br>
  </div>
</div>

<div class="fig figcenter fighighlight">
  <img src="/assets/images/ROCfitresult.png" width="1200" height="300">
  <div class="figcaption"><br> Summary of VGG Model Building.<br>
  </div>
</div>

<div class="fig figcenter fighighlight">
  <img src="/assets/images/actual_cm.png" width="1200" height="300">
  <div class="figcaption"><br> Summary of VGG Model Building.<br>
  </div>
</div>

<div class="fig figcenter fighighlight">
  <img src="/assets/images/actual_cmNeural.png" width="1200" height="300">
  <div class="figcaption"><br> Summary of VGG Model Building.<br>
  </div>
  




</div><div class="fig figcenter fighighlight">
  <img src="/assets/images/confuse.png" width="1200" height="300">
  <div class="figcaption"><br> Summary of VGG Model Building.<br>
  </div>
</div>

</div><div class="fig figcenter fighighlight">
  <img src="/assets/images/dimen_reduce.png" width="1200" height="300">
  <div class="figcaption"><br> Summary of VGG Model Building.<br>
  </div>
</div>



</div><div class="fig figcenter fighighlight">
  <img src="/assets/images/fitresult.png" width="1200" height="300">
  <div class="figcaption"><br> Summary of VGG Model Building.<br>
  </div>
</div>

</div><div class="fig figcenter fighighlight">
  <img src="/assets/images/overSamp.png" width="1200" height="300">
  <div class="figcaption"><br> Summary of VGG Model Building.<br>
  </div>
</div>



</div><div class="fig figcenter fighighlight">
  <img src="/assets/images/undersample_cm.png" width="1200" height="300">
  <div class="figcaption"><br> Summary of VGG Model Building.<br>
  </div>
</div>
