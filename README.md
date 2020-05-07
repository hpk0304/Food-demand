# Python project: Food-demand forecast
## Framework
Food demand forecast is a sample to track the business operation and control the inventory in Food and Beverage industry, particularly in online sales. Using the past data to train models aims to figure out the next 10 weeks food demand. 

Based on the analysis and model, the organization has overview about upcoming numbers of meal orders. Further, with the feature importance, the corporate can manage the raw materials, change the sales and marketing activities or maybe prepare the shipping and staffs according to the regions or cities

**Keywords:** Forecast; sales orders


## Targets, opportunities and challenges
**1. Targets**

Two main targets in the project include
- Figure out the feature importance and support the partner by understanding customer demand patterns 
- Do forecast for the next 10 weeks

**2. The opportunities**

There are several opportunities in the project
- High applicability not only for the e-commerce industry but also for any industry in terms of business overview and operation 
- This can be used as a baseline for further projects regarding to visualized and forecast with the linear regression models
- The variety of data helps the project develop the different visualizations  

**3. The challenges**

Some challenges in the project contain:
- The weekly number of meal orders are not unique. Therefore, it is necessery to aggregate the values by group
- The amount of meal orders after aggregation is huge and has lots of outliers. Thus, need to consider how to reduce the violation to support the predictions
- The collecting approaches has an impact on the evaluation metrics for each model and the final solution

## Outline
- Part 1: Define the problem
- Part 2: Exploratory Data Analysis (EDA)
- Part 3: Develop baselines and proposed solutions
- Part 4: Deploy the solutions
- Part 5: Further research

## Data
The data source is from Analytics Vidhya with three dataset 
| Data (csv) |     Weekly Demand     | Fulfilment_center_info | meal_info |
|------------|:----------------------|:-----------------------|:----------|
| Variables  | id                    | center_id              | meal_id   |
|            | week                  | city_code              | category  |
|            | center_id             | region_code            | cuisine   |
|            | meal_id               | center_type            |           |
|            | checkout_price        | op_area                |           |
|            | base_price            |                        |           |
|            | emailer_for_promotion |                        |           |
|            | homepage_featured     |                        |           |
|            | num_orders            |                        |           |

## Approaches
**1. Models**

- For importance feature, two methods Linear Regression model and Random Forest model are applied
Dataset is splitted randomly into two parts: train 70% and test 30% data

- For forecast, tuning ARIMA model aims to do out-of-sample forecast (10 weeks)
Dataset is spitted in order: train 70% and test 30% data

**2. Evaluation metrics**

- Apply Root of mean squared logarithmic error (100*RMSE) to evaluate the effieciency of models

## Insights and conclusions

**1. Target 1: Feature importance**

- Linear Regression model is highly recommended with 100*RMSE = 0.0167 and the score is nearly 0.94
- The important factors are op_area (operation area) with negative impact around 5.2 and homepage_featured with positive high coeficient approximately 0.75 on the increase of meal orders

**2. Target 2: Out-of-sample forecast**

- To ensure the stationarity, the forecast is based on the difference of target variable in t and t-1
- The result is reliable with 100*RMSE = 0.0773. 

## Further research

- Conducting the product-center combination in the past to do prediction can show the food demand and the center related. This helps corporate plan well the shipping and the staffing issues.
- The outliers in the dataset are large; however, to prevent removing the dataset, other investigations related to risk management and tail control should be proceeded
- Further, to improve the model, neuro network models can be conducted to optimize the predictions





