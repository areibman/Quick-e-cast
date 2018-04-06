# Sales forecasting with ML
Ever wanted to predict the future? Here's a thorough workthrough of how to do it. This dataset contains sales revenue data from a quick-serve restaurant chain featuring 14 separate stores. I go step by step from data cleaning to model evaluation. Rolling window CV, vizualization, feature importance analysis, and other steps also included.

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
![Image of Data]
(https://raw.githubusercontent.com/areibman/Quick-e-cast/master/Screen%20Shot%202018-04-06%20at%204.51.51%20PM.png)
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

### How to run
Use the `jupyter notebook` to run the notebook.


