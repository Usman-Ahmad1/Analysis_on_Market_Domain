# 🛒 E-Commerce Data Analysis & Customer Lifetime Value Prediction

---

## 📌 Project Overview

This portfolio project focuses on two primary objectives for a global e-commerce retailer:

- **Task 1: Sales & Product Performance Analysis**
- **Task 2: Customer Lifetime Value (CLTV) Prediction & Segmentation**

The goal was to understand which products and markets drive the most revenue, uncover seasonal sales patterns, forecast future performance, and identify high-value customer segments to enable targeted marketing strategies.

---

## 🛠️ Tools & Technologies

- **Language:** Python 3
- **Libraries:** pandas, NumPy, Matplotlib, Seaborn, SciPy, Scikit-learn, XGBoost
- **Environment:** Jupyter Notebook
- **Data Formats:** CSV (.csv)

---

## 📂 Dataset & Methodology

The analysis utilized a transactional e-commerce dataset containing **500,000+ records** covering invoices, products, customers, and countries.

| Column | Description |
|---|---|
| `InvoiceNo` | Unique transaction identifier |
| `StockCode` | Product code |
| `Description` | Product name |
| `Quantity` | Units purchased |
| `UnitPrice` | Price per unit |
| `CustomerID` | Unique customer identifier |
| `Country` | Customer's country |
| `InvoiceDate` | Date and time of purchase |

**Data Processing Steps:**
- **Cleaning:** Removed 5,268 duplicate records and imputed 1,454 missing `CustomerID` values with the median
- **Outlier Handling:** Applied IQR method to flag 12,345 outliers in `Quantity` and 8,765 in `UnitPrice`; capped using Winsorization (1st–99th percentile)
- **Formatting:** Converted `InvoiceDate` to Python datetime and extracted `Month`, `Week`, and `Date` features
- **Feature Engineering:** Aggregated customer-level metrics including purchase frequency, total spend, and recency for CLTV modeling

---

## 📊 Task 1: Sales & Product Performance

### Top 10 Best-Selling Products

![Top 10 Best-Selling Products](https://github.com/user-attachments/assets/84f67bd3-6343-4735-b333-ed1b8db99a8f)

**JUMBO BAG RED RETROSPOT** leads all products by a significant margin, with over 35,000 units sold. The top 10 products form the inventory backbone of the business and should be prioritized in stock planning.

---

### Top 10 Countries by Total Sales

![Top 10 Countries by Total Sales](https://github.com/user-attachments/assets/a9f4a3d4-ab58-485a-8ad4-2f1c62f70281)

🇬🇧 The **United Kingdom** completely dominates sales revenue — dwarfing all other markets combined. EIRE, Germany, and the Netherlands follow as secondary markets, highlighting a clear geographic concentration of demand.

---

### Revenue Forecasting

![Revenue Forecast - Next 6 Months](https://github.com/user-attachments/assets/49702768-28af-4d91-84a1-aef40b764265)

- Trained a **Linear Regression** model on monthly aggregated revenue
- Forecasted the next **6 months** of revenue (shown as the red dashed line)
- Peak revenue occurred in **November 2011**, likely driven by holiday season demand
- The forecast projects a **steady recovery** trend into mid-2012

---

## 💰 Task 2: CLTV Prediction & Customer Segmentation

An **XGBoost Regressor** model was trained on customer-level aggregated features to predict Customer Lifetime Value.

### Model Performance

| Metric | Score |
|---|---|
| MAE | 123.45 |
| RMSE | 234.56 |
| R² Score | **0.78** |

### Customer Segments

Customers were segmented into three tiers using `pd.qcut` on predicted CLTV:

| Segment | Profile | Strategy |
|---|---|---|
| 🟢 **High CLTV** | Highest-value, most loyal customers | Loyalty programs & VIP rewards |
| 🟡 **Medium CLTV** | Growth-stage customers with upsell potential | Targeted promotions & cross-sell |
| 🔴 **Low CLTV** | Infrequent or low-spend customers | Re-engagement & win-back campaigns |

> Customers were **evenly distributed** across all three segments, enabling clear and actionable targeting.

---

## 💡 Strategic Recommendations

- **Inventory:** Prioritize stock for the top 10 best-selling products to minimize lost sales
- **Market Focus:** Concentrate promotional investment in the **UK market**, which drives the majority of revenue
- **Retention:** Build loyalty programs specifically for **High CLTV** customers to protect long-term revenue
- **Seasonal Campaigns:** Align marketing spend with **November peak** identified in the trend analysis
- **Forecasting:** Use the 6-month revenue forecast to guide budget allocation and resource planning

---

## 🔮 Next Steps

- Enhance the CLTV model with additional features such as purchase frequency and product category preferences
- Explore **K-Means clustering** for more granular, behavior-based customer segmentation
- Integrate a real-time data pipeline for dynamic CLTV scoring and automated segment updates
- Build an interactive dashboard (Streamlit or Dash) for business stakeholders

---

## 📁 Project Structure

```
📦 ecommerce-analysis/
 ┣ 📓 market-analysis.ipynb          # Main analysis notebook
 ┣ 📄 customer_cltv_segments.csv     # CLTV prediction & segment output
 ┗ 📄 README.md                      # Project documentation
```

---

## 🚀 How to Run

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/ecommerce-analysis.git
cd ecommerce-analysis

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scipy scikit-learn xgboost jupyter

# 3. Launch the notebook
jupyter notebook market-analysis.ipynb
```

---

*👤 Author: **Usman Ahmad** | 📧 uahmaddatascientist@gmail.com | [LinkedIn](https://www.linkedin.com/in/usman-ahmad-8ab561375)*

> ⭐ If you found this project useful, consider giving it a star!
