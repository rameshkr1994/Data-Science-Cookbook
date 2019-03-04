> Written with [StackEdit](https://stackedit.io/).

## Methodology Summary

### Interactive Grouping

- Interactive Grouping is used for two main tasks:
	- Perform univariate screening to eliminate weak characteristics or those that do not conform to good business logic.
	- Group the strongest characteristics (that is, create attribute levels) in order to produce a model in scorecard format.

- Grouping also offers a number of advantages:
	- Helps with dealing with outliers
	- Useful for understanding relationships
	- Enables modeling nonlinearities with a linear model

- For categorical variables, attributes with similar WOE values can be grouped together in accordance with business logic or regulatory requirements.

> Grouping the attributes of characteristics is done for a number of reasons:
> -  Produce a scorecard in the format of a scorecard
> - Manage the number of attributes per characteristic and prevent overfitting
> - Improve the predictive power of the characteristic
> - Produce attributes that conform to business experience and allow for buy-in
> - Facilitate understanding of the relationships among the characteristics and the target variable
> - Increase knowledge of the applicant population, which  can help to develop better credit risk strategies
> - Help  handle outlier values
>  - Enable modeling nonlinear relationships with a linear model

### Initial Characteristic Analysis
Initial characteristic analysis of interval variables using the Interactive Grouping node of SAS Enterprise Miner
generally involves these steps:
1. Pre-bin the interval variables into a number of user-specified quantiles or buckets. This produces fine
detailed groupings.
2. Aggregate the fine detailed groupings into a smaller number using a decision tree to make split choices. This produces coarse groupings.
3. Calculate and examine the key assessment metrics, WOE and IV.
	- WOE is used for evaluating how well attributes discriminate for each given characteristic.
	- IV is used for evaluating a characteristic’s overall predictive power.
4. In some cases, override automatically generated groupings using options within the Interactive Grouping node so that characteristics and their attributes conform to good business logic and still have sufficient predictive power to be entered into a scorecard.

### Metrics for Characteristic Analysis
Measures commonly used in a characteristic analysis:
- Weights of evidence (WOE)
-  Information value (IV)
-  Gini statistic

### Weights of Evidence (WOE)
- WOE measures the strength of the attributes of a characteristic in separating good and bad accounts.
- WOE is based on comparing the proportion of goods to bads at each attribute level.
- It is defined as $ln(\frac{Distr\,Good_i}{Distr\,Bad_i})$ for each attribute $i$ of a characteristic.

The formula for WOE is  $ln( \frac{Distr\,Good_i}{Distr\,Bad_i})$, where $Distr\,Good_i$ and $Distr\,Bad_i$ are calculated for each attribute of the variable as shown in the table below.

>Negative numbers imply that the particular attribute is isolating a higher proportion of bads than
goods. (That is, negative numbers are ***worse*** in the sense that applicants in an attribute group with
a higher negative number are worse credit risks.)

The following table shows a typical grouping for the characteristic variable **`Age`**. In the table, the columns
`Total Distribution`, `Distribution Goods`, and `Distribution Bads` are the percentage distribution of the total,
good, and bad cases, respectively.

|Age|Count|Total Distribution|Goods|Distribution Goods|Bads  |Distribution Bads|Bad Rate|WOE  |
|--------|------|-----|-------|-------------------|------|------------------|---------|-----|
|Missing|1000|2.50%              |860|2.38%              |140|3.65%             |14.00%   |-0.43|
|18-22|4000|10.00%             |3040|8.41%              |960|25.00%            |24.00%   |-1.09|
|23-26|6000|15.00%             |4920|13.61%             |1080|38.13%            |18.00%   |-0.73|
|27-29|9000|22.50%             |8100|22.40%             |900|23.44%            |10.00%   |-0.05|
|30-35|10000|25.00%             |9500|26.27%             |500|13.02%            |5.00%    |0.70 |
|36-44|7000|17.50%             |6800|18.81%             |200|5.21%             |2.86%    |1.28 |
|44+|3000|7.50%              |2940|8.13%              |60|1.56%             |2.00%    |1.65 |
|**Total**|**40000**|**100%**               |**36160**|**100%**     |**3840**|**100%** |**9.60%**    |

### Logistic Funciton

To explain the popularity of logistic regression, we show here the *logistic function*, which describes the mathematical form on which the logistic model is based. This function, called $f(z)$, is given by 1 over 1 plus e to the minus z. We have plotted the values of this function as z varies from $-\infty$ to $+\infty$.

$$f(z)=\frac{1}{1 + e^{-z}}$$

### Scaling

Scorecards can be produced in many formats (e.g., SAS code, points system, etc.). In some cases— such as online or real-time scorecard usage that is often dependent on implementation platforms, regulatory instructions requiring the provision of reasons for decline, simplicity and ease of use, and other factors mentioned in the Why “Scorecard” Format? section in Chapter 4— the scorecard needs to be produced in a particular format with grouped variables and points (see Exhibit 1.1). In this case, **scaling needs to be applied**. Scaling refers to the range and format of scores in a scorecard and the rate of change in odds for increases in score. Scorecard scores can take several forms with decimal or discrete number scores:

- Where the score is the good/bad odd or probability of bad (e.g., score of 6 means a 6: 1 odd or 6 percent chance of default). 
- With some defined numerical minimum/ maximum scale (e.g., –1, 0– 1,000, 150– 350), or without a defined range but with a specified odds ratio at a certain point (e.g., odds of 5: 1 at 500) and specified rate of change of odds (e.g., odds double every 50 points).

The choice of scaling, or its parameters, does not affect the predictive strength of the scorecard. It is an operational decision based on considerations such as:

- Implementability of the scorecard into application processing software. Certain software can implement scorecards only in the format shown in Exhibit 1.1. 
- Ease of understanding by staff (e.g., variables with discrete points are easier to work with and understand, therefore generate confidence among end users). 
- Continuity with existing scorecards or other scorecards in the company. This avoids retraining on scorecard usage and interpretation of scores.

Note that at the moment we have a logistic regression equation and binned characteristics. What we want to do is assign points to each attribute in each characteristic, such that the total score (when you add up attributes across characteristics) can then be interpreted to mean odds or probabilities of default, for example.

There are various scales in use in the industry. One of the most common is a scorecard with discrete scores scaled logarithmically, with the odds doubling at every 20 points. To understand this, let’s take a look at a typical odds relationship to some rank ordered input. The curve would look something like Exhibit 10.23

![fsdafs](https://nbviewer.jupyter.org/github/markeyser/Data-Science-Cookbook/blob/master/Statistical-Analysis/Scorecards/imgs/figure-10.23.png)











<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU4MjQwMTMwNCwtMzQ3Mjg4NzMsLTY1OD
E2OTI5MSwtMTQ4MTYwOTc2NywxNDI5OTkxNzQ2LDUzNjk0OTY2
MCwtMTI1MjY1NzcyLDEwNjc4Mjg3NTYsLTIxMjI2ODQ2MTYsLT
E2OTE0ODI2MjYsLTI2MTQwMzU2OCwyMDIxMTgxMTY2XX0=
-->