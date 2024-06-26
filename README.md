# Telco-Customer-Churn
Telco Customer Churn Analysis and Prediction
In this personal project I analyzed a Telco Customer Churn dataset from Kaggle [datasets/blastchar/telco-customer-churn]. 
## First approach in predictive modeling
I made three quick initial predictive models that could give predictions whether a customer might churn depending on their current condition, based on the follow variables:
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

### Predictive Models created
1. Logistic Regression
2. Decision Tree Algorithm
3. Random Forest Algorithm

![image](https://github.com/arceldizon28/Telco-Customer-Churn/assets/148745972/ca029232-8574-47f9-92ff-90f595e6aef7)
  
Logistic Regression Predictive Model performed the best at 74% accuracy. Random Forest algorithm coming in at 72%, and Decision Tree at only 69%.

### Variables significant to Churn
I did chi square test on the categorical variables. Below are the categorical variables in decreasing order of significance to Churn:
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

## Second approach to predictive modeling
For the second approach, I performed further data cleaning and transformation. I implemented one-hot encoding on the categorical variables and did min-max feature scaling normalization on the numerical variables. I also checked for mutlicollinearity where I discovered the following pairs with high correlation.
- tenure & total charges
- monthly charges & has internet service
- monthly charges & fiber optic internet
- monthly charges & total charges
- monthly charges & has streaming tv & has streaming movies
- fiber optic internet & dsl internet  
I also measured the correlation of each predictor variable to the target variable churn:
- tenure @ -0.35
- electronic check payment method @ 0.3
- two year contract @ -0.3
- fiber optic internet @ 0.3
- has internet service @ 0.23

Despite the low correlation, it does not mean these do not have an effect, but that the effect is either weak or their relation to the churn is not linear which correlation analysis cannot detect.
There are other ways to discover the importance of predictor variables to the target variable churn, such as looking at the variance. Below are the top 3 and bottom 3 variables in variance.
- IsMale
- HasPartner
- Fiber_optic_Internet
- MonthlyCharges
- HasPhoneService
- TotalCharges

IsMale had a very low correlation but had high variance on its values. This means that despite the low predictive power, it can cover a wider range of data compared to tenure having high correlation but low variance. There seems to be a tradeoff between correlation and variance in the data.

### logistice regression models created
1. standard
2. standard (dropped variables with multicollinearity: monthly charges, total charges, has phone service) 
3. Lasso penalized

all three performed quite the same and gave accuracy scores of ~74-75% out of the three approaches, but the lasso penalized logistic regression model was more successful in feature reduction than the correlation and variance elimination approach. The lasso regression alpha value is 0.01. Below are the final variables and their respective coefficients.
- tenure: -1.443
- HasInternetService: 0.299
- HasPaperlessBilling: 0.127
- Fiber_optic_Internet: 0.850
- One_year_Contract: -0.209
- Two_year_Contract: -0.755
- Electronic_check_PaymentMethod: 0.414
- intercept: -0.267

### Interpretation
Using the lasso penalized logistic regression was the most successful way done to create a predictive model that could aid in estimating a customer's probability to churn. The variables remained from the penalized predictive model are:
1. Tenureship: the longer a customer has been using the services of the telco company, the lesser the probability to churn. Those customers most likely enjoy the current promo, discounts, or offers that they opted for, if any, and see the services as perfect for their use case.
2. Having Internet Service: customers who availed for the internet service in general has a slight increase in probability to churn.
3. Paperless Billing: contributes a little to the increase in churn probability
4. Fiber Optic Internet: is a significant factor that increases the probability to churn. The disadvantages of using a fiber optic internet may have outweighed the benefits of it. Fiber optic internet costs more and is prone to physical damage. This combination of problem may lead to customers not seeing the worth of the incredible speed because of the cost. It could also be seen in the correlation matrix that fiber optic internet is positively correlated to monthly charges, which is also slightly positively correlated to the churn.
5. One year contract: customers who commit to longer contracts could mean that they are willing to use the telco's services for a longer time hence can be attributed to lower probability to churn
6. Two year contract: similar to one year contract but has a higher influencing power
7. Electronic check payment method: there is a slight increase in churn probability for customers who opt for electronic check payment method. This could be due to inefficiencies in the payment method in the software's design, bank's processes, insufficient knowledge in doing electric payment or any other reason that cannot be inferred from the data alone. There aren't any clear insights I could extract from this variable because it is not correlated to all of variables in the dataset

### Recommendations
1. Tenure is slightly correlated to a mix of variables including: partner status, mailed check, online security and backup, device protection, and tech support. These quality-of-life improvements help the customers retain their loyalty to the telco. A maintained high quality of those mentioned can indirectly contribute to increase in tenure which leads to lower churn rate.
2. Longer contracts helps reduce a customer's probability to churn. Offering long contracts with a better deal may help increase the amount of customers who opt for a longer contract
3. Fiber optic internet seems to cause an increase in churn probability due to cost. It is highly correlated to monthly charges but not to total charges. Implementing discounts to fiber optic internet may make customers consider continuing using the service.
4. Explore and gather more data about the experiences of customers when using electronic payment method. It is one of the factors with high correlation but I cannot seem to find the reason.


