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

<img width="1446" alt="Screen Shot 2020-10-01 at 10 23 44 PM" src="https://user-images.githubusercontent.com/64563191/94905081-4b38f300-046a-11eb-824c-8214fd6bf0ba.png">

Model 11 was chosen due to best performance with minimum number of features. This model was a grid search decision tree model. I arrived at 24 features by conducting recursive feature elimination with a logistic regression model and then running an earlier iteration of the decision tree grid search model. I then selected the top 15 features from this model and combined them with the 15 from the RFECV logistic regression model. I inserted these features into this grid search decision tree model for optimal performance.

Twenty-nine features were found to be most predictive of an arrest. They are grouped below into a few  themes in no particular order:
- Physical characteristics: Age and weight were among the strongest predictors of arrest.
- Police Use-of-Force: Officers tend to use force in instances where they are going to arrest an individual. Force is often used in response to resistance (in most cases).
- Ongoing investigation: Whether the suspect was already being surveilled for involvement in a previous crime or if they fit a description of someone who committed a crime.
- Geography: Three precincts (13, 52, and 61) were among the strongest predictors of arrest. It’s likely that racial and socioeconomic factors are tied to these precincts as well.
- Searched: Whether a suspect was searched and if any contraband was found on their body.
- Suspicion of Particular Crimes:  Four criminal acts were strong predictors of arrest - theft of services, Trespassing, Criminal Possession of a Weapon, and Petit Larceny

**Age appears similarly distributed for individuals arrested and not arrested - the difference is statistically significant**

![download-7](https://user-images.githubusercontent.com/64563191/94903850-686cc200-0468-11eb-9ed8-fc77d48748a8.png)

**Among all individuals in SQF cases, the most common police use of force is applying handcuffs**

![download-9](https://user-images.githubusercontent.com/64563191/94903852-686cc200-0468-11eb-8c5d-f155542fd868.png)

**Among suspects in ongoing investigations, roughly 20% - 25% of individuals are arrested**

![download-8](https://user-images.githubusercontent.com/64563191/94903851-686cc200-0468-11eb-9f1c-4837f0052729.png)

**Precincts 13, 52, and 61 were identified as strong predictors of arrest, but only precinct 13 makes the top 30 for total arrests in 2016**

![download-12](https://user-images.githubusercontent.com/64563191/94903855-69055880-0468-11eb-85d4-835f8701802f.png)

- Precinct 13: Serving a southern portion of Midtown, Manhattan. The precinct features the Peter Cooper Village/Stuyvesant Town residential complex, Gramercy Park, the lower portion of Rosehill, Madison Square Park, and Union Square Park.
- Precinct 52: Serving a northern portion of the Bronx. The precinct is home to Bedford Park, Fordham, Kingsbridge, Norwood, Bronx Park, and University Heights.
- Precinct 61: Serving a southern portion of Brooklyn and encompasses Kings Bay, Gravesend, Sheepshead Bay, and Manhattan Beach.

**Whether someone is searched is a strong predictor of arrest**

![download-10](https://user-images.githubusercontent.com/64563191/94903853-69055880-0468-11eb-970d-d83dc693a7c4.png)

**Admission by suspect results in the highest likelihood of arrest from a search**

![download-13](https://user-images.githubusercontent.com/64563191/94903856-69055880-0468-11eb-8833-3657590708f7.png)

**Possession of a weapon is a very strong predictor of arrest**

![download-6](https://user-images.githubusercontent.com/64563191/94903849-686cc200-0468-11eb-8498-66a879d901d8.png)

**Each of the features below make the list for optimal feature importance, but criminal trespass and theft of services result in the highest likelihood of arrest**




![download-11](https://user-images.githubusercontent.com/64563191/94903854-69055880-0468-11eb-8830-68a35b960481.png)


![download-5](https://user-images.githubusercontent.com/64563191/94903848-67d42b80-0468-11eb-8555-b4360d3abd3a.png)
![download-6](https://user-images.githubusercontent.com/64563191/94903849-686cc200-0468-11eb-8498-66a879d901d8.png)
![download-9](https://user-images.githubusercontent.com/64563191/94903852-686cc200-0468-11eb-8c5d-f155542fd868.png)

![download-12](https://user-images.githubusercontent.com/64563191/94903855-69055880-0468-11eb-85d4-835f8701802f.png)

