
> Written with [StackEdit](https://stackedit.io/).

## Multiple Comparisons

When comparing more than two means, an ANOVA _F_ test tells you whether the means are significantly different from each other, but it does not tell you which means differ from which other means. Multiple-comparison procedures (MCPs), also called _mean separation tests_, give you more detailed information about the differences among the means. The goal in multiple comparisons is to compare the average effects of three or more "treatments" (for example, drugs, groups of subjects) to decide which treatments are better, which ones are worse, and by how much, while controlling the probability of making an incorrect decision. A variety of multiple-comparison methods are available with the [MEANS](http://support.sas.com/documentation/cdl/en/statug/68162/HTML/default/statug_glm_syntax15.htm) and [LSMEANS](http://support.sas.com/documentation/cdl/en/statug/68162/HTML/default/statug_glm_syntax10.htm) statement in the GLM procedure.



### References
- [Interpreting the Differences Among LSMEANS in Generalized Linear Models]([https://www.mwsug.org/proceedings/2011/dataviz/MWSUG-2011-DG08.pdf)
- [Means vs. LSMeans and Type I vs. Type III Sums of Squares](https://dnett.public.iastate.edu/S402/wlsmeanssol.pdf)
- [GENMOD AND MULTIPLE COMPARISON](https://communities.sas.com/t5/SAS-Procedures/GENMOD-AND-MULTIPLE-COMPARISON/td-p/294042?nobounce)
- [Multiple Comparisons using GLM Procedure]([http://support.sas.com/documentation/cdl/en/statug/68162/HTML/default/viewer.htm#statug_glm_details29.htm](http://support.sas.com/documentation/cdl/en/statug/68162/HTML/default/viewer.htm#statug_glm_details29.htm))
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAxNDczMzUxLDk3MTk2ODg3Myw1ODg2NT
Q4MjksMTQ2MTQ2Mjk5NF19
-->