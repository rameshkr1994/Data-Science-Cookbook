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
4. In some cases, override automatically generated
groupings using options within the Interactive Grouping
node so that characteristics and their attributes
conform to good business logic and still have sufficient
predictive power to be entered into a scorecard.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE2MjUyODQsLTI2MTQwMzU2OCwyMDIxMT
gxMTY2XX0=
-->