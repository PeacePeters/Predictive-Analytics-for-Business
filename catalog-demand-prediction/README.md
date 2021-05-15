# Predicting Catalog Demand

## Business and Data Understanding

### The Business Problem

A company that manufactures and sells high-end home goods is preparing to send out this year's catalog to 250 new customers in the coming months. Management does not want to send out these catalogs unless the expected profit contribution exceeds $10,000. As such, the manager needs to know how much profit the company can expect from sending out a catalog to these customers.

### Key Decisions

Being a part of the analytical team tasked to predict the expected revenue, we are to assist management decide whether to send the catalog to these new customers or not. The critical information that needs to be known is the expected profit if catalog is sent and if this profit exceeds the required threshold. Unfortunately, this information is not known at the time decision needs to be made. So the potential profit from these 250 new customers need to be predictive. Therefore, we will applied predictive analysis to help obtain the data to inform the decision. This expected profit can be obtained through the following steps:

* Building a model using last year mail-order catalog business data to predict the expected sales amount.
* Next is calculating the potential revenue of each new customer by multiplying the predicted sale amount with the probability that the customer will respond to the catalog and make a purchase.
* Finally, multiplying the aggregate by gross margin and then deducting the catalog printing cost for all customers to obtained the expected profit.

### Data Understanding

For our analysis, we have been provided with clean data which has all the required information required to make prediction. There two datasets:
1. [p1-customers](https://github.com/PeacePeters/Predictive-Analytics-for-Business/blob/main/catalog-demand-prediction/dataset/p1-customers.xlsx) - contains data on about 2,300 customers and it is used to build the model
2. [p1-mailinglist](https://github.com/PeacePeters/Predictive-Analytics-for-Business/blob/main/catalog-demand-prediction/dataset/p1-mailinglist.xlsx) - contains data on 250 new customers that we need to predict sales. We use this dataset to estimate how much revenue the company can expect if they send out the catalog.

Additional information provided are:

▫ The costs of printing and distributing is $6.50 per catalog.

▫ The average gross margin (price-cost) on all products sold through the catalog is 50%.

p1-customers.xlsx
![Screenshot 2021-05-15 143729](https://user-images.githubusercontent.com/68206315/118378066-feed8e00-b5c8-11eb-879c-36cf003042bd.png)

p1-mailinglist.xlsx
![Screenshot 2021-05-15 143607](https://user-images.githubusercontent.com/68206315/118378072-0b71e680-b5c9-11eb-9a97-7fa5a9d50425.png)

Looking at the data available in p1-customers.xlsx, we can see we have past data on Avg_Sales_Amount which is the average sales amount generated in the last catalog sent. Since we are predicting sales in order to get our expected profit, our target variable is Avg_Sales_Amount and it is a continuous numeric variable. Therefore, we will apply a Linear Regression model to solve our problem.
In examining our data for better understanding, we can see that the information of each customer on <i>Customer_Segment</i>,<i> City</i>, <i>Avg_Num_Products_Purchased</i> & <i>X_Years_as_Customer</i> are likely the important factors in predicting the sales amount. Therefore, these are the potential predictor variables for our analysis.

## Analysis, Modeling, and Validation

From our business and data understanding, we determined that we need to predict our target variable ```Avg_Sales_Amount``` using these critical predictor variables ```Customer_Segment``` ```City```, ```Avg_Num_Products_Purchased``` & ```X_Years_as_Customer```. Other variables are not logically and statistically significant in making prediction.
To set up the multiple linear regression model, we first test the numeric predictor variables using scatter plot to understand their relationship with the target variable.

#### Testing Numeric variables Assumptions using Scatter Plot

Scatter plot of <i>Avg_Num_Products_Purchased</i> versus <i>Avg_Sales_Amount</i>
![Screenshot 2021-05-04 095557](https://user-images.githubusercontent.com/68206315/118359323-cd4dd600-b57a-11eb-8f90-d059d67afaf1.png)

Scatter plot of <i>X_Years_as_Customer</i> versus <i>Avg_Sales_Amount</i>
![Screenshot 2021-05-04 100021](https://user-images.githubusercontent.com/68206315/118359347-e5255a00-b57a-11eb-954f-55e139ace044.png)

As shown above, we can see that as the Avg_Num_Products_Purchased increases, the <i>Avg_Sales_Amount</i> increases too at an approximate linear fashion. The trend line which is sloped shows that the predictor variable: A<i>vg_Num_Products_Purchased</i> is a good potential predictor variable to use to create our multiple linear regression model. Also, from the graph of <i>X_Years_as_Customer</i> vs <i>Avg_Sales_Amount</i>, the trend line is flat indicating there is no relationship between the between the predictor and target variable.

For the categorical variables, we use trial and error to check which are statistically significant. This is done by running the categorical variables through the regression model and checking the P-values. P-value is the probability that the coefficient estimate (the observed result) is zero. The lower the p-value the higher the probability that a relationship exists between the predictor and target variable. If the p-value is high, we should not rely on the coefficient estimate.

Report for linear model with potential categorical variables
![CV2](https://user-images.githubusercontent.com/68206315/118378270-825baf00-b5ca-11eb-9fc1-8ced313f85e1.png)

We are looking for categorical variables with the P-values less than 0.05. From the figure above, City has a high ```P-value = 0.67246``` with no significant code. This means we should not rely on the coefficient estimate and therefore cannot be used as a predictor for our model. On the other hand, Customer_Segment is statistically significant with a very small ```P-value < 0.00000000000000022```.

Now that we have establish our good predictor variables, we run our initial model using all the potential predictor variables
![ALL_V1](https://user-images.githubusercontent.com/68206315/118378613-f26b3480-b5cc-11eb-8677-d9ea1ba3f37a.png)

Finally, we build the linear regression model using <i>Avg_Sales_Amount</i> as target variable and <i>Avg_Num_Products_Purchased</i> & <i>Customer_Segment</i> as predictor variables
![CDR](https://user-images.githubusercontent.com/68206315/118378660-2f372b80-b5cd-11eb-93c2-8eea63d37d5c.png)

For our model, we can see that both predictor variables have a P-values of ```< .00000000000000022``` which is very small! This means the relationship between the predictor variables and the target variable is statistically significant.
The <b>Adjusted R-squared</b> value is ```0.8366``` which means the model is strong, since a R-squared greater than or equal to 0.7 is considered strong. This indicate that the model has a high explanatory power. Therefore, with low P-values and a high R-squared the model is highly predictive and we can confidently predict the sales amount and perform analysis.

#### Final Project Workflow
![Workflow](https://user-images.githubusercontent.com/68206315/118378850-44f92080-b5ce-11eb-9e60-99e46904114b.png)

### Regression Equation
The best linear regression equation based on the analysis, model and validation is:

```Predicted_Average_Sales = 303.46 + -149.36 * (Loyalty Club Only) + 281.84 * (Loyalty Club and Credit Card) + -245.42 * (Store Mailing List) + 0 * (Credit Card Only) + 66.98 * (Avg_Num_Products_Purchased)```

## Presentation/Visualization
Scatter plot of actual average sales and predicted average sales versus Avg_Num_Products_Purchased
<img width="745" alt="Screenshot 2021-05-15 at 22 45 23" src="https://user-images.githubusercontent.com/68206315/118379014-71616c80-b5cf-11eb-998f-88f2a80f1004.png">

We can see that the actual average sales increases with the number of products purchased, but there’s a lot of variation among customers that bought the same number of products. This makes it less compact than the predicted average sales and that’s because we are not accounting for other predictor variables that affects the sales amount. As seen in our formula, predictor variables like customer segment accounted for some of the variation.

We recommend the company send out catalog to its 250 new customers because the expected profit exceed $10,000. We arrive at this decision through the following steps:
• Using the best linear regression equation determined above, we calculated the Predicted_Average_Sales based on the attributes of the 250 new customers.
• Next, we multiply the result by [Score_Yes] column which is the probability that the customer will respond to the catalog and make a purchase. This gives us the Expected_Revenue as shown below:
![Exp Revenue](https://user-images.githubusercontent.com/68206315/118379117-56432c80-b5d0-11eb-9ff1-11fde50761ac.png)

Next we add all the expected revenue together. This gives us an estimate of the total revenue generated from the 250 customers, which is $47,224.87
• Finally, we multiply [Sum_Expected_Revenue] by 50% gross margin, and then deducted catalog printing cost for all customers ($6.5*250) to obtain the expected profit
• The expected profit from the new catalog is $21,987.44. This is above management required threshold of $10,000



