# customer_behavior_analysis
Customer Behavior Analysis

An end-to-end data analytics project on retail customer shopping behavior. Raw data is cleaned and feature-engineered in pandas, loaded into PostgreSQL, analyzed through 10 business questions in SQL, and presented in an interactive Power BI dashboard.

dashboard_screenshort.png

Tech Stack
Python (pandas) — data cleaning & feature engineering
PostgreSQL + SQLAlchemy — data storage & SQL analysis
Power BI — interactive dashboard
Dataset

customer_shopping_behavior.csv — 3,900 customer records, 18 columns covering customer profile (age, gender, location), transaction details (item, category, amount), experience (review rating, shipping, payment), and loyalty signals (subscription status, discounts, previous purchases).

Pipeline
CSV  →  pandas (clean + feature engineer)  →  PostgreSQL  →  SQL analysis  →  Power BI dashboard
1. Data Cleaning (pandas)
Filled 37 missing review_rating values using the category-level median
Standardized column names (lowercase, underscores)
Dropped promo_code_used after confirming it was 100% identical to discount_applied
2. Feature Engineering
age_group — Young Adult / Adult / Middle-aged / Senior, via pd.qcut
purchase_frequency_days — mapped purchase frequency labels (Weekly, Monthly, etc.) to numeric day counts
3. SQL Analysis

Cleaned data loaded into PostgreSQL, then queried to answer 10 business questions — revenue by gender, discount behavior vs. average spend, top-rated products, shipping type comparison, subscriber spend, customer segmentation (CTEs), top products per category (window functions), and revenue by age group.

See customer_behaivor_sql_queires.sql for all queries.

4. Power BI Dashboard

Interactive dashboard with KPI cards (customer count, average purchase amount, average review rating), category and age-group breakdowns, and slicers for subscription status, gender, category, and shipping type.

Key Insights
Only 27% of customers are subscribed — the largest untapped opportunity in the data
Clothing leads both revenue and order volume; revenue closely tracks order volume across all categories
Purchase amounts are tightly clustered ($20–$100), so growth is a volume problem, not a basket-size problem
Average review rating (3.75/5) is mediocre across the board, a possible retention risk
Repository Contents
File	Description
customer_behavior_analysis.ipynb	Data cleaning, feature engineering, and PostgreSQL load
customer_behaivor_sql_queires.sql	10 SQL business-question queries
customer_behavior_dashboard.pbix	Power BI dashboard
dashboard_screenshort.png	Dashboard screenshot
Limitations
No date/time column — trend and cohort analysis isn't possible
discount_applied and promo_code_used are perfectly collinear, so their individual effects can't be separated
previous_purchases is a running total, not a transaction log, so true customer lifetime value can only be approximated
