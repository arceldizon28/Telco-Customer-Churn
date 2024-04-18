# Telco-Customer-Churn
Telco Customer Churn Analysis and Prediction
In this personal project I analyzed a Telco Customer Churn dataset from Kaggle. I also quickly made three predictive models that could give predictions whether a customer might churn depending on their current condition, based on the follow variables:
- gender
- is a senior citizen
- has partner
- has dependents
- tenure
- has phone service
- has multiple lines
- has internet service
- has online security
- has online backup
- has device protection
- receives tech support
- streams tv shows
- streams movies
- contract type
- opted for paperless billing
- payment method
- monthly charges
- total charges  

### Class imbalance problem
There were significantly less churning customers compared to customers staying. To create the predictive models, I undersamples the majority class and left some based on the amount of the minority class.

### Predictive Models created
1. Logistic Regression
2. Decision Tree Algorithm
3. Random Forest Algorithm

![image](https://github.com/arceldizon28/Telco-Customer-Churn/assets/148745972/ca029232-8574-47f9-92ff-90f595e6aef7)
  
Logistic Regression Predictive Model performed the best at 74% accuracy. Random Forest algorithm coming in at 72%, and Decision Tree at only 69%.

### Variables significant to Churn
Since the variables are categorical, I implemented chi square test. Below are the categorical variables in decreasing order of significance to Churn:
1. contract
2. online security
3. tech support
4. internet service
5. payment method
6. online back up
7. device protection
8. streaming movies
9. streaming tv
10. paperless billing
11. dependents
12. senior citizen
13. partner
14. multiple lines
15. phone service
16. gender

The effects of the significance can be seen by filtering through variables via interactive visualization in the PowerBI dashboard I made. In there, the contract type variable's strong significance to Churn is demonstrated: month-to-month has a churn of 42.71%, one year has a churn of 11.27%, and two year has a churn of 2.83%, suggesting that implementing a two year term contract can lessen the churn rate of customers.
It can also be seen in the gender variable which has the lowest significance to Churn, that difference in gender only accounted for 0.76% change in churn rate, female:26.92% male:26.16%.

I would interpret the top 10 most significant variables from the analysis as the 10 most important factors for the customers when considering their loyalty to the Telco company's services.

### Dashboard static images (pbix file in folder)
![image](https://github.com/arceldizon28/Telco-Customer-Churn/assets/148745972/3d871434-57ad-49e7-9bb5-82724e57502e)
![image](https://github.com/arceldizon28/Telco-Customer-Churn/assets/148745972/eb16b411-969c-4795-b110-fbf647c78c2d)
![image](https://github.com/arceldizon28/Telco-Customer-Churn/assets/148745972/5daf9e3d-3395-4ab4-925e-dbbe6be06f09)
![image](https://github.com/arceldizon28/Telco-Customer-Churn/assets/148745972/90c833e0-51b1-4c16-b33c-eccc7b41b826)



