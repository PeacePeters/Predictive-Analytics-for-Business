# Create an Analytical Dataset
## Business and Data Understanding 
### The Business Problem  
Pawdacity is a leading pet store chain in Wyoming with 13 stores throughout the state. This year, Pawdacity would like to expand and open a 14th store. As such, the analytical team have been tasked to perform an analysis to recommend the city for Pawdacity’s newest store, based on predicted yearly sales.   
### Key Decisions  
Being a part of the analytical team, we are to assist management decide which city to situate Pawdacity’s newest store by predicting the yearly sales. The critical information that needs to be known is the predicted yearly sales of cities whose past sales data are known. To decide the location of Pawdacity’s 14th store, we will apply predictive analysis to help obtain the data to inform the decision. This is done by creating an analytical dataset that would be used to build a regression model. As business analysts, we have been asked to prepare the data for modelling.  

### Data Understanding 

To build our analytical dataset used for predicting yearly sales, we need data on existing stores sales as well as demographic information associated with these existing stores such as household income, age distribution, education, race, and population density to see whether there are any demographic variables that can drive our existing store sales. These variables are critical in building a model that predicts sales for the new store, particularly total population and population density which could be useful as denser areas would have more customers. 

Also, number of families and families with individuals under 18 are important demographic information that would allow us to detect areas with more potential customers. In addition to demographic variables, we could also seek out the traffic drivers to our current stores to understand what are the other landmarks or businesses that can drive foot traffic to the store. Understanding how far competitors’ stores are from the company’s stores can help model any traffic drivers as well. 

Competitor sales could also be relevant to understand if there is significant customer demand in the city. It would also be helpful to see if competition might pose a risk in case Pawdacity decides to open a store there. 

Finally, we could gather data relative to our current local promotions and marketing budget spent per city on the current stores. We can also try to get information on the expected marketing funds the company will spend to promote the new store. 

The data needed to create our dataset is in three different csv files. We need to make the data digestible for our analytic model by cleaning, formatting, and blending it. The files include:  
1. <i>p2-2010-pawdacity-monthly-sales.csv</i> - contains all of the monthly sales for all Pawdacity stores for 2010. 
2. <i>p2-wy-demographic-data.csv</i> - contains demographic data for each city and county in Wyoming. 
3. <i>p2-partially-parsed-wy-web-scrape.csv</i> - is a partially parsed data file that can be used for population numbers. 

## Building the Training Set 
The major steps involve in building the training set are as follow: 
 
### Data Structure                                                                                                                  
Looking at ```p2-2010-pawdacity-monthly-sales.csv```, it is a structured data with monthly sales for Pawdacity stores located in cities across Wyoming. The data will have to be transformed before it can be merged with other data.

![dt1](https://user-images.githubusercontent.com/68206315/119833432-04b36f80-bef7-11eb-982c-891cb58ede63.png)

```p2-wy-demographic-data.csv``` is also a structured data with four numerical fields like Land Area, Population density, etc. and two categorical field – City & County 

 ![dt2](https://user-images.githubusercontent.com/68206315/119833734-42b09380-bef7-11eb-9c9a-5ed44c8d93f3.png)

```p2-partially-parsed-wy-web-scrape.csv``` is a file containing an incomplete parsed data from which the 2010 census population data can be extracted and used for analysis. 

![dt](https://user-images.githubusercontent.com/68206315/119833893-6542ac80-bef7-11eb-8930-380f1649ae0c.png)

## Data Formatting 
* First, we’ll have to transform the Pawdacity sales dataset using Transform tool.

<img width="685" alt="Screenshot 2021-05-27 at 14 18 24" src="https://user-images.githubusercontent.com/68206315/119834669-11849300-bef8-11eb-9f03-7a9ce2636b99.png">

* Then we’ll use the summarize tool to aggregate the yearly sales for each city. 
* And lastly, we will rename the field using Select tool Next  

Transformed dataset with yearly sales values
![ss1](https://user-images.githubusercontent.com/68206315/119835221-8ce64480-bef8-11eb-9d3c-8c76ae10a48c.png)
