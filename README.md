# Project 2: Ames Housing Saleprice Prediction

---

## Problem Statement

A leading American online real estate marketplace company that specializes in using simple models to predict house prices based on a few different aggregated data sources, has created a website that provides both home-buyers and home-sellers more transparency about the market and a tangible baseline to evaluate offers against. 

The CEO had an idea to use the estimates that they were generating to buy houses at undermarket value, flip them and thereafter sell them for a profit on their website as another business model for the company. However, the existing estimates currently in used were initially designed to be only baseline estimates (i.e the starting point for a conversation about home values between buyers and sellers) and its algorithms were not meant to be a comprehensive model for predicting 'true' housing sale prices.

The CEO has instructed the in-house data team to begin creating a model that can identify undervalued properties as accurately as possible, and with the lowest Root Mean Square Error (RMSE). The team could begin building the model based on a comprehensive database already collected by the company on the houses in Ames, Iowa, and subsequently improve from there. 

Management would also like this new model to address certain business concerns that they may have when buying undervalued houses and flipping them:

- Which features appear to add the most value to a home?
- What are the things that the renovation team could improve in these houses to increase its value?
- What neighborhoods seem like they might be a good investment?
- Do the team feel that this model will generalize to other cities? How could the team revise the model to make it more universal?


## Summary of Analysis
---

For our prediction model, we had used lasso regression as it had the best predictive performance (lowest RMSE) on housing price in Ames, Iowa, USA. The production model had a final total of 28 independent variables after applying feature selection, feature engineering and automated feature selection (namely: Recusive Feature Elimination and Lasso Regression). Although decreasing to 28 features, there had been a slight tradeoff between interpretability and accuracy of our prediction model. However, the benefits outweigh the costs and we will accept the tradeoffs.

<u>Interpretation of Coefficients</u>

As we have log-transformed our dependent variable, y, we would then have to interpret our coefficents differently as the linear regression equation then becomes:

$$log(y) = \beta_0 + \beta_1 x_1$$

The rule<sup>[(source)](https://data.library.virginia.edu/interpreting-log-transformations-in-a-linear-model/)</sup> for interpretation when only the dependent variable is log-transformed is to expnentiate the coefficient, subtract one from this number, and multiply by 100. This gives the percent increase (or decrease) in the response for every 1-unit increase in the independent variable.

To see why we exponentiate:
$$exp(log(y)) = exp(\beta_0 + \beta_1 x_1)$$

$$y = exp(\beta_0 + \beta_1)$$

$$y = exp(\beta_0) exp(\beta_1)$$

From this, we can see that our independent variable now has a **multiplicative relationship** with our dependent variable instead of the usual **additive relationship**. Hence, the need to express the effect of a 1-unit change in x on y as a percent!

Example: 
- For every 1-unit increase in `gr_liv_area`, our target variable `saleprice` will increase by 14%


![](/pictures/coefficient.png)

The coefficients of our production model (lasso regression model) had also indicated that **area** and **quality** of the house in general seems to be the biggest contributor to value of housing. Hence, a per unit increase in area of the house would cause a much greater percentage increase in the house price compare to other features. This is the same for quality / condition of the house, in which the better the quality / material used, the house price would increase to a greater extent as compared to other features.

<u>Other limitations faced when creating production model</u>

Having domain knowledge is important when deciding whether to convert nominal catergories to ordinal, especially when looking at materials. For example, for fence, it is difficult to determine the rank of privacy, material and no fence or if one hot encoding it should be a fairer way. Hence, domain knowledge here was important in which we would know if house buyers would deem which value as more valuable to them.


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

<u>Applicability of our model outside of Ames, Iowa<u/>
    
![](/pictures/ames_trend.png)
![](/pictures/general_trend.png)

The city of Ames do display trends that are in line with the majority of the cities. One example is the trend of housing prices even during the subprime mortgage crisis of 2008. However, one point to keep in mind that the last date recorded was in 2010 and there are not enough recent data to determine that Ames saleprice trend is still the same as the general US cities trend due to various factors such as housing policy changes, recession economy and COVID'19. Hence, the team do feel that this model may be applicable to a certain extent when using on other cities in the United States 

In order to revise the model to make it more universal, the simplest say would be to collect more recent data (2011-2021), preferably from other cities as well such as Los Angeles and New York, and create a model with a time period of 2000 - 2021. More universal features could also be added into the new data such as 'high rise buildings', 'elevators' and 'centralise carparks'.


## Data Dictionary
---

|Feature|Description|
|---|---|
|SalePrice|The property's sale price in dollars|
|MSSubClass|The building class|
|MSZoning|Identifies the general zoning classification of the sale|
|LotFrontage|Linear feet of street connected to property|
|LotArea|Lot size in square feet|
|Street|Type of road access to property|
|Alley|Type of alley access to property|
|LotShape|General shape of property|
|LandContour|Flatness of the property|
|Utilities|Type of utilities available|
|LotConfig|Lot configuration|
|LandSlope|Slope of property|
|Neighborhood|Physical locations within Ames city limits|
|Condition1|Proximity to main road or railroad|
|Condition2|Proximity to main road or railroad (if a second is present)|
|BldgType|Type of dwelling|
|HouseStyle|Style of dwelling|
|OverallQual|Overall material and finish quality|
|OverallCond|Overall condition rating|
|YearBuilt|Original construction date|
|YearRemodAdd|Remodel date (same as construction date if no remodeling or additions)|
|RoofStyle|Type of roof|
|RoofMatl|Roof material|
|Exterior1st|Exterior covering on house|
|Exterior2nd|Exterior covering on house (if more than one material)|
|MasVnrType|Masonry veneer type|
|MasVnrArea|Masonry veneer area in square feet|
|ExterQual|Exterior material quality|
|ExterCond|Present condition of the material on the exterior|
|Foundation|Type of foundation|
|BsmtQual|Height of the basement|
|BsmtCond|General condition of the basement|
|BsmtExposure|Walkout or garden level basement walls|
|BsmtFinType1|Quality of basement finished area|
|BsmtFinSF1|Type 1 finished square feet|
|BsmtFinType2|Quality of second finished area (if present)|
|BsmtFinSF2|Type 2 finished square feet|
|BsmtUnfSF|Unfinished square feet of basement area|
|TotalBsmtSF|Total square feet of basement area|
|Heating|Type of heating|
|HeatingQC|Heating quality and condition|
|CentralAir|Central air conditioning|
|Electrical|Electrical system|
|1stFlrSF|First Floor square feet|
|2ndFlrSF|Second floor square feet|
|LowQualFinSF|Low quality finished square feet (all floors)|
|GrLivArea|Above grade (ground) living area square feet|
|BsmtFullBath|Basement full bathrooms|
|BsmtHalfBath|Basement half bathrooms|
|FullBath|Full bathrooms above grade|
|HalfBath|Half baths above grade|
|Bedroom|Number of bedrooms above basement level|
|Kitchen|Number of kitchens|
|KitchenQual|Kitchen quality|
|TotRmsAbvGrd|Total rooms above grade (does not include bathrooms)|
|Functional|Home functionality rating|
|Fireplaces|Number of fireplaces|
|FireplaceQu|Fireplace quality|
|GarageType|Garage location|
|GarageYrBlt|Year garage was built|
|GarageFinish|Interior finish of the garage|
|GarageCars|Size of garage in car capacity|
|GarageArea|Size of garage in square feet|
|GarageQual|Garage quality|
|WoodDeckSF|Wood deck area in square feet|
|OpenPorchSF|Open porch area in square feet|
|EnclosedPorch|Enclosed porch area in square feet|
|3SsnPorch|Three season porch area in square feet|
|ScreenPorchScreen|Porch area in square feet|
|PoolArea|Pool area in square feet|
|PoolQC|Pool quality|
|Fence|Fence quality|
|MiscFeature|Miscellaneous feature not covered in other categories|
|MiscVal|Dollar Value of miscellaneous feature|
|MoSold|Month Sold|
|YrSold|Year Sold|
|SaleType|Type of sale|

