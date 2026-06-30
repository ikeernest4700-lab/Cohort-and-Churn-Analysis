# Cohort Retention & Churn Analysis
SQL • Power BI • Excel • Cohort Analysis • Churn Segmentation

---

## Overview
This project analyzes customer retention and churn behavior for an e-commerce platform (Mr Fuzzy Teddy Bear Store). It tracks how user cohorts behave over time, measures how quickly retention collapses, and segments churn by product, device, and traffic source to identify which acquisition channels need retention focus.

---

## Data Source
This project uses a public dataset from Maven Analytics as part of a data analytics challenge.

Source: https://www.mavenanalytics.io/data-playground

---

## Business Problem
In the e-commerce dataset for **Mr Fuzzy Teddy Bear Store**, customer retention dropped sharply after the first purchase, with churn quietly costing the business millions in lost revenue. The business had no clear view of how severe the churn was or which segments were driving it.

---

## Objectives
- Measure month-over-month cohort retention and overall churn rate
- Quantify the revenue impact of customer churn
- Segment churn by product, device, and traffic source to find the highest-risk segments
- Identify which acquisition channels and products need retention focus

---

## Tools & Technologies
- SQL → Data extraction, cleaning, cohort modeling
- Excel → Data validation and inspection
- Power BI → Dashboards, cohort heat maps, churn segmentation, DAX measures
- Analytics Methods → Cohort Analysis, Churn Analysis, Segmentation, Revenue Impact Estimation

---

## Core Skills Demonstrated
- SQL cohort modeling and retention calculation
- Power BI dashboard development and DAX measures
- Cohort retention analysis and churn modeling
- Churn segmentation by channel, device, and product
- Business impact estimation and revenue analytics

---

## Solution Approach

### 1. Cohort Retention Modeling
Built a cohort retention model in SQL tracking repeat purchase behavior month-over-month across 394K users, grouped by acquisition month.

### 2. Cohort Heat Map & Retention Curve
Visualized retention decay in Power BI using a cohort heat map (High/Medium/Low retention by month) and a retention curve showing the drop from Month 0 to Month 5.

### 3. Churn Segmentation
Built a dedicated Churn Segmentation page breaking down churn rate by product, traffic source, and device — instead of leaving these as filter-only slicers — so the highest-risk segments are visible at a glance.

---

## SQL Data Preparation (Sample)

```sql
cohort_orders AS (
SELECT
    user_id,
    order_id,
    created_at,
    DATE_TRUNC('month', MIN(created_at) OVER (PARTITION BY user_id)) AS cohort_month,
    DATE_TRUNC('month', created_at) AS order_month
FROM orders
),

retention AS (
SELECT
    cohort_month,
    DATEDIFF('month', cohort_month, order_month) AS month_number,
    COUNT(DISTINCT user_id) AS active_users
FROM cohort_orders
GROUP BY 1, 2
)
```

[View live cohort retention SQL code for Power BI reporting](SQL/cohort-retention.sql)

---

## Insights Dashboard View

![Cohort Analysis Dashboard](images/cohort-analysis.png)

![Churn Segmentation Insight](images/churn-segmentation.png)

[Live link to full report]()

---

## Key Metrics & Findings

### Cohort Overview
- Total Users: **394,318**
- Month 1 Retention: **6.95%**
- Overall Retention Rate: **11.13%**
- Retained Users: **43,892**
- Churn Rate: **88.87%**
- Estimated Revenue Lost From Churn: **$2.29M**

### Cohort Retention Decay
- Month 0: **100.00%**
- Month 1: **6.95%**
- Month 2: **5.78%**
- Month 3: **1.39%**
- Month 4: **0.18%**
- Month 5: **0.00%**

### Churn Segmentation
- Churned Users: **350.43K**

**By Product:**
- No Order: **88.75%**
- The Original Mr Fuzzy: **81.81%**
- The Forever Love Bear: **79.42%**
- The Hudson River: **77.12%**
- The Birthday Sugar Panda: **77.07%**

**By Traffic Source:**
- Facebook/Social: **100.00%**
- Google Search: **94.56%**
- Bing Search: **92.86%**
- Other: **11.32%**

**By Device:**
- Desktop: **88.62% churn** ($2.03M, 85.59% of lost revenue)
- Mobile: **82.60% churn** ($0.34M, 14.41% of lost revenue)

---

## Key Insights
- Retention collapses almost immediately — by Month 1, fewer than 7% of users are still active
- Facebook/Social and Google Search traffic show the highest churn, suggesting weaker post-acquisition engagement from paid/social channels
- Desktop users account for the large majority of revenue lost to churn, despite a similar churn rate to mobile
- "No Order" and Mr Fuzzy product lines carry the highest churn, pointing to first-purchase experience as a key retention risk

---

## Recommendations
- Build a first-30-day engagement sequence (email/SMS) targeting new users before Month 1 drop-off
- Re-evaluate retention strategy for Facebook/Social and Google Search-acquired users specifically
- Investigate the post-purchase experience for Mr Fuzzy buyers, given their disproportionate churn and revenue impact
- Prioritize desktop retention efforts first, given it represents 85.59% of revenue lost to churn

---

## Overall Business Impact
- Churn rate: **88.87%**
- Revenue lost to churn: **$2.29M**
- Revenue concentration: **85.59% of churn losses tied to desktop users**

---

## Conclusion
This project demonstrates the ability to model customer retention using SQL, build cohort-based dashboards in Power BI, and translate churn behavior into segmented, revenue-focused business recommendations.

---

## 🤝 Open to Opportunities

I am actively seeking opportunities in:

- Data Analyst roles (Entry-Level / Graduate / Junior)
- Healthcare Analytics roles
- Business Intelligence (BI) Analyst positions
- Data Engineering Internships
- Graduate Trainee Programs

I am open to remote, hybrid, and on-site opportunities where I can contribute to data-driven decision-making and continue developing technical expertise.

---

## 📬 Contact

**Ike Ernest**
Data Analyst | SQL | Power BI | Healthcare Analytics

- GitHub: [github.com/ikeernest4700-lab]
- LinkedIn: [https://www.linkedin.com/in/emeka-ike-108748198](https://www.linkedin.com/in/emeka-ike-108748198)
- Email: [ikeernest4700@gmail.com](mailto:ikeernest4700@gmail.com)
