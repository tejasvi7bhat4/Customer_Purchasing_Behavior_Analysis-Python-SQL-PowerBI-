# Customer_Purchasing_Behavior_Analysis-Python-SQL-PowerBI-

**📌 Project Overview**

This project performs an end-to-end analysis of customer shopping behavior using transactional data from 3,900 purchases across various product categories. The pipeline covers data cleaning in Python, business analysis using MySQL, and visual storytelling through a Power BI dashboard.

The goal is to uncover actionable insights into spending patterns, customer segments, product preferences, discount dependency, and subscription behavior to guide strategic business decisions.

---

**🎯 Objectives**

- Understand who is buying and what they are buying
- Identify high-value customer segments based on purchase history
- Analyze the impact of discounts and promotions on revenue
- Compare subscriber vs. non-subscriber spending behavior
- Deliver data-driven business recommendations

---

**📂 Dataset Summary**

Rows	3,900

Columns	18

Missing Data	37 values in `Review Rating` column

---

**🔧 Tech Stack**

| Tool | Purpose |
|---|---|
| Python (Pandas) | Data cleaning, EDA, feature engineering |
| MySQL | Business queries & SQL analysis |
| Power BI | Interactive dashboard & visualization |
| Jupyter Notebook | Development environment |

---

**🧹 Data Cleaning & EDA (Python)**

**Steps Performed**

**1. Data Loading**
```python
import pandas as pd
df = pd.read_csv('shopping_behavior.csv')
```
**2. Initial Exploration**
```python
df.info()
df.describe()
df.isnull().sum()
```
**3. Missing Data Handling**

Found 37 null values in `Review Rating`
Imputed using median rating per product category to preserve distribution

**4. Column Standardization**

Renamed all columns to `snake_case` for consistency

**5. Feature Engineering**

`age_group` — binned ages into Young Adult, Adult, Middle-aged, Senior

`purchase_frequency_days` — derived from purchase frequency data

**6. Data Consistency Check**

Verified `discount_applied` and `promo_code_used` were fully redundant

Dropped `promo_code_used` to avoid duplication

**7. Database Integration**

Connected Python to MySQL using `mysql-connector-python`

Loaded the cleaned DataFrame directly into MySQL for SQL analysis

---
**🗄️ Business Analysis using MySQL**

Ten key business questions were answered using structured SQL queries.

**1. 💰 Revenue by Gender**

| Gender | Revenue (USD) |
|---|---|
| Female | 75,191 |
| Male | 157,890 |

> **Insight:** Male customers contribute ~2x more revenue than female customers.

---
**2. 🏷️ High-Spending Discount Users**

839 customers used discounts yet still spent above the average purchase amount

These are high-intent buyers who respond well to promotions without needing deep discounts

---
**3. ⭐ Top 5 Products by Average Rating**

|Rank|Item|Avg Rating|
|---|---|---|
|1|Gloves|3.86|
|2|Sandals|3.84
|3|Boots|3.82
|4|Hat|3.80|
|5|Skirt|3.78|

---
**4. 🚚 Shipping Type Comparison**

|Shipping Type	|Avg Purchase Amount (USD)
|---|---|
|Standard	|58.46|
|Express|	60.48|

> **Insight:** Express shipping customers spend slightly more on average, suggesting a willingness to pay for convenience.

---
**5. 📋 Subscribers vs. Non-Subscribers**

|Subscription	|Total Customers|	Avg Spend (USD)|	Total Revenue (USD)|
|---|---|---|---|
|Yes|	1,053	|59.49|	62,645|
|No|	2,847	|59.87|	170,436|

> **Insight:** Average spend is nearly identical, but only 27% of customers are subscribers — a major growth opportunity.

---
**6. 🏷️ Most Discount-Dependent Products**

|Item|Discount Rate (%)|
|---|---|
|Hat	|50.00|
|Sneakers	|49.66|
|Coat|	49.07|
|Sweater|	48.17|
|Pants	|47.37|

> **Insight:** Nearly half of purchases for these items use discounts. Margin review is advised.

---
**7. 👥 Customer Segmentation**

Customers classified by purchase history:
|Segment	|Customers	|Description|
|---|---|---|
|Loyal	|3,116	|High purchase history|
|Returning|	701	|Moderate purchase history|
|New	|83|	First-time or very few purchases|

> **Insight:** 80% of the customer base is already loyal — retention strategy is more important than acquisition.

---
**8. 🛒 Top 3 Products per Category**

|**Category**|**#1**|**#2**	|**#3**|
|---|---|---|---|
|Accessories|	Jewelry (171)|	Sunglasses (161)	|Belt (161)|
|Clothing|	Blouse (171)|	Pants (171)	|Shirt (169)|
|Footwear|	Sandals (160)	|Shoes (150)	|Sneakers (145)|
|Outerwear|	Jacket (163)	|Coat (161)	|Sunglasses (149)|

---
**9. 🔁 Repeat Buyers & Subscription Behavior**
Among customers with more than 5 purchases:
|Subscription| Status	Count|
|---|---|
|No	|2,518|
|Yes|	958|

> **Insight:** Most repeat buyers are NOT subscribed — targeted conversion campaigns could significantly boost subscription revenue.

---
**10. 👶 Revenue by Age Group**
|Age Group	|Total Revenue (USD)|
|---|---|
|Young Adult|	62,143|
|Middle-aged|	59,197|
|Adult|	55,978|
|Senior|	55,763|

> **Insight:** Revenue is fairly distributed across age groups, with Young Adults slightly ahead — good opportunity for targeted digital campaigns.

---
**📊 Power BI Dashboard**

An interactive Customer Behavior Dashboard built in Power BI featuring:

**KPI	Value:**

Total Customers	3.9K

Avg Purchase Amount	$59.76

Avg Review Rating	3.75

**Visuals included:**

🍩 Subscription Status breakdown — Yes 27% / No 73%

📊 Revenue & Sales by Category

📊 Revenue & Sales by Age Group

🔽 Slicers for Gender, Category, Subscription Status, Shipping Type

---

**💡 Business Recommendations**

1	Subscriptions	Launch targeted campaigns to convert the 2,518 repeat non-subscribers — they already show buying intent

2	Loyalty Programs	Reward Returning (701) customers with perks to push them into the Loyal segment

3	Discount Strategy	Review margins on Hat, Sneakers, and Coat — ~50% discount rate is unsustainable long-term

4	Product Campaigns	Feature top-rated products (Gloves, Sandals, Boots) prominently in ads and homepage

5	Targeted Marketing	Focus digital spend on Young Adults and Express-shipping users — both show higher revenue potential

6	Gender Strategy	Investigate why female revenue is lower and tailor product/marketing mix accordingly

---

**📈 Key Takeaways**

🔑 80% of customers are Loyal — retention > acquisition

📉 73% are non-subscribers despite similar spending to subscribers

💸 Discount dependency is high (~50%) for several key products

👨 Male customers drive 2x more revenue than female customers

🛒 Express shipping users spend more on average

---
