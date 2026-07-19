# Customer Shopping Behavior Analysis

An end-to-end data analytics project covering data preparation, SQL-based analysis, and interactive visualization — built to answer a real retail business question using a dataset of 3,900 customer transactions.

## Business Problem

A retail company wants to better understand its customers' shopping behavior to improve sales, customer satisfaction, and long-term loyalty. Management has noticed shifts in purchasing patterns across demographics, product categories, and sales channels, and wants to know which factors — discounts, reviews, seasons, payment preferences — drive consumer decisions and repeat purchases.

**Core question:** How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?

## Tech Stack

| Stage | Tool |
|---|---|
| Data Cleaning & Feature Engineering | Python (pandas) |
| Data Storage & Querying | PostgreSQL |
| Business Analysis | SQL |
| Visualization | Power BI |

## Repository Contents

```
├── Customer_Behavior.ipynb              # Data cleaning, EDA, feature engineering, DB load
├── querryyyy.sql                        # 10 business-question SQL queries
├── Customer_behavior_dashboard.pbix     # Interactive Power BI dashboard
├── customer_shopping_behavior.csv       # Raw dataset (3,900 rows, 18 columns)
├── Business_Problem_Document.pdf        # Project brief
├── Customer_Shopping_Behavior_Analysis.pdf  # Full write-up with results and screenshots
└── README.md
```

## Dataset

- **Rows:** 3,900 transactions
- **Columns:** 18, including customer demographics (age, gender, location, subscription status), purchase details (item, category, amount, season, size, color), and shopping behavior (discount applied, previous purchases, review rating, shipping type)
- **Missing data:** 37 nulls in `review_rating`, imputed using the median rating per product category

## 1. Data Preparation (Python)

- Loaded and profiled the dataset with `pandas` (`df.info()`, `.describe()`)
- Imputed missing review ratings using category-level medians
- Standardized column names to snake_case
- Engineered `age_group` (via age binning) and `purchase_frequency_days`
- Checked `discount_applied` vs. `promo_code_used` for redundancy and dropped the latter
- Loaded the cleaned dataset into PostgreSQL for SQL analysis

## 2. Business Analysis (SQL)

Ten queries answering specific business questions, including:

1. Total revenue by gender
2. Customers who used a discount but still spent above average
3. Top 5 products by average review rating
4. Average purchase amount: Standard vs. Express shipping
5. Subscriber vs. non-subscriber spend comparison
6. Top 5 products by discount-usage rate
7. Customer segmentation (New / Returning / Loyal) by purchase history
8. Top 3 products per category (via `ROW_NUMBER()`)
9. Whether repeat buyers (>5 previous purchases) are more likely to subscribe
10. Revenue contribution by age group

Full queries and inline notes are in `querryyyy.sql`.

## 3. Visualization (Power BI)

An interactive dashboard with filters for subscription status, gender, category, and shipping type, showing:
- Number of customers, average purchase amount, average review rating
- Revenue and sales by category
- Revenue and sales by age group
- Subscriber vs. non-subscriber split

## Key Findings

- **Revenue by gender:** Male customers generated $157.9K vs. $75.2K for female customers
- **Subscriptions:** Non-subscribers generated more total revenue ($170.4K) than subscribers ($62.6K), though subscriber base is smaller (1,053 vs. 2,847) — an opportunity to grow the subscriber segment
- **Age groups:** Young Adults are the top-spending segment ($62.1K), followed by Middle-aged, Adult, and Senior
- **Discount dependency:** Hats, Sneakers, and Coats have the highest share of discounted purchases (48–50%)
- **Customer segments:** 3,116 Loyal, 701 Returning, 83 New customers by purchase history
- **Shipping:** Express shipping customers spend slightly more on average ($60.48) than Standard ($58.46)

## Business Recommendations

- **Boost subscriptions** — promote exclusive benefits to convert non-subscribers, who currently drive the majority of revenue
- **Loyalty programs** — reward repeat buyers to move them into the Loyal segment
- **Review discount policy** — high discount dependency on certain products may be eroding margin
- **Product positioning** — highlight top-rated and best-selling products in marketing campaigns
- **Targeted marketing** — focus on high-revenue age groups and express-shipping users

## Author

Raj — MBA (Finance & Business Analytics), CMR University, Bengaluru
[GitHub](https://github.com/rajaraj2816)
