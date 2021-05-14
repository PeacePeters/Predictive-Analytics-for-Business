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

For our analysis, we have been provided with clean data which has all the required information required to the prediction. There two datasets:
1. [p1-customers](https://github.com/PeacePeters/Predictive-Analytics-for-Business/blob/main/catalog-demand-prediction/dataset/p1-customers.xlsx) - contains data on about 2,300 customers and it is used to build the model
2. [p1-mailinglist](https://github.com/PeacePeters/Predictive-Analytics-for-Business/blob/main/catalog-demand-prediction/dataset/p1-mailinglist.xlsx) - contains data on 250 new customers that we need to predict sales. We use this dataset to estimate how much revenue the company can expect if they send out the catalog.

Additional information provided are:

▫ The costs of printing and distributing is $6.50 per catalog.

▫ The average gross margin (price-cost) on all products sold through the catalog is 50%.

Looking at the data available in p1-customers.xlsx, we can see we have past data on Avg_Sales_Amount which is the average sales amount generated in the last catalog sent. Since we are predicting sales in order to get our expected profit, our target variable is Avg_Sales_Amount and it is a continuous numeric variable. Therefore, we will apply a Linear Regression model to solve our problem.
In examining our data for better understanding, we can see that the information of each customer on <i>Customer_Segment</i>,<i> City</i>, Avg_Num_Products_Purchased & X_Years_as_Customer are likely the important factors in predicting the sales amount. Therefore, these are the potential predictor variables for our analysis.

### Analysis, Modeling, and Validation

From our business and data understanding, we determined that we need to predict our target variable Avg_Sales_Amount using these critical predictor variables - Customer_Segment, City, Avg_Num_Products_Purchased & X_Years_as_Customer. Other variables are not logically and statistically significant in making prediction.
To set up the multiple linear regression model, we first test the numeric predictor variables using scatter plot to understand their relationship with the target variable.

Scatter plot of <i>Avg_Num_Products_Purchased</i> versus <i>Avg_Sales_Amount</i>

As shown above, we can see that as the Avg_Num_Products_Purchased increases, the Avg_Sales_Amount increases too at an approximate linear fashion. The trend line which is sloped shows that the predictor variable: Avg_Num_Products_Purchased is a good potential predictor variable to use to create our multiple linear regression model. Also, from the graph of X_Years_as_Customer vs Avg_Sales_Amount, the trend line is flat indicating there is no relationship between the between the predictor and target variable.
