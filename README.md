<h1 align='center'>Web Page Design A/B Test</h1> 

## Introduction

Web Pages of any business is the most powerful tool in attracting and keeping old customers. It is like the smile of a person you just met. If the person was not smiling you just don't have a good first impression of them. Similarly a well designed web page leads to more subscriptions, products sold and ads clicked. In this project I will showcase how a web page's design was A/B tested to check which one led to more clicks or as the company obtaining the data called in "conversions".

## What is A/B Testing?
A/B tests are one of the most powerful tools in a Data Scientists arsenal which is widely used in the industry to test features/products on a small group of people to percieve how it will be received to the end customer. A Product Data Scientists competency in A/B testing is at the core of their work. One thing to remember is that not every idea needs to be A/B tested. Some ideas can be expensive to test even on a small scale, so we have to be wise about which ideas to actually test on. This particular company decided this idea was worth testing and they have collected the data. I will be analyzing the data and conduct a statistical hypothesis test to determine whether the differences in user preference of one web page design over the other, are statistically significant or not.

## The Data

The dataset I have used contains around 300 thousand rows, where each row is an user who has been put into either a Control or Variation group (called treatment group in the data). The control group has been shown the old web page design and the treatment group has been shown the new webpage design. The last column in the datast signifies whether the user has 'converted' or not. Conversion here stands for any action the business wants a customer/user to make which results in a positive outcome.

The dataset I have used can be found at this URL: https://www.kaggle.com/zhangluyuan/ab-testing

## Data Cleaning and EDA

After importing all the necessary libraries and reading in the data, it is always a good idea to take a look at the dataset and the various data types it contains. 

