# Sales forecasting with ML
Ever wanted to predict the future? Here's a thorough workthrough of how to do it. This dataset contains sales revenue data from a quick-serve restaurant chain featuring 14 separate stores. I go step by step from data cleaning to model evaluation. Rolling window CV, vizualization, feature importance analysis, and other steps also included.

### How to run
Use the `jupyter notebook` to run the notebook.
For a full detailed workthrough, run the notebook or visit: http://nbviewer.jupyter.org/github/areibman/Quick-e-cast/blob/master/Sales%20Forecasting.ipynb


### Information: 
Contains: 
* Slides explaining the model
* Complete workbook
* (TODO) Quick workbook

The dataset is rather large, please DM me if you would like access.

## Objective:
• Analyze time series sales data for 14 quick-serve food chains
• Identify trends in purchasing over time
• Determine key periods of performance
• Identify top predictors
• Create forecast for future sales

## Data Modeling Process:

• One-hot encode categorical features
• Remove negative and large outliers from training set
• Include rolling averages for the entire franchise as well as each
individual store
• Scale data in values between 0 and 1
• Test 5 separate models:
• General goodness of fit
• Rolling window cross validation
• Two separate modeling processes:
• Model all data available across all stores and make predictions
• Model data unique to each store and make predictions

## Data Description:

![Image of Data](https://raw.githubusercontent.com/areibman/Quick-e-cast/master/Screen%20Shot%202018-04-06%20at%204.51.51%20PM.png)

The column descriptions are:
1. Store_ID
2. Fiscal_Quarter
3. DateString in YYYYMMDD format
4. DayOfWeek (1 = Monday)
5. Daypart
6. Hourly weather summary
7. Hour of the day
8. Avg Hourly Temperature during this hour at this store
9. Sales Revenue during this hour (target)

## Samples

![Sales Data](https://raw.githubusercontent.com/areibman/Quick-e-cast/master/Screen%20Shot%202018-04-06%20at%204.52.04%20PM.png)

## Problems
![Problems](https://raw.githubusercontent.com/areibman/Quick-e-cast/master/Screen%20Shot%202018-04-06%20at%204.52.16%20PM.png)

## Distributions
![Distributions](https://raw.githubusercontent.com/areibman/Quick-e-cast/master/Screen%20Shot%202018-04-06%20at%204.52.28%20PM.png)

• Large irregularities lead to skewed distributions.
• Negative values present

## Transform categorical features into dummy variables
The following features were one-hot encoded:
• Fiscal_Qtr- A dummy variable for each quarter
• Fiscal_dayofWk- 1 through 7
• Daypart- Breakfast, lunch, dinner, etc.
• Hourly Weather- Clear-day, rain, etc.
• Store_ID
Holidays did not seem to vary enough to warrant encoding.

## Modifications
• Negative values removed
• Any value greater 10 standard deviations from the
mean removed

## Rolling Mean
• Encode average daily sales of all stores from previous day
![Rolling mean](https://raw.githubusercontent.com/areibman/Quick-e-cast/master/Screen%20Shot%202018-04-06%20at%204.52.47%20PM.png)
• Average daily sales from each individual store
[!Rolling mean sales](https://raw.githubusercontent.com/areibman/Quick-e-cast/master/Screen%20Shot%202018-04-06%20at%204.53.05%20PM.png)

## Predictive Models
Categories of models
• Generalized models- fit on sales revenue for all
stores
• Store specific models- fit on sales revenue for each
individual store
• 5 separate models selected:
* Linear models:
    * Linear regression (ordinary least squares)
    * Ridge Regression
    * Lasso Regression
* Decision tree based models-
    * Random Forest Regression
    * Gradient Boosting Regression
• Models were chosen on a basis of interpretability, intuitiveness, and performance.

## Metrics

Models were tested by two categories: 
* General goodness of fit in R2
    * How well the model fits to all recorded data 
* Rolling window cross validation
    * Each dataset was split into 10 separate time windows. The model is fitted on 10% of the earliest samples and tested on the remaining samples. Then, fitted on 20%, etc.
![RW CV](https://raw.githubusercontent.com/areibman/Quick-e-cast/master/Screen%20Shot%202018-04-06%20at%204.53.21%20PM.png)

## Generalized models:
#### Linear regression: Poor
* R squared 0.45839

#### Random forest regression: Good
* R squared 0.9413

#### Ridge Regression: Decent, better average performance
* R squared 0.4584

#### Lasso Regression: Similar to Ridge
* R squared 0.458

#### Gradient Boosting Regression: Good
* R squared 0.6318

## Performance Example:
![Store 17](https://raw.githubusercontent.com/areibman/Quick-e-cast/master/Screen%20Shot%202018-04-06%20at%204.58.38%20PM.png)

## Correlation with Sales:
![Corr](https://raw.githubusercontent.com/areibman/Quick-e-cast/master/Screen%20Shot%202018-04-06%20at%205.04.28%20PM.png)

## Features by importance:
![features](https://raw.githubusercontent.com/areibman/Quick-e-cast/master/Screen%20Shot%202018-04-06%20at%205.00.28%20PM.png)

## Summary
• Gradient boosting regression yields the best performance of the models selected and gives insight as to which features matter the most
• Each store shows a lunch rush trend
• Models fit on data unique to each store perform significantly
better
• “Predictionisdifficult,especiallyaboutthefuture.”--NielsBohr

