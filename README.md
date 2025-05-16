# Survival_Project-FALL_2024

## Final project for STA 779: Survival Analysis

## Abstract

Chronic granulomatous disease is a severe genetic disorder which affects white blood cells, and renders them unable kill certain types of bacteria and fungi. This results in patients with CGD being at great risk of serious infection, with most needing to be given antibacterials for the majority of their lives. Recent research has shown that patients who received Gamma Interferon treatment developed fewer severe infections. This was studied in a placebo-controlled trial which looked at the time to infection for patients injected with Gamma Interferon. Naturally, survival analysis methods are best suited to observe a differences between the treatment and control groups. In this data analysis we propose to fit a Cox proportional hazards model with treatment as a covariate. From this analysis, we find that the group given Gamma Interferon had a significantly lower hazard of experiencing an infection than the placebo group. In addition, using Breslow's estimator, we find that the treatment group had a higher probability of not experiencing an infection given they remained infection-free to a certain time. We found these conclusions held for when fitting for interactions between other covariates including sex, pattern of inheritance, and body composition. Specifically, treatment of Gamma Interferon increased the time to infection for patients regardless of factors. 

## Statistical Analysis Plan

As I explained in the topic proposal, the dataset measures time (in days) to serious infection with chronic
granulotamous disease. The data was collected during a controlled placebo study, measuring the effects
of gamma interferon on time to infection. The patients were assigned to placebo or treatment randomly.
Measurements were taken in thirteen treatment centers across the United States and Europe. The 203
individuals were accepted into the trial on a rolling basis, and left the study at different times as well.
Therefore, some were censored throughout the study. I have decided to drop one observation based on the
perceived inaccuracy of their reported measurements. This is because I intend to take body composition
into account, through the means of BMI, and their BMI was calculated to be above 80. Therefore the post-
exclusion sample size is 202. With this being said, I will drop patients who are younger than two years-old
when I fit a model with BMI as a covariate because the CDC says that BMI is not applicable to children
under two. Dropping these would bring the sample size to 190, which is still enough to get meaningful results.
As I stated before, the event of interest is a serious infection. I found that 37.62% of individuals got a
serious infection during the duration of the study. This means 76 patients were infected. To analyze the
overall survival, I will use the Cox-model to find the survival curve. From this, I will find survival estimates
at various times, including 50, 100, 200, and 300 days. These will be presented with a measure of uncer-
tainty by calculating a 95% log-log transformed confidence interval. When analyzing the survival, I will also
observe the effects on survival of a couple covariates. The main categorical variable I wish to observe are
the treatment status; in the dataset, this is defined as the variable ”treat” with two levels, ”placebo” and
”rIFN-g”. Because this variable is binary, I will summarize it using the count as well as the proportion of
total patients who were given the treatment. I will fit a Cox-model and find estimates of the log hazard ratios,
ˆβ. I will present this with a confidence interval. This will give me insight on the relative hazard between
two covariates. For example, when looking at the treatment group, I would expect that the estimates of ˆβ
to indicate that the gamma interferon is associated with a lower hazard than the placebo. Similarly to the
overall survival, I will find survival estimates at times 50, 100, 200, and 300 days, and these will be presented
with a measure of uncertainty by calculating a 95% log-log transformed confidence interval. In addition to
this, I want to look at interactions between treatment and age, treatment and sex, and treatment and disease
inheritance. This would be interesting to see if the gamma interferon affects the hazard differently based on
these other covariates. I will compare these estimates the same way as before, using confidence intervals with
estimates of the log hazard ratios.
For the continuous covariates, I would like to look at the variables age and BMI. For these covariates I
will, again, fit a Cox-model and find estimates of the log hazard ratios, ˆβ. For each of these I will construct
a 95% confidence interval for the log hazard ratios, and use a local Wald test. This will test the hypothesis,
H0 : β = 0, meaning I will be able to tell if the covariates are correlated with the survival. In order to analyze
the survival, the textbook recommends that I partition the continuous variables into ranges.

I would analyze the survival based on the groups the same way as before. I would find 95% log-log
transformed confidence intervals for survival estimates at 50, 100, 200, and 300 days.

When presenting the results of this analysis I will display the survival curves for different groups, as
well as the overall survival. I believe this is the most intuitive way to see differences in survival based on
covariates. In addition, I will display the confidence intervals using a forest plot. However, when I need to
communicate statistical significance, I will need to include p-values which are best displayed using formatted
tables.

The secondary objective that I wish to explore is to fit a nonparametric survival model to the data
using the covariate, treatment, and calculate nonparametric measures of central tendency. My reason for
exploring this is to compare the nonparametric Kaplan-Meier estimates to the survival estimates obtained
by the semi-parametric Cox-model. Finally, all of my analysis will be done in R.


