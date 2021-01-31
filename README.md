<h1 align='center'>Web Page Design A/B Test</h1> 

## Introduction

Web Pages of any business is the most powerful tool in attracting and keeping old customers. It is like the smile of a person you just met. If the person was not smiling you just don't have a good first impression of them. Similarly a well designed web page leads to more subscriptions, products sold and ads clicked. In this project I will showcase how a web page's design was A/B tested to check which one led to more clicks or as the company obtained the data called in "conversions".

## What is A/B Testing?
A/B tests are one of the most powerful tools in a Data Scientists arsenal which is widely used in the industry to test features/products on a small group of people to perceive how it will be received by the end customer. A Product Data Scientists competency in A/B testing is at the core of their work. One thing to remember is that not every idea needs to be A/B tested. Some ideas can be expensive to test even on a small scale, so we have to be wise about which ideas to actually test on. This particular company decided this idea was worth testing and they have collected the data. I will be analyzing the data and conducting a statistical hypothesis test to determine whether the differences in user preference of one web page design over the other, are statistically significant or not.

## The Data

The dataset I have used contains around 300 thousand rows, where each row is a user who has been put into either a Control or Variation group (called treatment group in the data). The control group has been shown the old web page design and the treatment group has been shown the new webpage design. The last column in the dataset signifies whether the user has 'converted' or not. Conversion here stands for any action the business wants a customer/user to make which results in a positive outcome.

The dataset I have used can be found at this URL: https://www.kaggle.com/zhangluyuan/ab-testing

## Data Cleaning and EDA

After importing all the necessary libraries and reading in the data, it is always a good idea to take a look at the dataset and the various data types it contains. 

<h5 align="center">The Dataset</h5>
<p align="right">
  <img src="https://github.com/CSmahesh04/CTR_AB_Test/blob/main/Images/the_dataset.png" width=750>
</p>
There are exactly 294,478 rows and 5 columns in the dataset. The five columns have only two data types: object and int64. The **_timestamp_** column is not converted to a better date-time format as we will not require it for A/B testing.

Next we check to see if there's any overlap or duplicate inputs in the dataset. I checked to see whether users from one group saw the web page of the other group. As you can see below, there seem to be a total of around 4000 users who use the other groups web pages. Since 4000 is 0.1% of the total number of rows (~400,000), I just removed those users.

HERE PUT IMAGE OVERLAPPING USERS

Now I check whether there any more anomalies by checking again. Now the treatment group is restricted to the new page and the control group is restricted to the old page, we can move forward. Next I checked for multiple user records, based on **_user_id_**. There seems to be just one instance of multiple user entry in the dataset. Below are the instances where a user has been recorded multiple times.

HERE PUT IMAGE of Duplicate users.

This particular user(**_user_id_**: 773192) from the treatment group saw the new web page twice and didn't convert either time. So for simplicity's sake I will remove the second instance from the dataset.

To better understand the data, I have plotted a bar chart where the total number of users from each group and conversion rate have been visualized. It seems that both groups have about the same ratio of conversion. But we will determine this with certainty.

HERE PUT IMAGE OF BAR

Also I checked if the number of users in the two groups are divided equally or not.

HERE PUT IMAGE OF PIE

## Chi-Squared Test

Since we are dealing with the conversion variable, which has a discrete value, it is considered a **Bernoulli Distribution**. That means an user will either convert (1) or not convert(0). The Chi-Squared test is a perfect testing method for values in the **Bernoulli Distribution**. We calculate the chi-squared test statistic and use that to calculate the p-value. Then the p-value is compared against the level of significance to check whether there is a significant difference between the two groups.

## Data Preparation and Results

Now that we have cleaned the data, it is time to conduct a statistical hypothesis test. The dataset has to be in a specific format to use the _scipy_ library to do the Chi-Squared test on our data. Once the data is in the correct format, the test can be done using the _scipy_ library. It automatically calculates both the chi-squared statistic and the p-value.

The p-value turns out to be 0.1898, which translates to 19%. The p-value is greater than _alpha_, at a 5% level of significance (we have to look alpha up in a table). This means we don't reject the null hypothesis. The null hypothesis here being, there is a statistically significant difference between the conversion rates for the two web pages. Thus, by rejecting the null hypothesis, it has been established that there is no preference for the user of one web page over the other.

For a quick verification, I conducted a sanity check where I calculated the conversion rates between the two groups and the difference between them is minimal at 0.0013. Since the total number of people in both groups is the same, this means there wasn't any problem with the Chi-Squared test itself. 

## Technologies Used

1. Python
2. Pandas
3. Numpy
4. Matplotlib
5. Scipy
 
