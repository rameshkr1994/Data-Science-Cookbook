
> Written with [StackEdit](https://stackedit.io/).

# Mixed Models

## Overview

Correlated data arise frequently in statistical analyses. This may be due to: 

- Grouping of subjects, e.g., students within classrooms, 
- or to repeated measurements on each subject over time or space, 
- or to multiple related outcome measures at one point in time. 

Mixed model analysis provides a general, flexible approach in these situations, because it allows a wide variety of correlation patterns (or variance-covariance structures) to be explicitly modeled.

Multiple measurements per subject generally result in the **correlated errors** that are explicitly forbidden by the assumptions of standard (between-subjects) AN(C)OVA and regression models.

- While repeated measures analysis of the type found in SPSS, which I will call “classical repeated measures analysis”, can model general (multivariate approach) or spherical (univariate approach) variance-covariance structures, they are not suited for other explicit structures.
- Even more importantly, these repeated measures approaches discard all results on any subject with even a single missing measurement, while mixed models allow other data on such subjects to be used as long as the missing data meets the so-called missing-at-random definition.
- Another advantage of mixed models is that they naturally handle uneven spacing of repeated measurements, whether intentional or unintentional.
- Also important is the fact that mixed model analysis is often more interpretable than classical repeated measures.
- Finally, mixed models can also be extended (as generalized mixed models) to non-Normal outcomes.

The term **mixed model** refers to the use of both fixed and random effects in the same analysis. As explained in section 14.1,  **fixed effects** have levels that are of primary interest and would be used again if the experiment were repeated. **Random effects** have levels that are not of primary interest, but rather are thought of as a random selection from a much larger set of levels. **Subject effects** are almost always random effects, while **treatment levels** are almost always fixed effects. Other examples of random effects include cities in a multi-site trial, batches in a chemical or industrial experiment, and classrooms in an educational setting.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI0MzQ5OTEzMF19
-->