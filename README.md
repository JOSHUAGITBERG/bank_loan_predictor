Business Problem:

The bank of Portugal collected data on forty four previous marketing campaigns, which have yielded mixed results.  The team would like to leverage the data from generated during the campaigns to generate profiles of future customers most likely to consign a loan so that they can maximize customer loan sales.

Data Activities:

Historical data shows that 11% of customer accepted a bank loan (referred to as the “conversion rate” in our model).  This data point will serve as the criterion for our models.
The data collected includes 45k records of sixteen features and a yes/no indicator as to  whether the customer agreed to take a loan from the bank.  Full information on the features can be found in the “Attribute Information” section of this link.
Eleven of the attributes required conversion to a numerical type, including whether or not a loan was sold to a client (column ‘y’).   

Methodology:

Prepare and compare the performance of four logistic regression models
Identify the most important features in the models, which can be used to build high value cohorts
Build cohorts and compare predicted conversion rates for each.  The highest scoring cohorts will drive our recommendations to the marketing team

Models:

We produced six models, which scored just below 70% precision.  While 70% may be low
In another context, it serves us well here given that our starting point was effectively 11%.

Regression Models:
Decision Tree
Logistic Regression
KNearest Neighbor
SVC default (radial basis kernel function)
SVC with linear regression kernel function
SVC with polynomial kernel function 

![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Model_Scores.jpg)

From the models we extracted feature weights, which compare the relative influence of each feature on the model.  The results are shown for three of the six models below.  

Features:

Features to Pursue:
Duration
All models agree that duration is the strongest indicator
Poutcome-
Previous outcome was the second highest score by SVC, the best performing model
Housing
Housing scored highly for both linear regression and SVC
Balance
Balance was the second highest indicator for decision tree


Features to Disregard:
Although contact scored highly, it effectively a proxy for previous outcome (‘poutcome’)
Pdays also scored highly in the models, but is also a proxy for poutcome
Campaign also scored highly, but we do not have information on the campaigns we can use in our analysis

![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Relative_Feature_Importance.png) 


Categorical Features:

     We did not include jobs information in our regression models because they are not numerical.  However, if we calculate the conversion rate per job function and compare it to the other features, we see that the student cohor conversion rate scores as the second strongest 
feature. 

![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Conversion_By_Job.jpg)  


Finally we calculated conversion rate for a long list of cohorts, isolated and blended, from which we determined the recommendations in the summary.  The full list is below:


Large Balance
Customers with a balance over $1300
Housing
Customer who do not already have a housing loan
Student
Students
Repeat Customers
Customers who previously took a loan
Duration
Customers who have been in the system more than 220 days

![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Conversion_By_Cohort.jpg)

![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Blended_Relative_Feature_Importance.png)


Appendix:

The workbook used to build the models and the charts above can be found at [this link](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/bank_load_predictor_workbook.ipynb)


