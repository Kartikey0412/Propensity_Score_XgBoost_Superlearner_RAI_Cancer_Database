# PS_score_RAI_Cancer_Database

In this analysis, a cohort of individuals comprising of controls vs cases who received Radioactive Iodine (RAI) for Thyroid cancer is obtained. The objective of this study was to find whether the treatment had a significant effect. But the control and case subjects are not matched based on the covariates and had significant differences before matching. 
In propensity_score.R, the differences in covariates before performing any matching are calculated. In an observational study propensity scores can be used to balance cases and control for covariates. this was shown in Rosenbaum and Rubin (1983) paper. In the first case I calculate propensity scores from logistic regression analysis from the probability to be in the treatment group. We use the 'Matchit' R library to create a 'Matched'  dataset using the 'Nearest' method. 
In ps_xgboost.R xgboost trees are used to calculate the propensity scores. I implement a 5 fold cross-validation to tune the xgboost algorithm, and obtain the matched dataset again using 'Matchit' with 'Nearest' neighbor matching. 
With help from PI, Ivan Diaz, In ps_superLearner.R, propensity scores are estimated based on the superLearner algorithm for a try for creating better matched datasets. Multi superLearner libraries are implemented (glm, glm.interaction, randomforest, mean, glmnet and finally 10 fold cross-validation was used for fine tuning for the binomial outcome. In the end again 'Matchit' algorithm is implemented with the 'full' method to create the final matched dataset.