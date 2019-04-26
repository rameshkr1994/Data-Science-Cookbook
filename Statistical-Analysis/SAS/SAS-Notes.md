


> Written with [StackEdit](https://stackedit.io/).

# SAS Notes

### How Do You Compute an R-square Statistic in GLM, GAMPL and GLIMMIX ?

For Generalized linear models and Generalized Additive models use the following SAS macro:
- [R-square and partial R-square for generalized linear models based on the variance function](http://support.sas.com/kb/60/162.html)
- For Generalized Linear Mixed Models there are two macros:
	- The two macros appears in book the book [_"Generalized Linear and Nonlinear Models for Correlated Data: Theory and Applications Using SAS"_](https://support.sas.com/en/books/authors/edward-vonesh.html).
	- Also read this article: [_Insights into Using the GLIMMIX Procedure to Model Categorical Outcomes with Random Effects_](https://www.sas.com/content/dam/SAS/support/en/sas-global-forum-proceedings/2018/2179-2018.pdf).

### CHOOSING THE CORRECT STATISTICAL TEST IN SAS, STATA, SPSS AND R

[CHOOSING THE CORRECT STATISTICAL TEST IN SAS, STATA, SPSS AND R](https://stats.idre.ucla.edu/other/mult-pkg/whatstat/)

### Using the Output Delivery System

- [Good summary about the use of ODS](https://support.sas.com/documentation/cdl/en/statug/63033/HTML/default/viewer.htm#ods_toc.htm)
- In the above page you can find the way to creating an Output Data Set from an ODS Table [here](https://support.sas.com/documentation/cdl/en/statug/63033/HTML/default/viewer.htm#statug_ods_sect011.htm). 
- [Maintaining Formats when Exporting Data from SAS® into Microsoft® Excel](http://support.sas.com/resources/papers/proceedings13/316-2013.pdf)
- [Maintaing date format when exporting to XLSX](https://communities.sas.com/t5/SAS-Programming/Maintaing-date-format-when-exporting-to-XLSX/td-p/422748)
- [Proc export to CSV](https://communities.sas.com/t5/SAS-Programming/Proc-export-to-CSV/td-p/300803)
- [Statistical Graphics Using ODS](http://support.sas.com/documentation/cdl/en/statug/68162/HTML/default/viewer.htm#statug_odsgraph_sect016.htm)
- [Send your SAS graphs to Excel, directly to Excel](https://blogs.sas.com/content/sastraining/2016/11/15/send-your-sas-graphs-to-excel-directly-to-excel/)

A good use case:
```sas
*=================================================================================;
/* GLMM with Dist= BETA Link = LOGIT + Random effect: intercept*/
*=================================================================================;

*ods select StudentPanel ResidualPanel PearsonPanel;
*ods listing gpath='/nyl/data/tenants/insurance/asd/marcos/projects/TriggerAnalysis/git_traking/imgs';
*ods graphics  / imagename="ResidualPanel" imagefmt=png reset;

*ods output FitStatistics=Output;  

title "CC Model - Version 04";
title2 "GLMM model - Distribution Beta - Link Logit - Random Intercept";
ods trace on;
PROC GLIMMIX DATA = work.abt_cc_05 PLOTS=ALL METHOD=LAPLACE oddsratio;
	CLASS GOCODE TRIGGER (REF = FIRST) PROACTIVE (REF = FIRST)  /*TRIGGERGO*/ PRIOR_FYC_LOG_GRP (REF = FIRST) AVG_FYC_GRP CULTMARK_GRP (REF = FIRST);
	MODEL RETENTION = TRIGGER /*PROACTIVE*/ /*TRIGGERGO*/ &grp_vars LIFE_INVESTMENT AAPR RURAL_URBAN /  SOLUTION DIST=BETA LINK=LOGIT ;
	RANDOM INTERCEPT / SUBJECT=GOCODE SOLUTION;
	OUTPUT OUT=FRACOUT PRED=XBETA PRED(ILINK)=PREDPROB LCL(ILINK)=LOWER UCL(ILINK)=UPPER;
	ODS OUTPUT ParameterEstimates=model_output_cc Tests3=type3;
RUN;

*=================================================================================;
*Variable importance calculation;
*=================================================================================;
data model_output_cc_01;
	set model_output_cc;
	aux = abs(estimate) / abs(stderr);
	if effect = "Intercept" then aux = .; 
run;
	
proc sql;
 	create table model_output_cc_02 as select *, sum(aux) as TotalVar
 	from model_output_cc_01;
quit;

data model_output_cc_03 (drop = aux TotalVar);
	set model_output_cc_02;
	format VarImp PERCENT8.2 Probt 8.4;
	VarImp = aux / TotalVar;
run;

%let fileloc = '/data/Output_Data/CC_MODEL_OUTPUT2.xlsx';

ods excel file=&fileloc style=HTMLBLUE;

proc print data=model_output_cc_03;
run;

/*proc print data=type3; It is possible to add another table on a differnent excel tab too.
run;*/

ods excel close;
```

### Different ways to use `__NULL__`in SAS

- This is an interesting link with that includes the way to create a macro variable from a value in a data set. This is the [link](https://blogs.sas.com/content/iml/2018/06/11/6-ways-_null_-data-set-sas.html).


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2OTg4MzM0MjgsLTE3NjEyMjIxMTYsLT
U2NDExODQwLDExNjU5MzAyOTgsLTEwMDQ3Mjc1NTcsLTE1Mzg0
OTI5MDVdfQ==
-->