# Restaurant Sales Forecasting

This project aims to forecast restaurant sales using machine learning and time series forecasting techniques. It covers data exploration, feature engineering, model training, and evaluation using various models, including Linear Regression, Random Forest, XGBoost, and LSTM (Long Short-Term Memory) networks.

## Table of Contents
1. [Project Structure](#project-structure)
   - [1. Data Merging and Preparation](#1-data-merging-and-preparation)
   - [2. Exploratory Data Analysis (EDA)](#2-exploratory-data-analysis-eda)
   - [3. Time-Based Sales Analysis](#3-time-based-sales-analysis)
   - [4. Popular Items and Restaurants](#4-popular-items-and-restaurants)
   - [5. Modeling](#5-modeling)
   - [6. Time Series Forecasting with LSTM](#6-time-series-forecasting-with-lstm)
2. [Key Findings and Insights](#key-findings-and-insights)
3. [Model Performance](#model-performance)
4. [Suggestions for Improvement](#suggestions-for-improvement)
5. [Conclusion](#conclusion)
6. [Future Work](#future-work)

## Project Structure

### 1. Data Merging and Preparation
The project starts by merging three key datasets:
- `sales.csv`: Contains daily sales information for various items across restaurants.
- `items.csv`: Includes details about the food items, such as price and calories (`kcal`).
- `restaurants.csv`: Provides restaurant information.

We merged these datasets on relevant keys (`item_id` and `store_id`) to create a comprehensive dataset for analysis.

**Screenshot**:
- Merged Dataset Preview (Table preview of merged data)

![Screenshot 2024-10-21 at 3 03 54 PM](https://github.com/user-attachments/assets/f4c1bb7a-3626-4fb7-8aba-764ce267b1ba)

### 2. Exploratory Data Analysis (EDA)
Extensive EDA was conducted to gain insights into the sales patterns, item distribution, and potential data quality issues.

Key Observations:
- **Sales Distributions**: Histograms for `price`, `item_count`, and `kcal` revealed that `item_count` is highly skewed, with many items having 0 or low sales.
- **Outliers**: Boxplots for `price` and `item_count` identified several outliers, especially high-priced items or bulk orders.
- **Time-Based Trends**: Date-based analysis shows cyclical sales trends, indicating possible seasonality.

**Screenshots**:
- Histograms of `price`, `item_count`, and `kcal` distributions.

![histograms](https://github.com/user-attachments/assets/92deb6e8-ba7b-4041-a572-557995856224)

- Boxplots for `price` and `item_count` showing outliers.

![EDA Boxplot](https://github.com/user-attachments/assets/49065257-51dc-458e-91a6-79618faeb41a)

- Date-Wise Sales (Time-series plot of total sales over time).

![dailysalestrend](https://github.com/user-attachments/assets/8fd01534-2fb2-4f6d-889d-a52af452a03a)

### 3. Time-Based Sales Analysis
The analysis then focused on uncovering time-based patterns in the data, including:
- **Sales by Day of the Week**: Identified that sales peak on Fridays and Saturdays, while they dip on Mondays and Sundays.
- **Sales by Month and Quarter**: Sales tend to peak in May and July, possibly due to seasonal trends or events.

**Screenshots**:
- Bar chart of total sales by day of the week.

![totalsalesbydayofweek](https://github.com/user-attachments/assets/940b4b60-4ade-4a5e-8ef8-7bd1386844f9)

- Bar chart of sales per month, highlighting peaks in May and July.

![salespermonth](https://github.com/user-attachments/assets/52f50de0-9818-4524-b9d8-242c07acde78)

### 4. Popular Items and Restaurants
We identified the most popular items and the restaurants where they are sold. Bob's Diner consistently stood out as the highest-performing restaurant in terms of both item sales and revenue.

Key Findings:
- **Top 10 Most Popular Items**: Frozen Milky Smoothy and Strawberry Smoothy were the top-selling items.
- **Top-Performing Restaurants**: Bob's Diner had the highest sales, followed by Corner Cafe. The other restaurants showed lower and more steady sales.

**Screenshots**:
- Top 10 most popular items.

![Screenshot 2024-10-21 at 3 07 02 PM](https://github.com/user-attachments/assets/e4015787-57dc-4b17-bc61-b1d9a8bc3ffd)

### 5. Modeling
We applied several machine learning models to forecast restaurant sales:

- **Linear Regression**: A baseline model for predicting total sales (`item_count`) based on date and time features.
- **Random Forest**: An ensemble model to capture complex relationships between features and sales.
- **XGBoost**: A gradient boosting model that outperformed other models after hyperparameter tuning.
- **Model Comparison**: RMSE (Root Mean Squared Error) was used to compare model performance.

Key Results:
- Linear Regression RMSE: 36.27
- Random Forest RMSE: 36.18
- XGBoost RMSE: 36.18 (after tuning)


### 6. Time Series Forecasting with LSTM
To forecast future sales, we applied an LSTM model designed for sequential data. The model used a 90-day window to predict future sales based on historical data.

Steps:
- **Feature Scaling**: Scaled the `sales_amount` to normalize the data.
- **Model Training**: Trained the LSTM model on historical data to predict the next year's sales.
- **Prediction**: Generated sales forecasts for 365 future days, though the model's Mean Absolute Percentage Error (MAPE) suggested room for improvement.

**Screenshots**:
- LSTM forecast plot showing actual vs predicted sales.

![actualpredictedsales](https://github.com/user-attachments/assets/e2a6d471-06e3-4321-b870-64f997d51a0f)

- Plot showing predicted sales for the next 365 days.

![ForecastingFutureSales](https://github.com/user-attachments/assets/992d891d-a28b-4e80-90a9-47ac71774bc9)

## Key Findings and Insights

### Sales Patterns and Trends
- **Cyclical Trends**: Sales show clear seasonality, with peaks in the middle of the year.
- **Restaurant Performance**: Bob's Diner dominates in both sales volume and revenue.
- **Popular Items**: Smoothies and large meals are the most popular items, contributing significantly to overall sales.

## Model Performance
- **XGBoost**: Provided the best performance with a tuned RMSE of 36.17, outperforming both Linear Regression and Random Forest.
- **LSTM for Time Series**: The LSTM model showed promise but needs further tuning, as the high MAPE indicated that predictions were too smoothed and lacked accuracy in capturing short-term fluctuations.


## Suggestions for Improvement
1. **Refining LSTM**: Tuning the LSTM model by adjusting hyperparameters, such as the number of units or layers, and incorporating additional features (e.g., external holidays or events) may improve performance.
2. **Incorporating External Data**: Adding data on holidays, promotions, or weather could provide more accurate forecasts.
3. **Addressing Outliers**: Further exploration of outliers in the `item_count` and `price` columns could lead to cleaner data and better model accuracy.

## Conclusion
This project successfully demonstrated the use of machine learning and deep learning models to forecast restaurant sales. While models like Random Forest and XGBoost performed well, the LSTM model's high MAPE indicates the need for further refinement. The insights gained from EDA and time-series analysis provided valuable recommendations for improving sales strategies and restaurant performance.

## Future Work
1. **Improve LSTM**: Enhance the LSTM model by fine-tuning its architecture, adding more features, and experimenting with different scaling methods.
2. **Include Additional Features**: Introduce external data sources (e.g., holidays, promotions) to enhance the predictive power of the models.
3. **Outlier Treatment**: Implement a robust method to handle or remove outliers that may skew the model's predictions.
