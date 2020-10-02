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

![download](https://user-images.githubusercontent.com/64563191/94903532-f2685b00-0467-11eb-8a31-0b863336408e.png)

**More than 90 percent of incidents in 2016 involved males**

![download-1](https://user-images.githubusercontent.com/64563191/94903843-67d42b80-0468-11eb-9a80-317973b90d4c.png)

**The average suspect in SQF incidents is 28 years old**

![download-4](https://user-images.githubusercontent.com/64563191/94903847-67d42b80-0468-11eb-944f-c68a9c9472aa.png)

**Roughly 75 percent of SQF incidents resulted in neither an arrest or issuance of a summons**

![download-3](https://user-images.githubusercontent.com/64563191/94903846-67d42b80-0468-11eb-8e45-6c544a140c09.png)

## Model Development
**Statistical Analysis:**
- Difference of two means t-test to compare the means of arrested vs not arrested for continuous variables (e.g., age, weight)
- Difference of 2 proportions Z test to compare the percentages of positive cases for each  feature (e.g., comparing the percentage of individuals carrying a weapon in the arrested group vs the not arrested group)
- Insignificant features (p>0.05) were pruned from later models to facilitate model interpretability

**Classification Models:**
- Logistic Regression and Decision Tree models were tested for this analysis given their high level of interpretability for classification problems
- GridSearchCV was used to tune hyperparameters for both Logistic Regression and Decision Tree Models
- Recursive Feature Elimination was used to select the most important features from Logistic Regression Models

**Model Performance:**


![download-5](https://user-images.githubusercontent.com/64563191/94903848-67d42b80-0468-11eb-8555-b4360d3abd3a.png)
![download-6](https://user-images.githubusercontent.com/64563191/94903849-686cc200-0468-11eb-8498-66a879d901d8.png)
![download-7](https://user-images.githubusercontent.com/64563191/94903850-686cc200-0468-11eb-9ed8-fc77d48748a8.png)
![download-8](https://user-images.githubusercontent.com/64563191/94903851-686cc200-0468-11eb-9f1c-4837f0052729.png)
![download-9](https://user-images.githubusercontent.com/64563191/94903852-686cc200-0468-11eb-8c5d-f155542fd868.png)
![download-10](https://user-images.githubusercontent.com/64563191/94903853-69055880-0468-11eb-970d-d83dc693a7c4.png)
![download-11](https://user-images.githubusercontent.com/64563191/94903854-69055880-0468-11eb-8830-68a35b960481.png)
![download-12](https://user-images.githubusercontent.com/64563191/94903855-69055880-0468-11eb-85d4-835f8701802f.png)
![download-13](https://user-images.githubusercontent.com/64563191/94903856-69055880-0468-11eb-8833-3657590708f7.png)
