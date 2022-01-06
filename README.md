# Project 2: Ames Housing Saleprice Prediction

---

## Problem Statement

A leading American online real estate marketplace company that specializes in using simple models to predict house prices based on a few different aggregated data sources, has created a website that provides both home-buyers and home-sellers more transparency about the market and a tangible baseline to evaluate offers against. 

The CEO had an idea to use the estimates that they were generating to buy houses at undermarket value, flip them and thereafter sell them for a profit on their website as another business model for the company. However, the existing estimates currently in used were initially designed to be only baseline estimates (i.e the starting point for a conversation about home values between buyers and sellers) and its algorithms were not meant to be a comprehensive model for predicting 'true' housing sale prices.

The CEO has instructed the in-house data team to begin creating a model that can identify undervalued properties as accurately as possible, and with the lowest Root Mean Square Error (RMSE). The team could begin building the model based on a comprehensive database already collected by the company on the houses in Ames, Iowa, and subsequently improve from there. 

Management would also like this new model to address certain business concerns that they may have when buying undervalued houses and flipping them:

- Which features appear to add the most value to a home?
- What are the things that homeowners could improve in their homes to increase the value?
- What neighborhoods seem like they might be a good investment?
- Do the team feel that this model will generalize to other cities? How could the team revise the model to make it more universal?

## Summary of Analysis
---

For our prediction model, we had used lasso regression as it had the best predictive performance (lowest RMSE) on housing price in Ames, Iowa, USA. The production model had a final total of 28 independent variables after applying feature selection, feature engineering and automated feature selection (namely: Recusive Feature Elimination and Lasso Regression). Although decreasing to 28 features, there had been a slight tradeoff between interpretability and accuracy of our prediction model. However, the benefits outweigh the costs and we will accept the tradeoffs.

![](/pictures/coefficient.png)

The coefficients of our production model (lasso regression model) had also indicated that **area** and **quality** of the house in general seems to be the biggest contributor to value of housing. Hence, a per unit increase in area of the house would cause a much greater percentage increase in the house price compare to other features. This is the same for quality / condition of the house, in which the better the quality / material used, the house price would increase to a greater extent as compared to other features.


## Conclusion and Recommendations
---

Based on our model, our company looking to flip undervalued houses and sell them for a profit could focus on the following during the renovation (i.e. flipping) process:

- Improve the overall quality of material and finish of the house
- Improve the overall condition of the house ( e.g. repainting and upkeeping )
- The foundation of the house should be 'Poured Concrete'
- Improve the basement finished area ( * do not let it go unfinished )
- Renovate the garage if it is in bad condition ( * add a garage if there isn't one )
- Add a paved driveway
- Add a fireplace
- Invest in housing specifically from Stone Brook, Northridge Heights and Northridge

<u>Applicability of our model:<u/>
    
![](../pictures/coefficient.png)
![](../pictures/general_trend.png)

The city of Ames do display trends that are in line with the majority of the cities. One example is the trend of housing prices even during the subprime mortgage crisis of 2008. However, one point to keep in mind that the last date recorded was in 2010 and there are not enough recent data to determine that Ames saleprice trend is still the same as the general US cities trend due to various factors such as housing policy changes, recession economy and COVID'19. Hence, the team do feel that this model may be applicable to a certain extent when using on other cities in the United States 

In order to revise the model to make it more universal, the simplest say would be to collect more recent data (2011-2021), preferably from other cities as well such as Los Angeles and New York, and create a model with a time period of 2000 - 2021. More universal features could also be added into the new data such as 'high rise buildings', 'elevators' and 'centralise carparks'.

## Data Dictionary
---

|Feature|Description|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
|---|---|
