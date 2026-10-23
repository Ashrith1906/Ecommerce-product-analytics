# E-commerce Funnel, Retention & RFM Analysis

This project analyzes e-commerce user activity to understand how users move through the purchase funnel, how conversion rates differ across channels and devices, how customer retention changes over time, and which customer segments contribute the most revenue.

I built this project using SQL and Python, along with an interactive dashboard to explore the results.

## Interactive Dashboard

**[Open the Interactive Dashboard](./interactive_dashboard.html)**

The dashboard brings the main analyses together in one place.

- **KPI Overview:** Users, conversion rate, revenue, and average order value (AOV).
- **Conversion Funnel:** Track users from product views to purchases and identify drop-offs.
- **Channel Analysis:** Compare purchase conversion rates across acquisition channels.
- **Device Analysis:** Compare conversion rates across mobile, desktop, and tablet users.
- **RFM Segmentation:** Explore customer segments by revenue contribution or customer count.
- **Cohort Retention:** View repeat-purchase behaviour using a retention heatmap.
- **Interactive Filters:** Filter by device and acquisition channel to explore the results.

> **Note:** The dataset is synthetic and was generated for this project. The results are illustrative and do not represent the performance of a real business.

## Project Objectives

The project focuses on five questions:

1. At which stage of the purchase funnel do the most users drop off?
2. How do conversion rates differ across acquisition channels and devices?
3. How does customer retention change over time?
4. Which customer segments contribute the most revenue?
5. How can these findings help identify areas for further investigation?

## Project Structure

```text
ecommerce-funnel-retention/
├── data/
├── sql/
│   └── analysis.sql
├── src/
│   ├── generate_data.py
│   ├── run_analysis.py
│   ├── build_interactive_dashboard.py
│   └── prepare_powerbi.py
├── charts/
├── interactive_dashboard.html
├── powerbi/
├── requirements.txt
└── README.md
```

- `data/` contains the generated CSV files.
- `sql/analysis.sql` contains the SQL queries used for analysis.
- `src/` contains the scripts for generating data, running the analysis, building the dashboard, and preparing Power BI tables.
- `charts/` contains the generated visualizations.
- `interactive_dashboard.html` is the interactive dashboard.
- `powerbi/` contains Power BI preparation files and the build guide.

## Getting Started

### Requirements

- Python 3
- pandas
- NumPy
- Matplotlib
- SQLite

SQLite is included with Python.

### Installation

Clone the repository and navigate to the project directory:

```bash
git clone YOUR_REPOSITORY_URL
cd ecommerce-funnel-retention
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

### Run the Project

Run the scripts in the following order:

```bash
python src/generate_data.py
python src/run_analysis.py
python src/build_interactive_dashboard.py
```

The scripts generate the dataset, perform the analysis, create visualizations, and build the interactive dashboard.

Open `interactive_dashboard.html` in a browser to explore the results.

## Dataset

The project uses three tables.

| Table | Description | Key Columns |
|---|---|---|
| `users` | User information | `user_id`, `signup_date`, `acquisition_channel`, `device` |
| `events` | User activity | `user_id`, `event_name`, `event_time` |
| `orders` | Completed purchases | `user_id`, `order_time`, `revenue` |

The purchase funnel follows four stages:

`product_view → add_to_cart → begin_checkout → purchase`

The dataset is generated locally, so no external download is required.

## Analysis

### 1. Conversion Funnel Analysis

I used distinct-user counts to measure how many users reached each stage of the purchase funnel.

The analysis compares consecutive stages to calculate step-conversion rates and identify where the largest drop-offs occur. This helps highlight stages that may need further investigation.

### 2. Conversion by Channel and Device

I compared purchase conversion rates across five acquisition channels:

- Organic
- Paid Search
- Social
- Email
- Referral

I also compared conversion rates across mobile, desktop, and tablet users.

These comparisons help identify differences in user behaviour and potential areas for further analysis.

### 3. Cohort Retention Analysis

Customers are grouped by the month of their first purchase, and their purchasing activity is tracked in subsequent months.

The cohort analysis helps examine repeat-purchase behaviour and compare retention across different customer groups. Results are displayed in a heatmap, with options to view retention percentages or user counts.

### 4. RFM Customer Segmentation

RFM analysis groups customers using three metrics:

- **Recency:** How recently a customer made a purchase.
- **Frequency:** How often a customer made purchases.
- **Monetary:** How much a customer spent.

The SQL analysis uses quintile-based scoring with `NTILE(5)` and categorizes customers into segments such as Champions, Loyal, At Risk, and Lost/Hibernating.

These segments can help identify valuable customers and groups that may benefit from targeted retention efforts.

### 5. Interactive Dashboard

I built an interactive HTML dashboard to make the results easier to explore.

It includes KPI cards, conversion charts, RFM visualizations, and a cohort-retention heatmap. Users can filter by device and acquisition channel, switch between funnel user counts and step-conversion percentages, and change the RFM and cohort display modes.

The device and channel filters update the KPI cards, funnel, and conversion charts. RFM and cohort views remain global and are not affected by those filters.

## SQL Concepts Used

The project uses the following SQL techniques:

- `COUNT(DISTINCT ...)` for distinct-user funnel calculations.
- `JOIN` operations to combine user, event, and order data.
- `CASE` expressions for conversion flags and customer segmentation.
- Common Table Expressions (CTEs) for organizing multi-step queries.
- Window functions such as `NTILE(5)` for RFM scoring.
- Date-based grouping for cohort analysis.
- Aggregations for calculating conversion rates and customer metrics.

The queries are available in `sql/analysis.sql`.

## Tech Stack

- **Languages:** SQL, Python, JavaScript
- **Data Analysis:** pandas, NumPy
- **Database:** SQLite
- **Visualization:** Matplotlib, HTML, CSS
- **Analytics:** Funnel analysis, conversion metrics, cohort retention, RFM segmentation
- **Additional Tools:** Power BI-ready tables and DAX preparation

## Limitations

The dataset is synthetic and does not represent actual customer behaviour or real business performance.

The analysis identifies patterns in the generated data, but these patterns do not establish causality. Any business recommendations would need to be validated using real data and, where appropriate, controlled experiments.

## Future Improvements

- Add statistical significance testing for conversion comparisons.
- Extend the analysis with additional customer and transaction metrics.
- Apply the analysis to a real e-commerce dataset.
- Deploy the dashboard as a live web demo.
- Build a Power BI dashboard using the prepared tables and DAX examples.

- GitHub: YOUR_GITHUB_PROFILE_URL
- LinkedIn: YOUR_LINKEDIN_PROFILE_URL
