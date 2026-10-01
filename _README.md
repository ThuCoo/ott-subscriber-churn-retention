<h1> OTT Subscriber Churn Analysis </h1>

This is a project following Rishabh Mishra's walkthrough

- [Rishabh Mishra's walkthrough](https://youtu.be/tTtI2arH214?si=2VeDz_QnK6-L8zHp)
<h2> Project Summary </h2>

This project analyzes a multi-dimensional database of OTT platform subscribers to uncover the primary drivers of customer churn. \
By evaluating demographic distribution, subscription tiers, and support escalations, the analysis builds a data-backed retention strategy and identifies key areas for product and customer service improvement.

<h2> Problem Statement </h2>

In the hyper-competitive OTT landscape (Netflix, Hotstar, Prime), retention is the only way to survive.

As a Data Analyst tasked with identifying high-risk subscribers using a multi-dimensional dataset (Customer
demographics, Subscription tiers, and Support escalations), **figure out why customers stop doing business with company.**

<h2> Tools Used </h2>

- **SQL & Python** - Data Preparation and Modeling, Data Analysis, Visualization and insights.
- **VS Code** - Development environment.
<h2> Dataset Summary </h2>
db_customer:

- Rows: 21
- Columns: 8

db_subscription:

- Rows: 21
- Columns: 11

db_support:

- Rows: 9
- Columns: 6

Key features:

- **Customer Info** (_db_customer_): Customer ID, Name, Country, State, Gender, Date of Birth.
- **Subscription Details** (_db_subscription_): Subscription Start Date, Plan Type (Basic/Standard/Premium), Contract Type, Monthly Charges, Cancellation Reason, Churn Score.
- **Support Logs** (_db_support_): Complaint Date, Escalations, CSAT Score.

<h2> Data Analysis using Python </h2>

**Data Loading**: Connected to a local database and extracted tables into DataFrames.

**Data Cleaning**:

- Dropped irrelevant or empty columns (_interests, pincode, col_1, comment_).
- Renamed primary keys to a standard customer_id across all DataFrames.
- Standardized string variables.

**Feature Engineering**:

- Calculate customer age using Date of Birth and the current timestamp, then bin them into age_group categories.
- Generate a binary churn_flag (1 or 0) based on the presence of a cancellation date.
- Create a churn_risk label by segmenting the existing numerical churn score.
- Calculate tenure_days by subtracting the subscription start date from either the cancellation date or the current date.
- Calculate complaint_count per customer.
- Missing Data Handling: Imputed missing Country values using a State-to-Country mapping dictionary.

**Data Consistency Check**: Filtered out duplicate support logs by sorting by complaint date and keeping only the last recorded escalation/CSAT score per customer.

**Data Merging & Export**: Merged all three cleaned DataFrames into a single master dataset, then exported the final table.

<h2> Visualization using Matplotlib </h2>

![Monthly Churn Trend](https://github.com/ThuCoo/DAProject_Churn/blob/07dbc818c44ec4c6c4dc2feceefbc8ed93354d07/visualization/monthly_churn_trend.png)

![Churn Rate by Plan Type](https://github.com/ThuCoo/DAProject_Churn/blob/07dbc818c44ec4c6c4dc2feceefbc8ed93354d07/visualization/churn_rate_by_plan_type.png)

![Churn Rate by State](https://github.com/ThuCoo/DAProject_Churn/blob/07dbc818c44ec4c6c4dc2feceefbc8ed93354d07/visualization/churn_rate_by_state.png)

![Correlation Matrix on Numeric Figures](https://github.com/ThuCoo/DAProject_Churn/blob/07dbc818c44ec4c6c4dc2feceefbc8ed93354d07/visualization/heatmap_numeric.png)

![Correlation Matrix on Churn Data](https://github.com/ThuCoo/DAProject_Churn/blob/07dbc818c44ec4c6c4dc2feceefbc8ed93354d07/visualization/heatmap_churn.png)

![Pairplot](https://github.com/ThuCoo/DAProject_Churn/blob/07dbc818c44ec4c6c4dc2feceefbc8ed93354d07/visualization/pairplot.png)

![Catplot](https://github.com/ThuCoo/DAProject_Churn/blob/07dbc818c44ec4c6c4dc2feceefbc8ed93354d07/visualization/catplot.png)

<h2> Business Recommendations </h2>

- **Audit the Basic Plan Offering**: Due to 60% churn rate isolated within the Basic plan, immediate audits of the Basic tier's content restrictions, ad-load, or recent price hikes are necessary to prevent further low-tier drop-offs.

- **Implement Proactive Escalation Routing**: With a high correlation (0.63) between support escalations and eventual churn, implement a priority routing system for users submitting multiple complaints can resolve friction before cancellation.

- **Targeted 'High-Risk' Retention Campaigns**: Deploy automated, personalized retention offers (e.g., a one-month upgrade or discount) specifically to the 'High Risk' cohort.

- **Investigate Regional Outages**: With a 100% churn rate in specific areas (e.g., Karnataka) alongside high variations in others, investigate localized streaming latency, server issues, or aggressive regional competitor campaigns in these specific states.
