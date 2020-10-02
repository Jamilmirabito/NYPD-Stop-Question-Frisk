# NYPD-Stop-Question-Frisk
## Introduction
Policing crime in the United States has long been a highly controversial practice given the disproportionate surveillance, arrest, and imprisonment of individuals from communities of color. While these disparities are largely a result of systemic racism, research suggests that there are likely individual biases that may contribute to disparities in arrests as well. This analysis aims to determine which individual-level factors contribute most to an arrest in the hopes that, if biases are present, they may be addressed.
### Research Questions:
- How large are the disparities in  arrests resulting from a Stop, Question, and Frisk incident?
- What are the most common factors resulting in an arrest?

## Data
- NYC Stop, Question, and Frisk Data (2016): 2016 was the most recent year with understandable documentation
- Sample size: 12,404
- 113 features (before creating dummy variables)

## Methods
**Target Variable:** The target outcome that we are predicting is arrest. For the sake of model development, we grouped arrest and summons issued into one outcome arrest given the low numbers of summons issued.

**Sample Description:** High-level descriptive analysis of all 2016 Stop, Question, and Frisk incidents

**Model Development:**
- Statistical Analysis: Analysis to determine statistical significance of all features. This method was used to trim down the feature set to a more interpretable number of features 
- Classification model development and training:
- 14 different iterations of logistic regression and decision tree models
- Model performance metrics and model selection
- Exploration of feature importance:  26 features found to be most “important”

## Sample Description
**Black and Hispanic individuals make up the majority of 2016 SQF incidents**

