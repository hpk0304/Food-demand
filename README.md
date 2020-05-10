# Python project: Food-demand forecast
## Framework

**Describe the situation:** the corporation is a pickup business and desire to predict the amount of meal orders including Biryani, Pasta, Desert, Soup, Fish, Seafood, Starters, Pizza, Salad, Sandwich, Rice Bowl, Extras, other snacks and beverages in four cuisine such as Continential, Indian, Thai and Italian food. 

**Business problem:**

- The replenishment of majority of raw materials is done on weekly basis and since the raw material is perishable, the procurement planning is of utmost importance. 
- Staffing of the centers is also one area wherein accurate demand forecasts are really helpful.

Based on the analysis and model for the upcoming numbers of meal orders, the main purposes are to manage the raw materials for 10 weeks and to pay attention on how other fators effects the orders. Recognizing the most important features can also support the business to have an overview about the sales and marketing activities or maybe the negotiation with the shipping company.

Food demand forecast is a sample to track the business operation and control the inventory in Food and Beverage industry, particularly in online sales. Using the past data to train models aims to figure out the next 10 weeks food demand. 

**Keywords:** Forecast; sales orders


## Targets, opportunities and challenges
**1. Targets**

Two main targets in the project include
- Figure out the feature importance and support the partner by understanding customer demand patterns 
- Do forecast for the next 10 weeks

**2. The opportunities**

There are several opportunities in the project
- High applicability not only for the e-commerce activities but also for any industry in terms of business overview and operation 
- This can be used as a baseline for further projects regarding to visualized and forecast with the linear regression models
- The variety of data helps the project develop the different visualizations  

**3. The challenges**

Some challenges in the project contain:
- The weekly number of meal orders are not unique. Therefore, it is necessary to aggregate the values by group
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
| Data (csv) |     Weekly Demand                                       | Fulfilment_center_info              | meal_info            |
|------------|:--------------------------------------------------------|:------------------------------------|:---------------------|
| Variables  | id (unique)                                             | center_id                           | meal_id              |
|            | week (week no)                                          | city_code (unique code for city)    | category (meal type) |
|            | center_id (unique ID for center)                        | region_code (unique code for region)| cuisine              |
|            | meal_id (unique id for meal)                            | center_type (anonymized)            |                      |
|            | checkout_price (final price)                            | op_area (area operation (in km**2)  |                      |
|            | base_price (base price)                                 |                                     |                      |
|            | emailer_for_promotion (emailer sent for meal promotion) |                                     |                      |
|            | homepage_featured (meal featured on homepage)           |                                     |                      |
|            | num_orders (target - order count)                       |                                     |                      |

## Approaches
**1. Models**

- For importance feature, two methods Linear Regression model and Random Forest model are applied
Dataset is splitted randomly into two parts: train 70% and test 30% data

- For forecast, tuning ARIMA model aims to do out-of-sample forecast (10 weeks)
Dataset is spitted in order: train 70% and test 30% data

**2. Evaluation metrics**

- Apply Root of mean squared logarithmic error (100*RMSE) to evaluate the effieciency of models: MSE is quite popular in regression problem with the normality assumption. In the fact of dataset, due to the large deviations, the square helps to reduce the error values with the robust results and restrict the absolute error values (just show the magnitudes but not the trend of violations). Moreover, the huge outliers in the real num_orders (number of orders) can be solved with the logarithm num_orders_log, which is applied throughout part 3 and 4 as the target. Therefore, we use Root of mean squared logarithmic error (100*RMSE). Multiply with 100 to make sure the clear visualization for audiences.  

## Insights and conclusions

**1. Target 1: Feature importance**

- Linear Regression model is highly recommended with 100*RMSE = 0.0167 and the score is nearly 0.94
- The important factors are op_area (operation area) with negative impact around 5.2 and homepage_featured with positive high coefficient approximately 0.75 on the increase of meal orders

**2. Target 2: Out-of-sample forecast**

- To ensure the stationarity, the forecast is based on the difference of target variable in t and t-1
- The result is reliable with 100*RMSE = 0.0773. 

## Further research

- Conducting the product-center combination in the past to do prediction can show the food demand and the center related. This helps corporate plan well the shipping and the staffing issues.
- The outliers in the dataset are large; however, to prevent removing the dataset, other investigations related to risk management and tail control should be proceeded
- Further, to improve the model, neuro network models can be conducted to optimize the predictions





