# Car Price Prediction and Exploratory Data Analysis

## Overview
This project performs an exploratory data analysis (EDA) on a car prices dataset to understand factors influencing car prices and builds a basic linear regression model to predict car prices based on 'Year' and 'Mileage'.

## Dataset
The dataset contains information about car listings, including `year`, `make`, `model`, `trim`, `body_type`, `transmission`, `vin`, `state`, `condition`, `mileage`, `color`, `interior`, `seller`, `mmr` (Manheim Market Report price), `price` (selling price), and `saledate`.

- **Source**: `/content/car_prices.csv`
- **Shape**: 558,837 rows, 16 columns.

## Data Preprocessing
1.  **Missing Values**: Missing values in numerical columns were filled with the median, and categorical columns were filled with their mode.
2.  **Duplicate Check**: No duplicate rows were found in the dataset.
3.  **Column Renaming**: Key columns were renamed for clarity:
    - `sellingprice` to `Price`
    - `odometer` to `Mileage`
    - `body` to `Body_Type`
4.  **Column Formatting**: Column names were standardized by stripping spaces and capitalizing each word.

## Exploratory Data Analysis (EDA)
### Univariate Analysis
-   **Distribution of Car Prices**: The distribution is right-skewed, indicating that most cars are sold at lower prices, with a long tail extending to higher-priced vehicles. Price was visualized with a histogram and a box plot, showing many outliers in the higher price range.

### Bivariate Analysis
-   **Mileage vs. Price**: A strong negative correlation (-0.58) was observed, meaning as mileage increases, the car price generally decreases. This was visualized using a scatter plot.
-   **Year vs. Price**: A moderate to strong positive correlation (0.59) was found, indicating that newer cars tend to have higher prices. This was shown through a scatter plot and a line plot of average price by year.
-   **Average Price by Car Brand (Make)**: Luxury brands like Rolls-Royce, Ferrari, and Lamborghini consistently had the highest average prices.
-   **Transmission Type vs. Price**: Automatic cars were found to be significantly more expensive on average than manual cars, a difference confirmed statistically using a t-test.
-   **Condition's Influence on Mileage vs. Price**: Car condition acts as a mediating factor. While mileage generally lowers the price, cars in better condition (higher condition scores) retain their value more effectively and lose value more slowly than those in poor condition.

### Correlation Analysis
A correlation heatmap revealed strong relationships:
-   `Price` is highly correlated with `Mmr` (0.98), and moderately with `Year` (0.59) and negatively with `Mileage` (-0.58).
-   `Year` and `Mileage` have a strong negative correlation (-0.77), which is expected.

### Multivariate Analysis
A pair plot of `Price`, `Year`, and `Mileage` reinforced the bivariate findings, showing the distributions and relationships between these key numerical variables.

## Predictive Modeling
### Objective
To determine if car price is predictable using 'Year' and 'Mileage' as features.

### Model
A Linear Regression model was trained on the selected features.

### Performance Metrics
-   **MAE (Mean Absolute Error)**: 5261.75
-   **RMSE (Root Mean Squared Error)**: 7558.46
-   **R² Score**: 0.390

### Model Evaluation
The model explains approximately 39% of the variability in car prices. The presence of a relatively high RMSE suggests that while the model captures some trends, there are still significant individual prediction errors. A scatter plot of actual vs. predicted prices (both linear and log-scaled) further illustrated the model's limitations, showing that it struggles to predict higher prices accurately and a significant portion of price variation remains unexplained by just `Year` and `Mileage`.

## Key Insights & Conclusion
-   Car prices are primarily driven by `Year` (newer cars are more expensive) and `Mileage` (higher mileage leads to lower prices).
-   Luxury car brands command significantly higher prices.
-   Automatic transmission cars are generally more expensive than manual ones.
-   Car `Condition` plays a crucial role in how `Mileage` affects price, with better-conditioned cars retaining value longer.
-   While `Year` and `Mileage` are important predictors, they alone are insufficient for highly accurate car price prediction (R² = 0.39). More features (e.g., `make`, `model`, `trim`, `body_type`, `condition`, and potentially more advanced models) are required to build a more robust predictive model.
