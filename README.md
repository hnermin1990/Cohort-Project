# Cohort-Project
# 📊 Cohort Analysis – Customer Retention & Churn

## 📌 Project Overview

This project focuses on **cohort analysis** to understand customer behavior over time. The analysis groups customers based on their first purchase period and tracks how their activity changes in subsequent weeks.

The main goal is to measure **customer retention, churn, and cohort lifetime** and identify how effectively the business retains its customers over time.

---

## 🎯 Objectives

* Group customers into cohorts based on their first purchase week.
* Calculate **cohort lifetime** in weeks.
* Analyze customer **retention rates** over time.
* Identify customer **churn trends**.
* Compare the behavior of different customer cohorts.
* Visualize retention patterns using cohort tables and heatmaps.
* Identify periods where the largest customer drop-off occurs.

---

## 🗂️ Dataset

The analysis is based on customer order data.

The main variables used in the analysis include:

* `customer_id` – unique customer identifier
* `order_date` – date of the order
* `first_order_date` – customer's first purchase date
* `first_buy_week` – week in which the customer made their first purchase
* `cohort_lifetime` – number of weeks since the customer's first purchase

---

## 🧹 Data Preparation

The following preprocessing steps were performed:

1. Converted date columns to the appropriate datetime format.
2. Identified each customer's first purchase date.
3. Assigned customers to cohorts based on their first purchase week.
4. Converted first purchase dates to the beginning of the corresponding week.
5. Calculated the number of weeks between the customer's first purchase and subsequent purchases.
6. Prepared the data for cohort-based retention analysis.

### Cohort Week

The first purchase date was converted to the beginning of its week:

```python
orders['first_buy_week'] = (
    orders['first_order_date']
    - pd.to_timedelta(orders['first_order_date'].dt.weekday, unit='d')
).dt.normalize()
```

This allows customers who made their first purchase during the same week to belong to the same cohort.

### Cohort Lifetime

The time between the customer's first purchase and subsequent activity was converted into weeks:

```python
orders['cohort_lifetime'] = (
    orders['cohort_lifetime'] / np.timedelta64(1, 'W')
)
```

`cohort_lifetime` shows how many weeks have passed since the customer joined the cohort.

---

## 📈 Key Metrics

### Retention Rate

Retention measures the percentage of customers who remain active after joining a cohort.

**Formula:**

```text
Retention Rate =
Active Customers / Initial Cohort Customers × 100
```

A higher retention rate indicates that customers continue using the product or service for a longer period.

### Churn Rate

Churn Rate measures the percentage of customers who stop being active during a given period.

**Formula:**

```text
Churn Rate =
Lost Customers / Customers at the Beginning of the Period × 100
```

Retention and churn provide complementary views of customer loyalty and customer loss.

---

## 📊 Cohort Analysis

Customers are grouped according to their first purchase week.

The resulting cohort table shows how many customers from each cohort remain active during subsequent weeks.

For example:

| Cohort | Week 0 | Week 1 | Week 2 | Week 3 |
| ------ | -----: | -----: | -----: | -----: |
| Week 1 |   100% |    65% |    45% |    30% |
| Week 2 |   100% |    70% |    50% |    35% |
| Week 3 |   100% |    60% |    40% |    25% |

This makes it possible to compare the long-term behavior of different customer groups.

---

## 📉 Visualizations

The project includes visualizations such as:

* Cohort retention table
* Retention heatmap
* Retention rate by cohort lifetime
* Customer churn trends
* Cohort comparison charts

The heatmap helps identify which cohorts demonstrate stronger or weaker retention over time.

---

## 🔍 Key Questions

The analysis aims to answer questions such as:

1. How quickly do customers become inactive after their first purchase?
2. Which cohorts have the highest retention?
3. At which week is the largest customer drop-off observed?
4. How does retention change as cohort lifetime increases?
5. Which cohorts have the highest churn?
6. Are newer cohorts performing better than older cohorts?
7. Is customer retention improving over time?

---

## 💡 Business Insights

Cohort analysis can help businesses:

* Identify customer retention problems.
* Detect periods of high customer churn.
* Evaluate the effectiveness of customer acquisition strategies.
* Compare the quality of different customer cohorts.
* Develop targeted retention campaigns.
* Improve customer lifetime value.

---

## 🛠️ Tools & Technologies

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Jupyter Notebook**

---

## 📁 Project Structure

```text
cohort-analysis/
│
├── data/
│   └── orders.csv
│
├── notebooks/
│   └── cohort_analysis.ipynb
│
├── visualizations/
│   └── retention_heatmap.png
│
└── README.md
```

---

## 📌 Conclusion

Cohort analysis provides a clearer understanding of customer behavior than looking only at overall customer metrics. By tracking customers from their first purchase and measuring retention and churn over time, businesses can identify customer drop-off points and develop strategies to improve long-term customer retention.
