
**Business Problem:**

The bank of Portugal collected data on forty four marketing campaigns aimed at signing existing account holders a term deposit.  Previous campaigns averaged a conversion rate of 11%.  The bank would like to leverage data collected during the campaigns to target customers in future campaigns in order to optimize marketing resources and increase the conversion rate.

**Recommendations:**


Based on the data models discussed below, we recommend that sales executives target the following customers:

- Repeat customers
     -  Customers who previously took a loan are 6x more likely to sign up for a term deposit
-  Long Duration
     -  Customers who have been with the bank over 220 days are 5.5x more likely to sign up han customers with a shorter duration
-  Students and retirees
     -  Students and retirees are 2.5x more likely than other jobs to sign a loan
-  Renters
     -  Renters are 2x more likely to sign up than homeowners
-  Large Balance
     -  Customers with a minimum balance of $1300 are 1.5x more likely to sign up


**Data Description:**

- The original dataset contains the following 16 features:
     -  Age of the customer
     -  Customer occupation
     -  Marital Status
     -  Highest level of education
     -  Whether the customer was in default
     -  Customer Account Balance
     -  Whether the customer owns their house
     -  Whether they currently have a loan
     -  Whether the customer was previously contacted
     -  Date of last contact
     -  Month of last contact
     -  Duration they have held their account
     -  Number of days since their last contact
     -  Number of previous contacts
     -  Outcome of previous contacts
Whether a client signed up for a term deposit

 Full descriptions of the features can be found in the “Attribute Information” section of this [link](https://archive.ics.uci.edu/dataset/222/bank+marketing)

**Data Preparation:**

-  Eleven of the sixteen attributes required conversion to a numerical type, including whether or not a loan was sold to a client (column ‘y’)

-  Historical data shows that 11% of customers accepted a bank loan (referred to as the “conversion rate” in our model).  This data point will serve as the criterion for our models.

-  Categorical feature “job” was excluded from the models. However, we were able to analyze conversion rates per occupation to determine that it would score as the third most important relative to the features identified by the models.  

-  The data collected includes 45k records with no nulls or duplicates

**Methodology:**

-  Scale the data and fit the data to four logistic regression models- Knearest Neighbor, Logistic Regression, Decision Tree and SVC.  We tested rbf, linear and polynomial SVC kernels.
-  Identify the most important features in the models
-  Use the highest weighted features to build potentially high value cohorts
-  Calculate conversion rate for each cohort.  This data was the basis for recommendations above. 

**Models:**

We produced six models, which scored just below 70% precision.  While 70% may be low
In another context, it serves us well here given that our initial conversion rate is effectively 11%.

Regression Models:
-  Decision Tree
-  Logistic Regression
-  KNearest Neighbor
-  SVC default (radial basis kernel function)
-  SVC with linear regression kernel function
-  SVC with polynomial kernel function 

![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Model_Scores.jpg)

From the models we extracted feature weights, which compare the relative influence of each feature on the model.  The results are shown for three of the six models below.  

**Features:**

Features to Pursue:
-  Duration
     -  All models agree that duration is the strongest indicator
-  Previous outcome (i.e. existing customers)
     -  Previous outcome was the second highest score by SVC, the best performing model
- Occupation
     -  Occupation (or ‘job’) was manually calculated and scored 
-  Housing
     -  Housing scored highly for both logistic regression and SVC
-  Balance
     -  Balance was the second highest indicator for decision tree

Features to Disregard:
-  Although contact scored highly, it effectively a proxy for previous outcome (‘poutcome’)
-  Pdays also scored highly in the models, but is also a proxy for poutcome
-  Campaign also scored highly, but we do not have sufficient information to focus on campaign details

![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Relative_Feature_Importance.jpg) 

Categorical Features:

We did not include jobs information in our regression models because they are not numerical. 
However, if we calculate the conversion rate per job function and compare it to the other
features, we see that the student cohort conversion rate scores as the second strongest raw (non-blended) cohort. 

![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Conversion_By_Job.jpg)  

Finally we calculated conversion rate for a long list of cohorts, isolated and blended, from which we determined the recommendations in the summary.  The full list is below:


-  Large Balance
     -  Customers with a balance over $1300
-  Housing
     -  Customer who do not already have a housing loan
-  Students and retirees 
-  Repeat Customers
     -  Customers who previously took a loan
-  Duration
     -  Customers who have been in the system more than 220 days

![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Conversion_By_Cohort.jpg)

![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Conversion_By_Blended_Cohort.jpg)


Appendix:

The workbook used to build the models and the charts above can be found at [this link](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/bank_load_predictor_workbook.ipynb)


