# Predicting Diamond Prices

## Project Overview

A jewelry company wants to put in a bid to purchase a large set of diamonds but is unsure how much it should bid. They want a 30% margin so they can make a profit when they resell the diamonds. In this project, we will use the results from a predictive model that was built based on the diamond attributes to make recommendation on how much the jewelry company should bid.

## Understanding the Model

- According to the model, if a diamond is 1 carat heavier than another with the same cut, how much more should I expect to pay? Why? 

   * From our regression model, we created a formula that determined the coefficient for carat (diamond weight), which is 8413. So, that means for every increase in the weight of diamond the price will increase by the amount of the coefficient. Therefore, one additional carat would result in an additional $8,413 in price 

* If you were interested in a 1.5 carat diamond with a Very Good cut (represented by a 3 in the model) and a VS2 clarity rating (represented by a 5 in the model), how much would the model predict you should pay for it? 

   - The formula is price = -5269 + 8413 * Carat + 158.1 * Cut + 454 * Clarity 

   * so now we will plug in the values for the different variables.  

   + price = -5269 + 413 * 1.5 + 158.1 * 3 + 454 * 5 

   - price = $10,094.80 

## Visualize the Data  

- Plot 1 - Plot the data for the diamonds in the database, with carat on the x-axis and price on the y-axis.  

* Plot 2 - Plot the data for the diamonds for which you are predicting prices with carat on the x-axis and predicted price on the y-axis. 

   + Note: You can also plot both sets of data on the same chart in different colors. 

+ What strikes you about this comparison? After seeing this plot, do you feel confident in the model’s ability to predict prices? 
