
> Written with [StackEdit](https://stackedit.io/)

## Variable selection for Generalized Linear Mixed Models

In general, using stepwise model selection is not recommended see [here](https://communities.sas.com/t5/Statistical-Procedures/proc-glimmix-selection-stepwise-or-backwards/td-p/172976).  Here, they recommend to use SAS GLMSELECT to find the main factors. But GLMSELECT is only able to deal with general linear models and not with generalized linear models. Therefore, there is no way to use binomial or even a beta distribution. You can find some interesting examples about hot to apply GLMSELCECT [here](https://www.coursera.org/lecture/machine-learning-data-analysis/testing-a-lasso-regression-with-sas-ntKNE) and among youtube SAS short videos. You also have HPGENSELECT that is able to use LASSO for Generalized Linear Models but not for Generalized Linear Mixed Models, see [here](https://www.youtube.com/watch?v=IlLUpUEAhXg). 

Another option could be use BIC and AIC for model selection. 

The reference for applying 

One option is using LASSO with R package [glmmLasso](https://cran.r-project.org/web/packages/glmmLasso/glmmLasso.pdf). Currently only "binomial" and "poisson" are implemented as you can see [here](https://rdrr.io/rforge/glmmixedlasso/man/glmmlasso.html). 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg2MTkzMTY2NF19
-->