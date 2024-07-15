# Generalized-Linear-Model-for-the-Stroke-Rate
Exploring the association between whether Stroke and these various  factors, which include Age, BMI, Average glucose level, Gender, Smoking  status and Hypertension.
1. Introduction
Background
Stroke is correlated with many factors. It is commonly considered that stroke is highly correlated with
age, health status, and lifestyle. Understanding what factors correlate with stroke and how they correlate
with stroke help identify at-risk populations and prevent stroke. In the article Influence of Age and Health
Behaviors on Stroke Risk: Lessons from Longitudinal Studies, the author investigated how age affects stroke
by analyzing trends across different populations over time and concluded that stroke risk increases significantly with age (Kelly-Hayes, 2010). In another article Body Mass Index Measured Repeatedly over 42 Years
as a Risk Factor for Ischemic Stroke: The HUNT Study, researchers calculated average BMI values and
related these to the risk of stroke and observed a higher risk for stroke among participants with obesity or
overweight over adulthood (Horn et al., 2023). Further in the article Glucose and Acute Stroke : Evidence
for an Interlude, by analyzing clinical data and categorizing them by blood glucose levels, the researchers
concludes that both hyperglycemia and hypoglycemia significantly affect stroke risk (Helgason, 1988).
Research Question
We want to combine all predictors in the existing literature in one comprehensive stroke prediction model.
Our goal is to predict the probability of getting a stroke based on age, BMI, average glucose level, which are
already discussed in the literature, as well as gender, smoking status and hypertension, three other candidate
predictors. We want to identify significant predictors and find the best stroke prediction model.

Model Diagnostics. and Validation
1. Dfbetas:
We will use dfbetas to identify influential observations by measuring how each one affects the regression
coefficients. Observations with a dfbeta over √
2
(n)
are flagged as influential, and we’ll consider their context
to decide whether to keep them.
2. Deviance Residuals:
We will plot residuals vs covariates to see whether residuals are independent of covariates. Residuals independent of covariates are a sign of a good model. Having systematic patterns might indicate misspecification
of model, where transformation or adjustments are required.
3. Cross-Validation
We’ll employ cross-validation to assess our model’s predictive accuracy. We fit the model on n-1 data parts
and test on the remaining part. A good model’s calibration plot will align closely with a 45-degree line, with
predicted probabilities equal to actual probabilities.
4.Discrimination With The ROC Curve
We’ll assess model performance using ROC curves, plotting sensitivity versus (1-specificity) across thresholds
to determine the true positive and false positive rates. A higher AUC indicates better model discrimination.

Godness of Model
1. Dfbetas:
-Age: No influential points exceed the threshold; however, a fanning pattern in age-related dfbetas suggests
observations at older ages affect the estimates of age more. This can be due to the non-linearity of the
relationship between age and stroke or the skewness of data in age. We will discuss this further in the
limitation section.
-Average Glucose Level: Dfbetas values vary around the zero and there are no systematic patterns. The
blue lines are relatively flat around zero. No influential observations are observed.
-Hypertension and Heart Disease: There are no observations within each group (0 and 1) that appear
to have a significant influence on the estimates for hypertension and heart disease.

2. Deviance Residuals
-Age: The residual plot shows a separation pattern, with one group having significantly higher deviance
residuals. This suggests there are missing variables or missing interactions. We will further discuss this in
the limitation section.
-Average Glucose Level: Residuals are mostly centered around zero but show some separation. One group
have average higher deviance residuals then the other. Reasons might be missing predictors, interactions, or
subgroups. We will discuss this in the limitations.
-Hypertension and Heart Disease: Residuals are centered slightly below zero with a similar spread in
each group, suggesting no systematic bias.The flat blue lines indicate no trends.

3.Cross Validation
The small deviation of the Bias-corrected line from the off-diagonal line indicates overestimation at high
probabilities by the model. The mean absolute error (MAE) is 0.004. That is, on average, the absolute
difference between the predicted probabilities and the actual outcomes is 0.004. The model is predicting
well for low probabilities but not good enough for high probabilities.

4. Discrimination with ROC curve
The ROC is displayed as the red line with AUC being 0.83. It shows that the model can discriminate 83%
of stroke and not stroke. The AUC is high, thus the model has good discrimination ability.
