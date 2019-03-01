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

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyNTI2NTc3MiwxMDY3ODI4NzU2LC0yMT
IyNjg0NjE2LC0xNjkxNDgyNjI2LC0yNjE0MDM1NjgsMjAyMTE4
MTE2Nl19
-->