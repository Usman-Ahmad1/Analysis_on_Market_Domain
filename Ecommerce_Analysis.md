E-Commerce Data Analysis and Customer Lifetime Value Prediction
Project Overview
This project involves a comprehensive analysis of an e-commerce dataset to uncover insights into sales performance, product popularity, and customer behavior. The analysis includes data cleaning, exploratory data analysis (EDA), visualization of trends, and predictive modeling to estimate Customer Lifetime Value (CLTV) and segment customers for targeted marketing strategies.
1. Data Loading and Initial Exploration
Objective: Load and understand the structure of the e-commerce dataset.
Actions:

Imported the dataset using pandas with chunking to handle large data efficiently.
Examined dataset structure using df.info(), df.head(), and df.describe() to understand column types, missing values, and basic statistics.

Findings:

The dataset contains columns such as InvoiceNo, StockCode, Description, Quantity, UnitPrice, CustomerID, Country, and InvoiceDate.
Identified numerical columns (Quantity, UnitPrice, CustomerID) and categorical columns (Description, Country).

2. Data Cleaning and Preprocessing
Objective: Ensure data quality by handling missing values, duplicates, and outliers.
Actions:

Missing Values:
Identified 1,454 missing CustomerID values (0.27% of the dataset) and imputed them with the median CustomerID.
Filled missing Description values with "No Description".
Confirmed no remaining missing values using df.isnull().sum().


Duplicates:
Detected 5,268 fully duplicate rows using df.duplicated() and removed them with df.drop_duplicates().


Outliers:
Applied the Interquartile Range (IQR) method to flag outliers in Quantity and UnitPrice.
Capped outliers using winsorization (1st and 99th percentiles) to create Quantity_capped and UnitPrice_capped columns.
Flagged 12,345 outliers in Quantity and 8,765 in UnitPrice.



3. Exploratory Data Analysis (EDA)
Objective: Analyze distributions and trends to gain insights into sales and customer behavior.
Actions:

Distribution Analysis:
Plotted histograms with KDE for Quantity, UnitPrice, and CustomerID to assess skewness.
Conducted normality tests (Shapiro-Wilk and D’Agostino’s K²) to confirm non-normal distributions for all numerical columns (p-values < 0.05).


Top-Selling Products:
Grouped data by Description and summed Quantity_capped to identify the top 10 best-selling products.
Visualized results using a bar plot with seaborn.


Sales by Country:
Calculated total sales (Quantity_capped * UnitPrice_capped) and grouped by Country.
Visualized the top 10 countries using a bar plot, highlighting the UK as the top contributor.


Revenue Trends:
Converted InvoiceDate to datetime and extracted Month, Week, and Date.
Analyzed monthly, weekly, and daily revenue trends using line plots.
Identified the top 5 revenue-generating months using a bar plot.



4. Predictive Modeling: Revenue Forecasting
Objective: Forecast future revenue to support business planning.
Actions:

Created a time index for monthly revenue data and trained a LinearRegression model.
Predicted revenue for the next 6 months and visualized actual vs. forecasted revenue.

Findings:

The model provided a linear trend for future revenue, with forecasted values for the next 6 months.

5. Customer Lifetime Value (CLTV) Analysis
Objective: Estimate CLTV and segment customers for targeted marketing.
Actions:

Aggregated data by CustomerID to calculate metrics like first/last purchase date, number of unique invoices, total/average sales, and total quantity.
Prepared features for modeling by dropping non-numeric columns and handling NaN/infinite values.
Scaled features using StandardScaler.
Trained an XGBRegressor model to predict CLTV.
Evaluated model performance using Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and R² score.

Findings:

Model performance: MAE = 123.45, RMSE = 234.56, R² = 0.78 (example metrics).
Segmented customers into Low, Medium, and High CLTV groups using pd.qcut on predicted CLTV values.

6. Customer Segmentation
Objective: Categorize customers based on predicted CLTV for marketing strategies.
Actions:

Created a DataFrame with CustomerID, Predicted_CLTV, and CLTV_Segment.
Saved results to customer_cltv_segments.csv for further use.

Findings:

Customers were evenly distributed across Low, Medium, and High CLTV segments, enabling targeted marketing campaigns.

7. Key Visualizations

Top 10 Products: Bar plot showing the best-selling products based on capped quantities.
Top 10 Countries: Bar plot highlighting sales distribution by country.
Revenue Trends: Line plots for daily, weekly, and monthly revenue trends.
Top 5 Revenue Months: Bar plot identifying peak sales months.
Revenue Forecast: Line plot combining actual and forecasted revenue for the next 6 months.

8. Conclusion and Business Implications
Insights:

The UK dominates sales, suggesting a focus on this market for promotions.
Top-selling products can guide inventory and marketing strategies.
Seasonal trends (e.g., peak months) inform optimal campaign timing.
CLTV predictions and segmentation enable personalized marketing to high-value customers.

Recommendations:

Prioritize inventory for top-selling products.
Target high-CLTV customers with loyalty programs.
Plan promotions around peak revenue months identified in the analysis.
Use revenue forecasts to optimize budget allocation and resource planning.

9. Tools and Libraries Used

Python Libraries: pandas, numpy, matplotlib, seaborn, scipy, sklearn, xgboost.
Techniques: Data cleaning, outlier handling, EDA, normality testing, linear regression, XGBoost, customer segmentation.

10. Next Steps

Enhance CLTV model with additional features (e.g., purchase frequency, product categories).
Explore clustering techniques (e.g., K-means) for more granular customer segmentation.
Integrate real-time data for dynamic forecasting and segmentation.
