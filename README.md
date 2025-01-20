# A-B-Testing-for-Marketing-Campaign

A company recorded its data on marketing campaigns. The campaigns consist of 2 groups: (1) Test Campaign and (2) Control Campaign. Some keys metrics are recorded: Date, Amount of Money Spent (in USD), Number of Impressions, number of reach, number of website clicks, number of searches, number of view content, number of Add to Cart, number of Purchase.

We will conduct A/B testing to analyze whether one campaign outpeform the other in certai key metrics.
Dataset: https://www.kaggle.com/datasets/amirmotefaker/ab-testing-dataset/data
Agenda:
- Introduction of A/B testing
- Data Cleaning
- EDA
- Transformations
- Statistical Testing


## Introduction of A/B testing
A/B testing is the method to compare 2 versions and determine which version performs better in achieving a specific goal through hypothesis testing. This data-driven approach involves dividing the audience into segments, where one group (control group) experiences the original version, and the other group (test group) is exposed to a variation.
By analyzing key performance metrics such as click-through rates, conversion rates, or engagement levels, A/B testing enables teams to make informed decisions about content, or functionality improvements. 

## Data Cleaning
The dataset was transformed into better format suitable for DataFrame, through the use of split text. We then converted the metrics to the right type (integer) and removed null, duplicates and outliers.

## EDA
We plotted the key metrics for both control and test group: (1) Line plot for examining daily metrics (2) Bar plot for average metrics
As we can conclude from the plots, overall:
- Test group has more daily budget ( ~ 10% higher than control group), higher clicks (~ 18%) and slightly higher number of purchase (~3%)
- However, control group has higher number of impressions (~42%)

## Data Transformation:
We extracted some key metrics based on the columns provided to further analyse the campaign performances:
- Conversion rates = #purchase/ #website clicks
- Cost per click = Spend/ website clicks
- Cost per purchase = spend/ purchase
- Click through rates = clicks/ #impressions

## Statistical Testing:

We first examine whether the data follow the normal distribution to decide if we should apply parametric or non-parametric testing. We used Q-Q plot for visual examination and Shapiro-Wilk test for statistical testing. Both methods indicate that only the click through rate for control group follows the normal distribution. However, we need both distributions from test and control group in order to apply parametric testing. Therefore, we will need to apply non-parametric testing on all metrics.

The test we used is the Mann Whitney U test with no assumption on normal distribution - hence, it is applicable in this case. The null hypothesis is there is no significant difference between the 2 groups. When we use alpha = 0.05, we could conclude that there is no statistical difference between the 2 campaigns on conversion rate, cost per click, cost per purchase. However, there is a statistically significant difference between the test and control group (p = 0.00025) where test group performs better than the control group.
