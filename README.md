Business Problem:

     Our bank would like to optimize its marketing dollars.  The marketing team has completed forty four campaigns, which have yielded mixed results.  Fortunately, the team kept records of their efforts. This project will analyze the data generated by previous campaigns to generate a profile of customer most likely to engage in a loan.  

Data Understanding:

     The data collected includes 45k records of sixteen features in addition to whether the customer agreed to take a loan.  We will discuss the more useful features in our evaluation.  Full information on the features can be found in the “Attribute Information” section of this link.

     Note that the data is imbalanced, with 89% of the customers failing to take out a loan.  We found that the models performed well enough on the original dataset that we did not need to leverage SMOTE or oversampling to address the issue. For example, our SVC regression model yielded a 63% recall score.  This means we would expect a 63% sign up rate for targeted customers, versus the 11% you expect from a random sampling.

     Otherwise, the data was relatively clean, with no duplicated  or null values in the initial dataset. 

Data Preparation:

Eleven of the attributes required conversion to a numerical type, including whether or not a loan was sold to a client (column ‘y’).   

Modeling Evaluation:

     As an exercise, we generated four different regression models.  We optimized parameters for two of the models, and compared the relative recall scores for each.  Recall was used as the determining factor because we want to preserve every loan opportunity.  

![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Model_Scores.jpg)

Once we were able to compare models, we identified the more important  features from each model, and used those to generate cohorts more likely to sign up for a loan.  

![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Relative_Feature_Importance.png)

By reducing the target customer base to those which exhibit important features, we were able to raise our recall score to over 80%.  
![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Conversion_By_Cohort.jpg)

We can see the impact of the identified features if we group customers into cohorts and measure the percent of customers that took out a loan (“conversion rate”).  For example, we have charted the conversion rate based on occupation in the chart below:

![alt text](https://github.com/JOSHUAGITBERG/bank_loan_predictor/blob/main/images/Conversion_By_Job.jpg)

We can also stack the respective groups to improve recall.  For example when we stack the top three feature cohorts, which consist of  long standing student customers who have a load already, we can increase the change of reaching a customer from 11% to over 80%.  All cohort information is shown in the chart below:

![alt text](http://url/to/img.png)
<link to cohort chart> 

Appendix:

The workbook used to build the models and the charts above can be found at this link:

<pyb link>


