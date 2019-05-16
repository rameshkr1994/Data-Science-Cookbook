


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

### Delete all dataset from the `work` library 

```SAS
proc datasets lib=work kill nolist memtype=data;
quit;
```

### List all datasets on the `work` library

```SAS
ods output Members=Members;
proc datasets library=work memtype=data;
run;
quit;
```

### Using `PROC APPEND` to append multiple datasets into one dataset while using a macro 

```sas
*Remove TRIGGER.R2_GLMM_MODELS to avoid accumulating;
proc datasets library=TRIGGER;
   delete R2_GLMM_MODELS;
run;

%MACRO R2GLMM (INSET=,MODEL=);

*### macro code ####;

*Use PROC APPEND to append the R2 of every model;
proc append base=TRIGGER.R2_GLMM_MODELS data=R2_&MODEL force;
run;

%MEND R2GLMM;

%R2GLMM (Inset = FRACOUT_GLMM_1P_P07_18, MODEL = GLMM_1P_P07_18);	
%R2GLMM (Inset = FRACOUT_GLMM_2P_P07_10, MODEL = GLMM_2P_P07_10);	
%R2GLMM (Inset = FRACOUT_GLMM_2P_P07_17, MODEL = GLMM_2P_P07_17);	

```

[reference](https://support.sas.com/resources/papers/proceedings/pdfs/sgf2008/085-2008.pdf)

### Break up long string in code
Example:

```sas
%let basedir=/nyl/data/tenants/insurance/asd/marcos/projects;
%let procject=TriggerAnalysis/git_traking/Output_Data;
%let fname=3P_MODEL_OUTPUT.xlsx;
%let infile="&basedir/&procject/&fname";

%put &infile;
```
Output:
```
"/nyl/data/tenants/insurance/asd/marcos/projects/TriggerAnalysis/git_traking/Output_Data/3P_MODEL_OUTPUT.xlsx"
```

Reference: [SAS: Break up long string in code](https://stackoverflow.com/questions/40002883/sas-break-up-long-string-in-code)

### Looping through table rows to create Macro Variables
Let's say we have the following SAS dataset:

|Effect                  |
|------------------------|
|Intercept				 |
|PROACTIVE				 |
|PROACTIVE				 |
|LHIPrt_GRP				 |
|LHIPrt_GRP				 |
|Life_Health_Investment	 |
|RURAL_URBAN_GRP		 |	
|RURAL_URBAN_GRP		 |	
|AVG_AGE_GRP			 |	
|AVG_AGE_GRP             |

We want to extract a unique name per each variable and assign this name to a macro-variable. Don't use the following code, use the next one instead.

```sas
*Getting odd rows only;
data OddRows (keep= effect);
	set trigger.model_output_glmm_2p_p07_10;
	orig_obs = _n_;
	if mod(_n_,2) eq 0 then output;
run;

*getting the total number of rows;
data _null_;
	set OddRows nobs=nobs;
	put nobs=;
	call symputx("nobs", nobs);
	stop;
run;

%put &nobs;

*Assigning a macro-variable to each row-value;
%macro do_all;

%do i=1 %to &nobs;
    Data _null_;
        Set Oddrows(firstobs=&i obs=&i);
        call symputx(cats('VarName',&i) , Effect);
    run;
%end;

%mend;
%do_all;

%put &VarName1;
%put &VarName2;
%put &VarName3;
%put &VarName4;
%put &VarName5;
```
output:

```
73 %put &VarName1;
PROACTIVE
74 %put &VarName2;
LHIPrt_GRP
75 %put &VarName3;
Life_Health_Investment
76 %put &VarName4;
RURAL_URBAN_GRP
77 %put &VarName5;
AVG_AGE_GRP
```
the above code won't work, this is the right code:

```sas
*Getting odd rows only;
data OddRows (keep= effect);
	set trigger.model_output_glmm_2p_p07_10;
	orig_obs = _n_;
	if mod(_n_,2) eq 0 then output;
run;
*create &effect macro variable to store the 5 values;
proc sql noprint;
   		select distinct effect 
      		into :effect
      		separated by " "
      		from oddrows;
quit;

%put &effect;
*We can use &effect in the keep to select the columns;
*But the IN funciton needs 'value1', 'value2', ...;
*Let's crete a varible called vars with the sring;
data testy(keep=vars);
	vars = "'"||tranwrd(trim("&effect"), " ", "','")||"'";
run;
*Now let assign the new string to a macro variable &variables;
data _null_;
	set testy;
	call symputx("variables", vars);
run;

%put &variables;

*Now we are ready to extract the rows and columns we
nedd from the big matrix;
data xxx (keep= variable &effect );
	set TRIGGER.CORR_MATRIX_2P;
	if variable in(&variables)  then output;
run;
```
References:

- [Values in a column as a Macro Variable](https://stackoverflow.com/questions/20749040/values-in-a-column-as-a-macro-variable)
- [Setting Macro Variable equal to value in table](https://stackoverflow.com/questions/29656010/setting-macro-variable-equal-to-value-in-table)
- [Add single quotes and commas to a list of words]([https://communities.sas.com/t5/SAS-Programming/add-single-quotes-and-commas-to-a-list-of-words/td-p/437511](https://communities.sas.com/t5/SAS-Programming/add-single-quotes-and-commas-to-a-list-of-words/td-p/437511))

### Remove suffix / prefix or any sub string from column values or from column names

```sas
*Remove _02 suffix from the variable column variable names;
data TRIGGER.CORR_MATRIX_&MODEL;
	set TRIGGER.CORR_MATRIX_&MODEL;;
	variable = tranwrd(variable,'_02','');
;
run;
*Remove _2 from the variable names (columns);
proc contents data=TRIGGER.CORR_MATRIX_&MODEL out=_contents_ noprint;
run;
proc sql noprint;
    select cats(name,'=',tranwrd(name,'_02','')) into :renames 
        separated by ' ' from _contents_ where find(name,'_02')>0;
quit;
%put &=renames;

proc datasets library=trigger nolist;
    modify CORR_MATRIX_&MODEL;
    rename &renames;
    delete _contents_;
run;
quit;
```
- Refernece: [Delete the last few character in variable name](https://communities.sas.com/t5/SAS-Programming/Delete-the-last-few-character-in-variable-name/td-p/546907)

### Inserting Comments in Macro

Macro comment: 
> - First form: beginning with `/*` and ending with `*/`
>    - Recommended when explaining the definition of the macro parameters. 
>    - Not recommended in the macro since it can be hard for debugging due to the inconvenience when you try to comment out code you don’t want to run. 
>  - Second form: begins with a `%* `and ends with a `;` 
>    - Recommended and should be the first choice when inserting a comment in a macro. 
>   - The comment will not be seen in the log when macro is executed. 

The asterisk-style comment ( `*` commentary `;` ) used in SAS code is not recommended within a macro.

reference: [Get Started Writing SAS® Macros]([https://www.lexjansen.com/nesug/nesug11/cc/cc12.pdf](https://www.lexjansen.com/nesug/nesug11/cc/cc12.pdf))

### Jittering Data
There are many techniques and approaches to jittering data. The simplest is to add random uniform noise to each variable, as shown in the following DATA step:
```SAS
data iris(drop=s);
set sashelp.iris(where=(Species="Setosa"));
/** add random uniform noise in [-0.5, 0.5] **/
s = 1; /** scale factor **/
jPetalWidth = PetalWidth + s*(ranuni(1)-0.5);
jPetalLength = PetalLength + s*(ranuni(1)-0.5);
label jPetalWidth = "Petal Width (mm)"
      jPetalLength= "Petal Length (mm)";
run;
 
proc sgplot data=iris;
title "Scatter Plot of Jittered Data";
scatter x=jPetalLength y=jPetalWidth;
run;
```
Reference: [Jittering to prevent overplotting in statistical graphics](https://blogs.sas.com/content/iml/2011/07/05/jittering-to-prevent-overplotting-in-statistical-graphics.html)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NTQyNTE0MjEsMjEyNjI0MTc0LC0xNj
A0NjM4MDAyLDk1MDM1NjE3OSwtMzQxMzE5Nzk1LDMxNTA5NDAy
OSw1MjMxOTQyMDMsMTYwMzA2MzI1MywtNTE2MDgyNzk3LDEwNj
kxMjk1MjUsLTE2OTg4MzM0MjgsLTE3NjEyMjIxMTYsLTU2NDEx
ODQwLDExNjU5MzAyOTgsLTEwMDQ3Mjc1NTcsLTE1Mzg0OTI5MD
VdfQ==
-->