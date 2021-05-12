# Predicting Catalog Demand

## Business and Data Understanding

### The Business Problem

A company that manufactures and sells high-end home goods is preparing to send out this year's catalog to 250 new customers in the coming months. Management does not want to send out these catalogs unless the expected profit contribution exceeds $10,000. As such, the manager needs to know how much profit the company can expect from sending out a catalog to these customers.

### Key Decisions

Being a part of the analytical team tasked to predict the expected revenue, we are to assist management decide whether to send the catalog to these new customers or not. The critical information that needs to be known is the expected profit if catalog is sent and if this profit exceeds the required threshold. Unfortunately, this information is not known at the time decision needs to be made. So the potential profit from these 250 new customers need to be predictive. Therefore, we will applied predictive analysis to help obtain the data to inform the decision. This expected profit can be obtained through the following steps:

Building a model using last year mail-order catalog business data to predict the expected sales amount.
• Next is calculating the potential revenue of each new customer by multiplying the predicted sale amount with the probability that the customer will respond to the catalog and make a purchase.
• Finally, multiplying the aggregate by gross margin and then deducting the catalog printing cost for all customers to obtained the expected profit.
